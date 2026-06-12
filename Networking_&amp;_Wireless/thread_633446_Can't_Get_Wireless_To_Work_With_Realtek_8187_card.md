---
title: "Can't Get Wireless To Work With Realtek 8187 card"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by bigalreturns on 2007-12-06
I've been struggling with this for a matter of weeks now, and have finally conceded defeat and posted here!
I'm running Ubuntu 7.10, all updated, and trying to get wireless to work with my Realtek card.  I've been through several threads about using the native drivers, and the windows drivers through ndiswrapper, but can't get anything to work.
A few outputs of various commands that others seem to have requested in the past to get you started (currently trying to use the native drivers):

> alex@alex-desktop:~$ lsusb
Bus 004 Device 005: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


[quote=lshw -C network]
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0e:2e:e4:51:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
[/quote]
I've also tried (as described in [this thread]("http://ubuntuforums.org/showthread.php?t=571188") adding an "x" to the end of the essid name, again to no avail.

Any help would be very much appreciated.
[/URL]

---

### Post by Original Brownster on 2007-12-06
Hi,
Please post the output of 
$ iwconfig
and
$ ifconfig

also the content of your /etc/network/interfaces file

Which wireless ap / router do you have?

Which encryption do you intend to use / WEP / WPA?

---

### Post by bigalreturns on 2007-12-07
> 
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Squirrelsx"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B5:FB:0F:AB
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fefb:fab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:986241 (963.1 KB)  TX bytes:194735 (190.1 KB)
          Interrupt:16 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:E4:51:9A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:0E:2E:E4:51:9A
          inet addr:169.254.7.93  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-E4-51-9A-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


[quote=/etc/network/interfaces]
auto lo
iface lo inet loopback

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

#iface wlan0 inet dhcp

#iface eth0 inet dhcp

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-key s:xxxxx
wireless-essid Squirrelsx

auto wlan0

auto eth0
[/quote]
Thats with several empty lines taken out.

The router is a D-Link DSL 2640B, and I plan to use WEP(ascii) security (despite its shortcomings!)

Thanks

---

### Post by Original Brownster on 2007-12-07
Hi,

A driver for your wireless card is loaded, a good start assuming it works ok with linux we are out of the blocks and running..

from the output I can see eth0 is up and running, in using dhcp on this sys, your default gateway will be set as well and possibly cause problems whilst trying to sort this so my advice is:

1/ dont use the network manager tool! it reconfigures the devices automatically which is great when everything is working but a PITA when you're trying to debug/fix something. you can un-install it and re-install if you like.its your choice though :)

2/ before you do any changes, post us the output of 
$netstat -rn
as this will show the default gateway set along with any other useful routing info

3/ edit the interfaces file by commenting out the eth0 and any other than wlan0 connection (just add a # at the beginning of the line) then all you do is run
$ sudo /etc/init.d/networking restart
to get your system to re-read the configurations, you can easily switch back to eth0 by uncommenting and re-running this command of course.

this is what you should have in the interfaces file for starters

iface wlan0 inet dhcp
wireless-key sxxxx
wireless-essid Squirrelsx

Assuming this does not work, remove the encryption settings above and from your wireless AP as this can help whilst troubleshooting.
restart the network using the command in (3) above

try again and see if you get a connection, if
$ifconfig
shows wlan0 has been assigned an ip in the range 192.168 .... (as this is what your eth0 card range is)  then it's working.
if it's blank try the following commands:

$sudo iwlist wlan0 scan

this should return a list of ap's in range (called cells) yours should be there. if not then there is a problem at a lower level. 

Anyway that should get you started, post back and let us know how you get on.

---

### Post by bigalreturns on 2007-12-07
> 
netstat -rn
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 wlan0


I'll follow up with how the rest of it goes. Thanks

---

### Post by lvleph on 2007-12-07
Doesn't the auto wlan0 need to come before face wlan0 inet dhcp?

What exactly is the problem you are having anyway? Does NetworkManager see that you have wireless and sees the networks, but doesn't let you connect? If that is not the problem, have you used sudo modprobe ndiswrapper in terminal? And is ndiswrapper added to the bottom of /etc/modules?

This is what my interfaces looks like for wlan0. I have r8185
```
auto wlan0
iface wlan0 inet dhcp
```

---

### Post by bigalreturns on 2007-12-07
Still a lot of heartache going on at this end I'm afraid!!!
1) I uninstalled Network Manager.
2) Turned off any security on router. (tried without this step, leaving code in step 3 first)
3) Edited /etc/network/interfaces (started with commenting out, then backed up and literally just left in:
iface wlan0 inet dhcp
wireless-essid Squirrelsx
4) Restart networking
5) Try to connect to net, works...but through eth0 not wireless card.  Surely taking any eth0 lines out of interfaces should stop this?  ifconfig gives the following:
> 
eth0      Link encap:Ethernet  HWaddr 00:0F:B5:FB:0F:AB
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fefb:fab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:522183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:223291139 (212.9 MB)  TX bytes:184838680 (176.2 MB)
          Interrupt:16 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5048 (4.9 KB)  TX bytes:5048 (4.9 KB)


