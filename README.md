# Segmentation-and-Repositioning-of-an-Image

This repository contains code for object segmentation and repositioning within images. The code leverages the Segment Anything Model (SAM) for segmentation and OpenAI's CLIP model for object classification. The project's primary goal is to identify a specific object in an image, generate a segmentation mask, and reposition the object based on user-defined pixel shifts.


![image](https://github.com/user-attachments/assets/785d896c-ed74-414a-aac1-66842377f0b7)

This project provides the following functionalities:

Object Identification: Uses the CLIP model to match an object class (e.g., "bag", "Wall hanging", "stool") with objects in the input image.
Segmentation Mask Generation: Uses the Segment Anything Model (SAM) to generate segmentation masks for all objects in the image.
Repositioning Objects: Moves the segmented object to a new location within the image based on user-specified pixel shifts.
#Dependencies
Python 3.7+
PyTorch
OpenAI's CLIP
SAM (Segment Anything Model)
OpenCV
PIL (Python Imaging Library)
NumPy
Installation
Clone this repository:

bash
Copy code
git clone https://github.com/your_username/object-segmentation-repositioning.git
cd object-segmentation-repositioning
Install the required dependencies:

bash
Copy code
pip install -r requirements.txt
Download the SAM checkpoint from SAM Checkpoints.

Usage
Command Line Interface
To run the segmentation and repositioning script, you can use the following command:

bash
Copy code
python main.py --image_path /path/to/your/image.jpg --object_class 'cat' --output_path /path/to/output.png --shift_x 50 --shift_y -20
Parameters:
image_path: Path to the input image.
object_class: The object class to identify (e.g., 'cat', 'dog').
output_path: Path to save the output image with the segmented object.
shift_x: Horizontal pixel shift is used to reposition the object.
shift_y: Vertical pixel shift is used to reposition the object.
Functions Overview
load_clip_model(device)
Loads the CLIP model and its preprocessing pipeline.

generate_masks(sam, image_array)
Generates segmentation masks for the input image using SAM.

load_sam_model(checkpoint_path)
Loads the SAM model from a given checkpoint.

main(image_path, object_class, output_path)
Performs the following steps:

Loads the image and preprocesses it.
Loads SAM and CLIP models.
Identifies objects in the image that match the specified class.
Generates segmentation masks for the objects.
Saves the output image with a mask overlay.
reposition_object(image_path, final_mask, shift_x, shift_y, output_path)
Repositions the object in the image based on a segmentation mask and specified pixel shifts. The final image is saved to the provided output path.

Example
Here’s a quick example of how to run the code:

Python
# Example to identify and reposition a 'cat' in an image
final_mask = main('cat-and-dog-sitting. jpg', 'cat', 'output_image1.png')

# Task 2
# Reposition the object if segmentation is successful

if final_mask is not None:
    reposition_object('cat-and-dog-sitting.jpg', final_mask, shift_x=50, shift_y=-20, output_path='repositioned_output_image.png')
Troubleshooting
Common Issues:
Model Checkpoint Not Found: Please make sure you have downloaded the SAM model checkpoint and placed it in the right directory.

CUDA Errors: If you encounter CUDA errors, please check that your machine has a compatible GPU and PyTorch is installed with CUDA support. If not, the code will default to CPU.

Incorrect Object Class: If CLIP fails to identify the object, ensure that the object class label provided  is appropriate for the image.

Debugging:
If segmentation or object repositioning doesn't work, please make sure that the segmentation mask is generated successfully by adding debug statements in the main function to verify the mask generation.
Contributing
Contributions are welcome! Please submit a pull request or open an issue for any bugs or feature requests.

License
This project is licensed under the MIT License.


#output
![image](https://github.com/user-attachments/assets/fc837470-bd46-488c-b65f-e65230f70195)
