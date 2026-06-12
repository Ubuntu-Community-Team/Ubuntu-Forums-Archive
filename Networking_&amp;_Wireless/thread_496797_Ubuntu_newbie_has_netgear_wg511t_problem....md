---
title: "Ubuntu newbie has netgear wg511t problem..."
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by sloeren on 2007-07-09
Hello,

I just installed Feisty on my old laptop, since I'm considering "making the switch" as they say.
Everything went well during installation, however, I got a message concerning restricted drivers and something about proprietary software. In the restricted drivers panel "Atheros Hardware Access Layer (HAL)" is marked enabled and in use, but I cannot connect to my wireless network.
I found some information here [http://ubuntuforums.org/showthread.php?t=38972&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=38972&page=1&pp=10) but this is almost Chinese to me...and I don't seem to have the HAL Status 13 "condition"
Can anyone talk me through getting my wireless adapter to work? (I do know how to open a terminal window ;-)

Thanks!
Sloeren

---

### Post by t4thfavor on 2007-07-09
if you are using network-manager (the icon on the taskbar in the top right) get rid of it and install wicd.

Works much better. I have never ever been able to get it to work with anything but the most basic, and unencrypted wlans.

I will bet that will work perfectly.

sudo apt-get remove network-manager; sudo apt-get install wicd

That should handle it just fine.
Note: wicd will be located under Applications->internet->wicd

---

### Post by sloeren on 2007-07-09
I removed network manager, but when I try to install wicd, I get the error: Couldn't find package wicd...
Where is this package? I can't find it on my ubuntu installation disk neither...

Thanks!
Sloeren

---

### Post by kevdog on 2007-07-09
Oh, I wish you hadnt removed network manager!!  Network manager or wicd is not the cure or cause of your problem.  Its likely a driver issue.  Did you install any drivers for the card, and if so, how did you do it!  If you dont know can you type the following in the command prompt and cut and paste the output (may need USB stick to transfer to a different computer)

lspci -nn
lshw -C network

---

### Post by t4thfavor on 2007-07-09
All I did was type sudo apt-get install wicd 

Try typing "sudo apt-get install wic" and hitting tab 2 times.

Or google it, I know their homepage has a .deb file for all distros.
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by sloeren on 2007-07-09
I did not install any divers for the card...

Here's the info you requested:

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:04.0 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:04.1 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1978 Maestro 2E [125d:1978] (rev 10)
00:09.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0449] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility P/M AGP 2x [1002:4c4d] (rev 64)
06:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5212 802.11abg NIC [168c:0013] (rev 01)



lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@06:00.0
       logical name: wifi0
       version: 01
       serial: 00:09:5b:c4:e9:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c00ffff irq:11


Thanks!
Sloeren

---

### Post by t4thfavor on 2007-07-09
I was working from experience though, I have a Cisco card that is Atheros which gave my fits until I uninstalled network-manager, and installed wicd.

After Wicd install I have no more problems.


EDIT: This card also worked fine until feisty.

---

### Post by kevdog on 2007-07-09
It looks like a driver conflict between your card and the built-in linux driver.  What this basically means for you is that just like about everyone here in the forum you will have to go through an installation process to install your drivers.  The two methods I know of for you are either ndiswrapper or madwifi.  Here is what I pulled off the ndiswrapper site:

> #
Card: Netgear WG511T 108Mbps Cardbus adapter (with super G)

    *
      Chipset: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
    *
      pciid: 168c:0013
    *
      Driver: Windows XP driver available on the Netgear CD: netw511.inf + wg511nd5.sys Native
    *
      Driver: MadWiFihttp://madwifi.sf.net/
    *
      Other:Tested with ndiswrapper 1.2 source compile Note: It&#8217;s needded 2.6.11.7 kernel with no ACPI support (otherwise kernel risks to crash)


Notice that this seems to state the same thing -- either driver off cd, or madwifi.  Before you make up your mind which way to decide, do you have the windows xp drivers they mention??  If you dont, then madwifi is the answer.

---

### Post by sloeren on 2007-07-09
Since I don't have the original drivers, I downloaded the madwifi drivers.
There is only one compressed file.
Is this a driver package for all Atheros based wifi adapters?
How do I install it?
I downloaded the file unto a usb-stick.
Is there a way for me to reinstall network-manager?

Thanks!
Sloeren

---

### Post by t4thfavor on 2007-07-09
I have the same chipset in my card.

