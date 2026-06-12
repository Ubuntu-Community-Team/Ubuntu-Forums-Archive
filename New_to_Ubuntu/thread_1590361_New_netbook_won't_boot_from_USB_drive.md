---
title: "New netbook won't boot from USB drive"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by pdxjayhawk on 2010-10-07
Can not install Ubuntu from usb drive on brand new Gateway netbook.

Hitting the F2 key does take me to the set up utility. In the "boot priority order" section I now have the following....

1) USB HDD
2) USB FDD
3) IDEO Hitachi HTS5**************300
4) IDE1
5) Network Boot : Atheros Boot Agent
6) USB CDROM

No matter what I do, the thing just seems to bypass it all and go straight to loading the existing copy of Windows 7 starter. 

??????????????????????????????????

---

### Post by sikander3786 on 2010-10-07
How was the USB prepared as an installation media? Which software did you use?

In some newer system bios, USB drives tend to show under the Hard Disk menu as an HDD. Did you see there?

---

### Post by lbrty on 2010-10-07
A USB flash drive or USB CD/DVD drive?

---

### Post by pdxjayhawk on 2010-10-07
PNY 2 gig USB stick. 

Created USB drive using the Universal USB Installer provided at ubuntu.com. 

The iso image seems to have gone on the drive perfectly. 

With Win 7 starter running, the drive and files all show up, so I don't think it's a problem with the USB stick or the download. 

Just can't seem to get the netbook to boot anything other than Windoze.

---

### Post by hamstermoon on 2010-10-07
Can you get into the BIOS (on my machine you press esc before Windows starts up) and change where the netbook boots from?

---

### Post by lbrty on 2010-10-07
Have you booted into BIOS by pressing F10 (usually) to enable booting from USB. Also, pressing the ESC key (on some machines) will allow you select which media to boot from.

---

### Post by pdxjayhawk on 2010-10-07
> **hamstermoon said:**
> Can you get into the BIOS (on my machine you press esc before Windows starts up) and change where the netbook boots from?

Isn't that what "boot priority order" does? 

It would seem to me that the machine should be looking at the usb drive first. 

But its not.

---

### Post by pdxjayhawk on 2010-10-07
> **lbrty said:**
> Have you booted into BIOS by pressing F10 (usually) to enable booting from USB. Also, pressing the ESC key (on some machines) will allow you select which media to boot from.

F10 results in the following...

Screen reads "Edit Boot Options" at the top. 

Then shows the following:

Edit Windows boot options for: Windows 7

Path: \windows\system32\winload.exe

Partition: 3
Hard Disk: 37f5140a

[ /NOEXECUTE=OPTIN   ]

And my choices are to hit enter for "submit" or ESC to "cancel"

This can't be the right area.

And pressing "ESC" instead of "F10" does nothing other than cause a very loud alarm tone of some kind.

---

### Post by lbrty on 2010-10-07
No, that is not the right place you want to be. Most machines will boot into BIOS by pressing F10.

Can you provide the exact model number (or service tag/etc) so I can look on Gateways website for the manual.

---

### Post by pdxjayhawk on 2010-10-07
> **lbrty said:**
> No, that is not the right place you want to be. Most machines will boot into BIOS by pressing F10.

Can you provide the exact model number (or service tag/etc) so I can look on Gateways website for the manual.

Gateway LT2106u

---

### Post by lbrty on 2010-10-07
Gateway is requesting a serial. For privacy reasons maybe you should go to the website and download the manual. Once you download the manual, upload the manual to your next message (if the forums allow it based on the size). If the file is too big, search in the manual for booting from a flash drive and how to get into BIOS.

Once you find that, please post your findings.

