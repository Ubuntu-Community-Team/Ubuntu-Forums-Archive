---
title: "GEtting a Linksys WMP11 v4 PCI card working"
date: 2004-12-06
forum: Networking &amp; Wireless
---

### Post by offby1 on 2004-12-06
Alright, I tossed Ubunu on my laptop the other day and was generally rather pleased.

Trying it on a desktop with the WMP11 card however is working out to be less than stellar.  The only networking that this PC has is its wireless card.  However, there seem to be no drivers for it in Ubuntu.  I'm led to believe that the prism2 drivers from [here](http://www.linux-wlan.org/) will work, if only I could somehow manage to *compile* them.  I managed (with much sturm und drang) to get the linux-sources-2.6.8.1.tar.gz file and the relevant driver file onto the system, but when I attempt to configure the driver to compile, it chokes because of the nonstandard layout of the kernel files (specifically, there's no version.h in $LINUX/include/linux/ ) and so I cannot compile it.

Has anyone had any luck with this driver, or kernel modules of their own and could share with me how to fix my mom's computer? :)

---

### Post by Quest-Master on 2005-01-03
I pretty gave up on trying to get my old computer's networking to work in Ubuntu. Linksys only makes their drivers available in Windows, and there haven't been any written by the kernel developers.

I heard you can use the ndiswrapper package to still get the PCI card working though. Haven't tried it myself.

---

### Post by crane on 2005-01-03
I too picked up a wireless card the other day. 
And no it didn't work. but from whet I gather the older linksys cards work fine. The card I bought was a linksys WMP11 v4 . Linux doesn't even notice when it is plugged in.
 I emailed linksys about it. Their response was pretty much sorry that card doesn't work with linux right now, have a nice day :-(

---

### Post by jdodson on 2005-01-04
i have the same card, check into program called ndiswrapper, it takes the windows driver and uses that to connect to the wireless card.  it works for me, flawlessly.

you can download the driver from either the universe OR get the source and follow the directions contained in a text file.  

personally i did the source compile as i did not have internet connection until my wireless was working.

good luck.

---

### Post by crane on 2005-02-08
[QUOTE=jdodson]i have the same card, check into program called ndiswrapper, it takes the windows driver and uses that to connect to the wireless card.  it works for me, flawlessly.

you can download the driver from either the universe OR get the source and follow the directions contained in a text file.  

personally i did the source compile as i did not have internet connection until my wireless was working.

good luck.[/QUOTE]


just curious, what .inf file did you use?

---

### Post by wapowell on 2005-02-18
I, too, got my wireless working using ndiswrapper.

I am not sure what the driver cd for your card has on it, but mine (it is a linksys WPC54GS) had only two inf files in the root of the cd.  One was the autorun.inf and the other was lsbcmnds.inf.  Ok, autorun.inf was a no brainer.  It contains no driver info.  So I used the other one (lsbcmnds.inf).  As it turns out, when I search the driver cd, those are the only two inf files on there.

If you're not sure which inf to use, post the url to the drivers for your card and I can take a look.

Hope this helps a bit.   :-) 

-Bill

---

### Post by asimonelli on 2005-05-03
I have a Linksys WMP11 ver 4 PCI card and I got it to work with NDISWrapper.

Go to this site [here](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=8bf5bdc62cc022bdeb0df66fb4b11fcb) for a list of compatible cards and a link to download the drivers.

Download the driver and extract it to you home directory. Then use the following commands (assuming you have the [FONT=Courier New]ndiswrapper-utils[/FONT] package installed from synaptic):

[FONT=Courier New]sudo ndiswrapper -i LSIPNDS.inf[/FONT]
[FONT=Courier New]sudo ndiswrapper -l[/FONT]  (to make sure the driver and hardware are present)
[FONT=Courier New]sudo modprobe ndiswrapper[/FONT]
[FONT=Courier New]sudo ndiswrapper -m[/FONT] (to add an alias wlan0)

configure with System --> Network or use [FONT=Courier New]iwconfig[/FONT] command.

I can't get it to work with WEP though.  It connects with an open wireless network but not with a WEP key even though it sees all of the access points around me.  My router/access point's authentication is set to Open System as suggested in a different thread but it still doesn't work.  Did I need to install ndiswrapper-source and compile it or am I missing something else?

---

### Post by abbot on 2005-06-07
[QUOTE=asimonelli]I have a Linksys WMP11 ver 4 PCI card and I got it to work with NDISWrapper.

Go to this site [here](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=8bf5bdc62cc022bdeb0df66fb4b11fcb) for a list of compatible cards and a link to download the drivers.

Download the driver and extract it to you home directory. Then use the following commands (assuming you have the [FONT=Courier New]ndiswrapper-utils[/FONT] package installed from synaptic):

