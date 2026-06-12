---
title: "PLEASE help--I'm very frustrated and cannot find help. Wireless drivers?"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by pencils42 on 2011-01-22
Okay, here's my story, which of course includes some of my own stupid mistakes.

I got my netbook in the mail yesterday, opened it up, logged in, and Windows 7 was installed. Being a Windows hater my whole life, I followed a friend's advice and downloaded Ubuntu netbook, made a USB drive, changed the BIOS settings, all that. Here's when the stupidity occurs--I decided to go ahead and install Ubuntu without trying it, and to delete Windows to do so. A couple minutes later I realized that was a really, really stupid idea, so in a panic I turned my netbook off. I turned it back on and it was still on install but not really moving, so I powered off and on again and went back to the "Try Ubuntu" or "Install Ubuntu" choice screen. I chose "Try Ubuntu" and found that it did not recognize my home wifi network or ask me to join--or any wifi network, for that matter. 

Now, it did recognize my wifi network the few minutes I spent on Windows 7, so I tried to change the BIOS settings back to where I could just use that until I figured out the problem. But no matter which setting I tried (HDD/SDD just gives me a black screen, and FDD and LAN do the same as the USB drive), I can't get back to Windows, so I guess I did delete it. Which leaves me with a netbook that can only connect to the internet via ethernet cable. Which kind of defeats the purpose.

Questions I should answer:

1. How am I trying to get online? My home's wireless network. We have a router. All the other laptops in the house connect fine.

2. Who is my internet service provider (and in which country?) COX, United States.

3. Can you get online with any other method? Yes, the internet works fine with an ethernet cable.

4. How am I getting online to post in this forum? My parent's laptop.

5. What hardware are you using? Toshiba N505 netbook and a router. I can give more information about the router if you need it, but I doubt it's the program since the other laptops are fine.

Give me one moment and I will add some code that it gives me when I put in the commands this website tells me to.

My two final questions are:

1. Is there any way to recover Windows without buying it again?
2. How can I get Ubuntu to connect to my home wifi network?

PLEASE NOTE THAT I AM AWARE THAT THE SOLUTION IS TO HOOK UP TO ETHERNET AND DOWNLOAD/AND INSTALL A WIRELESS DRIVER. But I have no idea how to go about doing this. What driver to I need? Where do I find it? Etc.? I'm so terribly lost and very frustrated at this point. I would REALLY appreciate any help you gave me. A lot. 


EDIT: Here's some code. I have no idea what it means, but hopefully you do.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
*-network UNCLAIMED 
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:07:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: ioport:2000(size=256) memory:f0100000-f0103fff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 05
serial: 1c:75:08:76:9f:96
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.5 latency=0 multicast=yes
resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
ubuntu@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 1c:75:08:76:9f:96 
inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::1e75:8ff:fe76:9f96/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3011 errors:0 dropped:0 overruns:0 frame:0
TX packets:2383 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:3682498 (3.6 MB) TX bytes:326427 (326.4 KB)
Interrupt:43 Base address:0xc000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 1 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
ubuntu@ubuntu:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

---

### Post by spiky001 on 2011-01-22
As you can connect via an eth0 cable can you update the system via update manager  System/Administration/update manager hopefully this will install any drivers, also check hardware drivers in System/administration/hardware drivers

---

### Post by fabricator4 on 2011-01-22
You probably don't want to hear this, but you should really have made the Windoze bootable recovery disks before blowing away the windows partition.

The Toshiba recovery partition _may_ still be on the hard drive, unless you let the install program blow that away too (you may be lucky here). 

The recovery program is normally accessed by a function key press when the computer is going through post.  Consult the laptop manual and/or the the Toshi site for more information.  I suggest you re-install windows, make the recovery disks, then proceed with the Ubuntu install.

You can also use the disk utility or Gparted to check that the recovery partition is still there.  I think from Memory that Toshiba may put this recovery partition at the _end_ of the drive, and it's normally about 4Gb or so.

There are probably third party drivers needed to get the WIFI working under Linux.  Check the compatibility lists for your machine (should have done that before purchase, though I shouldn't kick a guy while he's down ;-) ).  Enable proprietary drivers in the software sources and then tell Ubuntu to check for Hardware drivers.

Chris.

---

