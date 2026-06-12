---
title: "HowTo: Broadcom Wireless on Hardy"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Ayuthia on 2008-05-03
As you now know or will find out, the developers of the native Linux Broadcom module have developed a new module for the 2.6.24 kernel.  With this change, the bcm43xx modiule has been depreciated.  The b43, b43legacy, b44, and ssb modules have been introduced.

Like the bcm43xx module, people have mixed feelings about whether the new b43/b43legacy modules work well or not.  Some feel that the connection speed is not quite there and others experience connection loss periodically.  Those who do not like it are using NDISwrapper.  This post will cover how to install the firmware to get the b43/b43legacy module.  This post is not going to cover the NDISwrapper process mainly because there are many different Broadcom drivers and a post will not do it justice.  I will recommend the following site:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If you are looking for a troubleshooting guide, please check out:
NDISwrapper - [http://ubuntuforums.org/showthread.php?t=780590](http://ubuntuforums.org/showthread.php?t=780590)
b43/b43legacy - [http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692)

**Current non-working chipsets--Ones that do not work with b43/b43legacy so NDISwrapper is the only option** (check by doing lspci -nn and look for something like [14e4:43XX]):
(From [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43))
The 802.11a part of the 4309 and 4312 is not supported 
Any wireless-N features
BCM 4328/4329

(From the b43 mailing list)
(Kernel versions < 2.6.24-17) Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01) **if kernel version >= 2.6.24-18, install linux-restricted-modules**

(Found in Ubuntu)
14e4:4311 (rev 02) (Fixed in 2.6.24-18)
14e4:4312 (rev 02) (Possibly fixed in 2.6.24-17--Can anyone confirm this?)

[B]Option 1
For those with a working internet connection[/B]
In the Terminal/Konsole/xterm window do the following:
```
sudo aptitude install b43-fwcutter
```
Once it downloads the package, it will ask you if you want it to download the firmware for you.  Select yes and it will install it for you.  Then do the following:
```
sudo ifconfig wlan0 up
```You should be wireless!

For those of you who are configuring your /etc/network/interfaces, you might need to do:
```
sudo /etc/init.d/networking restart
```That will restarting your network and will read through the /etc/networking/interfaces to connect.

[B]Option 2
For those without a working internet connection[/B]

**If you have a Hardy install CD, **
Insert your CD and do the following:
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter
```
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**
Now skip down to the Downloading Firmware section.

**If you don't have a Hardy install CD**
You will have to find a place with a working internet connection.  Go to this link:
[http://packages.ubuntu.com/hardy/utils/b43-fwcutter](http://packages.ubuntu.com/hardy/utils/b43-fwcutter)
Download the version that you need--amd64 for 64-bit and i386 for 32-bit.  Copy the file to your home directory and do the following:
64-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-1_amd64.deb
```
It is possible that the _011-1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

32-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-1_i386.deb
```
It is possible that the _011-1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

**Downloading Firmware**
Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
```
Copy those files to your home directory.  In the Terminal/Konsole/xterm window do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

For those of you who are configuring your /etc/network/interfaces, you might need to do:
```
sudo /etc/init.d/networking restart
```That will restarting your network and will read through the /etc/networking/interfaces to connect.

That should be it!

Another option (if you have a working internet connection) in Kubuntu is to go into System->Hardware Driver Manger.  Once you have entered your password (if you have not done anything as root recently) the Hardware Driver screen will appear.  It should have Broadcom B43 wireless drvier as an option.  Click on the Enabled checkbox and it should do the b43-fwcutter install for you.  It will ask you if you want it to find the firmware for you.  Select yes and you should be set.

Ubuntu users should have something similar menu item (System->Adminstration->Hardware Driver ?) or a pci card symbol on the panel that you can click.

**Note for users of encryption:** If for some reason you cannot connect, you might need to enter the password through Network Manager (wireless icon in the panel) and it should ask you for a keyring password.  From there you should be able to connect.  See post #30 for more information.  Thanks esteckis!

Good luck!  Hope this helps.

**Configuration Tool**
Here is a new tool I am trying to add that will help configure your Broadcom wireless card.  It will help set up the blacklisting and add the modules needed so that it will work on reboot.  Just download the attachment and extract the file.  If you want to do it from the Terminal:
```
tar -cvvzf toolbox_*.tar.gz
```.  The application is in the early stages but it does make backup copies for you.  Since it is in the early stages, use at your own risk.

In order to run the program, you will need to click on toolbox.py or from the terminal:
```
./toolbox.py
or
python toolbox.py
```

---

### Post by xomp on 2008-05-04
This does not work. The card shows up as enabled in Hardware Driver and shows all the networks around me but I cannot connect to anything. It will not obtain a lease on any address.

---

### Post by Ayuthia on 2008-05-04
Can you post your lspci -nn and did you try the b43 process or did you try the ndiswrapper howto?

EDIT:
Another thing to add, when you use iwlist scan, does it show a lot of other wireless connections using the same channel as you?  I have seen a few people using the b43 driver that has received interference from other wireless routers using the same channel.  Once they changed the channel, things were fine.

One other thing.  I just read your other post and it mentions that it comes with an attached wireless adapter (prism).  Unfortunately, this post only works with the Broadcom versions.

---

### Post by xomp on 2008-05-06
Here is my lscpi -nn

> xomp@medic:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:04.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:0450] (rev 02)
02:06.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:06.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller [8086:1038] (rev 42)
02:0e.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:0e.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:0e.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


Here is my iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     No scan results


I have disabled the other wifi adapter (the prism2) since linux is incapable of utilitzing it, hence the reason I purchased this Belking Wireless G.. I am 'trying' to use the propietary driver and not ndiswrapper at all for this.

---

### Post by Ayuthia on 2008-05-06
> **xomp said:**
>  I am 'trying' to use the propietary driver and not ndiswrapper at all for this.
Thanks for the clarification and the information.

Can you provide the results for:
```
lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
lshw -C network
```
This will tell us what modules are loaded and what your wireless card is trying to use.

---

### Post by mikeymo1741 on 2008-05-06
The problem I seem to be having is that the connection gets dropped, but only when I am connected to a WEP-enabled access point.   To an unsecured network I can connect all day long without an issue.   

Once I connect to my WEP-enabled home network, the connection will randomly drop, and I will get a Connection Manager window asking for the WEP key, although that is saved in the connection settings.  It might reconnect, it might not, but if it doesn't, that SSID will not even show up in the scan unless I reboot.  When I reboot, it connects fine on it's own until the connection drops.  

As I said, to an open network, there are no issues.  

Any thouughts? 

>  lspci -v | grep Broadcom
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


I am using the b43 driver, BCM43XX is blacklisted.

---

### Post by Ayuthia on 2008-05-06
> **mikeymo1741 said:**
> The problem I seem to be having is that the connection gets dropped, but only when I am connected to a WEP-enabled access point.   To an unsecured network I can connect all day long without an issue.   

Once I connect to my WEP-enabled home network, the connection will randomly drop, and I will get a Connection Manager window asking for the WEP key, although that is saved in the connection settings.  It might reconnect, it might not, but if it doesn't, that SSID will not even show up in the scan unless I reboot.  When I reboot, it connects fine on it's own until the connection drops.  

As I said, to an open network, there are no issues.  

Any thouughts? 



I am using the b43 driver, BCM43XX is blacklisted.

Does anything show up in dmesg when the connection drops?  Also, is your SSID the only one that is missing?  If it is, you might try a different channel on your router to see if it makes a difference.

---

### Post by mikeymo1741 on 2008-05-06
I'll have to make note of the log next time it happens.   

Yes it's only my SSID that drops.   I'll try switching channels, but it never happens from Windows on the same laptop in the same place.    Besides, if the connection dropped, I would assume it should reconnect on it's own without having to re-enter the key.

---

### Post by Ayuthia on 2008-05-06
> **mikeymo1741 said:**
> I'll have to make note of the log next time it happens.   

Yes it's only my SSID that drops.   I'll try switching channels, but it never happens from Windows on the same laptop in the same place.    Besides, if the connection dropped, I would assume it should reconnect on it's own without having to re-enter the key.
The driver that Windows uses and what Ubuntu uses are different.  What could be happening is that there is just enough interference on that channel that it cannot find your SSID.  When that happens, it cannot re-establish the signal because it cannot find it.  When that happens, you get the WEP key question.

If you want it to be more like Windows, you can try NDISwrapper.  It uses the Windows driver to communicate with your wireless card.  No guarantees that it will be exactly like Windows though. :)

---

