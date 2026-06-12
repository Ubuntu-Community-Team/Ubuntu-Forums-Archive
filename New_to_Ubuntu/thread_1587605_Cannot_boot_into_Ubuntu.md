---
title: "Cannot boot into Ubuntu"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by dotdeb on 2010-10-03
Hello, I'm new to these forums, but lately I've been having a problem. Right now I'm using live CD to post because when I start up ubuntu, it does not go to the startup menu, instead it goes to a screen where it tries to mount my filesystem but it fails. It's called BusyBox v1.13.3. It asks me to type 'help' for a list of commands. the commands do nothing unless I type "return" it responds by saying 'Kernel panic - not syncing: Attempted to kill init' and never does anything. I seriously doubt this is malware. When I boot up into the live CD, whenever I try to mount my HDD it doesn't allow me to, it takes a while then pops up with a warning telling me that ubuntu cannot mount this drive. I have no idea what to do at this point. I believe my HDD may be messed up, it had smart errors for about a year until I deleted the partition and installed Ubuntu. Ever since then it ran perfectly fine (it's an old laptop) but I think the hard drive might have died. Is there any way I can check? I don't remember the terminal commands.

---

### Post by cgroza on 2010-10-03
I think it got corrupted. Any bad shutdowns or HDD acting crazy? This happened to me 2 times because my HDD is a piece of junk.

---

### Post by switch10 on 2010-10-03
It sounds like your hard drive has failed. You can use smartmontools to check the SMART values.

> 
sudo apt-get install smartmontools

sudo smartctl -H


---

### Post by andrewthomas on 2010-10-03
You should be able to check the disk out with System > Administration > Disk Utility

---

### Post by dotdeb on 2010-10-03
For the bad shutdowns, I guess this could qualify - I gave my bro my good laptop for college and thought I could live on my ubuntu laptop and gaming PC, and I'm used to tabbed browsing, especially in firefox, so forgetting that my laptop is about 4 years old, I try to keep a tab for email, tab for youtube, and many more tabs for many more sites. This causes the computer to freeze up constantly but I cannot stand going to different sites just to see something real quick. Yesterday I had a particularly bad freeze, nothing worked so I pulled the plug and went to bed. I woke up and this happened. Maybe me pulling out the plug was the problem?

---

### Post by dotdeb on 2010-10-03
I'm going to delete the partition and reinstall. Wish me luck.

---

