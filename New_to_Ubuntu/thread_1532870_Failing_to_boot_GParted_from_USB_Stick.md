---
title: "Failing to boot GParted from USB Stick"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by Andavane on 2010-07-17
I'm trying to make a bootable usb stick on my old sony vaio VGN-S3HP which I purchased in 2004. Windows has long since gone, having been deleted on it.
I went into the BIOS and put "floppy" at the top of the boot list.

I made the usb stick which system>admin>startup disk creator and made the source the iso file gparted-live-0.4.8-6.iso. It made it successfully, but the pc won't boot from the usb.

Is the startup disk creator the correct tool for making usb bootable gparted, or will it only work with ubuntu distros?

The reason I want it is that I have a new HP Pavilion 11.6" notebook without cd drive. For the first switch-on I want to change the BIOS to boot into Gparted to look at the space allocation before the Windows 7 bumph starts doing its stuff. The idea is mainly to use Ubuntu, but to use the windows when sheers frustration prevents me (or certain things things that have to be run in Windows), i.e. using windows will be the last resort.

---

### Post by candtalan on 2010-07-17
> I went into the BIOS and put "floppy" at the top of the boot list.

I do not think this will be correct. If the bios in the machine allows booting from a usb device then you will also see in the bios setup, an option to boot from a usb device, in a similar way that you see an option to boot  from hdd or CD drive.

hth

---

### Post by bumanie on 2010-07-17
It is not correct to set the bios to from floppy, if you want it to boot from usb; you need to choose the boot from usb option (if there is one, a laptop that age may or may not have a usb boot option). As far as I know, the startup disk creator, used from within ubuntu will only work with ubuntu distro's, although there is a universal usb creator [here]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). But if you want to make a bootable gparted usb stick, best to to go to the [gparted site]("http://gparted.sourceforge.net/livecd.php") and create one from there - all the files to do so are there. If you want grub 2 on a usb stick, look [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB").

---

### Post by Andavane on 2010-07-17
Thanks to both of yous.
I set the BIOS to boot from floppy (there is no floppy slot in this machine) because before I purchase the HP, I went into the shop armed with Ubuntu 10.04 on a USB stick, and set the BIOS on that machine to boot from floppy, and it booted into Ubuntu fine. It was on that basis that I purchased it, combined with its discount due to being end of line, I presume.

I also went to the BIOS on this old Sony Vaio and looked in the BIOS as you suggested, and there is no reference to USB anywhere so yes you must be right, it's not possible to boot from USB on this machine.

Thanks for the suggestions on the USB stick making options. Off to investigate that now. :)

---

### Post by Andavane on 2010-07-17
> **bumanie said:**
> It is not correct to set the bios to from floppy, if you want it to boot from usb; you need to choose the boot from usb option (if there is one, a laptop that age may or may not have a usb boot option). As far as I know, the startup disk creator, used from within ubuntu will only work with ubuntu distro's, although there is a universal usb creator [here]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). But if you want to make a bootable gparted usb stick, best to to go to the [gparted site]("http://gparted.sourceforge.net/livecd.php") and create one from there - all the files to do so are there. If you want grub 2 on a usb stick, look [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB").

PS: I never heard of grub 2 (until just now!)

---

### Post by Jazzy_Jeff on 2010-07-17
First of all plug in the USB stick and then boot the computer up. Go into the bios and see if the USB stick shows up in the boot order. Then move it to the top. My computer does not show the USB stick until it is plugged in first. 2004 is not that old. It should have the option to boot from USB.

You can also use a program called [unetbootin]("http://unetbootin.sourceforge.net/") to make the USB image. That is what I use. Let us know if it works.

---

### Post by bumanie on 2010-07-17
I have used some computers that boot from a usb without setting an option for same in bios, others don't - have no idea why some do and others won't. re grub 2 - it is the default bootloader in the latest ubuntu releases.

---

### Post by oldfred on 2010-07-17
I have not used this but I think it lets you boot from other devices. Many are obsoleting the boot USB from floppy capability as most systems now can directly boot USB.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)


I really like grub2 on a USB as on one 4GB USB I installed grub2 and loopmount several ISO directly. Makes it really easy to update, just copy ISO and edit grub. I did it manually from these and Herman's site linked above.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

There have been several other scripts beside panticz and this one looks most complete and gives more options on what to install.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by Andavane on 2010-07-17
> **Jazzy_Jeff said:**
> First of all plug in the USB stick and then boot the computer up. Go into the bios and see if the USB stick shows up in the boot order. Then move it to the top. My computer does not show the USB stick until it is plugged in first. 2004 is not that old. It should have the option to boot from USB.

You can also use a program called [unetbootin]("http://unetbootin.sourceforge.net/") to make the USB image. That is what I use. Let us know if it works.
If I plug in the usb stick then boot the computer up, how can I go into the BIOS? I thought you could only see the BIOS before booting, or is there a way to see it when PC is booted?
I'm working round all these answers with great interest - learning slowly.

---

### Post by Jazzy_Jeff on 2010-07-17
> **Andavane said:**
> If I plug in the usb stick then boot the computer up, how can I go into the BIOS? I thought you could only see the BIOS before booting, or is there a way to see it when PC is booted?
I'm working round all these answers with great interest - learning slowly.

When you first start up the computer you have to hit a key to go into the BIOS. Each computer is different. I have to hit the Delete key on mine, some use the F keys. It should say as soon as you turn on the computer what to hit.

---

### Post by Andavane on 2010-07-18
> **Jazzy_Jeff said:**
> When you first start up the computer you have to hit a key to go into the BIOS. Each computer is different. I have to hit the Delete key on mine, some use the F keys. It should say as soon as you turn on the computer what to hit.

It's F2 with me, and if I do that with usb stick, there's not a sausage about the BIOS anywhere.

---

### Post by Andavane on 2010-07-18
> **oldfred said:**
> I have not used this but I think it lets you boot from other devices. Many are obsoleting the boot USB from floppy capability as most systems now can directly boot USB.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)


I really like grub2 on a USB as on one 4GB USB I installed grub2 and loopmount several ISO directly. Makes it really easy to update, just copy ISO and edit grub. I did it manually from these and Herman's site linked above.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

There have been several other scripts beside panticz and this one looks most complete and gives more options on what to install.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Oldfred, I'd love to be able to do this, but I have no idea what loopmounting is. Being a windows orphan, I'd have numerous questions to hurl.
;)

---

### Post by oldfred on 2010-07-18
I do not know what loopmounting is. It has something to do with grub2 being able to look inside a ISO and then use that to boot.

All I did was follow the procedures to install grub2, copy some ISOs. The biggest problem was getting the commands just right in the grub2 menu to make it work. For most common ISO examples are in above links. And the new script MultibootUSB does all of it without having to know much at all.

---

### Post by C.S.Cameron on 2010-07-18
Usb-creator is not the right tool for making a bootable Gparted USB disk.
(It only works with buntus)

MultiBootUSB works well with Gparted:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

