---
title: "Brand new to Linux"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by meleeman on 2010-03-25
Hello all, I'm new to Ubuntu now I'm usually not the type to post about a problem I have but after spending the better part of 2 hours trying to figure this out. I'm seeing this problem very common among version 9.10.

At best I can connect to my router (Netgear WNR834B) at 81% and at that it runs very slow. Most of the time it doesn't connect at all.
I'm connecting with a WPA & WPA2 Personal Security. Here is my lspci.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14) 
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01) 
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Thanks in advance for any help.

---

### Post by meleeman on 2010-03-26
If I'm trying to get drivers for a sony vaio vgn-nr120e what should i do?

---

### Post by Paqman on 2010-03-26
Poor connection over wifi could be a lot of things.

Are you dual-booting? If so, do you have a better connection on your other OS? If not then i'd look at environmental factors. Often cordless phones, microwaves, video senders, etc can interfere with wifi.

Otherwise it could be your wifi hardware. Or like you say drivers. What driver are you using? Check System > Admin > Hardware Drivers and if you've got alternatives, try switching to one of them.

---

### Post by ugm6hr on 2010-03-26
Can't find much on this, but it appears others have had similar issues:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442031](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442031)

---

### Post by meleeman on 2010-03-26
> **Paqman said:**
> Poor connection over wifi could be a lot of things.

Are you dual-booting? If so, do you have a better connection on your other OS? If not then i'd look at environmental factors. Often cordless phones, microwaves, video senders, etc can interfere with wifi.

Otherwise it could be your wifi hardware. Or like you say drivers. What driver are you using? Check System > Admin > Hardware Drivers and if you've got alternatives, try switching to one of them.

No I am not dual booting but i had window 7 on here before and it ran perfect I never had problems. I haven't had any problems with wifi interfere either.

When I search for drivers it doesn't show that I have any drivers installed.

---

