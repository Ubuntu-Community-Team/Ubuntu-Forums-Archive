---
title: "Installing Ubuntu 8.10 To A USB Drive--Tutorial?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Aurora@FleetBuzz on 2009-01-18
Been searching and can't find it.   Can someone please point me in the direction of a good tutorial I can use to install 8.10 to a USB memory stick?  My Dell Inspiron 1525 supports booting from a USB drive and I want to do an install on the USB to "test drive" 8.10.

---

### Post by CLomax on 2009-01-18
> **Aurora@FleetBuzz said:**
> Been searching and can't find it.   Can someone please point me in the direction of a good tutorial I can use to install 8.10 to a USB memory stick?  My Dell Inspiron 1525 supports booting from a USB drive and I want to do an install on the USB to "test drive" 8.10.

UNetBootin is good.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Just select the distro and drive, click install and it downloads the .iso and installs it automatically.

---

### Post by Aurora@FleetBuzz on 2009-01-18
Thanks.  I should have asked this before I created an installation CD!  

I'm running Vista on my laptop and don't want to disturb it in any way including having a boot menu presented when I boot the OS from the USB drive.  I just want to be able to select the USB drive and have Ubuntu boot up, completely oblivious of Vista.  

Would it be better to do a direct install from the CD to the USB to do this?  Would that installation be persistent?

---

### Post by akimatsu123 on 2009-01-18
do you want a persistent liveUSB install, or an actual install? "USB Drive" sounds like you are talking about the small USB sticks, in which case you simply have to boot from LiveCD and go to System --> Administration --> Create a USB Startup Disk.

If you are talking about an actual install on an external HDD then [http://ubuntuforums.org/showthread.php?t=1042219]("http://ubuntuforums.org/showthread.php?t=1042219") is a good tutorial with screen shots.

---

### Post by akimatsu123 on 2009-01-18
> **Aurora@FleetBuzz said:**
> Thanks.  I should have asked this before I created an installation CD!  

I'm running Vista on my laptop and don't want to disturb it in any way including having a boot menu presented when I boot the OS from the USB drive.  I just want to be able to select the USB drive and have Ubuntu boot up, completely oblivious of Vista.  

Would it be better to do a direct install from the CD to the USB to do this?  Would that installation be persistent?

If you want this to be a long-term thing (ie. not just installing Ubuntu through USB) then a "real" ubuntu install is definitely the way to go. A LiveUSB shortens your USB pen drive's life cycle, and if you are booting off LiveUSB there is no sudo password which is a security risk. 

Follow the link i gave above.

---

### Post by Aurora@FleetBuzz on 2009-01-18
Yes, I'm going to use a small USB stick.  Will the "Create a USB Start Up" option install the entire operating system to the drive, so that it is portable and persistent?

---

### Post by akimatsu123 on 2009-01-18
> **Aurora@FleetBuzz said:**
> Yes, I'm going to use a small USB stick.  Will the "Create a USB Start Up" option install the entire operating system to the drive, so that it is portable and persistent?

Yes, it will be portable and persistent. But you have small storage on a usb stick, and it's just not very realistic to use. What it does is it basically copies everything from the LiveCD onto the USB and makes it bootable. It's not really "installing the entire operating system". There is on sudo password just like the LiveCD, and boot up takes about 3 minutes minimum.

I tried the persistent liveusb method for about 2 days, then gave up and installed Ubuntu on a 80GB external HDD (only 20 GB for ubuntu partition, 8GB for SWAP, the rest is still data storage) and i am booting off the HDD as I write. 

If you have an external hard drive (new would be preferred,the faster ur HDD the better) i would definitely advise you to actually install the full version of Ubuntu on it instead of using a LiveUSB from a USB stick.

---

### Post by kansasnoob on 2009-01-18
[http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/](http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/)

One thing you should be prepared for *just in case things go amiss as far as Vista's bootloader* is how to restore Vista's MBR if needed. Better to always be prepared ahead of time, eh?

If you should need to restore Vista's mbr you'll need your Vista installation disc. If you have no disc you can get a "repair" disc here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You'd want to "fix boot" and "fix mbr"!

---

### Post by vegetarianshrimp on 2009-01-18
Insert your** [COLOR=Blue]_[USB flash drive]("http://en.wikipedia.org/wiki/USB_flash_drive")_[/COLOR]** (1GB should be enough, although less may work too, I just haven't tested it with less)

Go to [COLOR=Blue]_**[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)**_[/COLOR]

Click on **Download (for Linux)**

**Save** to **Desktop**

Applications>Accesories>[B]Terminal

[/B]Copy and paste each of these lines separately into the terminal (Edit>Copy and Edit>Paste on the menu bars) and press enter after each
     Code:
     cd Desktop
chmod u+x unetbootin-linux-304
sudo ./unetbootin-linux-304 
enter your password, press enter again

Before UNetbootin opens, there might be messages saying that you need to install certain packages (e.g. p7zip-full) Use the **Synaptic Package Manager** to install these. If you don't know how [COLOR=Blue]_[click here]("https://help.ubuntu.com/community/SynapticHowto")_[/COLOR]. Once you've installed those packages, run the last command (sudo ./unetbootin-linux-304) again in the terminal.

**Do NOT close the Terminal AT ANY TIME, for doing this will also close UNetbootin.**

In the UNetbootin window, there will be a drop-down menu "==Select Distribution=="
Select **Ubuntu**

There will also be one called "==Select Version=="
Select **8.10_Live** for 8.10 Intrepid Ibex

In the bottom left corner of the window, there will be another drop down menu. It will either say "Hard Disk" or "USB Drive". You want it to say **USB Drive**

Click **OK**

Wait for everything to finish. While you are waiting, **DO NOT CLOSE THE TERMINAL. UNETBOOTIN WINDOW, OR TAKE OUT YOUR USB DRIVE**

---

### Post by Aurora@FleetBuzz on 2009-01-18
Thanks to all who replied.

The reason I want to try Ubuntu from the USB stick is to see if the 8.10 will support my wireless card.  I've had issues in the past getting my wireless to work (Dell Inspiron 1525) and had to uninstall 8.04.  I don't have the guts or the time to partition the hard drive again and install the new version, or to do it with Wubi.  

I'm hoping that the USB stick will show if its compatible.  If it is, then I'll configure my HD for dual booting.

---

### Post by clive littlewood on 2009-01-18
Hi

Why not try Live CD  ????     :)


Clive



Whoops sorry did not read all the previous posts  !!!!!!!!!!  lol

---

### Post by fuser312 on 2009-01-18
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by Aurora@FleetBuzz on 2009-01-19
Clive, I actually tried the live CD for 8.10, but alas, it did not pick up my wireless.  I guess its because the full range of drivers aren't available unless I install the full OS.

Fuser312, thank you.  This tutorial seems geared to creating a live CD on a USB stick rather than an install, or am I reading it wrong?

---

