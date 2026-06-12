---
title: "Installation issues"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by karlo01007 on 2009-10-18
help! jumped the gun and installed.....lost everything windows. now ubuntu says I still don't have enough free disc space. I have an older dell with 1G mem and I can not find info about the rest of my computer like I used to with windows. I can't find how to defrag or know what programs to remove in order to make space to install "important security updates". any chance of retrieving my old windows and starting over?  if not where to now? also, some screens appear too large to see the lower portions, so I can not see "ok" or "cancel" icons. This may be too much all at once, any and all help greatly appreciated! new dunce, karlo.:(

---

### Post by beastrace91 on 2009-10-18
How big is your hard drive that you installed and do not have enough space to install updates? Did you give Ubuntu the entire hard disc or did you install it along side Windows? It sounds like you installed it along side Windows but did not give it enough room to fully function.

~Jeff

---

### Post by halitech on 2009-10-18
open a terminal and post the results of
```
sudo fdisk -l
```
```
lspci
```

what cd did you ise to install with? What version did you install?

---

### Post by karlo01007 on 2009-10-18
thanks for the super fast replies!  I'm pretty sure that install did not "dual boot" wjith windows.  I get the black screen at startup and no mention of windows. I cant find info about my computer like I used to clicking on"start" at bottom left and tooling around "system info". I dont know processor speed or the like... 1gig memory all I know. I went to "terminal" and typed in the two codes and ubuntu said "command not found" on both.  when I typed in sudo f disk-1 it came out with spaces and would not let me correct. looked like this.  sudo f di sk- 1 .I've tried the display preferences and view,edit and other sections to try to shrink screens to no avail. I used a friends home burned disc with the 9.04 version. thanks again for your thoughts and advice. karlo

---

### Post by halitech on 2009-10-18
if your screen resolution is off it may appear to have spaces but it might not really have them

on the first command, its -l (lowercase L) not the number 1 and the second is lspci (again, lower case L, not the number 1)

---

### Post by |Mitch| on 2009-10-18
An older Dell with 1 gig of ram? I would expect at least a 20 gig hard-drive, I seriously doubt you're out of free space. 

When you installed, did you select use full disk when you partitioned? That would have removed everything and you would have your full hard drive to work with. 

Unless you're computer is 8+ years old, I'm talking Pentium 1 days, you should have at least 20 gigs. My P1 233Mhz, back in the day had a 6gig hard drive.

I find this to be just a little too unbelievable.

---

### Post by karlo01007 on 2009-10-18
I'm better with cars, trucks and lawnmowers than these plastic fantastic boxes. I could re-wire the hard drive easier than type in a command or two. I dont know where they'd put one gazillion bytes of necco wafers! all I know is *I have successfully lost all my windows pics, documents, music, etc... I'm pretty mad at myself for being so quick at the send button. anyway...ubuntu installed. box tells me I should install security updates, then tells me I dont have room. tried "sudo apt-get clean*" command, same thing, weird space "cl ean" , will not let me backspace or re-type. would a fresh start with disc be a bad idea now that everything is gone anyway? I've got my mac, that I'm using as we speak, to communicate in any down time.  thanks again for any help or ideas! karlo

---

### Post by halitech on 2009-10-18
first off, take 10 and go grab a smoke/coffee/cola and relax. Before you do anything anymore drastic then you may have already done, we need to try and get some info to find out if you have actually lost your windows data. Even if you have, you may be able to recover it using testdisk which you can install but you may want to boot from the live cd and run things there to prevent any more damage being done.

try the commands again that I gave you earlier and see what we get for output and post it here.

---

### Post by karlo01007 on 2009-10-18
thanks again for stickin with me! I got "sudo fdisk -l" to show up in "terminal"  now I don't know how to post it in this forum because I'm using my mac laptop to talk to you and looking at the ubuntu dell screen next to me. I'm that green that I don't have any idea how to send it or if I have ubuntu set up to transport image.  first few lines as follows:  Disk /dev/sda: 80.0 GB 80000000000 bytes  255 heads, 63 sectors/track,9726 cylinders Units = cylinders of 16065 * 512 =8225280 bytes Di sk i dent i f i er: 0xd0f 4738c.........then there's some start-end numbers.. then "partition table entries are not in disk order"  sorry takes me so long to send back... typing skills not so good.  thanks again, karlo

---

### Post by karlo01007 on 2009-10-18
gotta sign out for the night... thanks again and hope I will learn enough to be a help to someone else down the line!!  I'll check back tomorrow. karlo

---

### Post by halitech on 2009-10-18
if it will help and you have a usb thumbdrive, you can run this instead
```
sudo fdisk -l >> ~/Desktop/fdisk.txt
```

that will save the info in a text file on your desktop that you can opy to the Mac and then open and paste for us. The important info is in what you didn't give us :)

---

### Post by karlo01007 on 2009-10-20
newbie nucklehead update!!!  somehow I allowed program to load six plus times on my computer after unknowingly  bypassed dual-boot.... need a breath-a-lizer on my keyboard and enter button! after consulting some all knowing ubuntu users at work who giggled and took my dell box under they're control...back in buisiness.  my advice to myself and anyone considering jumping into this operating system..... learn it first, backup every file important to you off your existing system, dual boot so you can go back, and give it a whirl!! I am amazed at the free stuff available right from the start.... so far so good, I am not sorry I lost windows by accident to gain this new operating system... thanks for welcoming me to this site and quick replies. as I learn I hope to give back to community! karlo.:)

---