### Post by tpprynn on 2011-01-22
Does it say anything about a Recovery Partition in your netbook's manual? I'd hope that if you have got a recovery disc that they'd at least supply a Recovery Partition - my Toshiba laptop had one when I was using Vista, hopefully the company's consistent. If you have a friend with a Windows 7 disc too you at least have a license on the bottom of the netbook to get that installed, using a memory stick/pendrive and the program called 'Novicorp WinToFlash' to copy the disc to the stick (maybe find a link for it through Wikipedia so you can be sure it's not tampered with).

The wireless question I'll be even less assistance, except to say that you might have more luck with Wicd than Network Manager, which you'd need to purge. Somehow my laptop seems randomly not to have wireless during some boots, or it comes on a bit late - sure you didn't just miss it starting up?

Don't panic!

---

### Post by fabricator4 on 2011-01-22
I should have also said, you don't need to buy windows again if it came with the machine.  Your license label is stuck on the bottom of the machine.  If you can't recover from the recovery partition and can't find any disks that will work with that particular license then you can contact Toshiba and ask them to send you a set.  For a fee, of course.  They will want to know the exact model of your computer, and probably other details as well.

Chris.

---

### Post by walt.smith1960 on 2011-01-22
Did you get a DVD with your netbook? If so, you can restore Windows. If not, is there a restore partition?  Some keystroke or keystroke combination to restore to factory configuration? I'd be disappointed if you don't have one or the other.  Ubuntu and windows can exist on the same machine at the same time.

---

### Post by Runckle on 2011-01-22
Ooopppsss You're like me Act 1st think later. You really need to learn like myself that it has to be think 1st act later...;)

---

### Post by pencils42 on 2011-01-22
Thank you SO MUCH to everyone who has tried to help. I truly and deeply appreciate it. I'm well aware that I have done some very stupid things and yes, I should definitely learn to think before I act haha. Something to work on! I'll be trying several different things now. Here's my first course of action.

[QUOTE=tpprynn;10387728]Does it say anything about a Recovery Partition in your netbook's manual? I'd hope that if you have got a recovery disc that they'd at least supply a Recovery Partition - my Toshiba laptop had one when I was using Vista, hopefully the company's consistent./QUOTE]

Didn't come with a user manual strangely enough, but I found one on Toshiba's website. In case you're interested in reading:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2861099&rpn=PLL50U&modelFilter=NB505-N508BL&selCategory=2756709&selFamily=2336267](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2861099&rpn=PLL50U&modelFilter=NB505-N508BL&selCategory=2756709&selFamily=2336267)

I'm on page 51, where it says to hold zero while powering on. I'm doing that, but it just goes to this like Ubuntu set up page, with language selection and stuff like that. Any ideas?

---

### Post by Michael Dooley on 2011-01-22
>  Here's when the stupidity occurs--I decided to go ahead and install Ubuntu without trying it, and to delete Windows to do so.

Ouch! Not a great decision but not so unusual either. 

> Which leaves me with a netbook that can only connect to the internet via ethernet cable. Which kind of defeats the purpose.

This can be fixed. Your situation involves the Netbook edition, not the more ordinary ubuntu version. I'd ignore advice that is non-specific to the netbook edition for the moment though.

> 1. How am I trying to get online? My home's wireless network. We have a router. All the other laptops in the house connect fine.

To get your netbook installation up and running as it should, please connect using an ethernet connection. This should only be needed for an update of your installation.

> 1. Is there any way to recover Windows without buying it again?

Install Win7 with a usb drive if you have an installation cd. There are ways to transfer the installation CD to a usb key. If you don't have an installation CD, I'd explore having your source for the netbook reinstall it for you.

> 2. How can I get Ubuntu to connect to my home wifi network?

PLEASE NOTE THAT I AM AWARE THAT THE SOLUTION IS TO HOOK UP TO ETHERNET AND DOWNLOAD/AND INSTALL A WIRELESS DRIVER.

You must use an ethernet connection to update the OS software. At the left of your netbook version screen, you should see a stack of menus, Favorites, Files & Folders, Accessories, Games, and so on. Click on System, which should be at the bottom of the stack.

Your desktop screen should now display Preferences and about 16 icons below. Over to the right of the screen is a scroll bar - scroll to the bottom of the screen.

You should now see eleven icons. The one you need to click on is called Update Manager. Click once on this icon.

If you get a notice about battery, as in "Running on battery", please hook up your power supply/charger as the update process could take a bit of time. 

You should see the Starting Update Manager dialog box. The Update Manager should have quite a number of updates for you to agree to install.

One of them is quite possibly a driver for your wireless card. Install all the updates. 

Report back if this (1) either worked or (2) did not work.

Good luck pencils42. I'm pulling for ya.

---

### Post by pencils42 on 2011-01-22
> **Michael Dooley said:**
> Ouch! Not a great decision but not so unusual either. 



