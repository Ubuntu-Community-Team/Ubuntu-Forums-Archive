---
title: "Making DVD's"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by servicetech on 2010-09-15
I want to make DVD's from avi/mpeg/h264 files on my computer that will play in a standard DVD player. What is the easiest program to use?

---

### Post by 3rdalbum on 2010-09-15
Brasero. It's even preinstalled on Ubuntu.

---

### Post by servicetech on 2010-09-15
> **3rdalbum said:**
> Brasero. It's even preinstalled on Ubuntu.

How do you get it to convert avi/mpeg/h264 files to a format compatible with a standard DVD player?

---

### Post by jhanus10 on 2010-09-15
Currently i am playing with this myself right now i am using avi files right now and using DVD Styler finding it to be pretty easy to use and create menu's. Havnt tried other video formats yet. With avi I add the avi files to the project, create the menu & layout etc.. click burn and bout 20 min  later i have a finished DVD thats playable on my home player.

---

### Post by servicetech on 2010-09-15
> **jhanus10 said:**
> Currently i am playing with this myself right now i am using avi files right now and using DVD Styler finding it to be pretty easy to use and create menu's. Havnt tried other video formats yet. With avi I add the avi files to the project, create the menu & layout etc.. click burn and bout 20 min  later i have a finished DVD thats playable on my home player.

That's what I'm looking for, I'll give it a try.

---

### Post by servicetech on 2010-09-15
How do I start the program? I don't see it anywhere in the applications list after installing.

---

### Post by 3rdalbum on 2010-09-15
> **servicetech said:**
> How do you get it to convert avi/mpeg/h264 files to a format compatible with a standard DVD player?

Click on "Create a video project" and then drag your file(s) into the window. If the files aren't DVD standard (yours aren't) then Brasero will transcode them.

If your files aren't playable in Totem Movie Player then they probably can't be transcoded by Brasero (because the transcoding is done by Gstreamer, which also powers Totem). In this situation you could use Devede instead - it should be in the repositories, but it's not as easy to use.

---

### Post by SquishyOctopus on 2010-09-15
Personally, I like using Devede to convert my avi's to a DVD image.  Then just burn the image to a DVD.

---

### Post by jhanus10 on 2010-09-16
> **servicetech said:**
> How do I start the program? I don't see it anywhere in the applications list after installing.

WOW weird all i did was use the apt install method from terminal and it appeared in my sound video menu i did nothing special.

sudo apt-get install dvdstyler

and that was it.

---

### Post by jhanus10 on 2010-09-16
> **SquishyOctopus said:**
> Personally, I like using Devede to convert my avi's to a DVD image.  Then just burn the image to a DVD.

DvD Styler lets you do that too ISO, Save to a Folder, or burn directly to DVD

---