### Post by mikeymo1741 on 2008-05-06
I was using ndswrapper with Gutsy and had no issues.  I think I might go back to it... :(


When I look at availible networks, mine is always the strongest.  Besides, this has happened when it was in the same room as the silly router, five feet away...

---

### Post by Ayuthia on 2008-05-06
> **mikeymo1741 said:**
> I was using ndswrapper with Gutsy and had no issues.  I think I might go back to it... :(


When I look at availible networks, mine is always the strongest.  Besides, this has happened when it was in the same room as the silly router, five feet away...If you do switch over, just be aware that ssb needs to be loaded after ndiswrapper.  If you don't have a Broadcom ethernet card (the wired one), you should be able to just blacklist b43 and ssb.  Check with lsmod|grep ssb before blacklisting to make sure that nothing else is using it.

---

### Post by Apipote on 2008-05-06
Hello
This procedure, works in broadcom 4311 rev 2 ?
Thanks
Regards

---

### Post by bcardarella on 2008-05-06
To contradict what Apipote said, this procedure does *not* work with broadcom 4311 Rev 2. I just tried it, didn't work. Sorry.

---

### Post by Ayuthia on 2008-05-06
bcardarella and Apipote-
bcardarella is correct.  The 4311 rev 02 and 4312 rev 02 cards to not work on Hardy.  There was a patch attempted right before the release, but they broke other cards so the patch was backed out.

NDISwrapper is the way to go.  Here is a link that might help.  The post was created by someone who as the same wireless card as yours.

[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by summuner848 on 2008-05-06
AAAAHH!!! I don't know what i did!? For some reason, i get this:

user@user-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
___

Does anyone at all have an idea of how to fix this?

---

### Post by Ayuthia on 2008-05-06
> **summuner848 said:**
> AAAAHH!!! I don't know what i did!? For some reason, i get this:

user@user-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
___

Does anyone at all have an idea of how to fix this?What does ifconfig show?  It might be possible that yours could be eth1.

---

### Post by Apipote on 2008-05-07
> The 4311 rev 02 and 4312 rev 02 cards to not work on Hardy

Thanks, I will wait Intrepid with kernel 2625
Gracias !!

---

### Post by Dav_Criv on 2008-05-07
Hello, I am running into a problem when i try to install the firmware....i dont know why it is doing this...any help on this would be appreciated!!!
When i try to download the firmware either through the terminal, synaptic package manager, or through hardware drivers it ALWAYS askes me to insert the Ubuntu CD. This is the output i get using the terminal:

davide@computer:~$ sudo aptitude install b43-fwcutter 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libawn0 
The following NEW packages will be installed:
  b43-fwcutter 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/15.8kB of archives. After unpacking 61.4kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)' in the drive '/cdrom/' and press [Enter].

Why does it do this??
any help would be great,
Thank you,
Dav_Criv

---

### Post by Ayuthia on 2008-05-07
You might try
```
sudo apt-get install b43-fwcutter
```
I think that might be the auto-remove feature of aptitude.  Let me know if that resolves the problem.

---

### Post by seuaniu on 2008-05-07
Good guide!  ```
ifup wlan0
```didn't work for me, so I had to ```
sudo /etc/init.d/networking restart
```and it came right up.

Here's the hardware:
```
 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

``` Its a dynex pcmcia card i bought about a year ago.

---

### Post by Handssolow on 2008-05-08
Currently unable to use wifi after yesterday's Hardy upgrade on my wife's PC.  In System>Administration>Hardware Drivers I used a wired connection to download and install the b43 Broadcom driver. I'm stuck. I's there anything wrong with the following? What should I do next?

~$ lspci -nn
00:09.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)
00:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

~$ lsmod|grep -i -e b43
b43                   113952  0 
ssb                    31236  1 b43
mac80211              162708  1 b43
led_class               5124  1 b43
input_polldev           5000  1 b43
rfkill                  7568  3 b43,rfkill_input

$ sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:"OUR ESSID"  
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
Tx-Power=27 dBm   Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
Encryption key:"OUR WEP HEX KEY without quote marks" Link Quality:0  Signal level:0  Noise level:0 Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Ayuthia on 2008-05-08
> **Handssolow said:**
> Currently unable to use wifi after yesterday's Hardy upgrade on my wife's PC.  In System>Administration>Hardware Drivers I used a wired connection to download and install the b43 Broadcom driver. I'm stuck. I's there anything wrong with the following? What should I do next?

~$ lspci -nn
00:09.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)
00:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

~$ lsmod|grep -i -e b43
b43                   113952  0 
ssb                    31236  1 b43
mac80211              162708  1 b43
led_class               5124  1 b43
input_polldev           5000  1 b43
rfkill                  7568  3 b43,rfkill_input

$ sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:"OUR ESSID"  
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
Tx-Power=27 dBm   Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
Encryption key:"OUR WEP HEX KEY without quote marks" Link Quality:0  Signal level:0  Noise level:0 Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Are you able to connect without encryption?

---

### Post by Handssolow on 2008-05-08
Thanks Ayuthia for the support.
To my amazement I've just got my (rather my wife's) Linksys PCI card WMP54GS with Broadcom 4306 rev 03 working. Furthermore it's still working after a reboot. I'm mystified though.

Thinking that my experiments with the ndiswrapper approach had been unsuccessful because I'd lost wlan0 showing in iwconfig, I thought I'd reverted to  Hardy's b43 driver. However I was wrong, 
$ lshw -C network
now shows
 *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:6d:ce:a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Linksys,12/22/2004, 3.100.4 ip=192.168.0.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by Handssolow on 2008-05-08
I read your message Ayuthia as I was about to continue with this posting. It's bad enough for me not knowing why something doesn't work but now I don't know why it works. Since my last post I've looked further. Unfortunately I'm not sure my experiences will be of much help to other having problems with their Broadcom wifi.

in
~$ lshw -C network
seeing that I appeared to be using the ndiswrapper this came as a bit of a surprise considering I'd blacklisted it in
~$ sudo gedit /etc/modprobe.d/blacklist
However, looking in 
~$ cat /etc/modules|grep ndiswrapper
I found several entries for ndiswrapper probably cause by my previous attempts to get my wifi working.

Assuming on the evidence that I was using the ndiswrapper I removed all but one of the ndiswrapper entries and removed the blacklisting. Reboot though and I'd lost my wifi.

So I reverted to blacklisting ndiswrapper and on reboot I've got wifi back but as I've posted
~$ lshw -C network
shows

configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Linksys,12/22/2004, 3.100.4 ip=192.168.0.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Earlier today when I was working on the ndiswrapper approach b43 disappeared from the Hardware Devices menu. So getting stuck with loss of recognition of my wlan0, I decided to revert to b43. After I ran
sudo apt-get install b43-fwcutter
The b43 driver reappeared in the Hardware Devices menu but wasn't enabled.
Later after I had enabled the b43 driver and got my wifi working I assumed that I was back on b43. Looking back though in the Hardware menu I was surprised to see that the Broadcom b43 option had disappeared.

I've no idea how I come to be using the ndiswrapper and bcmwl5 except that's what I was using in Gutsy.

---

### Post by Ayuthia on 2008-05-08
> **Handssolow said:**
> I read your message Ayuthia as I was about to continue with this posting. It's bad enough for me not knowing why something doesn't work but now I don't know why it works. Since my last post I've looked further. Unfortunately I'm not sure my experiences will be of much help to other having problems with their Broadcom wifi.

in
~$ lshw -C network
seeing that I appeared to be using the ndiswrapper this came as a bit of a surprise considering I'd blacklisted it in
~$ sudo gedit /etc/modprobe.d/blacklist
However, looking in 
~$ cat /etc/modules|grep ndiswrapper
I found several entries for ndiswrapper probably cause by my previous attempts to get my wifi working.

Assuming on the evidence that I was using the ndiswrapper I removed all but one of the ndiswrapper entries and removed the blacklisting. Reboot though and I'd lost my wifi.

So I reverted to blacklisting ndiswrapper and on reboot I've got wifi back but as I've posted
~$ lshw -C network
shows

configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Linksys,12/22/2004, 3.100.4 ip=192.168.0.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Earlier today when I was working on the ndiswrapper approach b43 disappeared from the Hardware Devices menu. So getting stuck with loss of recognition of my wlan0, I decided to revert to b43. After I ran
sudo apt-get install b43-fwcutter
The b43 driver reappeared in the Hardware Devices menu but wasn't enabled.
Later after I had enabled the b43 driver and got my wifi working I assumed that I was back on b43. Looking back though in the Hardware menu I was surprised to see that the Broadcom b43 option had disappeared.

I've no idea how I come to be using the ndiswrapper and bcmwl5 except that's what I was using in Gutsy.

The b43 option does disappear from the Hardware Devices Manager when you use NDISwrapper.

Going back to your confusion about why ndiswrapper is coming back, did you by any chance use a script that will load ndiswrapper?  It would have gone into /etc/init.d or else it would be found in rc.local.  If you did, that is what is causing ndiswrapper to keep on haunting you.  That script will unload and load drivers.

Just to take a couple of steps back, when the system loads up, it will go through the blacklist and make sure that none of the modules in the list will load.  It will also go into /etc/modules and see if there are any modules to load (provided that they are not in the blacklist).  Once that is done, anything that happens after that can change things.  For instance, if you wanted to right now to load ndiswrapper and it is blacklisted, all you have to do is sudo modprobe ndiswrapper.  Having the sudo privilege is saying that you know what you are doing.  Going back to using scripts to load things automatically in /etc/init.d or /etc/rc.local is doing the same thing.  It assumes that even though the stuff is blacklisted, it is going to load them as root because it assumes that is what you want.

Hopefully that is what is happening.

It sounds like you have both ndiswrapper and b43 loaded.  Only for this session we can load ndiswrapper:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe ndiswrapper
```
To load b43:
```
sudo modprobe -r ndiswrapper
sudo modprobe b43
sudo ifconfig wlan0 up
```

If you are able to see wireless access points by doing:
```
sudo iwlist scan
```then things are working.

Let me know if that works.  If so, we can then go about cleaning up your entries to whichever one you want.

Just to let you know, your experiences are similar to most people starting out.  Unless you are one of the lucky few that got it working on the first try.

---

### Post by xomp on 2008-05-08
> **Ayuthia said:**
> Thanks for the clarification and the information.

Can you provide the results for:
```
lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
lshw -C network
```
This will tell us what modules are loaded and what your wireless card is trying to use.

This is the output for grep:
> xomp@medic:~$ lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43                   115104  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    32260  1 b43
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd


This is the output for lshw:
> xomp@medic:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:94:48:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.102 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:11:50:9f:cd:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
xomp@medic:~$ 


---

### Post by Ayuthia on 2008-05-08
xomp - 
> **xomp said:**
> *-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network
description: Wireless interface
physical id: 1
logical name: wlan1
serial: 00:11:50:9f:cd:65
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
Ok.  Your lsmod information shows that ndiswrapper is still being loaded.  Just to see if the b43 driver works, we can unload the ndiswrapper module and reload the b43:
```
sudo modprobe -r ndiswrapper b43 ssb
sudo modprobe b43
sudo ifconfig wlan1 up
sudo iwlist scan
```

Your lshw -C network information is saying that your wireless device is wlan1.  Most likely because of the other wireless.  If iwlist is able to find wireless signals, then things look good.  

This will only work for this session.  To make it last, we will have to remove ndiswrapper from loading.

---

### Post by talonstriker on 2008-05-08
Does this work for Broadcome 4401?  I've tried about 4 different HOWTOs and none of them have worked.

EDIT: Pardon my profanity, but OH MY ******* GOD, IT WORKS!  A 1000 internetz to you, good sir.

---

### Post by Ayuthia on 2008-05-08
> **talonstriker said:**
> Does this work for Broadcome 4401?  I've tried about 4 different HOWTOs and none of them have worked.

EDIT: Pardon my profanity, but OH MY ******* GOD, IT WORKS!  A 1000 internetz to you, good sir.
Glad to see it works!  The 4401 is your wired network card.  It would use the b44 driver. :)

---

### Post by esteckis on 2008-05-08
Also I think should be mentioned is that if you use encryption with the wireless device. **Now in Hardy Heron, the Keyring will not let wireless engage until you provide your password and then the wireless will connect.** What happened to me when I first installed Hardy, I had the wireless all set up and it would not connect. Then when I shut the computer down (by being frustrated, LOL) and re-logged on, the keyring pop-up window asked for my password. I entered the password and the wireless has connected every time now.  There is supposedly a fix to have the password automatically entered upon your successful log on. I have not tried it yet because it involves the terminal.  Please note there is another fix where you have to download WCID (I think it was that?).  Well, when you download WCID, your network manager is disabled. This WCID fix uses the NDSwrapper. WCID did not work for me (Broadcom wireless) and I had a heck of a time trying to restore to the prior setup.

[http://www.savvyadmin.com/pam_keyring-automatic-keyring-authentication/](http://www.savvyadmin.com/pam_keyring-automatic-keyring-authentication/)

Above is the keyring fix, I question whether trying it because maybe the team is update this keyring hassle and it might cause problems, I am not sure.

---

### Post by Ayuthia on 2008-05-08
> **esteckis said:**
> Also I think should be mentioned is that if you use encryption with the wireless device. Now in Hardy Heron, the Keyring will not let wireless engage until you provide your password and then the wireless will connect. What happened to me when I first installed Hardy, I had the wireless all set up and it would not connect. Then when I shut the computer down (by being frustrated, LOL) and re-logged on, the keyring pop-up window asked for my password. I entered the password and the wireless has connected every time now.  There is supposedly a fix to have the password automatically entered upon your successful log on. I have not tried it yet because it involves the terminal.  Please note there is another fix where you have to download WCID (I think it was that?).  Well, when you download WCID, your network manager is disabled. This WCID fix uses the NDSwrapper. WCID did not work for me (Broadcom wireless) and I had a heck of a time trying to restore to the prior setup.
Thanks for the information!  I will add that to the post.

As for WICD, it should work for b43 or NDISwrapper.  I am currently using it and I use both NDISwrapper and b43.

---

### Post by esteckis on 2008-05-08
Yes, I am also using the b43 driver. But me being such a linux newbie, I could not get the WICD and NDISwrapper to work. I did not realize what a hassle it was to restore to the prior state.  I was lucky.  Most likely I am doing something wrong with the WICD.

---

### Post by Handssolow on 2008-05-08
> **Ayuthia said:**
> The b43 option does disappear from the Hardware Devices Manager when you use NDISwrapper.

Going back to your confusion about why ndiswrapper is coming back, did you by any chance use a script that will load ndiswrapper?  It would have gone into /etc/init.d or else it would be found in rc.local.  If you did, that is what is causing ndiswrapper to keep on haunting you.  That script will unload and load drivers.

Just to take a couple of steps back, when the system loads up, it will go through the blacklist and make sure that none of the modules in the list will load.  It will also go into /etc/modules and see if there are any modules to load (provided that they are not in the blacklist).  Once that is done, anything that happens after that can change things.  For instance, if you wanted to right now to load ndiswrapper and it is blacklisted, all you have to do is sudo modprobe ndiswrapper.  Having the sudo privilege is saying that you know what you are doing.  Going back to using scripts to load things automatically in /etc/init.d or /etc/rc.local is doing the same thing.  It assumes that even though the stuff is blacklisted, it is going to load them as root because it assumes that is what you want.

Hopefully that is what is happening.

It sounds like you have both ndiswrapper and b43 loaded.  Only for this session we can load ndiswrapper:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe ndiswrapper
```
To load b43:
```
sudo modprobe -r ndiswrapper
sudo modprobe b43
sudo ifconfig wlan0 up
```

If you are able to see wireless access points by doing:
```
sudo iwlist scan
```then things are working.

Let me know if that works.  If so, we can then go about cleaning up your entries to whichever one you want.

Just to let you know, your experiences are similar to most people starting out.  Unless you are one of the lucky few that got it working on the first try.

Thanks again Ayuthia. It does look as though I have both ndiswrapper and b43-fwcutter loaded as evidenced in Synaptic. I hope you will understand that having devoted several hours before I could re-establish wifi on my wife's PC after the upgrade to 8.04, I am reluctant to mess around with it any further.

---

### Post by talonstriker on 2008-05-08
> **Ayuthia said:**
> Glad to see it works!  The 4401 is your wired network card.  It would use the b44 driver. :)
For that I suppose I'd replace b43 with b44 in the initial command.  One a side note, KNetwork manager seems to be unable to connects to weak signals--even though the Wireless Manager in Windows does so effortlessly, do you think that the wrong driver might be the problem?

---

### Post by Ayuthia on 2008-05-08
> **talonstriker said:**
> For that I suppose I'd replace b43 with b44 in the initial command.  One a side note, KNetwork manager seems to be unable to connects to weak signals--even though the Wireless Manager in Windows does so effortlessly, do you think that the wrong driver might be the problem?
Your wired connection should work automatically.  If not, try:
```
sudo modprobe b44
```
If that doesn't do it, you might want to start a post for your wired card and post the lspci -nn for it.

As for weak signals, I have seen the same thing.  I think that the b43 driver is not quite as good as the Windows version.  I have tested that before with NDISwrapper, b43 and Windows and Windows still can connect a little further away.  All the changes that have been made to the bcm43xx and b43 drivers have been making great improvements though.

---

### Post by computer on 2008-05-12
thanxxxxxxxxxxxxxxxxxxx a lot this is work from the first time :)

---

### Post by SurferGTO on 2008-05-16
[http://ubuntuforums.org/showthread.php?t=794816&page=2](http://ubuntuforums.org/showthread.php?t=794816&page=2)

i got my bcm4310 working no problem now using the tips and links provided in this thread. for anyone thats having a problem with that driver install or hardware recognition.

---

### Post by Ayuthia on 2008-05-16
> **SurferGTO said:**
> [http://ubuntuforums.org/showthread.php?t=794816&page=2](http://ubuntuforums.org/showthread.php?t=794816&page=2)

i got my bcm4310 working no problem now using the tips and links provided in this thread. for anyone thats having a problem with that driver install or hardware recognition.
Just as a note on this:
The information provided from SurferGTO's link is for NDISwrapper instead of b43.  Also, the 4310 (14e4:4315) does not work with b43 so NDISwrapper is currently the only option.

SurferGTO-Thanks for adding this!!!

---

### Post by SurferGTO on 2008-05-17
thank YOU ayuthia for providing it in the first place!

---

### Post by rizitis on 2008-05-24
if some one looking for bcm 4329, look here
[http://ubuntuforums.org/showthread.php?t=805631](http://ubuntuforums.org/showthread.php?t=805631)

---

### Post by Ayuthia on 2008-05-24
> **rizitis said:**
> if some one looking for bcm 4329, look here
[http://ubuntuforums.org/showthread.php?t=805631](http://ubuntuforums.org/showthread.php?t=805631)
The information that you posted looks like you are trying to install both the NDISwrapper and native drivers at the same time.  It is recommended that you only do one.  If you do both, there is a good chance that the wireless card might not work.  Also, the NDISwrapper instructions will work for Gutsy and older versions.  The Hardy versions need to have the b43 driver removed and ssb to be loaded after NDISwrapper is installed (if ssb is needed).

---

### Post by pippo_jedi on 2008-05-24
ARGH! nothing works! can anybody help me? 
my pc is a asus laptop a7d amd turion 64

i've tried both the automated method using fwcutter and ndiswrapper... neither of them seem to work... positive thing using ndiswrapper gives a scan in network manager, but

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```

then

```
lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:15:f2:35:9d:5b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=27.240.89.161 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:f2:57:20:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

 ```
lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ndiswrapper           243872  0 
b43                   126760  0 
rfkill                 10128  3 rfkill_input,b43
mac80211              192532  1 b43
input_polldev           6928  1 b43
led_class               7176  2 b43,asus_laptop
ssb                    37252  1 b43
usbcore               169904  6 ndiswrapper,hci_usb,usbhid,ehci_hcd,ohci_hcd
```



i've tried to 

```
ifconfig wlan0 up
iwconfig wlan0 essid "myessid" mode managed channel 11 key off
iwconfig wlan0 ap 00:14:7C:52:7F:C4
dhclient -q wlan0
```

without results...

any help?

---

### Post by rizitis on 2008-05-24
> **Ayuthia said:**
> The information that you posted looks like you are trying to install both the NDISwrapper and native drivers at the same time.  It is recommended that you only do one.  If you do both, there is a good chance that the wireless card might not work.  Also, the NDISwrapper instructions will work for Gutsy and older versions.  The Hardy versions need to have the b43 driver removed and ssb to be loaded after NDISwrapper is installed (if ssb is needed).

we did it at Hardy and it works.
if you want look at greek ubuntu forum
[http://ubuntu.opengr.net/viewtopic.php?f=10&t=136&start=10](http://ubuntu.opengr.net/viewtopic.php?f=10&t=136&start=10)

---

### Post by Ayuthia on 2008-05-24
> **pippo_jedi said:**
> 
 ```
lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ndiswrapper           243872  0 
b43                   126760  0 
rfkill                 10128  3 rfkill_input,b43
mac80211              192532  1 b43
input_polldev           6928  1 b43
led_class               7176  2 b43,asus_laptop
ssb                    37252  1 b43
usbcore               169904  6 ndiswrapper,hci_usb,usbhid,ehci_hcd,ohci_hcd
```


You might be better to try NDISwrapper first.  Can you try the following:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwlist scan
```
Let me know if it sees any wireless sites.

---

### Post by Ayuthia on 2008-05-24
> **rizitis said:**
> we did it at Hardy and it works.
if you want look at greek ubuntu forum
[http://ubuntu.opengr.net/viewtopic.php?f=10&t=136&start=10](http://ubuntu.opengr.net/viewtopic.php?f=10&t=136&start=10)
I don't doubt you, but most of the cases, the b43 driver will cause a conflict with ndiswrapper.  Can you do me a favor and post the following:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```

---

### Post by pippo_jedi on 2008-05-24
No, it doesn't work. I also installed the ndiswrapper gui and reinstalled it
rebooted a couple of times, but no... it doesn't work

now
```
lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  6 ndiswrapper,hci_usb,usbhid,ehci_hcd,ohci_hcd

```

iwlist scan doesn't find anything

---

### Post by chades on 2008-05-24
sorry
i'm a little newbie,so my quetions might be a pin in the ***, but still i can't get my wlan going.
i did everything as described above,but when i get to the very last step 
   [COLOR="Blue"]sudo ifconfig wlan0 up[/COLOR]
i get the following error message
   [COLOR="Blue"]wlan0: error while getting interface flags: no such device[/COLOR]
what am i doing wrong?
 i don't know if it helps, but ifconfig shows only 2 devices
[COLOR="Blue"]eth0[/COLOR] and [COLOR="Blue"]lo[/COLOR]
 unfortunately i cannot copy-paste all the crap, 'cause my laptop does not connect to the internet 
so i'm writing it all by hand

---

### Post by dpick on 2008-05-24
Can someone give me a hand. I've got a brand new install of hardy with a linksys wmp54gs wireless card. lspci shows 
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I installed b43-fwcutter and now I can see all the wireless networks around me, but when I try to connect, network manager times out.

I tried installing wicd, but still had the same problem. Thanks

---

### Post by Ayuthia on 2008-05-24
> **dpick said:**
> Can someone give me a hand. I've got a brand new install of hardy with a linksys wmp54gs wireless card. lspci shows 
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I installed b43-fwcutter and now I can see all the wireless networks around me, but when I try to connect, network manager times out.

I tried installed wicd, but still had the same problem. Thanks
If the router is yours, can you change the channel and see if it works?  Also is it encrypted?  If it is, you can try turning off the encryption to see if it will connect then you can try using it with encryption.

---

### Post by Ayuthia on 2008-05-24
> **chades said:**
> sorry
i'm a little newbie,so my quetions might be a pin in the ***, but still i can't get my wlan going.
i did everything as described above,but when i get to the very last step 
   [COLOR="Blue"]sudo ifconfig wlan0 up[/COLOR]
i get the following error message
   [COLOR="Blue"]wlan0: error while getting interface flags: no such device[/COLOR]
what am i doing wrong?
 i don't know if it helps, but ifconfig shows only 2 devices
[COLOR="Blue"]eth0[/COLOR] and [COLOR="Blue"]lo[/COLOR]
 unfortunately i cannot copy-paste all the crap, 'cause my laptop does not connect to the internet 
so i'm writing it all by hand
When you type lshw -C network, see if there is a logical name for your wireless.  It should look something like this:
```
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:aa:11:bb:22:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.15.102 multicast=yes wireless=IEEE 802.11g

```
Please let us know if lshw -C network shows UNCLAIMED or DISABLED.  Also, please let us know if the driver shows b43-pci-bridge and module=ssb.

---

### Post by dpick on 2008-05-24
It was encrypted, but unecrypting the network made no difference and same with changing the channel, I went from 11 to 1 and still no connection.

---

### Post by Ayuthia on 2008-05-24
> **pippo_jedi said:**
> No, it doesn't work. I also installed the ndiswrapper gui and reinstalled it
rebooted a couple of times, but no... it doesn't work

now
```
lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  6 ndiswrapper,hci_usb,usbhid,ehci_hcd,ohci_hcd

```

iwlist scan doesn't find anythingCan you post the results of ndiswrapper -v from the Terminal.  Or can you just tell us if the ndiswrapper gui says hardware present?

We could also try the b43 method.  It looks like your card should work with it.  You might try post #3 from this [thread]("http://ubuntuforums.org/showthread.php?t=761325")

---

### Post by rizitis on 2008-05-25
> **Ayuthia said:**
> I don't doubt you, but most of the cases, the b43 driver will cause a conflict with ndiswrapper.  Can you do me a favor and post the following:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```

Oh No !I am sorry , my English are not so good , I dint fell doubt, I just write that it works...
I hope you understand what I mean. 

I sent an email to the person who hand the laptop.I just help him with his problem, at the Greek ubuntu forum, I had the same problem with (bmc 4310) and I solved it by the same way look down the results. (of course I install different drivers but all the others commands was exactly the same.)  
Any way, he will command and after we will post the results here for bcn 4329.

thank you.


ps. my command results are

```
rizitis@dell-rizitis:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ssb                    32260  1 b44
ndiswrapper           192920  0 
usbcore               146028  7 ndiswrapper,uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
rizitis@dell-rizitis:~$ 

```

dell vostro 1700 
bcm 4310.

---

### Post by HuntMike79 on 2008-05-25
Just tried this with my belkin card abd wirkked like a charm in 8.04. :)

---

### Post by chades on 2008-05-25
> **Ayuthia said:**
> When you type lshw -C network, see if there is a logical name for your wireless.  It should look something like this:
```
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:aa:11:bb:22:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.15.102 multicast=yes wireless=IEEE 802.11g

```
Please let us know if lshw -C network shows UNCLAIMED or DISABLED.  Also, please let us know if the driver shows b43-pci-bridge and module=ssb.

yes, it shows exactly as you say
driver b43-pci-bridge, module ssb
but now,as i read i see , that you told APIPOTE that my card(4311 v02) would not work with this driver,i should try using NDISwrapper
i'll try it and let you know what the result was
thanks for helping out

update:
could not do it, requires working internet connection,i have none. if you could please help me do it without connection or help me get my wired working, i'd appreciate it

---

### Post by Ayuthia on 2008-05-25
> **chades said:**
> yes, it shows exactly as you say
driver b43-pci-bridge, module ssb
but now,as i read i see , that you told APIPOTE that my card(4311 v02) would not work with this driver,i should try using NDISwrapper
i'll try it and let you know what the result was
thanks for helping out

update:
could not do it, requires working internet connection,i have none. if you could please help me do it without connection or help me get my wired working, i'd appreciate it

Do you have Windows XP anywhere?  If so, look for bcmwl5.inf and bcmwl5.sys.  If you can find those, you can install NDISwrapper from the Hardy install CD.  Try the following:
```
sudo apt-get install ndiswrapper-utils-1.9
```If it cannot find it try:
```
sudo apt-cdrom add
```Insert the Hardy CD when it asks and then press Enter.  After that, try installing ndiswrapper again:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

If you have the XP driver (bcmwl5.inf and bcmwl5.sys), copy those files to your Desktop.  From there:
```
cd ~/Desktop
```
then you can follow the instructions from this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") at step 3.

---

### Post by Ayuthia on 2008-05-25
> **dpick said:**
> It was encrypted, but unecrypting the network made no difference and same with changing the channel, I went from 11 to 1 and still no connection. How about trying to turn off wicd and see if you can connect manually without encryption first:
```
sudo /etc/init.d/wicd stop
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```

---

### Post by venture68 on 2008-05-25
Hello.

I am new to Ubuntu and so far it's nice. However, I'm having an issue with my Broadcom network card for wireless networking on a Dell Inspiron 6000 laptop.

I installed a fresh copy of 8.04 and the first thing I did was open a terminal and execute the first two "Option 1" commands in this thread. I knew I had a card that fell into that category.

If I set the wireless connection to roaming in Network Mgr (I am I supposed to have it set to roaming?) then I get uncolored wireless bars in the upper bar with the tooltip to the effect of "[network name] 0%" and it's definitely not connected.

For now I have a wired connection but I need the wireless networking to work. I believe my router is Pre-N and I have WPA2 security enabled. This is known to be working with the other Windows PCs wirelessly so it's not the router (afaik)

So, being a linux noob :) if anyone could walk me through how I can provide info to the forum to help I would greatly appreciate it. I've been trying to resolve this for 2 days and it's giving my OCD fits.  :confused:

Thank you very much in advance!

---

### Post by Ayuthia on 2008-05-25
> **venture68 said:**
> Hello.

I am new to Ubuntu and so far it's nice. However, I'm having an issue with my Broadcom network card for wireless networking on a Dell Inspiron 6000 laptop.

I installed a fresh copy of 8.04 and the first thing I did was open a terminal and execute the first two "Option 1" commands in this thread. I knew I had a card that fell into that category.

If I set the wireless connection to roaming in Network Mgr (I am I supposed to have it set to roaming?) then I get uncolored wireless bars in the upper bar with the tooltip to the effect of "[network name] 0%" and it's definitely not connected.

For now I have a wired connection but I need the wireless networking to work. I believe my router is Pre-N and I have WPA2 security enabled. This is known to be working with the other Windows PCs wirelessly so it's not the router (afaik)

So, being a linux noob :) if anyone could walk me through how I can provide info to the forum to help I would greatly appreciate it. I've been trying to resolve this for 2 days and it's giving my OCD fits.  :confused:

Thank you very much in advance!

Can you post the results of:
```
lspci -nn|grep 14e4
```
I just want to confirm that your card will work with the native driver.

---

### Post by venture68 on 2008-05-25
Here you go:

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Thank you very much for the fast reply! I'd love to get this working!

And please, feel free to direct me like a 5-year-old. I'm very new to this but feeling my way around.

Thanks!

---

### Post by Ayuthia on 2008-05-25
> **venture68 said:**
> Here you go:

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Thank you very much for the fast reply! I'd love to get this working!

And please, feel free to direct me like a 5-year-old. I'm very new to this but feeling my way around.

Thanks!You might try to turn off encryption to see if you can connect.  This will help us pinpoint where the issue is.  If that doesn't help, we should try to see if we can connect from the terminal.  We can check and see if you can scan any networks:
```
sudo iwlist scan
```

