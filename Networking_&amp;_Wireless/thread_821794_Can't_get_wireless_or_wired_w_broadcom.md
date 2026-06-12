---
title: "Can't get wireless or wired w/ broadcom"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by hlgladiator on 2008-06-07
Hi there, I know there are a ton of threads about this already as well as many sites with articles on how to get wireless working. Unfortunately, none have worked for me, and I've tried all I can find.

I have an HP dv6000 laptop with Broadcom wireless/wired. Neither works. I've tried installing the drivers but haven't had any luck. I've tried "apt-get install b43-fwcutter" but get an error message ("E: Couldn't find package b43-fwcutter".

I thought perhaps running update manager might help, but I can't connect to wired internet either. I tried taking my router of the equation and connecting directly to my modem, but that doesn't work either. 

Thanks in advance

---

### Post by cdtech on 2008-06-07
I've been having the same issues, although I can access my wireless. I still need to reset the modules for some reason yet.

These are the procedures I used to get mine working. I use wpa2 security on my router so my interfaces file is setup using wpa and dhcp..

Be sure you have ndiswrapper installed:
```
ndiswrapper -l
```

Should see something along these lines:
```
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

```
Next be sure you have the windows driver installed: System > Administration > Windows Wireless Drivers

Use version 011 of b43-fwcutter.
From within your home dir:
Download and extract the b43-fwcutter tarball then build it:

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
```

Use version 4.80.53.0 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware/2.6.24-18-generic"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

[COLOR="Red"]The firmware directory above is for my kernel, yours may differ.[/COLOR]

Then do:
```
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b43
```

I guess any information will be helpful to anyone. Like I said, this works for me but it's intermittent and I have to reload the modules as above to reset the wireless card.

I hope you have better luck with this....

---

### Post by Ayuthia on 2008-06-07
> **hlgladiator said:**
> Hi there, I know there are a ton of threads about this already as well as many sites with articles on how to get wireless working. Unfortunately, none have worked for me, and I've tried all I can find.

I have an HP dv6000 laptop with Broadcom wireless/wired. Neither works. I've tried installing the drivers but haven't had any luck. I've tried "apt-get install b43-fwcutter" but get an error message ("E: Couldn't find package b43-fwcutter".

I thought perhaps running update manager might help, but I can't connect to wired internet either. I tried taking my router of the equation and connecting directly to my modem, but that doesn't work either. 

Thanks in advance

You might try this link also:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

It will tell you how to install the b43 driver without an internet connection (although you do need an internet connection to download the firmware).  The b43-fwcutter package is in the Hardy live CD also.  You can also install NDISwrapper through the live CD (ndiswrapper-utils-1.9).

cdtech's post actually installs both the b43 firmware and ndiswrapper, but only uses the ndiswrapper method.  I would recommend trying to install b43 first and then trying NDISwrapper if it doesn't work.  I have no problems with cdtech's sugguestion, I just feel that NDISwrapper has extra steps and can create confusion if this is the first time at getting your wireless to work.

---

### Post by Unix_Slayer on 2008-06-07
> **hlgladiator said:**
>  I've tried "apt-get install b43-fwcutter" but get an error message ("E: Couldn't find package b43-fwcutter".


sudo apt-get install b43-fwcutter <=== you forgot the sudo. Also... you need to be plugged in wired to apt-get. Also, when you install, and reboot.... don't forget to unplug your cat5. Otherwise the wireless won't work.

---

### Post by hlgladiator on 2008-06-08
I've tried going through this thread:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

But I get stuck with the step where I type:

tar xfvj broadcom-wl-4.80.53.0.tar.bz2. The first issue is that it downloads as .tar.tar, not .tar.bz2 (I tried renaming it, that doesn't work). The second issue is that when I download it and try to open it on my windows PC, I get an error saying it's corrupt.

Any and all help is appreciated.

Thanks again

---

### Post by Unix_Slayer on 2008-06-08
> **hlgladiator said:**
> I've tried going through this thread:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

But I get stuck with the step where I type:

tar xfvj broadcom-wl-4.80.53.0.tar.bz2. The first issue is that it downloads as .tar.tar, not .tar.bz2 (I tried renaming it, that doesn't work). The second issue is that when I download it and try to open it on my windows PC, I get an error saying it's corrupt.

Any and all help is appreciated.

Thanks again

Type this in terminal window:

```
ark
```

Ark will open it, and you can extract where ever you like.

---

### Post by hlgladiator on 2008-06-08
Typing "ark" in the terminal outputs this message:

"The program 'ark' is currently not installed. You can install it by typing:
sudo apt-get install ark
bash: ark: command not found"

sudo apt-get install ark didn't work because I don't have an internet connection. I tried using sudo aptitude install ark, but that didn't work either.

Any ideas?

Thanks

---

### Post by Unix_Slayer on 2008-06-08
> **hlgladiator said:**
> Typing "ark" in the terminal outputs this message:

"The program 'ark' is currently not installed. You can install it by typing:
sudo apt-get install ark
bash: ark: command not found"

sudo apt-get install ark didn't work because I don't have an internet connection. I tried using sudo aptitude install ark, but that didn't work either.

Any ideas?

Thanks

It should be on the cd. Try:
```
sudo apt-cdrom install ark
```

---

### Post by hlgladiator on 2008-06-08
"sudo apt-cdrom install ark" => "E: Invalid operation install"

---

### Post by HunterThomson on 2008-06-08
I was helping someone set up broadcom 4306 just yesterday... Check it out on a walk though on how to set up Ndiswrapper but in the last two pages there is a better way to use b43fwcutter....

[http://ubuntuforums.org/showthread.php?p=5144120&posted=1](http://ubuntuforums.org/showthread.php?p=5144120&posted=1)

---

### Post by Unix_Slayer on 2008-06-08
> **hlgladiator said:**
> "sudo apt-cdrom install ark" => "E: Invalid operation install"


I'm having a weird night. Follow HunterThomson's thread. I will monitor the thread. But please.... You need a wired internet connection just to finish the setup. Would make it easier.

---

### Post by hlgladiator on 2008-06-09
[QUOTE=hlgladiator]I thought perhaps running update manager might help, but I can't connect to wired internet either. I tried taking my router of the equation and connecting directly to my modem, but that doesn't work either.[/QUOTE]

^^

---

### Post by Unix_Slayer on 2008-06-09
> **hlgladiator said:**
> ^^

hmmmm.... What service you running? It's not Verizon? is it?

---

### Post by geopearl on 2008-06-09
good site with vast info..........
======================
geopearl
Suffering from an addiction. This website has a lot of great resources and treatment centers. 
[http://www.treatmentcenters.org](http://www.treatmentcenters.org)

---

### Post by hlgladiator on 2008-06-09
Comcast. It used to work just fine, it stopped once I upgraded to 8.04

---

### Post by hlgladiator on 2008-06-10
Right, so I could be wrong but I'm still stuck with the one method, and with the others I need a wired connection, which also doesn't work for me.

Where do I go from here?

---

### Post by Ayuthia on 2008-06-10
> **hlgladiator said:**
> Right, so I could be wrong but I'm still stuck with the one method, and with the others I need a wired connection, which also doesn't work for me.

Where do I go from here?
Can you post your lshw -C network information?  It will help us identify your card.  As for which method you want to use, both do require you to download either an XP wireless driver (unless you have one already) or else you need to download the firmware.

NDISwrapper (ndiswrapper-utils-1.9) and b43-fwcutter are both on the liveCD.  If you download the firmware for the b43-fwcutter, you don't need to have a live connection.

---

