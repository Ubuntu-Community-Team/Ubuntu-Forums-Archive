---
title: "Dlink DWL-G122 C1 Ubuntu fiesty 7.04 working this is how to do it."
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by sammao on 2007-05-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ubuntu Fiesty 7.04

1. Follow this link below and don't use any network manager it ***** up the thing. At step 6 see below. Do not insert the usb dongle untill you done step 1.
 
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)

2. At Step 6 I had to have it like this instead..
--------------------------------------------
# rt73 wireless network device using static IP address
# all info channel etc you can set up in your router
auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "networkessid"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwconfig rausb0 channel 8
        pre-up iwpriv rausb0 set AuthMode=WEPAUTO
        pre-up iwpriv rausb0 set EncrypType=WEP  #64bit
        pre-up iwpriv rausb0 set Key1=1234567891
        pre-up iwpriv rausb0 set SSID="networkessid"
        pre-up iwconfig rausb0 ap xx:xx:xx:xx:xx:xx #your mac id printed on the usb device
--------------------------------------------------
(remember step 7,  sudo modprobe rt73)
3. Then i have to reboot without the usb dongle inserted, pull out
4. when booted up and logged in insert it.. wait .. wait.. surf the web.
5. reboot just to check .. still working.. 
6. now working every time you boot no need to take it out.

---

### Post by kaar3l on 2007-05-25
I tried to get mine work under Xubuntu, but it didn't:
```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
laptop@laptop-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ 

```

Could anybody send me exactly those files: rt73.bin and rt73sta.dat

---

### Post by Thiudareiks on 2007-06-18
Hi, I tried to set up my  DWL-G122 C1 on Xubuntu feisty 7.04 following another guide:
[http://wiki.ubuntu-it.org/Hardware/Wireless/RalinkRT73](http://wiki.ubuntu-it.org/Hardware/Wireless/RalinkRT73)
it' an italian guide...anyway my key seem to work fine cause I can ping my router 192.168.1.1 or [www.google.it](www.google.it).

When I open firefox or gaim instead, the system freezes and I have to shut it down.

Any idea?

Thanks

---

### Post by Swab on 2007-06-24
> **kaar3l said:**
> I tried to get mine work under Xubuntu, but it didn't:
```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function &#8216;usb_rtusb_probe&#8217;:
/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable &#8216;device&#8217;
make[2]: *** [/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/laptop/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
laptop@laptop-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ 

```

Could anybody send me exactly those files: rt73.bin and rt73sta.dat

Same problem here.   Anyone know what's going on?

Edit:  Wasn't using the latest driver.  Get it here: [http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz)

---

### Post by davidwhthomas on 2007-07-10
That link at the top ( [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview") ) is an excellent guide! I finally got my Dlink DWL-G122 C1 USB adapter working :-) and using WPA too :-)

For those in the same situation, I followed the guide to the letter but with these changes:

In Step 6: This was all I needed to add at the bottom of the **etc/network/interfaces** file:

```
# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
auto rausb0
```

I commented out the 'auto eth0' part to default to wireless

The rest of the config went into **etc/Wireless/RT73STA/rt73sta.dat** :

Here's the whole file, configured to use WPA encryption / auth :

```
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=MyNetworkSSID
NetworkType=Infra
Channel=1 # I got this value from the router for wireless channel
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=mypasswordstringwenthere
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0
AdhocOfdm=0
FastRoaming=0
RoamThreshold=70
```

Then I just restarted the computer and Voila! Here I am typing how I did it, connected via my D-Link DWL-G122 RevC1 USB adapater using WPA encryption

Thanks so much to everyone who contributes and writes these guides, it was a huge help

---

### Post by diesel1 on 2007-07-16
Hi all, thanks for the link, it worked perfectly.

Diesel1.

---

### Post by jocku on 2007-09-24
Hi,
I am getting mad... I can not seem to get this working! My computer freezes up every time I start gaim or firefox after i plugged my D-Link DWL-G122. This is when I'm using my usb 1.1 ports. When I try connecting it to the usb 2.0 ports i have on a PCI card, I can use the Internet for about 10 seconds (if I am lucky) and then it stops working!! Overall the D-link usb stick seems to start off better when I am plugging it in the usb 1.1 slots despite the fact that my computer crashes every time I connect it there .

Ideas anyone?? Could someone please help me!?

---

### Post by jocku on 2007-09-26
OK, I now have done everything from the scratch, and I noticed an error in the make command:


jocku@institutionen:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make clean
rm -rf *.o *~ .*.cmd *.ko *.mod.c .tmp_versions built-in.o
jocku@institutionen:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/jocku/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/jocku/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/jocku/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/jocku/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/jocku/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/home/jocku/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/jocku/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2
jocku@institutionen:~/RT73_Linux_STA_Drv1.0.3.6/Module$


Ideas anyone???

---

### Post by Rodrigue on 2007-12-14
I just had this error. 

You probably have a newer version of the kernel.  In the include file <linux/wireless.h>, it says

```
 * V20 to V21
 * ----------
 *	- Remove (struct net_device *)->get_wireless_stats()
```

You just need to comment that line on the rtmp_ main.c file and it should work.

At least, that is what I did when I had this error and the resulting driver works fine!

---

### Post by g99 on 2007-12-25
Hi!

I followed the guide and everything was perfect until Step 6-7. I dont know if I should use dynamic or static ip. I started with dynamic: I set my networkd essid and wireless-key but I get this from iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Then I tried what sammao's suggestion, but it's all the same. Perhaps I'm the one who does something wrong, but I cant figure out what it is. 
Any ideas?

---

