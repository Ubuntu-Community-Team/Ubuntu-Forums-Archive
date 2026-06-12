---
title: "how to export images from digiKam to the desktop?"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by cdpottery on 2011-01-27
Hello,
  I'm hoping desperately that someone can help me.  First off, I am brand spanking new to Linux.  I have always be a mac user.  With that in mind I can manage to turn the computer on or off and check internet plus a few extras.  Yup, I am not in the least bit techy.
  What I need to do is resize and export my digiKam images to a desktop folder so I can upload them to my internet shop as either .jpg or .png files.  DigiKam does not provide that option as export to desktop.  Somewhere I read that you can link between digiKam and the desktop folder, how do you do this?
  Any assistance is appreciated!

---

### Post by cariboo on 2011-01-27
Can you not just navigate to the directory where your pictures are stored, instead of having duplicates in a folder on your desktop?

---

### Post by AlphaLexman on 2011-01-27
> **cdpottery said:**
>  What I need to do is resize and export my digiKam images to a desktop folder so I can upload them to my internet shop as either .jpg or .png files.
Are your original files in jpg, png or raw format?

How many megapixels is your camera, what size do you want to output to?

ImageMagik's 'convert' program can resize and change filetype in one step.
```
convert input_image.jpg -resize [geometry] output_image.jpg
```

See 'man convert' for more options.

If you are shooting in raw format (you should be, if your camera supports it) you may want to do some post-processing before compressing to jpg or png formats. Look into 'ufraw'.

> **cdpottery said:**
> Somewhere I read that you can link between digiKam and the desktop folder, how do you do this?
You can [soft] link files this way:
```
ln -s ~/Pictures/2011-01-27/original_image_001.jpg ~/Desktop/link_to_original_image_001.jpg
```

---

### Post by cdpottery on 2011-01-29
Thank you very much for your responses.  
Yes, exporting the images files will copy or move them them to the desktop.  My method has always been to place them in a file folder on the desktop, list them and then trash the copies.  It's just how I've always done it...

My camera does not support raw files, it's 4 mega pixels and 6 years old now.  Generally, I do the sizing in jpeg format down to 1000 X 1000 or 1600 X 1200 pixels.  I didn't have the option for .png files before Linux.  Much better quality, I need to learn how to upload and work with these.

I did figure out a way to do this after much trial and error and frustration.  In DigiKam I choose the image I want.  Select the image edit button and do my editing.  Then under transform I click the resize option.  In that screen I can resize my images and select okay.  Then I save or save as under the file option.  In this screen I can choose where to save the image, picture folders or albums within digiKam.  Under filter I can choose the type of image file I want to save, .png or jpg or 15 other options.  Then click save.  

Going back into the digiKam albums I can then click and drag my newly saved image onto the desktop.  Since this moves the image onto the desktop I then click and copy it back into digiKam so that I don't loose it.  It's a whole lot of steps and I'm certain there is a more efficient way of doing this but I don't know how yet.

Thank you for the soft link, I will try that to see if it removes some of the these steps.  I know I will only understand and learn how to use 10% of digiKams capabilities.

---

