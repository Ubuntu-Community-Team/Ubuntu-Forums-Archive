---
title: "Belkin F5D7050 version 4000 USB wireless card"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by pate4ever on 2006-09-06
Hello everyone I am new at this. I have been reading for hours and hours about this problem and I wanted to make a post about it. I received the Belkin F5D750 version 4000 wireless USB for free and I am trying to make it work on Dapper. After hours of reading I came to the realization that I have to get drivers specifically for the version you are using.

I have used: 
sudo ndiswrapper -i rt73.inf

In order to install the drivers for version 3. This method works for a version 4000 card, kinda. It says that my hardware and drivers are recognized, but i when i use iwconfig I do not find any wireless connections.
the drivers for F5D750 version 3000 are here: [http://www.planetamd64.com/index.php?act=Attach&type=post&id=4193]("http://www.planetamd64.com/index.php?act=Attach&type=post&id=4193")

In order to correct this I have tried, to no avail to use the VERSION 4000  drivers from the disk. There is one problem ... these drivers have no .ini extension so I don't think ndiswrapper recognizes them as drivers.
The files are 
BLKWGU.CAT
BLKWGU2K.sys
BLKWGU9X.sys
Driver.2k
Driver.98
Driver.ME

they can be downloaded from belkin's website, remember: version 4000 drivers
[http://www.belkin.com/support/download.asp?lang=1&download=F5D7050&mode]("http://www.belkin.com/support/download.asp?lang=1&download=F5D7050&mode")



So the big question is it possible to install a Belkin F5D7050 version 
4000 driver or do can I configure the drivers from version 3000 to work 
for me? Or, is it impossible to even use this version 4000 adapter?

Please help,
pate4ever

---

### Post by Layman's terms on 2006-09-27
Hey, pate4ever,

I'm also brand new to Ubuntu and have a Belkin F5D7050 v4000, and I've been doing some research of my own on the subject.


Ndiswrapper has a list of all the wireless hardware that it supports on its sourceforge wiki ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List))

To save you some time, I've listed the Belkin F5D7050 devices that appear on that list below.

> Card: Belkin F5D7050 (USB 2.0 Adaptor 802.11g 54Mbps) 
     Chipset: Conexant (PrismUSB) 
     usbid: 050D:7050 
     Driver: Install the drivers for windows included in the box and fetch the .inf and .sys fyles from the installation directory. 
     Other: linux-2.6.9: Blocks Linux momentarily when another device is plugged into the same USB Hub, more precisely a 1.1 memory stick. 
     Other: SuSE 9.1, kernel-2.6.8-default (kernel-of-the-day 22 Dec. 2004): 1.0rc1 with bknUSB.inf from the vendor CD and WEP security works quite stable. The procedure as described in WiKi/SuSE 9.1. Professional. 
     Other: SuSE 9.1, kernel-2.6.x-smp: doesn't work, 'modprobe ndiswrapper' freezes the system. 

Card: Belkin F5D7050 (USB 2.0 Adaptor 802.11g 54Mbps) 
     Chipset: RT2500 
     usbid: 050d:7050 
     Driver: Install the drivers for windows included in the box and fetch the .inf files from the installation directory. 
     Other: Works fine. When entering in resume mode, freeze the system. 

Card: Belkin F5D7050B (USB 2.0 Adaptor 802.11b/g 54Mbps) ("version 3000uk" only tested at this time) 
     Chipset: RT73 
     usbid: 050d:705A 
     Driver: Install the drivers for windows included in the box and fetch the .inf files from the installation directory. 
     Other: Works fine with WPA(PSK-TKIP) using wpa_supplicant on ubuntu 6.06 with ndiswrapper driver. Will freeze the system if removed without ifdown and/or ifconfig down on the device, and even then sometimes. Even though WPA works, I have not yet managed to succeed in using with WEP! 

Card: Belkin F5D7050E (USB 2.0 Adaptor 802.11g 54Mbps) 
     Chipset: Accton Technology Corp. 
     usbid: 083a:f503 
     Driver: Install the drivers for windows included in the box and fetch the .inf files from the installation directory. 
     Other: Suse 10.1, kernel 2.6.16.13-4-default, ndiswrapper 1.20rc1 
     Other: Works fine. Stops working from time to time requiring an unplug-replug.

