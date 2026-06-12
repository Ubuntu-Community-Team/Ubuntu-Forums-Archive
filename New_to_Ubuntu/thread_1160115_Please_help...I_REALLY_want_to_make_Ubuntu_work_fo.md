---
title: "Please help...I REALLY want to make Ubuntu work for me."
date: 2009-05-15
forum: New to Ubuntu
---

### Post by charon2112 on 2009-05-15
Hi everyone.  I am very new to Linux and Ubuntu, but I am already in love with it.  I am, however, having two catastrophic problems that I hope someone can help with.  

#1 -- Ubuntu is not detecting my Dynex network card, so no internet.  

#2 -- When I try to properly install Ubuntu without a partition (my preferred way if possible), instead of just booting and playing around with it from the CD...the installation fails at the very end.

I didn't have much luck in searching for these problems on the forums, I apologize for my 'rookie' mistakes.  If anyone can help, I would be grateful.  I really want to use Ubuntu.  I love it, and the whole philosophy behind it.

Many thanks to all.

Rick

---

### Post by Kosimo on 2009-05-15
> **charon2112 said:**
> Hi everyone.  I am very new to Linux and Ubuntu, but I am already in love with it.  I am, however, having two catastrophic problems that I hope someone can help with.  

#1 -- Ubuntu is not detecting my Dynex network card, so no internet.  

#2 -- When I try to properly install Ubuntu without a partition (my preferred way if possible), instead of just booting and playing around with it from the CD...the installation fails at the very end.

I didn't have much luck in searching for these problems on the forums, I apologize for my 'rookie' mistakes.  If anyone can help, I would be grateful.  I really want to use Ubuntu.  I love it, and the whole philosophy behind it.

Many thanks to all.

Rick


Ok, let's start from the begging: 

Which version are you trying to install? 

Are you using CD or a flash drive?

What computer are you currently using?

---

### Post by charon2112 on 2009-05-15
Thanks for responding... :)

It's 9.04

a burned the ISO to a DVD actually, which seemed to work so far for running from the CD drive.

The PC is a home build, running Windows XP SP2.  Athlon XP 2600+ processor.

my NIC card details are:  dynex dix-e102 pci 10/100mb network adapter

> **Kosimo said:**
> Ok, let's start from the begging: 

Which version are you trying to install? 

Are you using CD or a flash drive?

What computer are you currently using?

---

### Post by Metallion on 2009-05-15
I did a quick search and came up with this:

> Somehow, when the WOL is disabled in the Windows driver, Windows will disable the card after every shutdown or reboot, making it uninitializable for Linux.

The work-around to this it to check the option box "Wake-On-Lan after shutdown" in Windows device manager.

source: [https://answers.launchpad.net/ubuntu/+question/42429](https://answers.launchpad.net/ubuntu/+question/42429)

---

### Post by WinterMadness on 2009-05-15
you might have to go online(with windows or something) to find the driver for your dynex. save it and then install it in ubuntu

second when you burn a disc make sure you burn it at the slowest speed. What you describe is quite common, and its almost always because of the speed issue.

---

### Post by charon2112 on 2009-05-15
> **Metallion said:**
> I did a quick search and came up with this:



source: [https://answers.launchpad.net/ubuntu/+question/42429](https://answers.launchpad.net/ubuntu/+question/42429)

Oh, thank you!  I'm at work right now, but will try that when I get home this evening...

---

### Post by Kosimo on 2009-05-15
> **Metallion said:**
> I did a quick search and came up with this:



source: [https://answers.launchpad.net/ubuntu/+question/42429](https://answers.launchpad.net/ubuntu/+question/42429)

Good answer, give it a try by selecting the "Wake on Lan" and let's see if works.

Ask here any question you may have!

---

### Post by charon2112 on 2009-05-15
> **Metallion said:**
> I did a quick search and came up with this:



source: [https://answers.launchpad.net/ubuntu/+question/42429](https://answers.launchpad.net/ubuntu/+question/42429)

I don't see a 'wake-on-lan after shutdown' in the device manager in the network adapter properties.  Is it somewhere else?

---

