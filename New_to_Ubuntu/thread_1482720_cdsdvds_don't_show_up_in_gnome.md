---
title: "cds/dvds don't show up in gnome"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by ghostofzuul on 2010-05-13
ever since i upgraded to lucid, whenever i put in a cd or dvd i can't see it. not on the desktop and not in "places" in gnome. 

i can open the discs using programs like k3b or vlc, but they still don't show up anywhere. 


any advice? 

thx.

---

### Post by cariboo on 2010-05-13
What is the output of:

```
dmesg | tail -n15
```

when you insert a CD/DVD?

---

### Post by Sealbhach on 2010-05-13
Some people have filed a bug report about this, you could subscribe to it and find out what they're doing about it: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092)

Others have reported the same problem on this forum

[http://ubuntuforums.org/showthread.php?t=1468035](http://ubuntuforums.org/showthread.php?t=1468035)

.

---

### Post by ghostofzuul on 2010-05-18
after a few more days with lucid i noticed something interesting. if i go to system>admin>disc utility, i can see both disc drives that don't show up in gnome, but not the media in them. when i try to burn a disc or watch a dvd, the program recognizes the disc but still not gnome.

---

### Post by ghostofzuul on 2010-05-18
> **cariboo907 said:**
> What is the output of:

```
dmesg | tail -n15
```

when you insert a CD/DVD?


[236104.566192] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[236104.566203] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[236104.566211] sr 1:0:1:0: [sr1] Add. Sense: Logical block address out of range
[236104.566221] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[236104.566237] end_request: I/O error, dev sr1, sector 0
[236104.572676] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[236104.572687] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[236104.572695] sr 1:0:1:0: [sr1] Add. Sense: Logical block address out of range
[236104.572705] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[236104.572721] end_request: I/O error, dev sr1, sector 0
[236104.579147] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[236104.579159] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[236104.579167] sr 1:0:1:0: [sr1] Add. Sense: Logical block address out of range
[236104.579177] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[236104.579192] end_request: I/O error, dev sr1, sector 0

---

### Post by The Boogster on 2010-05-19
Hi. Running clean install of Lucid. A similar problem happened to me. On first putting a DVD in it mounted,gave me a desktop icon and played. However after this it refused to recognise any DVD put in the drive and would not give me a desktop icon. Going to places allowed me to mount the disc but would not let me play it.
This problem was solved on my machine by changing the boot drive from cd to hard drive, which did not fix it, then disabling both my floppy drives in the bios. I do not have floppy drives installed.
Since doing this the drive now mounts, gives me an icon and plays the disc as you would expect.
This has been a permanent fix as it has continued to function through numerous reboots.

Hope this may help

---

### Post by ghostofzuul on 2010-06-23
this was fixed in an update via 'update manager' that i installed last week. sorry i wasn't able to notice the specific update.

---

