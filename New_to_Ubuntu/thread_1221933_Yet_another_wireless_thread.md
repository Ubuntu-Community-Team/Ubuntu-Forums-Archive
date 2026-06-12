---
title: "Yet another wireless thread"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by lsouth on 2009-07-24
Hi, I've been lurking and trying to understand my problem but still have some questions.
New 9.04 install.
Cannot connect to wireless. 
 Linksys wireless router working fine with windows. Unsecured.  (We are in the boonies).
My ethernet controller is Intel Corp 82562ET/EZ/GT/GZ - Pro 100 ve (lom)  Ethernet Controller Mobile (Rev 03)  
My network manager is not finding the wireless signal, and I don't know how to configure the wireless manually.  
I will appreciate any help, suggestions or information.
Lee

---

### Post by pro003 on 2009-07-24
open terminal and type

```
sudo iwconfig
```

see which interface name you have with wireless ext, i.e ath0 wlan0

then

```
sudo iwconfig <interface> mode managed 
```
```
sudo iwconfig <interface> essid <youraccesspointname>
```
```
sudo iwconfig <interface> enc off | on 
```

for more usage and help type

```
sudo iwconfig --help
```

---

### Post by lsouth on 2009-07-24
Thanks Pro 003.  
My wlan0 is IEEE 802.11bg ESSID:""
When I enter  
sudo iwconfig IEEE 802.11bg ESSID:"" mode managed
I get "unknown command 802.11bg"
did I enter something incorrectly?

---

