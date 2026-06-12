---
title: "Get Your Wireless Setup to Work"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by pcarreon on 2010-09-11
I am brand new to Ubuntu. After spending several weeks off and on trying to get my wireless adapter working, I finally stumbled on an almost foolproof way to get wireless up and running. I say "almost" because I am not sure it will work in all circumstances and all setups. I am anxious to hear from forum members about their experience using this method. I am using Ubuntu 10.04 FYI.

First of all, you don't need to know anything about Linux or Ubuntu to get your wireless setup running. You do need to have a wireless modem already up, though. This post will only help get your wireless adapter working with your computer. The basic method here is to use an adapter that already has the drivers loaded up as part of the Linux kernel. Otherwise, as a new Ubuntu user, you may be doomed to failure because not all adapters will work with the O/S.

1. First, if you have an existing wireless adapter that you are trying to get working, make sure it is compatible with Linux. Go to this page ([http://linux-wless.passys.nl](http://linux-wless.passys.nl)/) to determine if your adapter is good. You can enter your manufacturer's name in the first text box and press the "Show" button. If your adapter is not found or is listed as Yellow or Red, you are better off abandoning the adapter. Go to step 5. If you do not want to bother with troubleshooting your existing adapter, go to step 5 as well.

2. If your adapter is listed as Green, you are in luck.  If your adapter is listed with the Comments "Driver included in mainline kernels since X.X.XX." you are in even better luck. Search this forum for help using the chipset or driver name(e.g. Ralink or Prism2/2.5/3) since it will usually apply to more than manufacturer. Follow the forum instructions 

3. If the forum help starts getting too complex or requires you to download and compile firmware or driver source code, you are simply better off, as a newcomer to abandon the adapter and go to Step 5.

4. You should be successful at this point. If the forum instructions are of little or no help or too complex, go to Step 5.

5. Remove your old adapter. Buy an adapter that has comments "*Driver included in mainline kernels since X.X.XX*" **and **is currently being manufactured **and **is inexpensive. You can do your own research on "[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl")" or simply use my research. It turns out that the Ralink rt2870sta fits the bill nicely. There are a number of manufacturers who currently use this driver. Search this page ([http://linux-wless.passys.nl/query_chipset.php?chipset=Ralink](http://linux-wless.passys.nl/query_chipset.php?chipset=Ralink)) using "rt2870sta" as a search criteria for a manufacturer of your preference. I used the Tenda W311U available from MicroCenter for $15 ([http://www.microcenter.com/single_product_results.phtml?product_id=0316240](http://www.microcenter.com/single_product_results.phtml?product_id=0316240)). There is a store near me and I went down and bought one from a large bin.

6. It still did not work!!! However a quick search of this forum brought me to this page ([http://ubuntuforums.org/showthread.php?t=1547195&highlight=modprobe+rt2870sta](http://ubuntuforums.org/showthread.php?t=1547195&highlight=modprobe+rt2870sta)). Solution thanks to Dangerouge. I'll repeat here, though to save some time.

Open a terminal window by clicking on Applications-->Accessories-->Terminal. When the window comes up, enter the following commands:

sudo su
echo "rt2870sta" >> /etc/modules
modprobe rt2870sta
exit

Plug in the adapter, restart the machine, and you should be connected. Good luck!

---

### Post by vjg on 2010-09-12
Did this include WPA support?

---

### Post by vjg on 2010-09-13
> **vjg said:**
> Did this include WPA support?

Responding to my own post... the answer appears to be yes. The instructions above were the only steps I needed to get my W311U working on 10.04 with WPA enabled on my router.

---

### Post by cleve298 on 2010-09-13
OK, I'm new to Ubuntu, and I d/L Ubuntu 10.4 for use on an HP TX2500 tablet. 
I have tried without sucess to get the wireless card to work. It has a Broadcom 43XX card in it, How do I get this thing up and running. AGAIN REALLY NEW TO LINUX so go easy on me ....any help would greatly be appreciated. ( I would hate to revert back to Windows) Thanks again

---

### Post by bkratz on 2010-09-13
> **cleve298 said:**
> OK, I'm new to Ubuntu, and I d/L Ubuntu 10.4 for use on an HP TX2500 tablet. 
I have tried without sucess to get the wireless card to work. It has a Broadcom 43XX card in it, How do I get this thing up and running. AGAIN REALLY NEW TO LINUX so go easy on me ....any help would greatly be appreciated. ( I would hate to revert back to Windows) Thanks again

This is really the best page for Broadcom information

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by cleve298 on 2010-09-13
Great Thanks for the link, I wil give this a try..

---

### Post by migs73 on 2010-09-13
> **cleve298 said:**
> OK, I'm new to Ubuntu, and I d/L Ubuntu 10.4 for use on an HP TX2500 tablet. 
I have tried without success to get the wireless card to work. It has a Broadcom 43XX card in it, How do I get this thing up and running. AGAIN REALLY NEW TO LINUX so go easy on me ....any help would greatly be appreciated. ( I would hate to revert back to Windows) Thanks again

Also as a first step I would connect to your network wired and then goto System-->Administration---> Hardware Drivers. The system will then look for drivers and possibly offer you a proprietary one for your wireless card. Then just enable it and you should be good to go. Mine uses the Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware.

Good Luck

---

### Post by rosehipzero on 2010-09-13
I tried that and i could not get it to work =/ I tried it twice thinking i did something wrong... no luck for me

my issue -> [http://ubuntuforums.org/showthread.php?p=9841591#post9841591](http://ubuntuforums.org/showthread.php?p=9841591#post9841591)

Can anyone recommend a good adapter from NewEgg if my problem cant be solved?

---

### Post by cleve298 on 2010-09-13
Hey Thanks for the help, I did that and now I have a blue light on the wireless indicator but still do not know what the next step is.  
Here is what ifconfig -a says

mick@mick-tablet:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:99:6c:0c  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe99:6c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5913550 (5.9 MB)  TX bytes:407210 (407.2 KB)
          Interrupt:28 

eth1      Link encap:Ethernet  HWaddr 00:21:00:35:7f:f3  
          inet6 addr: fe80::221:ff:fe35:7ff3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
Ok, any help would greatly be appreciated

Thanks in advance for any help...

---

### Post by cleve298 on 2010-09-13
Replying to my own post.
 I got it!!! It finally works......

 Many thanks to all that responded, especially mig73 and bkratz 
 I was just about to dump ubuntu and return to the world of windows.

I'm sure that this was an was one, however for those of use that are new to ubuntu and linux . Here is what appeared to work for me

 System-->Administration---> Hardware Drivers. The system will  then look for drivers and possibly offer you a proprietary one for your  wireless card. Then just enable it and you should be good to go. Mine  uses the Broadcom 802.11 Linux STA wireless driver for use with  Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware.

Hope this help somebody else..
Again Many thanks to the FORUM..

---

### Post by migs73 on 2010-09-15
> **cleve298 said:**
> Replying to my own post.

 Many thanks to all that responded, especially mig73 and bkratz 
 I was just about to dump ubuntu and return to the world of windows.



+1 to Ubuntu.
-1 to MS. 
Result  ):P

---

### Post by lkraemer on 2010-09-15
pcarron,
WOW! What an interesting post.  I always assumed that the hardware could
be made to work and didn't give a second thought as to finding the best
fit for Linux etc.

Here is a bit of information that others might find useful for finding
exactly what hardware is currently in their machine, before running out
to purchase more hardware.

This posting should help those of you with XXXX Wifi Hardware that
are Upgrading/Installing Ubuntu.

**1. How do I know what Hardware is currently installed for Wifi?**

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.

Your options that can be used to get the Wifi functional for Broadcom, or another manufacture.  I used Broadcom as an example:

**1. Ndiswrapper and a Windows Driver....example: bcmwl5.inf & sys**
The correct 32/64 Bit drivers must be used to match Ubuntu 32/64 Bit.

**2. Ubuntu B43 Driver and some Firmware that was downloaded/extracted when you enabled the Driver for Broadcom Products.**


**#1 - NDISWRAPPER**
To install the Windows Drivers that are located on your Desktop in a
folder named broadcom (.sys & .inf files):
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```
To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```
Then I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
SKIP to FINISH below.......


**REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

**SKIP to FINISH below.......**


**#2 Use DEFAULT B43 Driver in 10.04**
The Firmware is missing and you just need to have an Ethernet Connection
and ENABLE the B43 Driver, or if you don't have an Ethernet Connection,
you can just copy the Firmware to the proper folders.

Download the Firmware files located at:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
to a USB Flash Drive and copy them to your Desktop, and Extract.
You should have two folders b43 & b43legacy. You will be copying
these folders to /lib/firmware/b43 and /lib/firmware/b43legacy

Here are the commands I used on my old Compaq V5201US, running the
10.04 LiveCD to get it working: (Open a Terminal Window)
```

cd /
cd /lib
cd firmware
pwd
ls
sudo cp -r /home/loginname/Desktop/b43* .
cd b43
ls
cd ..
cd b43legacy
ls
exit

```
Now you just have to Enable the B43 Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a B43 Driver listed a driver listed for your wireless,
if so enable it. (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.
It should find the drivers and load them, because the Firmware is where
it needs to be.

Check Network Manager (right click on the icon) to be sure the "Enable Wireless" box is checked (It should be ENABLED already by default.)

Check to see if you have wireless now. If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```

You can check for errors with:
```

dmesg tail

```
You may have to remove other modules depending on what lsmod shows:.... ..
What you will REMOVE depends on what you post as output from your commands.

If lsmod shows module bcm43xx and other conflicts installed you will
need to blacklist them, since you are going to be using B43.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r ndiswrapper

```
You can use sudo nano /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

**FINISH:**
Click on the Wifi Icon in the top right toolbar and select the Network.

**Manual Choice:**
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink"

Maybe this will be some help.

lk

---