[FONT=Courier New]sudo ndiswrapper -i LSIPNDS.inf[/FONT]
[FONT=Courier New]sudo ndiswrapper -l[/FONT]  (to make sure the driver and hardware are present)
[FONT=Courier New]sudo modprobe ndiswrapper[/FONT]
[FONT=Courier New]sudo ndiswrapper -m[/FONT] (to add an alias wlan0)

configure with System --> Network or use [FONT=Courier New]iwconfig[/FONT] command.

I can't get it to work with WEP though.  It connects with an open wireless network but not with a WEP key even though it sees all of the access points around me.  My router/access point's authentication is set to Open System as suggested in a different thread but it still doesn't work.  Did I need to install ndiswrapper-source and compile it or am I missing something else?[/QUOTE]

Im working on getting the same card to work and am following the same steps.  However once i install the driver and check it it tells me "lsipnds invalid driver."  ive tried the one on the cd as well as the one from the site.  can someone please tell me what the deal is?

---

### Post by roshpat on 2005-06-09
I was just wondering what version of kernel that you are using.........

I am having trouble with setting essid using ndiswrapper and WMP11V4 PCI card.

I get the following error message :

ndiswrapper(set essid:58) : setting essid failed (0001003)

when I try to set essid or when I do ifup wlan0(which is my wireless interface).
Basically this error message pops up whenever I try to set any value using iwconfig.

I am using Kernel version 2.4.30
Ndiswrapper 1.1
WMP11 v4 PCI card with the the InproComm chipset since my lspci says 17fe:2120

I would really appreciate if someone could me out.I am pretty much a complete newbie .........

Thanks in advance...

---

### Post by kalico on 2005-06-21
In my googling for information on this problem (my error messagse are identical to yours, roshpat) I found this page:

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ)

