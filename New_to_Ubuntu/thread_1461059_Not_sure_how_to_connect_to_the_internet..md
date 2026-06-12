---
title: "Not sure how to connect to the internet."
date: 2010-04-23
forum: New to Ubuntu
---

### Post by kajiotaku on 2010-04-23
I just installed Ubuntu 9.10 and I'm not sure how to connect to the internet.  I am using Netgear WG311 v2 Wireless PCI Adapter.  I clicked on the icon that shows the signal level (there are no bars just so you know) and it said there are no network devices available.  I also right clicked on it and went to edit connections but I'm not sure what to do there either.  Thanks in advance.

[Solved]

---

### Post by arrrghhh on 2010-04-23
> **kajiotaku said:**
> I just installed Ubuntu 9.10 and I'm not sure how to connect to the internet.  I am using Netgear WG311 v2 Wireless PCI Adapter.  I clicked on the icon that shows the signal level (there are no bars just so you know) and it said there are no network devices available.  I also right clicked on it and went to edit connections but I'm not sure what to do there either.  Thanks in advance.

One thing to check, when you right clicked on the icon, instead of "Edit Connections" was there an "Enable Networking" or "Enable Wireless"?

Also, does the card have some lights on it, and are they dim or lit?

---

### Post by kajiotaku on 2010-04-23
> **arrrghhh said:**
> One thing to check, when you right clicked on the icon, instead of "Edit Connections" was there an "Enable Networking" or "Enable Wireless"?

Also, does the card have some lights on it, and are they dim or lit?

I right clicked again and it had "Enable _N_etworking" and it was already checked.  I unchecked and checked it again to see if it would do anything.  The card has no lights.

---

### Post by spiky001 on 2010-04-23
As you have just installed have you updated yet if not connect etho lead do all updates then see if your wireless works check all hardware drivers installed as well

---

### Post by arrrghhh on 2010-04-23
> **kajiotaku said:**
> I right clicked again and it had "Enable _N_etworking" and it was already checked.  I unchecked and checked it again to see if it would do anything.  The card has no lights.

Ok, if it was already enabled that's fine.  Can you do an lspci in the terminal and paste the output?

---

### Post by kajiotaku on 2010-04-23
> **spiky001 said:**
> As you have just installed have you updated yet if not connect etho lead do all updates then see if your wireless works check all hardware drivers installed as well

I have not updated yet.  I checked Hardware Drivers and it says that no proprietary drivers are in use on this system.  Is it just that I need to find and download the driver for my wireless adapter?

---

### Post by spiky001 on 2010-04-23
You need to connect via etho cable 1st

---

### Post by kajiotaku on 2010-04-23
> **arrrghhh said:**
> Ok, if it was already enabled that's fine.  Can you do an lspci in the terminal and paste the output?

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
02:0b.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
02:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0e.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)

---

### Post by kajiotaku on 2010-04-23
> **spiky001 said:**
> You need to connect via etho cable 1st

I physically can't.  The cable is nowhere near my desktop.

---

### Post by spiky001 on 2010-04-23
sorry either way to get the drivers for wireless you will need internet

---

### Post by kajiotaku on 2010-04-23
> **spiky001 said:**
> sorry either way to get the drivers for wireless you will need internet

Can I just use my laptop and a flash drive or does my desktop need to do it?

---

### Post by pastalavista on 2010-04-23
You should have booted to the desktop of the live CD (Try Ubuntu without changes) to see if the wireless worked. If it did, open System/Administration/Software Sources and enable using the CD as a repository. Then check the Hardware Drivers tool again. If it didn't work from the live CD, you will need to connect to a wired (ethernet) connection to download the required driver module package.

---

### Post by arrrghhh on 2010-04-23
A network cable would make it easier to get drivers onto it, but it is possible to get them over with a usb key...

However, I don't recognize that card.  I'll have to do some research.

IF you can get it connected with a hardline, it would make the whole process a lot less painless.

---

### Post by kajiotaku on 2010-04-23
> **pastalavista said:**
> You should have booted to the desktop of the live CD (Try Ubuntu without changes) to see if the wireless worked. If it did, open System/Administration/Software Sources and enable using the CD as a repository. Then check the Hardware Drivers tool again. If it didn't work from the live CD, you will need to connect to a wired (ethernet) connection to download the required driver module package.

So there is no way to download it on my laptop and put it on my desktop with my flash drive?

> **arrrghhh said:**
> A network cable would make it easier to get  drivers onto it, but it is possible to get them over with a usb key...

However, I don't recognize that card.  I'll have to do some research.

IF you can get it connected with a hardline, it would make the whole  process a lot less painless.

I just checked the back of my computer again and it turns out I don't even have an ethernet port.

---

### Post by spiky001 on 2010-04-23
There is something called apt get on cd try googling it, it requires abit of work tho

---

### Post by kajiotaku on 2010-04-23
> **spiky001 said:**
> There is something called apt get on cd try googling it, it requires abit of work tho

This? [http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html)

---

### Post by spiky001 on 2010-04-23
Thats what you need the deb file but I have never used it, it would have to go on laptop, another way is put hard drive in another pc with internet update that way I have done that before, but cant say it will work for you becarefull with that option, you will need to read up about apt on cd 1st as well

---

### Post by kajiotaku on 2010-04-23
Tried to install aptoncd_0.1-1_all.deb and it came up with "Error: Dependency is not satisfiable: nautilus-cd-burner"  I also found a a package that says comes with a driver for my wireless card called "madwifi" and I am not sure how to make the file.

---

### Post by spiky001 on 2010-04-23
Have a read [here]("http://techie-blogger.com/install-softwares-in-ubuntu-9-10-linux-in-a-pc-without-internet-connection/")

---

### Post by roger_1960 on 2010-04-23
Hi

Suggest you look at this:

[http://acx100.sourceforge.net/wiki/ACX](http://acx100.sourceforge.net/wiki/ACX)

You need an ACX111 driver.  The site has link sto everthing you need I think, but its not simple.  You should be able to do this via a CD or flash drive.

---

### Post by kajiotaku on 2010-04-23
> **spiky001 said:**
> Have a read [here]("http://techie-blogger.com/install-softwares-in-ubuntu-9-10-linux-in-a-pc-without-internet-connection/")

I don't have another computer running Ubuntu or any other Linux distro.

---

### Post by achase79 on 2010-04-23
instead of apt-on-cd you can use [keryx]("http://www.keryxproject.org").  It will work on linux, windows or mac (I have personally used on all 3)

---

### Post by kajiotaku on 2010-04-24
Got it working.  Did the NDIS Wrapper installation and copied the XP drivers from the disk.  Works fine so far.

---

