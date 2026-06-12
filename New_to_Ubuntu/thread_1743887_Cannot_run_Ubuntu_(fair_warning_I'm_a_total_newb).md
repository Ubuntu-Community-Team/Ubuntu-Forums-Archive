---
title: "Cannot run Ubuntu (fair warning I'm a total newb)"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Madmeeko on 2011-04-29
History: I found out about Ubuntu from a friend after my computer would not start. I have a Compaq laptop that run Windows XP Home Edition.
The error I get is windows\system32\config\system is missing or corrupt
 
My friend figured if I run Unbuntu I will be able to access the files on my computer and either run a virus scan or at least retrieve my files.
 
My Problem: I burned Ubuntu onto a disk and attempted to boot my laptop from the disk. It does not do it no matter what I do.
 
It seems that all the files downloaded and copied onto the disk correctly, so I'm not missing any. I've also tried to go into the recovery console and run Ubuntu from there but no luck with that either.
 
As computer savvy as I *think* I am, I really have no clue with this kind of stuff. Any suggestions would be most appreciated.
 
Thank you!!

---

### Post by prodo123 on 2011-04-29
> **Madmeeko said:**
> History: I found out about Ubuntu from a friend after my computer would not start. I have a Compaq laptop that run Windows XP Home Edition.
The error I get is windows\system32\config\system is missing or corrupt
 
My friend figured if I run Unbuntu I will be able to access the files on my computer and either run a virus scan or at least retrieve my files.
 
My Problem: I burned Ubuntu onto a disk and attempted to boot my laptop from the disk. It does not do it no matter what I do.
 
It seems that all the files downloaded and copied onto the disk correctly, so I'm not missing any. I've also tried to go into the recovery console and run Ubuntu from there but no luck with that either.
 
As computer savvy as I *think* I am, I really have no clue with this kind of stuff. Any suggestions would be most appreciated.
 
Thank you!!
Access the BIOS by pressing either F1, F2, F8 or F12 at the very first screen you see.
Go to the boot order/list and change your CD drive to be the first boot drive, usually using the -/+ keys.
Press F10 to save changes and exit.
The computer will automatically reboot into the CD.

As for your files, there's a good chance that the HARD DRIVE is corrupted. That would be PHYSICAL damage, not digital, so it's irreversible. The only way you can get data off a crashed hard drive is to salvage what you can, and whatever data you have lost is better off losing than paying cash for an IT professional to recover(which is possible only 50% of the time).

---

### Post by oldfred on 2011-04-29
Your error is from trying to still boot windows.

if prodo123's instructions on changing BIOS do not work, did you correctly burn the CD? Instructions here under #2. Best to use slowest speed your CD writer lets you use. Make sure you are installing/extracting the ISO to the CD not copying it as one file. 

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by th1rt3en on 2011-04-30
Can you give us a little more information on what happens when you boot?
Does it still try to boot Windows?
Do you get the initial screen prodo123 was referring to when you turn on your computer?

---

### Post by oldos2er on 2011-04-30
> **Madmeeko said:**
> It seems that all the files downloaded and copied onto the disk correctly, so I'm not missing any. 

The *.iso file has to be burned as an image: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Madmeeko on 2011-05-02
Yep I didn't have it burned as an image. Oops! Now it is working. Yay!! Still cannot access my c: but I'll post another thread on that one.
 
Thank you everyone for your help!!! :)

---

