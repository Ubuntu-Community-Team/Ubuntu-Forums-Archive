---
title: "Boot problem! Select kernal."
date: 2010-08-27
forum: New to Ubuntu
---

### Post by Cameron Murray on 2010-08-27
I am running a Samsung N130 with a dual boot XP/Ubuntu netbook edition.

I was uninstalling software on Ubuntu, I clicked the wrong thing and  ended up removing the main menu on Ubuntu Netbook edition. After a  restart, I got presented with somthing about a linux kernal and choose  which kernal to boot (or somthing). I restarted and got to my normal OS  select screen.
 
 After rebooting I have had that screen twice, I'm really worried that I  might make the computer unbootable. I'm afraid I'm an Ubuntu noob and  that I think I've cocked it up. 
 
 I don't want to turn off my laptop for fear that it will never boot again. 
 
 Please Help, I don't want to think I've destroyed my computer, especially since I was given it very recently.
 
 I'm not saying that uninstalling the main menu has caused the issue, but it happened straight after.
 
 I really don't know where to go from here. Please Help! Any help would be much appreciated. 
 
 This is the second time I've managed to **** up a computer with Ubuntu  on it. I really can't lose XP on this computer. This may seem drastic  but I've been confronted by 2 problems way above my fixing skill  (withouthelp) in 2 days.

I'll update with the error message if my computer does turn off and I manage to get onto XP again.

---

### Post by Rubi1200 on 2010-08-27
What software were you uninstalling?

Go to Applications > Accessories > Terminal and post the output of```
 sudo fdisk -l
``` Lowercase L not 1.

What graphics card do you have installed?

Post the output also of this ```
uname -r
```

---

### Post by Cameron Murray on 2010-08-27
I was just uninstalling usless games which came default with ubuntu. I accidently clicked delete over the main menu button. 

I haven't installed the graphics card drivers for Ubuntu but I'm running the intel graphics media accelorator (GMA) 950. 

I'm on XP at the moment, I'm worried if I restart I may not be able to boot again.

Do you want me to boot linux and give you the answers to your questions?

I'm sorry total noob here. But hell will break lose if I destroy this computer, its brand new.

---

### Post by Rubi1200 on 2010-08-27
Rather than uninstalling things just hide them in the menu; you have to be very careful getting rid of stuff because some of it is deeply embedded.

Better to ask here first before doing things.

Anyway, do you have a Windows XP installation CD and/or an Ubuntu CD?
(I want to make sure we have an escape plan before proceeding ;))

---

### Post by Cameron Murray on 2010-08-27
I can make a Ubuntu usb boot disk. But this computer is a netbook, it doesn't have a disk drive and it didn't come with a boot disk.

---

### Post by Cameron Murray on 2010-08-27
This might sound odd, but previously with a different pc I have had a problem with the grub menu. So I deleted the partition with ubuntu on it and then reinstalled it with a usb boot disk.

Would that help? If so could you tell me if there are any dangers involved.

I'm really grateful that your helping me.

---

### Post by Rubi1200 on 2010-08-27
> **Cameron Murray said:**
> I can make a Ubuntu usb boot disk. But this computer is a netbook, it doesn't have a disk drive and it didn't come with a boot disk.
This is not my day; I just posted something in another thread that was already posted.
Daydreaming again...

Yes, you are right!

When was the last time you booted into Ubuntu and do you remember anything about error messages? And once you selected a kernel were you able to boot Ubuntu normally?

---

### Post by Cameron Murray on 2010-08-27
Update: I rebooted the netbook and found it booted normaly. I selected Ubuntu and now I'm talking to you using it =) The Os appears normal, although looking at the installed software page, the main menu isn't there.

As far as I can see there is no problem. All I can say is that I haven't done anything to fix it. 

The problem may still be an issue although I did not see the error message.

As I recall the message mentioned Linux and it wanted me to select a kernel. There was no list just a flashing hyphen, prompting me to type.

I hope you understand this more than I do, either way, I'm very grateful. I just hope it continues not to be an issue.

And I didn't manage to boot a kernal (well I didn't press or type anything) I simply restarted and the menu was back.

---

### Post by Rubi1200 on 2010-08-27
Ok, that is good news :D

Sometimes these things happen and then return to normal.

Anyway, if you do run into problems, you know where to come and ask.

---

### Post by Cameron Murray on 2010-08-27
Thanks, I love messing with computers, and I'm really enjoy messing with ubuntu, but like most people, hate it, when things don't work (happens alot to people who are used to knowing a lot about the Os they use, and try to something they don't, yet, understand the implications of).

I'm going to reboot a few times and make sure it behaves, I'll come back here i I have any issue.

Thanks =) 
Cameron Murray

---

### Post by Cameron Murray on 2010-08-27
Just to say, all is well, and thanks again =):D

---

### Post by Rubi1200 on 2010-08-27
You are more than welcome :)

---

### Post by Cameron Murray on 2010-08-27
Afraid I'm back =( I won't boot any more.

Error message:

SYSLINUX 3.85 2010-02-20 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:_

Please help =(

---

### Post by Cameron Murray on 2010-08-27
Update: After repeated restarts I managed to get to the Os boot menu. Both Os are running normally.

There is a problem, no dought about it.

---

