---
title: "am stuck trying to install ndiswrapper"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by alexlaird87 on 2011-07-28
HELP!

Yesterday I installed Kubuntu 11.04 onto my Inspiron 1520. The computer's wifi (Wireles Dell 1395) is not working I am now trying to install ndiswrapper so i can install the driver for the wifi, but now I have hit a brick wall. I have googled it and searched on the forum, but none of the answers allowes me to complete the install.

The most success i have reached so far is to get half way through this instructional [video]("http://www.youtube.com/watch?v=v0Ist9aEKEg&feature=player_embedded"), but won't work past the command "make".
 
It tells me the "make" is not installed. it tells me i can install make by typing: "sudo apt-get install make"

I type this it tells me "E: Package make has no installation candidate"

I am brand new to Kubuntu, and have not used command lines since I stopped using DOS in 1995, so please explain slowly and at a beginners level.

---

### Post by gigenieks on 2011-07-28
First things first:

> 
The computer's wifi (Wireles Dell 1395) is not working

Did you try _first_ **Live CD?** Did it work then? 
Or you just installed Kubuntu straight away without even trying Live CD environment...

---

### Post by alexlaird87 on 2011-07-28
This was my old laptop, windows got corrupted and I don't have the Disc to reinstall. I installed Kubuntu to give it a try to see if i liked it. I can't really tell yet as the computer has no internet access.

I am currently writing these posts on my wifes Macbook.

---

### Post by whitethorn on 2011-07-28
Let's get some information.
Can you post the output from

```
lspci
```

Have you already installed (I think it's still called) build-essentials? Looks like you don't have make installed, and I'm guessing your also going to need install the kernel headers.

---

### Post by alexlaird87 on 2011-07-28
Here is the output from lspci;

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family)  PCI Express port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family)  PCI Express port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family)  USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LCP Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus:  Intel Corporation 82801H (ICH8 Family)  SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:00.0Ethernet controller: Broadcom Corporation BCM4401-B0 100base-TX (rev 02)
03:01.0 Firewire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

So far I have installed nothing, just the OS. can't really install much very easily until i get the wifi working.

---

### Post by anewguy on 2011-07-28
If at all possible, hard-wire a temporary connection between your laptop and the router so you can get on the net.  Then go to system/administration/additional drivers - it will take a while for this to complete.  When it does, there should be a driver showing - just enable the driver and that should be it.

If that is not possible, yes we could use some native tools to get you running (firmware cutter, the proper firmware, etc.), but the truth of the matter is that in this case ndiswrapper would be just as easy.

You do need, however, either a LiveCD or the USB version.  After booting Ubuntu, insert this installation media - it will probably say a software source has been found - just cancel that.

Using "Places", or what ever the file explorer is called in KDE, navigate to the /pool/main/n folder.  There you will find 2 folders:  ndisgtk and ndiswrapper.  Do the following:
[LIST]
[*]go to the ndiswrapper folder first
[*]double-click the ndiswrapper common file to begin it's installation.  It will probably ask for your password - just  type your normal password - it just won't show on the screen.  Wait for this to complete.
[*]Double-click on the ndiswrapper utilities file and it will begin its' installation.  If prompted, enter your password.  Wait for this to finish.
[*]Now go back to the ndisgtk folder.
[*]Double-click on the ndisgtk file to begin its' installation.  If prompted, enter your password.  Wait for this to complete.
[*]Now you need your Windows drivers.  There are 3 requirements these drivers must meet:
[LIST=1]
[*]They must be Windows XP drivers *ONLY*
[*]They must be unpacked - you will need the individual .inf and .sys files
[*]The architecture of the drivers must match your ubuntu architecture - 32 or 64 bit.
[/LIST]
[*]Start ndisgtk - I don't know where it is in the menus in KDE, but in Gnome it would be under system/administration/windows wireless drivers
[*]Now just add and point it to the .inf file for your driver.
[/LIST]

---