With encryption off, we can also try to connect to your router:
```
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
Replace <name> with the essid of your router.

---

### Post by venture68 on 2008-05-26
I turned off security on the router and tried the commands. I also turned on broadcasting to see if the card picked it up. Nada. Seems like the wireless card won't auto-find wireless networks transmitting in the area.

**sudo iwlist scan** results:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Second set of commands results:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:4f:5b:20
Sending on   LPF/wlan0/00:14:a5:4f:5b:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by venture68 on 2008-05-26
I'm not sure if this provides any useful additional information but I did a lshw -C network and these are the results:

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ee:58:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.153 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:4f:5b:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Ayuthia on 2008-05-26
> **venture68 said:**
> I'm not sure if this provides any useful additional information but I did a lshw -C network and these are the results:

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ee:58:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.153 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:4f:5b:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I am getting mixed answers about the 4318 card.  You might try the NDISwrapper route.  Here is the link.  If you have issues with this, you can post here also.  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by chades on 2008-05-26
> **Ayuthia said:**
> Do you have Windows XP anywhere?  If so, look for bcmwl5.inf and bcmwl5.sys.  If you can find those, you can install NDISwrapper from the Hardy install CD.  Try the following:
```
sudo apt-get install ndiswrapper-utils-1.9
```If it cannot find it try:
```
sudo apt-cdrom add
```Insert the Hardy CD when it asks and then press Enter.  After that, try installing ndiswrapper again:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

If you have the XP driver (bcmwl5.inf and bcmwl5.sys), copy those files to your Desktop.  From there:
```
cd ~/Desktop
```
then you can follow the instructions from this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") at step 3.

Hi again.
Thanks very much on the help. It works and actually i'm typing this message from my laptop. Thanks a load, Ayuthia, you are the best. Your truest fan forever

---

### Post by Peter Freeman on 2008-05-27
Hi Ayuthia,

I have yet to get my wireless working.  It is very close to working.  I have tried Ubuntu 7.04; 7.10; and now 8.04, but no success.

It shows me the available networks, I type in the WEP key to the network with the strongest signal, it spends a long time trying to connect and then comes back asking me again for the WEP key.  I'm currently using fwcutter (I believe) that comes with the Hardy install and using the System/Administration/Network application.  Here is information that you requested from other people with similar problems:


sudo lspci -nn

01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)



sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:06:25:56:A2:23
                    ESSID:"Smeeton"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/100  Signal level=-66 dBm  Noise level=-69 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000dacf709929
          Cell 02 - Address: 00:0F:66:77:56:75
                    ESSID:"Freeman"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=83/100  Signal level=-50 dBm  Noise level=-69 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000168cb3a6b0f
          Cell 03 - Address: 00:12:17:6C:66:7C
                    ESSID:"Musgrave"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-69 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000010361356bc5

sudo lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper

b43                   126760  0 
rfkill                 10128  3 rfkill_input,b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43
ssb                    37252  1 b43

sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:0b:fc:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Thanks for any help you can give me,

Peter

---

### Post by Ayuthia on 2008-05-28
> **Peter Freeman said:**
> Hi Ayuthia,

I have yet to get my wireless working.  It is very close to working.  I have tried Ubuntu 7.04; 7.10; and now 8.04, but no success.

It shows me the available networks, I type in the WEP key to the network with the strongest signal, it spends a long time trying to connect and then comes back asking me again for the WEP key.  I'm currently using fwcutter (I believe) that comes with the Hardy install and using the System/Administration/Network application.  Here is information that you requested from other people with similar problems:


sudo lspci -nn

01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)



sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:06:25:56:A2:23
                    ESSID:"Smeeton"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/100  Signal level=-66 dBm  Noise level=-69 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000dacf709929
          Cell 02 - Address: 00:0F:66:77:56:75
                    ESSID:"Freeman"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=83/100  Signal level=-50 dBm  Noise level=-69 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000168cb3a6b0f
          Cell 03 - Address: 00:12:17:6C:66:7C
                    ESSID:"Musgrave"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-69 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000010361356bc5

sudo lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper

b43                   126760  0 
rfkill                 10128  3 rfkill_input,b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43
ssb                    37252  1 b43

sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:0b:fc:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Thanks for any help you can give me,

Peter

I would try to connect without WEP first to see if you can connect.  If it is still not connecting, try using another channel on your router that is not 1, 6, or 11.

If it does connect, we will need to see why it will not connect using WEP.

---

### Post by jamesmorad on 2008-05-28
Ok i tried this guide and now for the first time i can see my wireless network show up in my network manager. However, it fails to connect to it. I'm thinking its most likely because i'm using WPA encryption, but does anyone know how to fix that?

EDIT:
I decided to try to connect to my wireless network without having WPA enabled, and it turns out that i still cannot connect. Does anyone have any idea of what is going on?

---

### Post by Ayuthia on 2008-05-28
> **jamesmorad said:**
> Ok i tried this guide and now for the first time i can see my wireless network show up in my network manager. However, it fails to connect to it. I'm thinking its most likely because i'm using WPA encryption, but does anyone know how to fix that?

EDIT:
I decided to try to connect to my wireless network without having WPA enabled, and it turns out that i still cannot connect. Does anyone have any idea of what is going on?
It could be interference to your router so you could try another channel.  Can you also post the results to:
```
lspci -nn|grep 14e4
```

---

### Post by TheNatealator on 2008-05-28
Hi,

I tried 8.04 from the liveCD first, because I was worried about the wireless drivers. When I started it up and tried to connect to my network, I got a window that said I had to install proprietary firmware that didn't come with the CD. I said OK, and everything was working.  So, now that I've installed 8.04, I've run into the same firmware problem, but I have not seen the very helpful firmware window.  If someone can help me get that back, that would be the quickest way to solve my problem.  

Failing that, I'm not afraid of the terminal. If there's any diagnostics I need to do, let me know.
```
$lspci -nn | grep Network
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

```

-Nate

---

### Post by jamesmorad on 2008-05-28
> **Ayuthia said:**
> It could be interference to your router so you could try another channel.  Can you also post the results to:
```
lspci -nn|grep 14e4
```

Changed the channel, but that appeared to do nothing.

Here is the output from the list:

```
02:08.0 Network Controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

---

### Post by jamesmorad on 2008-05-28
Does anyone have any input or suggestions on how to get my wireless to associate with the access point?

Also, I should add, that when trying to associate with nm-applet 0.6.6, the icon just keeps spinning and the dots never turn blue. Then after about 45 seconds, the two computer screen icon comes back and im still not connected

EDIT:

alex_kent is my new hero here. if anyone has a similar problem as me, follow this guide:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

btw, im using linksys wmp54gs card with broadcom 4306 chipset, so if you're using the same card and trying to get wireless working in hardy heron, you could probably do well to follow the guide i posted in this reply.

---

### Post by KarthVader on 2008-05-28
> **xomp said:**
> Here is my lscpi -nn



Here is my iwlist scan


I have disabled the other wifi adapter (the prism2) since linux is incapable of utilitzing it, hence the reason I purchased this Belking Wireless G.. I am 'trying' to use the propietary driver and not ndiswrapper at all for this.
I am having the same problem that xomp is having. I'm on an eMachine M6810.
lspci -nn

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge [1106:3188] (rev 01)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:0a.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
00:13.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]

iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Can anyone help? I'd appreciate it.

---

### Post by TheAmigo on 2008-05-28
There are lots of great tips here, but my problem is slightly different.

I have a ```
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
```
 that worked when I installed 08.04 Beta a couple days ago (old CD sitting around).  After I ran an update and selected a ton of software to install, I seem to have messed up the wireless.

After booting, the b43 module is not loaded (NDISwrapper isn't even installed) but the ssb module is loaded.  lshw shows:
```
           *-network
                description: Network controller
                product: BCM4312 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb

```

When I run modprobe b43, it loads b43, rfkill, mac80211, cfg80211, led_class and input_polldev.

But the problem is that ifconfig -a still doesn't show wlan0 (only eth0 and lo).  Nor does dmesg or /var/log/messages have anything logged regarding loading the b43 module.

I'm at a loss for what to check next.  Any pointers appreciated!

---

### Post by Ayuthia on 2008-05-29
> **TheAmigo said:**
> There are lots of great tips here, but my problem is slightly different.

I have a ```
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
```
 that worked when I installed 08.04 Beta a couple days ago (old CD sitting around).  After I ran an update and selected a ton of software to install, I seem to have messed up the wireless.

After booting, the b43 module is not loaded (NDISwrapper isn't even installed) but the ssb module is loaded.  lshw shows:
```
           *-network
                description: Network controller
                product: BCM4312 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb

```

When I run modprobe b43, it loads b43, rfkill, mac80211, cfg80211, led_class and input_polldev.

But the problem is that ifconfig -a still doesn't show wlan0 (only eth0 and lo).  Nor does dmesg or /var/log/messages have anything logged regarding loading the b43 module.

I'm at a loss for what to check next.  Any pointers appreciated!

If I recall correctly, your card worked just fine in one of the pre-releases, but right before the final release, the patch applied to make your card work had to be removed because it broke most of the other cards.  There has not been any working patches in Ubuntu as of yet.  The best bet is to install NDISwrapper.  

You can try the following links:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) (This one is for your card and is a decent guide)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) (This is also a good link.  It provides a lot of information and some good drivers to try.)

---

### Post by TheNatealator on 2008-05-29
I'm in the same situation (chipset 14e4:4311) and I've followed the ndiswrapper steps you link to (both pages show the same thing) but everytime I try 'sudo modprobe ndiswrapper' the message I get is 'FATAL: Module ndiswrapper not found.' Ideas?

---

### Post by Ayuthia on 2008-05-29
> **KarthVader said:**
> I am having the same problem that xomp is having. I'm on an eMachine M6810.
lspci -nn

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge [1106:3188] (rev 01)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:0a.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
00:13.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]

iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Can anyone help? I'd appreciate it.

You can try and see if you can connect manually without Network Manager running:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```This will only stop Network Manager until you reboot.  You can then try to see if you can see anything by doing 'sudo iwlist scan'.  You might have to try a couple of times before it sees something.  If something does show up, you can then try to connect:
```
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
You will need to have any encryption turned off before you can try this because I didn't provide the command for WEP or WPA.

---

### Post by 4partee on 2008-05-30
> **Ayuthia said:**
> If you do switch over, just be aware that ssb needs to be loaded after ndiswrapper.  If you don't have a Broadcom ethernet card (the wired one), you should be able to just blacklist b43 and ssb.  Check with lsmod|grep ssb before blacklisting to make sure that nothing else is using it.

I blacklisted b43 and ssb. On reboot ssb was still loaded before ndiswrapper and no blue light.  After I rmmod ssb ndiswrapper followed by modprobe ndiswrapper I get the blue light and the wireless works fine.

I would like to learn how to do this on boot using 8.04 Ubuntu 64bit on a Compaq F572 notebook. Should I just put the above commands in /etc/rc.local or is there a better way to have ndiswrapper loaded before ssb on boot?

---

### Post by TheAmigo on 2008-05-30
> **Ayuthia said:**
> If I recall correctly, your card worked just fine in one of the pre-releases, but right before the final release, the patch applied to make your card work had to be removed because it broke most of the other cards.  There has not been any working patches in Ubuntu as of yet.  The best bet is to install NDISwrapper.

Interesting.  That would explain what I saw.

Thanks for the pointer, I'm posting this reply via WiFi now using NDISwrapper.

---

### Post by Ayuthia on 2008-05-31
> **TheNatealator said:**
> I'm in the same situation (chipset 14e4:4311) and I've followed the ndiswrapper steps you link to (both pages show the same thing) but everytime I try 'sudo modprobe ndiswrapper' the message I get is 'FATAL: Module ndiswrapper not found.' Ideas?
How did you install ndiswrapper?  The message that is coming up is because either ndiswrapper was not installed or else ndiswrapper had a problem while compiling.

---

### Post by Ayuthia on 2008-05-31
> **4partee said:**
> I blacklisted b43 and ssb. On reboot ssb was still loaded before ndiswrapper and no blue light.  After I rmmod ssb ndiswrapper followed by modprobe ndiswrapper I get the blue light and the wireless works fine.

I would like to learn how to do this on boot using 8.04 Ubuntu 64bit on a Compaq F572 notebook. Should I just put the above commands in /etc/rc.local or is there a better way to have ndiswrapper loaded before ssb on boot?You can do it that way, but it is harder to troubleshoot if something goes wrong.  From what you are telling me, b44 is not needed.  You can try this:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```This will add an additional line to the loading of ndiswrapper.  It will do the module removal for b43, b44, b43legacy, and ssb and then load ndiswrapper.  This is a modification from this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb").  I made the modification because it does not sound like you need to have b44 installed (it is a driver for Broadcom wired cards).

---

### Post by Ayuthia on 2008-06-04
I have added an attachment that will help configure your Broadcom card.  It should work for bcm43xx, b43, and NDISwrapper drivers.  It is nothing fancy.  It will set up your blacklisted files, modules to add at rebooting, and does the ssb fix if needed.  The tool also has a button to Display Info.  It will list out your blacklisted modules, your modules to load on reboot, and your lshw -C network.  Hopefully it will help somebody.

It is in the very early stages so there could be the chance that it might not work.  So please use at your own risk.  The files do get backed up just in case, but this is just the first release.

The attachment can be found in the first post.

---

### Post by TheNatealator on 2008-06-05
> **Ayuthia said:**
> How did you install ndiswrapper?  The message that is coming up is because either ndiswrapper was not installed or else ndiswrapper had a problem while compiling.

Well, between restarting, compiling the latest kernel, ndiswrapper, and b43, I have gotten wireless on Ubuntu working.  When I have the time, I'm going to figure out what I have. Until then, I'm using XP anyways, since I don't have time to move all my files and make sure I can open all of them.  Also, since I haven't found an open source backup util or file synchronizer I like, I think I'll write those, first.

-Nate

---

### Post by inwo on 2008-06-05
so, what am I doing wrong?


```
jr@mistmore:~/Documents/toolbox$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```


```
jr@mistmore:~/Documents/toolbox$ lspci | grep -i broadcom
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```

```
jr@mistmore:~/Documents/toolbox$ lsmod | grep b43
b43                   126760  0
ssb                    37252  1 b43
rfkill                 10128  1 b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43

```

```
jr@mistmore:~/Documents/toolbox$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:41:2b:d6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.10.100 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

---

### Post by Ayuthia on 2008-06-05
> **inwo said:**
> so, what am I doing wrong?


```
jr@mistmore:~/Documents/toolbox$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```


```
jr@mistmore:~/Documents/toolbox$ lspci | grep -i broadcom
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```

```
jr@mistmore:~/Documents/toolbox$ lsmod | grep b43
b43                   126760  0
ssb                    37252  1 b43
rfkill                 10128  1 b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43

```

```
jr@mistmore:~/Documents/toolbox$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:41:2b:d6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.10.100 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

The only thing that you are doing wrong is that you are trying to install the b43 driver for a card that is not yet supported.  Your card has the wireless N feature and the developers are currently working on a solution for this.  You will need to try and use NDISwrapper.

---

### Post by inwo on 2008-06-05
> **Ayuthia said:**
> The only thing that you are doing wrong is that you are trying to install the b43 driver for a card that is not yet supported.  Your card has the wireless N feature and the developers are currently working on a solution for this.  You will need to try and use NDISwrapper.

Thanks.   by any chance is there a page for dev hardware?

---

### Post by gatorbowls on 2008-06-05
My wireless speed is very slow it shows as 2mb/s  is there anyway to raise that?

---

### Post by Ayuthia on 2008-06-06
> **inwo said:**
> Thanks.   by any chance is there a page for dev hardware?

I am not for sure what you mean.  If you are looking for the page for the b43 driver development, it is [here]("http://linuxwireless.org/en/users/Drivers/b43").

---

### Post by Ayuthia on 2008-06-06
> **gatorbowls said:**
> My wireless speed is very slow it shows as 2mb/s  is there anyway to raise that?
You could try:
```
sudo iwconfig wlan0 rate 54M
```

---

### Post by crazyness003 on 2008-06-07
Hello, Just though i should join in the conversation. 

I do have a question.

I have the BCM94311 chipset and for some bizarre reason the b43 (or b43legacy) driver actually worked in my 32bit setup Of Hardy Heron (I actually have Ubuntu Studio 8.04). 

Unfortunately, im not satisfied with 32bit, so I installed the 64 bit OS and was expecting similar results...obvioulsy not.

So back to my question, is there even a slight chance thet the b43 or b43legacy will work for 64 bit?

According to you guys (and several other sources) my chipset should not be supported by b43 (according to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) only if you use a patch...which i dont remember doing)

Just wanted to get some feedback. I'll post some specs about my 32bit setup in a min.

Thanks in advance

ps: This should be a sticky

edit-1: Your troubleshooting post is what saved my 32bit setup. Just wanted to thank you
[http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692)

```
shype@troggie-2:~$ uname -a
Linux troggie-2 **2.6.24-19-rt** #1 SMP PREEMPT RT Wed Jun 4 18:50:11 UTC 2008 **i686** GNU/Linux

```

32bit network stuff
```
shype@troggie-2:~$ 
shype@troggie-2:~$ ls /lib/firmware/b43
a0g0bsinitvals4.fw  a0g1bsinitvals13.fw  b0g0bsinitvals13.fw  b0g0initvals4.fw    pcm4.fw     ucode4.fw
a0g0bsinitvals5.fw  a0g1bsinitvals5.fw   b0g0bsinitvals4.fw   b0g0initvals5.fw    pcm5.fw     ucode5.fw
a0g0initvals4.fw    a0g1initvals13.fw    b0g0bsinitvals5.fw   lp0bsinitvals13.fw  ucode11.fw
a0g0initvals5.fw    a0g1initvals5.fw     b0g0initvals13.fw    lp0initvals13.fw    ucode13.fw
shype@troggie-2:~$ ls /lib/firmware/b43legacy
a0g0bsinitvals2.fw  a0g0initvals5.fw    b0g0bsinitvals2.fw  b0g0initvals5.fw  ucode11.fw  ucode5.fw
a0g0bsinitvals5.fw  a0g1bsinitvals5.fw  b0g0bsinitvals5.fw  pcm4.fw           ucode2.fw
a0g0initvals2.fw    a0g1initvals5.fw    b0g0initvals2.fw    pcm5.fw           ucode4.fw
shype@troggie-2:~$ 

```
```
shype@troggie-2:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.109 multicast=yes wireless=IEEE 802.11g

```
```
shype@troggie-2:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43                   115360  0 
rfkill                  8848  3 rfkill_input,b43
mac80211              168212  1 b43
led_class               6148  1 b43
input_polldev           5896  1 b43
ssb                    32772  1 b43

```
```
shype@troggie-2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"The Swamp"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:8C:60:9F   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=71/100  Signal level=-66 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Ayuthia on 2008-06-07
> **crazyness003 said:**
> Hello, Just though i should join in the conversation. 

I do have a question.

I have the BCM94311 chipset and for some bizarre reason the b43 (or b43legacy) driver actually worked in my 32bit setup Of Hardy Heron (I actually have Ubuntu Studio 8.04). 

Unfortunately, im not satisfied with 32bit, so I installed the 64 bit OS and was expecting similar results...obvioulsy not.

So back to my question, is there even a slight chance thet the b43 or b43legacy will work for 64 bit?

According to you guys (and several other sources) my chipset should not be supported by b43 (according to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) only if you use a patch...which i dont remember doing)

Just wanted to get some feedback. I'll post some specs about my 32bit setup in a min.

Thanks in advance

ps: This should be a sticky

The 64-bit should work like the 32-bit.  But of course, sometimes they don't...

I am currently using the 64-bit of Ubuntu, but I have the rev 01 of the 4311.  I am hearing that the 2.6.24-18 release fixes the issue for the rev 02 cards, but I have not seen any confirmations of it.  I ran into some connection issues (had to remove the module and reload it to get it to stay working) then they released the 2.6-24-19 during the past 24 hours and it now works without any problems.  The other sad part is that I cannot find the release notes on the most recent release.  As far as I know, the 2.6.24-19 is in the proposed repositories and I am not for sure if/when it will be moved to the mainstream section.

Out of curiosity, do you know what kernel version you were using with Studio when it was working?

---

### Post by crazyness003 on 2008-06-07
> **Ayuthia said:**
> The 64-bit should work like the 32-bit.  But of course, sometimes they don't...
True. I just wish i can get it to work. Id much rather use 64bit. Its so much more...bit-esque...

> **Ayuthia said:**
> Out of curiosity, do you know what kernel version you were using with Studio when it was working?

Yes, its my current one
```
Linux troggie-2 2.6.24-19-rt #1 SMP PREEMPT RT Wed Jun 4 18:50:11 UTC 2008 i686 GNU/Linux
```
Of course its x86. That probably explains the whole deal. and here i though i was just too good. Meh.

So any idea on how i should tackle my 64bit version? I already installed the fwcutter, b43, b43legacy, and all that other stuffs. I even installed a little program called "Network Selector". I though it was the missing piece (evidenly not). What i cant get it the ifconfig to set up the wlan0 flag-thingy (you guessed it, im a newb). 
I really wanna stay away from the NDISwrapper since it uses win'doze drivers to get it to work...we all know how mighty they are. Plus i've read that they inhibit connection speed like crazy.

anyway, awesome posts and even awesome-r response times. I only had time to reboot and *wham!, you replied. Kudos

---

### Post by Ayuthia on 2008-06-08
> **crazyness003 said:**
> What i cant get it the ifconfig to set up the wlan0 flag-thingy.
If ifconfig is not turning on wlan0, you might want to check lshw -C network and see how it is configured.  Check to see if the logical name is set to wlan0 and also check and make sure that it is not DISABLED or UNCLAIMED.  If you want, you can post the message that ifconfig is giving you when you try to turn on wlan0 and also post your lshw -C network information.
> anyway, awesome posts and even awesome-r response times. I only had time to reboot and *wham!, you replied. KudosThanks!  As for the response times, that is more luck than anything...  I just happen to be on right now because all the kids are asleep.

---

