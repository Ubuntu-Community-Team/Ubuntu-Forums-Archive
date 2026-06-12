---
title: "nautilus crop multiple images"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by duruttye on 2009-03-12
Hey there!

I'm looking for a way to crop multiple images in nautilus, or any other way. I have a few scripts in nautilus, rotate and resize, but no crop. It doesn't have to be necessarily be in nautilus...

Thanks!

---

### Post by aeiah on 2009-03-12
im assuming your rotate and resize scripts actually use imagemagick? you can crop with that. of course, if you want it to be dynamic it'll get a bit more complicated but if you're gonna be cropping every photo in the same way each time you could just use a simple imagemagick command.

if you want to specify pixels or percents to crop etc you could knock something up in bash that uses imagemagick with zenity at the front end for a GUI config dialog. if you go down that path though you might as well use a full image editor (although gimp would still be overkill no doubt)

---

### Post by Paqman on 2009-03-12
There's a plugin for Nautilus called nautilus-image-resizer that can resize and rotate images from a right-click (which it sounds like you've already got?)

If you want to actually crop part of the image though you'll have to open them individually and select the part you want to crop off.

---

### Post by binbash on 2009-03-12
Did you check Phatch ?

---

### Post by duruttye on 2009-03-12
Well, I'm not very good at making scripts, so I will leave that part out, but I will try out that Phatch thing, will get back to you in a while!

Thanks!

---

### Post by Paqman on 2009-03-12
I've never used ACDSee, but if you want an image manipulation package you've got GIMP pre-installed.

---

### Post by empty_spaces on 2009-03-12
gthumb does image cropping quite easily.
It is also my program of choice for viewing animated gifs.

---

### Post by duruttye on 2009-03-13
Well, I installed Phatch, but I haven't had the time to figure it out yet. I have a few hundred images to crop, so it won't be easy croping them one by one...

thanx for the replies so far, after I try out the Phatch application I will gat back to you again!

---

### Post by unutbu on 2009-03-13
Is the amount you want to crop off each image the same? If so, imagemagick might be able to do the job from the command-line.
(See [http://www.imagemagick.org/Usage/crop/#crop](http://www.imagemagick.org/Usage/crop/#crop), for example).

---

