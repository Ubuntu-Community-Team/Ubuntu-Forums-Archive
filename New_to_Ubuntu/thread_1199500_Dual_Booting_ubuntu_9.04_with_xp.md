---
title: "Dual Booting ubuntu 9.04 with xp"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by rsiddharth on 2009-06-29
I want to dual boot ubuntu 9.04 with windows xp in my comp , for this I need the community's help . 

My system as it is mow . 

I have three primary partitions - c:\, for windows system files , d:\ drive is the  Windows system recovery partition and p:\ for Windows softwares and personal files . I also have ~18GB of unallocated space ( which I have kept it for ubuntu ) .  

I desire to install ubuntu in the unallocated space and leave the rest of the Hard drive untouched .I tried my hand  in  installing ubuntu side by side with Windows but the 'partitioning' step ( which comes after the step in which you configure your keyboard)
was confusing to me and I just quit the installation process . 

I request the ubuntu community to help install ubuntu 9.04  . 

my advance thanks for your help.:KS

--
I have at present installed ubuntu 9.04 ' inside Window ' which I presume to be slow and sluggish .

---

### Post by powel212 on 2009-06-29
In windows right click my computer and click "Manage"

in there you will find your partition editor.

create a new empty partition say about 10 gigs do not format it leave it as unalocated space.

or if you already have a partition you want to use for Ubuntu then just click it and set as unused unalocated unformatted space.

put in the ubuntu live cd and reboot.

when you get to the partition part of the install select install to "largest continuous free space"

this will put ubuntu into that empty partition we made earlier in windows.

don't touch the sliders just check largest continuous... and hit next.

I have done this numerous times and it always works perfectly.

Good luck and have fun

Powel

---

### Post by rsiddharth on 2009-06-29
I Thank you Powel . 

I have few more questions to clarify before I commence to install ubuntu 9.04 . 

* Will the performance of the computer come down if I run two Operating Systems ? .
* I also like to know about the difference in performance of the ubuntu OS when installed " as the only operating system " , "when dual booted with another OS like Windows XP " , and " When installed inside Windows " . 
* As i mentioned in my first post in this thread , I already have ubuntu 9.04 installed "inside Windows" . I would like to back up the system configuration and updates . Is there any software which can do the job for me ?. 

thank you 
R.Siddharth

---

### Post by Roadbloc on 2009-06-29
> **rsiddharth said:**
> I Thank you Powel . 

I have few more questions to clarify before I commence to install ubuntu 9.04 . 

* Will the performance of the computer come down if I run two Operating Systems ? .
* I also like to know about the difference in performance of the ubuntu OS when installed " as the only operating system " , "when dual booted with another OS like Windows XP " , and " When installed inside Windows " . 
* As i mentioned in my first post in this thread , I already have ubuntu 9.04 installed "inside Windows" . I would like to back up the system configuration and updates . Is there any software which can do the job for me ?. 

thank you 
R.Siddharth

1. Your computer's performance will not come down when dual booting two os's. You just have less hard disk space.

2. There are really no differences apart from i think a few power saving options and hibernating.

3. I use Nero BackItUp when i want to backup my xp machine.

hav fun with ubuntu. hope it all goes well.

---

### Post by rsiddharth on 2009-06-29
[quote=Roadbloc] 
1. Your computer's performance will not come down when dual booting two os's. You just have less hard disk space.
[/quote] 
I was under impression that it would indeed slow down my pc ! . 

[quote=Roadbloc] 
3. I use Nero BackItUp when i want to backup my xp machine.
[/quote]
Thank you for your suggestion Roadbloc , but I meant  a software which would back my ubuntu ( which I have installed ' installed inside Windows )  system up !.

---

### Post by rsiddharth on 2009-06-29
Yes! .  I have finally installed ubuntu with my windows XP :KS . I am able to perceive the performance difference in ubuntu between installing 'inside  windows ' and dual booting with Windows. 

Now i am facing a minor problem with NTP - its installed in my comp ( saw it in synaptic manager , the check box was green) but when I try it to enable it in " Time And Date Settings "  there is a pop up telling me install  NTP to enable Time and Date synchronization , when I click install NTP the dialog boxes closes and nothing happens . Can anyone help me with this .

---

