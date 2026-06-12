---
title: "First time user"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Dymmesdale on 2009-04-24
Hi, I am trying out Linux for the first time, hoping to eventually be able to get by without Windows.

I am using an Ubuntu 8.04 live cd, and I am having trouble connecting to a wireless network.  Wehn I click on the Network Manager icon, the drop down menu appears, but the wireless network option doesn't respond when I click on it.  I think it may be an issue with my Windows drivers, and I'm not sure how to install new ones.  I would appreciate some help, thanks!:)

---

### Post by durand on 2009-04-24
If you go to System > Administration > Hardware Drivers, you should be able to find your wireless card. Since ubuntu does not have a licence to distribute these drivers, it is not on the cd so you will need an internet connection to install the drivers :( Maybe you could plug in a network cable?

---

### Post by ajgreeny on 2009-04-24
It will depend on your wireless adapter chipset as to how easily you can connect.  What hardware or chipset do you have?  It may also be worth trying the newer 9.04 which I think has much updated wireless driver support.

---

### Post by MockY on 2009-04-24
You are better off trying a later version. Since 9.04 was just released, try that one out.

---

### Post by sandyd on 2009-04-24
8.110 and 9.04 have WAY better support on wireless drivers than 8.04 :)

---

### Post by Dymmesdale on 2009-04-24
I actually burned a 9.04 live cd and tried that first, but the wireless network option was greyed out on that one too I tried 8.04 after that because i thought since 9.04 was still beta, it might not be as stable.  I am using a Dynex G Desktop Card (according to windows' wireless connection properties box), i'm not sure what chipset it is.  Unfortunately, plugging in a cable would be difficult without drilling holes into my house and stuff, so I was hoping to be able to get the wireless working.

---

### Post by lindsay7 on 2009-04-24
Well one relatively cheap way would be to buy a usb wireless card that works with Ubuntu. After reading lots of posts I found that the Linksys model WUSB54GC worked, I bought one and it worked fine.  My router is sort of far from the computer that uses the wireless card and I looked for a usb adapter that would work at longer distances. I read about the Edimax High Gain Model EW-7318USG that has an external antenna and ended up getting one of these. It works super at the longer distance.

I might add that initially I had a Dynex G USB adapter, Ubuntu would not recognize it at all.

---

### Post by lisati on 2009-04-24
One thing that's easily overlooked: does your adapter have some kind of switch to turn it on or off? Both my laptops have have one.

---

### Post by Dymmesdale on 2009-04-25
> **lisati said:**
> One thing that's easily overlooked: does your adapter have some kind of switch to turn it on or off? Both my laptops have have one.

Not that I know of...how much do those USB wireless cards usually cost?

---

### Post by lisati on 2009-04-25
> **Dymmesdale said:**
> Not that I know of...how much do those USB wireless cards usually cost?

It can depend where you live: not counting Bluetooth (which is another story) the cheapest USB wireless adapter I could find at one of my local outlets was $NZ59, and PCI cards that go inside desktops started about the same price.

---

### Post by Dymmesdale on 2009-04-25
So is it safe to say that I will need new hardware to connect to wifi using ubuntu? if that is the case, is there another distro you could recommend? Somoeone yold me I should try gentoo.

---

### Post by Dymmesdale on 2009-04-25
Would it help if I installed it instead of using a live cd?

---

### Post by nandemonai on 2009-04-25
> **Dymmesdale said:**
> So is it safe to say that I will need new hardware to connect to wifi using ubuntu? if that is the case, is there another distro you could recommend? Somoeone yold me I should try gentoo.

First time user trying gentoo? Whoever told that is crazy.

You have to build gentoo yourself, from source.

---

### Post by ubuntu27 on 2009-04-25
Hello Dymmesdale. You said that you tried Ubuntu 9.04 (Jaunty) on the LiveCD/DesktopCD.

Did you try going to System menu---->Administration---> Hardware Drivers?
Check if there is an proprietary driver available for you network card.

Also, when did you download Ubuntu 9.04? Was it Beta or RC (Release Candidate) version?



Also, do not try Gentoo. It is not meant for new users.

Maybe you should try [CrunchBang Linux]("http://crunchbanglinux.org/"), [Fedora]("http://fedoraproject.org/"), or [OpenSuse]("http://www.opensuse.org/")

---

### Post by -kg- on 2009-04-25
One other thing that I notice has not been mentioned yet.  You say you are using Jaunty from the Live CD...do you have WEP or WPA security set on the wifi on your modem?  If so, then yes, you will need to install Jaunty before you can access your wifi network.

When you access a wifi network that is WEP or WPA enabled, you must enter your security key.  When running Ubuntu from a Live CD, it has nowhere to store that security key, therefore you can't access your network.

I found that out on my laptop, which I run using wifi to my DSL modem.  I could see the network (and my neighbor's) but was unable to connect.  Only once I installed could I enter my WEP security key and access the network.

---

### Post by lindsay7 on 2009-04-25
BestBuy in the U.S. for the Linksys is about $39.  I thing the price for the price from Egghead for the Edimax was about $29 on sale. There is a good tutorial on the Edimax on Youtube for running this USB adapter on Ubuntu.

---

### Post by NightwishFan on 2009-04-25
Perhaps you can use Windows drivers for it.

Did you look in the hardware drivers program?

press alt+f2 and type: jockey-gtk
press enter.

See if you have drivers there. If not then follow this tutorial to use ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by Lazy-buntu on 2009-04-25
Seriously, try 8.10 or better yet 9.04.

I could not even get my wired internet to work with 8.04. I was using Fedora for almost a year, but when I tried 8.10 it just worked. After I installed 8.10 and updated, I went to the Restricted Drivers (now I think it's Hardware Drivers) and enabled my Broadcom drivers.

I would try that before doing anything else. Besides, why would you use 8.04 when there are two newer releases?

---

### Post by NightwishFan on 2009-04-25
8.04 is still supported. I would try to get his working rather than install a new one. :popcorn:

Look up your cards specific model and see if anyone else got it to work. Or try ndiswrapper. (I have no hands on experience with wireless, however I have heard a lot).

---

### Post by Dymmesdale on 2009-04-25
Ok, it showed a B3 Broadcom driver (or something close, I know I should have written it down), but it wasn't activated.  If I activate that, will it mess up my connectivity in Windows?

I think I am going to go ahead and install it, but just defragging will probably take all day:(.  Thanks for the help so far!

---

### Post by albinootje on 2009-04-25
> **Dymmesdale said:**
> it showed a B3 Broadcom driver

Can you post the output of the following (in a terminal) :
```

lspci
lsusb
sudo lshw -C network

```
Then it will be easier for us to help you, and possibly more quickly too.

---

### Post by Simian Man on 2009-04-25
It will work but you must install it (not just the Live CD) and plug it into an ethernet connection.
[LIST=1]
[*]Download 9.04
[*]Install it
[*]Plug it into a wired connection
[*]Install the restricted drivers (if it give you two choices, go with SATA)
[*]Profit :)
[/LIST]

---

### Post by Dymmesdale on 2009-04-25
i will install 9.04, BTW. How much space should I partition for it? I have about 13 GB free at the moment, but I can back as much up to DVD's as needed, if necessary.

---

### Post by albinootje on 2009-04-25
> **nandemonai said:**
> First time user trying gentoo? Whoever told that is crazy.

I agree that Gentoo Linux is not meant for Linux beginners.
> 
You have to build gentoo yourself, from source.
You don't have to build Gentoo completely from source, there's the stage3 installation.

---

### Post by Dymmesdale on 2009-04-25
Here is the output.


ubuntu@ubuntu:~$ lspci 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3) 
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3) 
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2) 
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) 
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) 
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2) 
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) 
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) 
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) 
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) 
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3) 
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) 
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) 
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) 
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
01:0b.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) 
05:00.0 VGA compatible controller: nVidia Corporation D9M-20 [GeForce 9400 GT] (rev a1) 
ubuntu@ubuntu:~$ lsusb 
Bus 001 Device 002: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
ubuntu@ubuntu:~$ sudo lshw -c network 
  *-network               
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 7 
       bus info: pci@0000:01:07.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 module=ssb 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:1c:df:4e:74:37 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 52:7d:fa:81:b9:84 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

