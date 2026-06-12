---
title: "Grub 2 Error. Deleted Windows XP. URGENT!!!"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by campb.andrew on 2010-12-21
HELP PLEASE! URGENT!

I installed ubuntu 10.04 on my dad's laptop. I had partioned the HD, placing the ubuntu partition in FAT32 format. The install went through without a hitch. But then it began to update and halfway through, it asked me if i wanted to update the grub file. Knowing nothing about Linux, but thinking that if i didnt update it with the rest, it would be outdated and wouldnt work, i clicked yes and clicked the only HD i saw there as the option, as the forward button was unhighlighted when it was unselected. The rest of the install went through fine....Then the computer restarted. :-( And instead of getting to choose my OS's, i got a grub rescue screen. IDK what to do. My dad is ok with ubuntu being on it without XP. But the CD drive doesnt work and it cant boot from a USB so i cant reinstall. How do i fix this???

Please help.

---

### Post by garvinrick4 on 2010-12-21
> **campb.andrew said:**
> HELP PLEASE! URGENT!

I installed ubuntu 10.04 on my dad's laptop. I had partioned the HD, placing the ubuntu partition in FAT32 format. The install went through without a hitch. But then it began to update and halfway through, it asked me if i wanted to update the grub file. Knowing nothing about Linux, but thinking that if i didnt update it with the rest, it would be outdated and wouldnt work, i clicked yes and clicked the only HD i saw there as the option, as the forward button was unhighlighted when it was unselected. The rest of the install went through fine....Then the computer restarted. :-( And instead of getting to choose my OS's, i got a grub rescue screen. IDK what to do. My dad is ok with ubuntu being on it without XP. But the CD drive doesnt work and it cant boot from a USB so i cant reinstall. How do i fix this???

Please help. What did you use to install with, use that same media and choose try ubuntu. When it boots up open a terminal and:
```
sudo fdisk -l
``` (lower case L)
post here.

---

### Post by alzie on 2010-12-21
How did you install Ubuntu?  Was it from the USB or CD? and is it a regular install or Wubi install?

---

### Post by campb.andrew on 2010-12-21
I used Wubi to install to that partition. From windows. I have ubuntu on a flash drive, but my BIOS doesnt have the capability to boot from a USB device. I cant boot into windows nor ubuntu cause i dont get to the screen to choose either. I turn on the computer, the computer name comes up, then i get the Grub Rescue screen.

---

### Post by campb.andrew on 2010-12-21
Wubi

---

### Post by bcbc on 2010-12-21
OK don't panic. Your computer contents are all still there. Just the bootloader has been replaced with Grub. (The bootloader is in the drive Master Boot Record and should contain the Windows bootloader, not grub).

