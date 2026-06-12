---
title: "trouble with netgear wg111v2"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by bns on 2006-12-05
I'm trying to use Dapper on a Thinkpad A20m.  Right now it is in live-cd mode, but if I can get wireless working I'll install it.  Dapper recognizes my usb wireless device but I can't connect to the router.  I have successfully connected with the same computer and wireless device under winxp, but I want to use ubuntu.  If anyone knows how to make this thing work, I will be eternally grateful.

---

### Post by FrodoB on 2006-12-07
Have you tried to configure it using the GUI:

System -> Administration -> Networking

If you are using WEP or no security it should work for you.

---

### Post by bns on 2006-12-07
Yes I have tried configuring it with the gui.  I'm using no security and I think it *should* work too, but it doesn't.

---

### Post by FrodoB on 2006-12-07
Several folks have been able to get it going using the ndiswrapper. It might work for you as well.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Here are detailed instructions for a different device, so you will obviously use a different NDIS .inf file for yours, but the first part will get you going:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by bns on 2006-12-10
I tried ndiswrapper.  I think I followed the instructions found at those links correctly.  The driver seems to be associated with the device, but I can't see my router.  It's really confusing me.

---

### Post by ltcolfury on 2006-12-10
> **bns said:**
> I tried ndiswrapper.  I think I followed the instructions found at those links correctly.  The driver seems to be associated with the device, but I can't see my router.  It's really confusing me.

I use Ndiswrapper with the exact card you are using. Perhaps I may be able to help you.

I installed Ndiswrapper, then installed the driver for the Netgear card. I turned off my WEP and enabled my SSID on my router. (It's easier to it that way while configuring.) 

I then configured the card in System/Administration/Networking. (I used WLAN0) After that I opened up the Networking icon in the tray. (In Gnome, I use my the bar at the top.) I then clicked on the drop down menu associated with the wireless device. Mine was using ETH0. I chose WLAN0, After that I pinged my router, pinged a web address and it found my router. I then turned my WEP back on, entered my WEP key, made sure I was still connected, then disabled my SSID.

To put Ndiswrapper on startup, I used this page as a guideline because I just came from using Suse and Ubuntu was different.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

I sure hope you are able to get it working. If what I suggested doesn't work, post back and I will gladly assist in some troubleshooting for you.

---

### Post by bns on 2006-12-10
Okay this is new.  I did what you suggested, i.e. I did a fresh install of kubuntu 6.10.  Then I installed ndiswrapper and the driver from my netgear cd following the instructions from ndiswrapper.sourceforge.net   Now I still don't see MY router, but I do see a different network that isn't mine.  So maybe I need to change the settings on my router...

---

### Post by bns on 2006-12-10
Alright.  I can't figure this out.  I'm using a netgear wgr614v6 router.  I don't know what the problem is, but at least my usb adapter is doing something.  Thanks for the help so far guys.

---

### Post by FrodoB on 2006-12-11
You have a good sign there. 

You do need to look at the wireless router configuration, this is often a problem at this point.

The wireless adapter is also a problematic one as well.

I had to return a Netgear wireless router because it would work with my wireless devices that used native drivers, but not my laptop which uses ndiswrapper with a bcm4311 wireless chipset. 

If you could borrow a Linksys or D-Link router, or any other brand except Netgear, if you don't have any luck with the Netgear you might be able to debug the WG111v2 at any rate.

Keep us informed on what you find.

---

### Post by bns on 2006-12-11
I took it to school and it connected to the network there.  I googled my router and apparently a lot of people have had trouble out of it.  I'm gonna keep trying and I'll post back if I have anything new.

---

### Post by bns on 2006-12-12
Alright, I tried the native driver again and it worked.  I don't know what I did wrong the first time.  I can now see my router.  Unfortunately I cannot connect.  Probably just because I don't know what I'm doing.  The gui is just not working for me, but I was able to find my network with iwlist and iwconfig shows that I am associated with my network.  But I can't do anything else.  If anyone can help me that would be great.

---

### Post by FrodoB on 2006-12-12
Using the Text Editor (gedit) we need to modify the interfaces file to get the device started correctly:

sudo gedit /etc/network/interfaces 

Dynamic Address Assignment using DHCP: Add this data at the end of the file for a DHCP setup: (Choose one key type, either hex or ASCII, but not both, uncomment one, and fill in your key.)


iface wlan0 inet dhcp
wireless-essid MY_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto wlan0

Set the WEP keys as in the above examples. Hexidecimal format is preferred, but there is an example for ASCII keys which must preceded by s:

Save the file.

use ifdown and ifup to control the device:

sudo ifdown wlan0

sudo ifup wlan0

---

### Post by bns on 2006-12-12
I did exactly that.  I get "no DHCPOFFERS received"

---

### Post by FrodoB on 2006-12-12
Back to your router though, correct? 

Have you tested your new driver at school as you did before? 

If not do so and post the results.

Also try the iwlist command at each location:

 iwlist wlan0 scanning

You hope to see somethng like this:

wlan1     Scan completed :
          Cell 01 - Address: 00:70:3c:E4:50:14
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality:88  Signal level:0  Noise level:22
                    Extra: Last beacon: 9ms ago


Also, be aware that one of two of these things only worked on ndiswrapper and not the native drivers, but check the native drivers in where you got good results before for comparison.

Check your router's security carefully, all I have to do to duplicate your results here is to have an invalid ESSID or WEP key.

What does your interfaces file look like now?

---

### Post by bns on 2006-12-12
I have not tried the native driver at school.  I won't be going today, but maybe in the next couple of days I can try.

iwlist wlan0 scanning gives:

Scan completed :
Cell 01 - Address 00:18:4D:4A:A8:D8
ESSID:"STEPHENS"
Protocol:IEEE 802.11bg
Mode:Master
Channel:11
Encryption key:off
Bit Rates:54Mb/s
Extra Rates:1 2 5.5 6 9 11 12 18 24 38 48 54
Quality:25 Signal level:0 Noise level:30
Extra: Last Beacon:0ms ago

Interfaces file:

iface wlan0 inet dhcp
wireless-essid STEPHENS
auto wlan0

---

### Post by skinny on 2006-12-12
Have you guys got the Netgear working with WPA-PSK networks? I've got my wireless usb dongle set up fine (I think, I mean I can see the network I want to connect to and I know its a WPA-PSK encrypted one) but I just can't connect. Where do I enter the key? :-k 

$

---

### Post by FrodoB on 2006-12-12
Go to your router and experiment with the preamble, if it is short make it long. 
 
You could try short if it is long, but I think that long is preferred in most cases.

---

### Post by FrodoB on 2006-12-12
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

---