### Post by crazyness003 on 2008-06-08
Hers my attempt
```
shype@troggie-2:~$ **sudo ifconfig wlan0 up**
[sudo] password for shype: 
wlan0: ERROR while getting interface flags: No such device
shype@troggie-2:~$ 

```
also i tried **sudo /etc/init.d/networking restart**
```
...
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```
Heres my **lshw -C network**
```
shype@troggie-2:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       **configuration: driver=b43-pci-bridge latency=0 module=ssb**

```
I modified my **/etc/network/interfaces** manually
```
....# The primary network interface
auto eth0
iface eth0 inet dhcp

[b]# The Wireless network interface (set up by Shype {thats me})
auto wlan0
iface wlan0 inet dhcp[/b]

```
My modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
loop
lp
rtc
fuse
[b]b43
ssb[/b]
```
 lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```

shype@troggie-2:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43                   127272  0 
rfkill                 10512  1 b43
mac80211              194324  1 b43
led_class               7304  1 b43
input_polldev           6928  1 b43
ssb                    37892  1 b43

```
My blacklist
```
...
[b]# replaced by b43 and ssb.
blacklist bcm43xx[/b]

...

[b]blacklist ndiswrapper
#blacklist b43legacy[/b]
```

> Check to see if the logical name is set to wlan0 and also check and make sure that it is not DISABLED or UNCLAIMED

How do you do that. Remember...semi-n00b here

Again. Thanx

---

### Post by Ayuthia on 2008-06-08
> **crazyness003 said:**
> 
Heres my **lshw -C network**
```
shype@troggie-2:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       **configuration: driver=b43-pci-bridge latency=0 module=ssb**

```

Usually, lshw -C network will show something like:
```
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:aa:11:bb:22:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.193.142.111 multicast=yes wireless=IEEE 802.11g
```
There is usually the second portion that shows the Wireless interface.  You will see that it will show wlan0 as the logical name.  As for the UNCLAIMED or DISABLED, it will show up in lshw -C network also.  It will usually show up right after the *-network portion like this:
```
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:aa:11:bb:22:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.193.142.111 multicast=yes wireless=IEEE 802.11g
```

Another place to check and see what your wireless name might be is to look at /etc/udev/rules.d/70-persistent-net.rules.  Just type:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
and the information should show something like:
```
# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:aa:11:bb:22:cc", ATTR{type}=="1", NAME="wlan0"
```
The information in NAME= will be the name that you will need to use for ifconfig.

---

### Post by crazyness003 on 2008-06-08
> **Ayuthia said:**
> Another place to check and see what your wireless name might be is to look at /etc/udev/rules.d/70-persistent-net.rules.  Just type:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
and the information should show something like:
```
# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:aa:11:bb:22:cc", ATTR{type}=="1", NAME="wlan0"
```
The information in NAME= will be the name that you will need to use for ifconfig.

You may be correct, i just opend that file up and here is what it holds
```

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:24:91:ca:16", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```
Im missing the entire device. Im gonna just copy the exact same file from my 32bit partition and see what happens.

---

### Post by crazyness003 on 2008-06-08
It didnt work. I restarted, and nothing happend (aside from X crashing...completely different story). I did realize the mac address was wrong, but its weird that *that* address works in my 32bit partition. I changed it to the correct one (i looked on the actual chip), but still no luck.
Also, i noticed this when i entered *sudo /etc/init.d/networking restart*
```
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 4620
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:24:91:ca:16
Sending on   LPF/eth0/00:1b:24:91:ca:16
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:24:91:ca:16
Sending on   LPF/eth0/00:1b:24:91:ca:16
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.103 from 192.168.2.1
DHCPREQUEST of 192.168.2.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.103 from 192.168.2.1
bound to 192.168.2.103 -- renewal in 15307325 seconds.
wlan0: ERROR while getting interface flags: No such device
**There is already a pid file /var/run/dhclient.wlan0.pid with pid 0**
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```
So i moded the "interfaces" file and the "70-persistent-net.rules" file to wlan1...but still it gives me ```
...Listening on LPF/eth0/00:1b:24:91:ca:16
Sending on   LPF/eth0/00:1b:24:91:ca:16
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.2.103 from 192.168.2.1
DHCPREQUEST of 192.168.2.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.103 from 192.168.2.1
bound to 192.168.2.103 -- renewal in 12389662 seconds.
wlan1: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan1: ERROR while getting interface flags: No such device
wlan1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan1.
```
Im wondering maybe 2.6.24-18-rt just dosnt have it in it. Is there a way to upgrade to the .24-19-rt release. Maybe thats whats missing.
Thanks for trying with me. Im sure you coulda done something better (like zzzzz). Any suggestions will be extremely considered (short of changing the card, i looked into that, and its not a good idea. HP has something against modding their systems...its a pain in the *.)
Thank you

---

### Post by Ayuthia on 2008-06-08
Another thing to try is to see if dmesg is saying anything:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
dmesg
```
You don't need the ssb when you load b43 because ssb will automatically be loaded since b43 needs it.  The last few lines in the results of dmesg will hopefully tell us something or maybe reloading b43 might just bring it back up too.

---

### Post by Unix_Slayer on 2008-06-08
This might be a stupid question, but is your cat5 still plugged into your wired card? Or are you running more than one wireless device?

---

### Post by Ayuthia on 2008-06-08
> **Unix_Slayer said:**
> new kernel update messes up wlans and video.
Is that 2.6.24-19?  Oddly enough for me, it made my wireless work better, but I am currently using the Nvidia driver from Nvidia instead of the repositories because I don't have an external monitor on my laptop so I was not able to access the console and had to fiddle with recovering my screen when my laptop is inactive and the screen goes black (the 6150 Go had problems with the 169 series in Nvidia).

---

### Post by crazyness003 on 2008-06-08
> **Ayuthia said:**
> 
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
dmesg

```

