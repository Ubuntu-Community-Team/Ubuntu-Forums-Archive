---
title: "stuck at grub rescue prompt after partition resize"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by le_phare on 2011-03-25
[B]My laptop has Windows Vista installed.
When I update Windows from Microsoft I use to loose my DVD/CD rom. 
(You may read about this on the internett, there is also answers from
Microsoft how to fix this problem, but it does not work.) So therefore I
only updated up to January 2011. After every update I look to see if the
DVD/CD player is present.
So thereafter I stoped the "automatic Windows Update".
Then I installed Ubuntu 10:10 and updated Ubuntu.
Last night Ubuntu was working well, also the [/B]** DVD/CD rom.**
[B]
This morning I was aware that my DVD/CD rom had disappeared again, (have not been working in Windows only used Ubuntu)! 
I then got the idea that the fault had become as I worked in Ubuntu. Now
I went to Windows and deleted all partitions for Ubuntu. Only Windows were
left.
Then I rebooted. Scream!!!!!!!!  Now I only get this message:
error: no such partition.
grub rescue> _

The DVD/CD player don't work (I have tried to boot from Ubuntu 10:10
disk. Don't work.
I have tried to go to grub> not succeeded.
Staying at "[/B]**grub rescue> _"****Caught **[B]here!!! -  I can't use sudo - how do I move to a rergular prompt? 

I have an other computer with Windows XP and  Ubuntu 10:10. Can this one help me?
Remember DVD/CD player are not working....

I need to use this laptop HP dv9605eo for use abroad.
[/B]

---

### Post by An Sanct on 2011-03-25
If the DVD/CD disappears, it is "inside" windows and you can still boot to your Ubuntu installation CD.

So put your installation CD in the tray, when prompted, select the "Test Ubuntu without making changes to the system", then after you reach the desktop, enter the terminal (press Alt+F2 and type "gnome-terminal" in the box)

Once there, enter this commands
```
sudo mount /dev/sda1 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda
```

This will reinstall GRUB (the boot loader) and make it possible for you to boot into windows.

After that, consider "fixing" the MBR with a Microsoft tool.

---

### Post by dgindra on 2011-03-26
I'm having the same problem. I accidentally deleted the partition created by ubuntu (which i'm  assuming had grub installed on it) and I am getting the same massage. I don't have any installation disks that for windows 7 or ubuntu. I'm a beginner and have no idea what to do... please help!

---

### Post by An Sanct on 2011-03-27
Welcome to the forums!

Well, to get your version of Ubuntu, go to the official [Ubuntu homeapge]("http://ubuntuforums.org/www.ubuntu.com") and follow the download procedure.

After that, make a Live USB, step by step how-to [here]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Then from the Live USB/CD reinstall GRUB, as mentioned in [my previous post.]("http://ubuntuforums.org/showpost.php?p=10599125&postcount=2")

---

### Post by Hedgehog1 on 2011-03-27
Another option is to start by booting into windows directly first, then reinstalling Ubuntu at your leisure:

To get your PC to boot directly into Windows again:

You need a Windows 7 / Vista emergency repair disk.  If you don't have a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

***The Hedge***

:KS

---

### Post by le_phare on 2011-03-27
Staying at "grub rescue> _"Caught here!!! - I can't use sudo - how do I move to a rergular prompt? 
I see only Grub rescue>_

The DVD/CD player don´t work or come up. 

What to write to leave Grub rescue>_ ??

---

### Post by Hedgehog1 on 2011-03-27
Please boot off of your LiveCD/LiveUSB.  I know that the DVD didn't show in windows, but it will still boot the PC.

Once in the live LiveCD/LiveUSB, you can install Ubuntu 'alongside' windows.

If you boot off a LiveUSB, you can download an ISO and burn a windows rescue CD - and then follow the pictures about to boot directly into Windows.

***The Hedge***

:KS

p.s. You may have to change your boot order in BIOS to get the PC to boot from the USB/CD

---

### Post by An Sanct on 2011-03-28
You may have to change the boot order (as Hedgehog1 said) or select a temporary boot option, that is displayed right after you turn the computer on. It is something like F2 or F8, follow the on screen instructions.

---

### Post by le_phare on 2011-03-28
Here is what I have done:
F10 	Main – Security - Systen Configuration – Diagnostics – Exit

Choosed:	Systen Configuration

Language				        English
Button Sound				Enabled
Dedicated Video Memory up to 	64Mb
Virtualization Technology		Enabled

Boot Options
CD – Rom Boot Enabled
Floppy Boot Disabled
Internal Network Adapter Boot Enabled

&#10146;	Boot Order

Atapi CD/DVD Rom Drive
USB Floppy
Notebook hard Drive
USB Diskett on Key
USB Hard Drive
Network adapter

F10

Setup Confirmation
Save configuration changes and exit now?

Yes			No

Pressed:  Yes

The Computer restarted and…
Error: no such partition.
grub rescue>_

I have tried both the recovery CD´s from HP and Ubuntu 10:10 in the cd tray.

---

### Post by le_phare on 2011-03-29
I have a removable disk and an other Computer where I went to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
On my removable disk I have create a USB drive....with UBUNTU 10:10
My Laptop have been sat to start from the removable disk.
Now I got the message" Operating system not found"
Can I get a solution using this removable disk?

--

Pressing F10 &#8594; Insert/delete 
NVIDIA Boot Agent 247.0541
Copyright C (2001 &#8211; 2005) NVIDIA  Corporation
Copyright C (1997 &#8211; 2000) Intel  Corporation
PXE-E61:	Media test failure, check cable
PXE-M0F: Exiting NVIDIA Boot Agent.
Operating System not found

The rest of the keyboard gives only:
Operating System not found

---

### Post by le_phare on 2011-03-31
Tried to start the laptop using a mobile DVD/CD player with Windows Vista recovery CD. The same result; 

Error: no such partition.
grub rescue>_

 The Ubuntu (10:10) installation disk gave the same result.
---

 tried to press Alt+F2 and type "gnome-terminal" in the box, nothing happened.

Never coming there, therefore I can´t enter this commands
Code:
sudo mount /dev/sda1 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda

---

### Post by le_phare on 2011-03-31
Re: stuck at grub rescue prompt after partition resize
Tried to start the laptop using a mobile DVD/CD player with Windows Vista recovery CD. The same result; 

Error: no such partition.
grub rescue>_

The Ubuntu (10:10) installation disk gave the same result.
---

tried to press Alt+F2 and type "gnome-terminal" in the box, nothing happened.

Never coming there, therefore I can´t enter this commands
Code:
sudo mount /dev/sda1 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda

---

### Post by le_phare on 2011-03-31
Ok, I have just taken the harddisk out and reformated it. Now the problem will be solved - thanks!

---

### Post by corncob on 2011-03-31
Is this grub rescue>_ a command line prompt?  If so, what are some of the commands it accepts?

---

