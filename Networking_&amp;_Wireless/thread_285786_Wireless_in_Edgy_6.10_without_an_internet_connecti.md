---
title: "Wireless in Edgy 6.10 without an internet connection"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Bealer on 2006-10-27
I need to setup wireless in 6.10, but don't have a wired connection. With purely what comes on the disc, can someone give me some pointers for setting it up?

I followed a guide ([http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)) before, whereby I generated a WPA SK, then added this to my wpa_supplicant.conf. I then set wpa_supplicant to initialise during startup.

So my wpa_supplicant.conf looks like:

```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="GUnit"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=b22ec921c254c73f99b31b76ff876692ecde36839a1f2d92150829e6afcb5515

```

and my network interfaces file has the following below my wireless adapter's section

```

iface wlan0 inet static
address 10.0.0.10
netmask 255.255.255.0
wireless-essid my_essid
gateway 10.0.0.1
pre-up wpa_supplicant -Bw -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

Couple of things that confused me though. Under Networking in the admin GUI, I seem to have two wireless devices. wlan0 and (can't remember what it's called exactly) wlanmaster?? I've only got one wireless device, unless it's my bluetooth adapter.

I'm using a Gigabyte GN-WP01GS ([http://www.gigabyte.com.tw/Products/Communication/Products_Spec.aspx?ProductID=970](http://www.gigabyte.com.tw/Products/Communication/Products_Spec.aspx?ProductID=970))

Also, is the "wext" part correct? What can I enter to find out what the correct driver for my card is.

Is there anything else I can do without having an internet connection? Shame Network Manager isn't included.

---

### Post by Bealer on 2006-10-27
anyone?

---

### Post by chupacabrah on 2006-11-15
I'm having the same problem...](*,) ](*,) 

did you find a solution??

This is my first time attempting wireless with linux, and I'm pretty new to the whole thing...

any help appreciated!

---

### Post by chupacabrah on 2006-11-15
I've done a ton of searching, but I can't really find anything to fix what's going on here....

Right now I'm usuing my ethernet cable from my other computer, but I need to get the wireless working.

I used ndis, and installed the windows driver

I've tried to configure.

my router (belkin) uses a WEP 128bit code....  if that matters.
don't i just enter that in the configure for the networking?

then...I have wired connections.... wlan0, and then wmaster0

DHCP

and...I'm using this wireless card:
 GIGABYTE GN-WP01GS IEEE 802.11b/g PCI Wireless Adapter up to 54Mbps Data Rates 64/128 bit WEP, WPA, WPA2, TKIP, 802.11i 

What else can i do to get this thing to work?

where should I start?

---

### Post by chupacabrah on 2006-11-16
help? :confused:

---

### Post by somerandomnerd on 2006-11-16
Having a very similar problem here- no internet connection other than wireless, can't connect to repositories so any software has to be transferred via a USB stick until I can get a wireless connection...

System-administration-Networking seems to see that there is a wifi card, which I understand indicates that the driver is present. But it doesn't seem able to connect to anything.

A bit of googling got me to a page saying that if the connection shows up but doesn't work, then the firmware might not be present. So I ran "lspci" in the Terminal, found that I've got an Intel 2200BG network connection- I then found a website with the drivers and firmware, downloaded them, transferred them across... then found that the files appear to already be there in my /lib/firmware/2.6.17-10-generic folder. :confused:

---

### Post by somerandomnerd on 2006-11-18
Well, I seem to be doing better than I though- I've discovered the command "iwlist scanning", which reveals that actually my card is working fine, and detects my wireless network.

Now, how do I actually connect to it? I've set the ESSID and Network Password in Network Settings, but it doesn't seem to have any effect. Is there some sort of "connect" command that I'm missing?

---

### Post by chupacabrah on 2006-12-15
> **somerandomnerd said:**
> Well, I seem to be doing better than I though- I've discovered the command "iwlist scanning", which reveals that actually my card is working fine, and detects my wireless network.

Now, how do I actually connect to it? I've set the ESSID and Network Password in Network Settings, but it doesn't seem to have any effect. Is there some sort of "connect" command that I'm missing?


sudo ifdown eth0 
--that turns off ethernet.


sudo ifup ra0
--substitute your wlan connection name for ra0. wlan0, maybe?


then, what i have to do is this:


sudo iwconfig key <mykey>
sudo iwconfig essid <myssid>

after that, it's all configured, and I just have to wait ~5 minutes or so, and i'm online!

try 
route -n  

to see if you can see the gateway and all that good stuff.

try this link, too:
[http://justlinux.com/forum/showthread.php?t=147582](http://justlinux.com/forum/showthread.php?t=147582)

that was where i figured out what was going on, and the problems i had/still have.

---

