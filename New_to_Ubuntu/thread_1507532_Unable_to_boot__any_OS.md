---
title: "Unable to boot  any OS"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by ccunningham83 on 2010-06-11
I got a Asus UL20A-A1 about two months ago. As soon as I got it I installed a dual boot Ubuntu (10.04 32bit) / Windows 7 (64bit) setup. Everything was working fine, no problems. A few days ago my computer froze and I had to power it off manually. after that I get this error message:
 
[ 1.1770131] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)
 
No matter what I do I can't get any of my partitions to boot. I have searched on these forums and found many other people have this problem, but everybody could boot into their windows partition. On mine I get the Blue Screen of Death. I set mine up with /home on a seperate partition. I don't care if I have to re-install the OS, but I can't do anything from here
 
Everything I have read where somebody else has this problem, Either I have tried and it didn't work, or I don't understand. My scenerio seems unique in that I can't boot into windows, where everybody else can. 
 
Any help would be appreciated. I am not stupid when it comes to computers, but I am new to Ubuntu and would need simple instructions. It is very different.

---

### Post by Chronon on 2010-06-11
Can  you boot from the LiveCD okay?

---

### Post by ccunningham83 on 2010-06-11
I can't figure out how to boot from the USB. I have the .iso on a stick, but when I insert it and power on i get
 
```
boot:
```
 
I can tell it is looking for a kernel to boot from, but I don't know how to specify it properly.

---

### Post by NightwishFan on 2010-06-11
Try to install ubuntu to a flash drive using:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Mark Phelps on 2010-06-11
I would suggest you fix the booting into Win 7 first...

Since you probably did NOT use the Win7 Backup function to create and burn a Win7 Repair CD, go to the link below, download and burn the appropriate Win7 CD image, boot from that, and run Startup Repair three times -- that's right, three times:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Once you get Win7 booting working, come back and we'll let you know how to restore booting to Ubuntu.

---

### Post by ccunningham83 on 2010-06-12
Okay, I got UNetbootin installed on my girlfriend's laptop, Created a bootable USB. Tried both a Windows 7 64-bit .iso and an Ubuntu 10.04 .iso both of them freeze my laptop as soon as I select "Default" from the Unetbootin screen when it boots from USB. I know it is installed properly because I am typing from my girlfriends laptop using Ubuntu from the USB (which normally runs Vista,  but I am working to change that).

So to summarize:

Unetbootin will not let me boot from either OS.

---

