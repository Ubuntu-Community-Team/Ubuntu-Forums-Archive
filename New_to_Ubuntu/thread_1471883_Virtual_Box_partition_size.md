---
title: "Virtual Box partition size?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by IanMcBride on 2010-05-03
Please forgive the really ignorant questions.

I am going to install Sun Virtualbox and load an old version of XP I have so I can use iTunes on this laptop (I just cannot get Rhythmbox or GTKPOD to play nice with my iPod).

Anyway, I started going through the setup and got to the part about partition size.  If iTunes will be living there (and nothing else) can I assume the partition needs to be at least the size of the iPod (20 gig) plus 10 for good measure (I have 200 free on this computer).  Or can it be smaller and have the music stored in my Ubuntu music folder?  

Also, can a VB partition be removed down the road, in case I get my iPod/Ubuntu situation figured out?

Thanks.

---

### Post by bdentremont on 2010-05-03
I've allocated 10GB to my Windows XP Virtualbox partition although the entire virtual hard drive file is actually only 5.3 GB at this time (it expands as the space is used).  Virtualbox can share folders with the host system, and, assuming you can specify where iTunes stores its data, I'd share a folder with the host system and tell iTunes to put your music there rather than on the virtual disk.  This could be the Ubuntu "Music" folder, in which case your music would be available to Linux if unencrypted.

I'll note that if you want to use connect iTunes to your Ipod, I believe that you need to use the proprietary edition of VirtualBox rather than the open source one that it in the Ubuntu repositories.  I've not used the USB support, but my sister has used it successfully to run Windows-only hardware on her Mac.

---

### Post by IanMcBride on 2010-05-03
Thanks for the info.

I tried doing a copy/paste from the iPod into the Music folder and it took a while but it looks like Rhythmbox is sorting through the files and making some sense out of them (they came over as JXDG.m4a, etc)  There are a lot of import errors, but I'm hoping that as it puts the files together most of the music will survive.

---

### Post by IanMcBride on 2010-05-03
Oh well.  Only 478 out of around 3000 songs made it in.  The rest showed 'Import Error' in Rhythmbox.  Tomorrow I try the VirtualBox

---

