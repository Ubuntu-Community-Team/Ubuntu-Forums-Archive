---
title: "Wireless Connection, SET ESSID Invalid arguement"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by battousai567 on 2007-02-25
I'm very new to Linux, only had it for 2 days.  I'm using Ubuntu 6.10 and finally got my Linksys wireless card installed with the drivers but I'm having trouble connecting to networks.

Every time I try to input a ESSID it says....

```
battousai567@battousai567:~$ sudo iwconfig wlan0 essid west
Password:
Error for wireless request "Set ESSID" (8B1A) "
   SET failed on device wlan0 ; Invalid argument.
```

When I use iwlist on my wireless connection it finds about 7 different wireless networks nearby (I'm on college campus) and no matter what essid I use it gives me the "Invalid argument".

If it helps, my iwconfig is...

```
IEEE 802.11g  ESSID:off/any
Mode:Managed    Frequency:2.462 GHz   Access Point: Not-Associated
Bit Rate: 1 Mb/s
RTS thr:2347 B   Fragment thr:2346 B
Power Management:off
Link Quality:0   Signal level:0   Noise level:0
Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
Tx excessive retries:0   Invalid misc:0 Missed beacon:0
```

Any help would be appreciated.

---

### Post by gradedcheese on 2007-02-25
what chipset and driver are you using?  it looks like a driver problem (iwconfig sends standard requests to the driver, which then either is able to issue them to the chipset or not)

---

### Post by battousai567 on 2007-02-25
I'm using the Linksys WPC54G ver 4 wireless card.  lspci says it's...

Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

I guess thats what your asking for, I don't know where to find the chipset.

I'm using the driver WPC54Gv4_dr that I downloaded off their website for this card.  It's the file at the top of this page [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&displaypage=download#versiondetail)

Do you think taking the driver directly from the CD that came with the card would be better or wouldn't help?

---

### Post by gradedcheese on 2007-02-25
That card isn't supported by any Linux driver.  You're using ndiswrapper then?

---

### Post by battousai567 on 2007-02-25
Yes, I installed it with ndiswrapper.  It looks like it's installed correctly.  ndiswrapper -l says it's all working.

```
battousai567@battousai567:~$ ndiswrapper -l
wlipnds : driver installed
           device (17FE:2220:1737:0029) present
           device (17FE:2220) present
```

---

### Post by RomeReactor on 2007-02-25
> battousai567@battousai567:~$ **wudo** iwconfig wlan0 essid west

I suppose that's just a typo, right? should be

```
sudo iwconfig wlan0 essid west
```

---

### Post by battousai567 on 2007-02-25
> Quote:
battousai567@battousai567:~$ wudo iwconfig wlan0 essid west  

I suppose that's just a typo, right? should be


Yea, sorry, I'll fix it, just a typo on the forum.  I'm typing on my desktop while looking at my laptop, that has Ubuntu on it.

---

### Post by RomeReactor on 2007-02-25
This is what the [NdisWrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L") page has to say about your card (look under entry # 23):

> Card: Linksys #[WPC54G v4], 54mbps -- [link here|List#WPC54G v4]

    * Chipset: AirConn? IPROCOMM IPN 2220 (rev 01)
    * pciid: 17fe:2220
    * Driver: Linksys [ftp://ftp.linksys.com/pub/network/WPC54G%20v4%20driver%20rev%201.22.1.2004.zip](ftp://ftp.linksys.com/pub/network/WPC54G%20v4%20driver%20rev%201.22.1.2004.zip)
    * Used ndiswrapper -i WLINPDS.INF on Debian Sarge for the Linksys driver. Worked perfectly.
    * Driver:IPN2220 [ftp://ftp.rediris.es/sites/arklinux.org/arklinux/arklinux.org/apt/arklinux/dockyard/en/i586/RPMS.contrib/driver-ipn2220-2.10.03.2004-1ark.i586.rpm](ftp://ftp.rediris.es/sites/arklinux.org/arklinux/arklinux.org/apt/arklinux/dockyard/en/i586/RPMS.contrib/driver-ipn2220-2.10.03.2004-1ark.i586.rpm)
    * Other: Debian/Sarge 2.6.11, Ndhttp://ftp.us.dell.com/network/R140747.EXEiswrapper 1.1 with module asistant.Works with WEP 64bits and 128bits and WAP-PSK,other encription not tested

so it seems like it should work. If you're still having trouble setting th ESSID on the card, try editing the /ETC/NETWORK/INTERFACES file by hand:

```
gksudo gedit /etc/network/interfaces
```

and add under **wlan0**

wireless-essid YOUR_ESSID

save, close and reboot

---

### Post by battousai567 on 2007-02-25
Ok, I'll try that right now.

---

### Post by battousai567 on 2007-02-25
under all the eth0 connections it now says 

```
iface wlan0 inet dhcp
wireless-essid west

auto wlan0
```

The connection is still not working.  iwconfig still returns that ESSID: off/any but the connection properties in the tool bar show that the ESSID for wlan0 is "west" and is disconnected with 0% signal strength.  Something doesn't seem to be working right since the terminal says there is no ESSID but the connection properties say there is one.

---

### Post by RomeReactor on 2007-02-26
> **battousai567 said:**
>  ...I'm typing on my desktop while looking at my **laptop**, that has Ubuntu on it.

Somehow i missed that. What laptop are you using? You can find drivers for it on the [NdisWrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") page; if you're browsing with Firefox, once the page loads press CTRL+F and paste **17fe:2220**. Then keep pressing the "Next" button below (right of the "Find" box) until your laptop appears. Or post it here and we'll see what we can do.

---

### Post by battousai567 on 2007-02-26
> Card: Linksys #[WPC54G v4], 54mbps -- [link here|List#WPC54G v4] 
Chipset: AirConn? IPROCOMM IPN 2220 (rev 01) 
pciid: 17fe:2220 
Driver: Linksys [ftp://ftp.linksys.com/pub/network/WPC54G%20v4%20driver%20rev%201.22.1.2004.zip](ftp://ftp.linksys.com/pub/network/WPC54G%20v4%20driver%20rev%201.22.1.2004.zip) 
Used ndiswrapper -i WLINPDS.INF on Debian Sarge for the Linksys driver. Worked perfectly. 
Driver:IPN2220 [ftp://ftp.rediris.es/sites/arklinux.org/arklinux/arklinux.org/apt/arklinux/dockyard/en/i586/RPMS.contrib/driver-ipn2220-2.10.03.2004-1ark.i586.rpm](ftp://ftp.rediris.es/sites/arklinux.org/arklinux/arklinux.org/apt/arklinux/dockyard/en/i586/RPMS.contrib/driver-ipn2220-2.10.03.2004-1ark.i586.rpm) 
Other: Debian/Sarge 2.6.11, Ndhttp://ftp.us.dell.com/network/R140747.EXEiswrapper 1.1 with module asistant.Works with WEP 64bits and 128bits and WAP-PSK,other encription not tested 

That's my wireless card.  I have the first driver linked installed.  I'm not sure what you mean by finding my laptop on there.  The laptop with Ubuntu on it is a Gateway 400 Notebook.  I think the wireless card drivers are ok and installed correctly because it shows the drivers are installed an dthe device is present.

```
battousai567@battousai567:~$ ndiswrapper -l
lsbcmnds : driver installed
wlipnds : driver installed
           device (17FE:2220) present
```

I'm wondering if maybe its the network im trying to connect to or if it's possibly the wireless-tools were not installed correctly.  I'm going to try and go to the library and try their wireless network to see if it works, tonight.

---

### Post by battousai567 on 2007-02-26
I had an interesting break through.  I found if I change the mode from "Managed" to "Ad-Hoc", I can connect to some of the networks, though not the ones with internet connection, they are mostly just peer-to-peer.  When in "Ad-Hoc" mode I can set the ESSID and it works fine connecting but if I try to connected to a network thats "Managed", I can't connect and if I change back to "Managed" mode, I have the same problem trying to set my ESSID.   That was probably really confusing to read.  I don't have any idea what the difference between "Ad-Hoc" and "Managed" mode is, does this make any sense?

---

### Post by battousai567 on 2007-02-26
It seems to be a problem with the "Managed" mode.  When I and the network I am connecting to are both in "Ad-Hoc", whatever that means, the network connection works fine (still no internet though) but if I change to "Managed" mode, I can't change my ESSID or frequency which is stuck on Channel 1 for some reason.  Any attempt to change it under "Managed" has no effect at all.  Any idea what would cause this?

---

### Post by RomeReactor on 2007-02-27
> battousai567@battousai567:~$ ndiswrapper -l
lsbcmnds : driver installed
wlipnds : driver installed
           device (17FE:2220) present

According to this, you have 2 drivers installed; try

```
sudo ndiswrapper -e lsbcmnds
```

to uninstall the other one. As far as i know, it shouldn't be there.

---

### Post by battousai567 on 2007-02-28
Everything is finally working, I'm typing this message in the library with my laptop on wireless.  After a lot of experimenting with your ideas and other things I've found over the internet I found the problem.  Thanks a lot of your help.

---

