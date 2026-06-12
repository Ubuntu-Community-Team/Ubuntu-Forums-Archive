---
title: "Mounting XFS My Book World Edition Drive"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Macbook10.6 on 2009-08-27
So I seem to have a problem with my NAS no connecting me to one of my share folders. It is a linux setup with 4 partitions. A 950GB partition stores all of the data. I have the latest ubuntu booting from a live cd in my macbook. I launch gparted and it shows my drive, including the XFS raid I need to mount. I cant seem to get it mounted however. I've done some research but i dont understand what other people have done. I dont seem to have write access, so I cant create or save files. Could someone walk me through the steps of how to set this up?

---

### Post by beastrace91 on 2009-08-27
You can see the files on the partition but you cannot read/write to it if I am under standing correctly? I am willing to bet you are simply lacking permission to write to said drive. Try running ```
gksudo nautilus
``` in terminal and see if that is able to add/write files to said partition. If so you simply need to chown the partition for your normal user to be able to do the same. ```
chown <username> /pathto/mypartition
```

Let me know if you need any help with any of the above instructions.

~Jeff

---

### Post by Macbook10.6 on 2009-08-31
I'm sorry I didnt really explain my problem. I have ubuntu installed on my disk. I use sudo to gain admin access. How can I mount an xfs drive, what are the commands I should use?

---

### Post by Bucky Ball on 2009-08-31
Try:

sudo mount -a

That will mount anything and everything. You can use the same command in a terminal and replace '-a' with the name of the partition you are trying to mount.

You need to have a mount point set for it in /media and a corresponding reference in /etc/fstab.

When you say the latest version, what version is it exactly?

---

### Post by Macbook10.6 on 2009-08-31
Thanks Bucky Ball. I have version 9.04 installed on an external HDD and booted from my Mac. I made a directory in media called server. I dont know what to do with fstab? What do I add to it and how do I add to it. I use sudo in terminal to make changes, will that do? Thanks

---

### Post by Bucky Ball on 2009-08-31
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

That might help. You might also find some ideas here:

[http://www.google.com/custom?hl=en&client=pub-2070091971271392&channel=7979263543&cof=FORID%3A13%3BAH%3Aleft%3BCX%3A9%252E04%2520Start%2520Page%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BLC%3A%230000ff%3BVLC%3A%23663399%3BGFNT%3A%230000ff%3BGIMP%3A%230000ff%3BDIV%3A%23336699%3B&adkw=AELymgXxrKD2oLA8x1x9o6ouyWzIpUVMof2aWzEqVf5vEWq4hNK_chnEGSyeWDYRiP0WaKwfCVe7FvKr4A2PdsEF1owvxJra42oIOc_FnzxMObKvMl0hrTs&ie=ISO-8859-1&oe=ISO-8859-1&q=mount+external+usb+drive+ubuntu&btnG=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19]("http://www.google.com/custom?hl=en&client=pub-2070091971271392&channel=7979263543&cof=FORID%3A13%3BAH%3Aleft%3BCX%3A9%252E04%2520Start%2520Page%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BLC%3A%230000ff%3BVLC%3A%23663399%3BGFNT%3A%230000ff%3BGIMP%3A%230000ff%3BDIV%3A%23336699%3B&adkw=AELymgXxrKD2oLA8x1x9o6ouyWzIpUVMof2aWzEqVf5vEWq4hNK_chnEGSyeWDYRiP0WaKwfCVe7FvKr4A2PdsEF1owvxJra42oIOc_FnzxMObKvMl0hrTs&ie=ISO-8859-1&oe=ISO-8859-1&q=mount+external+usb+drive+ubuntu&btnG=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19")


Ps: From memory, that is a USB drive, yes?

pps: Ah ha. Now I get you. You are trying to boot Ubuntu from an external drive ... that is different. You need the grub to point to that drive. Get into your BIOS and set the boot order to 'boot from USB' probably. Have you tried that? Your machine is probably trying to boot from the internal drive and if there is no Grub on it, not much will happen.

---

### Post by Bucky Ball on 2009-08-31
[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

That is probably more what you are after. :)

---

### Post by Macbook10.6 on 2009-09-01
Hey I figured it out. If anyone else has a problem like this. Heres what I did.
I used fdisk-l to find out what partition I wanted to create
I then used cd to go to /media
I used mkdir to create a directory there for my mount point
Finally I mounted the partition with sudo mount -t xfs /dev/(partition label) /media/(mount point)

---

### Post by Bucky Ball on 2009-09-01
That is still not going to mount it at boot, if that is what you are wanting to do. For this you need to change the /etc/fstab file. :)

---

