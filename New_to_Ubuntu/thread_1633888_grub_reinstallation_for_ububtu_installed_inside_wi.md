---
title: "grub reinstallation for ububtu installed inside windows7"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by showbhut on 2010-11-29
Hello,

I have ubuntu10.04 installed inside win7. After some updates on ubuntu,  when i next started the system, i was not able to boot into any of the  OS' because of a grub error.

I tried to rectify the problem by command prompt using windows cd, after which i was able to boot windows but not ubuntu.

Then i tried to reinstall grub using the live cd using this thread
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I reached nowhere and now windows and ubuntu both are not booting.I  don't know if I'm wrong but I think that this is not the correct way to  reinstall grub when ubuntu is installed inside windows, and that a  correct procedure might be the cure.

Please help.

Thank you

---

### Post by Mauldrick on 2010-11-29
Sometimes I find the best way to fix a problem like that is to start over. It sounds like you just installed so if you don't have anything to lose on Ubuntu I would just fix your MBR with the windows repair disk and reinstall Ubuntu. I have never installed inside of windows before so I don't really know how that works.

---

### Post by showbhut on 2010-11-29
> **Mauldrick said:**
> Sometimes I find the best way to fix a problem like that is to start over. It sounds like you just installed so if you don't have anything to lose on Ubuntu I would just fix your MBR with the windows repair disk and reinstall Ubuntu. I have never installed inside of windows before so I don't really know how that works.

I'm sorry man, would've done that if I wanted to. It is actually imperative that I recover. I've been working on it for a while.

---

### Post by drs305 on 2010-11-29
Most likely you have installed Grub to the mbr of your Windows drive. This, as you have found out, won't work.

The first thing to do is to restore the Windows bootloader. This is best accomplished with a Windows recovery CD using various recovery comamnds (fixboot, fixmbr, etc - I'm not a Windows guy).

An alternative is to use the Ubuntu LiveCD, install lilo and then have it write to the drive's mbr. If Windows is on sd**[COLOR="DarkRed"]a[/COLOR]**, the commands would be:

```
sudo apt-get install lilo
sudo lilo -M /dev/sd**[COLOR="DarkRed"]a[/COLOR]** mbr
```

Once you get back to a normal Windows boot, you can try 2 things.

1. Backup c:\wubildr and then copy c:\ubuntu\winboot\wubildr to c:\
Reboot and see if Wubi now boots.

2. If not, reboot, get to the Grub Ubuntu menu (probably the second time you see Ubuntu). Highlight the first menuentry in the Grub menu and press "e". Remove the entire "search" line using the DEL key. Once removed, press CTRL-X to boot.

3. If still unsuccessful, boot to the LiveCD. You will mount Windows, then Wubi after making mount points for them:

From the LiveCD Desktop (assumes Windows is sda1 - change to the correct device - sda1, sda2, etc):
```
sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sd**[COLOR="DarkRed"]a1[/COLOR]** /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
```

At this point, your Wubi files are accessible at /mnt/wubi.

Make grub.cfg writable, backup, then edit:
```
sudo chmod +w /mnt/wubi/boot/grub/grub.cfg
sudo cp /mnt/wubi/boot/grub/grub.cfg /mnt/wubi/boot/grub/grub.cfg.bak
gksu gedit /mnt/wubi/boot/grub/grub.cfg

```
Remove every line above the first "menuentry". (About 40 lines usually, perhaps more.)
Save the file. Do **not** update-grub.
Exit the LiveCD and reboot.


Let us know how it goes.

---

### Post by showbhut on 2010-11-30
heyy,

Thanx a lot! that worked perfectly fine :) Ubuntu rocks \m/ :D

---

