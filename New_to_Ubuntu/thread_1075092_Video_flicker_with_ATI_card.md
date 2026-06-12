---
title: "Video flicker with ATI card"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by stotheg on 2009-02-19
I was fed up with Windows, but at least I could see my videos...

I have a Averatec 6235 laptop w/AMD Mobile Athlon 64 2800+ / 1.8 GHz, 64-bit, 1 gig of ram, with a 60 gb hard drive, and the video is integrated SIS (described as 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter using the lshw command in the terminal). I am running Ubuntu 8.1 64 bit edition (I had the same issue with the 32 bit version and upgraded hoping to fix it.) and everything works great exception of the flicker and the low quality of video. It flickers during video playback and when scrolling on web pages with dark backgrounds. The resolution is correct as is the aspect ratio.  I am sure this is a driver issue, but I can't find it anywhere.  The closest thing I have found are some drivers for Red Hat.  Will those work?    Help me stay Ubuntu!

---

### Post by overdrank on 2009-02-19
> **stotheg said:**
> I was fed up with Windows, but at least I could see my videos...

I have a Averatec 6235 laptop w/AMD Mobile Athlon 64 2800+ / 1.8 GHz, 64-bit, 1 gig of ram, with a 60 gb hard drive, and the video is integrated ATI (described as 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter using the lshw command in the terminal). I am running Ubuntu 8.1 64 bit edition (I had the same issue with the 32 bit version and upgraded hoping to fix it.) and everything works great exception of the flicker and the low quality of video. It flickers during video playback and when scrolling on web pages with dark backgrounds. The resolution is correct as is the aspect ratio.  I am sure this is a driver issue, but I can't find it anywhere.  The closest thing I have found are some ATI drivers for Red Hat.  Will those work?    Help me stay Ubuntu!

Hi and welcome, are you sure that is not a SIS chipset for graphics?

---

### Post by stotheg on 2009-02-19
> **overdrank said:**
> Hi and welcome, are you sure that is not a SIS chipset for graphics?

You are correct.  I have abbreviations coming out my ears.  I changed it in the post.  Any thoughts?

---

### Post by overdrank on 2009-02-20
> **stotheg said:**
> You are correct.  I have abbreviations coming out my ears.  I changed it in the post.  Any thoughts?

Hi and I have limited experience with the SIS graphics. If you have not tried Hardy 8.04 then you may, unless Intrepid solves some of your issues. 
You my try using the xfix option by booting into recovery mode, which is usually the second choice from the grub.

---

### Post by stotheg on 2009-02-21
> **overdrank said:**
> Hi and I have limited experience with the SIS graphics. If you have not tried Hardy 8.04 then you may, unless Intrepid solves some of your issues. 
You my try using the xfix option by booting into recovery mode, which is usually the second choice from the grub.

No luck.  Still have the same issue.  Any other ideas?  Maybe I should repost this question with with the proper heading?

---

### Post by aaamos on 2009-03-01
> **stotheg said:**
> No luck.  Still have the same issue.  Any other ideas?

Do you have compiz installed? I do, and had these video flicker problems, until [Compiz-Switch]("http://ubuntuforums.org/showthread.php?t=662926") fixed my problems... :)

---

