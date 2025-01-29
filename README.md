Text_to_Image

Text_to_Image is a project that utilizes Stable Diffusion to convert textual descriptions into high-quality images. The application filters out unwanted features using a negative prompt to ensure the generated images meet quality standards.

Features
Convert text prompts into images using Stable Diffusion
Filters out common issues like low quality, duplicates, and errors with a negative prompt
Simple and user-friendly interface
Installation
To get started, clone the repository and install the necessary dependencies:
bash
Copy code
git clone https://github.com/pradeepsengarr/Text_to_Image.git
cd Text_to_Image
# Assuming a requirements.txt or similar file exists for dependencies
pip install -r requirements.txt
Usage
Input Text: Enter a descriptive text prompt into the text box.
Generate Image: The application uses Stable Diffusion to create an image based on the input prompt.
View Result: The generated image will be displayed on the interface.
Example prompts:

"astronaut, riding a horse, on mars"
"cargo ship, flying, in space"
"Dancing bitches"
Code Overview
The core function get_completion takes a prompt and generates an image using Stable Diffusion. It includes a negative_prompt to exclude undesirable elements like low quality, duplicates, and errors.

python
Copy code
def get_completion(prompt):
  negative_prompt = """
  simple background, duplicate, low quality, lowest quality,
  bad anatomy, bad proportions, extra digits, lowres, username,
  artist name, error, duplicate, watermark, signature, text,
  extra digit, fewer digits, worst quality, jpeg artifacts, blurry
  """
  return sd_pipeline(prompt, negative_prompt=negative_prompt).images[0]
The Gradio interface genai_app provides an easy-to-use frontend for users to input prompts and view generated images.

python
Copy code
genai_app = gr.Interface(fn=get_completion,
                         inputs=[gr.Textbox(label="Your prompt")],
                         outputs=[gr.Image(label="Result")],
                         title="Generate Cool Images",
                         description="Generate any image with Stable Diffusion",
                         allow_flagging="never",
                         examples=["astronaut, riding a horse, on mars",
                                   "cargo ship, flying, in space",
                                   "Dancing bitches"])
genai_app.launch()
Contributing
We welcome contributions! Please follow these steps:

Fork the repository.
Create a new branch (git checkout -b feature-branch).
Make your changes.
Commit your changes (git commit -m 'Add new feature').
Push to the branch (git push origin feature-branch).
Open a Pull Request.
License
This project is licensed under the MIT License. See the LICENSE file for details.

Contact
For any inquiries, please contact pradeep19sengar@gmail.com.