Still didint work, and dmesg gave me about 1500 lines of nothing (wlan0, bcm4311, etc weren't even mentioned)
So anyway, how can i get this risky new kernel?

> **Ayuthia said:**
> Is that 2.6.24-19?  Oddly enough for me, it made my wireless work better, but I am currently using the Nvidia driver from Nvidia instead of the repositories because I don't have an external monitor on my laptop so I was not able to access the console and had to fiddle with recovering my screen when my laptop is inactive and the screen goes black (the 6150 Go had problems with the 169 series in Nvidia).
I still have that problem with the screen. Theres a way to fix that? I have the 6159 Go with 169.
...back on track. Should i just wait it out, or dive straight in. I have nothign to lose but time, and all to gain knowlege.

---

### Post by Ayuthia on 2008-06-08
> **crazyness003 said:**
> Still didint work, and dmesg gave me about 1500 lines of nothing (wlan0, bcm4311, etc weren't even mentioned)
So anyway, how can i get this risky new kernel?


I still have that problem with the screen. Theres a way to fix that? I have the 6159 Go with 169.
...back on track. Should i just wait it out, or dive straight in. I have nothign to lose but time, and all to gain knowlege.

If you want to try the new kernel, you will need to add these two lines to /etc/apt/sources.list:
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
```You will need to use sudo when you edit the file since it is in /etc.

As for the Nvidia fix, if you are still using 64-bit go to this site:
[http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)
In step 2, they have a link that you will need to download.  You will have to uninstall nvidia-glx-new.  The tricky part is that you have to be able to go into a console and stop the X server.  The way I did mine is that I changed my /etc/X11/xorg.conf file so that it used the 'nv' driver instead of 'nvidia' and restarted.  If that works for you, then you can follow this guide:
[http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html](http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html)
Just don't use the driver in step 4, instead use the one I linked to you.

If that does not make any sense, please create a new thread in the Hardware and Laptop section or the General section and include your xorg.conf file.  Please PM me the link to the thread and I can try to help you further there (So that we don't go off-topic on this thread).  I will say that I might not be able to respond until the evening on Sunday though.

---

### Post by crazyness003 on 2008-06-08
Thanks a bunch, im gonna have to sleep on the above information. You'v been a great deal of help (and hope). I started to think i had to use the-beaten-path-32bit. Thanks again. I'll post if i decide to dig that deep. I think i should get a better understanding of X before i try messing with video drivers. As for the kernel, im gonna give it a shot asap.

Thanks

---

### Post by whorush on 2008-06-08
hi, my asus WL-138G V2 pci card isnt working in amd64 hardy.  i'm using an amd chip and an amd/ati 780g chipset.

i just installed ubuntu, and on install it finds the card and installs b43-fwcutter which goes and gets the latest firmware and installs it.   then i restart, and go to my network manager and i see all the available netoworks, their strength, if they're protected or not, but i can't connect to any of them!

thanks in advance!
bradley

this is the printout for when it installed b43-fwcutter...
```
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 112129 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a011-1_amd64.deb) ...
Setting up b43-fwcutter (1:011-1) ...
--12:37:49--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      246.24K/s             

12:37:52 (245.71 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--12:37:52--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072      299.04K/s             

12:37:57 (298.32 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw

```


this is my lspci -nn
```
03:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```


here is my dmseg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 19:28:38 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] Command line: root=UUID=098b7725-64f7-453e-9a64-5cbdceb9d9f9 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fee0000 (usable)
[    0.000000]  BIOS-e820: 000000006fee0000 - 000000006fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fee3000 - 000000006fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fef0000 - 000000006ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 458464) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F71C0 checksum 0
[    0.000000] ACPI: RSDP 000F71C0, 0014 (r0 RS780 )
[    0.000000] ACPI: RSDT 6FEE3000, 0038 (r1 RS780  GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 6FEE3040, 0074 (r1 RS780  GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 6FEE30C0, 6550 (r1 RS780  GBTUACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 6FEE0000, 0040
[    0.000000] ACPI: SSDT 6FEE9700, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 6FEE9940, 0038 (r1 RS780  GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 6FEE9980, 003C (r1 RS780  GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 6FEE9640, 0084 (r1 RS780  GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000006fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 458464) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000006fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   458464
[    0.000000] On node 0 totalpages: 458367
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2723 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6212 pages used for memmap
[    0.000000]   DMA32 zone: 448156 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 6ff00000:70100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 450879
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=098b7725-64f7-453e-9a64-5cbdceb9d9f9 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   21.163868] Marking TSC unstable due to TSCs unsynchronized
[   21.163870] time.c: Detected 2104.469 MHz processor.
[   21.164844] Console: colour VGA+ 80x25
[   21.164847] console [tty0] enabled
[   21.164863] Checking aperture...
[   21.164865] CPU 0: aperture @ 287e000000 size 32 MB
[   21.164866] Aperture too small (32 MB)
[   21.174370] No AGP bridge found
[   21.188600] Memory: 1795724k/1833856k available (2488k kernel code, 37744k reserved, 1319k data, 320k init)
[   21.188633] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   21.265729] Calibrating delay using timer specific routine.. 4212.29 BogoMIPS (lpj=8424580)
[   21.265759] Security Framework initialized
[   21.265765] SELinux:  Disabled at boot.
[   21.265777] AppArmor: AppArmor initialized
[   21.265780] Failure registering capabilities with primary security module.
[   21.265936] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   21.266982] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.267471] Mount-cache hash table entries: 256
[   21.267589] Initializing cgroup subsys ns
[   21.267592] Initializing cgroup subsys cpuacct
[   21.267604] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.267606] CPU: L2 Cache: 512K (64 bytes/line)
[   21.267608] CPU 0/0 -> Node 0
[   21.267610] CPU: Physical Processor ID: 0
[   21.267611] CPU: Processor Core ID: 0
[   21.267634] SMP alternatives: switching to UP code
[   21.268191] Early unpacking initramfs... done
[   21.558424] ACPI: Core revision 20070126
[   21.558476] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.613299] Using local APIC timer interrupts.
[   21.660767] APIC timer calibration result 12526594
[   21.660769] Detected 12.526 MHz APIC timer.
[   21.660853] SMP alternatives: switching to SMP code
[   21.661257] Booting processor 1/2 APIC 0x1
[   21.671517] Initializing CPU#1
[   21.748857] Calibrating delay using timer specific routine.. 4208.97 BogoMIPS (lpj=8417954)
[   21.748863] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.748865] CPU: L2 Cache: 512K (64 bytes/line)
[   21.748867] CPU 1/1 -> Node 0
[   21.748869] CPU: Physical Processor ID: 0
[   21.748870] CPU: Processor Core ID: 1
[   21.748963] AMD Athlon(tm) Dual Core Processor 4050e stepping 02
[   21.748854] Brought up 2 CPUs
[   21.748976] CPU0 attaching sched-domain:
[   21.748979]  domain 0: span 03
[   21.748980]   groups: 01 02
[   21.748983]   domain 1: span 03
[   21.748984]    groups: 03
[   21.748986] CPU1 attaching sched-domain:
[   21.748988]  domain 0: span 03
[   21.748989]   groups: 02 01
[   21.748991]   domain 1: span 03
[   21.748992]    groups: 03
[   21.749201] net_namespace: 120 bytes
[   21.749574] Time: 15:06:23  Date: 06/08/08
[   21.749603] NET: Registered protocol family 16
[   21.749791] ACPI: bus type pci registered
[   21.749856] PCI: Using configuration type 1
[   21.751171] ACPI: EC: Look up EC in DSDT
[   21.756222] ACPI: Interpreter enabled
[   21.756228] ACPI: (supports S0 S1 S4 S5)
[   21.756248] ACPI: Using IOAPIC for interrupt routing
[   21.761294] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.761492] pci 0000:00:11.0: set SATA to AHCI mode
[   21.762636] PCI: Transparent bridge - 0000:00:14.4
[   21.762661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.762938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   21.763058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[   21.763143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   21.779225] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.779330] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.779433] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.779536] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.779639] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.779742] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.779844] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.779948] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   21.780067] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.780095] pnp: PnP ACPI init
[   21.780101] ACPI: bus type pnp registered
[   21.783106] pnp: PnP ACPI: found 15 devices
[   21.783108] ACPI: ACPI bus type pnp unregistered
[   21.783327] PCI: Using ACPI for IRQ routing
[   21.783330] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.792670] NET: Registered protocol family 8
[   21.792672] NET: Registered protocol family 20
[   21.792755] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   21.792759] hpet0: 4 32-bit timers, 14318180 Hz
[   21.793810] AppArmor: AppArmor Filesystem Enabled
[   21.796614] Time: hpet clocksource has been installed.
[   21.796626] Switched to high resolution mode on CPU 0
[   21.796930] Switched to high resolution mode on CPU 1
[   21.804608] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   21.804612] system 00:01: ioport range 0x220-0x225 has been reserved
[   21.804614] system 00:01: ioport range 0x290-0x294 has been reserved
[   21.804620] system 00:02: ioport range 0x4100-0x411f has been reserved
[   21.804623] system 00:02: ioport range 0x228-0x22f has been reserved
[   21.804626] system 00:02: ioport range 0x238-0x23f has been reserved
[   21.804628] system 00:02: ioport range 0x40b-0x40b has been reserved
[   21.804631] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   21.804634] system 00:02: ioport range 0xc00-0xc01 has been reserved
[   21.804636] system 00:02: ioport range 0xc14-0xc14 has been reserved
[   21.804639] system 00:02: ioport range 0xc50-0xc52 has been reserved
[   21.804641] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[   21.804644] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[   21.804647] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[   21.804649] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[   21.804652] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[   21.804655] system 00:02: ioport range 0x4000-0x40fe has been reserved
[   21.804657] system 00:02: ioport range 0x4210-0x4217 has been reserved
[   21.804660] system 00:02: ioport range 0xb00-0xb0f has been reserved
[   21.804663] system 00:02: ioport range 0xb10-0xb1f has been reserved
[   21.804665] system 00:02: ioport range 0xb20-0xb3f has been reserved
[   21.804677] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.804683] system 00:0e: iomem range 0xcea00-0xcffff has been reserved
[   21.804686] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   21.804689] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   21.804692] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   21.804695] system 00:0e: iomem range 0x6fee0000-0x6fefffff could not be reserved
[   21.804698] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
[   21.804701] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   21.804704] system 00:0e: iomem range 0x100000-0x6fedffff could not be reserved
[   21.804707] system 00:0e: iomem range 0x6fff0000-0x7ffeffff has been reserved
[   21.804710] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
[   21.804713] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   21.804716] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
[   21.805094] PCI: Bridge: 0000:00:01.0
[   21.805096]   IO window: e000-efff
[   21.805099]   MEM window: fde00000-fdffffff
[   21.805102]   PREFETCH window: d0000000-dfffffff
[   21.805106] PCI: Bridge: 0000:00:0a.0
[   21.805108]   IO window: d000-dfff
[   21.805110]   MEM window: fdd00000-fddfffff
[   21.805112]   PREFETCH window: fda00000-fdafffff
[   21.805115] PCI: Bridge: 0000:00:14.4
[   21.805118]   IO window: c000-cfff
[   21.805122]   MEM window: fdc00000-fdcfffff
[   21.805126]   PREFETCH window: fdb00000-fdbfffff
[   21.805155] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[   21.805159] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.805174] NET: Registered protocol family 2
[   21.840632] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   21.841378] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   21.843315] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   21.843821] TCP: Hash tables configured (established 262144 bind 65536)
[   21.843824] TCP reno registered
[   21.852677] checking if image is initramfs... it is
[   22.424181] Freeing initrd memory: 7512k freed
[   22.428707] audit: initializing netlink socket (disabled)
[   22.428719] audit(1212937583.220:1): initialized
[   22.430611] VFS: Disk quotas dquot_6.5.1
[   22.430679] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   22.430814] io scheduler noop registered
[   22.430816] io scheduler anticipatory registered
[   22.430817] io scheduler deadline registered
[   22.430913] io scheduler cfq registered (default)
[   22.567820] Boot video device is 0000:01:05.0
[   22.567982] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   22.568005] assign_interrupt_mode Found MSI capability
[   22.568029] Allocate Port Service[0000:00:0a.0:pcie00]
[   22.595317] Real Time Clock Driver v1.12ac
[   22.595496] hpet_resources: 0xfed00000 is busy
[   22.595524] Linux agpgart interface v0.102
[   22.595527] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.595722] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.596557] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.597244] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.597303] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.597390] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.597957] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.597966] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.612357] mice: PS/2 mouse device common for all mice
[   22.612401] cpuidle: using governor ladder
[   22.612403] cpuidle: using governor menu
[   22.612534] NET: Registered protocol family 1
[   22.612632] registered taskstats version 1
[   22.612749]   Magic number: 12:255:133
[   22.612857]   hash matches device device:08
[   22.612862] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   22.612865] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.612866] EDD information not available.
[   22.612877] Freeing unused kernel memory: 320k freed
[   22.629211] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.803662] fuse init (API version 7.9)
[   23.820743] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.820754] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.942290] SCSI subsystem initialized
[   23.951805] libata version 3.00 loaded.
[   23.959864] ahci 0000:00:11.0: version 3.0
[   23.959903] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 22
[   23.960120] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   23.983495] usbcore: registered new interface driver usbfs
[   23.983516] usbcore: registered new interface driver hub
[   23.984183] usbcore: registered new device driver usb
[   23.993972] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.121723] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.121729] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.253730] Floppy drive(s): fd0 is 1.44M
[   24.273337] FDC 0 is a post-1991 82077
[   24.960897] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   24.960902] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
[   24.961272] scsi0 : ahci
[   24.961331] scsi1 : ahci
[   24.961374] scsi2 : ahci
[   24.961406] scsi3 : ahci
[   24.961483] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 510
[   24.961487] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 510
[   24.961490] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 510
[   24.961493] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 510
[   25.436270] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   25.618334] ata1.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[   25.618339] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[   25.618342] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   25.651524] ata1.00: configured for UDMA/133
[   25.959609] ata2: SATA link down (SStatus 0 SControl 300)
[   26.435019] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.591719] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB03, max UDMA/100, ATAPI AN
[   26.747552] ata3.00: configured for UDMA/100
[   27.058235] ata4: SATA link down (SStatus 0 SControl 300)
[   27.058339] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   27.059063] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB03 PQ: 0 ANSI: 5
[   27.059142] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.059313] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   27.059554] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   27.059579] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[   27.069838] Driver 'sd' needs updating - please use bus_type methods
[   27.072237] Driver 'sr' needs updating - please use bus_type methods
[   27.074771] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.074782] sd 0:0:0:0: [sda] Write Protect is off
[   27.074785] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.074799] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.074853] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.074861] sd 0:0:0:0: [sda] Write Protect is off
[   27.074863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.074876] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.074880]  sda: sda1 sda2
[   27.089303] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.093357] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.093376] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   27.098340] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   27.098345] Uniform CD-ROM driver Revision: 3.20
[   27.098387] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   27.122118] usb usb1: configuration #1 chosen from 1 choice
[   27.122140] hub 1-0:1.0: USB hub found
[   27.122149] hub 1-0:1.0: 3 ports detected
[   27.221923] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 16
[   27.222115] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   27.222174] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   27.222193] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[   27.281872] usb usb2: configuration #1 chosen from 1 choice
[   27.281893] hub 2-0:1.0: USB hub found
[   27.281902] hub 2-0:1.0: 3 ports detected
[   27.365714] Attempting manual resume
[   27.365718] swsusp: Resume From Partition 8:1
[   27.365720] PM: Checking swsusp image.
[   27.365910] PM: Resume from disk failed.
[   27.385719] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[   27.385895] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   27.385958] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   27.385981] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[   27.394076] kjournald starting.  Commit interval 5 seconds
[   27.394097] EXT3-fs: mounted filesystem with ordered data mode.
[   27.445668] usb usb3: configuration #1 chosen from 1 choice
[   27.445692] hub 3-0:1.0: USB hub found
[   27.445700] hub 3-0:1.0: 3 ports detected
[   27.549518] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 18
[   27.549706] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   27.549764] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   27.549781] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[   27.609451] usb usb4: configuration #1 chosen from 1 choice
[   27.609473] hub 4-0:1.0: USB hub found
[   27.609481] hub 4-0:1.0: 3 ports detected
[   27.713271] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 18
[   27.713455] ohci_hcd 0000:00:14.5: OHCI Host Controller
[   27.713513] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[   27.713530] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[   27.773243] usb usb5: configuration #1 chosen from 1 choice
[   27.773267] hub 5-0:1.0: USB hub found
[   27.773275] hub 5-0:1.0: 2 ports detected
[   27.877225] r8169 Gigabit Ethernet driver 2.2LK loaded
[   27.877252] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   27.877271] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   27.877508] eth0: RTL8168c/8111c at 0xffffc200008b8000, 00:1f:d0:55:5f:b3, XID 3c4000c0 IRQ 509
[   27.879397] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
[   27.879582] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   27.879648] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
[   27.879695] ehci_hcd 0000:00:12.2: debug port 1
[   27.879713] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[   27.889683] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.889776] usb usb6: configuration #1 chosen from 1 choice
[   27.889796] hub 6-0:1.0: USB hub found
[   27.889801] hub 6-0:1.0: 6 ports detected
[   27.993670] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 19
[   27.993844] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   27.993901] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
[   27.993941] ehci_hcd 0000:00:13.2: debug port 1
[   27.993959] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[   28.005539] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.005631] usb usb7: configuration #1 chosen from 1 choice
[   28.005651] hub 7-0:1.0: USB hub found
[   28.005655] hub 7-0:1.0: 6 ports detected
[   28.109350] ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
[   28.109368] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   28.109380] ATIIXP: not 100% native mode: will probe irqs later
[   28.109388]     ide0: BM-DMA at 0xfa00-0xfa07, BIOS settings: hda:pio, hdb:pio
[   28.109401]     ide1: BM-DMA at 0xfa08-0xfa0f, BIOS settings: hdc:pio, hdd:pio
[   28.109411] Probing IDE interface ide0...
[   28.676016] Probing IDE interface ide1...
[   29.243378] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 22
[   29.293506] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.293821] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 21 (level, low) -> IRQ 21
[   29.351902] ssb: Sonics Silicon Backplane found on PCI device 0000:03:07.0
[   30.562463] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[007033a300001fd0]
[   35.359847] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   35.735961] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.848931] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   35.848938] shpchp: shpc_init: cannot reserve MMIO region
[   35.848961] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.098914] input: Power Button (FF) as /devices/virtual/input/input3
[   36.158715] ACPI: Power Button (FF) [PWRF]
[   36.158773] input: Power Button (CM) as /devices/virtual/input/input4
[   36.198955] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   36.222646] ACPI: Power Button (CM) [PWRB]
[   36.222727] ACPI: WMI-Acer: Mapper loaded
[   36.399592] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   36.450397] parport_pc 00:0a: reported by Plug and Play ACPI
[   36.450456] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   36.724049] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   36.808899] [fglrx] Maximum main memory to use for locked dma buffers: 1645 MBytes.
[   36.808930] [fglrx] ASYNCIO init succeed!
[   36.809201] [fglrx] PAT is enabled successfully!
[   36.810453] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   36.841712] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   36.879663] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   36.916086] ACPI: PCI Interrupt 0000:01:05.1[B] -> GSI 19 (level, low) -> IRQ 19
[   36.916274] PCI: Setting latency timer of device 0000:01:05.1 to 64
[   36.958043] b43-phy0: Broadcom 4318 WLAN found
[   37.022691] phy0: Selected rate control algorithm 'simple'
[   38.757503] lp0: using parport0 (interrupt-driven).
[   38.840580] Adding 1461872k swap on /dev/sda1.  Priority:-1 extents:1 across:1461872k
[   39.384417] EXT3 FS on sda2, internal journal
[   40.519701] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.875120] No dock devices found.
[   41.269975] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4050e processors (2 cpu cores) (version 2.20.00)
[   41.269899] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xc
[   41.269903] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xd
[   41.269905] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xf
[   41.269907] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x16
[   42.201668] ppdev: user-space parallel port driver
[   42.331386] audit(1212937603.663:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5032 profile="/usr/sbin/cupsd" namespace="default"
[   43.609984] Clocksource tsc unstable (delta = -71436148 ns)
[   43.688083] input: b43-phy0 as /devices/virtual/input/input6
[   43.731036] Bluetooth: Core ver 2.11
[   43.731375] NET: Registered protocol family 31
[   43.731380] Bluetooth: HCI device and connection manager initialized
[   43.731385] Bluetooth: HCI socket layer initialized
[   43.746099] Bluetooth: L2CAP ver 2.9
[   43.746105] Bluetooth: L2CAP socket layer initialized
[   43.818814] Bluetooth: RFCOMM socket layer initialized
[   43.818832] Bluetooth: RFCOMM TTY layer initialized
[   43.818835] Bluetooth: RFCOMM ver 1.8
[   44.554177] Registered led device: b43-phy0:tx
[   44.554196] Registered led device: b43-phy0:rx
[   44.554213] Registered led device: b43-phy0:assoc
[   44.554227] Registered led device: b43-phy0:radio
[   44.591978] r8169: eth0: link up
[   44.591987] r8169: eth0: link up
[   45.093107] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   45.532550] [fglrx] GART Table is not in FRAME_BUFFER range 
[   45.532560] [fglrx] Reserve Block - 0 offset =  0Xfffc000 length = 0X4000
[   45.532563] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   45.648646] [fglrx] interrupt source 10000000 successfully enabled
[   45.648653] [fglrx] enable ID = 0x00000006
[   45.648661] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   45.746268] NET: Registered protocol family 17
[   48.098649] NET: Registered protocol family 10
[   48.098952] lo: Disabled Privacy Extensions
[   48.099716] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.551909] hda-intel: Invalid position buffer, using LPIB read method instead.
[   53.464354] eth0: no IPv6 routers present
```

---

### Post by Unix_Slayer on 2008-06-08
> **Ayuthia said:**
> Is that 2.6.24-19?  Oddly enough for me, it made my wireless work better, but I am currently using the Nvidia driver from Nvidia instead of the repositories because I don't have an external monitor on my laptop so I was not able to access the console and had to fiddle with recovering my screen when my laptop is inactive and the screen goes black (the 6150 Go had problems with the 169 series in Nvidia).


My video driver needed to be re-installed everytime there's a new kernel update. I see a lot of people complaining about the same thimg.

---

### Post by Unix_Slayer on 2008-06-08
> **whorush said:**
> hi, my asus WL-138G V2 pci card isnt working in amd64 hardy.  i'm using an amd chip and an amd/ati 780g chipset.

i just installed ubuntu, and on install it finds the card and installs b43-fwcutter which goes and gets the latest firmware and installs it.   then i restart, and go to my network manager and i see all the available netoworks, their strength, if they're protected or not, but i can't connect to any of them!




I had the same problem. Your wireless is showing up, and the driver is installed. You can see the wireless networks, but the button to connect is greyed out? Try unplugging your cat5 from your wired card. Reboot, and see if it works.

---

### Post by EXCiD3 on 2008-06-08
Config tool worked like a charm on a desktop linksys broadcom card :D

---

### Post by crazyness003 on 2008-06-08
> **Ayuthia said:**
> If you want to try the new kernel, you will need to add these two lines to /etc/apt/sources.list:
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
```You will need to use sudo when you edit the file since it is in /etc.


After adding these repos, I did get a bunch of new updates, and it even gave me an "Update Distribution" window. I guess it made some intense updates, but the kernel remained the same. I did look under Synaptics and noticed the linux-headers-2.6.24-19 (regular one, -generic, and -rt) were installed. But from what I could understand, i need the linux-image-2.6.24-19-rt, linux-restricted-modules 2.6.24-19-rt and linux-modules 2.6.24-19-rt (all x86_64 of course)

I see the -generic one and the -server one, but for some reason (this may be my own wrongdoing) I'm looking for the -rt, since its how my particular distribution shipped (Ubuntu Studio x64). Can anyone direct me as how to proceed from here.

---

### Post by crazyness003 on 2008-06-08
> **Unix_Slayer said:**
> This might be a stupid question, but is your cat5 still plugged into your wired card? Or are you running more than one wireless device?

Sorry man, musta overlooked this post. To answer your question, yes indeed my Ethernet was plugged in. I should probably try it unplugged, I guess thats what you might be suggesting.
And no, i dont have more than one wireless device. Just the problematic 4311.

Thanks for the inquiry.

---

### Post by Ayuthia on 2008-06-08
> **crazyness003 said:**
> After adding these repos, I did get a bunch of new updates, and it even gave me an "Update Distribution" window. I guess it made some intense updates, but the kernel remained the same. I did look under Synaptics and noticed the linux-headers-2.6.24-19 (regular one, -generic, and -rt) were installed. But from what I could understand, i need the linux-image-2.6.24-19-rt, linux-restricted-modules 2.6.24-19-rt and linux-modules 2.6.24-19-rt (all x86_64 of course)

I see the -generic one and the -server one, but for some reason (this may be my own wrongdoing) I'm looking for the -rt, since its how my particular distribution shipped (Ubuntu Studio x64). Can anyone direct me as how to proceed from here.
By any chance, do you have the 2.6.24-17 kernel?  You might try and see if it works on that one.  I think that was the first version that I heard was working for your card.

---

### Post by whorush on 2008-06-08
> **Unix_Slayer said:**
> I had the same problem. Your wireless is showing up, and the driver is installed. You can see the wireless networks, but the button to connect is greyed out? Try unplugging your cat5 from your wired card. Reboot, and see if it works.

almost, but not exactly.  the driver is installed, i can see the local networks, but nothing is greyed out.  i can really click each network and try to connect to it, and if the network is secure ubuntu asks me for a password, i just can't get on to them.  can't get on if its secure or not secure.  i tried restarting without my network cable and it still didnt work.  thanks for trying though.  any more ideas?

---

### Post by Ayuthia on 2008-06-08
> **whorush said:**
> almost, but not exactly.  the driver is installed, i can see the local networks, but nothing is greyed out.  i can really click each network and try to connect to it, and if the network is secure ubuntu asks me for a password, i just can't get on to them.  can't get on if its secure or not secure.  i tried restarting without my network cable and it still didnt work.  thanks for trying though.  any more ideas?

Some people have had problems with getting WEP running with Network Manager.  Some have had better success with wicd or wifiradar.  You might try turning off Network Manager and connecting manually:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name> key <password>
sudo dhclient wlan0
```
Just replace <name> with the name of the network you ar trying to connect and replace <password> with your password.

---

### Post by crazyness003 on 2008-06-08
> **Ayuthia said:**
> By any chance, do you have the 2.6.24-17 kernel?  You might try and see if it works on that one.  I think that was the first version that I heard was working for your card.
Actually, i skipped that one. I installed with -2.6.24-16-rt and autoupdated to 2.6.24-18-rt. If -17 was supported, I would assume the -18 would also support it.

I have to ask you, You said you use Ubuntu Studio, and you also have the -19 kernel installed right? Is it the 19-generic kernel or is it the default uStudio one 19-rt. Im just curious since i read an article about rt and it basically concluded that regular kernels and realtime kernels are basically the same, with minor differences (like midi support and music production). So im wondering if I should just use -generic or wait to see when some -rt kernel is available.

---

### Post by Ayuthia on 2008-06-08
> **crazyness003 said:**
> Actually, i skipped that one. I installed with -2.6.24-16-rt and autoupdated to 2.6.24-18-rt. If -17 was supported, I would assume the -18 would also support it.

I have to ask you, You said you use Ubuntu Studio, and you also have the -19 kernel installed right? Is it the 19-generic one or is it the default uStudio one 19-rt. Im just curious since i read an article about rt and it basically concluded that regular ones and realtime ones are basically the same, with minor differences (like midi support and music production). So im wondering if I should just use -generic or wait to see when some -rt one is available.
I don't think that I said I was on Studio.  If I did, I was mistaken.  I am using the 19-generic on Kubuntu.  You could try to use the -generic, but I would think that you would get the same result though but I don't have a strong enough reason to support my thought.

---

### Post by crazyness003 on 2008-06-09
> **Ayuthia said:**
> I don't think that I said I was on Studio.  If I did, I was mistaken.  I am using the 19-generic on Kubuntu.  You could try to use the -generic, but I would think that you would get the same result though but I don't have a strong enough reason to support my thought.

Sorry, I musta misunderstood. :S
Well in that case im gonna try a bunch of things and see how long it takes me to tank my system :D
I wanna thank everyone (esp. you, Ayuthia) For your help. If it wansnt for people like you, not so many would even try linux let alone get by with your awesome tutorials so easily. Again, thanks. I dont think i can stress that enough.

---

### Post by whorush on 2008-06-09
> **Ayuthia said:**
> Some people have had problems with getting WEP running with Network Manager.  Some have had better success with wicd or wifiradar.  You might try turning off Network Manager and connecting manually:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name> key <password>
sudo dhclient wlan0
```
Just replace <name> with the name of the network you ar trying to connect and replace <password> with your password.

hi,

i loved madison wisc when i visited.  we went shopping at that HUGE supermarket.  checked out the school and that neighborhood and the frank llyod wright building.  sweet.

right, my wireless is WEP, and i thought it might be a WEP problem, so i just took the security off, and i still couldnt log in.  but i still tried your plan.  here's the output including my joke password :-) ...


```
daniels@daniels-desktop:~$ sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
[sudo] password for daniels: 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
daniels@daniels-desktop:~$ sudo /etc/dbus-1/event.d/25NetworkManager stop
 * Stopping network connection manager NetworkManager                    [ OK ] 
daniels@daniels-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   Socket/fallback
daniels@daniels-desktop:~$ sudo iwconfig wlan0 essid bsk key 1357135713
daniels@daniels-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
daniels@daniels-desktop:~$ 

```

---

### Post by Unix_Slayer on 2008-06-09
> **whorush said:**
> almost, but not exactly.  the driver is installed, i can see the local networks, but nothing is greyed out.  i can really click each network and try to connect to it, and if the network is secure ubuntu asks me for a password, i just can't get on to them.  can't get on if its secure or not secure.  i tried restarting without my network cable and it still didnt work.  thanks for trying though.  any more ideas?

Damn drivers..... There is something up with the WPA/WPA2 pairing. What kind of network are you trying to connect to? Is it WEP or WPA/WPA2?

Ok... that answers my question. Wep also... Not even an open network will it connect to? I noticed this same problem before. I had to use knetworkmanager, and it was corrected. I don't know what X11 your running, and I see you were told to not use network manager.

---

### Post by Unix_Slayer on 2008-06-09
> **whorush said:**
> 
```
daniels@daniels-desktop:~$ sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
[sudo] password for daniels: 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
daniels@daniels-desktop:~$ sudo /etc/dbus-1/event.d/25NetworkManager stop
 * Stopping network connection manager NetworkManager                    [ OK ] 
daniels@daniels-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   Socket/fallback
daniels@daniels-desktop:~$ sudo iwconfig wlan0 essid bsk key 1357135713
daniels@daniels-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   LPF/wlan0/00:1e:8c:d9:f1:a7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
daniels@daniels-desktop:~$ 

```

That subnet mask doesn't look right. Did you manually config your router?

---

### Post by whorush on 2008-06-09
> Not even an open network will it connect to? I noticed this same problem before. I had to use knetworkmanager, and it was corrected. I don't know what X11 your running, and I see you were told to not use network manager.

my wireless router works because my roommates connect wirelessly all day.  and i dont think its a wep/wpa thing because i cant connect to it when i turn the security off (completely open it up) either.  you think its a network manager thing?  because i'm using the network manager thing, which is that icon on my taskbar and stuff :-).

i'm using the latest version of x11 for ubuntu amd64, 1:7.3+10ubuntu10.  thats a whacky version number.  why do you ask by the way?

> **Unix_Slayer said:**
> That subnet mask doesn't look right. Did you manually config your router?

i didnt, i dont know anything about these things?  is that the one thats 255.255.255.255?

thanks!
bradley

---

### Post by David Valentine on 2008-06-09
> **Ayuthia said:**
> You could try:
```
sudo iwconfig wlan0 rate 54M
```I tried that, but to no avail--the rate is still given as a paltry 1 Mb/s.  After I installed b43legacy, I got a new network interface called wmaster0--is that supposed to happen?  Here's my hardware:   ```
$ lspci | grep Broadcom
01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```Using bcm43xx under gutsy, I got 24 Mb/s.  Does this mean I need to go to NDISwrapper?:confused:

---

### Post by Ayuthia on 2008-06-09
> **David Valentine said:**
> I tried that, but to no avail--the rate is still given as a paltry 1 Mb/s.  After I installed b43legacy, I got a new network interface called wmaster0--is that supposed to happen?  Here's my hardware:   ```
$ lspci | grep Broadcom
01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```Using bcm43xx under gutsy, I got 24 Mb/s.  Does this mean I need to go to NDISwrapper?:confused:
wmaster0 is common with the new b43 driver.  Are you getting any different results?  You can reboot and see which driver will come up for you.  Ubuntu will determine whether you need b43 or b43legacy.

If you had better success with bcm43xx, you can still install the firmware for that driver.  All you have to do is install bcm43xx-fwcutter.  Once the firmware is installed, edit /etc/modprobe.d/blacklist (using sudo and your favorite editor) and remove the blacklisting for bcm43xx and blacklist b43.  If you don't want to do the configuring for bcm43xx, just install the firmware and run the attached application in the first post.  There is a button there to configure bcm43xx.

---

### Post by David Valentine on 2008-06-09
> You can reboot and see which driver will come up for you.  Ubuntu will determine whether you need b43 or b43legacy.It came back with b43legacy (from lsmod | grep b43).  I'll try going back to bcm43xx; it's a shame because I had hoped the new driver would enable the full 54 Mbps rate the 802.11g spec on this chipset...:-(

---

### Post by whorush on 2008-06-09
any more ideas?  i'm really stuck.  maybe b43-fwcutter has a bug or something.  should i try ndiswrapper?  maybe its just gnome's network manager?  if so, then i think when i tried to manually connect before it would have worked?  i put the output of that event in another thread.

thanks!

---

### Post by Unix_Slayer on 2008-06-09
> **whorush said:**
> my wireless router works because my roommates connect wirelessly all day.  and i dont think its a wep/wpa thing because i cant connect to it when i turn the security off (completely open it up) either.  you think its a network manager thing?  because i'm using the network manager thing, which is that icon on my taskbar and stuff :-).

i'm using the latest version of x11 for ubuntu amd64, 1:7.3+10ubuntu10.  thats a whacky version number.  why do you ask by the way?



i didnt, i dont know anything about these things?  is that the one thats 255.255.255.255?

thanks!
bradley


Yes.... It should be 255.255.255.0 unless if your using a different ip subset.

---

### Post by whorush on 2008-06-09
> **Unix_Slayer said:**
> Yes.... It should be 255.255.255.0 unless if your using a different ip subset.

i checked my router and the subnet mask is 255.255.255.0.  but i figure thats not the problem, since my roommates connect to it.

---

### Post by Unix_Slayer on 2008-06-09
> **whorush said:**
> i checked my router and the subnet mask is 255.255.255.0.  but i figure thats not the problem, since my roommates connect to it.

Are they using Windows? If they are, check their network properties for IPv4 and see what their settings are. Write down the DNS servers, and the gateway ip. You might have to do a manual config, instead of DHCP.

---

### Post by jimmy the saint on 2008-06-10
quick question.  This method involves a firmware change?  I am looking to enable wireless on a laptop that dual boots Vista (I know) and Ubuntu.  Will this firmware change affect vista's ability to utilize the card?

---

### Post by Unix_Slayer on 2008-06-10
> **jimmy the saint said:**
> quick question.  This method involves a firmware change?  I am looking to enable wireless on a laptop that dual boots Vista (I know) and Ubuntu.  Will this firmware change affect vista's ability to utilize the card?

No. The firmware is used in linux like a driver is used in Windows. I can understand your concern.

---

### Post by redbook4574 on 2008-06-10
Hi don;t know if this has already been covered, I have b43 drivers on a bcm4312 working great kernel 2,6.24.19, It automatically detected the card, loaded b43 asked if I wanted to load firmware and away it went, so no complaints there.

Anyway to the point it seems to have a strange mac address (00:00:00:1A:73:9E). Correct address for the card is (00:1A:73:9E:C2:17).
As you can see it seems to have added 2 new octets of 00.00 at the beginning and lost C2:17 from the end.

Does anybody know how to correct this ???

---

### Post by crazyness003 on 2008-06-10
I just wanted to post back and let everyone know that the 2.6.24-19 kernel is AWESOME! I got wifi working sweet-like! And according to 'KwifiManager" im connected at almost 54 mbps. Sweet!!! Thanks guys who rock so much.

> **redbook4574 said:**
> ...Anyway to the point it seems to have a strange mac address (00:00:00:1A:73:9E). Correct address for the card is (00:1A:73:9E:C2:17).
As you can see it seems to have added 2 new octets of 00.00 at the beginning and lost C2:17 from the end.

Does anybody know how to correct this ???

Same thing happend to me on 32bit and 64bit, but IMO i dont think it really matters as long as it works. But since you mention it, there is a way to try to manually correct it. Its risky and may mess everything up.

Theres a file
```
/etc/udev/rules.d/70-persistent-net.rules
```
That hold the info for your network devices. In there my mac address is all wonky like yours. I guess ***IF*** you really wanted to, you could modify that. I wouldnt since my wifi works as is. So, you decide. If you wanan do it, i'd back up the old file and if you tank it, hope that your backup will save you.

---

### Post by crazyness003 on 2008-06-10
> **jimmy the saint said:**
> quick question.  This method involves a firmware change?  I am looking to enable wireless on a laptop that dual boots Vista (I know) and Ubuntu.  Will this firmware change affect vista's ability to utilize the card?

Im not an expert, and if anyone knows better correct me, but the firmware that is loaded for ubuntu is loaded in the kernel, not the actual chip (im sure this isnt exactly how it happens), so im gonna assume that no, it will not affect Vista. 
But id wait to get a second opinion on that.

---

### Post by crazyness003 on 2008-06-10
> **whorush said:**
> any more ideas?  i'm really stuck.  maybe b43-fwcutter has a bug or something.  should i try ndiswrapper?  maybe its just gnome's network manager?  if so, then i think when i tried to manually connect before it would have worked?  i put the output of that event in another thread.

thanks!

Just a reminder, do you have a mac filter on your router? I know its seems simplistic, but if your mac isnt allowed, it wont connect. Just check to see. I was having a similar problem (and i was using XP at the time)

---

### Post by crazyness003 on 2008-06-10
Heres a semi-intelligent question:
Since im using GNOME (not that it matters)  what is the best network interface management software i should use. I have 
1. Network Manager
2. Network Selector
3. KWiFiManager
4. SWScanner (which crashes everytime i try to scan) and
5. RutilT WLAN Manager
And i also have heard of a "manual way" to do it. Does anyone have any suggestions and what i should use (preferably only one piece)
And if manual works better, how does it work?

ps: If I'm off topic, pleas direct me where to post for better results

---

### Post by Ayuthia on 2008-06-10
> **crazyness003 said:**
> Heres a semi-intelligent question:
Since im using GNOME (not that it matters)  what is the best network interface management software i should use. I have 
1. Network Manager
2. Network Selector
3. KWiFiManager
4. SWScanner (which crashes everytime i try to scan) and
5. RutilT WLAN Manager
And i also have heard of a "manual way" to do it. Does anyone have any suggestions and what i should use (preferably only one piece)
And if manual works better, how does it work?

ps: If I'm off topic, pleas direct me where to post for better results

I have been using wicd, but I prefer to go the manual route.  You should check out the sticky:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Kevdog does a pretty good job with helping you do things manually.

---

### Post by crazyness003 on 2008-06-10
> **Ayuthia said:**
> I have been using wicd, but I prefer to go the manual route.  You should check out the sticky:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Kevdog does a pretty good job with helping you do things manually.

Thanks. I looked for WICD in Synaptic but i cant seem to find it. Can anyone tell me which repo its from, maybe i havent added it.
I just wanna keep a gui for quick glances because i know old school is the best way to do it. 

> sudo make -mylife ./easier ;D

---

### Post by Ayuthia on 2008-06-10
> **crazyness003 said:**
> Thanks. I looked for WICD in Synaptic but i cant seem to find it. Can anyone tell me which repo its from, maybe i havent added it.
I just wanna keep a gui for quick glances because i know old school is the best way to do it. 

 ;D

I guess my memory is bad because I thought that it was in the repos, but actually the wicd site created their own repo for it:
deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras

Here is the link on how to install it:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by paul.roberts20 on 2008-06-11
I followed these steps, and that worked fine. I can now see my wireless network, but I can't connect to it.. I get the spinning icon next to the clock but the circles don't light up green.. can anyone help?

---

### Post by Ayuthia on 2008-06-11
> **paul.roberts20 said:**
> I followed these steps, and that worked fine. I can now see my wireless network, but I can't connect to it.. I get the spinning icon next to the clock but the circles don't light up green.. can anyone help?
If your router is encrypted, check and see if you can connect with the encryption turned off. 

You might also try unloading and reloading the module:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
I have found that sometimes the connection does not work so well using Network Manager.  

You can always try installing wicd (info posted in post 138) or wifi-radar.

Another way is to try the manual method:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
kevdog explains how to connect manually and also has a way to have the wireless connect at boot.

---

### Post by redbook4574 on 2008-06-11
Thanks for that,

Tried editing 70-persistent-net.rules.

all that happens is that wlan0 accepts the new mac but does not connect or even exist. A new connection of wlan1 is created with the old incorrect mac and connection goes ahead as normal on wlan1, so i think I will just leave things alone and put it down to weird linux things that happen but don't matter.

---

### Post by whorush on 2008-06-11
this howto for ndiswrapper worked for me.
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

problems i had...

1) i needed to use 32 bit ubuntu, 64 didnt work because the drivers i needed were 32 only.

2) ndiswrapper seemed to work much better, faster, better reception, etc. than b43-fwcutter.  and the instructions in this thread worked, except that i used the windows xp asus drivers for my asus WL-138g v2 card.

3) then i found network manager a bit annoying, asking me for a key everytime i logged in, so i used wicd, now i startup and it connects automatically.

summary) 32 bit ubuntu, this howto with asus winxp drivers, then wicd.

any questions, private message me.

thanks again!
bradley

---

### Post by Unix_Slayer on 2008-06-11
> **redbook4574 said:**
> Hi don;t know if this has already been covered, I have b43 drivers on a bcm4312 working great kernel 2,6.24.19, It automatically detected the card, loaded b43 asked if I wanted to load firmware and away it went, so no complaints there.

Anyway to the point it seems to have a strange mac address (00:00:00:1A:73:9E). Correct address for the card is (00:1A:73:9E:C2:17).
As you can see it seems to have added 2 new octets of 00.00 at the beginning and lost C2:17 from the end.

Does anybody know how to correct this ???

Is that the mac address stated on the card itself? If so, you would have to go into the config file, and manually correct it. Strange that it would pickup a wrong mac address.

---

### Post by Unix_Slayer on 2008-06-11
> **crazyness003 said:**
> Heres a semi-intelligent question:
Since im using GNOME (not that it matters)  what is the best network interface management software i should use. I have 
1. Network Manager
2. Network Selector
3. KWiFiManager
4. SWScanner (which crashes everytime i try to scan) and
5. RutilT WLAN Manager
And i also have heard of a "manual way" to do it. Does anyone have any suggestions and what i should use (preferably only one piece)
And if manual works better, how does it work?

ps: If I'm off topic, pleas direct me where to post for better results

I've had better luck with networkmanager. I tried wicd, and my system didn't like it all that well.

---

### Post by Unix_Slayer on 2008-06-11
> **whorush said:**
> 
3) then i found network manager a bit annoying, asking me for a key everytime i logged in, so i used wicd, now i startup and it connects automatically.

See I use knetworkmanager. Also, my kwallet holds that info for me so I don't have to re-enter it every time. I think Gnome should have something simular.

---

### Post by crazyness003 on 2008-06-11
> **whorush said:**
> this howto for ndiswrapper worked for me.
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

problems i had...

1) i needed to use 32 bit ubuntu, 64 didnt work because the drivers i needed were 32 only.

2) ndiswrapper seemed to work much better, faster, better reception, etc. than b43-fwcutter.  and the instructions in this thread worked, except that i used the windows xp asus drivers for my asus WL-138g v2 card.

3) then i found network manager a bit annoying, asking me for a key everytime i logged in, so i used wicd, now i startup and it connects automatically.

summary) 32 bit ubuntu, this howto with asus winxp drivers, then wicd.

any questions, private message me.

thanks again!
bradley
Dunno about your card, but all of my woes got solved with the 2.6.24-19 kernel. 32bit and 64bit. Since you already have it working, i wouldnt mess with it, but maybe in the future you might wanna fiddle with it. Of course im gonna assume that whatever thay did to the -19 one they're gonna keep in future releases.
-The less windows stuff you use in linux...the more linux-y everything becomes...
I guess those are some words of wisdom...anyone?

---

### Post by crazyness003 on 2008-06-11
> **Unix_Slayer said:**
> I've had better luck with networkmanager. I tried wicd, and my system didn't like it all that well.
Im most likely gonna go manual old-school "sudo gimme-wireless" than gui. But its good to use gui once in a while, since it gives feedback to the devs to make it better...plus peoples gets lazys.

Network manager keeps messing things up for me. But there is another one called Network selector that im kinda getting accustomed to. its kinda nice.

---

### Post by crazyness003 on 2008-06-11
> **Ayuthia said:**
> I guess my memory is bad because I thought that it was in the repos, but actually the wicd site created their own repo for it:
deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras

Here is the link on how to install it:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Thanks. Gonna try it in a sec

##Edit 1: Installed but cant get anything on it to work. No gui, no tray applet...nothin'

Edit 2: Restarted and everything works good, do ignore what i typed above.. 
I really like the WICD interface and tray icon. *****

---

### Post by rated_emman on 2008-06-12
hey guys! i downloaded that thing... but when i type: 

sudo ifconfig wlan0 up, this is what i get:

```
emman@emmanuel-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

anybody knows solution? :(

---

### Post by Ayuthia on 2008-06-12
> **rated_emman said:**
> hey guys! i downloaded that thing... but when i type: 

sudo ifconfig wlan0 up, this is what i get:

```
emman@emmanuel-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

anybody knows solution? :(
Can you go into the Terminal and post the results of:
```
lshw -C network
```

---

### Post by rated_emman on 2008-06-14
> **Ayuthia said:**
> Can you go into the Terminal and post the results of:
```
lshw -C network
```

here is the result:

```
emman@emmanuel-laptop:~$ sudo lshw -C network
[sudo] password for emman: 
PCI (sysfs)
```

thanks in advance :D

---

### Post by Ayuthia on 2008-06-14
> **rated_emman said:**
> here is the result:

```
emman@emmanuel-laptop:~$ sudo lshw -C network
[sudo] password for emman: 
PCI (sysfs)
```

thanks in advance :D
Can you post the results without the sudo?  Sometimes it gets stuck using sudo.

---

### Post by rated_emman on 2008-06-14
> **Ayuthia said:**
> Can you post the results without the sudo?  Sometimes it gets stuck using sudo.

here's the result:
```
emman@emmanuel-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
emman@emmanuel-laptop:~$ 

```

thanks for ur patience and willingness to help :D thanks :D i appriciate it

---

### Post by Ayuthia on 2008-06-14
> **rated_emman said:**
> here's the result:
```
emman@emmanuel-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
emman@emmanuel-laptop:~$ 

```
thanks for ur patience and willingness to help :D thanks :D i appriciate it


The 4311 rev 02 card does not work with the initial version of Hardy.  I think that it is  supposed to be working in 2.6.14-18 though.  You can check the version that you are running by:
```
uname -r
```
Otherwise, you might try NDISwrapper.  Here is a link to someone that has your card:
[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by rated_emman on 2008-06-14
i got this:

```
emman@emmanuel-laptop:~$ uname -r
2.6.24-16-generic

```

thanks for trying to help me :D i appreciate it :D
and yeah thanks for the link :)

---

### Post by Ayuthia on 2008-06-14
> **rated_emman said:**
> i got this:

```
emman@emmanuel-laptop:~$ uname -r
2.6.24-16-generic

```

thanks for trying to help me :D i appreciate it :D
and yeah thanks for the link :)
If you have any problems after trying the link, feel free to post either here or at that link.  I tend to watch that one also.

---

### Post by albywolf on 2008-06-15
Finally solved on my NB!!!
I have an HP Compaq 6715s with BCM4312 rev 02
With Kubuntu 7.10 32bit wireless only worked with ndiswrapper and second to last HP driver.
With 8.04 AMD64 wireless didn't work anymore with ndiswrapper, the interface was still listed by lspci, but not by iwconfig and it didn't appear in KNetworkManager settings and the Rastricted Drivers Manager didn't list any wireless interface or drivers for it.
Having done a clean 8.04 install, this I was able to try b43 before ndiswrapper, it didn't work. Updating kernel to 2.6.24-18-generic didn't solve.
Even tried patches, drivers and firmware from wireless.kernel.org, no luck. ](*,)
Then in [http://forum.ubuntu-it.org/index.php?topic=187938.msg1280331](http://forum.ubuntu-it.org/index.php?topic=187938.msg1280331) I stumbled upon a guy that yesterday tried enabling proposed and unsupported updates and then all for him worked. :-o :idea: 
I uninstalled b43-fwcutter, and ndiswrapper, checked that no b43 or b43legacy directories remained in /lib/modules, enabled proposed and unsupported updates, updated all the new things suggested, I noticed it proposed me 2.6.24-19-generic, installed, restarted choosing to boot this new kernel, installed b43-fwcutter, restarted, again choosing 2.6.24-19-generic, EVERYTHING WORKED!!!   :popcorn::popcorn: 
The only thing I still don't like is that while with Ubuntu and Xubuntu I can avoid password request to hook up to a wireless network giving my main password also to the password manager, with Kubuntu the only way to avoid a second password request after login is to keep the passkey in a kdewallet with blank password. Anyway it's really a minor disturb, I'm very happy, after only less than two months from release I have from the last Kubuntu full support for all my HW and I can enjoy all the improvements 8.04 introduced without drawbacks. \\:D/ :biggrin: ):P 

PS I read others in this thread that they too solved with 2.6.24-19, but I felt it could be useful adding my experience about the HP 6715s and BCM4312 rev 02, as in my past efforts I found around the net, and in this forum too, solutions involving previous kernels and/or ndiswrapper that solved for lots other NB and cards, but didn't work with every NB model with BCM4312 rev 02 and 6715s and 6715b looked like they were amongst the unlucky models. So I hope that explicitly mentioning in this thread the 6715s model will take people still struggling to a possible solution.

---

### Post by grandpa2390 on 2008-06-18
Sir that was beautiful. I had no ethernet connection either and your offline wireless installation tutorial was perfect to the Tee. I had to do the second step before the first but that was to be expected because i didn't have all required files. Thankyou again. the easiest wireless configuration i ever had to do.

---

### Post by LittleFoot on 2008-06-18
I've got a cheesy little dynex wireless usb for my laptop.  I have tested it on xp computers and it works just fine though I do have to install the driver.  I've attempted ndiswrapper as well as the b43 b43legacy and b43xx drivers alternately blacklisting the modules I was not using.  I installed the b43-fwcutter package through aptitude, and rebooted a few times.  So far I can't get it to work at all.  I've posted the output of lsusb -v as well as lsmod in thread [http://ubuntuforums.org/showthread.php?t=782903&highl](http://ubuntuforums.org/showthread.php?t=782903&highl)

Using the bcmlw5.inf from the install directory of the driver on the xp machine only results in invalid driver.  I've tried several combinations of those files and others that seemed to be associated with the inf found in the windows directory and have even used third party utilities to extract the driver from windows.  Ndiswrapper returned invalid driver after each attempt.

Any help is appreciated I've been banging my head against this wall all night.

---

### Post by Joker5bb on 2008-06-20
guys use kernel 2.6.25.7

---

### Post by Ayuthia on 2008-06-20
> **Joker5bb said:**
> guys use kernel 2.6.25.7

That is definitely an option, but it will require kernel compiling knowledge.  It could cause you to have to compile other items to get things to work.  Not a super difficult task, but not always a fun one unless you know what you are doing.

---

### Post by Joker5bb on 2008-06-20
> **Ayuthia said:**
> That is definitely an option, but it will require kernel compiling knowledge.  It could cause you to have to compile other items to get things to work.  Not a super difficult task, but not always a fun one unless you know what you are doing.

hey use my how-to here [http://tinyshell.be/aircrackng/forum/index.php?topic=3602.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3602.0)

please comment

:lolflag:

---

### Post by LittleFoot on 2008-06-20
Well I eventually was able to figure out how to get my drivers pulled from the cabs, and realized I has a *.sys file or two to many.  Now ndiswrapper is working.  Just to taunt me my laptop was actually able to connect through the wireless card.  Unfortunately I have no idea how it managed it since it happened while I was asleep and had left wpa_supplicant running, I woke up it had closed but the connection was working.  It then stopped after a reboot.  I've followed several tutorials for configuring wpa_supplicant, but I don't think it's working at the moment and it's not pulling dhcp information.  this card has been a real pain in the rear side.

---

### Post by Ayuthia on 2008-06-20
> **Joker5bb said:**
> hey use my how-to here [http://tinyshell.be/aircrackng/forum/index.php?topic=3602.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3602.0)

please comment

:lolflag:Nicely done!  The only comment that I have is that any kernel related packages that you have installed from the repositories will not work under the new kernel unless you compile them manually.  I am thinking of things like the Nvidia graphics driver or ndiswrapper.

Don't get me wrong, I think that this is great for those who have some experience with Linux and loves the adventure of taking a different path.  I generally have compiled kernels for Gentoo and it is fun, but I can see that it could cause a lot of frustration for those who have just started with Ubuntu.  It is also nice to try out the new wireless drivers as they come out and it also provide a great opportunity to learn more about your system and hardware.

---

### Post by Ayuthia on 2008-06-20
> **LittleFoot said:**
> Well I eventually was able to figure out how to get my drivers pulled from the cabs, and realized I has a *.sys file or two to many.  Now ndiswrapper is working.  Just to taunt me my laptop was actually able to connect through the wireless card.  Unfortunately I have no idea how it managed it since it happened while I was asleep and had left wpa_supplicant running, I woke up it had closed but the connection was working.  It then stopped after a reboot.  I've followed several tutorials for configuring wpa_supplicant, but I don't think it's working at the moment and it's not pulling dhcp information.  this card has been a real pain in the rear side.

Sorry I can't help too much on the WPA side of things.  I have not had a chance to play around with it yet.  I will try it out more when I get my laptop back from HP.  Apparently I had a motherboard defect that has prevented my network card from being detected.

---

### Post by Joker5bb on 2008-06-21
> **Ayuthia said:**
> Nicely done!  The only comment that I have is that any kernel related packages that you have installed from the repositories will not work under the new kernel unless you compile them manually.  I am thinking of things like the Nvidia graphics driver or ndiswrapper.

Don't get me wrong, I think that this is great for those who have some experience with Linux and loves the adventure of taking a different path.  I generally have compiled kernels for Gentoo and it is fun, but I can see that it could cause a lot of frustration for those who have just started with Ubuntu.  It is also nice to try out the new wireless drivers as they come out and it also provide a great opportunity to learn more about your system and hardware.

i know what you mean i had to make my graphics and sound work, not hard at all:)

---

### Post by Joker5bb on 2008-06-21
in the new 2.6.24-19 bugs have been fixed for b43.

---

### Post by Unix_Slayer on 2008-06-22
> **LittleFoot said:**
> Well I eventually was able to figure out how to get my drivers pulled from the cabs, and realized I has a *.sys file or two to many.  Now ndiswrapper is working.  Just to taunt me my laptop was actually able to connect through the wireless card.  Unfortunately I have no idea how it managed it since it happened while I was asleep and had left wpa_supplicant running, I woke up it had closed but the connection was working.  It then stopped after a reboot.  I've followed several tutorials for configuring wpa_supplicant, but I don't think it's working at the moment and it's not pulling dhcp information.  this card has been a real pain in the rear side.

What program are you using for your wireless connection?

---

### Post by Joker5bb on 2008-06-23
Supported Chips (Broadcom's AirForce&#8482; family)

# bcm4301
# bcm4303
# bcm4306
# bcm4307
# bcm4309
# bcm4311
# bcm4312
# bcm4318
# bcm4319

---

### Post by LittleFoot on 2008-06-24
Sadly my chip is a bcm4320.  Ndiswrapper is doing a passable job.  And encryption works up until I try WPA.  So far I've attempted every variant that seemed feasable according to the numerous tutorials and options I've reviewed and have had no success.  I did notice that with both network-manager-gnome and wicd that I cannot use a wep passphrase and have it work.  So far I'm limited to putting int the entries in hex when I need to connect.

---

### Post by David Valentine on 2008-06-24
> **Joker5bb said:**
> in the new 2.6.24-19 bugs have been fixed for b43.
Well, not all bugs--I'm still getting 1 MB/s with the new kernel and b43 on a broadcom 4306 chipset.  :(

---

### Post by Don DeGregori on 2008-06-24
Did fresh install of 8.04 and all updates. Was able to get BCM4306 to work on Fujitsu P5010D laptop using the "No-Fluff" procedure.

Can connect with open wireless (no encryption), but NOT with WPA. I believe I followed all the steps. No problem if I turn off wireless (switch on laptop) and use a TRENDnet USB access point. WPA connection is OK.

What can I do to get WPA working using internal BCM4306?

Thanks

---

### Post by Ayuthia on 2008-06-24
> **Don DeGregori said:**
> Did fresh install of 8.04 and all updates. Was able to get BCM4306 to work on Fujitsu P5010D laptop using the "No-Fluff" procedure.

Can connect with open wireless (no encryption), but NOT with WPA. I believe I followed all the steps. No problem if I turn off wireless (switch on laptop) and use a TRENDnet USB access point. WPA connection is OK.

What can I do to get WPA working using internal BCM4306?

Thanks

Have you tried this [link]("http://ubuntuforums.org/showthread.php?t=318539")?  Unfortunately, I am out of town right now and my Dell laptop is at home (it has the 4306 rev 03 card) so I am unable to test it right now.  I plan to do some WPA testing on my 4311 rev 01 and my 4306 rev 03 card when I get back next week.

---

### Post by LittleFoot on 2008-06-25
> **Unix_Slayer said:**
> What program are you using for your wireless connection?

I have used both `Network-Manager + Network-Manager-Gnome` and Wicd
both use the wpa_supplicant backend as far as I know.  Is there another wpa backend that may pull it off?

---

### Post by oniichan on 2008-06-25
I had the same problem after the kernel upgradw, i.e. 1MB/s. Uninstall and reinstall the driver 'bcmwl5.inf', reboot, and I was back to 5MB/s. It's not 54MB/s but better 5 than 1.

---

### Post by LittleFoot on 2008-06-27
> **Ayuthia said:**
> Have you tried this [link]("http://ubuntuforums.org/showthread.php?t=318539")?  Unfortunately, I am out of town right now and my Dell laptop is at home (it has the 4306 rev 03 card) so I am unable to test it right now.  I plan to do some WPA testing on my 4311 rev 01 and my 4306 rev 03 card when I get back next week.
Yep gave it a shot, great tutorial.  Didn't work for me but I could see how it should for most.

---

### Post by buccaneere on 2008-06-29
Worked on 2 machines; HPdv 9000 w/bcom 4311; dell d600 w/4309.

Now, do you know what this attached means on an Atheros wireless (which works only after 'networking restart', and needed a start-up script)?

---

### Post by LittleFoot on 2008-06-29
> **buccaneere said:**
> Worked on 2 machines; HPdv 9000 w/bcom 4311; dell d600 w/4309.

Now, do you know what this attached means on an Atheros wireless (which works only after 'networking restart', and needed a start-up script)?

This post might be relevent.  [http://ubuntuforums.org/showthread.php?p=5238628](http://ubuntuforums.org/showthread.php?p=5238628)

*edit what was in the post led me to removing the avahi-daemon package which has cleared up my wpa problem and things are now working more or less correctly.  avahi was apparently creating wlan0:avahi and blocking dhcp configuration.  Not sure if there is a better work around.

---

### Post by buccaneere on 2008-06-29
> **LittleFoot said:**
> This post might be relevent.  [http://ubuntuforums.org/showthread.php?p=5238628](http://ubuntuforums.org/showthread.php?p=5238628)

*edit what was in the post led me to removing the avahi-daemon package which has cleared up my wpa problem and things are now working more or less correctly.  avahi was apparently creating wlan0:avahi and blocking dhcp configuration.  Not sure if there is a better work around.

Thanks there LFoot... Looks like the fix. 

Mine is 'ath0:avahi', and the other OP's error was 'wlan:avahi'. I'm gonna' wait for some feedback from him. If I don't know how to reverse what I've done, I won't do it, and I don't see a clear explanation of what this does.

For the meantime, just a few workarounds brings up wireless after booting.

Good lead!




I don't suppose you know about Edgy wireless too???

---

### Post by LittleFoot on 2008-06-29
> **buccaneere said:**
> Thanks there LFoot... Looks like the fix. 

Mine is 'ath0:avahi', and the other OP's error was 'wlan:avahi'. I'm gonna' wait for some feedback from him. If I don't know how to reverse what I've done, I won't do it, and I don't see a clear explanation of what this does.

For the meantime, just a few workarounds brings up wireless after booting.

Good lead!




I don't suppose you know about Edgy wireless too???

Good to hear it's working.  Nope to Edgy wireless but I know linux. :)  Remember the three R's Research, Research, Research.

---

### Post by bluzepher on 2008-06-29
Code:

cd /tmp
unzip R20071019.exe

[COLOR="Purple"]after that, open ndiswrapper and isntall the file bcmwl5.inf
you will find it at /tmp->WPMN300N->drivers->xp_2k
[/COLOR]

I am hung up here ^  {dont know how to install bcmwl5.inf}  

then command at terminal
Code:




my lshw -C network  comes up with network disabled.


 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:79:3c:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:23:13:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g




ndiswrapper -l

if the answer is something like this
Code:

Installed ndis drivers:
{name of driver}* driver present, hardware present


thanks

---

### Post by buccaneere on 2008-06-29
> **bluzepher said:**
> Code:

cd /tmp
unzip R20071019.exe

[COLOR="Purple"]after that, open ndiswrapper and isntall the file bcmwl5.inf
you will find it at /tmp->WPMN300N->drivers->xp_2k
[/COLOR]

I am hung up here ^  {dont know how to install bcmwl5.inf}  

then command at terminal
Code:




my lshw -C network  comes up with network disabled.


 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:79:3c:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:23:13:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g




ndiswrapper -l

if the answer is something like this
Code:

Installed ndis drivers:
{name of driver}* driver present, hardware present


thanks

Try this...
> sudo ndiswrapper -i bcmwl5.inf

---

### Post by LittleFoot on 2008-07-01
in my case I also had to manually copy the sys files
notauser@box:/etc/ndiswrapper/bcmwl5$ ls
0A5C:D11B.F.conf  bcmwl5.inf  rndismpx.sys  usb8023x.sys
and reboot for the system to give anything other than invalid driver.

---

### Post by crazyness003 on 2008-07-24
Well, it seems like no one has poster here in a while. I would consider that a good thing, since wifi cards all over the grid are being supported out of the box...and ones that arent, have fixes already mentioned in this thread. I consider this a successful HowTo.

I would like to personally thank Ayuthia for the infinite knowledge and patience. Also everyone else, bravo.

---

### Post by fdhenard on 2008-07-25
Thank you for this HowTo.  It's the one that got me going with wireless.

---

### Post by lousy.ratbag on 2008-07-29
> **Joker5bb said:**
> Supported Chips (Broadcom's AirForce™ family)

# bcm4301
# bcm4303
# bcm4306
# bcm4307
# bcm4309
# bcm4311
# bcm4312
# bcm4318
# bcm4319
how is it supported - native driver, via ndiswrapper, or by some other means?

my bcm4303 works fine on 2.6.22-14 using ndiswrapper, but on no later kernel including the abovementioned ...-19

---

### Post by Ayuthia on 2008-07-29
> **lousy.ratbag said:**
> how is it supported - native driver, via ndiswrapper, or by some other means?

my bcm4303 works fine on 2.6.22-14 using ndiswrapper, but on no later kernel including the abovementioned ...-19
The bcm4303 card only works for the 802.11b chips only with the native driver.  If you are able to get it to work with ndiswrapper on 2.6.22, you should be able to get it to work with the newer kernels.  You do have to use ndiswrapper versions 1.50 or higher.  You will also have to do more blacklisting also because there is a new native driver introduced in 2.6.24.

---

### Post by khaoslove on 2008-08-10
Hi all, I'm new to linux trying to switch from win-blows.  I have an HP DV9000 series laptop, with the Broadcom BCM4311 wireless card, i've tried this and several other threads and, guess what.....no luck.  I don't know what i'm doing wrong. I can get the xp driver to install, but thats about it.  I didn't see any errors pop up on any of the steps I did.  

Please msg back with information you need to see what is wrong.  I really would appreciate the help.

---

### Post by pippo_jedi on 2008-08-10
> **khaoslove said:**
> Hi all, I'm new to linux trying to switch from win-blows.  I have an HP DV9000 series laptop, with the Broadcom BCM4311 wireless card, i've tried this and several other threads and, guess what.....no luck.  I don't know what i'm doing wrong. I can get the xp driver to install, but thats about it.  I didn't see any errors pop up on any of the steps I did.  

Please msg back with information you need to see what is wrong.  I really would appreciate the help.

could it be an acpi problem? I mean: come notebook (mine too) have problems with acpi. that is the software doesn't control well, or at all, the power of some of it's component: I had this problem and I discovered that the card did work, but that as the sistem started the "antenna was powered down" so it wouldn't work, try pushing the fn+something to see if it's working, and investigate in this direction, it may be worth: it was for me at least... bye bye

I have a 4318 on an asus a7d laptop by the way

---

### Post by paul.blair on 2008-08-10
I have a 4318 and after days of playing around, I found that the card did not connect on higher channels (10-13). My router was set to channel 13 to try and find some clean air, but as soon as I changed this, the card connected happily. Also when the router channel was set to 'auto' I would get varying connection success as the router used these higher wi-fi channels. If you are having issues, it might be worth checking this as it's very easy to set your wireless router to a lower channel. Hope this helps someone.

---

### Post by Ayuthia on 2008-08-10
> **khaoslove said:**
> Hi all, I'm new to linux trying to switch from win-blows.  I have an HP DV9000 series laptop, with the Broadcom BCM4311 wireless card, i've tried this and several other threads and, guess what.....no luck.  I don't know what i'm doing wrong. I can get the xp driver to install, but thats about it.  I didn't see any errors pop up on any of the steps I did.  

Please msg back with information you need to see what is wrong.  I really would appreciate the help.

Can you help provide the results of:
```
lshw -C network
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e wl
uname -a
```

It will help us see what modules your card is trying to use and tell us which version of Ubuntu you are using (32 or 64-bit).  It could just be that the XP driver you are using is the wrong version of Ubuntu.

---

### Post by khaoslove on 2008-08-12
> **Ayuthia said:**
> Can you help provide the results of:
```
lshw -C network
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e wl
uname -a
```

It will help us see what modules your card is trying to use and tell us which version of Ubuntu you are using (32 or 64-bit).  It could just be that the XP driver you are using is the wrong version of Ubuntu.
Hey thanks for your help.  I actually tried a fresh install of the latest version of ubuntu and the -19 kernel, sorry i can't remember right now what the rest of the number is.  and it seems to have worked just fine.  Only problem now is if i close my screen, I can't get the video back up...blasted thing; works great with everything else even the SD card slot and CD burnning!

---

### Post by PhantomOG on 2008-08-14
when I run:

sudo aptitude install b43-fwcutter

I get among other things:

Couldn't find any package whose name or description matched "b43-fwcutter"
Couldn't find any package whose name or description matched "b43-fwcutter"

My laptop has a wired internet connection, I'm using it in ubuntu to reply to this thread.  I know its probably something stupid, but I'd appreciate any help.
Thanks.

---

### Post by Ayuthia on 2008-08-14
> **PhantomOG said:**
> when I run:

sudo aptitude install b43-fwcutter

I get among other things:

Couldn't find any package whose name or description matched "b43-fwcutter"
Couldn't find any package whose name or description matched "b43-fwcutter"

My laptop has a wired internet connection, I'm using it in ubuntu to reply to this thread.  I know its probably something stupid, but I'd appreciate any help.
Thanks.

By any chance have you run any updates in Ubuntu yet:
```
sudo aptitude update
```
If you have, can you check and see if your /etc/apt/sources.list has the deb lines uncommented (they should not start with a #)?

---

### Post by PhantomOG on 2008-08-14
Update would require a network connection right?  If so, no.  Just a few minutes ago was the first time I plugged in the network cable and all I did was open firefox to this forum and run that line in the terminal.  When I first booted up (no network connection) there was a popup about updates but I have ignored it, I believe there is still an icon in the upper right (down arrow or something).

I'm in Vista right now so I'll reboot into ubuntu and check out sources.list file.  Thank you so much for your help with this.

---

### Post by PhantomOG on 2008-08-14
Sorry for the long post but this is my entire sources.list file:

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Ayuthia on 2008-08-14
> **PhantomOG said:**
> Update would require a network connection right?  If so, no.  Just a few minutes ago was the first time I plugged in the network cable and all I did was open firefox to this forum and run that line in the terminal.  When I first booted up (no network connection) there was a popup about updates but I have ignored it, I believe there is still an icon in the upper right (down arrow or something).

I'm in Vista right now so I'll reboot into ubuntu and check out sources.list file.  Thank you so much for your help with this.

If you have not done the updates, it would not hurt to just do the updates without installing them.  The key part is to update the package list so that you can find b43-fwcutter.  When you do:
```
sudo aptitude update
```you should get somewhere around 25-30 lines of updates.  

EDIT:  I just saw your previous post and the sources.list file looks ok.  You should just have to do:
```
sudo aptitude udpate
sudo aptitude install b43-fwcutter
```and hopefully it will do it. :)

---

### Post by PhantomOG on 2008-08-14
ok, did the aptitude update and installed b43-fwcutter, said yes to firmware.

Then I ran sudo ifconfig wlan0 up and get:
wlan0: ERROR while getting interface flags: No such device

---

### Post by Ayuthia on 2008-08-14
> **PhantomOG said:**
> ok, did the aptitude update and installed b43-fwcutter, said yes to firmware.

Then I ran sudo ifconfig wlan0 up and get:
wlan0: ERROR while getting interface flags: No such device

Please post the results for the following commands:
```
lsmod |grep -i -e b43 -e bcm43xx -e ssb -e wl -e ndiswrapper
uname -a
lshw -C network
```
The first command will let us know what modules are currently loaded, the second command will tell us what kernel version you are using and if it is 32 or 64 bit, and the last command will hopefully let us know what logical name your card is.

---

### Post by PhantomOG on 2008-08-14
nothing for the first line returned

second:
Linux laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:bb:54:ab
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.104 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by Ayuthia on 2008-08-14
> **PhantomOG said:**
> nothing for the first line returned

second:
Linux laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:bb:54:ab
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.104 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

I am thinking that the module has not been loaded.  The b43-fwcutter just creates the firmware for the module, but does not load it.  Try the following:
```
sudo modprobe b43
sudo ifconfig wlan0 up
```

---

### Post by Ayuthia on 2008-08-14
> **PhantomOG said:**
> 
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

I just noticed that you have a 4328 card.  Since it is a wireless-n card, there is good chance that the b43 driver is not going to work because the wireless-n cards are not supported yet.

Your choices are to try using ndiswrapper or trying a pre-release kernel.  For ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

For the pre-release version:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you do choose the pre-release version, there are always chances that your system might not work properly.  This is because it is still being tested.  However, you always will be able to go back to the previous kernel and use it and things should be like it is right now.

---

### Post by PhantomOG on 2008-08-14
thank you so much Ayuthia.  I opted for the ndiswrapper since it was so well documented and it worked wonderfully.

Now, on to other issues!

---

### Post by John R Carson on 2008-08-15
Worked? YES...but!

john@KI4BLT:~$ uname -a
Linux KI4BLT 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

john@KI4BLT:~$ lspci | grep Broadcom
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

john@KI4BLT:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:CC:9C:D1
                    ESSID:"Blakslee Retreat"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=88/100  Signal level=-45 dBm  Noise level=-69 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007cc9e2be0f

john@KI4BLT:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Blakslee Retreat"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:CC:9C:D1   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=90/100  Signal level=-44 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I followed the instructions in the HowTo pretty carefully, following those related to not having Internet in Ubuntu, and no install CD.  I did have a working wireless under Vista.

Many thanks for the information about Network Manager's problems with WEP and WPA/WPA2.  I used the manual configuration:

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name> key <password>
sudo dhclient wlan0

That was the final step to connecting!

---

### Post by John R Carson on 2008-08-15
Worked? YES!

john@KI4BLT:~$ uname -a
Linux KI4BLT 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

john@KI4BLT:~$ lspci | grep Broadcom
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

john@KI4BLT:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:CC:9C:D1
                    ESSID:"Blakslee Retreat"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=88/100  Signal level=-45 dBm  Noise level=-69 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007cc9e2be0f

john@KI4BLT:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Blakslee Retreat"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:CC:9C:D1   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=90/100  Signal level=-44 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I followed the instructions in the HowTo pretty carefully, following those related to not having Internet in Ubuntu, and no install CD.  I did have a working wireless under Vista.

Many thanks for the information about Network Manager's problems with WEP and WPA/WPA2.  I used the manual configuration:

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name> key <password>
sudo dhclient wlan0

That was the final step to connecting!:lolflag:

Many thanks especially to Ayuthia, and to all who contributed to this thread!

---

### Post by phoenixphyre on 2008-08-19
ok small problem and i would love some help. this is all the stuff i get from terminal when i try to install wireless config.

phoenixphyre@phoenixphyre-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

phoenixphyre@phoenixphyre-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ab:3f:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.3 latency=64 module=ssb multicast=yes

phoenixphyre@phoenixphyre-laptop:~$ sudo aptitude install b43-fwcutter
[sudo] password for phoenixphyre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done

phoenixphyre@phoenixphyre-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

now i followed the instructions, what in the heck does this last part mean?

---

### Post by Ayuthia on 2008-08-19
> **phoenixphyre said:**
> ok small problem and i would love some help. this is all the stuff i get from terminal when i try to install wireless config.

phoenixphyre@phoenixphyre-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

phoenixphyre@phoenixphyre-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ab:3f:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.3 latency=64 module=ssb multicast=yes

phoenixphyre@phoenixphyre-laptop:~$ sudo aptitude install b43-fwcutter
[sudo] password for phoenixphyre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done

phoenixphyre@phoenixphyre-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

now i followed the instructions, what in the heck does this last part mean?
The last part means that there was no wlan0.  Unfortunately, wireless-n cards are not supported yet.

Your choices are to try using ndiswrapper or trying a pre-release kernel. For ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

For the pre-release version:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you do choose the pre-release version, there are always chances that your system might not work properly. This is because it is still being tested. However, you always will be able to go back to the previous kernel and use it and things should be like it is right now.

---

### Post by graafh on 2008-08-20
**After trying and reading (a lot of both) I got my Broadcom 4328 working, stable, and relatively fast, with WPA2 and static address.**

Ubuntu: Hardy
Machine: Dell 1525, dual OS (Ubuntu; Vista)
Wireless router: Linksys 150N (Draft N)
Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
Using ndiswrapper, with bcmwl5.inf from the Dell patch R151517.EXE
With wpasupplicant and network manager I could see the wireless networks, but was unable to get a working connection. 
Finally, I tried WICD (default install, using WEXT as WPA supplicant (WICD menu: preferences).
(Installing WICD removes network manager: some people were having problems to get network manager back)

Still no working connection.
Router is Linksys 150N, it supports b/g/n.
After changing the network mode of the router from MIXED (which is B/G/N) to B/G MIXED, everything was and still is working! 
(Time from starting to connect until being able to browse the network takes about 50 secs, so don't be too soon drawing conclusions)
BTW: The mixed mode causes no problems with Vista.

Some speed info: copying a video DVD from another (Windows XP) machine:
With Ubuntu: 2.7 Mbyte/sec (router network mode set on B/G MIXED)
With Vista : 2.9 Mbyte/sec (router network mode set on B/G MIXED)
With Vista : 4.1 Mbyte/sec (router network mode set on MIXED)

Conclusion: For my router, at least changing the router network mode was necessary. Maybe this was the only necessary change, although it looks like WICD has a better WPA support than NM? (This I will only know after reinstalling network manager, or even a complete reinstall of Ubuntu). Furthermore: Establishing a working connection takes about a minute (now, on my machine). Don't be too quick when testing a certain setting!

---

### Post by madj0ck on 2008-08-25
Thanks, that worked  np for me.  My wireless h/w registerd as BCM4318.

Thanks,
madj0ck

---

### Post by Dremora on 2008-08-26
Thank you so much for this!

---

### Post by dm47 on 2008-08-29
so I'm pretty new to ubuntu, and linux in general, with only a mild understand of it's overall construction and the concept behind such a versatile operating system.

anyways, I unfortunately have a Broadcom BCM4306 wireless PCI card, so inevitably i was facing some trouble.

At first, I was going to make a huge post about my problem, because despite the dozens of threads I read about different broadcom cards and their functionality on hardy, each thread was entirely different and many required a wired internet connection, which I didn't have.

But I found this thread, which explained what to do without an internet connection so I thought I'd try it.  To make a long story short I entered the first three commands listed in the tutorial.  ```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```

No matter how hard I tried, the following 2 commands ```
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
``` would not work, giving me a "cannot resolve host" error (I think).

So initially I was discouraged but then I saw some new activity in the wireless recognition, and suddenly my network appeared.  So I entered my WPA key and viola!  Every was suddenly working.  Now obviously this isn't a huge problem, and trust me when I say that I was thrilled, but basically, I don't understand why it worked.  I didn't even do the last 2 steps!  lol

So yea, it's not a big deal that I know why, but I like to understand things, and the more I learn about linux the better.  This is a really long post... so I'm done.  It's my first post btw ;).

So if you have any idea what went on here, just post it I guess, and if nothing unusual happened and I'm just being dumb, say that too, lol.  Thanks guys,

---

### Post by YourClone on 2008-08-29
Nice guide. I've been looking for this for a while.

I have the Broadcom BCM4309 chip, and have been using Windows because the wireless didn't work. Now I'm full Ubuntu!

Thanks!

---

### Post by Ayuthia on 2008-08-30
> **dm47 said:**
> 
No matter how hard I tried, the following 2 commands ```
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
``` would not work, giving me a "cannot resolve host" error (I think).

The only thing that I can think of right now is that the logical name of your card is eth1 instead of wlan0.  I could be wrong though.  The key part is that the firmware is installed.  Once it is installed and the module is reloaded (either by modprobe or by restarting), Network Manager will be able to function.  Network Manager does similar commands that will turn on your card, find wireless connections, and connect.

If you want to see what the logical name of your card (wlan0, eth1, etc.), you can type this in the Terminal:
```
lshw -C network
```and look for "Logical Name:" under your wireless card.

---

### Post by Beth1957 on 2008-09-05
Thank you, Ayuthia; lovely clear instructions got my wireless up & running at first attempt.

---

### Post by EmperorMoo on 2008-09-11
Many thanks for this excellent guide and your kind support to those less knowledgeable.  After 2-3 hours of experimentation, I have my card up and running.

I would advise those who have spent time doing this on a fresh install to do the simple-and-classic "turn it off and on again" - this was what finally fixed it for me.  I had tried

```
 sudo /etc/init.d/networking restart 
```

but I still found it necessary to restart the machine.

Also, I am still getting this error:

```

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801

```

I read your answer to someone who posted about it earlier, but I didn't fully understand the answer.  Is it something I need to be concerned about, or should I worry about it later?

Thanks again

---

### Post by Ayuthia on 2008-09-12
> **EmperorMoo said:**
> Many thanks for this excellent guide and your kind support to those less knowledgeable.  After 2-3 hours of experimentation, I have my card up and running.

I would advise those who have spent time doing this on a fresh install to do the simple-and-classic "turn it off and on again" - this was what finally fixed it for me.  I had tried

```
 sudo /etc/init.d/networking restart 
```

but I still found it necessary to restart the machine.

Also, I am still getting this error:

```

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801

```

I read your answer to someone who posted about it earlier, but I didn't fully understand the answer.  Is it something I need to be concerned about, or should I worry about it later?

Thanks again

You don't really need to worry about it.  I can't seem to remember what causes this, but it has not caused a problem for me.

---

### Post by djamie on 2008-09-24
First off, let me say I am a complete newbie to linux.  At the advice of a friend I decided to load Hardy Heron 8.04 on an aging presario 2500 to extend its useful life.  The distribution loaded find, but I found I had no wireless connectivity when I tried to search for available networks using network icon at top of page.  After searching this forum i came across this post.  I opted for option 1 for installation as I was able to connect to internet by ethernet.  I thought the driver installation for my BCM4306 Rev 2 went well as I can now see available wireless networks when I use the network icon.  However, when i try to connect the icon does the two black circle thing but they never turn green and I am not able to connect to any networks. I've tried both secured (WPA) and open networks.  I've posted what appears to be the information most asked for in this post.... PLEASE HELP

root@keith-laptop:/home/keith# lspci -nn | grep Broadcom
```
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
root@keith-laptop:/home/keith# lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43legacy             127776  0 
mac80211              165652  1 b43legacy
ssb                    34308  1 b43legacy
```

root@keith-laptop:/home/keith# lshw -C network
```
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a8:6e:81
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:cd:74:b0:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

root@keith-laptop:/home/keith# iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:8D:92:61
                    ESSID:"KHAN"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/100  Signal level=-77 dBm  Noise level=-63 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000cc046fb188
          Cell 02 - Address: 00:xx:xx:xx:xx:xx
                    ESSID:"Some SSID"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=86/100  Signal level=-37 dBm  Noise level=-63 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000c18fd7e181
```

---

### Post by Rocko262c on 2008-09-26
> **YourClone said:**
> Nice guide. I've been looking for this for a while.

I have the Broadcom BCM4309 chip, and have been using Windows because the wireless didn't work. Now I'm full Ubuntu!

Thanks!
Dear yourClone,
I am glad to hear that your wireless works now in Ubuntu.  We have the same card, but does your cable connection work?  I am not sure what set of instructions you have used, but I basically have the driver running through Ndiswrapper and the cable connection now doesn't work.  I have read tons and tons of forums and have seen that people have to run one connection or the other in Hardy.  Can you please help?
Thanks,
Martin

---

### Post by martin15s on 2008-09-26
thanks very much - works perfectly with my Dell 1370/Bcm 4318:)

---

### Post by Ayuthia on 2008-09-26
> **djamie said:**
> First off, let me say I am a complete newbie to linux.  At the advice of a friend I decided to load Hardy Heron 8.04 on an aging presario 2500 to extend its useful life.  The distribution loaded find, but I found I had no wireless connectivity when I tried to search for available networks using network icon at top of page.  After searching this forum i came across this post.  I opted for option 1 for installation as I was able to connect to internet by ethernet.  I thought the driver installation for my BCM4306 Rev 2 went well as I can now see available wireless networks when I use the network icon.  However, when i try to connect the icon does the two black circle thing but they never turn green and I am not able to connect to any networks. I've tried both secured (WPA) and open networks.  I've posted what appears to be the information most asked for in this post.... PLEASE HELP

root@keith-laptop:/home/keith# lspci -nn | grep Broadcom
```
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
root@keith-laptop:/home/keith# lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43legacy             127776  0 
mac80211              165652  1 b43legacy
ssb                    34308  1 b43legacy
```

root@keith-laptop:/home/keith# lshw -C network
```
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a8:6e:81
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:cd:74:b0:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

root@keith-laptop:/home/keith# iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:8D:92:61
                    ESSID:"KHAN"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/100  Signal level=-77 dBm  Noise level=-63 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000cc046fb188
          Cell 02 - Address: 00:xx:xx:xx:xx:xx
                    ESSID:"Some SSID"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=86/100  Signal level=-37 dBm  Noise level=-63 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000c18fd7e181
```

Let's see if any messages are showing up in dmesg.  We can test it out by doing:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper bcm43xx wl
sudo modprobe b43legacy
sudo ifconfig wlan0 up
dmesg|grep b43legacy
```
This will remove the wireless drivers, install b43legacy back, start up the card, and then look for any error messages.  Let us know if any odd messages show up in dmesg or just post the results.

Can you also post your ifconfig results (sudo ifconfig)?  Thanks!

It could also be that NetworkManager is not playing well with your card.  We might need to turn off NetworkManager and see if you can connect via the command line.  If you can, you might need to install a different network manager.  This will turn off NetworkManager for this session (you will just need to reboot to turn it back on):
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```You should turn off encryption and then try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper bcm43xx wl
sudo modprobe b43legacy
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "Some SSID"
sudo dhclient wlan0
```

---

### Post by djamie on 2008-09-26
> **Ayuthia said:**
> Let's see if any messages are showing up in dmesg.  We can test it out by doing:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper bcm43xx wl
sudo modprobe b43legacy
sudo ifconfig wlan0 up
dmesg|grep b43legacy
```
This will remove the wireless drivers, install b43legacy back, start up the card, and then look for any error messages.  Let us know if any odd messages show up in dmesg or just post the results.

Can you also post your ifconfig results (sudo ifconfig)?  Thanks!

It could also be that NetworkManager is not playing well with your card.  We might need to turn off NetworkManager and see if you can connect via the command line.  If you can, you might need to install a different network manager.  This will turn off NetworkManager for this session (you will just need to reboot to turn it back on):
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```You should turn off encryption and then try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper bcm43xx wl
sudo modprobe b43legacy
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "Some SSID"
sudo dhclient wlan0
```

keith@keith-laptop:~$ sudo modprobe -r b43 b43legacy ssb ndiswrapper bcm43xx wl
[sudo] password for keith: 
keith@keith-laptop:~$ sudo modprobe b43legacy
keith@keith-laptop:~$ sudo ifconfig wlan0 up
keith@keith-laptop:~$ dmesg|grep b43legacy
```
[   33.211580] b43legacy-phy0: Broadcom 4306 WLAN found
[   33.236502] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   33.236526] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   33.259347] b43legacy-phy0 debug: Radio initialized
[   44.643831] b43legacy-phy0 debug: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   44.749171] b43legacy-phy0 debug: Chip initialized
[   44.749578] b43legacy-phy0 debug: 30-bit DMA initialized
[   44.749716] b43legacy-phy0 debug: Wireless interface started
[   44.749723] b43legacy-phy0 debug: Adding Interface type 2
[  198.635280] b43legacy-phy0 debug: Removing Interface type 2
[  198.648162] b43legacy-phy0 debug: Wireless interface stopped
[  198.650963] b43legacy-phy0 debug: DMA-32 0x0260 (RX) max used slots: 1/64
[  198.651531] b43legacy-phy0 debug: DMA-32 0x0200 (RX) max used slots: 1/64
[  198.651826] b43legacy-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  198.659295] b43legacy-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  198.667272] b43legacy-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  198.675282] b43legacy-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  198.683264] b43legacy-phy0 debug: DMA-32 0x0220 (TX) max used slots: 4/128
[  198.691380] b43legacy-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  198.699255] b43legacy-phy0 debug: Radio initialized
[  198.699273] b43legacy-phy0 debug: Radio initialized
[  209.658525] b43legacy-phy0: Broadcom 4306 WLAN found
[  209.680883] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[  209.680913] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  209.704884] b43legacy-phy0 debug: Radio initialized
[  210.215038] b43legacy-phy0 debug: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  210.281037] b43legacy-phy0 debug: Chip initialized
[  210.281921] b43legacy-phy0 debug: 30-bit DMA initialized
[  210.284901] b43legacy-phy0 debug: Wireless interface started
[  210.292846] b43legacy-phy0 debug: Adding Interface type 2
```

keith@keith-laptop:~$ sudo ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:a8:6e:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53200 (51.9 KB)  TX bytes:53200 (51.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:cd:74:b0:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-CD-74-B0-D3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I've also tried configuring manually.... but get the following..

keith@keith-laptop:~$ sudo dhclient wlan0
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0b:cd:74:b0:d3
Sending on   LPF/wlan0/00:0b:cd:74:b0:d3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

One thing I find interesting is when I enter ```
lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```, I seem to get much less entries than most people in this post (see previous output).

---

### Post by Ayuthia on 2008-09-27
> **djamie said:**
> 
One thing I find interesting is when I enter ```
lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```, I seem to get much less entries than most people in this post (see previous output).

You can try doing the following:
```
sudo modprobe -r b43legacy ssb
sudo depmod -a
sudo modprobe b43legacy
sudo lsmod|grep b43legacy
```
The depmod will rebuild the dependencies for the modules.  I am not for sure if that will help or not though.

You can try changing the channel on your router to see if it makes a difference or not.  Otherwise, you might try out either ndiswrapper or bcm43xx (the depreciated driver).

---

### Post by PFSpectrum on 2008-10-01
I love you! It worked for me! =D your my hero =]

---

### Post by TheSmokingGNU on 2008-10-09
hey, question... I have a dual boot system, running ubuntu and xp home... I am using a neighbor's wireless signal, so i don't know the proper configuration for it. how do i get this thing working?
I have internet when on my windows, and I am using a Belkin Wireless G Desktop card. intel core 2 duo e8400 processor. I need some help, please and thank you.

---

### Post by Ayuthia on 2008-10-09
> **TheSmokingGNU said:**
> hey, question... I have a dual boot system, running ubuntu and xp home... I am using a neighbor's wireless signal, so i don't know the proper configuration for it. how do i get this thing working?
I have internet when on my windows, and I am using a Belkin Wireless G Desktop card. intel core 2 duo e8400 processor. I need some help, please and thank you.

The first thing that we need to do is identify what the Belkin Wireless card is identified as in Ubuntu.  Can you post the results of (from the Terminal):
```
lspci -nn
```

---

### Post by TheSmokingGNU on 2008-10-09
sure, gimme a couple minutes. lol, every time you ask me for new stuff from the terminal i have to restart my computer

---

### Post by TheSmokingGNU on 2008-10-09
k, sorry. the file i copied it to was an open office file. so i need to get that to view it. this will be a minute. thanks for your patience

---

### Post by TheSmokingGNU on 2008-10-09
alright, this is the output.

darren@darren-desktop:~$ lspci -nn 
00:00.0 Host bridge [0600]: nVidia Corporation Unknown device [10de:07c1] (rev a2) 
00:00.1 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07cb] (rev a2) 
00:01.0 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07cd] (rev a1) 
00:01.1 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07ce] (rev a1) 
00:01.2 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07cf] (rev a1) 
00:01.3 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d0] (rev a1) 
00:01.4 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d1] (rev a1) 
00:01.5 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d2] (rev a1) 
00:01.6 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d3] (rev a1) 
00:02.0 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d6] (rev a1) 
00:03.0 ISA bridge [0601]: nVidia Corporation Unknown device [10de:07d7] (rev a2) 
00:03.1 SMBus [0c05]: nVidia Corporation Unknown device [10de:07d8] (rev a1) 
00:03.2 RAM memory [0500]: nVidia Corporation Unknown device [10de:07d9] (rev a1) 
00:03.3 Co-processor [0b40]: nVidia Corporation Unknown device [10de:07da] (rev a2) 
00:03.4 RAM memory [0500]: nVidia Corporation Unknown device [10de:07c8] (rev a1) 
00:04.0 USB Controller [0c03]: nVidia Corporation GeForce 7100/nForce 630i [10de:07fe] (rev a1) 
00:04.1 USB Controller [0c03]: nVidia Corporation GeForce 7100/nForce 630i [10de:056a] (rev a1) 
00:08.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:056c] (rev a1) 
00:09.0 Audio device [0403]: nVidia Corporation MCP73 High Definition Audio [10de:07fc] (rev a1) 
00:0a.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:056d] (rev a1) 
00:0b.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:056e] (rev a1) 
00:0c.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:056f] (rev a1) 
00:0d.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:056f] (rev a1) 
00:0e.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:07f0] (rev a2) 
00:0f.0 Ethernet controller [0200]: nVidia Corporation MCP73 Ethernet [10de:07dc] (rev a2) 
01:07.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01) 
02:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600 GT] [10de:0140] (rev a2) 
darren@darren-desktop:~$

---

### Post by Ayuthia on 2008-10-09
> **TheSmokingGNU said:**
> alright, this is the output.

darren@darren-desktop:~$ lspci -nn 
01:07.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01) 
Well, here is your wireless card.  Unfortunately, I am not going to be much help in this because I don't have any experience in the Atheros cards.  You will be better off creating a new post with a title that contains something like "Need help installing Atheros AR2413 card".  Sorry I can't be any more help.  It might be helpful to include the following in your post:
```
lspci -nn
lshw -C network
```

---

### Post by TheSmokingGNU on 2008-10-09
thanks so much for the help you did give me though. yay. maybe i can get this thing working after all!! :D

---

### Post by Jive Turkey on 2008-11-15
The file at this url "http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2" gives me errors 
"bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors"
bummer...

---

### Post by Mehrban on 2008-11-23
> **Ayuthia said:**
> Well, here is your wireless card.  Unfortunately, I am not going to be much help in this because I don't have any experience in the Atheros cards.  You will be better off creating a new post with a title that contains something like "Need help installing Atheros AR2413 card".  Sorry I can't be any more help.  It might be helpful to include the following in your post:
```
lspci -nn
lshw -C network
```

hi Dear , I need ur help plz,
have broad com usb 4310
not working, also not installing ndiswrapper please help it is a month i am looking for it

---

### Post by Ayuthia on 2008-11-23
> **Mehrban said:**
> hi Dear , I need ur help plz,
have broad com usb 4310
not working, also not installing ndiswrapper please help it is a month i am looking for it

You can try this link:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
It will explain how to install the wl driver in 8.04.

If you have a wired connection, you can try and get the system updated to the most recent updates and then go to System->Administration->Hardware Drivers and activate the Broadcom STA driver.  If I recall correctly, the driver is not introduced into Hardy until kernel version 2.6.24-17.

The other option is to install 8.10.  The driver comes with the installation.  You just need to go to System->Administration->Hardware Drivers to activate the Broadcom STA driver.

Hope that helps.

---

### Post by colonel_sanderson on 2008-12-04
After following the instructions in the first post, my wireless card is no longer even listed in the hardware. lshw -C network only lists the ethernet card, and lshw doesn't show anything either.  It's as if it never existed.

```