And the following information helped me to the point where I am getting an access point, and it's connecting to the SSID:

    First, make sure that you can see the Access PointAP/router/ad-hoc station in the scan: =iwlist wlan0 scan= should list the station you are trying to connect to. If it is not seen, then either the radio is off or the station you are trying to connect is not broadcasting its SSID. If the radio is off, you should turn it on different systems have different ways of toggling the radio status: some have a special key, e.g., Fn F2 some have a BIOS setting some need a special kernel module - see [[http://rfswitch.sourceforge.net]](http://rfswitch.sourceforge.net]) for details. Once the station is seen, set the operating mode Managed or Ad-Hoc as appropriate e.g., =iwconfig wlan0 mode Managed=. Then set the WEP encryption key, if you are using WEP. While setting the key, specify the security mode =open= or =restricted= used by the station. e.g., =iwconfig wlan0 key restricted XXXXXXXXXX=. If in doubt, try both modes. Until proper key is set check output of =iwconfig wlan0=, ESSID can't be set. Then set the ESSID e.g., as =iwconfig wlan0 essid myssid=. Note that quotes shouldn't be used around ESSID string, in this case, =myssid=. At this point, the MAC hardware address of your station's interface should also be set automatically. Check the output of =iwconfig wlan0= if ESSID and station's MAC address have been set. Note that unless ESSID is set, the interface can't be configured.



The following might also be helpful..... I am still learning myself, so this is where I'm headed next. That and my guru just showed up on GAIM.... :)

    Try setting the ESSID first, then the key. If ESSID is still not set, set it again after the key.
    Enable ESSID broadcast on your station. Make sure your station is listed in =iwlist wlan0 scan=. If the station is not listed in the scan, you can't associate with that station.
    Note that when setting the ESSID in Managed mode, the ESSID does not show up in iwconfig until the card has successfully associated with the access point!

---

### Post by rictus007 on 2006-10-24
For WMP11 v4 according to other post you need to install all inf (3) to make it work.  It worked for me just fine except for the problem mention before...wep for some reason don't work.

---

### Post by apps4apps on 2007-04-07
I'm also working on setting up the Linksys WMP11 ver 4 PCI card and the driver seems to load but I can't seem to get a connection. Trying to set the WEP key seems to be the problem. If I do:```
sudo modprobe ndiswrapper
```then do:```
dmesg|grep ndiswrapper
```
I see the following at the end: ```
[17216315.572000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17216315.588000] ndiswrapper: driver lsipnds (Linksys,07/09/2003,3.01.7.2003) loaded
[17216315.700000] ndiswrapper: using irq 11
[17216316.456000] ndiswrapper (set_encr_mode:689): setting encryption mode to 0 failed (00010003)
[17216316.572000] ndiswrapper (add_wep_key:815): adding encryption key 1 failed (C0010014)

```
Trying to set any key seems to fail using iwconfig. Does anyone have any suggestions?

---

### Post by apps4apps on 2007-04-07
If I do ```
sudo iwlist encryption
``` I get the following```
wlan0     2 key sizes : 40, 104bits
          4 keys available :
                [1]: off
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [0]
          Security mode:restricted
          Authentication capabilities :
                WPA
                CIPHER TKIP
                CIPHER CCMP
          Current key_mgmt:0x0
          Current cipher_pairwise:0x0
          Current cipher_group:0x0

```Any suggestions?

---

### Post by apps4apps on 2007-04-07
I seem to have figured out one method of using some security by using wpa_supplicant :) . After a bit of trial and error the following seems to work ok on this machine connecting to a Linksys BEFW11S4 router using a WMP11 v4 Linksys wireless card. Hopefully I've remembered the steps correctly...

- download the driver for the v4 card from Linksys 
- use the directions from the previous post to set up ndiswrapper
- set your router to use WPA Pre-Share Key, TKIP and set a key (I used a password 10 characters long).
- in Advanced Wireless Settings, verify that Authentication Type is set to: Auto(Default)
- verify your router's settings by checking the values from a scan```
iwlist wlan0 scan
```Your output should be similar to this:```
wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:08:3A:E0
                    ESSID:"your_network"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-53 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

```
- next, verify that you have wpa_supplicant installed. (eg: type **sudo wpa_supplicant** in a console)
-  create a file named **wpa_supplicant.conf** in **/etc** and add the following (substitute network_name and thisismine with your information):```
# Only WPA-PSK is used. Any valid cipher combination is accepted.
network={
        ssid="network_name"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40
        psk="thisismine"
        priority=2
}

```
- next, run the following to test the connection (This should display information that may help troubleshoot problems connecting if things don't work as expected.)```
wpa_supplicant -Dwext -w -iwlan0 -c/etc/wpa_supplicant.conf -dd
``` 
- open another console window and run (if using dhcp):```
dhclient wlan0
```If all goes well you should have a connection. The -B flag can be used to run in the background instead of using the -dd flag:```
wpa_supplicant -Dwext -Bw -iwlan0 -c/etc/wpa_supplicant.conf
```To start things up automatically after rebooting try the following:
```
sudo gedit /etc/network/interfaces
```Then, edit the wlan0 section to look something like the following:```
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

post-down killall -q wpa_supplicant

auto wlan0
```
This seems to work well on this PC but, please be aware that I'm a newb at setting this up so the information I've provided has been gathered from various sources and tested by trial and error... ;)

---

### Post by apps4apps on 2007-04-18
Out of curiosity, has anyone else tried setting up wpa_supplicant using WPA to work with this wireless card (WMP11 v4) and had problems with their system locking up? I'm still new to setting this up so I've probably missed a setting or set something wrong. Could someone ***please*** give a suggestion of what might be wrong?  

Everything completely locks up after a short while once wpa_supplicant is running. The screen freezes and the mouse and keyboard have no effect. I thought that it must be a hardware failure and spent a lot of time troubleshooting. In fact I went as far as to change the motherboard, power supply, memory, hard drive, video card then re-install Ubuntu 6.10, set everything up gain, just to find that the error remains. If I leave everything set up "as is" but don't load wpa_supplicant at startup then the machine runs great for days (and longer) without any issues. 

Please help. I'd like to run Ubuntu on this machine but may have to delete and run something else if I can't get the wireless card working on this machine. Also, I doubt it's a defective card issue since it works great using Windows Vista...

---

### Post by PARO on 2007-06-27
Nevermind, I think I'm just going to throw this in the trash and buy a new card.

---

### Post by Kilz on 2007-09-21
[The list of drivers is now here. ]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

---

### Post by 1976saint on 2008-01-13
Hi, I have the same problem with a Linux PC I just set-up for someone. They did not want windows so I thought great a chance to get Linux running for someone. Anyway, go it working but the wireless driver seems to crash (using the NDIS Wrapper, its a version 4 card) and most apps have to be forced to close, other won't open and when trying to shutdown it hangs trying to stop Suppliment modules.

Anyone seen this or fixed? 

I'm a relative Noob so anyhelp much appriciated...

Regards, Paul.

---

### Post by brettp on 2008-01-20
I have also run into the same problem with wpa_supplicant.  Using wpa_supplicant, I can connect to my WPA-enabled router fine but my system will freeze after a random amount of time (usually about 30 minutes) and I am forced to restart.

For now, I've had to turn off security on my router and not use wpa_supplicant (I can't even get WEP to work).  My system has been fine ever since.

Has anyone found a solution to this problem?  I really don't like having my network unsecured.

Regards,

Brett P

---

### Post by pgreenwood on 2008-01-28
> **brettp said:**
> ...For now, I've had to turn off security on my router and not use wpa_supplicant (I can't even get WEP to work).  My system has been fine ever since.

Has anyone found a solution to this problem?  I really don't like having my network unsecured.


This is consistent with **[what I have ]("http://forums.gentoo.org/viewtopic-t-652580-highlight-wmp11.html")**with my Gentoo box. I was very generous giving myself a [SOLVED].

---

