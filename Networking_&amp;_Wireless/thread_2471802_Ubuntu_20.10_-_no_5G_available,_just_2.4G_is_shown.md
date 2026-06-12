---
title: "Ubuntu 20.10 - no 5G available, just 2.4G is shown"
date: 2022-02-09
forum: Networking &amp; Wireless
---

### Post by azo2 on 2022-02-09
I installed 20.10 on Raspberry Pi 400 and just 2.4 G band is shown. The RPi OS can see both 2.4 & 5 GHz. Also, I have two more computers running Linux Mint and no issue. I search many forums but not real solutions.  Just one user solved the issue by running <sudo iwconfig wlo1 freq 5.7G>. The post is from 2018, and it was not helpful. I sent a private message to the user for follow up. If I run the command I get the following error: <Error for wireless request "Set Frequency" (8B04) : SET failed on device wlo1 ; No such device.>
Below is a view of the /etc/NetworkManager/system-connections/Asus_2.4.nmconnection. It does not show the Asus_5 corresponding to 5GHz band.
[connection]
id=Asus_2.4
uuid=068f3641-63e7-434a-9f57-cbffac2e72cd
type=wifi
interface-name=wlan0
permissions=

[wifi]
mac-address-blacklist=
mode=infrastructure
ssid=Asus_2.4

---

### Post by guiverc on 2022-02-10
Ubuntu 20.10 (*and all flavors*) is **end of life**.

See [https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)

It's upgrade path has gone too, as it *release-upgraded* to the next release which was [21.04 but it's already EOL]("https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/").

I'd suggest you start again with a *supported* release of Ubuntu.

---

### Post by mIk3_08 on 2022-02-10
> **azo2 said:**
> I installed 20.10 on Raspberry Pi 400 and just 2.4 G band is shown. The RPi OS can see both 2.4 & 5 GHz. Also, I have two more computers running Linux Mint and no issue. I search many forums but not real solutions.  Just one user solved the issue by running <sudo iwconfig wlo1 freq 5.7G>. The post is from 2018, and it was not helpful. I sent a private message to the user for follow up. If I run the command I get the following error: <Error for wireless request "Set Frequency" (8B04) : SET failed on device wlo1 ; No such device.>
Below is a view of the /etc/NetworkManager/system-connections/Asus_2.4.nmconnection. It does not show the Asus_5 corresponding to 5GHz band.
[connection]
id=Asus_2.4
uuid=068f3641-63e7-434a-9f57-cbffac2e72cd
type=wifi
interface-name=wlan0
permissions=

[wifi]
mac-address-blacklist=
mode=infrastructure
ssid=Asus_2.4

yeah. guiverc is right. you must have to install new supported released of Linux Ubuntu. I suggest you go with the long term support (LTS) you wont regret it. For more  release information of Linux Ubuntu you can just [click here]("https://wiki.ubuntu.com/Releases"). And c[lick here]("https://ubuntu.com/download") for the latest Linux Ubuntu Release download page. So Good Luck and cheers.

---

### Post by grahammechanical on 2022-02-10
Apart from the comments made above you may need to enter the router/hub setting utility and activate in some way the 5 GHZ band for it is most likely not broadcasting.

Regards

---

### Post by azo2 on 2022-02-10
Three days ago on Pi Imager were available two Desktop versions: 20.10 and 20.04 LTS. Now when I open it is just 21.10 and no LTS option. I installed 21.10 and same issue, only 2.4G band is available. But the main issue is that 21.10 is not stable. It froze during installation and I had to power it off. Alt+Sys+reisub did not work. After reboot I open Firefox and when I tried to log in to forum it froze again - matter of minutes. The old 20.10 did not froze at all for about three days. No issues, except the wifi 5G connection. Maybe 21.10 is prematurely declared compatible with RPI. 
I may have to wait until April when LTS will be released, or even more if it may need debugging. RPi OS is a Debian too and it is working well. I heard many exciting things about Ubuntu and I wanted to try it. 
Still I want to fix the 5G band to be ready for the future LTS version. I may encounter the the same issue.

Best Regards,

---

### Post by azo2 on 2022-02-10
If I understand correctly the router may have a setting for each connected device to turn on/off the bands? This is the only one device that cannot see the 5GHz band. I am not an expert in Routers, please give me, if possible, some details.

Best Regards,

---

### Post by grahammechanical on 2022-02-11
The router/hub should have come with a setup guide or some instructions. They should include: the router address (this will be a https:// type address); the router user name; the router password; the wireless key. This information is needed to setup the connection between the OS and the modem/router. We use a web browser to go to the router address and should be prompted to enter a user name (default may be admin) and the password. Then we will be in the modem/router's settings utility.

It is there that we set the internet address of the Internet Service Provider, our username and password. Also we can test the internet connection, disconnect it and connect it if it is not connected. Other information may be available. If you do not have a user guide you may be able to download one from the modem/router supplier and even access the settings utility from the supplier's website.

Regards

---

### Post by MAFoElffen on 2022-02-13
Your info in the right of your post does not say what country you are from but...
```

sudo vim /etc/default/crda 

```
Add the country code for you... Mine is "US".

5GHz WiFi is 'localized' to 'allowable' countries (or sometimes just defined.)

---

### Post by jeremy31 on 2022-02-13
Moved to Networking and wireless, please see the wireless script link in my signature and post results

---

### Post by MAFoElffen on 2022-02-14
A better explanation for the fix from Post #8... CRDA stands for the central regulatory domain agent and *is* relevant for choosing the permitted wireless channels for a given country. 

CRDA is not set by default. On Raspberry Pi 3, 4 & 400 wireless, if it see's 2.4 GHz and not 5 GHz networks, a common fix for that is to set the the CRDA...

That file I said to edit to add your Country Code to is /etc/default/crda:
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=

```
If you look in file /usr/share/zoneinfo/zone.tab, look at columns 3 & 4 to find your location, then use the two letter code from column 1 to set REGDOMAIN.

---

