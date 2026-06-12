---
title: "Hardy Heron install freeze on 80%"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Tchert on 2009-03-24
Dear Ubuntu gurus,

I am yet another noob who has had enough of Windows, cannot afford (and doesn't really want to conform to the hype) an Apple, and has decided to give Linux a crack. Having read a bit about it I am well aware and ready for the steep learning curve, command line, and yada yada yada... However Ubuntu managed to outsmart me even before I got to the above.

The system in question is my 5 year old laptop. It's specs are something in the region of 1.2Ghz, 512RAM and a broken Escape key. The graphical 8.04 cd would not let me boot a demo, nor will it let me partition - it always came up with errors before I got to the install menu. After clearing a lot of disk space, defragmenting and praying a little I finally overcame that, but, being a still hormonal 21 year-old, decided to go for broke and forgo partitioning, wiping by drive (yes, I backed up) and surrendering to the warm orange palette of 8.04.

Unfortunately, for the last 2 hours I have been staring at the install bar stuck at 80%, and I think it's set up camp. Sometimes if I listen carefully I can hear it laughing. My laptop has also seemingly given up, the hard drive is idle. Now I have no clue what I should do - I'm scared to eject the cd, I'm scared to reboot, I'm also scared of pigeons but that's another story.

I did some feeble searching and did not manage to find relevant enough info about this on these forums. May be I'm just retarded. Your help, good Sirs, will be muchly appreciated. 

Thank you in advance!

---

### Post by lavinog on 2009-03-24
Try checking the cd for defects. The cd is highly compressed, so a small defect can cause big problems.  Some users would recommend not burning the disk at the fastest speed.

Another thing do when having weird problems is to do a memory test (also on the live cd)
The memory test takes a while.
If the memory test passes (the test will loop forever so check on it every now and then) try resetting the memory module anyway.  Normally I don't see laptops suffer from dust on the memory bank, but I do see it all the time on desktops. Sometimes a stubborn desktop just needs the memmory reseated.

It also may be a good idea to do a disk check with a diagnostic cd from your harddrive manufacture. I recently had a computer suffer from a bad sector that caused windows to not boot...running the manufactures disk fixed that.

If all else fails, try the text based installer (the alternate cd)...sometimes the live cd just has issues.
Oh, and try the latest version of ubuntu (8.10) There are many improvements to it over 8.04
8.04 is a "long-term release" which means it will continue to recieve security fixes, but it does not mean that the software will be up to date. (You will find that software in the open-sourced world goes through many changes)

---

### Post by SikEnCide on 2009-03-24
Also because of the minimum ram you may find Xubuntu to be faster on your system the then the normal Ubuntu with Gnome. IT usesw XFCE which is much faster.

---

### Post by lavinog on 2009-03-24
> **SikEnCide said:**
> Also because of the minimum ram you may find Xubuntu to be faster on your system the then the normal Ubuntu with Gnome. IT usesw XFCE which is much faster.

512M should be sufficient for ubuntu though. Although if it is using shared memory for the video card, it might be close.

---

### Post by spcwingo on 2009-03-24
I had this problem on my laptop.  The only suggestions I can give is to look in the bios and try turning off sata (if it's a sata drive).  This won't actually turn off your HD, but will treat your sata drive as an ide drive (this is what I had to do to install).  Alternately, you can try the alternate install CD located here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

Scroll down until you find a mirror near you and download.  As recommended above check the downloaded iso before burning and don't forget to burn at a slow speed (around 4x) as an image.

---

### Post by Tchert on 2009-03-25
Thanks guys!

I am currently downloading alternate install CD of Xubuntu 8.10 (thus following most points you guys have recommended), so we'll see how it goes. I have very little idea about BIOS and what's in there, so I think Ill leave it for the moment. Hopefully the new cd and distro will do better.

Thanks again for all your help!

---

