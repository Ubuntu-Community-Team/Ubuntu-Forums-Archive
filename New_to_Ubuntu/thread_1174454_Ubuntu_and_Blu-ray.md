---
title: "Ubuntu and Blu-ray"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-05-30
So I'm getting a new computer and decided to throw a blu-ray drive in there.  Other than that article about using hd dump to rip the movie off the disc, is there any free or commercial software that will play the disc on ubuntu?

My computer is hooked up to an HDTV with an HDCP compatible card.

I don't want to use 30 gb of space every time using that decryption program, but I will if there are no other options.

---

### Post by CryptiniteDemon on 2009-05-30
Also, has anyone tried Nero for Linux for Blu-rays?

Also, I guess another good question would be how well (if at all) vmware or virtualbox support blue-ray drives.

---

### Post by 3rdalbum on 2009-05-31
There's no software on Linux yet that can play Blu-rays directly from the disc, unfortunately. Ripping is going to be your only option.

Nero Linux is more like Brasero than it is like Nero for Windows. No, there's no Blu-ray playback in Nero Linux.

It might be possible to run a Blu-ray playback program within a virtual machine, but playback would be choppy as the CPU would be doing all the work AND running the overhead of an extra operating system (no GPU acceleration). You'd probably need a 3.33Ghz Core 2 CPU or better to get reasonable playback performance. But I can only theorise on performance - I haven't tried it. YMMV.

---

### Post by binbash on 2009-05-31
If you are going to rip it, you can use 2 pass x264 encoding with dvd::rip.Tho i did not try it with blurays.

---

### Post by 3rdalbum on 2009-05-31
I don't think Dvd::rip will help with Blu-rays, binbash. They're completely different beasts to DVDs - different encryption and different file format. Besides, all Dvd::rip seems to do for me on DVDs is fill up my hard disk with garbage data.

---

### Post by Sef on 2009-05-31
Read this Ubuntu Help post: [Blueray and HDDVD]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD").  Note: It refers to Intrepid Ibex (8.10.)

---

### Post by Sealbhach on 2009-06-01
I don't really like the idea of needing 50GB of disk space just to play a movie. I was wondering if there's been any progress since last November on this problem?


.

---

### Post by CryptiniteDemon on 2009-06-02
> **Sef said:**
> Read this Ubuntu Help post: [Blueray and HDDVD]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD").  Note: It refers to Intrepid Ibex (8.10.)

That's the article I referenced in the first post.

> 
 You'd probably need a 3.33Ghz Core 2 CPU or better to get reasonable playback performance. But I can only theorise on performance - I haven't tried it. YMMV.

It's a Core i7 940 processor with 12 gb of ram.


See Nero offers the ability to back up blu ray discs, but nothing on their site says anything about actually playing them.

Hopefully DRM will die within the next 6 years or so.

---

### Post by Mornedhel on 2009-06-02
> **CryptiniteDemon said:**
> [...] 12 gb of ram [...]

Whoa.

What kind of applications do you run ?...

---

### Post by philinux on 2009-06-02
It is interesting that nautilus has the options for blue-ray. See edit>prefs>media tab, other media then type. But no application to deal with a blu-ray video disc. Maybe something for the future.

---

