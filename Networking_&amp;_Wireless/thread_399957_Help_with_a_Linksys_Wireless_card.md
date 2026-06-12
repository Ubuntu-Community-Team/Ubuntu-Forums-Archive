---
title: "Help with a Linksys Wireless card"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by renmaxuo on 2007-04-02
I'm running the latest Ubuntu Live CD, WindowsXP is installed on my machine.

The hardware list says that Linksys WMP54G works out of the box, but I'm having a problem with it.  I tried using the Networking admin tool in Gnome, where it lists wlan0 and wmaster0 as separate wireless cards.  I enabled wlan0 and entered the ssid (home) and the network key.  Then it enables it, but I can't do anything.

I tried the following:

iwlist wlan0 scan 

no scan results

sudo iwconfig wlan0 essid home
sudo dhclient wlan0

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

It did that several times, then ended with:

No DHCPOFFERS recieved.

Can someone help me to get this card working?  Thanks.

---

### Post by chili555 on 2007-04-03
Is the network key WEP or WPA? Hex or ASCII? I have sometimes seen scanning take a few tries to get a result, so try again. Make sure the ESSID is home and not Home. One will not connect to the other. You may also have luck telling iwconfig which access point you want to connect to. Here is my scan result, slightly disguised and abbreviated:```
 Cell 01 - Address: 88:13:18:62:8D:F7
                    ESSID:"GBR1"
                    Protocol:IEEE 802.11bg
```I would then try :```
sudo iwconfig wlan0 ap 88:13:18:62:8D:F7
sudo iwconfig wlan0 key xxxxxxxxxx
sudo dhclient wlan0
```Post back and let us know.

---

### Post by renmaxuo on 2007-04-03
The key is WPA, but how do I know if it's hex or ascii?

"home" is correct.

I tried the iwlist lan0 scan about 30 times just now, I got "No scan results" each time.

I didn't get a message when I entered:

sudo iwconfig wlan0 ap (my address)

However, I received an error message when trying this one:

sudo iwconfig lan0 key xxxxxxxx

Error for wireless request "Set Encode" (8B2A): Invalid argument "key".

---

### Post by MeeMaw on 2007-04-03
> **renmaxuo said:**
> The key is WPA, but how do I know if it's hex or ascii?

"home" is correct.

I tried the iwlist lan0 scan about 30 times just now, I got "No scan results" each time.

I didn't get a message when I entered:

sudo iwconfig wlan0 ap (my address)

However, I received an error message when trying this one:

sudo iwconfig lan0 key xxxxxxxx

Error for wireless request "Set Encode" (8B2A): Invalid argument "key".

Probably because you typed "sudo iwconfig lan0 key xxxxxxxx"
instead of "sudo iwconfig **w**lan0 key xxxxxxxx"
Keep putting in the settings, I'm sure you will get it!!!!

(Howdy, Chili555!!!)

---

### Post by renmaxuo on 2007-04-03
Oops, that was a typo!  I did use wlan instead of lan in the actual console.  I have to retype what happens in the console because I have nowhere to save the file (I'm guessing linux can't read NTFS partitions on my external drive?)

---

### Post by chili555 on 2007-04-04
First, linux *can* read ntfs files, with ntfs support installed, but that's a different forum! Second, iwconfig assumes 'key' is WEP, not WPA. You will also need WPA support installed and configured. See: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539).

Third, hi Sis! (MeeMaw)

---

### Post by RedPeasant on 2007-04-04
I was having a similar problem with my WMP54G. It says the drivers are built in, but I couldn't figure out how to get it working. I got the card running with other drivers yesterday. I am assuming that you're using the rt61 chipset card ( I think it's the WMP54g v4.0 or v4.1, not sure about older models).
Go into System -> Administration -> Software Sources in the menu and add Universe and Multiverse to the sources list, then launch Synaptec. Do a search for rt2500. Apparently the RT61 chipset is actually the same as the 2561. My Synaptec lists three packages: rt2500, rt2500-modules-...., and rt2500-source. I downloaded the source package, and the readme at /usr/share/doc/rt2500-source/README.Debian was very straightforward. They give you a manual way and a way that uses some module-assistant. Do the module-assistant way, it's easy. I think the assistant is a dependancy for the source package, so it should have gotten installed when you got the source. If it wasn't it's a dependancy for one of the other two rt2500 packages. Just follow that readme in the source package, and you should be good.

Sorry for the somewhat vague nature of this walkthrough, I wasn't trying to remember what I was doing when I did all this. Good luck.

---

### Post by a65bugman on 2007-04-05
So, I'm having the same problem with my WMP54g version 4.1 card.  The system sees the card but I am still unable to scan for networks.  I have followed the directions listed by RedPeasant and everything went with out a hitch.  Although after a reboot nothing seems to have changed.  I'm still unable to scan networks and the system still recognizes the card as a RT2561 card.  In the Networking portion it sees the card but says it is not configured.

Can anyone give step by step instructions on how they achieved this miracle?  It is quite frustrating that it says these cards are good to go out of the box but in reality that is far from it.  By the way I am on a brand new Ubuntu 6.10 box and am running Network Manager installed via Automatix2.

---

### Post by a65bugman on 2007-04-05
So when looking further into the system I found that under the Device manager and under the wireless card it lists an unknown device.  Could this be the issue?  Also when running sudo dhclient wlan0 this is the output I get:

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:39:14:41:4f
Sending on   LPF/wlan0/00:18:39:14:41:4f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any ideas?

---

### Post by MeeMaw on 2007-04-05
All of you may have different chipsets (Linksys used lots!!!) ....  the guys that know they have a RaLink chipset and need the RT61 or RT2561 drivers could get help from this post

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

and if you aren't sure, post us the output of     "sudo lspci"   (without the quotes)

Keep trying!!!


(Howdy again, Chili555!!!!)

---

