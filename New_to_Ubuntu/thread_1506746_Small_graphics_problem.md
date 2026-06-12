---
title: "Small graphics problem"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by sparkplug619 on 2010-06-10
Hello, I am not sure if it has to do with the nvidia graphics driver I have installed (one of the 2 the hardware manager suggested) But I turned my computer off after a few changes to the grub bootloader.

When my computer booted up, I went to firefox and now when I scroll, some of the lines dont scroll correctly. When I try to take a screenshot of the page to post here, the screen reverts to normal right before the screenshot is taken so it doesnt show up messed up in the screenshot.

---

### Post by sparkplug619 on 2010-06-10
I found a way to take the screenshot by using the delay function... ill post it as soon as I upload it. This only shows the problem in a few images and logos but it is usually in the text.

---

### Post by sparkplug619 on 2010-06-10
EDIT: nevermind the problem is back

---

### Post by sparkplug619 on 2010-06-10
Here is another screenshot.. this one shows how bad it is.


it also happens when I scroll in file explorer

---

### Post by sparkplug619 on 2010-06-11
bump.

---

### Post by sparkplug619 on 2010-06-12
Ive tried everything I could think of. I barely started linux so I cant go any further than a few graphic card tweaks. Nothing is working. 

I am at a point of desperation, very close to repartitioning and reinstalling ubuntu.

---

### Post by oldsoundguy on 2010-06-12
do NOT know if this will work or even if you can do it with your settings .. but try experimenting with the refresh rate in your video settings.

---

### Post by sparkplug619 on 2010-06-12
> **oldsoundguy said:**
> do NOT know if this will work or even if you can do it with your settings .. but try experimenting with the refresh rate in your video settings.


Thanks for the reply.

I only have 1 setting for my refresh rate. 60hz.

---

### Post by Tackleberry 518 on 2010-06-12
I had the same problem when I installed 10.04 but the lines were vertical.  Formatted and went back to 9.10 and the problem went away.  BTW Im using an ATI 5850.

---

### Post by oldsoundguy on 2010-06-12
Spark, are you using the default install drivers or are you using the restricted drivers from Synaptic?

I had all sorts of display issues (minor, but issues) with  10.04 on an UPGRADE install over 8.04.
Found the solution by going to terminal and REMOVING running rm /etc/X11/xorg.conf   ..  I then re-booted and Lucid installed a NEW xorg without all of the dragged along stuff from previous builds.  ALL of the issues went away and I gained total control over everything including screen settings (refresh and resolution) and even the RandRRotation feature for my monitor SELF INSTALLED.

---

### Post by sparkplug619 on 2010-06-12
> **oldsoundguy said:**
> Spark, are you using the default install drivers or are you using the restricted drivers from Synaptic?

I had all sorts of display issues (minor, but issues) with  10.04 on an UPGRADE install over 8.04.
Found the solution by going to terminal and REMOVING running rm /etc/X11/xorg.conf   ..  I then re-booted and Lucid installed a NEW xorg without all of the dragged along stuff from previous builds.  ALL of the issues went away and I gained total control over everything including screen settings (refresh and resolution) and even the RandRRotation feature for my monitor SELF INSTALLED.


The only driver I am using that wasnt default was the wireless adapter driver.

I will try what you recommended and report back with details

---

### Post by sparkplug619 on 2010-06-12
Thank you oldsoundguy. I am no longer experiencing graphic issues.

Thank you for your support.

---

