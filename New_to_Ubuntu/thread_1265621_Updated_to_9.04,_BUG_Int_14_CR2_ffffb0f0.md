---
title: "Updated to 9.04, BUG: Int 14: CR2 ffffb0f0"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by PrairieShaman on 2009-09-13
Hey!

I updated my ubuntu machine to 9.04 and now when i boot from either live cd or from the hard drive i get the error:

BUG: Int 14: CR2 ffffb0f0
      EDI 00000000 ESI 00000000 EBP c0731f3c ESP c0731f1c
      EBX 00000046 EDX 0000000e ECX 00000000 EaX ffffb0f0
      err 00000000 EIP c0119891  CS 00000060 flg 000010046


there is a part that says Stack: with a bunch of numbers and letters too.. if you need that i will take the time to type it out but really dont want to. hahah.

Any help would be good!! ! thanks!

---

### Post by nhasian on 2009-09-13
probably the simplest solution is to do a fresh install of ubuntu.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554)

---

### Post by stderr on 2009-09-13
Which motherboard do you have?

---

### Post by PrairieShaman on 2009-09-13
the motherboard is an MSI NEO 875P or something... 

a fresh install of ubuntu is what I just did recently. the only reason I am using this old PC is to put all of my music/videos/documents onto a USB HD so I can grab them to my Mac with MacFuse.

if I have to reformat the drive I might as well just fill it with cans of butane and toss it in a fire pit somewhere because it's useless to me if I lose all my files. 

I was having trouble with permissions on the USB drive to copy the files, and then it told me to update. So i updated, and after the update I cant get on to get my files.

---

### Post by PrairieShaman on 2009-09-13
by the way - I have no idea what kernel is or how to edit anything? I cant do anything before I get this error.. how are these other people editting anything when you immediately recieve this error?

---

### Post by stderr on 2009-09-13
Firstly - don't worry about not being able to access your data. Even if you can't boot the drive at the moment, the data is still there. You can get another hard drive, install an operating system on it, boot it with this hard drive connected, and access all the data on there. Same thing goes for any live CDs that you can get to boot.

When you boot the PC, do you see the GRUB boot menu first? (It looks something like [this]("http://i28.tinypic.com/308llcy.jpg")).

---

### Post by 73ckn797 on 2009-09-13
I had monkeyed with a BIOS setting for Memory Hole and started having the same message and not booting to Ubuntu. If you have switched on Memory Hole, disable it. It does not appear that is what has happened to you but just thought that I would pass along my solution. It is an older MB with an AMD Athlon XP 2800 processor.

There are some bug reports related to this at Launchpad. Google this "Ubuntu BUG: Int 14". That is where I found my solution and also saw several reports of what you specifically are talking about. You may have to register on Launchpad.

---

