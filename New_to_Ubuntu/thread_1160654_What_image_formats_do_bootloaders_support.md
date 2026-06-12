---
title: "What image formats do bootloaders support?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-05-15
I installed startup manager and I am trying to add bootloader themes and I cannot add any image files like .jpg and .png. Am I doing something wrong? What image formats should I select as bootloader theme? I am using Ubuntu 9.04. And on the side, changing the usplash in Jaunty does not work.

Please advise. Thank you!

---

### Post by ScottMorris on 2009-05-15
What boot loader are you trying to use? is it the modified GRUB that is all pretty like in openSUSE?

---

### Post by LesterPalooza on 2009-05-15
> **ScottMorris said:**
> What boot loader are you trying to use? is it the modified GRUB that is all pretty like in openSUSE?

Normal grub.

---

### Post by ScottMorris on 2009-05-15
Normal GRUB has some picky issues with images.

Rez: 640 x 480
Type: xpm.gz
Colours: 16

The GIMP is a good editor to convert your images in and it saves to xpm, then you just need to gunzip it.

The images need to be put into the /boot/grub folder and a line to the menu.lst added at the top add splashimage=(hd0,0)/boot/grub/myfile.xpm.gz

Here is a thread with example images: [http://ubuntuforums.org/showthread.php?t=278396](http://ubuntuforums.org/showthread.php?t=278396).

And another good one: [http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.1](http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.1)

---

### Post by LesterPalooza on 2009-05-15
> **ScottMorris said:**
> Normal GRUB has some picky issues with images.

Rez: 640 x 480
Type: xpm.gz
Colours: 16

The GIMP is a good editor to convert your images in and it saves to xpm, then you just need to gunzip it.

The images need to be put into the /boot/grub folder and a line to the menu.lst added at the top add splashimage=(hd0,0)/boot/grub/myfile.xpm.gz

Here is a thread with example images: [http://ubuntuforums.org/showthread.php?t=278396](http://ubuntuforums.org/showthread.php?t=278396).

And another good one: [http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.1](http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.1)

Thank you! :)

---

### Post by ScottMorris on 2009-05-15
I went th*r*ough the same thing once :) I used to have a 16 colour tropical fish :D

---

