---
title: "WPA2 - Broadcom 4306 - B43 Module versus Ndiswrapper - Intrepid Ibex Comparison"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by kevdog on 2008-11-21
I just wanted to pass along some clarifications that I discovered today while playing around with the new Ibex installation.

Currently there seems to exist a problem with using WPA2 wireless authentication.  I've found the following with my setup:

Kernel Version (Default Intrepid Ibex Installation):
```
$ uname -r
2.6.27-7-generic
```

Wireless Device: Linksys WPC54GS, Chipset Broadcom 4306 (Rev 03)
```
$ lspci -nn | grep Broadcom
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

Comparison Ndiswrapper vs B43 Driver

Ndiswrapper (SVN Version: 2673) with Windows Driver as Described in this thread: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Driver Obtained Via the Following:
```
wget http://myspamb8.googlepages.com/Driver_3607.zip
unzip Driver_3607.zip
```


B43 Driver
```
 modinfo b43
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       FW13
license:        GPL
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     9B6D0D14CB834660F8EAC23
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        mac80211,ssb,input-polldev,led-class,rfkill
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistance (default on) (int)

```


**[SIZE="4"]Results With Each Driver Loaded Showing Authentication Capabilities[/SIZE]**

**[SIZE="2"]Ndiswrapper[/SIZE]**
```
$ sudo iwlist wlan0 auth
wlan0     Authentication capabilities :
		WPA
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		disabled
          Current Key management :
          Current Pairwise cipher :
		none
          Current Pairwise cipher :
		none
          Current Authentication algorithm :
		open

```

**[SIZE="2"]b43 Open Source Driver[/SIZE]**

```
$ sudo iwlist wlan0 auth
wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current Authentication algorithm :
		open


