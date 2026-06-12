---
title: "Problems with wireless in Ubuntu, not sure where to begin :("
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by noreaga on 2006-12-24
Hi guys. After finally installing Ubuntu, Im ready to start using it as my full time OS. As a result, Ill need to be able to browse the Net.

Im using a Toshiba laptop which has a built in Intel wireless card. Problem is, and Im sure this is nothing new to you guys, is that I cant seem to get wireless to work.

I tried to install the Network Manager app through Synpatic (i didnt have the package), but I realized that I need an Internet connection to be able to download that.

So, I went into System->Networking, and configured my eth1 interface with the SSID of the router here at home, as well as the WEP key. Still no luck.

Can someone kindly take the time to break things down, or point me to a step by step guide ?  Ive researched here on the forums, but it seems very overwhelming, as almost every other post suggests something different.

Ive run iwconfig, and this is what I see :

lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11g ESSID:"mac" 
Mode:Managed Frequency:2.447 GHz Access Point: 00:0F:66:0A:7C:B4
Bit Rate=54 Mb/s Tx-Power:15 dBm
Retry Limit:15 RTS thr=off Fragment thr=off
Power Management: off
Link Quality:79/100 Signal level:-56 dBm Noise level:-57 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0

Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

When I run sudo ifconfig, I see:

eth1 Link encap:Ethernet HWaddr 00:18:DE:4F:23:AB
inet6 addr: fe80::218:deff:fe4f:b23ab/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1549 errors:0 dropped:0 overruns:0 frame:0
TX packets:1494 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1350646 (1.2 MiB) TX bytes:216277 (211.2 KiB)
Interrupt:185 Memory:da000000-da000fff

Hopefully someone can help, at least by telling me where to start.

Thanks guys

---

### Post by meng on 2006-12-24
Try
sudo iwconfig eth1 key restricted [enter your key in hexadecimal]

or else:
sudo iwconfig eth1 key restricted s:[enter your key in alphanumeric]

then:
sudo iwconfig eth1 up [this may be optional]
sudo dhclient eth1

---

### Post by noreaga on 2006-12-24
I ran this command without any issues:

sudo iwconfig eth1 key restricted [enter your key in hexadecimal]

Then, when I ran this sudo iwconfig eth1 up [this may be optional], I got the message:

Error: unrecognized wireless request "up"

Finally, when I run dhclient, it basically gets no DHCP offers.

i should mention that Im connecting to a router, which then connects to the DSL modem. 

Also, when I ran lspci, I see that my Network Controller is listed as

"Intel Corportation: Uknown device 4222 (rev 02)"

Does this mean that my wireless card isnt recognized ? Wwhat do I need to do ? This same applies for the Ethernet Controller

---

### Post by ryan00davis on 2006-12-24
if your not comfortable with the command line, you can boot into windows (assuming your dual booting), or go on another computer and download the packages there, then either save them to a drive you have mounted, or put it on a thumb drive then install in ubuntu.  make sure you download the dependencies as well as networkmanager.

---

### Post by meng on 2006-12-24
Sorry the second command should have read
sudo ifconfig eth1 up
(f not w)

---

### Post by noreaga on 2006-12-24
tried that new command, and firefox still cant browse.

im wondering if ubuntu is even recognizing my wireless card. I put my lspci output above, where my network card is listed as an unrecognized device.

I have no issues with using the CLI, but its just that to download and install the package I need an active Internet connection.

If i wanted to download the network manager package, where/what do i need to download ?

thanks

---

### Post by loui19 on 2006-12-24
You may want to read the efforts of the folks that have develop the WiFi docs in the Ubuntu community. I used the docs to get my laptop wirelss card to work with ubuntu.

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by c.dric on 2006-12-25
could you post the output you get after the last command (sudo dhclient eth1) ?

also the output of the following commands could be usefl to debug : 

```
route 
```

```
less /etc/network/interfaces
```
(you can blank the key before posting)

---

### Post by noreaga on 2006-12-25
hey guys, ive been reading a fair amount in the hopes of getting this to work, and it seems that I might need to install a driver ? Even though I know that for my Intel 3945 wireless card, Ubuntu comes with a preinstalled driver (ipw3945.ko).

The process to install this new driver looks really complicated...

As for the route command, the routing table is empty. For the dhclient command, it just does DHCPDISCOVER on eth1 to 255.255.255.255, and eventually comes back and says that no DHCPOFFERS were received

Finally, for the less /etc/network/interfaces command, I see:

#auto eth1
#iface eth1 inet dhcp
#wireless-essid mac
#wireless-key XXXXXXXXXXX (I blanked this out)

---

### Post by noreaga on 2006-12-25
just as a side note, i am able to go into system->networking and add in the ssid and key of my wireless router.

ubuntu says that the wireless interface is active, but im still not able to surf at all. I can see from the network name box under Interface properties that the card is actually picking up the different access points around my area, and i just select the one that has the name of the router we use at home ...

any ideas ? the routing table is still empty, and i dont have any indicator on the dekstop panels of whether im actually connected to something or not (like you have in windows)

---

### Post by c.dric on 2006-12-25
from what i've read in the forums if you get a similar output for this command : 

```
lsmod | grep ipw3945
ipw3945 124576 0
ieee80211 35272 1 ipw3945
```

you have the correct driver and you shouldn't worry about that.

are you sure your network uses dynamic ips (dhcp) ?

what happens when you remove the # before the four lines in /etc/network/interfaces
and then run 

```
sudo /etc/init.d/networking restart
```

finally i would recheck my wep key one last time ;)

---

### Post by noreaga on 2006-12-25
Man, I cant believe this, but I had the wrong WEP key in there. How embarassing !

In any case, Im up and running now, so thanks a lot to all of you who contributed.

One last question: now that the connection and profile are set up in Ubuntu, will the connect attempt to the wireless network be made automatically every time I boot up ?

Thanks !

---

### Post by c.dric on 2006-12-25
> **noreaga said:**
> Man, I cant believe this, but I had the wrong WEP key in there. How embarassing !

Been there. Done that. :rolleyes: 

> **noreaga said:**
> In any case, Im up and running now, so thanks a lot to all of you who contributed.

One last question: now that the connection and profile are set up in Ubuntu, will the connect attempt to the wireless network be made automatically every time I boot up ?

I suppose, but i'm using a different setup so i can't tell you for sure.

Have fun :)

---

### Post by nicknn on 2006-12-30
> **noreaga said:**
> just as a side note, i am able to go into system->networking and add in the ssid and key of my wireless router.

ubuntu says that the wireless interface is active, but im still not able to surf at all. I can see from the network name box under Interface properties that the card is actually picking up the different access points around my area, and i just select the one that has the name of the router we use at home ...

any ideas ? the routing table is still empty, and i dont have any indicator on the dekstop panels of whether im actually connected to something or not (like you have in windows)

Hi,
follow these directions to install network manager applet. It gives a drop down graphic
of all the networks around you. I used it to get my wireless 3945abg working on a dell 6400
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
if the packages arent found
update your repositories according to
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
look at  How to add extra repositories section

---

