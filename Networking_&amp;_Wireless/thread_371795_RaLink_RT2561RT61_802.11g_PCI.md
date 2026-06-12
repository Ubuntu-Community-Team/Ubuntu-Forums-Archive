---
title: "RaLink RT2561/RT61 802.11g PCI"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by gareth41 on 2007-02-27
i have a:

RaLink RT2561/RT61 802.11g PCI

that is what shows up from lspci.

i cant get the internet to work, in the networking dialog i have wmaster0 and wlan0, it says these are both enabled (i endabled them) after searching the forums it seems i have to get the latest drivers for the card, and compile them etc, or maybe i have to not use network settings (im on xubuntu), or maybe something else, is there not a simple way to get the internet using this card, i got it because i thought there would be.

i am using xubuntu 6.10

---

### Post by K.Mandla on 2007-02-27
I used to have a Linksys WMP54G v4.1 which had an RT61 chipset. I don't know if you have an Nvidia video card or not, but [this]("http://kmandla.wordpress.com/2006/12/17/ralink-rt61-edgy-and-nvidia-again/") is the way it worked for me. If you don't have an Nvidia card, you probably won't need to work so hard at it. 

Search around the forums, too. There is a howto or two about RT61 cards that might help.

---

### Post by tictacman on 2007-02-27
I have managed to get an edimax card which has rt61 chip working with xubuntu.  Most frustrating for me is that 6.10 shipped with a bad driver.  I followed this guide and it managed to get it working.

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

I did have some difficulty following the guide to get wpa encryption working though.  Instead I used another guide:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136).

Good luck

---

### Post by gareth41 on 2007-03-01
ok, i tried installing ubuntu 6.10 over xubuntu, this gave me the ra0 in the network manager, so i activated it - this had a progress bar that took ~3 minutes to complete. Now when i boot into ubuntu it hangs on configuring the network, what is it doing that is taking so long? Is there no timeout? how can i fix it?

the card works fine in windows.

---

### Post by tictacman on 2007-03-01
Are you running wpa on your card?  

For me xubuntu loads up quickly, but I did have some problems getting wpa_supplicant to work. I had to manually bring the card down and then restart it once I logged in, in  order to get it to work.  In the end I created a simple script with a delay to do this for me automatically on boot, and its been running great ever since.

---

### Post by gareth41 on 2007-03-01
there is no security on my router, apart from mac filtering. I cant boot into ubuntu at all tho...

---

### Post by raymac46 on 2007-03-01
I had a similar situation with an RT73 setup and had to blacklist some competing drivers before I could install the right one. Check this out.
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by tictacman on 2007-03-01
Must be something to do with the way the card is setup if there's no security.  I'm sure if you post the output from ifconfig and /etc/network/interfaces someone will be able to spot what's going on.  

I thought it might be useful if I posted my working configuration as a comparison.  Here it is:

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
essid NETWORKNAME

(I don't need wired connection so there's no eth0)

ifconfig:


sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:0F:E0:3D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:333099 (325.2 KiB)  TX bytes:333099 (325.2 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:9D:62:C7  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:691050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:6939 txqueuelen:1000 
          RX bytes:799996408 (762.9 MiB)  TX bytes:27228209 (25.9 MiB)
          Interrupt:193

---

### Post by whayong on 2007-03-02
Here's my post from last night taken from this thread:
[http://www.ubuntuforums.org/showthread.php?t=296822&page=25&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=296822&page=25&highlight=wpa)

> That actually didn't work, but guess who's posting this wirelessly? Woooohoooooo!

Here's what I did:

I followed this how to:
[https://help.ubuntu.com/community/Wi...cs%2FDriver%29](https://help.ubuntu.com/community/Wi...cs%2FDriver%29)
which to my knowledge is the same as this how to.

When i got to the part of blacklisting, I had some problems so I used nautilus and went to /etc/modprobe.d/blacklist and addedd "blacklist rt61pci" (without the quotation marks) to the last line and followed the rest of the how to.

For the record, my wireless card is a MSI MP54G5 mPCI card. lspci lists it as RaLink RT2561/RT61 rev B 802.11g.

This is on a Vaio PCG-SRX77 laptop 20 GB HD 384 MB RAM. Ubuntu 6.10

I hope this info will be usefull to others just as this how to was usefull to me. It only took me 1 month and 6 fresh installs to get the wireless working. lol!

Thanks to the great people on this forum and to the OP for the help.


Hope that helps.  I know it sucks when people point you to other threads, but really, the info is there, and the patience is KEY!

---

### Post by gareth41 on 2007-03-02
thanks for suggesting those idea, but as i said, i cant boot into ubuntu (i also tried recovery mode), it just hangs on "configuring hardware interfaces..." or "loading hardware drivers...", what can i do?

---

### Post by tictacman on 2007-03-02
Is it definately the card that's stopping you from booting?  What happens if you take the card out?

Also you can at least access and edit the /etc/network/interface and any other file by booting with the cd that you installed from.  Always a good idea to backup any configuration file before editing :)

---

