---
title: "Connect to Internet"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Badhon_raj on 2009-02-27
Hi, I'm a newbie in ubuntu. I want to connect to internet via nokia 6630(Data Cable)(EDGE Modem). Now please explain me how to do that. As I am a beginner in ubuntu, so please explain it in a step by step procedure.
Thanks...

---

### Post by Sealbhach on 2009-02-27
Hi,
Are you using Intrepid Ibex 8.10?  What happens when you plug in the phone?

I found a method on the forums which applied to earlier versions of ubuntu, which you could try - see this post here:

[http://ubuntuforums.org/showpost.php?p=4018367&postcount=29](http://ubuntuforums.org/showpost.php?p=4018367&postcount=29)

However, it is possible that your phone is supported in the latest version.

Don't be too scared of those instructions, it's not actually that difficult and you are given step-by-step instructions. Hope this helps and good luck.

.

---

### Post by Badhon_raj on 2009-02-27
Thanks a lot for so early reply. One more question.
I've downloaded some apps from
```
http://linux.softpedia.com/progDownload/VLC-Download-2608.html
```
They are in .bz2 format.
But I don't know how to install them. Please help me.

---

### Post by Hobgoblin on 2009-02-27
> **Badhon_raj said:**
> Thanks a lot for so early reply. One more question.
I've downloaded some apps from
```
http://linux.softpedia.com/progDownload/VLC-Download-2608.html
```
They are in .bz2 format.
But I don't know how to install them. Please help me.

Install VLC through synaptic package manager, you'll need to enable universe repositories first.

---

### Post by Badhon_raj on 2009-02-27
But I want to install app on a pc that has no internet connection!

---

### Post by Sealbhach on 2009-02-27
> **Badhon_raj said:**
> 
They are in .bz2 format.
But I don't know how to install them. Please help me.

That is a file containing the source code for VLC, you would have to compile it to install it. You don't want to get into that (yet). I tried compiling VLC recently - just for the learnings - and it didn't work properly... and was difficult to do.

You can get .deb files of VLC here:

[http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/)

But I think that's just the installer, you would probably still need an internet connection to get the full package. Linux is heavily dependent on having a working internet connection...


.

---

### Post by arm-c on 2009-02-28
There is probably a better way, however, you do want to ensure you get all dependencies for the package.  I'd go to synaptic package manager and right click on the package, get properties, then click the dependencies tab.  That should tell you all packages you MUST have to instal.  Some might be installed by default, some might not.

Then, you will move those all a specific location on new computer or on CD.  You'd have to tell synaptic where to find them ideally, however, alternately, you could install from command line and list all packages on the install line.

I'd take the new directory approach, and then point synaptic to that location as an alternate source.

Hope that helps or points down right path for you.

---