```

**[SIZE="4"]Summary[/SIZE]**

Notice that the Offered Ndiswrapper Driver Does Not Support WPA2, whereas the b43 driver does offer WPA2 capabilities.  Findings may be significant given recent WPA exploit.  

Conclusion
If using WPA2 wireless Authentication with Broadcom 4306 chipset - Use the b43 driver instead of Ndiswrapper.  B43 offers WPA2, WPA, WEP, and Open Authentication. Ndiswrapper offers WPA, WEP, and Open Authentication.

---

### Post by Ayuthia on 2008-11-22
I took a look at the bcmwl5.inf file for the driver that you used.  The date on it was in April of 2004.  It looks like the driver is too old for WPA2.  I did try it out on Dell laptop that does have a 4306 rev 03 card and this driver produced the same info as yours when I ran sudo iwlist wlan0 auth.  However, my laptop was using a different driver prior to trying yours and it does have WPA2 capabilities (although I am unable to test and see if it works--found out my router does not provide WPA2).  Unfortunately, it is most likely using the XP drivers that came with the laptop.

My current thought is to try the sp33008 or the sp34152 options (2a and 2b from the no-fluff guide).  The bcmwl5.inf file does show that it supports the 14e4:4320 chipset.  The sp33008 is what I am using in my HP laptop but it has the 4311 rev 01 card.  It also has WPA2 listed in the sudo iwlist wlan0 auth results.

---

### Post by yipperzz on 2008-11-22
> **Ayuthia said:**
> I took a look at the bcmwl5.inf file for the driver that you used.  The date on it was in April of 2004.  It looks like the driver is too old for WPA2.  I did try it out on Dell laptop that does have a 4306 rev 03 card and this driver produced the same info as yours when I ran sudo iwlist wlan0 auth.  However, my laptop was using a different driver prior to trying yours and it does have WPA2 capabilities (although I am unable to test and see if it works--found out my router does not provide WPA2).  Unfortunately, it is most likely using the XP drivers that came with the laptop.

My current thought is to try the sp33008 or the sp34152 options (2a and 2b from the no-fluff guide).  The bcmwl5.inf file does show that it supports the 14e4:4320 chipset.  The sp33008 is what I am using in my HP laptop but it has the 4311 rev 01 card.  It also has WPA2 listed in the sudo iwlist wlan0 auth results.

Thanks, I tried the sp33008 driver and it showed WPA2 support after.  But it seems like my reception isn't as good as the WPC54Gv2 driver that I was using before.  It was working perfectly in 8.04 with the WPC driver, but with 8.10 it seems like I can only connect to one of my three routers.  With the sp33008 driver, I'm able to connect to two out of my three routers now but it's odd that signal strength is down.  With the WPC54Gv2 driver installed my closest router (about 5 ft. away) shows 98% strength.  The sp33008 driver shows ~80%.  I'm going to try the sp34152 and see if that works any better.  But at least I can connect to two of my three routers now.  When I was using the b43legacy (I couldn't get b43 to work) it seemed like my speed was at 1 mbps.  So since I was working perfectly in 8.04 with ndiswrapper, I think I'm going to stick with that.

---

### Post by yipperzz on 2008-11-22
Well I tried sp34152 and it's the same if not worse as signal strength.  But Ayuthia was correct that it did support WPA2.  I can't connect to that other router that I was able to connect earlier with sp33008.  So now I'm stuck again.  Just to make sure I wasn't going crazy, I went back to the WPC54Gv2 driver and the signal strength is a lot better.  It's showing consistently 100% strength to my closest router.  It's odd because I was able to connect to one of my WPA2 routers with this same driver in 8.04.  So I'm not sure what has changed where I can't connect anymore?  I'm confused.  I'm waiting for my new laptop to come in so I don't have to deal with this brcm crap anymore.  I'm really glad I don't work there anymore lol.

---

### Post by kevdog on 2008-11-22
I tried both those drivers:

sp33008 and the sp34152

The sp33008 was a total bomb -- wouldn't associate with card

The sp3415 could detect the networks, but could never obtain an IP address.  This driver stated it did support wpa2, but didnt work for me

---

### Post by Ayuthia on 2008-11-22
> **kevdog said:**
> I tried both those drivers:

sp33008 and the sp34152

The sp33008 was a total bomb -- wouldn't associate with card

The sp3415 could detect the networks, but could never obtain an IP address.  This driver stated it did support wpa2, but didnt work for me

Can you give me your lspci -nnm info?  I am looking for the subvendor information.  It will help in finding a better match.  My guess is that a newer Asus driver might do the trick.

EDIT:
You might try this one out:
[http://dlcdnet.asus.com/pub/ASUS/wireless/WL-270n/DR_WL270N_4%5B100%5D15%5B5%5D.zip](http://dlcdnet.asus.com/pub/ASUS/wireless/WL-270n/DR_WL270N_4%5B100%5D15%5B5%5D.zip)

---

### Post by kevdog on 2008-11-22
Here is the requested information:

$ lspci -nnm | grep Broadcom
02:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Linksys [1737]" "Device [4320]"


Where are you looking for drivers?

---

### Post by kevdog on 2008-11-22
> You might try this one out:
[http://dlcdnet.asus.com/pub/ASUS/wir...D15%5B5%5D.zip](http://dlcdnet.asus.com/pub/ASUS/wir...D15%5B5%5D.zip)

Ehh, that driver does the same dang thing!! It scans and locates networks, it even authenticates with wpa_supplicant, however fails to obtain an IP address.  Really stinks!!

---

### Post by Ayuthia on 2008-11-22
> **kevdog said:**
> Here is the requested information:

$ lspci -nnm | grep Broadcom
02:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Linksys [1737]" "Device [4320]"


Where are you looking for drivers?
I just googled the asus wireless driver.  Nothing too fancy yet.

Linksys.  This should be a fun one.  :)

---

### Post by Ayuthia on 2008-11-22
> **kevdog said:**
> Ehh, that driver does the same dang thing!! It scans and locates networks, it even authenticates with wpa_supplicant, however fails to obtain an IP address.  Really stinks!!

Here is one from Linksys for the WPC300N but the .inf file contains a line that says it can support the 4320 card:
> %WPC54GSv1_DeviceDesc% = WPC54GSv1_NT60, PCI\VEN_14E4&DEV_4320&SUBSYS_43201737

The file is around 19Mb:
[http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1144763513196&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1144763513196&pagename=Linksys%2FCommon%2FVisitorWrapper)

---

### Post by kevdog on 2008-11-22
Wow -- unless you know a way to force ndiswrapper to load with the particular device, the linksys driver didn't even associate with the device -- after adding the ndiswrapper kernel module and then checking lshw, the device is still unclaimed.

---

### Post by Ayuthia on 2008-11-22
> **kevdog said:**
> Wow -- unless you know a way to force ndiswrapper to load with the particular device, the linksys driver didn't even associate with the device -- after adding the ndiswrapper kernel module and then checking lshw, the device is still unclaimed.

The ndiswrapper --help says:
> -a devid driver  use installed 'driver' for 'devid' (dangerous)
I have never tried the -a like this though.  It is odd that your card is not being seen with this driver.  The subvendor matches with the .inf file for your card.  Mine is not listed on there and it seems to be happy.

I must have the most generic broadcom cards.  For some reason, my cards can't ever duplicate the issues of others.  The funny part is that it is frustrating for me because I don't really like the cards that "just work".  Where is the fun in plug and play?

EDIT:
Have you checked ls -l /etc/ndiswrapper/lsbcmnds to see if the symbolic link for 14E4:4320.5.conf is pointing to 14E4:4320:4320:1737.5.conf?  If it is not, you might change the link to point to it.  That might also do the trick.

---

### Post by kevdog on 2008-11-22
Here is what I am doing just to give you a clue

I using the WPC300N driver as you provided a link to above

I using the driver located in the 2KNT directory

Here is my list of commands:

$ sudo ndiswrapper -i lsbcmnds.inf
installing lsbcmnds ...
$ sudo ndiswrapper -l
lsbcmnds : driver installed
	device (14E4:4320) present (alternate driver: ssb)
$ sudo modprobe ndiswrapper


Yet the device remains unclaimed:
*-network UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64


Looking into dmesg I find the following:

[37364.089224] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[37364.154799] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
[37364.154979] usbcore: registered new interface driver ndiswrapper


And then looking into /var/log/syslog:

Nov 22 22:11:39 sue kernel: [37364.089224] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Nov 22 22:11:39 sue loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds 
Nov 22 22:11:39 sue loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds 
Nov 22 22:11:39 sue kernel: [37364.154799] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Nov 22 22:11:39 sue kernel: [37364.154979] usbcore: registered new interface driver ndiswrapper


What the heck does too many .sys files for driver lsbcmnds mean?

In the directory with the .sys, .inf files I have the following:
bcm43xx64.cat  bcm43xx.cat  bcmwl564.sys.bak  bcmwl5.sys  lsbcmnds.inf

---

### Post by kevdog on 2008-11-23
I am writing this from a connected ndiswrapper machine.

Here was one hurdled cleared:

The big hint was this: 
Nov 22 22:11:39 sue loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds

So inside /etc/ndiswrapper/lsbcmnds was the following:
```

