---
title: "NAS device for ubuntu"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by element42 on 2007-09-08
I'm going to buy an external NAS for home use. I don't need one of those massize 2tb RAID things, just 250gb-ish of network storage, but I'm a little worried as all the NAS devices I find seem to require windows. I'm guessing this is one of those times when what they mean is: bundled software requires windows, device will work fine with linux. Can anyone either reassure me that whatever I buy will be fine, or recommend me a good NAS, or perhaps just which brands to steer clear of?
thanks!

---

### Post by callan79 on 2007-09-08
> **element42 said:**
> I'm going to buy an external NAS for home use. I don't need one of those massize 2tb RAID things, just 250gb-ish of network storage, but I'm a little worried as all the NAS devices I find seem to require windows. I'm guessing this is one of those times when what they mean is: bundled software requires windows, device will work fine with linux.

Hi element42,

Good timing - I've just finished a heap of research on this topic!

Firstly, avoid Netgear storage devices, as they use a proprietary file system and a proprietary network protocol which requires Netgear software on your computer. Naturally, Windows only.

There are a bunch of other devices which also require client software to be installed on your PC, which is a foolish idea for a NAS - what if you want to share from work/school, or to your Linux machine or your X-Box?

I found a couple of suitable devices in the market place, but the choice for me was easy, I went with the [Repotec NA2310](http://www.repotec.com.tw/default.asp?pagename=Network_Storage/RP_NA2310.htm) which has a single SATA disk up to 400GB.

The NA2310 runs ext3 Linux file system, and actually runs Linux internally in its CPU. It runs SAMBA, CIFS and FTP for network sharing, so you just add a line to your fstab file and it mounts easily.

In fact, I'm using the NA2310 right now to back up 23GB of data from a customer's machine.

Just so you know, the other device I looked at was the [Hotway](http://www.hotway.com.tw) HD2, but this runs FAT32 and therefore has a maximum file size of 4GB which is not good.

If you need any more help please ask.

Cheers
Callan

Have fun!

---