Tried to scan using your code:
> 
sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down


---

### Post by bigalreturns on 2007-12-07
lvleph: I added auto wlan0 into my interfaces file, and then restarted, here's the output:

> 
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 3666
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:2e:e4:51:9a
Sending on   LPF/wlan0/00:0e:2e:e4:51:9a
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:2e:e4:51:9a
Sending on   LPF/wlan0/00:0e:2e:e4:51:9a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


[quote=iwconfig]
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Squirrelsx"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/quote]

---

### Post by lexograph on 2007-12-07
I am a brand new linux user.  I am having some trouble following the forums because I am not completely familiar with the language.  I have done well with the os so far but I am having the same issue that many people are with the Realtek 8187b wireless card.  I am running gutsy gibbon and I need help because I am very close to reinstalling VISTA....please save me! I downloaded the program that allows you to install the windows .inf driver for wireless cards but it returned the error of the wrong driver.  Is anyone willing to walk me through this?

---

### Post by Original Brownster on 2007-12-08
> **bigalreturns said:**
> lvleph: I added auto wlan0 into my interfaces file, and then restarted, here's the output:
 
Hi, sorry I missed the line 'auto wlan0'. 
after you re-run '/etc/init.d/networking restart' your output at least shows that wlan is configured and asking for an ip via dhcp, with no answer. 

steps you should take:
1. verify the AP is correctly configured as an 'open' network with no encryption, check the essid
2. make sure the interfaces file is correct, make sure the essid is identical to the one in the AP (no 'x''s added)

auto wlan0
iface wlan0 inet dhcp
wireless-essid Squirrels    < capital S and no x? , is this identical to the AP?

3. with your modified 'interfaces' file (only wlan0 configured) bring up the network, even if it fails, wlan0 should be partially configured, 

4. verify your sys can 'see' the AP:
$sudo iwlist wlan0 scan
can you now see your AP?
it will give you lots of info about the AP tell you the essid, whether encryption is off etc.
check this looks correct (post it if you're not sure)

HTH
let us know how it goes,

---

### Post by bigalreturns on 2007-12-08
Thanks again for your reply, still no joy though.  I've made sure of the essid and no security, connected to it from my housemates Vista PC using these options.  I tried both with and without the "x" at the end just to be sure as well.
Going through your steps, it seems that my card is not seeing the AP, doing sudo iwlist wlan0 scan gives:
wlan0      No Scan Results

---

### Post by Original Brownster on 2007-12-08
> **bigalreturns said:**
> Thanks again for your reply, still no joy though.  I've made sure of the essid and no security, connected to it from my housemates Vista PC using these options.  I tried both with and without the "x" at the end just to be sure as well.
Going through your steps, it seems that my card is not seeing the AP, doing sudo iwlist wlan0 scan gives:
wlan0      No Scan Results

ok well that would strongly suggest the problem is more fundmental rather than a configuration issue since the kernel recognises the device and loads a driver for it. I've been searching on this chipset and although I haven't found anything concrete there is a suggestion that the driver is broken with kernels > 2.6.18.x 

I would suggest you either confirm this by further searching or move onto using ndiswrapper and a windows driver as this seems to work for others. I guess you could also try building an earlier kernel as an alternative..

I would check the exact chipset too, try $sudo lspci -v 
and look for info on your card, it's a usb stick yes?

---

### Post by clayt0njknight on 2007-12-13
I have a gateway ML6721.  Needless to say, i hate it.

Gateway really screwed me over on this one, which was a replacement for my MX6454 that i loved so dearly.


After a month solid fighting with my wifi and Compiz, both finally work.  


First I'll start with the wifi since that is the issue here though.  This notebook contains the Realtek 8187b chipset.  Crappy.  NDISWRAPPER was the solution for me, sort of.

basic steps i took to get it working:

1.) disable wifi using hotkey (fn+F2).
2.) download latest NDISWRAPPER from repository
3.) download realtek 8187 drivers from realtek's site.
4.) extracted zip file
5.) opened terminal, changed to folder containing WinME driver (in this case it was /home/clay/Desktop/rtl8187b/WinME)
6.) input the following:
[I]sudo ndiswrapper -i net8187b.inf
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi[/I]