This can be fixed. Your situation involves the Netbook edition, not the more ordinary ubuntu version. I'd ignore advice that is non-specific to the netbook edition for the moment though.



To get your netbook installation up and running as it should, please connect using an ethernet connection. This should only be needed for an update of your installation.



Install Win7 with a usb drive if you have an installation cd. There are ways to transfer the installation CD to a usb key. If you don't have an installation CD, I'd explore having your source for the netbook reinstall it for you.



You must use an ethernet connection to update the OS software. At the left of your netbook version screen, you should see a stack of menus, Favorites, Files & Folders, Accessories, Games, and so on. Click on System, which should be at the bottom of the stack.

Your desktop screen should now display Preferences and about 16 icons below. Over to the right of the screen is a scroll bar - scroll to the bottom of the screen.

You should now see eleven icons. The one you need to click on is called Update Manager. Click once on this icon.

If you get a notice about battery, as in "Running on battery", please hook up your power supply/charger as the update process could take a bit of time. 

You should see the Starting Update Manager dialog box. The Update Manager should have quite a number of updates for you to agree to install.

One of them is quite possibly a driver for your wireless card. Install all the updates. 

Report back if this (1) either worked or (2) did not work.

Good luck pencils42. I'm pulling for ya.


Thank you so much, I truly appreciate the help. I found Update manager, but it says "The package information was last update 107 days ago. Your system is up to date. There are no updates to install."

---

### Post by Michael Dooley on 2011-01-22
You should not take this as an "everything is up to date" message. Click on Check. You will be asked for your password. Type it in and you should see numerous updates waiting to be installed. These need to be added to get things working.

I generally like to see something like "the package information was last updated three hours ago." Go for it.

---

### Post by pencils42 on 2011-01-22
> **fabricator4 said:**
> You probably don't want to hear this, but you should really have made the Windoze bootable recovery disks before blowing away the windows partition.

There are probably third party drivers needed to get the WIFI working under Linux.  Check the compatibility lists for your machine (should have done that before purchase, though I shouldn't kick a guy while he's down ;-) ).  Enable proprietary drivers in the software sources and then tell Ubuntu to check for Hardware drivers.

Chris.


I agree I should have done a LOT of this before purchase ;) Two questions, where can I check compatibility lists for my machine and how do I enable proprietary drivers? I told it to check for Hardware drivers and it said none were available.

---

### Post by pencils42 on 2011-01-22
> **Michael Dooley said:**
> You should not take this as an "everything is up to date" message. Click on Check. You will be asked for your password. Type it in and you should see numerous updates waiting to be installed. These need to be added to get things working.

I generally like to see something like "the package information was last updated three hours ago." Go for it.


Ahhh! My bad. I will install the updates and get back to you:)

---

### Post by pencils42 on 2011-01-22
> **pencils42 said:**
> Ahhh! My bad. I will install the updates and get back to you:)

Oooh wait, one problem. Not enough space on the drive. I'm on a 2GB USB. Is there stuff I can delete, or am I screwed?

---

### Post by Michael Dooley on 2011-01-22
Sorry that I didn't get that you were on a live usb instead of an actual netbook installation. Having never faced this particular problem before, I can't say.

If it were me, I'd look for some updates to either realtek or whatever your wireless chipset might be and update those things only. Sorry I can't be of more assistance here.

Maybe Intel NM10 chipset updates?

---

### Post by TBABill on 2011-01-22
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

That's your wireless device. I got a quote from another link that should provide the fix: > I have recently purchased this model of Toshiba laptop and encountered the same wireless issues. I have found that there is a workaround. Someone has written a DKMS driver for the RTL8192CE wireless chipset and set up a PPA. To install it, run the following commands:

sudo add-apt-repository ppa:lexical/hwe-wireless
apt-get update
apt-get install rtl8192ce-dkms

Now restart the machine and upon reboot you should be able to click on the wireless icon in the top panel and set up a wireless connection. Hope this helps.

Link to the thread this came from for your card [http://ubuntuforums.org/showthread.php?t=1620697&highlight=realtek+8176](http://ubuntuforums.org/showthread.php?t=1620697&highlight=realtek+8176)

EDIT: Yes, this says rtl8192, but that's the chipset the 8176 apparently uses.

---

### Post by fabricator4 on 2011-01-22
> **pencils42 said:**
> I agree I should have done a LOT of this before purchase ;) Two questions, where can I check compatibility lists for my machine and how do I enable proprietary drivers? I told it to check for Hardware drivers and it said none were available.

