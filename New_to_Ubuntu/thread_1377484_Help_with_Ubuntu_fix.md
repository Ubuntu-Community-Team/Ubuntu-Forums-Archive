---
title: "Help with Ubuntu fix"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Rigit63 on 2010-01-10
I can't get into Ubuntu on a dual boot. It seems to have been corrupted. I tried to uninstall and reinstall as I having nothing to lose data wise. But when I reinstall it gets to the end and says access denied and fails. When I try to boot into Ubuntu it says something about a windows dll missing or soemthing like that. I just want to start over. Wipe Ubuntu out completely and start fresh. Is there any way to do that other than reformat?

---

### Post by spiky001 on 2010-01-10
Did you load ubuntu from within windows ( start win load ubuntu) or boot from cd?

---

### Post by sandyd on 2010-01-10
did you perform any windows updates lately?
if you have, there is a fix somewhere... lemme look it up.

---

### Post by bodhi.zazen on 2010-01-10
> **Rigit63 said:**
> I can't get into Ubuntu on a dual boot. It seems to have been corrupted. I tried to uninstall and reinstall as I having nothing to lose data wise. But when I reinstall it gets to the end and says access denied and fails. When I try to boot into Ubuntu it says something about a windows dll missing or soemthing like that. I just want to start over. Wipe Ubuntu out completely and start fresh. Is there any way to do that other than reformat?

Are you dual booting or using wubi ?

Can you please be more specific on the "Access denied" error message - Windows or Ubuntu ?

You message about a missing dll suggests you are running wubi.

---

### Post by Rigit63 on 2010-01-10
> **spiky001 said:**
> Did you load ubuntu from within windows ( start win load ubuntu) or boot from cd?

I installed from within windows. I am dual booting. I can't recall the exact dll error message I can try to duplicate the error if need be. I'm not sure how to install from CD without hurting windows. Perhaps if I did that it would fix the issue?  I have to keep windows as well and dual boot. I have a home network to run several computers on and I need windows in order to do that since the other machines are windows boxes. It makes it easier. If I copy the iso to a cd will that start the install when booting from cd or do I have to extract the files and then do it? I really want to figure this out because I like Linux better than windows.

---

### Post by NoaHall on 2010-01-10
> **Rigit63 said:**
> I installed from within windows. I am dual booting. I can't recall the exact dll error message I can try to duplicate the error if need be. I'm not sure how to install from CD without hurting windows. Perhaps if I did that it would fix the issue?  I have to keep windows as well and dual boot. I have a home network to run several computers on and I need windows in order to do that since the other machines are windows boxes. It makes it easier. If I copy the iso to a cd will that start the install when booting from cd or do I have to extract the files and then do it? I really want to figure this out because I like Linux better than windows.

That isn't dual booting - it's called Wubi. I recommend you uninstall it from the Programs menu in Windows, then boot from the live disk, then install side by side with Windows.

---

### Post by spiky001 on 2010-01-10
Yes just burn the image to disc then you can boot off of it giving you a dual boot

---

### Post by bodhi.zazen on 2010-01-10
Well, yes we need to know the exact error message you are getting to advise a fix.

Most likely you will need to boot yoru Windows restore CD/ DVD and fix your windows boot files , regardless of what you do with Windows / wubi / or dual booting.

---

### Post by NoaHall on 2010-01-10
> **bodhi.zazen said:**
> Well, yes we need to know the exact error message you are getting to advise a fix.

Most likely you will need to boot yoru Windows restore CD/ DVD and fix your windows boot files , regardless of what you do with Windows / wubi / or dual booting.

To do this, open a command prompt through first running ```
cmd
```then in the command prompt```
sfc /SCANNOW
``` and then put in your windows disk when asked.

---

### Post by Rigit63 on 2010-01-10
> **NoaHall said:**
> To do this, open a command prompt through first running ```
cmd
```then in the command prompt```
sfc /SCANNOW
``` and then put in your windows disk when asked.

Working on it now. Can someone please tell me exactly what dual boot is please? I thought it was being given a choice of operating systems at boot but apparently that's not it. I didn't think you could run 2 operating systems at a time.

---

### Post by NoaHall on 2010-01-10
> **Rigit63 said:**
> Working on it now. Can someone please tell me exactly what dual boot is please? I thought it was being given a choice of operating systems at boot but apparently that's not it. I didn't think you could run 2 operating systems at a time.

Yes, it is choosing at boot time, but if you install Ubuntu while Windows is running, this installs inside Windows as if it were just another application, which isn't a true dual boot setup. This is bad because it relies on Windows, and just as you have found, if Windows has a problem, then your Wubi install will have a problem too.

---

### Post by bodhi.zazen on 2010-01-10
> **Rigit63 said:**
> Working on it now. Can someone please tell me exactly what dual boot is please? I thought it was being given a choice of operating systems at boot but apparently that's not it. 

No, that is exactly what dual booting is.

With Ubuntu there are tow methods of installation.

One is wubi, which is to install Ubuntu within Windows.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

In theory , wubi is "easier" although it sometime causes more problems that are harder to solve.

The othe rway is to burn the ubunt iso to a CD, reboot to teh CD, partition your hard drive, and install Ubuntu.

[GraphicalInstall - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by spiky001 on 2010-01-10
Dual boot is the opton to choose which OS you want to use at start up, also some games work better in windows also  you can keep a familier OS while switching

---

### Post by sdowney717 on 2010-01-10
be careful. when you install ubuntu in a new partition, the new partition is carved out of the windows partition. the installer will resize the windows ntfs partition to create an ext4 ubuntu partition. The danger is you could wipe out the windows partition completely which if you dont follow the installer directions will happen.
but it is best to do this as ubuntu can then run in a nice native ext4 partition space and sit next to windows.

a WUBI install just creates a large ubuntu file on the existing windows partition.

---

### Post by Rigit63 on 2010-01-11
OK I reinstalled within windows so I could get the error messages. The first one is in a file located in a folder that starts with doc~ I don't know where to find a documents folder that has the~ sign in it. The second error message I get is when I try to boot into Ubuntu and it says windows could not start because the following file is missing or corrupted reinstall a copy <windows root>\system32\hal.dll
Any ideas on how to fix that?

---

### Post by Rigit63 on 2010-01-11
OK I did some searching and found a Microsoft article that addressed the hal.dll error thing at startup. As I suspected a corrupted boot.ini was to blame. I have edited the boot log and the issue is gone now and windows boots without giving me an option to run Ubuntu since it isn't installed any more. I tried reinstalling wubi and got the following error message.
Access denied for information on this error see c:\docume~1\mark\locals~1\temp\wubi-9.04-rev128.log I looked at this log but honestly I'm not sure what to make of it. I've since done a search for anything Ubunu and deleted it along with registry entries that I felt ok deleting. I'm not as aggressive deleting registry items so there is still stuff there. Most of it referencing the cd drive evn though there isn't a cd in the thing. I can reinstall and then post the contents of this file but it is rather lengthy. I'll do if you guys can help.

---

