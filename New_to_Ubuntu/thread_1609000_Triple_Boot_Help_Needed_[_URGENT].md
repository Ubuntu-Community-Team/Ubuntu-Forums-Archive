---
title: "Triple Boot Help Needed [ URGENT]"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by D3SI on 2010-10-29
I am trying to get Triple Boot Working

Windows 7
XP
Ubuntu

i've used EasyBCD 2.0  to get Windows 7 and XP  to show up in Boot Menu but cant get Ubuntu to show up there

Attached Image - IMAG0064.jpg

shows Windows 7 and XP showing

-----------------------------

once i installed Ubuntu i noticed that Grub loader comes up as shown in IMAG0063.jpg

and if i select Windows Loader from there then i go to another screen where i get Windows 7 and XP

what do i need to do to get rid of Grub and have the second screen (IMAG0064.jpg)  with Ubuntu Listed?

Thank you

Edit: if you want to know how i installed it...

i already had Windows 7 and XP...

i installed Ubuntu today. loaded the CD by restarting the PC, Selected Partition Option (manual) - Selected the 139Gb partition and 9GB Swap..

and after that just normal options...

---

### Post by D3SI on 2010-10-29
I am trying to get Triple Boot Working

Windows 7
XP
Ubuntu

i've used EasyBCD 2.0 to get Windows 7 and XP to show up in Boot Menu but cant get Ubuntu to show up there

Attached Image - Picture 1

shows Windows 7 and XP showing

-----------------------------

once i installed Ubuntu i noticed that Grub loader comes up as shown in Picture 2

and if i select Windows Loader from there then i go to another screen where i get Windows 7 and XP

what do i need to do to get rid of Grub and have the second screen (Picture 1) with Ubuntu Listed?

Thank you

Edit: if you want to know how i installed it...

i already had Windows 7 and XP...

i installed Ubuntu today. loaded the CD by restarting the PC, Selected Partition Option (manual) - Selected the 139Gb partition and 9GB Swap..

and after that just normal options...

---

### Post by ivarn on 2010-10-29
Ok first of all. not my business but why would u waste space on having 2 copies of windows. Also, auto super grub will do the job for you.
Go to download.com and find it there.

---

### Post by darkstaar on 2010-10-29
I'm no expert at this but......

Ubuntu (Grub) has rewritten the master boot record. Running EasyBCD from Windows (again) should give you the results that you want by again rewriting the MBR.

---

### Post by D3SI on 2010-10-29
most of the time   some programs dont run on & even in Compatibility mode so i have XP is well

---

### Post by D3SI on 2010-10-29
yes that works and Grub goes away but i cant get Ubuntu to show up in options alongside with Windows 7 and XP

---

### Post by Quackers on 2010-10-29
Isn't there an option in EasyBCD to install a Linux system? I'm sure I saw that :-)

---

### Post by Quackers on 2010-10-29
It's not a good idea to post the same thread in 2 forums. At the very least it splits the replies.

---

### Post by Omnomnom on 2010-10-29
> **ivarn said:**
> **Ok first of all. not my business but why would u waste space on having 2 copies of windows**. Also, auto super grub will do the job for you.
Go to download.com and find it there.
Consider the possibility that he wants XP in case an old program isn't compatible with Windows 7?

---

### Post by uRock on 2010-10-29
Duplicate threads merged. Please do not create multiple threads on the same issue.

Regards,
uRock

---

### Post by D3SI on 2010-10-29
> **Quackers said:**
> Isn't there an option in EasyBCD to install a Linux system? I'm sure I saw that :-)


yes but i save the Config, Restart the PC and Ubuntu isn't listed on Loading Options

---

### Post by Omnomnom on 2010-10-29
While your at it, you might wanna remove the duplicate Windows 7 entries, one is recovery and one is the operating system, am I right?

---

### Post by D3SI on 2010-10-29
ok i started from Beginning..  Also Deleted XP (Can install later i guess)

now i have Windows 7 Only...

and this time am installing Ubuntu 10.10 using Wubi which is on Disc already..

I created new Partition and gave it (u) letters  as in Ubuntu

100GB  had to format it as NTFS  but will it be Ubuntu formatted later?  ex4 something like that?


lets see what happens...

---

### Post by darkstaar on 2010-10-29
Could this have something to do with EasyBCD not being compatible with the new Grub 2 that has been shipping with Ubuntu for the past year or so? I'm not sure if this is possible but very few linuxes actually use Grub 2 yet.

---

### Post by Omnomnom on 2010-10-29
Alright, what you should do, if your gonna use WUBI, is first of all, install the preferred windows. Then, install wubi with that one, on a single partition. Next, if you go start > right click computer > click manage. In Windows I mean. Then you want to click disk management, right click the windows partition, click resize. For XP I'd give at least 40GB, even more if you plan on long-term use. Format it as NTFS and give it a recoignizable drive letter that you can remember for later. Now reboot your computer with the windows disk in it and install over the.. Lets say X: is our partition we made earlier. Follow the instructions and choose X:.

Then, install superGRUB and easyBCD on ubuntu, then tweak the settings all you like. There might be an issue with Wubi though.. Just tell us how it goes.

---

### Post by uRock on 2010-10-29
> **D3SI said:**
> ok i started from Beginning..  Also Deleted XP (Can install later i guess)

now i have Windows 7 Only...

and this time am installing Ubuntu 10.10 using Wubi which is on Disc already..

I created new Partition and gave it (u) letters  as in Ubuntu

100GB  had to format it as NTFS  but will it be Ubuntu formatted later?  ex4 something like that?


lets see what happens...
Using Wubi usually installs within the C: drive with Windows, but as with normal Windows program installs, you may be allowed to install to the other precreated NTFS partition. Another good way to run ubuntu is within a VirtualBox within Windows, so that you don't need to reboot to use each OS independently.

---

### Post by NickJones on 2010-10-29
Install all of the OS's you want, and install Ubuntu last. Don't install it through Wubi, install it by booting off the CD.
If you install Ubuntu last it automatically detects the other OS's, and adds them to the MBR (Master Boot Loader, in Ubuntus case, this is Grub)

---

### Post by D3SI on 2010-10-29
i tried like i said in post #13 but something weird happened.

Once Wubi Installed the Ubuntu it asked me to restart PC.

so i did and after that Windows 7 loaded again and nothing happened :|   i sat there for 5 minutes and nothing...

so i deleted that again and installed it from CD by rebooting and select the space for Ubuntu there..

so now my main loader is Grub2  where i can select Ubuntu or Windows along with some other options

what cna i do to make that menu look neat?

thats the only reason i wanted Windows loader cause it looks really neat

any ideas?

---

### Post by Quackers on 2010-10-29
Some good info in here

[http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+menu+items](http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+menu+items)

---