It works out of the box with no questions asked. You should have had to do nothing but plug it in and connect to the network.
lshw -C network =
*-network DISABLED
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@03:00.0
       logical name: wifi0
       version: 01
       serial: 00:40:96:ae:49:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:64000000-6400ffff irq:18

If you install the windows cd drivers you will not get access to many of the advanced features of the card such as monitor mode, and packet injection. This  may not be a big deal to you, but I would prefer native over a Windows compatability layer.

I would try the easier stuff first, and if that fails, then you can work on drivers.

If you get an ath0 when you do an iwconfig on the command line, your drivers are most likely working just fine.


To reinstall network-manager

sudo apt-get install network-manager;

---

### Post by sloeren on 2007-07-09
iwconfig gives me this:

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:121501  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by t4thfavor on 2007-07-09
Its working just fine, you just need to either manually issue the commands to connect to the network, or use wicd.

Here is my network connect command (key edited of course).

sudo iwconfig ath0 essid "Some SSID here" key SomeKeyHereInHexNotString

Don't forget to broadcast for an IP using.

sudo dhclient ath0

My office still uses wep, but I think the process is the same for wpa.

---

### Post by sloeren on 2007-07-09
When I type

sudo apt-get install network-manager

I get

Package network-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package network-manager has no installation candidate

---

### Post by stchman on 2007-07-09
> **t4thfavor said:**
> if you are using network-manager (the icon on the taskbar in the top right) get rid of it and install wicd.

Works much better. I have never ever been able to get it to work with anything but the most basic, and unencrypted wlans.

I will bet that will work perfectly.

sudo apt-get remove network-manager; sudo apt-get install wicd

That should handle it just fine.
Note: wicd will be located under Applications->internet->wicd

I have Network Manager working on a WPA2 encrypted wireless network.

---

### Post by t4thfavor on 2007-07-09
That is funny since I tested out all of my commands before I posted them. 

The only thing I can think of is that you do not have the correct repos installed. 

I have enabled all of the standard ubuntu repos through the software sources app located under 
System-> Administration->Software Sources

Like I said I think your better off without network-manager. I know I am.

---

### Post by t4thfavor on 2007-07-09
> **stchman said:**
> I have Network Manager working on a WPA2 encrypted wireless network.
Sorry for the double post.

I am aware it will work in some situations, but I have had nothing but issues with it. It seems to work great until you switch networks a few times, then it either stops alltogether, or works very intermittently.

I have found while using an atheros card wicd is just much more reliable. 

I used network-manager quite a bit with my intel card without too many problems.

It seems that the problem is amplified if the ssid is set to disable broadcasts.

---

### Post by kevdog on 2007-07-09
If you want to reinstall network manager -- it may be on the ubuntu installation cd.  Here is how to do it:
All commands typed at command prompt:

1. Put ubuntu installation cd in driver - wait for it to "spin up"
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install network-manager

---

### Post by sloeren on 2007-07-09
All of the standard repos seem to be enabled, but since I can't connect to the internet because I can't get my netgear card to work, maybe I don't have access to all of these repos, or do I have that all wrong.
Also

sudo iwconfig ath0 essid "Some SSID here" key SomeKeyHereInHexNotString (with the correct values filled out)
sudo dhclient ath0

did not fix my problem. I still cannot go online...

Also 

sudo dhclient ath0 

gave me the return listed below

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:09:5b:c4:e9:c0
Sending on   LPF/ath0/00:09:5b:c4:e9:c0
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by sloeren on 2007-07-09
Hi Kevdog,

I tried your network-manager reinstall, but

sudo aptitude install network-manager

gave me the return listed below

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No candidate version found for network-manager
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by t4thfavor on 2007-07-09
Stupid question, Did you replace SomeSSID HERE with the ssid of your network?
Did you replace the key with your network key?

I just have to make sure since some users would take this literally.

Here is my iwconfig after issuing that same command.
Note that command is case sensative.
ath0      IEEE 802.11g  ESSID:"MySSID"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:0D:72:27:51:D1   
          Bit Rate:5 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/94  Signal level=-73 dBm  Noise level=-87 dBm
          Rx invalid nwid:1571  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sloeren on 2007-07-09
I'm not THAT newbie, t4thfavor ;-)
Although, I did just omit the key parameter, since I disabled my router's protection for the time being.

S

---

### Post by t4thfavor on 2007-07-09
Never know. 

Try the ssid in quotes and make sure you typed it correctly. 

I know your card works out of the box, I am using basically the same one right now.

