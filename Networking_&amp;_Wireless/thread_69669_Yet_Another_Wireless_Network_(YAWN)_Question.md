---
title: "Yet Another Wireless Network (YAWN) Question"
date: 2005-09-27
forum: Networking &amp; Wireless
---

### Post by DeadEyes on 2005-09-27
Ok I think everything is set up so why can't I surf, ping any sites or my router. If I try to access my router from a browser I get "connection refused". Everything, of course, works in windows.

Any help or pointers would be great.

Here are some outputs from various cmds 
```

iwconfig wlan0

wlan0     IEEE 802.11g/b+  ESSID:"wssid286"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=49/100  Signal level=29/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

iwlist wlan0 scan

wlan0     Peers/Access-Points in range:
    00:0F:CC:2D:80:70 : Quality:49/100  Signal level:28/100  Noise level:0/100
    00:0F:B5:7C:75:70 : Quality:32/100  Signal level:5/100  Noise level:0/100

```
Does the above output mean that my wireless card can see two access points? The MAC Address of the first is the same as my routers, the other I assume is a neighbours.

this is my /etc/network/interfaces
is wireless-essid right are should they all be underscores?
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

auto wlan0
iface wlan0 inet dhcp
wireless-essid wssid286
wireless_mode Managed
wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxxx
wireless-defaultkey 1
wireless-keymode restricted

```

and finally if I perform an ifdown wlan0 and then a ifup wlan0 I get this
```

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:a0:c5:94:75:8d
Sending on   LPF/wlan0/00:a0:c5:94:75:8d
Sending on   Socket/fallback
**the ip here looks wrong should it not be my routers ip?**
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

If you've managed to wade through all that I thank you.

---

### Post by augereffect on 2005-09-27
I'm m having exactly the same problem.  I think my card is installed correctly, although the lights don't go on.  I think its just a matter of configuring things.

---

### Post by mlomker on 2005-09-27
It's clear from your iwconfig that it isn't taking the encryption key.  Are you using WEP or WPA?  The longer keys can be a pain and I've heard about issues inputing hex keys.

I found a sample interfaces that looks like this:

```

wireless-essid HHH
wireless-mode managed
wireless-keymode restricted
wireless-key 1234-5678-90

```

If you are using WPA then you should look at the wpa_supplicant package as it was designed to handle that.

---

### Post by DeadEyes on 2005-09-27
I'm using 128bit WEP, my key is 26 characters long but from what I can find in linux the key can only be up to 10 characters?
I guess my next step is to try and get it working with encryption turned off.
And then have a look into using WPA. Both my router and card support it and it is supposed to be better.

Thanks for your input mlomker.

---

### Post by mlomker on 2005-09-27
> I'm using 128bit WEP, my key is 26 characters long but from what I can find in linux the key can only be up to 10 characters?

I've read other threads about funkiness with the long hex WEP keys.  I've heard that prefacing the entry with an **s:** and using ASCII characters only is easier to get going.

You can use wpa_supplicant to input WEP keys.  The main purpose of the tool is to automatically search for access points in the background and set up the association rather than using iwconfig (those lines in /etc/network/interfaces are actually just sent to iwconfig in the background prior to the interface coming up).

---

### Post by XjFrank on 2005-09-27
I am having exactly this problem as well.  I wish this were easier, I mean I'm trying to get the federal agency I work at to let me deploy my next release on linux and I can't even get this dang network connection up and going.  

Anyone have any real clues, I don't have the option of changing the key, and it is a 26-character hex wep key.  I'm using a Belkin (Prism 1) card.  

My config file looks about identical to his above.  The piece that is missing, and has to even be configured in Windows in order to attach, is I'm not seeing the check-box equivelant for shared key mode.

Please, please get me up so I can get back to php-land and make some waves in my small part of the federal govt.

Thanks,
Frank

Ps - Nice distro, I snagged a copy of this because Fedora 4 locked the box up solid.  Including incompatible drivers that install on auto-detect for all ATI Radeon cards has to be the worst deployment screw-up I've seen in Linux yet.  And I have to wonder why it's becming more of a pain to install.  I've been around linux for ages, just not the last 3 years.  And up to FC3 I've been fine, Red Hat 9 was fine, all the way back to 4 was fine, Suse has always been fine, now I can't get two distros in a row to work out, one leaves me a frozen screen of doom, and this can't connect to the world.

---

### Post by mlomker on 2005-09-27
> Please, please get me up so I can get back to php-land and make some waves in my small part of the federal govt.


Is your problem with [wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant/") or a configuration without it?

---

### Post by XjFrank on 2005-09-27
I used the utility in the admin menu, and when that didn't work I dove into the interfaces file in etc.  I have never used wpa_supplicant before, nor really heard of it until this post.  Think it'll do the trick?
...frank

---

### Post by mlomker on 2005-09-27
> Think it'll do the trick?

It's the best thing going on debian systems right now (redhat has network manager).  If you have a laptop the combination of ifplugd/whereami/wpa_supplicant/resolvconf really rocks.

I don't use encryption, so my setup is a little easier.  [Here's a post]("http://www.ubuntuforums.org/showpost.php?p=368604&postcount=4") that I made about a simpler setup with ifplugd.

---

### Post by XjFrank on 2005-09-27
omg it works :)  needed one small part of his above that i noticed i dind't have.  so i'm guessing the keymode being 'restricted' is somewhat like clicking that checkbox in winblows.  and so it has begun... i'm erasing the raid drives and getting ready to toss oracle on this thing and bang away.

thanks very much for the rapid responses, i mean it, it's nice to not feel distant and alone in a small corner room in the basement entirely helpless.

wish me luck, i got the cd from another linux-evangelist at the patent and trademark office, and my system needs to get out from under iPlanet (I inherited the system, that wan't my choice :rolleyes: ).  

...frank

now to get apache 2 and php 5.0.5 loaded while oracle downloads.  here goes my first shot on a debian-based box.  I've heard alot about this part and it's the main reason i'm on it, I'm tired of installing everything over each time a new version comes out.

---

### Post by DeadEyes on 2005-11-22
I know I shouldn't be dragging up this old post, but I'm sooo happy I'm finally on the Internet with Linux.
I installed v5.10 and everything just worked well nearly. From the installation all looked good, but when I tried firefox it just timed out. However if I browsed using an IP address it worked so in about:config I disabled IPv6 and Firefox works perfect.
BTW my wireless card is ZyXEL G-360 PCI

---