colonel@lappy486:~$ lshw
WARNING: you should run this program as super-user.
lappy486                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1002MiB
     *-cpu
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1596MHz
          capacity: 1596MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 4
                bus info: pci@0000:03:04.0
                logical name: eth0
                version: 10
                serial: 00:40:45:2d:32:e0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.90 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 module=ohci1394
           *-system UNCLAIMED
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.2
                bus info: pci@0000:03:06.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=64
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.3
                bus info: pci@0000:03:06.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

The problem started the day before yesterday. Wireless was working fine, then I upgraded to the latest kernel.  Wireless would connect, but no internet.  I installed ndiswrapper to try the windows driver.  Wireless was then no longer an option.  So I uninstalled ndiswrapper, still nothing.  Found this post and tried it... still no wireless card.

---

### Post by Ayuthia on 2008-12-05
> **colonel_sanderson said:**
> After following the instructions in the first post, my wireless card is no longer even listed in the hardware. lshw -C network only lists the ethernet card, and lshw doesn't show anything either.  It's as if it never existed.

```

colonel@lappy486:~$ lshw
WARNING: you should run this program as super-user.
lappy486                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1002MiB
     *-cpu
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1596MHz
          capacity: 1596MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 4
                bus info: pci@0000:03:04.0
                logical name: eth0
                version: 10
                serial: 00:40:45:2d:32:e0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.90 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 module=ohci1394
           *-system UNCLAIMED
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.2
                bus info: pci@0000:03:06.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=64
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.3
                bus info: pci@0000:03:06.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

The problem started the day before yesterday. Wireless was working fine, then I upgraded to the latest kernel.  Wireless would connect, but no internet.  I installed ndiswrapper to try the windows driver.  Wireless was then no longer an option.  So I uninstalled ndiswrapper, still nothing.  Found this post and tried it... still no wireless card.

If the network card does not show up with lspci also, then it might be a hardware problem.  Are you dual-booting?  If so, can you try and see if the wireless card works on the other OS?

---

### Post by colonel_sanderson on 2008-12-08
```

colonel@lappy486:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
03:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

Yeah, I'm dual booting with Vista.  The wireless card shows up and works fine.

---