### Post by Paqman on 2010-03-26
Possibly [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395565")? If so, it's a regression. Switching to an older kernel might sort it out for you.

---

### Post by kaldor on 2010-03-26
> **Paqman said:**
> Possibly [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395565")? If so, it's a regression. Switching to an older kernel might sort it out for you.

If you're new to Linux, you may not know what that means. Here's a brief explanation:

Kernel > OS > Programs

The kernel is the basic part of the OS; Linux is a kernel, not an OS.

Ubuntu is the OS based on the Linux Kernel

He means you should switch to an older version of the Linux kernel; the quickest and easiest way to do this with minimal problems would be to downgrade Ubuntu to version 9.04 or 8.04.

---

### Post by meleeman on 2010-03-26
> **kaldor said:**
> If you're new to Linux, you may not know what that means. Here's a brief explanation:

Kernel > OS > Programs

The kernel is the basic part of the OS; Linux is a kernel, not an OS.

Ubuntu is the OS based on the Linux Kernel

He means you should switch to an older version of the Linux kernel; the quickest and easiest way to do this with minimal problems would be to downgrade Ubuntu to version 9.04 or 8.04.

So the best to do your saying is to go back to 9.04 i'll try it see how it goes.

---

### Post by 2hot6ft2 on 2010-03-26
> **kaldor said:**
> 
The kernel is the basic part of the OS; Linux is a kernel, not an OS.

Ubuntu is the OS based on the Linux Kernel

He means you should switch to an older version of the Linux kernel; the quickest and easiest way to do this with minimal problems would be to downgrade Ubuntu to version 9.04 or 8.04.
Sounds kinda twisted around to me.
He/she said an older kernel, not an older OS.
When you boot up and see grub loading press the shift key and select a kernel with a lower number.
Say you have 
2.6.31-20
and
2.6.31-19

Choose the 2.6.31-19 kernel and see if it helps.
By default it will boot to the newest one.
You can install older kernels without installing an older version of ubuntu.

---

### Post by Paqman on 2010-03-26
> **meleeman said:**
> So the best to do your saying is to go back to 9.04 i'll try it see how it goes.

No, you can install different kernels without switching your version of Ubuntu.

Go to System > Admin > Synaptic and search for packages starting "linux-image-2.6.whatever". These are kernels. Try installing an older one, then reboot and make sure you pick that kernel from the Grub list. See if that sorts your problem, and if it does tell us and we'll sort out uninstalling the buggy one and making sure you don't get automatically upgraded to it later.

---

### Post by oleink on 2010-03-26
You may have to install a driver.  If thats the case you may not be able to get one without plugging into a router.  I could not search for one without plugging into router and needed wine to install it

---

### Post by 2hot6ft2 on 2010-03-26
To better clarify installing older kernels. In case it's needed.

There are 3 files needed for a kernel and I'll use kernel 2.6.31-19 as **an example** of the 3 files needed for it. These are the 3 files:
> linux-headers-2.6.31-19
linux-headers-2.6.31-19-generic
linux-image-2.6.31-19-generic
So to install a kernel such as the 2.6.31-14 **for example**
You could go to System > Administration > Synaptic Package Manager and search for 2.6.31-14 and mark these 3 packages for installation
> linux-headers-2.6.31-14
linux-headers-2.6.31-14-generic
linux-image-2.6.31-14-generic
And apply, then it would install that kernel and you could choose it when booting as described earlier.

Or you could install it using the terminal like this **example**.
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic
```
Then hitting Enter and your password when promted (which wouldn't be displayed) then Enter again.

---

### Post by meleeman on 2010-03-26
[IMG]http://i86.photobucket.com/albums/k81/meleeman5/Screenshot.png[/IMG]

So after pressing shift while booting up showed me one kernel so I came to Synaptic to see if i cold get a clear answer but all of this just confused me,

---

### Post by lien_meat on 2010-03-26
OH, I'm sorry man.  I have a atheros 5006 wifi card (similar to your ar5001), and I know what you are going through.  I'm currently using the broadcom 4311 that came in the laptop because the ath5k driver was nearly useless for me.

I reported serveral bugs every time there was a regression, but it only got worse.  The ar5006 used to work PERFECT using the madwifi driver, but now I have to compile it from source if I want to use it (cause I don't think it's in the repos anymore), so I just switched back to my old card, cause it works fine.

List of bugs I reported for this driver and my card:
Interface fails to come back up after resume from suspend.
Connections disconnect for seemingly no reason.
nm-applet asks for passwords even though it already has them.

NONE of these bugs happened with the madwifi driver, and they aren't an issue with my crappy broadcom card either.

I hate it that linux distros will use a less stable open source driver by default over a tried and true one.  It's silly, and terrible.

---

### Post by meleeman on 2010-03-26
> **lien_meat said:**
> OH, I'm sorry man.  I have a atheros 5006 wifi card (similar to your ar5001), and I know what you are going through.  I'm currently using the broadcom 4311 that came in the laptop because the ath5k driver was nearly useless for me.

I reported serveral bugs every time there was a regression, but it only got worse.  The ar5006 used to work PERFECT using the madwifi driver, but now I have to compile it from source if I want to use it (cause I don't think it's in the repos anymore), so I just switched back to my old card, cause it works fine.

List of bugs I reported for this driver and my card:
Interface fails to come back up after resume from suspend.
Connections disconnect for seemingly no reason.
nm-applet asks for passwords even though it already has them.

NONE of these bugs happened with the madwifi driver, and they aren't an issue with my crappy broadcom card either.

I hate it that linux distros will use a less stable open source driver by default over a tried and true one.  It's silly, and terrible.

I tryed madwifi it made it like 15% better, I currently have this laptop wired to the router this is making me doubt switchin my good laptop over to linux.

---

### Post by lien_meat on 2010-03-26
> **meleeman said:**
> I tryed madwifi it made it like 15% better, I currently have this laptop wired to the router this is making me doubt switchin my good laptop over to linux.

I completely understand.  If devs don't respect their users enough to acknowledge regressions that people report, then they don't deserve to have users.  It really is sad though, cause my card used to work flawlessly. Yours probably would too with 8.10..which is the last time mine worked really really well.

---

### Post by 2hot6ft2 on 2010-03-26
> **meleeman said:**
> [IMG]http://i86.photobucket.com/albums/k81/meleeman5/Screenshot.png[/IMG]

So after pressing shift while booting up showed me one kernel so I came to Synaptic to see if i cold get a clear answer but all of this just confused me,
Looks like you needed to scroll down some in your screenshot. And it would help if we knew what the number is for the kernel you have installed which would have a green check box next to it. It's less confusing when you search by the numbers.

I don't know why some have trouble with the AR5001 since I have a laptop that has it and has no problems.

EDIT: Looking closer at your list it's not the same as mine and I'm wondering why. I'm running 32 bit with an AMD 64 bit dual core processor.

Maybe it's because I'm running Ubuntu Ultimate Edition 2.5 which is based on ubuntu 9.10

---

### Post by meleeman on 2010-03-26
[IMG]http://i86.photobucket.com/albums/k81/meleeman5/Screenshot-1.png[/IMG]

There you go and yeah I have seen people who don't have a problem with this I'm just going to point the finger at sony they make there stuff compilcated.

---

### Post by 2hot6ft2 on 2010-03-26
> **meleeman said:**
> [IMG]http://i86.photobucket.com/albums/k81/meleeman5/Screenshot-1.png[/IMG]

There you go and yeah I have seen people who don't have a problem with this I'm just going to point the finger at sony they make there stuff compilcated.
That looks more like it. Now do a search for
2.6.31-20
since that's the most current right now

---

### Post by lien_meat on 2010-03-26
> **meleeman said:**
> [IMG]http://i86.photobucket.com/albums/k81/meleeman5/Screenshot-1.png[/IMG]

There you go and yeah I have seen people who don't have a problem with this I'm just going to point the finger at sony they make there stuff compilcated.

I'm sorry, but I don't think this is a sony issue.  Atheros cards have opensource drivers.  I have one that I bought for a different laptop, put it in this one.  It used to work great via madwifi, but it has regressed and now with ath5k it is terrible (on a dell laptop).  It's both ubuntu's fault for not making sure this stuff works (or using a stable madwifi driver instead of the buggy ath5k), and upstreams fault for not making ath5k as good as it SHOULD be.

---

### Post by 2hot6ft2 on 2010-03-26
> **lien_meat said:**
> I'm sorry, but I don't think this is a sony issue.  Atheros cards have opensource drivers.  I have one that I bought for a different laptop, put it in this one.  It used to work great via madwifi, but it has regressed and now with ath5k it is terrible (on a dell laptop).  It's both ubuntu's fault for not making sure this stuff works (or using a stable madwifi driver instead of the buggy ath5k), and upstreams fault for not making ath5k as good as it SHOULD be.
Madwifi is now ath9k, it was ath5k before becoming ath9k. Just so you know.
Madwifi is old

---

### Post by meleeman on 2010-03-26
[IMG]http://i86.photobucket.com/albums/k81/meleeman5/Screenshot-2.png[/IMG]

---

### Post by 2hot6ft2 on 2010-03-26
Mark these 3 for installation and click apply.
> linux-headers-2.6.31-20
linux-headers-2.6.31-20-generic **# the one with x86_64 at the end of the line**
linux-image-2.6.31-20-generic **# the one with x86_64 at the end of the line** 
Once it finishes it will want you to reboot.
Close Synaptic and whatever else is open and reboot it will load that kernel by default (automatically)

That should help clear things up for you. I don't know why you're still at kernel 2.6.31-14 but the newer kernels work better.

---

### Post by lien_meat on 2010-03-26
> **2hot6ft2 said:**
> Madwifi is now ath9k, it was ath5k before becoming ath9k. Just so you know.
Madwifi is old

Maybe so, but it worked.  I could care less if it is old.  It was functional...that's more than can be said with what ubuntu is using by default now...and it's a shame.

---

### Post by eggman03 on 2010-03-26
I thought Ubuntu was a Distro, not an operating system?

---

### Post by 2hot6ft2 on 2010-03-26
> **lien_meat said:**
> Maybe so, but it worked.  I could care less if it is old.  It was functional...that's more than can be said with what ubuntu is using by default now...and it's a shame.
I "think" more are being supported directly by the kernel now. That may be where the issues are.

---

### Post by 2hot6ft2 on 2010-03-26
> **eggman03 said:**
> I thought Ubuntu was a Distro, not an operating system?
Distro = Distribution
Ubuntu is both a distribution and an Operating system.

[http://en.wikipedia.org/wiki/Distro](http://en.wikipedia.org/wiki/Distro)

Time to go eat I'll check back after dinner.

---

### Post by meleeman on 2010-03-27
Well sorry for the long wait some things came up yesterday, That worked perfectly 100% connection everything loads quickly. Thank you very much.

---

### Post by 2hot6ft2 on 2010-03-27
> **meleeman said:**
> Well sorry for the long wait some things came up yesterday, That worked perfectly 100% connection everything loads quickly. Thank you very much.
Glad to hear it. You're welcome. Another satisfied member...
:popcorn:

---

### Post by oleink on 2010-04-01
yay! good stuff! I'm happy you got it working:p

---

