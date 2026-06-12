---
title: "Newbie Help!  error: no such device:"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by volkstech on 2011-05-21
Hi, I have installed Ubuntu 11.04 on my laptop and I love it. I just installed it on my older Dell Precision 670 and it installed great but after reboot I get This error: no such device: 3c00f307-7880-4a00-be06-16d0e984d493. Here is a screenshot. I typed exit to see if it would. It didn't. Any help would be great!! Thank you! 
[IMG]http://i53.tinypic.com/f54s90.jpg[/IMG]

---

### Post by jtarin on 2011-05-21
Can you boot with the Live CD? Personally I don't think 11.04 is going to work that well,if at all on that computer.

---

### Post by volkstech on 2011-05-21
I haven't tried using a live cd. I'll give it a go and post my results tomorrow. Thanks for the reply!

---

### Post by volkstech on 2011-05-23
Works with live. I found that during boot Ubuntu isn't seeing my SCSI host adapter then it errors out. I found this link that tells me to load the driver as a module at boot time. Being a noobie I have no idea how to do this so any or all help would be appreciated! Here is the link to the Ubuntu Manpage. [http://manpages.ubuntu.com/manpages/intrepid/man4/ahd.4freebsd.html]("http://manpages.ubuntu.com/manpages/intrepid/man4/ahd.4freebsd.html")
:guitar:

---

### Post by jtarin on 2011-05-23
You might need to write these instructions down unless you have another PC that has internet.
Use [this method (CHROOT)]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT") with Live CD to gain access to your installed system.Only proceed through number "7" (were not concerned about Grub installation).After you have executed number "7" then enter the command "lsmod" (without quotes). This will give you a listing of modules (drivers) that load at boot time. See if your module is listed(ahd). If not issue the command in the terminal "modprobe ahd" (without quotes).(You will not see any results from that command until you do the next step.) Now enter the command "lsmod" again and check to see if its loaded. Yes? If yes....go back to that link I gave you and continue with step number "11-15". You should have your driver loaded.

---

### Post by volkstech on 2011-05-23
Thank you so much for your help jtarin! I will give this a go as soon as possible and post results.

---

### Post by volkstech on 2011-05-23
I figured it out! All I needed to do was mess with my bios and disable my sata and pata drives besides my cdrom which is on pata-1!  It has installed but I need a driver for my ASUS EAH5450 SILENT HDMI video card to get a correct resolution. I have looked but there are no drivers that I can find for this card. Any idea where I can find a driver? Thanks for all the help!

:guitar:

---

### Post by jtarin on 2011-05-23
> **volkstech said:**
> I figured it out! All I needed to do was mess with my bios and disable my sata and pata drives besides my cdrom which is on pata-1!  It has installed but I need a driver for my ASUS EAH5450 SILENT HDMI video card to get a correct resolution. I have looked but there are no drivers that I can find for this card. Any idea where I can find a driver? Thanks for all the help!

:guitar:Enter the command "lspci" in a terminal and look for your video card and post the results of that here.

---

### Post by nerdy_kid on 2011-05-23
or enter
```

lspci | grep VGA

```
and you will get just the video card -- save you some searching ;)

---

### Post by jtarin on 2011-05-23
Good hint but sometimes more is less.

---

### Post by volkstech on 2011-05-23
Here is my reported video card after using  lspci | grep VGA in the terminal window. 

05:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]

That is not the right card!  :P  I guess it's reporting a compatible driver that willl work, I had it hooked up to HDMI but I wasn't getting any sound through the HDMI port and the resolution wasnt great as before when I was running windows 7. I figured it was a driver issue. So I swapped out the HDMI and used the regular monitor cable in the same card and analog sound out of the computer and everything works but obviously no 1080p.  I hope there will be a driver figured for my card so I can go back to luscious 1080p! 

Once again, THANK YOU!!

:guitar:

---

### Post by sandyd on 2011-05-23
> **volkstech said:**
> Here is my reported video card after using  lspci | grep VGA in the terminal window. 

05:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]

That is not the right card!  :P  I guess it's reporting a compatible driver that willl work, I had it hooked up to HDMI but I wasn't getting any sound through the HDMI port and the resolution wasnt great as before when I was running windows 7. I figured it was a driver issue. So I swapped out the HDMI and used the regular monitor cable in the same card and analog sound out of the computer and everything works but obviously no 1080p.  I hope there will be a driver figured for my card so I can go back to luscious 1080p! 

Once again, THANK YOU!!

:guitar:
what do you mean that's the wrong card?
If you installed the livecd version of ubuntu, you should simply be able to use the 'Hardware Drivers' (system -> administation -> hardware drivers) Utility to fetch the Video card drivers.

If you get bored, try using the xorg-edgers PPA. CEDAR support in gallium is going along nicely, and works quite well here.

---

### Post by jtarin on 2011-05-23
Please post the entire output of "lspci".

---

### Post by volkstech on 2011-05-23
Sandyd I just thought if it didn't list my card perfectly then I figured it was the wrong drivers. Like I said I'm just a noob here but I'm learning and loving every minute of it! I'll give that a try when I have a chance to tinker around. I'm in the midst of installing a virtual machine with VirtualBox so I can watch Netflix. This Ubuntu stuff is really cool!!


 :guitar:

---

### Post by volkstech on 2011-05-23
> **jtarin said:**
> Please post the entire output of "lspci".

Will do as soon as I finish installing my virtual machine. :)

---

### Post by volkstech on 2011-05-23
> **jtarin said:**
> Please post the entire output of "lspci".

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A
01:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B
02:0e.0 RAID bus controller: Adaptec AIC-7901 U320 w/HostRAID (rev 10)
03:0e.0 Ethernet controller: Intel Corporation 82545GM Gigabit Ethernet Controller (rev 04)
05:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
05:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
06:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
david@david-Precision-WorkStation-670:~$

---

### Post by jtarin on 2011-05-23
[Here's a read.]("http://www.linuxquestions.org/hcl/showproduct.php?product=4560")

---

### Post by volkstech on 2011-05-23
Yeah, I'm just using the VGA out to my 42 inch Toshiba LCD tv with analog sound from my pc to the tv. Seems to be working fine for what I need it to do. I guess you can't have everything you desire running an old pc with Linux. Now all I need is to get my Netflix running without a virtual machine! That VM sucks the resources right out of that old workstation! Makes for a choppy Netflix experience!

---

### Post by jtarin on 2011-05-24
> **volkstech said:**
> Yeah, I'm just using the VGA out to my 42 inch Toshiba LCD tv with analog sound from my pc to the tv. Seems to be working fine for what I need it to do. I guess you can't have everything you desire running an old pc with Linux. Now all I need is to get my Netflix running without a virtual machine! That VM sucks the resources right out of that old workstation! Makes for a choppy Netflix experience!Not the solution your looking for exactly but it has some potential and I think I might look into it further myself. [HERE]("http://www.innate-ideas.net/2010/10/watching-netflix-movies-in-vlc-on-linux.html")

---