My other research shows that the F5D7050 v4000 does not correspond to any of the devices above. The internal chipset of the v4000 is the zd1211b chipset from Zydas. I could be wrong, but I would interpret this to mean that the v4000 will not work with the current version of ndiswrapper. (But hey, I'm a newbie, so what do I know? 8) )


All hope is not lost, however, because there is an open source community at [http://zd1211.ath.cx/](http://zd1211.ath.cx/) that is devoted to creating a native Linux driver for zd1211 and zd1211b. They **do** list the Belkin F5D7050 v4000 as supported hardware, but this is where I run into problems. I installed the driver they have and am proud to say that I can now see the Belkin device in Network Manager listed as wlan0. But I still can't connect. I am able to see the surrounding networks using

```
sudo iwlist wlan0 scan
```

but DHCP isn't working so I never get assigned an IP address to my adapter (and thus can't connect to the Internet).

If you get this driver installed and manage to have success connecting to your network, please let me know what you did to resolve any problems.

---

### Post by blackest_knight on 2006-10-26
yes it is the zydas chip set and you can compile a driver for it the version 2 and version 3 used ralink (a lot easier to get going) I have version 1 and nobodys saying :( if i remember correctly the zydas source needs a small modification to take care of the b in the chipset version. 
in other words keep looking you may be successful

---

### Post by werdna5225 on 2006-11-03
How do you install the windows cd to your linux??? Is that what I'm supposed to do?

---

### Post by dracule on 2006-11-25
you download the linux zydas drivers, and just compile them, simple as that. worked for me. what is strange is that the very detailed and helpful guid that I used, is no longer up...

---

### Post by FrodoB on 2006-11-25
Guide:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by st_judas on 2006-12-04
> **Layman's terms said:**
> Hey, pate4ever,

I'm also brand new to Ubuntu and have a Belkin F5D7050 v4000, and I've been doing some research of my own on the subject.


Ndiswrapper has a list of all the wireless hardware that it supports on its sourceforge wiki ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List))

To save you some time, I've listed the Belkin F5D7050 devices that appear on that list below.