Keep trying, and I will check back after I get home from work today. 
We can get some kind of solution working.

It would probably help if you weht to the wicd site and downloaded the deb file for it. 
If your not using encryption, and the SSID is broadcasting this should be a no brainer:(

Good luck.

---

### Post by sloeren on 2007-07-09
By the way, kevdog thought it would be a driver issue.
Is this the case?
If so, how do I install those madwifi drivers I just downloaded?
If not...what the hell is wrong here???
Sorry, just a bit frustrated since I know too little of Linux to troubleshoot this myself...

Thanks for all the help guys!
S

---

### Post by sloeren on 2007-07-09
Ah, but the ssid is not broadcasting...

---

### Post by sloeren on 2007-07-09
I installed the wicd deb package and I got the message:

The NetworkManager applet could not find some required resources. It cannot continue.

Sigh...

---

### Post by stchman on 2007-07-09
> **t4thfavor said:**
> Sorry for the double post.

I am aware it will work in some situations, but I have had nothing but issues with it. It seems to work great until you switch networks a few times, then it either stops alltogether, or works very intermittently.

I have found while using an atheros card wicd is just much more reliable. 

I used network-manager quite a bit with my intel card without too many problems.

It seems that the problem is amplified if the ssid is set to disable broadcasts.

I disagree, I go over to my friend's house and use his WPA encrypted network.  I then go over to my dad's house and use his WPA2 encrypted wireless network.  Maybe you are running into the problem of you need to have your MAC address added to the MAC filter of a network you are trying to connect to.

I also can connect to Starbucks, Bread Co, etc., but those are unencrypted networks.

Now I will agree that network manager has trouble connecting to a network that does not broadcast its SSID.  As long as the SSID is broadcasted no problem.

Hidden SSID is WAY overrated as far as wireless security.  Don't think that just because your SSID is hidden that it is now invulnerable.  MAC filtering with WPA2 encryption with a least a 32 character passphrase will make your wireless connection VERY secure.

---

### Post by kevdog on 2007-07-09
I guess network manager isnt on the CD then, sorry.  I was taking a stab in the dark.  Im going to sit this one out for a while.  While it is true that you would be better off if you could get the built-in driver to work as suggested, it might not happen.  Im going to let you experiment for a while.  If nothing works, then we will try to install another driver.

It is kind of strange however that t4thfavor states that the exact same card for him works out of the box, but for you, it doesnt.

Getting wireless to work for Ubuntu is probably the biggest drawback to using Ubuntu.  Hang in there.  Once you get it, you will like everything else.

---

### Post by sloeren on 2007-07-09
Well, after installing wicd, getting the error message and still not being able to go online, I decided to reboot my machine and low and behold, I can go online.
Dunno what did it, but it's working.
I do however have a pretty weak signal for being right next to the router, only 57%
This used to be (in windows xp then) 100% at the same spot...
Any ideas?

Thanks!
S

---

### Post by imdano on 2007-07-09
> **sloeren said:**
> I installed the wicd deb package and I got the message:

The NetworkManager applet could not find some required resources. It cannot continue.

Sigh...Make sure you uninstall Network Manager.  It conflicts with wicd.  You'll need to remove both the network-manager and network-manager-gnome packages.

---

### Post by t4thfavor on 2007-07-10
I guess all it needed was a nice reboot :) 

I have a different card, just the exact same chipset. and I assure you it works for me out of the box and every time (after removing network-manager).

You said that the card was working just fine after a reboot, kudos to you. As I have said many times I still recommend wicd. For even more cinsistancy I recommend the command line over anything else. 

If your going to use GNU/Linux your going to have to learn at least a little about the CLI.

Don't worry, it will come to you, and when it does you will be wishing you could use bash whenever you get on a windows box.

---

### Post by clappr on 2007-08-01
Just wanted to say that the advice given in this thread was invaluable.

My system specs:
Toshiba M45-S359  
Netgear WG511T
Ubuntu-Feisty Fawn

How it worked:

-Downloaded WICD from sourceforge.net to a USB flashdrive
-Removed Network-manager, (keep in mind that you may lose internet connectivity)
-Opened flash drive and selected/install  WICD (automatically installed)
-right click the toolbar and added a network monitor icon.

Runs great!  Thanks to all who contributed to this thread and who are making this community better!  6 weeks ago I knew nothing about Linux and was extremely pissed off at Win XP's unreliability and expenses.  I completely dumped windows and can now enjoy my computer again instead of troubleshooting constantly!

---