7.) enable wifi using same hotkey sequence as step 1.
8.) restart machine
9.) left click on network manager at the top of my screen, chose manual configuration.
10.) selected wireless network adapter and clicked properties.
11.) uncheck "enable roaming"
12.) entered ESSID manually
13.) chose DHCP from drop down list in second section of window and click ok.
14.) you should see a little window pop up with a pretty flashing scrollbar that says "changing network adapter."

once that window disappeared, i was able to browse the web wirelessly.  took me a month to figure out disabling the adapter upon using ndiswrapper, then configuring my network setup manually does the trick.  pain in the *** if you travel a lot, but the good news is if you have it set to "enable roaming" it will find any access points around you, it just won't obtain an IP address from them for you automatically.  Realtek is usually pretty good about releasing wireless drivers for linux for their products, but they are really lagging on this one.

i'm not an expert by any means, but feel free to PM me or email me i'll do anything i can to assist.


NEXT PROJECT- installing OS X 10.5.

---

### Post by ftucker on 2007-12-13
help I'm having a similar issue with same card.. Please help... 
Here are some of my outputs...

 frank@frank-laptop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



frank@frank-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:03:25:4F:01:DD  

          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::203:25ff:fe4f:1dd/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:4567 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4263 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:4498105 (4.2 MB)  TX bytes:687663 (671.5 KB)

          Interrupt:17 Base address:0x8000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



auto lo

iface lo inet loopback



netgear 827 w 

I'm currently using no encryption but I am planning on using WEP

please help 
thanks for your time.
Frank

---

### Post by clayt0njknight on 2007-12-13
have you tried installing the drivers?

have you tried to initialize the interface or even alias ndiswrapper as a handle?  (i.e., wlan0?)

---

### Post by ftucker on 2007-12-19
I did try ndisgtk and it said it installed the drivers but i think it had issues and i have downloaded the unix driver from realtek but i'm new to ubuntu and not sure how to install the driver properly i also downloaded the new kernel but again not sure of what to do since I downloaded it.
Thanks 
Frank
i do know how to use the tar command to unzip them..
thanks again

---

### Post by clayt0njknight on 2007-12-20
Remove it from there.


Then open a terminal and install it via command line using the following directions:


