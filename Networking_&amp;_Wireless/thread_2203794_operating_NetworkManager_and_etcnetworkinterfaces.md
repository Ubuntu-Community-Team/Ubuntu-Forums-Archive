---
title: "operating NetworkManager and /etc/network/interfaces"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by a.m.wink on 2014-02-05
When I installed (k)Ubuntu on my work laptop it was connected to the internet with an all-fixed (IP address, hostnames, etc) setup.
After a few upgrades, and lately an overhaul of the networks at work, I don't seem to provide the correct settings any more.

The new network is DHCP, and there is a wireless connection that I tried to get working in NetworkManager (after failing setting it upwith /etc/network/interfaces -- The wireless security is called MSchapV2)

After trying loads of things I seem to have mangled NetworkManager, or /etc/network/interfaces, or both.

The symptom: every time when it starts up, the machine waits with two messages: 'waiting for network configuration', followed by 'waiting another 60s for network configuration' and then it boots without network.

The NetworkManager tooltip says 'eth0 -- connected to ifupdown' but is not connected. If I log in as root and do 'ifdown -a && ifup -a' then the wired connection works.
The wireless connection appears when I open the widget -- it is listed as a wired connection called wlan0 -- but I cannot save any settings to make it work.
The NetworkManager documentation says to comment both wired and wireless interfaces, but when I do that I cannot get any internet access.

Does anyone know a way to set up NetworkManager more or less from scratch, given a previous configuration via /etc/network/interfaces?

I thought about deleting & purging all settings and programs for wireless, wired and DHCP networking. I guess I would need to download the packages for installing afterwards before doing that though.

Many thanks for any suggestions/pointers!
Best wishes, Alle Meije 

My current /etc/network/interfaces says:
#
auto lo
iface lo inet loopback
#
#cards below managed by networkmanager
#
auto eth0
iface eth0 inet dhcp
#
auto wlan0
iface wlan0 inet dhcp

The manual for my work wireless says that it needs this -- I don't know a place / file to put all this wizardry.
--> the SSID of the network [EMAIL="user@domain.tld"]user@domain.tld[/EMAIL]
--> username
--> password
--> network verification: WPA2
--> data encryption: AES
--> EAP-type: PEAP
--> tick 'verify server certificate'
--> use 'GTE CyberTrust Global Root'
--> verification method: EAP-MSCHAP v2

---

### Post by varunendra on 2014-02-06
> **a.m.wink said:**
> The manual for my work wireless says that it needs this -- I don't know a place / file to put all this wizardry.
--> the SSID of the network [COLOR="#FF0000"]**user@domain.tld**[/COLOR]
--> username
--> password
--> network verification: WPA2
--> data encryption: AES
--> EAP-type: PEAP
--> tick 'verify server certificate'
--> use 'GTE CyberTrust Global Root'
--> verification method: EAP-MSCHAP v2
(I think the "user@domain.ltd" needs to go into the username field, as SSID is the name of network and is universal for all users of that network)

All this wizardry goes into Network Manager settings, as shown in the image below -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=250150&stc=1&d=1391741101[/IMG]

The SSID goes to the "SSID" field under the first tab ("Wireless").

But by default, you won't be able to save these changes until your /etc/network/interfaces file has entries regarding wlan0. So, you need to open your 'interfaces' file with root access (to be able to edit it), and remove all but first two lines so that it looks like -
```
auto lo
iface lo inet loopback
```

To open it with root access, use "gksu" (if running Ubuntu 12.04) or "sudo" (if on 13.04 or later) with your text editor. For example, if your are running default Ubuntu 12.04, your text editor would be "Gedit". Then the command to open the 'interfaces' file with root access would be -
```
gksu gedit /etc/network/interfaces
```
Remove the unwanted lines, proofread, save and close the file.

Then open Network Manager and save the settings in it as shown in the above image. The "**GTE CyberTrust Global Root.pem**" file (for "Ca Certificate" field) can be found in "**/etc/ssl/certs/**" or "**/usr/share/ca-certificates/mozilla/**" directory. Click the folder icon beside the field to browse to it.

---

### Post by a.m.wink on 2014-02-11
I think that did the trick! Not sure what it was that I haven't tried before (feels like I've tried all possible settings at least twice) but huge thanks!
This is also a good link [https://wiki.debian.org/NetworkManager](https://wiki.debian.org/NetworkManager)

---

### Post by varunendra on 2014-02-12
You're welcome!

And Thanks for the wiki link, it indeed appears to be good, I just bookmarked it. :)

---