But it concerns me that you say you cannot boot from CD. If this is really the case (sometimes it's not always obvious how to do this) - then your only other option to fix this is to boot from a USB - either a windows repair USB or an Ubuntu USB.

So - if you want to describe why you can't boot from CD we can try and help you, or else you'll have to use another computer to create a bootable USB.

EDIT: I just noticed that you said your computer can't boot from a USB.
If this is the case and you can't get your CD drive to work, you might have to remove the drive and fix it from another computer. Let's hope not.

---

### Post by alzie on 2010-12-21
The other option is if there is another working CD drive and plugging that into the computer.

<edit> how old is the computer?  You may be able to add the USB to the boot list if it is not too old

---

### Post by campb.andrew on 2010-12-21
Its an HP Compaq Presario 2400s. Six Years old.

---

### Post by alzie on 2010-12-21
I searched and came up here: 
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

At the grub prompt enter the following commands.  I've never done this so I can't guarantee results.
```
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```

<edit> I'm assuming you installed Wubi to drive C:

Hopefully this gets us into Ubuntu.

---

### Post by bcbc on 2010-12-21
Unfortunately that won't work. 

Your only option is to boot from a rescue medium and reinstall either the Windows boot loader (for XP only "fixmbr" is required, not "fixboot") or to install lilo. The following thread describes the problem and solution: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #1, Solution #1 or #2.

---

### Post by alzie on 2010-12-21
@bcbc I suspect you are right, but I'm hoping there is another option.

---

### Post by bcbc on 2010-12-21
I have an old compaq presario desktop - I'm pretty sure I've booted it from USB. I found this link about how to boot from usb from a presario 2100... maybe it will help
[http://www.ehow.com/how_6888480_boot-hp-compaq-presario-2100.html](http://www.ehow.com/how_6888480_boot-hp-compaq-presario-2100.html)

When I get home I'll check it out as well and post back.

---

### Post by bcbc on 2010-12-21
> **alzie said:**
> @bcbc I suspect you are right, but I'm hoping there is another option.

I tried this on my own computer - installed grub via wubi to see what would happen. Unfortunately it doesn't even allow you to access your partitions - there's no way to load any modules or any boot files. So it's pretty much a paper weight at that point.

I'd love to be proved wrong though... it would certainly make life a lot easier for wubi users.

---

### Post by sffvba[e0rt on 2010-12-21
The "convenience" of Wubi strikes again... if you could somehow boot from CD it would be a simple matter to fix using your Windows disc... other than than I hope some of the other posts come through for you!


404

---

### Post by alzie on 2010-12-21
I had a similar issue but I had access to my CD drive.  I know that Ubuntu can be booted from Grub but I'm not sure now.

---

### Post by alzie on 2010-12-21
[http://ubuntuforums.org/showthread.php?t=1639198&page=4](http://ubuntuforums.org/showthread.php?t=1639198&page=4)

drs305 offers this as a way to boot in post 33
```

insmod ntfs
set root=(hdX,Y)  # Your Windows partition. Example: set root=(hd0,1)
loopback loop(0) /ubuntu/disks/root.disk
set root=loop(0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

---

### Post by campb.andrew on 2010-12-21
> **alzie said:**
> [http://ubuntuforums.org/showthread.php?t=1639198&page=4](http://ubuntuforums.org/showthread.php?t=1639198&page=4)

drs305 offers this as a way to boot in post 33
```

insmod ntfs
set root=(hdX,Y)  # Your Windows partition. Example: set root=(hd0,1)
loopback loop(0) /ubuntu/disks/root.disk
set root=loop(0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```
I'm just an average user. And I know windows. Not linux. This is my first time using it. (What a first encounter...)I'll try your suggestions and see what works. I think i might just switch to ubuntu and leave windows alone. I really like it. If i can find a way to boot from a usb then i'll do that. (By the way, what's the average boot time?) I'm using PENDRIVELINUX as the bootmgr....i think.

---

### Post by campb.andrew on 2010-12-21
Is there a way to do a system restore from the bios in order to get the computer back to the state it was in before i did the update?

---

### Post by bcbc on 2010-12-21
> **alzie said:**
> [http://ubuntuforums.org/showthread.php?t=1639198&page=4](http://ubuntuforums.org/showthread.php?t=1639198&page=4)

drs305 offers this as a way to boot in post 33
```

insmod ntfs
set root=(hdX,Y)  # Your Windows partition. Example: set root=(hd0,1)
loopback loop(0) /ubuntu/disks/root.disk
set root=loop(0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```
That would only work from a grub prompt - not a grub rescue prompt. 
PS there's a couple of typos in that post. It should be
```
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)

```
EDIT: Although the code is unconventional and probably a typo, I just tried it and it works. (It still won't work from a grub rescue prompt).

@campb.andrew, 
I didn't have any luck booting my old presario from USB (but it's not the same model as yours, so hopefully you'll have better luck). If you get it booting, install lilo as described in that Wubi Megathread. That will fix it.
Good luck.

---

### Post by campb.andrew on 2010-12-21
> **alzie said:**
> The other option is if there is another working CD drive and plugging that into the computer.

<edit> how old is the computer?  You may be able to add the USB to the boot list if it is not too old
How would I do that? It's the latest version of the Phoenix BIOS.

---

### Post by alzie on 2010-12-21
When you first boot up you may see something like press F10 to enter setup.  That is what we would be looking for.  Otherwise, as the computer boots up try hitting F10 during the boot sequence to get to the bios screens.  It may use F1 as well.

Basically you'd be looking for 1st boot device, 2nd boot device...etc.  

You said the CD doesn't work, so I'd set USB first and HDD second. (if you can)

---

### Post by sffvba[e0rt on 2010-12-22
It would seem all measures needed is dependent on you being able to boot of either a CD/DVD or a USB... Good luck, hope you get it working!


404

---

### Post by campb.andrew on 2010-12-22
I've been there, and it says removable devices. I used pendrivelinux to create a bootable usb with a 1GB persistence, but that doesnt work.

---

### Post by campb.andrew on 2010-12-22
> **bcbc said:**
> That would only work from a grub prompt - not a grub rescue prompt. 
PS there's a couple of typos in that post. It should be
```
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)

```
EDIT: Although the code is unconventional and probably a typo, I just tried it and it works. (It still won't work from a grub rescue prompt).

@campb.andrew, 
I didn't have any luck booting my old presario from USB (but it's not the same model as yours, so hopefully you'll have better luck). If you get it booting, install lilo as described in that Wubi Megathread. That will fix it.
Good luck.
I got the model number wrong on mine. It's the same as yours. the 2100. I guess that means im out of luck on this one, unless i get the HD hooked up to a desktop somehow. :-(

---

### Post by theozzlives on 2010-12-22
> **alzie said:**
> When you first boot up you may see something like press F10 to enter setup.  That is what we would be looking for.  Otherwise, as the computer boots up try hitting F10 during the boot sequence to get to the bios screens.  It may use F1 as well.

Basically you'd be looking for 1st boot device, 2nd boot device...etc.  

You said the CD doesn't work, so I'd set USB first and HDD second. (if you can)

On my Dell, you have an option for "Boot Menu". The USB doen't show unless I have the USB plugged in. This may be the case with yours.

---

### Post by amjjawad on 2010-12-22
Have you tried this?
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

I have a very old laptop, 12 years old. CD-Drive is dead. No LAN and of course it can't boot up from USB. I tried Plop and it worked at a certain point then I had to format the HDD of that laptop and faced more complicated issues. Then, I had to connect the HDD to my PC and install from there. 

That laptop has Linux Mint Fluxbox 9 at the moment. It's Omni Book 4150 HP.

---

### Post by amjjawad on 2010-12-22
> **theozzlives said:**
> The USB doen't show unless I have the USB plugged in. This may be the case with yours.

It's the same case with everyone, I believe.

---

### Post by amjjawad on 2010-12-22
If your BIOS is capable of booting from USB, then when you plug your USB, restart and enter BIOS, you should have something like this:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

If not, then the CD-Drive is your only hope.


And this is the correct settings that you need to follow (just as a reminder)

[IMG]http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7126[/IMG]

---

### Post by bcbc on 2010-12-22
> **campb.andrew said:**
> I got the model number wrong on mine. It's the same as yours. the 2100. I guess that means im out of luck on this one, unless i get the HD hooked up to a desktop somehow. :-(

I don't have a 2100. I posted a link above with instructions on booting the 2100 from a USB, so follow it. Or follow amjjawad's advice. (It's pretty much the same instructions, but admjjawad has screen shots). Just set your boot priority so that the "USB devices" is higher than the hard disk.

e.g. 
1st boot device: [USB devices]
2nd boot device: [Hard Disk]

---