[http://support.gateway.com/support/drivers/](http://support.gateway.com/support/drivers/)

---

### Post by pdxjayhawk on 2010-10-08
> **lbrty said:**
> Gateway is requesting a serial. For privacy reasons maybe you should go to the website and download the manual. Once you download the manual, upload the manual to your next message (if the forums allow it based on the size). If the file is too big, search in the manual for booting from a flash drive and how to get into BIOS.

Once you find that, please post your findings.

[http://support.gateway.com/support/drivers/](http://support.gateway.com/support/drivers/)

Here's where we get in to problems. The manual says F2 takes you to the BIOS Utility. And I've already gone there and changed the boot order so that the USB drives are first. 

But it still goes straight to the Windoze boot.

---

### Post by k3lt01 on 2010-10-08
Connect the USB to the netbook and then start the netbook. Press F2 and go to the boot order screen. With the USB connected before you booted it it should show what USB option is actually the USB drive you connected earlier. Make it first boot option, save your new BIOS setting and reboot leaving the USB drive connected.

Let us know how you go.

---

### Post by pdxjayhawk on 2010-10-08
No luck. 

This machine has two usb ports on the left side of the device, and one on the right. I have tried the stick in all three ports and it goes to windows each time. 

Boot drive order is:

USB HDD
USB FDD
USB CDROM
IDEO Hitachi
IDE1
Network Boot

At this point I'm at a loss. 

I've installed Ubuntu on two desk tops, one with a CD and one with a USB drive, and never had these kind of problems. 

It just will not look at the USB ports for some reason without going to Windows first. 

What's the next step? Is there one?

---

### Post by k3lt01 on 2010-10-08
The USB drive was connected, and left connected, before you booted the machine to the boot order screen?

Have you tried the USB on another machine to see if it works on it? All I can suggest is you set it to one of the USB options and try each individual port until you get the one that works.

---

### Post by k3lt01 on 2010-10-08
You may want to [try this method]("http://ubuntuforums.org/showthread.php?t=1288604")

---

### Post by lbrty on 2010-10-08
Have you tried other functions keys (like F1, etc)?

---

### Post by pdxjayhawk on 2010-10-08
> **lbrty said:**
> Have you tried other functions keys (like F1, etc)?

Toward what end? I thought the idea was to get in to the BIOS so that the boot order could be changed so that the USB booted before Windoze. 

I've already done that and it still won't load.

---

### Post by pdxjayhawk on 2010-10-08
> **k3lt01 said:**
> The USB drive was connected, and left connected, before you booted the machine to the boot order screen?

Have you tried the USB on another machine to see if it works on it? All I can suggest is you set it to one of the USB options and try each individual port until you get the one that works.

The USB is fine. You can see the files, nothing looks to be corrupted. 

Anyone? 

Is the boot order (see above) wrong?

---

### Post by lbrty on 2010-10-08
Try these links below. Also, some BIOS may need you to manually enable USB support. Have you explored all the BIOS options instead of just changing the boot order?

[http://www.pendrivelinux.com/usb-bios-boot-options/#more-36](http://www.pendrivelinux.com/usb-bios-boot-options/#more-36)
[http://www.pendrivelinux.com/bios-usb-booting-tips-and-tricks/](http://www.pendrivelinux.com/bios-usb-booting-tips-and-tricks/)
[http://www.pendrivelinux.com/how-to-access-bios/#more-520](http://www.pendrivelinux.com/how-to-access-bios/#more-520)

---

### Post by pdxjayhawk on 2010-10-08
Thanks for the links. 

One of the pieces of advice there was to disable fast boot. On this system it's called "quick boot". I thought that might be the solution to the problem. 

But even doing that still won't force the machine to boot from USB.

I guess I'll just have to give up and live with Windoze 7 Starter. 

Really had hoped to be able to try the new 10.10 Unity for netbooks. 

Oh well.

---

### Post by lbrty on 2010-10-08
Did you explore BIOS for enabling USB support (previously stated)? I know there is a simple solution. When booting does a light on the USB flash drive have activity? I am certain we can get Ubuntu on your system if you have the patience and determination.

On another note, do you happen to have a CD/DVD drive whether it be an internal (from a desktop computer) or external? Because if you want to get creative, you can use an USB to SATA/IDE universal adapter (e.g. click [here]("http://cgi.ebay.com/USB-2-0-IDE-SATA-2-5-3-5-Hard-Drive-Converter-Cable-/120631396181") to view) and hook an internal drive via USB to your netbook and boot from there since the USB flash drive option is not working for you.

---

### Post by k3lt01 on 2010-10-08
> **pdxjayhawk said:**
> The USB is fine. You can see the files, nothing looks to be corrupted. That means nothing. I have burned cd/dvd and setup USbs that look fine yet will not work. You can navigate to files and even do a check to see if the files are ok yet the things will still not work.

Did you try my other suggestion?

> **pdxjayhawk said:**
> Anyone? 

Is the boot order (see above) wrong?Possibly. a USB stick should be seen as USB FDD not USB HDD which is what you have first on the list.

---

### Post by pdxjayhawk on 2010-10-08
Quick boot is disabled, and moved USB FDD to the top of the list.

Still no dice. 

Is there any way to literally force the machine to boot from a USB drive?

---

### Post by k3lt01 on 2010-10-08
2 questions for you (again).

1. Have you used this particular USB with its current setup on another machine?

2. Did you try the link I posted? This is the way I do it as the USB creator has never worked for me. I can use GRUB and have all 10.04 versions on one 16GB flash drive and choose which one I want to install from.

By asking these questions I am trying to see if the problem is with the machine or the USB flash setup. My gut feeling is it is the USB itself.

---

### Post by tux-curious on 2010-11-22
I know it's an old post, but I found this thread on Google and figured I might be able to help out the next person to get stuck here.

I run an eeePC 901 and for the life of me couldn't get it to boot from my USB stick. It didn't even pick up that there was a USB stick there, in the BIOS.

Then **I went to the hard drive boot order options. Turns out the BIOS had listed my USB stick as a hard drive**, instead of external media. 

Rebooted with it as my first "hard drive" and it went right to the USB stick like I was trying. 

I guess that makes sense because my 16GB USB key is bigger than the 4GB SSD in the netbook?

---

### Post by VraiChevalier on 2010-11-22
I have an Acer Aspire One netbook and had problems booting from USB with a "Data Traveler" USB flash drive. Very frustrating until I tried a Corsair Voyager USB flash drive and everything worked perfectly. 

Looks like your BIOS is not recognizing the USB drive as a bootable drive. I would either try a different USB drive or an external CD drive. You could also try booting a different computer with the thumb drive just to see if it is working.

Not all flash drives seem to play nice as bootable media.

---

### Post by ngrieb on 2010-11-23
Yes, the new netbook edition will not boot for me either, and I know that it should work because I have installed Ubuntu 9.10 and 10.04 on multiple computers including my this netbook using this FDD.

---

### Post by lbrty on 2010-11-23
Does the netbook recognize the USB device? In my experience with netbooks, I had trouble booting from a flash device until I figured out a different method. Insert the USB flash drive, turn on the machine, press F9/ESC/F12 (depending on your machines configuration), it should then prompt you to select a boot device or go into system configuration. If it takes you to select a boot device and the device is not posting then press Ctrl+Alt+Delete (by doing this rather than a hard reset, I believe Ctrl+Alt+Delete allows the machine enough time to recognize the boot device the second time) to restart the machine. Then from here press F2/F12 to boot into BIOS (depending on your machines configuration). In my experience when booting into BIOS, the machine will then recognize the USB flash device (or any other USB device as a bootable device). Then exit BIOS (change the boot order if necessary), and repeat the steps from the beginning. I have done this successfully on an ASUS netbook and an HP Mini.

---

### Post by castalla on 2011-04-04
I have exactly the same problem on a PB netbook.  F12 shows boot menu - usb HDD.  Selecting this starts syslinux but then the system stops with a flashing cursor ...

Used unetbootin and Universal USB installer - same issue with both.

The usb stick works on an older Acer laptop with f12 and usb HDD.

Is there a solution?

---

### Post by JaseP on 2011-05-01
Try using a powered USB hub. I had the same problem with some machines... A powered USB hub solved that problem.

---