14E4:4318:0048:1737.5.conf  14E4:4328:0068:1737.5.conf	wec600n.sys
14E4:4318:0049:1737.5.conf  14E4:4328.5.conf		wpc300n.sys
14E4:4318.5.conf	    14E4:4329:0058:1737.5.conf	wpc54gsv1.sys
14E4:4320:4320:1737.5.conf  14E4:4329.5.conf		wpc54gsv2.sys
14E4:4320.5.conf	    lsbcmnds.inf		wpc54gv3.sys

```

I don't know the limitations of ndiswrapper, however I noticed there were 5 .sys files in this directory.  What I did was to rename 2 of these files so they would be ignored:

```

14E4:4318:0048:1737.5.conf  14E4:4328:0068:1737.5.conf	wec600n.sys.bak
14E4:4318:0049:1737.5.conf  14E4:4328.5.conf		wpc300n.sys.bak
14E4:4318.5.conf	    14E4:4329:0058:1737.5.conf	wpc54gsv1.sys
14E4:4320:4320:1737.5.conf  14E4:4329.5.conf		wpc54gsv2.sys
14E4:4320.5.conf	    lsbcmnds.inf		wpc54gv3.sys

```

I then reloaded the ndiswrapper kernel module
```

$ sudo modprobe ndiswrapper

