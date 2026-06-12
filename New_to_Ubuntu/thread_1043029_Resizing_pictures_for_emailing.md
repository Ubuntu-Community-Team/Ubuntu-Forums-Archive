---
title: "Resizing pictures for emailing"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by lory on 2009-01-18
I would like to mail a certain number of pictures and resize them at the same time alltogether. This was possible with with Micorsoft, by clicking of the selected pictures and after "send to" email there was the option to resize them.

---

### Post by BennBuntu on 2009-01-18
if you import them all into f-spot, you can select them all and resize when you export to folder.
I'm sure there's a fairly simple command line approach too.

---

### Post by mcduck on 2009-01-18
Well, you can do that with any image editor you like..

But I suppose you'll want something in the right-click menu. So install the **nautilus-image-converter** package. (You'll have to restart Nautilus or log out and back again before the new options appear in the right-click menu)

Or you could do the same I always do, install Imagemagick and use a command like this:
```
for f in *.jpg; do convert "$f" -strip -resize 640x480 -quality 86 small-"$f"; done
```
That would go through all jpg images in current directory, remove EXIF data, resize images to fit into 640x480 (while maintaining correct aspect ratio) and then save the them into new images using "small-" as prefix for file names to separate the resized pics from originals.

---

### Post by treesurf on 2009-01-18
In terminal:

sudo aptitude install nautilus-image-converter

and then reboot and you will have image resizing options whenever you right click on an image.

---

### Post by jflarm on 2009-01-18
I don't think you have to reboot, only log out and log in again.

---

### Post by lory on 2009-01-18
cannot find the nautilus package under the menu for installing new software, where I can get this?

---

### Post by mcduck on 2009-01-18
> **lory said:**
> cannot find the nautilus package under the menu for installing new software, where I can get this?

Use the Synaptic Package Manager (System/Administration/Synaptic Package Manager). The Add/Remove-thing only lists a limited selection of most commonly used applications while Synaptic includes everything that available.

Or open a terminal and run "sudo apt-get install nautilus-image-converter"

---

### Post by harshpkaria on 2009-01-18
Or maybe just use Picasa/F-spot and do whatever u want..

---

### Post by Georgia boy on 2009-01-19
I just used OpenOffice.org Draw this morning. I did the insert picture then exported as jpeg. Let it send out at 75 percent. Came out okay. I messed up yesterday and didn't do this. Sent out as regular pictures and took forever. Felt like kicking myself when I saw what I had done.
Tom

---