Hi, to tell Ubuntu to load proprietary drivers, open
```

->System
    ->Administration
        ->Software Sources

```

Then make sure that there is a tick on "Proprietary drivers for devices (restricted)

Then to get the system to check for available drivers click 

```

->System
    ->Administration
        ->Hardware Drivers

```

If it doesn't find the drivers by itself, you will have to find and install them manually.

For Compatibility:

[Basic Information]("http://help.ubuntu.com/8.04/switching/preparing-hardware.html")

[Hardware Support Wiki]("http://wiki.ubuntu.com/HardwareSupport/")

Chris

---

### Post by TBABill on 2011-01-22
Realtek drivers are not proprietary. They're included in the kernel or available for download from Realtek like Intel drivers.

---

### Post by fabricator4 on 2011-01-22
> **pencils42 said:**
> Oooh wait, one problem. Not enough space on the drive. I'm on a 2GB USB. Is there stuff I can delete, or am I screwed?

If you get the driver working under the live USB, it will forget it again next time you boot.  The "live" system boots clean each time.  You can make a USB bootable (preferrably a 4gb minimum) and install it on that, but that doesn't help you either as you really want the updated and working config on your hard drive, not the USB.

If you can recover the windows (sounds like it might be gone) I would:

A) reinstall windows on a small(ish) partition
B) reinstall Ubuntu on the rest of the drive

which would give you a dual boot machine and access to either operating system as you needed it.

It sounds like you might have told Ubuntu to use the whole drive for it's initial install, and it might have taken everything including the hidden recovery partition at the end of the drive. 

You do need to run the disk utility and see what partitions are on the drive, if it's only two - the Ubuntu boot partition and the swap drive, then you might be pooched.

Chris.

---

### Post by pencils42 on 2011-01-22
> **TBABill said:**
> 07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

That's your wireless device. I got a quote from another link that should provide the fix: 

Link to the thread this came from for your card [http://ubuntuforums.org/showthread.php?t=1620697&highlight=realtek+8176](http://ubuntuforums.org/showthread.php?t=1620697&highlight=realtek+8176)

EDIT: Yes, this says rtl8192, but that's the chipset the 8176 apparently uses.

Tried it, got this:

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:lexical/hwe-wireless
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 88B3CE2CE934D5F973CC26C80C5CE27EA088FF1E
gpg: requesting key A088FF1E from hkp server keyserver.ubuntu.com
gpg: key A088FF1E: public key "Launchpad Keng-Yu's PAA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
ubuntu@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ apt-get install rtl8192ce-dkms

---

### Post by pencils42 on 2011-01-22
> **Michael Dooley said:**
> Sorry that I didn't get that you were on a live usb instead of an actual netbook installation. Having never faced this particular problem before, I can't say.

If it were me, I'd look for some updates to either realtek or whatever your wireless chipset might be and update those things only. Sorry I can't be of more assistance here.

Maybe Intel NM10 chipset updates?


I unchecked enough stuff to get it to install. Hopefully this helps, I'll let you know when it's done.

---

### Post by Michael Dooley on 2011-01-22
sudo apt-get update

---

### Post by pencils42 on 2011-01-22
> **fabricator4 said:**
> If you get the driver working under the live USB, it will forget it again next time you boot.  The "live" system boots clean each time.  You can make a USB bootable (preferrably a 4gb minimum) and install it on that, but that doesn't help you either as you really want the updated and working config on your hard drive, not the USB.

If you can recover the windows (sounds like it might be gone) I would:

A) reinstall windows on a small(ish) partition
B) reinstall Ubuntu on the rest of the drive

which would give you a dual boot machine and access to either operating system as you needed it.

It sounds like you might have told Ubuntu to use the whole drive for it's initial install, and it might have taken everything including the hidden recovery partition at the end of the drive. 

You do need to run the disk utility and see what partitions are on the drive, if it's only two - the Ubuntu boot partition and the swap drive, then you might be pooched.

Chris.

1. Okay, I'll keep that in mind.

At this point I'm thinking Windows is probably gone. How do I 'run the disk utility'?

---

### Post by pencils42 on 2011-01-22
> **Michael Dooley said:**
> sudo apt-get update

What should I use this command for exactly? Sorry, I'm confused...I'm installing stuff right now...should I stop?

---

### Post by pencils42 on 2011-01-22
> **fabricator4 said:**
> Hi, to tell Ubuntu to load proprietary drivers, open
```

->System
    ->Administration
        ->Software Sources

```

Then make sure that there is a tick on "Proprietary drivers for devices (restricted)

