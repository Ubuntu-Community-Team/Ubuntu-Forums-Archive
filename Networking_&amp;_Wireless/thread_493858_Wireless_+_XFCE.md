---
title: "Wireless + XFCE"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by i386DX on 2007-07-06
On my laptop I installed Ubuntu 7.04 and XFCE (not XUbuntu, just plain XFCE after a server-installation). 
My wireless networkcard is a Ralink RT2561/RT61 which seem to work.

First I tried to install Network-manager (removed entries in /etc/network/interfaces).
My homenetwork was detected, but i couldn't connect to it. Because my accesspoint doesn't have a DHCP-server I need to set-up static IP-adresses. In Gnome there's 'network-admin', but XFCE doesn't have anything like that.
When I choose 'manual configuration' in the NetworkManager-applet he asks my password, but then nothing happens.

Then I tried Wifi-radar. Also this program detects my network, but there's no possibility to connect to it (can't set ip and WEP-key). 
When I choose 'new' I can setup all those things, but than I can't give it the right networkname because it already exists.


How can I connect to a wireless network in XFCE?
I must be able to manual configure a WEP-key and static IP-address.

---

### Post by kevdog on 2007-07-06
Id upgrade the driver to the latest -- known as serialmonkey rt61 drivers.  They can be found here: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

I would also use this thread as a guide:
[http://82.211.81.186/showthread.php?t=400236&highlight=serialmonkey](http://82.211.81.186/showthread.php?t=400236&highlight=serialmonkey)

Although the above thread is for rt73 serialmonkey drivers, I think if you just substitute 61 for most of the steps 73 is listed it will work.

---

### Post by walkerk on 2007-07-06
remove network-manager and install [wicd]("http://wicd.sourceforge.net").. i find it works much better than network manager\

also, with wifi-radar you need to click the arrows w/in the profile for more options. you can enter your WEP key and a static ip.. but wicd does this better.

---

### Post by kevdog on 2007-07-06
Network manager doesnt work with ra cards anyway.  I dont know if wicd and ra cards have a conflict.

---

### Post by walkerk on 2007-07-06
> **kevdog said:**
> Network manager doesnt work with ra cards anyway.  I dont know if wicd and ra cards have a conflict.

i would give it a look.. i haven't heard of anyone being displeased with it.

---

### Post by imdano on 2007-07-06
Wicd shouldn't conflict with any particular cards, because it just uses built in linux tools (ifconfig, iwconfig, iwlist, etc) to manage things.  So unless your card conflicts with Linux in general wicd shouldn't have a problem (at least not because of the type of card you have, though something else could certainly get screwed up).

---

### Post by i386DX on 2007-07-06
I now installed WiCD and manually filled my IP (192.168.0.11), netmask (255.255.255.0), gateway (192.168.0.1) and DNS (also 192.168.0.1). Selected WEP as encryption and inserted the right key.
Now it hangs on 'Setting up static DNS-server' (or something like that, I translated from Dutch version).


I also tried KWifimanager (in KDE). This tool also detects my network. I can give my WEP-key and I'm able to make a connection. However, it expects DHCP so it doesn't find an IP.
When I give afterwards manually an ip (sudo ifconfig ra0 192.168.0.11), the network doens't work. (can't ping). However, everything seem to be in order.

---

### Post by walkerk on 2007-07-06
> **i386DX said:**
> I now installed WiCD and manually filled my IP (192.168.0.11), netmask (255.255.255.0), gateway (192.168.0.1) and DNS (also 192.168.0.1). Selected WEP as encryption and inserted the right key.
Now it hangs on 'Setting up static DNS-server' (or something like that, I translated from Dutch version).


I also tried KWifimanager (in KDE). This tool also detects my network. I can give my WEP-key and I'm able to make a connection. However, it expects DHCP so it doesn't find an IP.
When I give afterwards manually an ip (sudo ifconfig ra0 192.168.0.11), the network doens't work. (can't ping). However, everything seem to be in order.

try to see if wicd will connect using dhcp. (make sure to enable it on your router)

troubleshoot..

---

### Post by dolphin_oracle on 2007-07-06
are you connecting via  a wireless router or an wireless access point (not the same thing).  You mentioned not having a dhcp server, which leads me to think you are using an access point.  I'm curious what device the gateway and dns you specified is (192.168.0.1).  That will need to be a router or a computer acting as a router/gateway for this to work.