### Post by Ratscallion on 2009-07-24
Try doing a 
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```
Reboot, and then run 
```
sudo iwlist wlan0 scan
```
If that works, the wireless is on and working.

---

### Post by lsouth on 2009-07-24
"INterface doesn't support scanning : Network is down"

---

### Post by lsouth on 2009-07-24
Here is some more information much of which I don't get. 
following sudo iwconfig I see:

lo             no wireless extensions

eth0          no wireless extensions

wmaster0  no wireless estensions

wlan0  IEEE 802.11bg ESSID:""
          Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7  RTS thr: off   Fragment thr=2352B
          Encryption key: off
          Power Management: off
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0  Missed beacon:0

pan0     no wireless extensions

Is there any info here that will help someone with savvy?
Lee

---

### Post by Ratscallion on 2009-07-24
Ok.. That means that wlan0 is the only wifi card on your system and it basically shows a bit of its properties.

---

### Post by superprash2003 on 2009-07-24
post output of
1)sudo /etc/init.d/networking restart
2)sudo iwlist scanning

---

### Post by Ratscallion on 2009-07-24
sudo iwlist scanning = sudo iwlist wlan0 scan.

---

### Post by lsouth on 2009-07-24
> **superprash2003 said:**
> post output of
1)sudo /etc/init.d/networking restart
"reconfiguring network interfaces"

2)sudo iwlist scanning
lo     Interface doesn't support scanning
eth0            ditto
wmaster0    ditto
wlan0          ditto    : network is down
pan0           ditto

It appears that my computer isn't sending  -or receiving - or both.  Is there a way to turn the radio to "on"?  Btw, when I was installing ubuntu, firefox couldn't connect.  My computer has been severely compromised already.
Lee

---

### Post by Ratscallion on 2009-07-24
sudo ifconfig wlan0 up

---

### Post by lsouth on 2009-07-24
> **Ratscallion said:**
> sudo ifconfig wlan0 up

SIOCSIFFAGS : No such file or directory

Should I reinstall?  I getting desperate.
Lee

---

### Post by lsouth on 2009-07-24
BUMP

Everyone Give Up?

---

### Post by Ratscallion on 2009-07-25
No.. Don't reinstall. That would be pointless.

---

### Post by pro003 on 2009-07-25
> **lsouth said:**
> Thanks Pro 003.  
My wlan0 is IEEE 802.11bg ESSID:""
When I enter  
sudo iwconfig IEEE 802.11bg ESSID:"" mode managed
I get "unknown command 802.11bg"
did I enter something incorrectly?

Ok you obviously misunderstood me. Your interface must be something from the output of command **sudo iwconfig** perhaps maybe **ath0** or **wlan0** or **wifi0**, someting like that not ieee 802.11bg, 

type in terminal
```
sudo ifconfig -a
```

and you should see the list of your network interfaces like

lo

eth0

ath0

wlan0

...and let's say ath0 is your interface then type in terminal

```
sudo ifconfig ath0 up
```

then

```
sudo iwconfig ath0 mode managed
sudo iwconfig ath0 essid myaccesspointname
sudo iwconfig 
```

and it should give you the name of your myaccesspointname (thats hypothetical like example cause i dont know your access point name) and you should also see MAC address of that a.p like form of 00:22:45:C4:BA:CE

that means you're connected, now if you have an encryption enabled thats a different story, then will try to solve that...

---

### Post by Ratscallion on 2009-07-25
Once you've got the thing enabled you could always use the GUI to connect to something that's encrypted...

---

### Post by LewRockwell on 2009-07-25
> **lsouth said:**
> Hi, I've been lurking and trying to understand my problem but still have some questions.
New 9.04 install.
Cannot connect to wireless. 
 Linksys wireless router working fine with windows. Unsecured.  (We are in the boonies).
My ethernet controller is Intel Corp 82562ET/EZ/GT/GZ - Pro 100 ve (lom)  Ethernet Controller Mobile (Rev 03)  
My network manager is not finding the wireless signal, and I don't know how to configure the wireless manually.  
I will appreciate any help, suggestions or information.
Lee

here we are on the second page and we still don't know the make, model, part/build number of the equipment

quite frequently, once we know the particulars, the solution is one simple post away

we now return you to your regularily scheduled programming

beam me up scottie

.

---

### Post by pro003 on 2009-07-25
> **LewRockwell said:**
> here we are on the second page and we still don't know the make, model, part/build number of the equipment

quite frequently, once we know the particulars, the solution is one simple post away

we now return you to your regularily scheduled programming

beam me up scottie

.

ha-ha :)

---

### Post by a.m.wink on 2009-08-05
Well hopefully I can add to this thread because I have the same problem.

* My computer is a 1GHz Athlon (very old) with 1GB memory
* My network card is a Belkin Wireless G PCI card with a BCM4318 802.11g controller
* My Kubuntu is a freshly installed 9.04 with a 2.6.28-11 kernel
* b43-fwcutter, wireless-tools, etc are all installed

1. lspci shows the wireless controller
2. iwconfig shows the wlan0 entry, with the correct essid
    (although Tx-Power, signal level and noise level are 0)
3. if I type ifdown wlan0; ifup wlan0, I get messages like:
...
SIOCSIFFLAGS: No such file or directory
...
Could not set interface 'wlan0' UP
...
wmaster0: unknown hardware address type 801
...
Listening on LPF/wlan0/00:17:3f:86:bb:cd
Sending on LPF/wlan0/00:17:3f:86:bb:cd
receive packed failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: network is down
...
No DHCPOFFERS received
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down

To me it looks as if the hardware is recognised, but the driver and dhclient don't communicate?

Help is very much appreciated. I'll be happy to send more output, but I cannot copy/paste because I have no network on my Linux computer! Typing this on the Windows laptop sitting next to it, which connects to the router no problem.

Best wishes
Alle Meije

---

### Post by a.m.wink on 2009-08-05
One disconcerting message that I can bring up (other than ifup not working of course) is that lshw gives the message:

*-network:0 DISABLED
  description: wireless interface
  physical id: 1
  logical name: wlan0
  serial: 00:17:3f:86:bb:cd
  capabilities: ethernet serial wireless
  configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
  ...

Here: network:0 represents the wireless card and network 1 represents an ethernet card (whihch is not connected). The strange thing is: higher up in the list (where the drivers etc are listed), the ethernet card is network:0 and the wireless card is network:1. 

Could that be the source of the problem?

bw
AM

---

### Post by pro003 on 2009-08-05
can you please post the output of commands

```
sudo ifconfig -a
```

& this one

```
sudo iwconfig
```

thank you.

---

### Post by a.m.wink on 2009-08-06
Will do as soon as I get home (as I said, my ubuntu box is not connected so cutting and pasting was not possible).

The most obvious error messages were with lshw and after ifup wlan0.

Thanks
Alle Meije

---

### Post by pro003 on 2009-08-06
> **a.m.wink said:**
> Will do as soon as I get home (as I said, my ubuntu box is not connected so cutting and pasting was not possible).

The most obvious error messages were with lshw and after ifup wlan0.

Thanks
Alle Meije

you can write it down on a piece of paper for god sake....

anyway

---

### Post by a.m.wink on 2009-08-06
Yeah yeah I know. Back at home, as root, typing

##################################

[root $] ifconfig -a
eth0   ..... lots of stuff seems fine
lo       ..... lots of stuff seems fine
pan0   ..... lots of stuff seems fine
wlan0   Link encap:ethernet  HWaddr 00:17:3f:86:bb:cd
           BROADCAST MULTICAST MTU:1500 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 frame:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0,0 B) TX bytes:0 (0.0 B)
wmaster0   Link encap:UNSPEC  HWaddr 00-17-3f-86-BB-CD-00-00-00-00-00-00-00-00-00-00
                BROADCAST MULTICAST MTU:1500 Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 frame:0
                collisions:0 txqueuelen:1000
                RX bytes:0 (0,0 B) TX bytes:0 (0.0 B)

##################################
               
(no idea what wmaster is, but gives the same info as wlan)

then:

##################################

[root $] iwconfig

lo             no wireless extensions
eth0         no wireless extensions
pan0         no wireless extensions
wmaster0  no wireless extensions
wlan0        IEEE 802.11bg ESSID "madness"
                Mode:managed Frequency:2.412 GHz Access Point: Not-Associated
                Tx-Power=0 dBm
                Retry min limit:7 RTS thr:off Fragment thr=2352 B
                Encryption key: off
                Power Management: off
                Link Quality:0 Signal Level:0 Noise Level:0
                Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
                Tx excessive retries:0 Invalid misc:0 Missed beacon:0

##################################

A lot of typing, but that's what it says. It means nothing to me.

I have had a look at other posts about Belkin cards, and people seem to get them to work in very different ways. 1: by using ndiswrapper. Somehow that is not installed in Kubuntu 9.04. Others by installing modules (which are not present in my Kubuntu installation) or downloading files from the internet. It's the internet connection that doesn't work...

Would it help to put the sources on the drive (if they are on the Kubuntu disc) and recompile? Or is there a set of Belkin-related files that will definitely be enough to get it working?

Or is the problem obvious from the output above???

Cheers
Alle Meije

---

### Post by Buuntu on 2009-08-06
Have you tried simply adding a wireless network with a SSID of "madness"?
 
If that doesn't work, check out this site, it explains everything you need to do: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) 
Ndiswrapper would work, but it seems your computer is already recognizing your wireless card.

---

### Post by pro003 on 2009-08-06
well done, now if you could just once more type in terminal 

```
sudo ifconfig
```

not with option **-a**

and see the output, if there isn't **wlan0** interface, then you type

```
sudo ifconfig wlan0 up
```

then it should be up.

now if you type

```
sudo iwconfig mode managed
sudo iwconfig essid madness
sudo iwconfig rate auto
sudo iwconfig bit auto
sudo iwconfig txpower auto

