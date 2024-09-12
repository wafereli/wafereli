- 👋 Hi, I’m @wafereli
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
wafereli/wafereli is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
from PIL import Image, ImageDraw, ImageFont

def create_image_with_text(text, output_path, image_size=(800, 600), bg_color=(0, 0, 0), text_color=(255, 255, 255), font_size=50):
    # Create a new image with the specified background color
    image = Image.new('RGB', image_size, bg_color)
    draw = ImageDraw.Draw(image)

    # Load a font
    try:
        # Adjust the path to the font file if necessary
        font = ImageFont.truetype("arial.ttf", font_size)
    except IOError:
        font = ImageFont.load_default()

    # Calculate text size and position
    text_width, text_height = draw.textsize(text, font=font)
    text_x = (image_size[0] - text_width) / 2
    text_y = (image_size[1] - text_height) / 2

    # Draw the text on the image
    draw.text((text_x, text_y), text, font=font, fill=text_color)

    # Save the image
    image.save(output_path)

# Customize these parameters
text = "Your Name"
output_path = "output_image.png"
bg_color = (0, 0, 0)  # Black background
text_color = (255, 255, 255)  # White text
font_size = 50

# Create the image
create_image_with_text(text, output_path, bg_color=bg_color, text_color=text_color, font_size=font_size)

