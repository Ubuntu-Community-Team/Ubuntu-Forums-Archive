---
title: "Installing Jaunty w/ extra partition"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-06-05
Hi guys. I'm presently killdisking my old HD and am going to install Jaunty on it. 

It's a 40 gb (37.22gb) and I want to have a separate partition for storage. I am going to leave this HD in an external enclosure until I get my Ultrabay adapter for it. This will then be my second onboard HD.

While I'm waiting for my UBay adapter I'm going to leave this in the ext. enclosure and store mp3's on it hence the separate accessible partition.

Any suggestions on the manual installation? I have 17 mins of killdisk left. I have around 18 gb of music on DVD and want to make mods to the files. Thanks.

---

### Post by DBrocks on 2009-06-05
I'm not quite sure what you are asking. Are you making the 40gb into an external storage drive, or a bootable drive? If you are planning on installing Ubuntu on an internal drive, and use the 40gb for storage, then just install ubuntu, format the external disk to ext3/4, and plug the external drive into the computer. Is this what you mean?

---

### Post by emeraldgirl08 on 2009-06-06
Simple.

I have an 80gb 5400 rpm Windows XP Pro drive. I'm not shrinking and messing with that. I did one time and performance stunk after that. 

The other HD I have is in an external enclosure. It's an old 40gb 4200 rpm Hitachi Travelstar. My Thinkpad T30 will not allow me to boot from an external drive. I've tried to configure this in BIOS but there isn't anyway I can do it! 

The DVD Drive slot is called an Ultrabay. As far as I know there are four things you could use that bay for. An supplementary battery, an bootable HD, your optical drive, and an old floppy disk drive. I'm putting the old 40gig in that bay when the adapter gets here.

Now I'm getting my old HD prepped for it's new home in the Ultrabay. I've decided to install Jaunty on this HD. I've already done it so it's working and updated. I created an extra partition on the old HD. A FAT32. This will be the file migration between the two OS' when I get my Ultrabay adapter. It'll be easier for me to just drop "whatever" in that partition and use it in Windows or Jaunty. 

Hope that makes sense.

---

### Post by k_squired on 2009-06-06
For partitioning, you could try parted-magic.  

As I'm sure you know be EXTREMELY careful when working with drive partitions, unless you don't mind loosing/damaging all data on that disk!

Of course, consider other tools.

Good luck

---

### Post by DBrocks on 2009-06-07
Oh okay, I'm sorry. I didn't realize you were talking about a laptop enclosure. When you said enclosure, I figured you were talking about a HDD in a USB/FireWire/eSATA enclosure:popcorn:
Ubuntu's partition manager works just fine with windows. In all my experiences, I haven't lost anything to Ubuntu's partition manager (which I believe is gParted). Just be extremely careful what you are doing, and double/triple check before you hit "commit".

---

