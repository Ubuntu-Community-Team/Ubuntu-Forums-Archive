---
title: "install from cd rom..."
date: 2009-12-07
forum: New to Ubuntu
---

### Post by confubar on 2009-12-07
Have new Dell inspiron 15n...
I wanted to install Blender from cdrom.  All I could get out of synaptic was the error message
E: failed to mount the cd rom
I had previously gotten Blender online with Synaptic, and removed it because of doubling and blurring of images and freezing so that the blender windows only left the screen- after quitting- when I moused around over the window or used the "force app to quit " widget.
Any suggestions much appreciated...
confused and fubar

---

### Post by lotharmat on 2009-12-07
Can you read *any* disks in the CD ROM?

---

### Post by confubar on 2009-12-07
Unfortunately I don't have other cd's with me to try. It will play a movie from dvd, and file browser sees the folders and files on the blender cd

---

### Post by lidex on 2009-12-07
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1328242]("http://ubuntuforums.org/showthread.php?t=1328242")
also:
[http://ubuntuforums.org/showthread.php?t=381972]("http://ubuntuforums.org/showthread.php?t=381972")
[http://ubuntuforums.org/showthread.php?t=414993]("http://ubuntuforums.org/showthread.php?t=414993")

---

### Post by snowpine on 2009-12-07
Where did you get this magic CD, and why do you trust it to work better than the version of Blender in the Ubuntu repositories?

The normal method of installing Blender is through Synaptic, or the terminal:

```
sudo apt-get update && sudo apt-get install blender
```

If the version in the Ubuntu repositories is buggy for you, maybe you can try a different version: [http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

---

### Post by confubar on 2009-12-07
> **snowpine said:**
> Where did you get this magic CD, and why do you trust it to work better than the version of Blender in the Ubuntu repositories?

The normal method of installing Blender is through Synaptic, or the terminal:

```
sudo apt-get update && sudo apt-get install blender
```If the version in the Ubuntu repositories is buggy for you, maybe you can try a different version: [http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

I tried the cd from the book "The Essential Blender"....  Used the cd because I temporarily dont have internet access on my ubuntu computer, and I want Blender.
But, first I had downloaded Blender using Synaptic online.... Did not work properly so I removed it

---

### Post by snowpine on 2009-12-07
> **confubar said:**
> I tried the cd from the book "The Essential Blender"....  Used the cd because I temporarily dont have internet access on my ubuntu computer, and I want Blender.
But, first I had downloaded Blender using Synaptic online.... Did not work properly so I removed it

I understand, that makes sense. :) Personally, I would only install applications from a trusted source like the Ubuntu repositories or the Blender website, but that's just my opinion. 

The answer to your question is completely dependent on what's actually on that CD. If they have it set up as an apt mirror CD then you can use the apt-cdrom commands described above... but I kind of doubt it. Probably what you have on the CD is the source or an installer executable. So the actual install method depends on what they've given you to work with. 

At the risk of stating the obvious, does the book give instructions on how to install Blender? If not, maybe you deserve your money back. ;)

---

### Post by confubar on 2009-12-07
> **lidex said:**
> Have a look here:
[http://ubuntuforums.org/showthread.php?t=1328242](http://ubuntuforums.org/showthread.php?t=1328242)
also:
[http://ubuntuforums.org/showthread.php?t=381972](http://ubuntuforums.org/showthread.php?t=381972)
[http://ubuntuforums.org/showthread.php?t=414993](http://ubuntuforums.org/showthread.php?t=414993)


Thanks

---

### Post by confubar on 2009-12-07
> **snowpine said:**
> I understand, that makes sense. :) Personally, I would only install applications from a trusted source like the Ubuntu repositories or the Blender website, but that's just my opinion. 

The answer to your question is completely dependent on what's actually on that CD. If they have it set up as an apt mirror CD then you can use the apt-cdrom commands described above... but I kind of doubt it. Probably what you have on the CD is the source or an installer executable. So the actual install method depends on what they've given you to work with. 

At the risk of stating the obvious, does the book give instructions on how to install Blender? If not, maybe you deserve your money back. ;)

This afternoon I will go where wireless is available and try again from the ubuntu repositories. If the result is fubar on my laptop, I will try again using the first thread that lidex suggested.
The book assumes that one knows what one is doing.:redface:

---