My other research shows that the F5D7050 v4000 does not correspond to any of the devices above. The internal chipset of the v4000 is the zd1211b chipset from Zydas. I could be wrong, but I would interpret this to mean that the v4000 will not work with the current version of ndiswrapper. (But hey, I'm a newbie, so what do I know? 8) )


All hope is not lost, however, because there is an open source community at [http://zd1211.ath.cx/](http://zd1211.ath.cx/) that is devoted to creating a native Linux driver for zd1211 and zd1211b. They **do** list the Belkin F5D7050 v4000 as supported hardware, but this is where I run into problems. I installed the driver they have and am proud to say that I can now see the Belkin device in Network Manager listed as wlan0. But I still can't connect. I am able to see the surrounding networks using

```
sudo iwlist wlan0 scan
```

but DHCP isn't working so I never get assigned an IP address to my adapter (and thus can't connect to the Internet).

If you get this driver installed and manage to have success connecting to your network, please let me know what you did to resolve any problems.



First unplug your USB adapter.

Download the driver:
[http://zd1211.ath.cx/](http://zd1211.ath.cx/)
( currently: [http://zd1211.ath.cx/download/zd1211-driver-r83.tgz](http://zd1211.ath.cx/download/zd1211-driver-r83.tgz) )

Then just follow this:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))

The way to get it working is to build it with the ZD1211_B=1 flag.  You have to use "make ZD1211_B=1" when you build the driver.  Don't use the "make both" command that they show in the guide, that will build both versions and take longer. You just need the ZD1211_B version.

Then reboot.  I used KWifiManager, but iwconfig should work just as well for those of you who shun the GUI.

---

### Post by Jocka on 2006-12-12
I'm having a few problems with this thing myself. I'm getting tempted to just run a 100 foot cable across the building lol.

I've done everything in every tutorial and can't get this working. I ALMOST had this going and ran into this error:
```

src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.15-23-amd64-generic/build SUBDIRS=/home/jocka/zddrivers/zd1211-driver-r83 modules
make: *** /lib/modules/2.6.15-23-amd64-generic/build: No such file or directory. Stop.
make: *** [all] Error 2
jocka@gtwasupport:~/zddrivers/zd1211-driver-r83$

```

I did a search on google after I saw this and something came up saying it needed linux-headers but those are installed. If someone tells me i still need them then i'll try to search them out again.

Please help. My boss is going to kill me if I don't get this online by tomorrow lol.

---

### Post by FrodoB on 2006-12-12
See the link in post #6, you are missing a link from modules directory to the headers.

---

### Post by Jocka on 2006-12-12
so do I need to reinstall the linux-headers ? I installed those from the Ubuntu cd, since I don't have the internet on the Ubuntu side to download.

I'm going to download the latest version with all dependencies right now and see if I can't get it to work. Unless I'm on the wrong track, then please let me know.

---

### Post by FrodoB on 2006-12-12
If you already have the headers you do not need to download them again. If you need them insert the install CD and in a few seconds you should be asked if you want to open the package manage, say yes and then install them.

Otherwise you seem to be missing this part:

sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

Just copy and paste that line into a terminal, do not change anything. if you have to type this the backquotes ` they are on the same key as tilde ~ right under the Esc key.

Then you can continue with the make command, etc.

---

### Post by Jocka on 2006-12-12
```

jocka@gtwasupport:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
Password:
ln: creating symbolic link `/lib/modules/2.6.15-23-amd64-generic/build' to `/usr/src/linux-headers-2.6.15-23-amd64-generic': File exists

```
Put it in and got that. I'm so utterly and completely lost right now. I've tried everything I could think of.

---

### Post by Jocka on 2006-12-12
big *BUMP*

I've about decided to run the cable.. .. i really don't want to do that though. :-?

---

### Post by FrodoB on 2006-12-12
This is happening at make correct? If so publish the whole thing from make to this.

---

### Post by Jocka on 2006-12-12
```

jocka@gtwasupport:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
Password:
ln: creating symbolic link `/lib/modules/2.6.15-23-amd64-generic/build' to `/usr/src/linux-headers-2.6.15-23-amd64-generic': File exists
jocka@gtwasupport:~$ cd zddrivers
jocka@gtwasupport:~/zddrivers$ dir
zd1211-driver-r83
jocka@gtwasupport:~/zddrivers$ cd zd1211-driver-r83
jocka@gtwasupport:~/zddrivers/zd1211-driver-r83$ sudo make both
make ZD1211REV_B=0
make[1]: Entering directory `/home/jocka/zddrivers/zd1211-driver-r83'
/lib/modules/2.6.15-23-amd64-generic/build
/home/jocka/zddrivers/zd1211-driver-r83
-I/home/jocka/zddrivers/zd1211-driver-r83/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.15-23-amd64-generic/build SUBDIRS=/home/jocka/zddrivers/zd1211-driver-r83 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-23-amd64-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jocka/zddrivers/zd1211-driver-r83'
make: *** [both] Error 2

```

---

### Post by FrodoB on 2006-12-12
You are trying to use 64bit Ubuntu,  correct? I doubt that that is going to work.

---

### Post by Jocka on 2006-12-12
alright so this is what i have accomplished.

I went back into Ubuntu to give it another shot. I then thought to myself "what if a package is broken" and sure enough the linux-header package was. So I fixed and and got the stuff installed.. and thats where it stops.

I go to set up the wireless connection now and it acts weird. I can get signals, it shows me the signals from around me (there 3 and it shows all 3) yet it won't let me connect to any of them. When I put in the information for our signal which requires a key, my usb adaptors light goes off. About 2 minutes later it'll come back on and i'm still not connected. Why would it do that?

---

### Post by FrodoB on 2006-12-12
You need to be cutting and pasting the results that you see to the forum, it is hard to say what you have there without seeing the results.

Also check your /etc/network/interfaces file:

Using the Text Editor (gedit) we need to modify the interfaces file to get the device started correctly:

sudo gedit /etc/network/interfaces 


Make sure that is a record like this and that the WEP key and ESSID name are correct.

auto wlan0
iface wlan0 inet dhcp
wireless-essid My Essid Name
wireless-key XXXXXXXXXXXXXXXXXXXXXXX

Also what step are you at in the instructions?

---

### Post by Jocka on 2006-12-12
It's not showing me anything. I know it makes it easier to see whats going on but I'm not seeing anything either.

I fixed the file like you said to and it 'appears' to connect. I went to network tools and it shows that i'm getting packets but it won't let me do anything. I'm still offline.

If I had something to show you, believe me I would. I want this fixed as bad as you want to choke me for not giving you anything to work with.

---

### Post by FrodoB on 2006-12-12
Supply the outputs of:

iwconfig

lsusb

Remove the device, plug it back in and then get the part of the dmesg output that shows the initialization of the device.

---

### Post by Jocka on 2006-12-14
sorry it took so long to reply. I had to leave work and been sick. Still hoping for answers though lol.
```
gotoworkamerica@gtwasupport:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"2WIRE146"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:95:EE:7A:39
          Bit Rate:54 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=56/100  Signal level=47/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2658  Invalid misc:0   Missed beacon:0

gotoworkamerica@gtwasupport:~$ lsusb

Bus 002 Device 003: ID 050d:705c Belkin Components
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

gotoworkamerica@gtwasupport:~$ dmesg

[   84.509839] zd1205: (exit) zd1205_config, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 2601
[   84.509889] zd1205: (exit) zd1205_init, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 8570
[   84.600371] keybuf data [5]:
[   84.600522] 05 20 24 20 34
[   84.600879] zd1211:WEP64 Mode
[   84.606208] Update CardSetting
[   84.626184] zd1205: (enter) zd1205_open, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 4353
[   84.634875] zd1205: (exit) zd1205_open, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 4436
[   84.635239] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.064884] zd1211:Mixed Mode
[   85.085773] zd1211:STA_ASSOCIATED with 00:14:95:ee:7a:39
[   85.085947] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   89.811110] wlan0: no IPv6 routers present

```

---

### Post by FrodoB on 2006-12-14
iwconfig seems to indicate that you are connected.

---

### Post by Jocka on 2006-12-14
> **FrodoB said:**
> iwconfig seems to indicate that you are connected.
I know. Thats what I was saying in that other post. It seems to be 'connected' but it won't let me online. I tried using firefox, gaim, the network tools, etc. Nothing would work.

---

### Post by FrodoB on 2006-12-14
Search the forum for WG111v2. There is a post where I gave my router settings and it helped.  It may be as simple as changing WEP type, etc.

---

### Post by Jocka on 2006-12-14
Alright. I'll see what I can find/do. Hopefully I'll get lucky and finally get it online. ](*,)

---

### Post by Jocka on 2006-12-14
I don't know how to change the WEP encryption (I wanted to give that a shot). I tried switching between hex and plain but that did nothing. So I'm thinking maybe if I could change the encryption then I could get something working. How do I go about doing that?

---

### Post by FrodoB on 2006-12-14
You can create keys at:
[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Using the Text Editor (gedit) we need to modify the interfaces file to get the device started correctly:
sudo gedit /etc/network/interfaces 
Dynamic Address Assignment using DHCP: Add this data at the end of the file for a DHCP setup: (Choose one key type, either hex or ASCII, but not both, uncomment one, and fill in your key.)

iface wlan0 inet dhcp
wireless-essid MY_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX # This line for ASCII (string) keys
auto wlan0
Set the WEP keys as in the above examples. Hexidecimal format is preferred, but there is an example for ASCII keys which must preceded by s:
Save the file.
use ifdown and ifup to control the device:
sudo ifdown wlan0
sudo ifup wlan0

---

### Post by Jocka on 2006-12-14
I did just what you said and nothing. I also installed "wifi-radar" and it shows that it's connected too but i can't do anything.

Heres a list of all the info you may need :P.
```

IWCONFIG:
----------------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"2WIRE146"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:95:EE:7A:39
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=24/100  Signal level=53/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:7
          Tx excessive retries:23110  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

--------------------------------------------------

IFCONFIG:

--------------------------------------------------

eth0      Link encap:Ethernet  HWaddr 00:18:F3:95:56:64
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1483 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:111980 (109.3 KiB)  TX bytes:111980 (109.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:B3:88:EF
          inet6 addr: fe80::211:50ff:feb3:88ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:7 dropped:0 overruns:0 frame:7
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:21384 (20.8 KiB)

----------------------------------------------------

DMESG (my many attempts at trying to get online):

-----------------------------------------------------
[  383.602555] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  388.365802] wlan0: no IPv6 routers present
[  453.954307] zd1205: (enter) zd1205_close, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 4896
[  453.957930] zd1205: (exit) zd1205_close, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 4962
[  453.964020] keybuf data [0]:
[  453.964157]
[  453.964211] Just Update WEP key
[  454.002892] keybuf data [10]:
[  454.003029] 30 35 32 30 32 34 32 30 33 34
[  454.003201] zd1211:WEP128 Mode
[  484.233532] Update CardSetting
[  484.253591] zd1205: (enter) zd1205_open, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 4353
[  484.253882] zd1205: (exit) zd1205_open, /home/gotoworkamerica/zddrivers/zd1211-driver-r83/src/zd1205.c line 4436
[  484.254241] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  484.264534] zd1211:Mixed Mode
[  484.509733] zd1211:Mixed Mode
[  484.764014] zd1211:Mixed Mode
[  485.018295] zd1211:Mixed Mode
[  485.272576] zd1211:Mixed Mode
[  485.526857] zd1211:Mixed Mode
[  485.781137] zd1211:Mixed Mode
[  487.452127] zd1211:Mixed Mode
[  487.468590] zd1211:STA_ASSOCIATED with 00:14:95:ee:7a:39
[  487.468767] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  492.333230] wlan0: no IPv6 routers present
[  574.225979] zd1211:STA_DEAUTHED:00:14:95:ee:7a:39
[  574.666822] zd1211:Mixed Mode
[  574.922578] zd1211:Mixed Mode
[  574.952039] zd1211:STA_ASSOCIATED with 00:14:95:ee:7a:39
[  660.719154] zd1211:STA_DEAUTHED:00:14:95:ee:7a:39
[  661.150124] zd1211:Mixed Mode
[  661.170446] zd1211:STA_ASSOCIATED with 00:14:95:ee:7a:39
[  745.280175] zd1211:STA_DEAUTHED:00:14:95:ee:7a:39
[  745.777893] zd1211:Mixed Mode
[  745.804630] zd1211:STA_ASSOCIATED with 00:14:95:ee:7a:39
[ 1048.747858] zd1211:STA_DEAUTHED:00:14:95:ee:7a:39
[ 1049.201986] zd1211:Mixed Mode
[ 1049.227359] zd1211:STA_ASSOCIATED with 00:14:95:ee:7a:39
[ 1049.227364] zd1211:Notify_join_event:00:14:95:ee:7a:39

-----------------------------------------------------

LSUSB:

-----------------------------------------------------
Bus 002 Device 002: ID 050d:705c Belkin Components
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

---

### Post by FrodoB on 2006-12-14
You need to start looking at your router access point it would seem.

---

### Post by Jocka on 2006-12-14
Is it possible that my router could NOT allow ubuntu on the same computer that it DOES allow windows?

---

### Post by FrodoB on 2006-12-14
No it should be nothing like that. What kind of router do you have?

---

### Post by Jocka on 2006-12-14
2wire. Not sure what version or none of that but I can check it out if you think it'll help.

---

### Post by FrodoB on 2006-12-14
See my router settings in post #12 of this thread. Using these settings has worked for at least two folks who are having connection problems:

[ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip]("ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip")

Sorry, wrong thread:

[http://www.ubuntuforums.org/showthread.php?t=313349&highlight=WG111V2](http://www.ubuntuforums.org/showthread.php?t=313349&highlight=WG111V2)

---

### Post by Jocka on 2006-12-14
this is a windows program for drivers or something.. what am I supposed to do with it?

BTW, someone told me my IP wasn't right. That it was in IPv6 or something.. is this a problem?

---

### Post by FrodoB on 2006-12-14
Sorry posted to wrong thread. Check your wireless router settings against these:
My ViewSonic WAPR-100 Wireless Access Point Settings: (Linksys WRT54GL differences noted)


Authentication Type: Open System

Basic Rate: All  (Linksys only)
      
Transmission Rates: Auto (All for my Linksys)

Frame Burst: Disable  (Only on my Linksys)

RTS/CTS: Disable 

CTS Protection Mode : Disable (Linksys only)

Beacon Interval: 100 ms

RTS Threshold: 2346

Fragmentation Threshold: 2346 (2347 on my Linksys)

DTIM Interval: 3

Xpress mode: Disable   (Maybe this is the same as preamble on this router?)

Access Control: Disable

Wireless Mode 802.11b 11Mbps

Channel: 11

SSID Broadcast: Disable  (You could try enabling this to see if their is any difference.)

SecureEasySetup : Disable    (Linksys only)
 		 
Preamble:  Long

---

### Post by Layman's terms on 2006-12-17
> 
Guide:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29](https://help.ubuntu.com/community/Wi...cs%2FDevice%29)


FrodoB, I had renewed hope for surfing the Net with my Ubuntu partition when I noticed all the new posts to this thread, but I followed the installation tutorial and I still could not connect to the Internet.

I think my main problem is coming from Step 7 (Configuring the network settings). My setup is simple. I have an ESSID called "wireless," I'm not connecting to a secure network so there is no need for WEP settings, and I want to use DHCP. So after enabling my wlan0 and setting the ESSID to "wireless" in the properties dialog, I should have been set to run. However, when I ran iwconfig again, I noticed that the Access Point parameter said "Not-Associated."

I also observed that in the dmesg output I would get a line like:

```
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Following by many messages stating:

```
zd1211: Pure B-Mode
```

Do you have any thoughts on what might be the problem? I got no errors when I was building the module so I don't know why it won't associate with the router (by the way, iwlist wlan0 scan will show everything in the area so I know that the adapter is at least working to some degree).

Thanks.

---

### Post by chronographer on 2006-12-17
Hi all

I am having similar problems as above, where ubuntu seems to recognise the usb wireless card (fsd7050)  but wont connect properly.  I have scanned for wireless networks and my network (valance) and next doors show up, but i have manually added the network ID and the wep key to no avail...

DHCP wont assign me an ip...  I manually entered an ip etc. couldn't ping router or access its settings page...

I tried using ndiswrapper but this didn't help at all, so i removed it. 

One thing I notice I have is my wireless card shows up two things in the networking window..
the usual wlan0 and also wmaster0  What does this mean?

This is a fresh install of Ubuntu, I also have a partition with a clean install of xp, which I would prefer not to use as I am determined to migrate to open source, rather than the pirated software I am used to!

This message is being written on my laptop which is communicating to the router wirelessly and well, so its not a router problem and my desktop running xp (which i just reformetted) used the belkin card before, so the hardware should be able to work.....


Thanks in advance for any help! :-k

---

### Post by garlicsalt2 on 2006-12-20
Hello, I am considering buying one of these devices, as it has many features under both Linux AND Windows, and wanted to see if anyone had any problems with this device that I should know about.

I have a few ideas as to how to help with this, but I can't test them myself.

First possibility: loaded modules in memory may be old/stale. Solution: Restart system.

Second possibility: "Make" may not work correctly with USB device plugged in. Solution: unplug USB device; reboot; Try to "make clean" (to start with a fresh build environment); "make"; "make install"; reboot again, just to be sure; Insert USB dongle.

Note that commands "make clean" and "make install" are the usual commands for making any given app from source. The actual commands you need to use might be different for this program. You only need to "make clean" if you have a failed build, and need to recompile. Check the directions or README file to be certain.

Third possibility: Mismatch in wireless encryption settings. Solution: Hop onto an XP machine connected wirelessly to the desired AP, and right-click the Wi-Fi icon tn the system tray and select "View available wireless networks". Then select "change the order of preferred networks". Lastly, double-click on your network name. You should be on the "Association" tab. DO NOT CHANGE ANYTHING, just post the following information: "Network Authentication", and "Data encryption" Tell me to what those are set. Also, if "Key Index (Advanced)" is NOT set to the value of "1", then post that number as well. If all else fails, check the Linux Zydas User Manual, here:

[Linux_zd1211_UserGuide.doc]("http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211_USB/Linux/Linux_zd1211_UserGuide.doc")

---

### Post by garlicsalt2 on 2006-12-20
#Layman's Terms: FYI, "Pure B mode" means that the device is operating at Wireless B speed (11 MB/s). Either you are plugging your Belkin USB Dongle into a USB 1.1 port rather than a 2.0 port, or you are using a 2.0 port, but you don't have the ehci-hcd module loaded for USB 2.0 support. Check that your USB dongle is plugged into a USB 2.0 port. If it is not, then you will be unable to achieve 54mbps speed.

#Everybody: do a search in this forum for other products with the Zydas chipset, to see if other people have had and/or solved these problems. (hint: do a search for the word "zydas").

---

### Post by Layman's terms on 2006-12-21
Garlicsalt2, thanks for the tip about the Pure B mode. I thought it had to do something with using the zd1211b module but I guess I was wrong. When I followed FrodoB's guide, I neglected to run make clean (and the previous build of the modules was with the adapter plugged into a 1.1 port).

I'll try rebuilding the modules without the adapter plugged in (like I did a couple of days ago) but I'll make sure to make clean first, then I'll reboot and plug the adapter into a 2.0 port.

Thanks again. I'll post again with the results of my attempt when I get home after work.

---

### Post by Layman's terms on 2006-12-21
Well... it didn't work. :( 

For your viewing pleasure, I've posted the portion of dmesg that pertains to the device. This time around, I did make clean, make both, then I plugged in the adapter to a USB 2.0 port.

```

[17179664.452000] NET: Registered protocol family 10
[17179664.452000] lo: Disabled Privacy Extensions
[17179664.452000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179664.452000] IPv6 over IPv4 tunneling driver
[17179873.576000] usb 2-1: new high speed USB device using ehci_hcd and address 2
[17179873.724000] usb 2-1: configuration #1 chosen from 1 choice
[17179873.820000] ZD1211B - http://zd1211.ath.cx/ - r83
[17179873.820000] Based on www.zydas.com.tw driver version 2.5.0.0
[17179873.940000] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[17179874.092000] Release Ver = 4810
[17179874.092000] zd1211:bulk out: wMaxPacketSize = 200
[17179874.092000] zd1211:bulk in: wMaxPacketSize = 200
[17179874.092000] zd1211:interrupt in: wMaxPacketSize = 40
[17179874.092000] zd1211:interrupt in: int_interval = 1
[17179874.092000] zd1211:interrupt out: wMaxPacketSize = 40
[17179874.092000] EEPORM Ver = 4810
[17179874.100000] zd1211:USB Download Boot code success
[17179874.112000] zd1211:MAC address = 00:11:50:b2:cf:71
[17179874.120000] zd1211:AddrEntryTable = f7c6
[17179874.128000] zd1211:RF_Mode = 80000504
[17179874.128000] PA type: 0
[17179874.128000] AiroHa AL2230RF
[17179874.132000] zd1211:Mixed Mode
[17179874.172000] zd1211:AllowedChannel = 000007ff
[17179874.180000] zd1211:LinkLEDn = 200
[17179874.188000] AllowedChannel = 000107ff
[17179874.188000] Region:16
[17179874.996000] zd1205: (exit) zd1205_config, /home/matt/zd1211-driver-r83/src/zd1205.c line 2601
[17179875.000000] zd1205: (exit) zd1205_init, /home/matt/zd1211-driver-r83/src/zd1205.c line 8570
[17179875.000000] usbcore: registered new driver zd1211b
[17179875.104000] zd1205: (enter) zd1205_open, /home/matt/zd1211-driver-r83/src/zd1205.c line 4353
[17179875.212000] zd1205: (exit) zd1205_open, /home/matt/zd1211-driver-r83/src/zd1205.c line 4436
[17179875.212000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179877.216000] zd1211:Mixed Mode
[17179877.936000] zd1211:Mixed Mode
[17179878.644000] zd1211:Mixed Mode

```

I searched for zydas as garlicsalt2 recommended and noticed that in an alternate tutorial, the author mucks arounds with the make file. Was this editing necessary for success?

My guess is that something fishy is going on in those lines of code in the zd1205.c file. None of the other tutorials show those lines when they print info about the dmesg output.

Thanks in advance for any input that people can offer me. As soon as I can get a connection to the net in Ubuntu, I'll probably migrate there permanently (I currently have to jump into my XP partition to get on the Internet which is quite a hassle).

---

### Post by garlicsalt2 on 2007-03-17
Sorry, I've been busy lately. I've kinda let the Ubuntu forums slip by me.

For anyone who is brave, and has enough ram, they can try Qemu under Windows. It is an emulator that lets you simulate another PC from within Windows. Yes, there is a Linux port, as well as OSX, *BSD, etc.

Why do I bring this up?? Because if you boot Ubuntu under Qemu from within Windows, you should have Virtual Network Interface that Ubuntu will see as a Physical interface.

Yes, Microsoft has released Virtual PC to the public for free, but then you have to create a Virtual Hard Disk on your Physical Hard Drive and install Ubuntu onto it. If you want to use your pre-existing Ubuntu partition, you will need to be able to "See" the partition under Windows. Try:
[http://win2fs.sourceforge.net/]("http://win2fs.sourceforge.net/")

Then get Qemu for Windows at:
[http://www.h7.dion.ne.jp/~qemu-win/](http://www.h7.dion.ne.jp/~qemu-win/)

Read the documentation, then see if you can get online with Ubuntu and try those things which you cannot try under Ubuntu due to no Internet.

#Laymans Terms: Make sure that you only have loaded the modules for your exact chipset. There two different chipsets. There is the one without the 'b' suffix, and the one with the 'b' suffix. If you do a "make both", then make sure you don't have both types of modules loaded.

If in doubt, post the output of the 'lsmod' command, and maybe someone can tell you if there is something unusual.

I seem to recall reading somewhere, that some kind of USB "signature" needs to be compiled into one of the source code files. Do a lsusb, and then note the 4 hex digits, a colon, and four more hex digits, and write them down. That exact sequence should be listed in one of the source files - either a '.c' file or a '.h' file. I could be completely off, so do some research on this.

#Cronographer: I am just guessing here, but wmaster0 might be the built-in ability to be a "Master" a.k.a. Access Point. If you are trying to connect to a Router or Access Point, then this shouldn't be used.

Here is a simple test, albeit a little involved one, to test the basic connectivity of your USB Adapter.

Get two different PCs (Desktop or Notebook) set them both for a static IP address on the same subnet. Set the SSID or ESSID to something unique, such as "Test" or anything that is not used in your area. Set both to use the same channel, and use Ad-Hoc Mode. No encryption. Use unique IP addresses, but make sure that they are in the same subnet, like 192.168.1.1, and 192.168.1.2 - netmask of 255.255.255.0 . No DHCP, no default gateway, no DNS.

Then, try to ping each other. If this works, then the card and driver are working just fine. If it doesn't work, bring one of the interfaces down for a few seconds, and then back up. I'm going to assume that everyone knows how to do the steps mentioned above.

Oh, yeah. A "2wire" access point is used by SBC/AT&T DSL Customers. Note that there is a difference between WEP encryption, and WPA encryption. To get started under Linux, BE SURE TO USE WEP, NOT WPA!!

Although WPA encryption is much more secure, Linux doesn't have built-in support for it - you need the wpa-supplicant package to use it. Even then, there is a configuration file you need to configure. (Hmm, you need to configure the configuration - I need to get some more sleep...) :p

I hope some of this long winded explanation helps!!

--Aaron

---

### Post by kennedy4260 on 2007-04-07
I just wanted to upload this image that I put together from some other sites to help people find out there version.

[ATTACH]29172[/ATTACH]

---

### Post by emergingtechnologies on 2007-07-31
Why do I receive an index.html file when I enter the following:

wget [http://zd1211.ath.cx/download/zd1211-driver-r83.tgz](http://zd1211.ath.cx/download/zd1211-driver-r83.tgz) 

Thanks,
Chris

---

### Post by emergingtechnologies on 2007-07-31
> **kennedy4260 said:**
> I just wanted to upload this image that I put together from some other sites to help people find out there version.

[ATTACH]29172[/ATTACH]


Wow -- that was super useful.  I´m the Ralink.  Is there a different driver I should look for now that I know this?

---

### Post by bwingbob on 2007-08-26
Just want to keep this post up to date. I have a brand new Belkin F5D7050 version 4000 USB wireless card and it works out of the box with the current version of Ubuntu 7.04 and xubuntu. I have tested with 128bit wep and mac filtering on both versions of Ubuntu.

---

### Post by garlicsalt2 on 2007-09-13
> **emergingtechnologies said:**
> Why do I receive an index.html file when I enter the following:

wget [http://zd1211.ath.cx/download/zd1211-driver-r83.tgz](http://zd1211.ath.cx/download/zd1211-driver-r83.tgz) 

Thanks,
Chris

Probably because the file is no longer there, the html file you get is intended to be opened in a web browser, which would then be redirected to the new site at sourceforge.net

Try instead:
```
svn export https://zd1211.svn.sourceforge.net/svnroot/zd1211/trunk zd1211
```

edit: Fixed spelling mistake.

---

### Post by garlicsalt2 on 2007-09-13
> **bwingbob said:**
> Just want to keep this post up to date. I have a brand new Belkin F5D7050 version 4000 USB wireless card and it works out of the box with the current version of Ubuntu 7.04 and xubuntu. I have tested with 128bit wep and mac filtering on both versions of Ubuntu.

Yup, and most of us know about this. Thanks for the update. This driver works great for most standard tasks. Personally, I like the other driver from sourceforge. That driver supports AP (Master) mode. Currently the included driver doesn't.

Oh, by the way, if anyone dual-boots with Windows, and wants it, I have the drivers for this chipset that supports AP mode - via the included utility - which supports both client mode and Access Point mode under Windows.

I actually have a WiFiMax, but inside, it's the same as the Belkin v.4

---

### Post by garlicsalt2 on 2007-09-13
Hey LaymansTerms, did you ever get this thing working?
I haven't yet. It runs fine in Window XP, and everything SEEMS okay under my Kubuntu Fiesty, but I can't get AP Mode working, nor can I get an IP address when in station mode. I don't boot this PC into Linux too much, but I'll keep trying.

If it helps, try setting the region code from within Linux, with ```
 iwpriv wlan0 set_Region **X**
```, where X is the region code. For the US, (and Canada??), this code is **1**.

All that this does is change the selection channels available to you. In the US and Canada, we get 1-11. Other countries allow 1-13, or some limit to 9-13 or something. Find out the region code, and set it before you bring up the interface. It may not be essential, but the FCC requires we set this correctly. If one is careful, one might get by without it. Since you and I are still trying to get this up and running, I think it is better to be safe than sorry.

--Aaron

---

### Post by garlicsalt2 on 2007-09-13
All, right, me again. This time, I've rebooted into kubuntu, AND IT IS WORKING.

Two things to try:
1) Blacklist the zd1211rw module.
2) set the region code, as I mentioned above.

I am using WPA1 at home with TKIP encryption. Oddly, it doesn't work if I configure wpa_supplicant from within /etc/network/interfaces. Instead, I must run wpa_supplicant manually with a config file in place, and then ifup the device. Be certain to do this as root.

---

### Post by Layman's terms on 2007-10-18
garlicsalt2, I never managed to get it working.

But between then and now, I moved to a new apartment, bought a router (I was *borrowing* Internet service from a neighbor), and plugged an ethernet cable directly into my desktop. So I actually haven't tried to get the thing working since Edgy Eft.

But thanks for the tips, hopefully your information will be useful for somebody. Or maybe, even better, it will work for Gutsy out of the box.

---