change directories to the folder containing the windows ME version of the driver (command for this is "cd" and then the path...  in my case since it's on my desktop i would type cd /home/clay/Desktop/RTL8187B/WinME  and press enter.  keep in mind that this IS case sensitive.)

then type the following:  sudo ndiswrapper -i net8187b.inf    and press enter.

it will ask you for your password.  enter it and press enter.  this executes ndiswrapper and the "-i" tells it that you are using an INF file to install the driver.  the last part is the driver's name.

then type the following:  sudo ndiswrapper -m   and press enter.  then type sudo ndiswrapper -ma   and press enter.  then type sudo ndiswrapper -mi   and press enter.  executing these commands writes ndiswrapper to be the alias for "wlan0", or the system's alias for your primary wireless card.

once you have done this, reboot your machine.  log in, and go up to the top to your network utility and left click on it and click "configure manually."

if it asks for your password, enter it now and click ok.  then double click on the top connection (or the one that says "wireless connection").  uncheck the box that says "enable roaming".  the first drop down should have your wireless router, or any wireless router in the area in its list.  select yours and go down to the second drop down and tell it to use DHCP to connect.  once that's done, click ok, and then check the box next to the "wireless connection" in the list of your connections.  it should then say "changing network connections."  once that's done, you should then have connectivity.

---

### Post by bollix47 on 2007-12-20
FWIW, here is a setup for the rtl8187 with wpa security that worked for me
using Feisty and now continues to work with Gutsy.

Your gateway and other ip's may vary depending on your
router's ip address.

Network Manager is removed using Synaptic.
Ndiswrapper is NOT used.

Make sure wpasupplicant is installed with Synaptic.

/etc/network/interfaces

```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.2.102
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

```

/etc/wpa_supplicant.conf

```

network={
        ssid="xxxxxxxxxxxx"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
}

```

To restart networking:

```

sudo /etc/init.d/networking restart

```

I do get the occasional disconnect from signal interference but 
usually the above will bring it back to life.

Sometimes I have to do the following before the restart.

```

sudo rmmod rtl8187 && sleep 2s && sudo modprobe rtl8187

```

Hope this helps someone.

---

### Post by clayt0njknight on 2007-12-20
This helps quite a bit really... I haven't *successfully* implemented any type of encryption, but this works.  


It's unfortunate that actual drivers haven't been released by realtek yet, they are usually on-game in helping linux users use their products.

---

### Post by bollix47 on 2007-12-20
> **clayt0njknight said:**
> This helps quite a bit really... I haven't *successfully* implemented any type of encryption, but this works.  


It's unfortunate that actual drivers haven't been released by realtek yet, they are usually on-game in helping linux users use their products.

They've recently released a new one for Vista that works much better than the older one, so maybe the linux one won't be far behind.

---

### Post by clayt0njknight on 2007-12-29
SuSE 10.3 GM/32-bit...  and magically i can use the network manager to maintain a wireless connection for my Realtek 8187b??  I'm baffled beyond words right now.  And all I did was use NDISWRAPPER to install the WinME drivers as I had on Gutsy.  The only difference was with this I didn't reboot my box, I simply threw "modprobe ndiswrapper" into the terminal i had open, and with my wired connection going selected my wifi network from the network manager list.  I disconnect, and I've got wireless with signal strength feedback via network manager.  I can pick up and join any network broadcasting within range, and I can even use WEP or WPA...  I don't get it.  I just don't get it.

---

### Post by Frijolie on 2008-02-13
I'm also having "issues" with this freaking wireless card in Gutsy. Mine claims to be a RealTek 8817b Wireless b/g card and is running on the USB bus? Here's the output of a few aforementioned commands:

lsusb (only displaying applicable output)
```

brian@Frijolie:~$ lsusb
Bus 007 Device 003: ID 0bda:8197 Realtek Semiconductor Corp

```

lshw -C network
```

brian@Frijolie:~lshw -C network
  *-network DISABLED
        description: Ethernet Interface
        product: 88E8039 PCI-E Fast Ethernet Controller
        vendor: Marvell Technology Group Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eth0
        version: 14
        serial: 00:a0:d1:95:12:09
        capacity: 100MB/s
        width: 64 bits
        clock: 33Mhz
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt
        1-bt-fd 100bt 100bt-fd autonegotiation configuration: autonegotiaton=on                                                                                                                                                                                                                                 
        broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=yes
        module=sky2 multicast=yes port=twisted pair

  *-network
        description: Wireless interface
        physical id: 1
        logical name: wlan0
        serial: 00:16:44:8e:de:a4
        capabilities: ethernet physical wireless
        configuration: broadcast=yes multicast=yes wireless=802.11b/g

```

iwconfig
```

lo              no wireless extensions

eth0            no wireless extensions

wlan0           802.11b/g   Mode:Managed    Channel=10
                Access Point: Not-Associated    Bit Rate: 11 Mb/s
                Retry:on    Fragment thr:off
                Link Quality:0    Signal level:0    Noise Level:0
                Rx invalid nwid:0    Rx invalid crypt:0    Rx invalid frag:0
                Tx excessive retries:0    Invalid misc:0    Missed beacon:0

```

ifconfig
```

brian@Frijolie:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5562 (5.4 KB)  TX bytes:5562 (5.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:8E:DE:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:213 overruns:0 frame:0
          TX packets:1860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1833 (1.7 KB)  TX bytes:78120 (76.2 KB)

wlan0:ava Link encap:Ethernet  HWaddr 00:16:44:8E:DE:A4  
          inet addr:169.254.8.245  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```


my /etc/network/interfaces
```

# auto lo
# iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

pre-up		/usr/lib/rtl8187b-modified/wlan0up
post-down	/usr/lib/rtl8187b-modified/wlan0down

```


netstat -rn
```

brian@Frijolie:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 wlan0

```

and finally iwlist wlan0 scan (only displaying the SSID I wish to connect to)
```

brian@Frijolie:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
           Cell 06 - Address: 00:16:B6:B9:17:FD
                    ESSID:"Frijolie"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:29  Signal level:0  Noise level:54
                    Extra: Last beacon: 194ms ago
 
```

I've uninstalled network-manager-gnome, disabled my WPA security from my Linksys WRTG54G v5 router and am ready for the next step.  I just barley was able to get my card recognized via the rtl8187b-modified driver located at this website: 

[http://www.datanorth.net/%7Ecuervo/rtl8187b/](http://www.datanorth.net/%7Ecuervo/rtl8187b/)

I have gotten connectivity before but I can't seem to replicate it again. After each succesful reboot i have to configure everything again. Is this a kernel isue, a manufacturer (not issuing a linux driver) issue, or a POS wifi card issue?
I have another laptop which is also running Gutsy but has an Intel Pro Wireless 2200 a/b/g internal PCI card and it works flawlessly with WPA and network manager out-of-the-box. I guess you can't win them all! What can/do I do next?

---