EDIT: I don't think it makes any difference, but I had an external HDD, an iPod, a webcam, and a card reader plugged into USB before I rebooted and went back into Ubuntu, but I took them out.  There's actually a kind of long story behind that, but it's probably for a different forum/thread...

---

### Post by ubuntu27 on 2009-04-25
> **Dymmesdale said:**
> Ok, it showed a B3 Broadcom driver (or something close, I know I should have written it down), but it wasn't activated.  If I activate that, will it mess up my connectivity in Windows?

I think I am going to go ahead and install it, but just defragging will probably take all day:(.  Thanks for the help so far!

Activating Proprietary drivers in UBuntu Linux won't affect windows. In fact anything that you do on Ubuntu Linux won't affect WIndows. UNless of course you specifically do something like accesing the WIndows's NTFS partition and delete files...


For de-fragmenting the hard drive, I recommend you to try [JkDefrag]("http://www.kessels.com/Jkdefrag/") or [Smart Defrag]("http://www.iobit.com/iobitsmartdefrag.html")

---

### Post by Dymmesdale on 2009-04-25
Ok, I downloaded Smart Defrag, and it's running now. When that's done I will reboot and check the disk, and then I will run the install!

---

### Post by albinootje on 2009-04-25
> **Dymmesdale said:**
> 
01:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

Thanks. This might help, although it's a bit old.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)
See also here :
[https://bugs.launchpad.net/ubuntu/+bug/355645](https://bugs.launchpad.net/ubuntu/+bug/355645)
[http://kubuntuforums.net/forums/index.php?topic=3099213.0](http://kubuntuforums.net/forums/index.php?topic=3099213.0)

And i've seen some laptops where you need to use Fn+the-wifi-key to enable the wifi card, just FYI.

---

### Post by por100pre1 on 2009-04-25
> **Dymmesdale said:**
> Ok, I downloaded Smart Defrag, and it's running now. When that's done I will reboot and check the disk, and then I will run the install!

Please be sure to backup your files in an external hard disk drive or removable media before installing. **No operating system installion is 100% error proof.**

---

### Post by -kg- on 2009-04-25
> **por100pre1 said:**
> Please be sure to backup your files in an external hard disk drive or removable media before installing. **No operating system installion is 100% error proof.**

+1

Nor is a hard drive itself, which is a good reason to back up your system regularly in any case, preferably in multiple locations and several different types of media, unless your information isn't *that* important to you.

---

### Post by fballem on 2009-04-25
> **Dymmesdale said:**
> I actually burned a 9.04 live cd and tried that first, but the wireless network option was greyed out on that one too I tried 8.04 after that because i thought since 9.04 was still beta, it might not be as stable.  I am using a Dynex G Desktop Card (according to windows' wireless connection properties box), i'm not sure what chipset it is.  Unfortunately, plugging in a cable would be difficult without drilling holes into my house and stuff, so I was hoping to be able to get the wireless working.

If this is dumb, then please forgive me, but is your wireless adapter enabled? I just got through configuring a laptop and couldn't understand why the wireless networking option was greyed out - until I realised that somewhere in my process, I had accidentally turned off the wireless adapter. As soon as I turned it on, the wireless networking option was enabled and I was able to finish the configuration.

Hope this helps,

---

### Post by Dymmesdale on 2009-04-26
well, unless I have to specifically enable it when I boot into Ubuntu, it is enabled.  I am using it right now (in windows).

---

### Post by Dymmesdale on 2009-04-26
I installed 9.04 to an SD card, because I am still backing up data on my main disk and I got impatient.  I can't connect directly to ethernet...can someone send me a link for the drivers I need, so I can download them in windows and send them to the SD card?

---

### Post by ikisham on 2009-04-26
Here is a simple how-to for you to use its Windows drivers (which you may have in cd or get in the net or copy from your Windows system):
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/)

---

### Post by Dymmesdale on 2009-04-26
Thanks for the link!  I am going to be smart this time and save the page to USB so I can read them while disconnected.  I will go try it out.

---

### Post by Dymmesdale on 2009-04-27
Ok, I followed the instructions that came with ndiswrapper to install it (make uninstall...make...make install[btw is this generally how you install things in linux?]).    I downloaded the drivers from the link, and installed them with ndiswrapper (sudo ndiswrapper -i bcmwl5.inf or whatever it was actually called).    I rebooted, and the wireless networks option in the network manager drop down menu was still greyed out.  When I put ndiswrapper -l into the command line, it says driver installed (but not the name of the driver), and hardware present (alternate driver ssb).  I blacklisted ssb and rebooted, and the wireless networks option was still greyed out.  any ideas?  (Sorry I don't have the specific lines of code and stuff from the command line, I didn't think to save them)

---

### Post by emeraldgirl08 on 2009-04-28
Dym. What type of encryption are you using??? If it's WPA then try switching it to WEP- Hexadecimal.

I had major issues with WPA on my laptop so I switched over to WEP (reluctantly) and it worked.

Hope you get all this sorted out. I was in the same boat as you last week! *$indow$* wireless was fine but my Ibex wireless was as *"dead as a doornail!"*

---

### Post by Dymmesdale on 2009-04-28
Someone else originally set up my wireless network, and it was using WEP.  As far as I know, nothing has changed and it is still using WEP, but it is possible hat that could have changed.  I don't know a whole lot about wireless networking, so I haven't changed anything myself, but for about a year there was someone else living in my house that would sometimes randomly change things.

How would I check what kind of encryption I have?

---

### Post by ikisham on 2009-04-29
Hi, maybe you should open another thread in the 'Networking and Wireless' section with a link to this one. Sorry for not being so helpful but I have no wireless here.

---