Then to get the system to check for available drivers click 

```

->System
    ->Administration
        ->Hardware Drivers

```

If it doesn't find the drivers by itself, you will have to find and install them manually.

For Compatibility:

[Basic Information]("http://help.ubuntu.com/8.04/switching/preparing-hardware.html")

[Hardware Support Wiki]("http://wiki.ubuntu.com/HardwareSupport/")

Chris

I used the links you included and found this:

[https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

I'm really a newbie about this, is this anything I should be interested in?

---

### Post by Michael Dooley on 2011-01-22
> **pencils42 said:**
> What should I use this command for exactly? Sorry, I'm confused...I'm installing stuff right now...should I stop?

No, no. This was a response to post #20 where you got an error message because you "were not root". Sudo is used to initiate root privileges. Sorry to be imprecise. Good luck lad.

---

### Post by pencils42 on 2011-01-22
> **Michael Dooley said:**
> No, no. This was a response to post #20 where you got an error message because you "were not root". Sudo is used to initiate root privileges. Sorry to be imprecise. Good luck lad.

Oh, ok, thank you. As a general update, I'm going to try this once my netbook powers back up, but if it doesn't work, well--I just got off the phone with Toshiba tech support, who agreed that the hidden partition was probably deleted. She directed me to a website where I can buy a recovery disk. It'll be expensive to buy that *and* an external DVD drive, but I'm thinking it's what I'll have to do.

---

### Post by pencils42 on 2011-01-22
Well, I might not have to buy an external CD drive. On acclaim.toshiba.com one of the options is "USB-MINI NOTEBOOK-NB505-Windows 7 32bit Starter-EN". Is that the same thing just in USB form?

---

### Post by nm_geo on 2011-01-22
> **pencils42 said:**
> Oh, ok, thank you. As a general update, I'm going to try this once my netbook powers back up, but if it doesn't work, well--I just got off the phone with Toshiba tech support, who agreed that the hidden partition was probably deleted. She directed me to a website where I can buy a recovery disk. It'll be expensive to buy that *and* an external DVD drive, but I'm thinking it's what I'll have to do.

Since you are booting from the USB. Lets take a look at the hardrive in the computer.  Try the following.


boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.
How to use the boot info script

    * Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
    * Download the Boot Info Script    [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
    * Open a terminal (Applications>Accessories>Terminal in Gnome) and type

       sudo bash [path/to/the/download_folder]/boot_info_script*.sh

      For example if you downloaded the file to the desktop, use

       sudo bash ~/Desktop/boot_info_script*.sh 

    * If your operation system does not use sudo, use

           su 
           bash ~/Desktop/boot_info_script*.sh<<<<  (Ubuntu uses sudo ignore this)
           

    * You will now have the file RESULTS.txt in the same directory as the script. But if the script is inside a system directory (like /usr or /etc) RESULTS.txt will be in the home directory.
    * If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
    * Open RESULTS.txt in your favorite text editor.
    * If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.

---

### Post by pencils42 on 2011-01-22
> **Michael Dooley said:**
> No, no. This was a response to post #20 where you got an error message because you "were not root". Sudo is used to initiate root privileges. Sorry to be imprecise. Good luck lad.

Ok, so I was able to install the driver using that command, but it didn't work. If I actually installed ubuntu instead of having it on a flashdrive do you think it would work? Since there's apparently no hope of recovering Windows at this point save buying the recovery disk, I figure I might as well give it a shot. What do you think?

---

### Post by pencils42 on 2011-01-22
> **nm_geo said:**
> Since you are booting from the USB. Lets take a look at the hardrive in the computer.  Try the following.


boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.
How to use the boot info script

    * Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
    * Download the Boot Info Script    [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
    * Open a terminal (Applications>Accessories>Terminal in Gnome) and type

       sudo bash [path/to/the/download_folder]/boot_info_script*.sh

      For example if you downloaded the file to the desktop, use

       sudo bash ~/Desktop/boot_info_script*.sh 

    * If your operation system does not use sudo, use

           su 
           bash ~/Desktop/boot_info_script*.sh<<<<  (Ubuntu uses sudo ignore this)
           

    * You will now have the file RESULTS.txt in the same directory as the script. But if the script is inside a system directory (like /usr or /etc) RESULTS.txt will be in the home directory.
    * If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
    * Open RESULTS.txt in your favorite text editor.
    * If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.

This all sounds nice, and, pardon, I don't mean to sound sarcastic I'm just genuinely curious, but, what would it do? Like what would I gain from doing this?

---

### Post by nm_geo on 2011-01-22
It will tell us if your harddrive has been written to by Ubuntu or if maybe all that has happen is your windows MBR is corrupted.
We may be able to see that your windows is intact or not.

---

### Post by pencils42 on 2011-01-22
> **nm_geo said:**
> It will tell us if your harddrive has been written to by Ubuntu or if maybe all that has happen is your windows MBR is corrupted.
We may be able to see that your windows is intact or not.

Oh ok! I downloaded the file and it saved to 'downloads'. How would I code that? That squiggly line you put in fron of desktop...I don't have that key on my keyboard; it's a netbook. Edit: Whoops just kidding I found it, they put it in a different spot than usual.

---

### Post by pencils42 on 2011-01-22
So this is the results (sorry this is long)

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'swsuspend'

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   482,256,895   482,254,848  83 Linux
/dev/sda2         482,258,942   488,396,799     6,137,858   5 Extended
/dev/sda5         482,258,944   488,396,799     6,137,856  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,913,055     3,912,993   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        39926165-4ea6-4ecf-9e89-47d6f7ae9e06   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1afbe2b0-a88d-4b2f-9e94-f99cd30b4287   swsuspend                                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7FFA-17F1                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1afbe2b0-a88d-4b2f-9e94-f99cd30b4287 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 223.4GB: boot/vmlinuz-2.6.35-22-generic
 223.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c9 a6 24 fe db c9 a2 5c  e4 5c b1 b9 65 e6 c8 b4  |..$....\.\..e...|
00000010  45 0d 35 43 60 f1 97 d1  ec a2 7a 2d 38 b2 c9 f5  |E.5C`.....z-8...|
00000020  fb cb 3b d9 c3 8c 3d e5  3d 38 6b c5 c5 b5 c8 11  |..;...=.=8k.....|
00000030  13 e1 5c a2 e1 e3 61 7a  c6 f1 7f 49 21 11 26 c7  |..\...az...I!.&.|
00000040  06 99 10 68 c7 b3 2e a4  c4 a6 f4 8d 0b 64 ba a8  |...h.........d..|
00000050  91 8a 8e 22 80 41 46 e2  59 51 f0 26 c6 c3 bd f2  |...".AF.YQ.&....|
00000060  a8 6f 2b 55 64 7e af e8  5a e8 27 dd a2 1a aa 77  |.o+Ud~..Z.'....w|
00000070  15 4e ec 83 4a ff e9 08  e9 3e f8 24 7e 96 c3 73  |.N..J....>.$~..s|
00000080  78 e7 a7 5a 99 9f 2f b0  96 8e e3 31 69 1a 20 68  |x..Z../....1i. h|
00000090  a1 d4 13 f0 1d d2 a1 36  b0 3d 94 ff c3 1f 9f a7  |.......6.=......|
000000a0  f7 f2 2b 4b 11 92 68 85  9f 85 b9 e0 56 1b b8 d8  |..+K..h.....V...|
000000b0  e9 bc 5b 9b 74 31 9c 1d  8d bc 41 ea a0 21 53 20  |..[.t1....A..!S |
000000c0  5e 8c 9a 0d 5e 33 1f bb  b6 0e 17 eb 42 81 b7 b8  |^...^3......B...|
000000d0  4a ea e2 c8 33 c6 f3 80  5e b2 a4 02 52 e9 14 2e  |J...3...^...R...|
000000e0  ce 88 c0 2b 1d e0 c7 01  03 e9 27 66 2c 22 0b bd  |...+......'f,"..|
000000f0  24 0b d4 90 2f 62 72 7b  24 35 ad d5 d9 42 6c 15  |$.../br{$5...Bl.|
00000100  41 8c 75 f8 d0 f3 73 1a  c1 4a 8d 37 10 8b 5c 4f  |A.u...s..J.7..\O|
00000110  57 61 42 44 f0 cd 4e fd  c7 b7 09 16 d5 4d 4c 2a  |WaBD..N......ML*|
00000120  9b 04 64 ff 43 23 5a f3  1f e5 3a cf 6c 91 41 0b  |..d.C#Z...:.l.A.|
00000130  53 4c cf bd b5 a2 7e d0  a1 11 9f 57 7d f4 83 61  |SL....~....W}..a|
00000140  74 3b b2 a2 f2 d7 c0 a7  5a 0c dd c5 92 ea 53 f2  |t;......Z.....S.|
00000150  ab df 15 bf 0f f1 db a4  02 75 ba 88 51 9d 01 2a  |.........u..Q..*|
00000160  80 71 2c ce fd 8a cc 09  82 dd 61 97 90 4e 10 13  |.q,.......a..N..|
00000170  da 20 aa 0a e4 6b 25 ac  f5 c1 8d d6 24 5e 1d 29  |. ...k%.....$^.)|
00000180  7d 49 10 5e a1 e5 d5 b3  6e ef a4 fd 6c 8b dc a8  |}I.^....n...l...|
00000190  b1 21 85 77 37 56 36 f4  eb 43 9e 3a f4 f9 eb e2  |.!.w7V6..C.:....|
000001a0  ca 38 11 96 b9 6f 0b 25  fb ba dc 41 32 b3 75 63  |.8...o.%...A2.uc|
000001b0  a5 85 a7 73 f6 3f 8b eb  52 01 a6 74 37 f9 00 fe  |...s.?..R..t7...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 01 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 20 00 3f 00 00 00  |........?. .?...|
00000020  21 b5 3b 00 00 00 29 f1  17 fa 7f 20 20 20 20 20  |!.;...)....     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 cd 18  |      FAT16   ..|
00000040  fa 33 c9 8e d1 bc fc 7b  16 07 bd 78 00 c5 76 00  |.3.....{...x..v.|
00000050  1e 56 16 55 bf 22 05 89  7e 00 fa fc 31 c9 8e d1  |.V.U."..~...1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 7f 12 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 



Sorry that I'm so computer-illiterate, what does this mean for me?

---

### Post by nm_geo on 2011-01-22
> **pencils42 said:**
> Oh ok! I downloaded the file and it saved to 'downloads'. How would I code that? That squiggly line you put in fron of desktop...I don't have that key on my keyboard; it's a netbook. Edit: Whoops just kidding I found it, they put it in a different spot than usual.

Try this 

```
sudo bash ~/Downloads/boot_info_script*.sh
```

Copy that line and paste it in the terminal window,

Then copy the results file and put it in the middle of the  # {Code} brackets  That is how I boxed the command line above.

---

### Post by fabricator4 on 2011-01-22
> **pencils42 said:**
> 1. Okay, I'll keep that in mind.

At this point I'm thinking Windows is probably gone. How do I 'run the disk utility'?

Just go to:

```

->System
    ->Administration
        ->Disk Utility

```

Select the Hard Drive, and it should show a graphical representation of the partitions on the hard drive.

However...  at this stage I'm expecting you'll only see the two Linux partitions.  When you followed the procedure for recovery it should have given you the option to boot into either the recovery partition or the OS.  You only got an option that mentioned the OS.  If by some happy chance the windows hidden recovery partition is still there, you might just need to mark it bootable to get it to run.

Chris.

---

### Post by nm_geo on 2011-01-22
I see you got the results file.  Check out those (# signs) in the post/reply box for coping info.. No problem though. It does appear the win7 is overwritten one problem for sure is we have no Grub2 installed in the sda partition.  

I would first try another install and patient.  

The grub will install then.

---

### Post by pencils42 on 2011-01-22
> **fabricator4 said:**
> Just go to:

```

->System
    ->Administration
        ->Disk Utility

```

Select the Hard Drive, and it should show a graphical representation of the partitions on the hard drive.

However...  at this stage I'm expecting you'll only see the two Linux partitions.  When you followed the procedure for recovery it should have given you the option to boot into either the recovery partition or the OS.  You only got an option that mentioned the OS.  If by some happy chance the windows hidden recovery partition is still there, you might just need to mark it bootable to get it to run.

Chris.

Well...it looks like at this point Windows is gone for good. I guess if I want it back I'll be buying the recovery USB.

---

### Post by pencils42 on 2011-01-22
> **nm_geo said:**
> I see you got the results file.  Check out those (# signs) in the post/reply box for coping info.. No problem though. It does appear the win7 is overwritten one problem for sure is we have no Grub2 installed in the sda partition.  

I would first try another install and patient.  

The grub will install then.

I'm sorry, but I have absolutely no idea what you just said.

---

### Post by fabricator4 on 2011-01-22
> **TBABill said:**
> or available for download from Realtek like Intel drivers.

Shirley that would meet the definition of a proprietary driver?

Chris

---

### Post by nm_geo on 2011-01-22
> **pencils42 said:**
> I'm sorry, but I have absolutely no idea what you just said.

When you copy and paste large amounts of data there is a # sign above the reply box that you type in ... Click on the #
```
Insert copied data between the bracketed code signs
```We could try to install Grub in the sda partition where it needs to be but you said you had an interrupted installation.  I would re-install from the USB again first it will not hurt anything..

---

### Post by fabricator4 on 2011-01-22
> **pencils42 said:**
> I used the links you included and found this:

[https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

I'm really a newbie about this, is this anything I should be interested in?

Well that claims to be for the 8192 device, whereas yours appears to be the 8176.  As someone pointed out though, they may use the same driver so yes, the drivers in the repository may be useful.

Chris.

---

### Post by Michael Dooley on 2011-01-22
> **pencils42 said:**
> Ok, so I was able to install the driver using that command, but it didn't work. If I actually installed ubuntu instead of having it on a flashdrive do you think it would work? Since there's apparently no hope of recovering Windows at this point save buying the recovery disk, I figure I might as well give it a shot. What do you think?

My feeling is that you can conquer these difficulties once the ubuntu netbook version is installed on the hard drive. I have yet to see a difficulty in these forums that could not be resolved by following the "correct" instructions. There are a lot of well intentioned folks that attempt to give advice but lack the point of view of the novice user. You have to sort out the great advice from the well intentioned advice.

Good luck on doing this pencils42.

It might be wise to wait for your supplier to provide you with a re-install disc or image for your usb drive. Having Win7 is not a bad idea as far as I am concerned.

I'm off line for a few hours (no matter what the forum user shows). Let me know how it goes.

---

### Post by Michael Dooley on 2011-01-23
Any news? Are you still on the live usb or have you installed Ubuntu netbook?

---

### Post by tpprynn on 2011-01-23
Yeah, let us know how you're doing - definitely no need to give Toshiba or Microsoft any more money though!

You'll smile about this in a couple of years...

---

### Post by [Snc] on 2011-01-23
> **pencils42 said:**
> Ok, so I was able to install the driver using that command, but it didn't work. If I actually installed ubuntu instead of having it on a flashdrive do you think it would work? Since there's apparently no hope of recovering Windows at this point save buying the recovery disk, I figure I might as well give it a shot. What do you think?

Check this out, its also about Toshiba N505 Wifi with Ubuntu

[http://ubuntuguru.wordpress.com/2009/08/28/ubuntu-on-toshiba-nb200-nb-205-netbook/](http://ubuntuguru.wordpress.com/2009/08/28/ubuntu-on-toshiba-nb200-nb-205-netbook/)

---

### Post by pencils42 on 2011-01-23
Sorry about last night! I went to bed. Haha, timezones. But anyway, I went ahead and installed Ubuntu on the hard drive instead of the USB. I'm now going to try a couple of things suggested, and I will get back to you asap. (Side note: Worst comes to worst, I found out at church this morning that the woman who lives across the street from me is a linux expert. Hooray!)

---

### Post by pencils42 on 2011-01-23
> **TBABill said:**
> 07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

That's your wireless device. I got a quote from another link that should provide the fix: 

Link to the thread this came from for your card [http://ubuntuforums.org/showthread.php?t=1620697&highlight=realtek+8176](http://ubuntuforums.org/showthread.php?t=1620697&highlight=realtek+8176)

EDIT: Yes, this says rtl8192, but that's the chipset the 8176 apparently uses.

Ok, I tried this one more time. Unfortunately, it didn't work. Now I'm going to try the thing I linked to earlier.

---

### Post by pencils42 on 2011-01-23
> **fabricator4 said:**
> Well that claims to be for the 8192 device, whereas yours appears to be the 8176.  As someone pointed out though, they may use the same driver so yes, the drivers in the repository may be useful.

Chris.


I tried this one too, and no change. To be sure I'm doing this right: I enter the command in the terminal, let it do its thing, then command sudo apt-get update, then let that do its thing, restart my netbook, pull out the ethernet cable, and see if my wifi network shows up. It doesn't.

---

### Post by pencils42 on 2011-01-23
Also, I keep trying to run 'software sources' but it doesn't work. Like, I installed it but now I can't find it.

---

### Post by [Snc] on 2011-01-24
> **pencils42 said:**
> Also, I keep trying to run 'software sources' but it doesn't work. Like, I installed it but now I can't find it.

software sources readme
```
https://help.ubuntu.com/community/Repositories/Ubuntu
```

---

### Post by Rational1 on 2011-02-04
This worked for me on my wifes NB505-N500BL

[http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101)
Thread 6 has the link to the website to get the driver, and directions.
I suggest a clean install to the hard drive.

Download the driver to Downloads folder
Right click the tar.gz file and choose "extract here".
Change the name of the folder to something easier to type in the Terminal window.
Follow the instructions, wireless city.

---

