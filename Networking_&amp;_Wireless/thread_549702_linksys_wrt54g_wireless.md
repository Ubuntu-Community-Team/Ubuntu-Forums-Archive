---
title: "linksys wrt54g wireless"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by InGunsWeTrust on 2007-09-12
This depresses me very much, MY WIRELESS ROUTER ONLY WORKS ON WINDOWS! AH! 

Basically the problem I have is that I can connect to it in Windows using a WPA shared key but in Ubuntu 7.04 I enter the key and it just doesn't go. I don't get an IP address or anything. I know it isn't a router configuration error because quite obviously it works on Windows XP. I was wondering actually if there was just a better network manager than the gnome network piece of junk. I never liked that thing and wouldn't feel bad completely scraping it.

---

### Post by kevdog on 2007-09-12
Youve got to provide more details about your wireless card and drivers.  Any router should work with ubuntu if configured (ubuntu) properly.  Network manager is another issue.  It is not causing your problems, although there are alternatives available.

---

### Post by InGunsWeTrust on 2007-09-13
My wireless drivers (ipw3945 restricted) are irrelevant because I know that they are not the problem. My school uses Cisco Clean Access to get you to log into your school account after you connect to their open network. So I can connect to an open network meaning that my drivers are just fine. I do however hate with a passion the interface provided by the gnome network manager so if I can get it to work with that it'd be fine but a whole different manager would be ideal.

Also you are right I should have provided more info: Terminal output suggests that the interface is brought up successfully and I do a DHCP request with no response.

---

### Post by wieman01 on 2007-09-13
> **InGunsWeTrust said:**
> My wireless drivers (ipw3945 restricted) are irrelevant because I know that they are not the problem. My school uses Cisco Clean Access to get you to log into your school account after you connect to their open network. So I can connect to an open network meaning that my drivers are just fine. I do however hate with a passion the interface provided by the gnome network manager so if I can get it to work with that it'd be fine but a whole different manager would be ideal.

Also you are right I should have provided more info: Terminal output suggests that the interface is brought up successfully and I do a DHCP request with no response.
What makes you think the driver is not an issue? It is, as some drivers do not support WPA out of the box. The router definitely works for any operating system, they rely on industry standards that alls operating system must comply with. So the only issue is that...

a. an insufficient driver (very likely)
b. you handled the Network Manager application incorrectly (which I don't believe).

Talking about your network back home, do you see a WPA option when you open network manager? Is DHCP really enabled (guess it is)? What is the output of:
> sudo iwlist scan
It is likely that the current ipw3945 does not support WPA. That's why we need to know if Network Manager gives you the option. Attaching a screenshot of Network Manager would certainly help.

---

### Post by noob12 on 2007-09-13
With the ipw3945 you need the wpasupplicant package installed.  Have you got that?

---

### Post by wieman01 on 2007-09-13
> **noob12 said:**
> With the ipw3945 you need the wpasupplicant package installed.  Have you got that?
Is it not installed by default? In 7.04 it should be the case.

---

### Post by InGunsWeTrust on 2007-09-13
Thank you for all of the great suggestions. Here is the requested info:

> ty@ty-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:70:58:F5:B1
                    ESSID:"wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-17 dBm  Noise level=-17 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 28ms ago

Yes wpasupplicant is installed

> ty@ty-laptop:~$ sudo apt-get install wpasupplicant 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I tried to install wpagui and upon running it I discovered that perhaps there is something wrong with my wpasupplicant even though it is installed

> ty@ty-laptop:~$ wpa_gui 
Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect


Also the screenshots requested is uploaded

Also DHCP is obviously enabled because I get DHCP through the wire on linux and I get DHCP wireless in windows

Edited for a better screenshot

---

### Post by wieman01 on 2007-09-13
Obviously your network is configured to use WPA as security protocol, not WEP seen on the screenshot:
> IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Extra: Last beacon: 28ms ago
Do you have a WPA option (together with TKIP) in the networking applet? If not then we need to replace the current wireless driver.

---

### Post by InGunsWeTrust on 2007-09-13
> **wieman01 said:**
> Obviously your network is configured to use WPA as security protocol, not WEP seen on the screenshot:

Do you have a WPA option (together with TKIP) in the networking applet? If not then we need to replace the current wireless driver.

Nope I only have Open and what is shown. I thought that WEP and WPA were parallel technologies based on about the same thing, just with more encryption.

---

### Post by wieman01 on 2007-09-13
> **InGunsWeTrust said:**
> Nope I only have Open and what is shown. I thought that WEP and WPA were parallel technologies based on about the same thing, just with more encryption.
No, WPA (with both TKIP and AES) and WEP are incompatible, that is what you are experiencing right now. I will try to find something concerning the driver. You either revert to WEP (router and PC) or you replace the current driver. Let us see what I can find.

---

### Post by InGunsWeTrust on 2007-09-13
Basically, I don't really want to use WEP because of how easy it is to crack and the key and I tried the link you have in your signature for WPA but I need to be able to roam so hard codding the network ID into a file like that would just be a nightmare. So basically a driver that is compatible with the nm-applet would be my only option. ipw3945 is getting to be as common as ipw2100 and ipw2200 so I find it unlikley that there isn't a driver for it.

---

### Post by noob12 on 2007-09-17
Based on the docs at ipw3945.sourceforge.net, it expects wpa_supplicant for the WPA functionality, so we would have to diagnose why that isn't working.  Try at least to make sure your wpa_supplicant process is running during the attempt to connect (use **ps -ef | grep wpa**).  You could also try a newer version of the ipw3945 driver built from there.  I haven't tried one of those builds, so not sure I could guide you but could try.  Also not sure it would do better.

You could also try building the iwlwifi  drivers for Feisty: [http://intellinuxwireless.org/index.php?p=iwlwifi](http://intellinuxwireless.org/index.php?p=iwlwifi)

You might also try wicd as a wireless connection manager; it might do better here.  [Note: For my part, I can say I have used NM with ndiswrapper and several other drivers (but not the ipw3945) requiring wpa_supplicant, and it has worked fine for me without any kind of tweaks.]

I think you'll find people on the forum with working ipw3945 and WPA setups, and a thread with that kind of title might help you dig them up (whereas the current thread title may not).

---