### Post by alexlaird87 on 2011-07-28
"navigate to the /pool/main/n folder.  There you will find 2 folders:   ndisgtk and ndiswrapper.  Do the following:"

I got to the /n folder, but it only contained the ndiswrapper folder, no ndisgtk. What should I do now?

I only got through the first 3 points;


[LIST]
[*]go to the ndiswrapper folder first
[*]double-click the  ndiswrapper common file to begin it's installation.   It will probably  ask for your password - just  type your normal  password - it just won't  show on the screen.  Wait for this to complete.
[*]Double-click on  the ndiswrapper utilities file and it will begin  its' installation.   If prompted, enter your password.  Wait for this to  finish.
[/LIST]

---

### Post by alexlaird87 on 2011-07-28
also I have no access to a wired internet connection

---

### Post by anewguy on 2011-07-28
Do you see ndiswrapper common and ndiswrapper utilities?  If so go ahead and install those.  Copy all of those Windows driver .inf and .sys files to your Ubuntu desktop.

Now, remembering that in these instructions bcmwl5.inf is the name I'll be using - if yours is something different be sure to substitute:
[LIST]
[*]Open a terminal Window (applications/accessories/terminal)
[*]type:
[/LIST]
cd ~/Desktop

sudo ndiswrapper -l <press enter> Type your normal password - it just won't show on the screen.

If anything was returned from this statement, do the following:

sudo ndiswrapper -r xxxxxxxx <press enter> Where "xxxxxxxx" it the name returned in the first command.

sudo ndiswrapper -i bcmwl5.inf <press enter>

sudo modprobe ndiswrapper <press enter>

sudo depmod -a <press enter>

Next we need to blacklist the existing modules so they don't conflict.  I'm hoping I'm remembering them all:

sudo gedit /etc/modprobe.d/blacklist.conf <press enter> This will open the blacklist file in an editor.

Scroll to the end of the file and add the following lines:

blacklist ssb
blacklist b43
blacklist b43-legacy

Save the file and exit the editor.

Now we want to also be sure that ndiswrapper gets loaded at boot time:

sudo gedit /etc/modules <press enter>

Scroll to the end of the file, then add the following line:

ndiswrapper

Save the file, exit the editor.

sudo shutdown -r now <press enter>  This will restart you system.

Once you system is back up, look in network manager and see if any wireless networks show now.

It's too bad you can't find ndisgtk - it takes away all the typing you just had to do!

Post back and let us know the outcome.

Dave ;)

---

### Post by alexlaird87 on 2011-07-28
I have unpacked the XP drivers several times, but so far I can't find any files ending in .inf

---

### Post by alexlaird87 on 2011-07-28
also I managed to get a copy of ndisgtk working, just now no INF files.

---

### Post by anewguy on 2011-07-28
What are the names of the Windows files you have found?  I know it needs the .inf file, but if the file names look like what I think they should be, I may be able to get you a copy anyway.

---

### Post by lkraemer on 2011-07-28
I created a HOWTO: for the Broadcom and 10.04 which should also work
on later versions, because the firmware is missing.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

But, since you are well on the way with ndiswrapper, it's a bit late to switch
methods now.

lk

---

### Post by anewguy on 2011-07-29
> **lkraemer said:**
> I created a HOWTO: for the Broadcom and 10.04 which should also work
on later versions, because the firmware is missing.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

But, since you are well on the way with ndiswrapper, it's a bit late to switch
methods now.

lk

Hey LK - how are you doing?  I orginally was having the user try ndiswrapper - hopefully with ndisgtk - because it *should* have been a quick fix.  I do prefer the firmware cutter, etc., but just thought since the OP was trying ndiswrapper I'd try to help them through that.  I may regret that ;)

If I don't get the information back on the driver files fairly soon, I'm going to recommend the OP work with you  If they already had the Windows drivers it should have been just a couple of clicks and it would be working, especially since they apparently have no other internet connection on that PC.

Just wanted to say "hi!" again and let you know I really appreciated your input!

Dave ;)

---

