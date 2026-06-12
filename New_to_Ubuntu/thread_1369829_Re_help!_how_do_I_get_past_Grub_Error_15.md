---
title: "Re: help! how do I get past Grub Error 15?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Colochine on 2010-01-01
> **louieb said:**
> you can pickup Paddys sugestion once you get the **grub>** prompt  (thats what his 1st three steps did).

I am having the same problem and came across this thread. I tried typing find /boot/grub/stage1 and i get an error 15: File not found... any idea anyone

Mod Note: Here is the [thread]("http://ubuntuforums.org/showthread.php?t=1281533") being referred to.

---

### Post by stlsaint on 2010-01-01
if you get file not found than either you have a messed up install or just didnt instal ubuntu as you thought :D ...im gonna assume messed up install and ask a few questions first...please list out how your system is setup, IE: are you dual booting, laptop or desktop and if desktop how many drives are in system. Im thinking you will just have to install grub from installer via livecd. But first please answer questions for better assistance.

---

### Post by Colochine on 2010-01-01
I forgot my username and password so like an idiot not knowing anything about computers went into the BIOS setup utility and set a supervisor password and a HDD password thinking it was the same password needed to access my computer desktop. 

I have a dell mini inspiron 610 laptop. Just running Ubuntu or trying to that is.

When powered on first screen is a blue box in center that says Enter HDD Password [], once I enter that I get this error:
"[Minimal BASH-like line editing is supported. For the first word. TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]"

thanks for the help

---

### Post by mapes12 on 2010-01-02
Personally, unless there is an absolute security need to set BIOS passwords I would go back into BIOS setup and cancel them. Then to rectify the Grub Error 15 issue I would follow this HowTo: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

If that doesn't work I would make sure /home is on it's own partition ( [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866) ). This can be done via booting from a Live CD. That would leave 3 separate partitions:

/
/home
/SWAP

then reinstall Ubu making sure I selected "Manual" (or is it Advanced these days?) so that the installer only formatted / and I pointed it to where /home is located but NOT to format /home.

Should be back up and running in no time :guitar:

---

### Post by m4tic on 2010-01-02
> **Colochine said:**
> I am having the same problem and came across this thread. I tried typing find /boot/grub/stage1 and i get an error 15: File not found... any idea anyone

Mod Note: Here is the [thread]("http://ubuntuforums.org/showthread.php?t=1281533") being referred to.

hi mate, the thread you refferd to applies to previous versions of ubuntu. which one are you running

---