```

Within the syslog I found the following:
```

Nov 22 22:34:32 sue kernel: [38737.221409] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Nov 22 22:34:32 sue loadndisdriver: loadndisdriver: load_driver(321): file wpc300n.sys.bak is ignored 
Nov 22 22:34:32 sue loadndisdriver: loadndisdriver: load_driver(321): file wec600n.sys.bak is ignored 
Nov 22 22:34:32 sue kernel: [38737.824170] ndiswrapper: driver lsbcmnds (Linksys, A Division of Cisco Systems, Inc.,07/18/2007, 4.150.31.0) loaded
Nov 22 22:34:32 sue kernel: [38737.829915] ndiswrapper 0000:02:00.0: PCI INT A -> Link[PILF] -> GSI 10 (level, low) -> IRQ 10
Nov 22 22:34:32 sue kernel: [38737.838927] ndiswrapper: using IRQ 10
Nov 22 22:34:33 sue kernel: [38738.331255] wlan0: ethernet device 00:12:17:35:17:10 using NDIS driver: lsbcmnds, version: 0x4961f00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
Nov 22 22:34:33 sue kernel: [38738.332534] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Nov 22 22:34:33 sue kernel: [38738.333427] usbcore: registered new interface driver ndiswrapper

```

I then went ahead and completed a manual connection using the following as my wpa_supplicant.conf file:

```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="ESSID in QUOTES"
	psk="PASSWORD IN QUOTES"
        scan_ssid=0
	key_mgmt=WPA-PSK
	proto=RSN WPA
	pairwise=CCMP TKIP
	group=CCMP TKIP
}


```

I captured an IP address with the following manual commands:
```

sudo wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 
sudo dhclient wlan0

```


Update
The ndiswrapper method is very inconsistent --- I tried subsequently reconnecting after several reboots, and still receive no dhcp offers from the server.  The driver must work since I have connected once, however its really pathetic.  The log files give no further reason for not receiving an IP address from the DHCP server/router.

---

### Post by Ayuthia on 2008-11-23
Ok.  I found out that when ndiswrapper failed, my system automatically loaded b43 so I thought that all was fine.  I have now changed that and was able to duplicate the messages that you have.  I also did the same and changed the name of the two files.  The only difference is that I am able to connect via WPA (even after rebooting).  So either the driver does not play well with WPA2 or else the driver is not playing well with your card.

---

### Post by Ayuthia on 2008-11-23
Here is a driver for a WMP54GS v1.0 card:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843440&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4344040888B08&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843440&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4344040888B08&displaypage=download#versiondetail)

It also listed WPA2 and it connected on mine with WPA.  There was a driver out there for the WMP54G v1 but it was too old so it does not support WPA.

I just realized that I never asked which linksys card do you have?  I saw linksys and was only thinking of the pci drivers instead of staying with the PCMCIA cards.  I only realized this when I could not find a matching subvendor number in the WMP54* drivers.

In case you haven't guessed, I am grabbing the drivers from here:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859840888&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4088837314B06&displaypage=download](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859840888&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4088837314B06&displaypage=download)

---

### Post by kevdog on 2008-11-23
Some thoughts after playing around

My router is a Linksys WRT54GL flashed with the dd-wrt firmware.  Its very interesting to play with this firmware because it really gives you a very detailed description of what is going on at the router level when your client attempts to associate.

What I am seeing is this:

Within the router there is a Active Clients Table and DHCP Clients Table.  Listed under Active Clients are any clients connecting with a static IP, or clients that have connected but have not yet been issued a DHCP lease.  I'm only currently using DHCP.

When I connect manually on the command line with the following:
$ sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant.conf

I should see two things:
#1 - On client I should see something like the following: 
CTRL-EVENT-CONNECTED - Connection to 00:13:10:8e:94:e9 completed (auth) [id=0 id_str=]
#2 - On the router - I need to see my client listed under Active Clients with the appropriate MAC address

What I'm find is actually very funny.  In many cases I do get #1 but not #2.  If I do not get both, then going ahead and requesting a dhcp lease (sudo dhclient wlan0) always fails.  I always need to have both situations be true, unless the request for the dhcp lease always fails

When the situation fails, I sometimes need to "cycle" the client driver.  This is accomplished via the following:
```