If your access point is plugged directly into a dsl/cable modem, then the DNS will be that supplied by the ISP.

Please let me know if i'm off base.

Also, i'm using a rt61 based card on xubuntu, and I needed to install the firmware files (downloadable from ralink's website) and put them in a directory specified inthe readme that comes with the files.  This was with dapper and edgy though...don't know about feisty.  I think the directory was /etc/Wireless/RT61STA (capitalization sensitive).

---

### Post by CDiablo on 2007-07-06
Is there anyway to get a network monitor in wicd? The program got my wireless working but I would like the 4 bars monitor. Thanks

---

### Post by imdano on 2007-07-07
Yeah there's a tray icon you can use.  If you're using 1.3.0 (you should probably use this version, even though 1.2.7 is listed as stable most find 1.3.0 works a lot better) it's /opt/wicd/tray.py, and earlier versions use /opt/wicd/tray-edgy.py.  Go to System->Preferences->Sessions and add it to automatic startup.

---

### Post by i386DX on 2007-07-08
> **dolphin_oracle said:**
> are you connecting via  a wireless router or an wireless access point (not the same thing).  You mentioned not having a dhcp server, which leads me to think you are using an access point.  I'm curious what device the gateway and dns you specified is (192.168.0.1).  That will need to be a router or a computer acting as a router/gateway for this to work.

If your access point is plugged directly into a dsl/cable modem, then the DNS will be that supplied by the ISP.

Please let me know if i'm off base.

Also, i'm using a rt61 based card on xubuntu, and I needed to install the firmware files (downloadable from ralink's website) and put them in a directory specified inthe readme that comes with the files.  This was with dapper and edgy though...don't know about feisty.  I think the directory was /etc/Wireless/RT61STA (capitalization sensitive).


My home-network looks like this:


Cable-modem -> Windows 2000 with ICS -> switch/AP -> wired PC1 (ubuntu), wireless PC2 (windows), wireless laptop (ubuntu)
The switch/AP is in fact a wireless-router, but I don't use the router-capabilities
I know I could replace the Windows2000-PC with ICS with the router, but I first want to try it this way...

In Dapper and Edgy it was indeed necessary to install the firmware-files, but in Feisty the card is detected out of the box...

---

### Post by dolphin_oracle on 2007-07-08
> **i386DX said:**
> My home-network looks like this:


Cable-modem -> Windows 2000 with ICS -> switch/AP -> wired PC1 (ubuntu), wireless PC2 (windows), wireless laptop (ubuntu)
The switch/AP is in fact a wireless-router, but I don't use the router-capabilities
I know I could replace the Windows2000-PC with ICS with the router, but I first want to try it this way...

In Dapper and Edgy it was indeed necessary to install the firmware-files, but in Feisty the card is detected out of the box...


I'm not exactly sure about the ICS setup but I think that your WIN2000 box is acting as the gateway.  Have you tried specifying that machines IP address as the gateway/DNS server.  I think the IP you specified earlier sounds like the default IP of the router/AP.  Perhaps the two are in conflict.

---

### Post by i386DX on 2007-07-08
Yes, this is what I do. 
I changed the IP of the AP to 192.168.0.2 so there's no conflict.

---

### Post by imdano on 2007-07-08
If you only enter one address into the static DNS boxes in wicd it hangs (we'll be fixing that in the next release).  Enter the same address into both box 1 and box 2 and see if it connects then.

---

### Post by i386DX on 2007-07-09
It seem there is something wrong with the encryption-setting. When I disable the encryption on the AP everything works as it should be...

---

### Post by dolphin_oracle on 2007-07-09
I believe with the rt61 you need to specify the WEP key as a hexadecimal, which you probably know but I mention for those that may be reading.

---

### Post by i386DX on 2007-07-10
When I enter manually the encryption-key (sudo iwconfig ra0 key s: xxxxxx) then everything works, so probably there's a problem in the GUI-tools. (don't know if the same happens when I use a hex-key).

---

### Post by imdano on 2007-07-10
Were you entering your hex key or your ascii key into wicd?

edit: I think that wicd expects a hex-key to be entered if you're using WEP, although I've heard that putting double quotes around the ascii key works as well.

---

