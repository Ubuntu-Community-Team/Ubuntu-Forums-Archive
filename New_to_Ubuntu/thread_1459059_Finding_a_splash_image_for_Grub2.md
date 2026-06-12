---
title: "Finding a splash image for Grub2"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by GMHilltop on 2010-04-20
I am setting up a splash image for my grub2 boot menu, and the one that I think is soooo cool, is the background image that appears when I go to pick the user to Log In to Ubuntu 9.10 (the one that looks like there is a light shinning down from above and highlighting the floor and the name "Ubuntu".

Can I use that for my splash image?
where is it located in the file system?
what is it called?

thanks for the help :P

---

### Post by Sin@Sin-Sacrifice on 2010-04-20
[http://jaeger.morpheus.net/linux/grubsplash.html](http://jaeger.morpheus.net/linux/grubsplash.html)  You can edit any picture to be like this in gimp. The colors part I guesstimate.

---

### Post by bigsmitty64 on 2010-04-21
Isn't that page grub legacy? He has grub2. Won't it be different? I noticed the page is from 2004. I'm not saying I know, I'm just asking, as I would like to be sure so I can check it out also. :)
EDIT:
I just found [THIS]("http://ubuntuforums.org/showthread.php?t=1302743")....Maybe he would be better served there.

---

### Post by Sin@Sin-Sacrifice on 2010-04-21
I'm sorry... I meant to just refer to the first 6 lines. The point being that you can use any image format if you have grub set to read the other image formats as long as they fit the description. [This]("http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/") might be more helpful. I'm pretty sure you can make the resolution larger now too but it has to be 14 colors or less.

---

### Post by bigsmitty64 on 2010-04-21
Its all good, that tut you linked to looks interesting, gonna check it out also!

---

### Post by GMHilltop on 2010-04-21
Maybe to be a little more clear, the image that I am looking for must already be in the files somewhere.

I have attached it as a file called splash-screen.jpg -- that is the one that I am looking to find in the files that are already installed in the system.

=========

As a side note - I Like the log in screen (that was there :confused:)  -- see cool-ubuntu-login.jpg

I was tinkering with the settings just to see what they would do -- see the settings.jpg
I checked off the enhance contrast in colors (yuck) - and then unchecked it.  Now it won't go away.

I am stuck with the ugly login -- see  ugly-login.jpg  attached.

Any Ideas?

---

### Post by drs305 on 2010-04-21
I have those images in /usr/share/images/xsplash. The picture you want as a grub background image is a compilation of several images in that folder. The main background is called bg2560x1600.jpg and is accompanied by logo and throbber images.

You would need to create the total image with an app like GIMP.

---

### Post by GMHilltop on 2010-04-21
That's what I was looking for - Thanks!

Any Ideas regarding this:

> **GMHilltop said:**
> 
As a side note - I Like the log in screen (that was there :confused:)  -- see  cool-ubuntu-login.jpg

I was tinkering with the settings just to see what they would do -- see  the settings.jpg
I checked off the enhance contrast in colors (yuck) - and then unchecked  it.  Now it won't go away.

I am stuck with the ugly login -- see  ugly-login.jpg  attached.

Any Ideas?

........ or should that maybe be a different thread?

---

### Post by drs305 on 2010-04-21
Have you tried logging off and back in, or restarting? 

Unless that is successful, I'd recommend a new thread since the topic doesn't concern Grub2 splash images. You are likely to get more people who can help with that specific problem by using an applicable thread title.

---

### Post by philinux on 2010-04-21
Also look here.

[https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming)

---

### Post by GMHilltop on 2010-04-21
I'll start another thread, thanks

---

### Post by GMHilltop on 2010-04-21
New thread on the ugly Log In started here:

[http://ubuntuforums.org/showthread.php?p=9154459#post9154459](http://ubuntuforums.org/showthread.php?p=9154459#post9154459)

---

