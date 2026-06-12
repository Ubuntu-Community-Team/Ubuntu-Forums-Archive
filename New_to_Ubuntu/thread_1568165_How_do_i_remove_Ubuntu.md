---
title: "How do i remove Ubuntu?"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by velzevool on 2010-09-04
It's been 2 days that i'm using ubuntu,and i wanna know how can i switch to windows.I don't have windows installed,i have only ubuntu.

Anyone can help?

---

### Post by MooPi on 2010-09-04
If you have a install disk for Windows that is all you should need. Other than that You'll have to give more details. If you have the Windows install disk ? If there is a restore partition on the hard drive ? Etc etc............

---

### Post by velzevool on 2010-09-04
I have the windows cd,i also saw somewhere that i ll be able to install from boot with the cd but nothin happens.

I also can't run the autorun of the cd i don't know why.

---

### Post by belkinsa on 2010-09-04
You must do it when you booting up the computer.

---

### Post by TBABill on 2010-09-04
You need to do a restart of the computer with the Windows CD already in the drive so the system will boot from the CD, not from Grub2 on your hard drive. If the system just boots into Ubuntu after that, restart again, but go into your bios (most machines have a screen that comes up and says something like "click F2 for setup" or "click F12 for settings". Follow whatever prompt your screen says and move the CD drive up in the list of devices so the computer will look to the CD FIRST for an operating system. If it finds none it will still just boot from the hard drive as normal. 

Once you move the CDROM up in the list to before your hard drive you should be able to boot directly from the Windows CD. If that doesn't work you likely have a bad CD.

---

### Post by velzevool on 2010-09-04
I did but nothing happens...i mean there isn't any text that says "press any key to boot from cd" like windows,it's just a black screen.

---

### Post by audiomick on 2010-09-04
You might have to re-format the drive to NTFS so the Windows Installer recognises it as a drive.

I am not sure about that, but I think Windows stuff is a bit funny about acknowledging drives that aren't formatted to Windows file systems.

You can use gparted on the Ubuntu Live CD to do this.

---

### Post by velzevool on 2010-09-04
Bill thanks i will try that.

---

### Post by jeight on 2010-09-04
You might consider duel booting. It is always nice to have all available options at any given time. Having both Linux and Windows is a win win situation.

---

### Post by Chris1274 on 2010-09-04
I just put windows7 back on a HDD that had Ubuntu on it (to send it back to the manufacturer, *not* to go back to windows!). You'll have to use the "advanced options" button at some point in the process to delete the existing partitions and reformat the drive in NTFS. I didn't have any trouble in getting the process going though.

---

### Post by velzevool on 2010-09-04
Sorry but nothing helped.Can someone give me a simple answer?As i said it's been 2 days that i am using this,so i don't know much..

---

### Post by MooPi on 2010-09-04
What brand of computer and model number? If we know these we should be able to tell you how to configure your bios to boot from CD.

---

### Post by Chris1274 on 2010-09-04
Check your BIOS to make sure that the boot order has CD/DVD first on the list.

---

### Post by velzevool on 2010-09-04
It's not first,and i don't know how to do it.The are 3 options and the only thing i can choose is "auto" on the 2 first and "enable/disable" on the last one.

It doesn't say something similar in its description though..

---

### Post by linux18 on 2010-09-04
I'd give a link to my usb windows installer, but thats not legal (then why did I make it?). 

We need to know this:

1. did the computer come with windows or ubuntu
2. what is the make and model of the computer
3. what is your bios settings
4. are you trying to install windows from an 'upgrade' cd, a 'hush hush' version, an OEM, or other

---

### Post by baddnady23 on 2010-09-04
When the BIOS is posting, there should be a brief moment where on the screen is says to hit F12 or some other key to go to the boot menu.  You have to be quick because it will only stay on the screen for 1 or 2 seconds.  There you can tell it to boot directly from the windows CD as long as it is in the drive.

---

### Post by Chris1274 on 2010-09-04
When you find your way into the BIOS, look for something along the lines of "boot sequence," which will be a list of the various devices you can boot from (HDD, USB, CD/DVD, etc.) Make sure that CD/DVD is first, save your settings, put your windows CD in the tray and restart your computer.

---

### Post by velzevool on 2010-09-05
> **Chris1274 said:**
> When you find your way into the BIOS, look for something along the lines of "boot sequence," which will be a list of the various devices you can boot from (HDD, USB, CD/DVD, etc.) Make sure that CD/DVD is first, save your settings, put your windows CD in the tray and restart your computer.

Exactly as you said,it was saying "boot sequence",thank you very much it worked. :D

---