sudo dhclient -r wlan0
sudo ifconfig wlan0 down
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up

```

I then authenticate (because I'm using the -d (or debug flag) I authenticate in one terminal windows) and then ask for a dchp lease (I do this in another window)
```

sudo wpa_supplicant -i wlan0 -d wext -c /etc/wpa_supplicant.conf
sudo dhclient wlan0

```


Also since my router is set to use WPA2/1 (prefers WPA 2 but falls back to standard WPA), I also use the command line utility wpa_cli to actually verify what authentication mechanism was used after being issued the dhcp lease.

WPA hex passphrases are generated by using the wpa_passphrase utility
Syntax: wpa_passphrase <ESSID> passphrase
An Example would be:
```

$ wpa_passphrase ESSID_OF_ROUTER passphrase
network={
	ssid="ESSID_OF_ROUTER"
	#psk="passphrase"
	psk=f8d119b7e91e97a0878814ba6b4e8d715bcb189162080d92b3a1deb71037e1a7
}

```

Here are two examples.
**[SIZE="3"]WPA[/SIZE]**
wpa_supplicant.conf file
```

ap_scan=1
#fast_reauth=1
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="ESSID in QUOTES"
	psk=<hex passphrase>
        scan_ssid=1
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
}


```

WPA results using wpa_cli
```

$ sudo wpa_cli
wpa_cli v0.6.4
Copyright (c) 2004-2008, Jouni Malinen <j@w1.fi> and contributors

.....

Interactive mode

> status
bssid=<MAC ADDRESS of ACCESS POINT>
ssid=<ESSID>
id=0
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=COMPLETED
ip_address=192.168.1.100

```

**[SIZE="3"]WPA2[/SIZE]**

wpa_supplicant.conf

```

ap_scan=1
#fast_reauth=1
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="ESSID in Quotes"
        psk=<hex passphrase>
        scan_ssid=1
	key_mgmt=WPA-PSK
	proto=RSN WPA
	pairwise=CCMP TKIP
	group=CCMP TKIP
}


```

```

It was my full intention to show you the WPA2 confirmation here, however its very inconsistent.  It will not connect with any regularity

```


CONCLUSION:
Connecting manually using a WPA configuration is quite predictable.  Using a WPA2 configuration however, the chance of obtaining a connection is less than 20% using ndiswrapper/broadcom.

Possibly the WPA2/ndiswrapper/broadcom issue represents a driver issue however I have now tried 3 separate broadcom drivers for my particular chipset that claim to be wpa2 compatible.  Older versions only had WPA capabilities.  

When performing the WPA2 authentication handshake, the access point fails to see the client on most occasions.  The debug output produced from a wpa authentication vs a wpa2 authentication is usually much more detailed and contains many more steps before authentication is granted.  Whether this represents a bug with either the driver, ndiswrapper, or the wireless tools package, its difficult to speculate. 

I invite others to either confirm or deny these findings using ndiswrapper

__________Addendum
Please just as an addendum, I've run the same process using the b43 driver.  I was able to connect using a WPA2 configuration without a hitch.  Both #1 and #2 conditions were immediately satisfied with this driver.

Here is confirmation from the wpa_cli utility:
```