```

now if you do not use encryption likew wep or wpa/wpa2, you type:

```
sudo iwconfig enc off  
sudo iwconfig key off

```

and if you do use then type

```
sudo iwconfig enc 1234-5678-90
sudo iwconfig key 1234567890

```
ASSUMING THAT YOU'RE using WEP/64bit Hex Key.

---

### Post by a.m.wink on 2009-08-12
Thanks for your replies. I have been trying out things, with limited success,

Buuntu, if I type 'iwconfig', for wlan0 it shows ESSID "madness", so I have already done what you suggested? Or are there more things to set up?

Pro003, will try out your tips now, thanks.

What I have got in the meantime is: using the tips on [http://www.thirdstone.com/blog/2009/07/how-to-install-a-belkin-f5d7010-ver-4000-wireless-card-in-ubuntu-9-04](http://www.thirdstone.com/blog/2009/07/how-to-install-a-belkin-f5d7010-ver-4000-wireless-card-in-ubuntu-9-04) I managed to get the drivers going (I think) -used a USB stick for lack of internet.

Now if I type 'iwconfig', the TXpower is 20dbm, so that means the card is on I think. 

As well, when I do 'iwlist wlan0 scanning', my neighbour's wireless is found first, and my own second. So that's good!

Where it is not good is if I do 'ifup wlan0', then I get 5 DCHPDISCOVERs (no mention of network down, so that's good as well), but then it stops because no DHCPOFFERs are returned. 

So I guess the card is set up OK and tries its best, but the router ignores the DHCP requests? Does that sound ... well, sound?

If there is a root terminal-based solution (that doesn't mean re-doing it in KDE every session -maybe Ubuntu would be better than Kubuntu) for this I would be very interested!

Thanks!
Alle Meije

---

### Post by kwacka on 2009-08-12
1. The card is clearly working.

2. Is the ESSID of your router 'madness'?

3. does the pass key of your computer and router match?

4. try a graphic interface to enter details - Ubuntu go to System --> Preferences --> Network connections. In Kubuntu it's 'knetworkmanager'. 

As with most other stuff the graphic front-end is for a command line application (in this case iwconfig)

---

### Post by pro003 on 2009-08-12
well network manager in kubuntu is a bit weird I guess, it is far more better in gnome based ubuntu, but hence there are other nice alternatives like gnome-network-admin and wicd....

---

### Post by kwacka on 2009-08-12
Agreed.

Download & read instructions for wicd from [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by a.m.wink on 2009-08-12
kwacka, points 1, 2, and 3: yes. The SSID is madness, the passphrase (which I use in Windows on the same computer)  is correct.

Will try and do the wicd thing, but again, hopefully there is something that writes to a file in etc, instead of a session-bound GUI thingy.

Alle Meije

---

### Post by a.m.wink on 2009-08-13
Wow!

During one of my trial-and-error sessions and with WPA(1) security off (that's what it's set to for all the other users) I suddenly got a DHCP offer from the router.

So the setup of wpa_supplicant is definitely not kosher at the moment, need to work on that.

The problem is, even after getting an IP address from the router (192.168.0.180, sounds plausible),

* KDE still lists the wireless network as 'unmanaged' 
          reporting IP address 'unk.nown.add.ress' or something
* the command 'ping bbc.co.uk' returns 'unknown host'
* the browser cannot find any site.

So even though the router, with all security turned off, can give me an IP address, non of the networking stuff seems to work.

Not sure if I'm connected now or not??? As said, will try WCID first.

Thanks
Alle Meije

---

### Post by a.m.wink on 2009-08-13
Hmmm... Found a phone cable (!) and got a wired connection.

The wireless keeps not working, the ired connection (eth0) only works when all the security on the router is switched off. The problem is likely to be there for both wireless and wired, I guess?

Anyway, installed the updates etc and wicd as well. 

When as root I type 'wicd', it just says
/var/run/wicd/wicd.pid

When I type 'wicd-client' (running as sux rather than su) it says:
Traceback (most recent call last):
  File "/usr/share/wicd/wicd-client.py", line 50, in <module>
    import wicd.gui as gui
  File "/usr/share/wicd/wicd/gui.py", line 2005, in <module>
    setup_dbus()
  File "/usr/share/wicd/wicd/gui.py", line 177, in setup_dbus
    proxy_obj = bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files

That is a bit disappointing as, optimistically, I had expected a full explanation about why my router and my wireless card have these problems...

Does this make sense???

Alle Meije

---

### Post by a.m.wink on 2009-08-15
It looks like I've cracked it :)

The solution, for those who have come across a similar problem, was twofold in this case:

1. Make the driver working.
    The suggestions on the WWW often assume you have internet 
    (which might not be the case if your wireless does not work).
    I used the directions on
    [http://www.thirdstone.com/blog/2009/07/how-to-install-a-belkin-f5d7010-ver-4000-wireless-card-in-ubuntu-9-04/](http://www.thirdstone.com/blog/2009/07/how-to-install-a-belkin-f5d7010-ver-4000-wireless-card-in-ubuntu-9-04/)
    had to use USB stick to download the files
2. Set up the wireless protocols.
    This one is actually trickier for most people, I think. The site
    [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Using_iwconfig_For_wireless-tools_Configuration](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Using_iwconfig_For_wireless-tools_Configuration)
    gave me the information on how to eventually get in.

The files that needed editing were

#/etc/wpa_supplicant.conf
###################################
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
network={
ssid="TheSSID"
key_mgmt=WPA-PSK
pairwise=TKIP
psk="ThePreSharedKey"
}
###################################

#/etc/network/interfaces
###################################
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
        wireless-essid TheSSID
        pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
        post-down killall -q wpa_supplicant
###################################

This is so cool because it doesn't rely on WICD, NetworkManager or GUI tools.

Thanks to everyone for your help!

---

