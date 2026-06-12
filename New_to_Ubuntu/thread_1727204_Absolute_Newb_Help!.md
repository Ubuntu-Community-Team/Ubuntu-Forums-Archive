---
title: "Absolute Newb Help!"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by dailyfare on 2011-04-12
Hello, I'm brand new to xubuntu and have a question. I installed xubuntu on my primary drive (80G) and everything was easy and straightforward. I have a secondary hd (40g) that I use for storage. How do I view the contents of the 40 g secondary slave? What would it be labeled if at all in the file system? Thank you!:D


"Forgive me, I'm a musician"

---

### Post by nothingspecial on 2011-04-12
It should be mounted in your /media directory

---

### Post by Hippytaff on 2011-04-12
> **nothingspecial said:**
> It should be mounted in your /media directory
 
To find out open a terminal and do```
cd /media
``` then```
ls -a
```
 
also doing```
df -h
``` should show up any mass storage devices.

---

### Post by dailyfare on 2011-04-12
thank you both for your assistance, i'm still messing around trying to find my way around the terminal. haven't figured it out yet but im sure i will...eventually! thank you for the quick response and ps wow this os is ridiculously faster than windows, just wow :)

---

### Post by akakingess on 2011-04-12
Also, you could set it up within fstab so that it automatically mounts upon boot. [Here]("https://help.ubuntu.com/community/Fstab") is a link to the fstab help files to walk you through how to add that partition to the fstab for future reference.  Good luck and welcome the the forums!!!

---

### Post by dailyfare on 2011-04-12
Thank you [akakingess]("http://ubuntuforums.org/member.php?u=814426") i will check it out for sure, sorry guys for the stupid questions..i've been spoonfed by windows for too long. :P

---

### Post by akakingess on 2011-04-12
There are no stupid questions, we are all here to help and we all had to start somewhere, you will quickly find out that as long as you follow the forum rules, we are all very happy to help and love the fact that people are beginning to adopt what we consider the future of computing ;)

---

### Post by XubuRoxMySox on 2011-04-12
Hi!

Welcome to Xubuntu awesomeness! Here's a nice graphical way to check: I'm using Natty (Beta), the not-ready-for-prime-time version so it may be a little different, but if it helps:

Click on _M_enu and choose _S_ettings. Then select _S_ettings Manager and _R_emovable Devices and Media. You can set it to show external media on the desktop when mounted (for example, when I plug a USB stick in, it's automagically mounted and appears on my desktop as an icon).

Hope that helps too,
Robin -
- whose Xubuntu experience has been so trouble-free that I hardly feel qualified to help! But I like to help if I can)

---

### Post by dailyfare on 2011-04-13
Thank you all for your assistance, I have figured out how to access the drive. I'm very pleased with my xubuntu experience, these forums are a great help and my pc is running better than it ever did with windows. Thanks!!

---

### Post by Hippytaff on 2011-04-13
Glad you managed to sort it. Can you explain how so others with the same issue can benefit.
 
Also remember to mark the thread as solved in the thread tools at the top of the page :-)

---

### Post by grahammechanical on 2011-04-13
I think that you can also do this through the file manager. When I open Nautilus by clicking Places I see a panel on the left. You should see the same. Do you see any icons that look like hard disks? Is there one marked 40 GB? Ah! I just remembered. You are using Xubuntu. I am giving you directions for standard Ubuntu. Things might be done differently in Xubuntu. Sorry.

Regards.

---

### Post by dailyfare on 2011-04-14
essentially i was just lost (haha) as seen above i found my hard drive in the media folder. simple as that ! /media is where it was located and i haven't had an issue since...so this was a case of user naivety. I do appreciate the ubuntu community, talk about quick assistance!

---