$ sudo wpa_cli
wpa_cli v0.6.4

....

Selected interface 'wlan0'

Interactive mode

> status
bssid=<MAC ADDRESS>
ssid=<ESSID>
id=0
pairwise_cipher=CCMP
group_cipher=TKIP
key_mgmt=WPA2-PSK
wpa_state=COMPLETED
ip_address=192.168.1.100

```

---

### Post by kevdog on 2008-11-23
Im using a Linksys WPC54GS -- there is no version listed on the outside of the card so I'm assuming v1.0.  And yes its a pcmcia card.  I guess I've neglected that detailed -- which means yes -- I'm using a laptop to do all of my testing.

---

### Post by Joe2Shoe on 2008-11-23
I don't know if this helps.
I just did a fresh install of v8.10 (dual-boot) with Vista.
My wifi card is a Broadcoam BCM4312 rev. 02.
I did not use NDISwrapper or FWcutter.
I just went to System/Administration/Hardware Drivers and clicked on the "Broadcom STA wireless driver" and activated it.
Then I configured my network using "WPA & WPA2 Personal" encryption.
It works.
Sometimes I have to try several times for it to connect, as it keeps popping-up the box with the "WPA & WPA2 Personal" security password.  I just click "Connect" and it finally connects.

So, then I downloaded NDISwrapper via Synaptic Program Manager and installed the Windows Broadcom BCM4312 rev. 02 driver (bcmwl6.inf & bcmwl6.sys), and lost my connection.
So, I uninstalled the bcmwl6.sys driver and returned to the "Broadcom STA Wireless driver" and it works again.

As long as it's working, I'm leaving it alone.
Hope this helps.
Joe2Shoe.

---

### Post by kevdog on 2008-11-24
I'm going to pretty much consider this issue dead, except I got a few more drivers to try.   

I wonder what other people's experiences with wpa2/ndiswrapper/broadcom chipsets have been with Intrepid?

---

### Post by skinnejay on 2009-10-09
Hi, I've had little luck myself with the Broadcom 4306 rev 02 on Jaunty and now Karmic. Ndiswrapper worked fine on a WEP secured network. Just recently I switched over to WPA2 and all heck broke loose. Ndiswrapper failed to connect and I haven't been able to find a driver that will support WPA2. I know the hardware works because I can boot into Windows 7 and use the WPA2 secured network. B43-fwcutter installs the B43legacy drivers which do happen to connect to the network after a super long handshake but gives very shoddy speeds and eventually hangs after 5 minutes and losses connection to the internet. At this point, it looks like I'll just have to drop down to WPA so I can continue to use Ubuntu. Unless anyone knows a windows driver for the rev 02 that has WPA2 support :)

---

### Post by PrePenguin on 2009-10-09
> **skinnejay said:**
> Hi, I've had little luck myself with the Broadcom 4306 rev 02 on Jaunty and now Karmic. Ndiswrapper worked fine on a WEP secured network. Just recently I switched over to WPA2 and all heck broke loose. Ndiswrapper failed to connect and I haven't been able to find a driver that will support WPA2. I know the hardware works because I can boot into Windows 7 and use the WPA2 secured network. B43-fwcutter installs the B43legacy drivers which do happen to connect to the network after a super long handshake but gives very shoddy speeds and eventually hangs after 5 minutes and losses connection to the internet. At this point, it looks like I'll just have to drop down to WPA so I can continue to use Ubuntu. Unless anyone knows a windows driver for the rev 02 that has WPA2 support :)

Even WEP is weak in ubuntu its definately something that needs some attention.. All mine operate sub-par compared to how they work in windows. Maybe i just havent found the answer either but there seems to be a common issue with all the wireless set-ups.

---

### Post by kevdog on 2009-10-09
Although kind of a dead thread, I would suggest to any users using the 4306 rev02 card in karmic or jaunty to use the open source openfwwf card for their driver.  I'm using it now myself and it works great:

[http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/)

---

