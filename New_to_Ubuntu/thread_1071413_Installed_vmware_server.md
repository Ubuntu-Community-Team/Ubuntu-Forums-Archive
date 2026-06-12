---
title: "Installed vmware server"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by halovivek on 2009-02-16
Hi
i have installed the vmware server and i have installed windows xp as second system to work with and it is doing good. 
but i am getting the very small to view . it is just the same size what the thread message posting table size.
Could you please tell me how to increase the full screen. I have tried by clicking the full screen but i could able to get same window size as this message posting screen.
i want to increase this to full screen. any help please

---

### Post by thegreenblob on 2009-02-16
You have to change the resolution in guest OS.

IIRC in XP it's right click on desktop-->properties-->settings.

---

### Post by halovivek on 2009-02-17
> **thegreenblob said:**
> You have to change the resolution in guest OS.

IIRC in XP it's right click on desktop-->properties-->settings.

Thanks i have done that. Now i could not get sound from the system.
i could not see the hard disk other than vmware one.

---

### Post by dmizer on 2009-02-17
The hard disk is not shared. They are separate.

You need to think of the XP virtual machine as a completely separate computer. So if you want to share files between Ubuntu and XP, you'll have to set up file sharing through Samba.

As for sound, make sure you have the sound module enabled for the guest in the VMware interface (you'll have to shut your Windows guest down to do this).

---

### Post by halovivek on 2009-02-17
Could you please tell me how to configure samba i am really new to this and i want use. 
How about the sound output from windows

---

### Post by dmizer on 2009-02-17
Sometimes it's really easy. Just right click on the folder you want to share, select "Sharing Options". Then click "share this folder", and make sure to allow other people write access, and guest access. Then "create share". The system should take care of the rest. Do not share your entire home directory. Share only one folder (like "Public"), and then put all your shared files in that directory. Things work better this way.

As for sound in XP, you'll need to shut down XP. Then open the VMware interface, click on your Windows virtual machine in your inventory, then "edit machine settings" > "add" > "sound adapter" > "next" > "finish"

Then power on your XP machine and let it install the sound drivers. Reboot when required, and you should have sound.

---

### Post by halovivek on 2009-02-17
> **dmizer said:**
> 

As for sound in XP, you'll need to shut down XP. Then open the VMware interface, click on your Windows virtual machine in your inventory, then "edit machine settings" > "add" > "sound adapter" > "next" > "finish"

Then power on your XP machine and let it install the sound drivers. Reboot when required, and you should have sound.

i could find this.

---

