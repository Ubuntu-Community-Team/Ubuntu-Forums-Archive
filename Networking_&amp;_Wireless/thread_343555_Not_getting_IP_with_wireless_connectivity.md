---
title: "Not getting IP with wireless connectivity"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by willuminate on 2007-01-21
Hi everybody

I just installed Xubuntu on my desktop box last night and configured it to connect to a wireless network based on the stickied HOWTO written by wieman01. My network uses DHCP, WPA2, hidden SSID. Everything worked fine, until I had to restart.
iwconfig and ifconfig showed my ath0 fine, but it's not getting IP address from my router. The router itself is fine, as I was connected to it with my windows laptop trying to figure out what was wrong.

I tried to issue > sudo /etc/init.d/networking restart but the message I got was this
>  * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 4322
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
After fiddling around, I found that the solution was to do this:
> sudo ifup eth0
The message I got was
> Ignoring unknown interface eth0=eth0.
Then I had to
> sudo ifdown ath0
with the reply
> There is already a pid file /var/run/dhclient.ath0.pid with pid 4427
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
After that, I had to ifup my ath0 again:
> sudo ifup ath0
with the reply
> There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.14 -- renewal in 33391 seconds.
Everything worked fine after that, until the next restart. Then I've to do that all over again.
Anybody knows what exactly is going on here? How do I fix this problem so that I don't need to do this every restart? Just as a side note, I'm using an ASROCK P4i65G motherboard (It has a built-in Realtek ethernet) with a NETGEAR WG311T wireless card.

---

### Post by corax on 2007-01-21
Hi !

I'm not sure this will help you but I think you should add the network to you /etc/network/interfaces

to do it type this into the terminal :

```
sudo $TEXTEDITOR /etc/network/interfaces
```

(replace $TEXTEDITOR with a text editor program in Xubuntu (sorry I don't know the name of it :-( )
if you don't know any of them use "vim" it is a bit "strange" editor but you can find it everywhere so it is worth learning it ;) )

and that text file should look like this:
```

....

iface eth1 inet dhcp
wireless-essid mynetwork
wireless-key XXXXXXXXXXXX...XXXX
auto eth1

....

```

it is the default settings for my wireless interface (eth1)
I think you can find out what you should replace with what :-) (mynetwork and xxxxxx...xxxx need to be changed)

i think "auto eth1" is missing but I'm not sure ...

And maybe switch off the wired ethernet if you don't use it sometimes it helps for me...

It can be done automatically if you comment the lines in the same file (/etc/network/interfaces) connected with eth0 for me it looks like this :

```

#iface eth0 inet dhcp
#auto eth0

```

You can uncomment it if you need it or switch it back manually using :

```
sudo ifup eth0
```

bye & good luck

---

### Post by ssavelan on 2007-01-21
I don't use kde for anything, but I've always used the KDE network manager.  As a complete noob, it has always worked so well in ubuntu and xubuntu.  All that I have ever done is set the network setting to dhcp and launch the network manager.

I am wondering why my buddy's d-link dwl-900ap+ router to accept multiple connections.  I don't really know where to start.

Either one of our laptops will connect two the router just fine in ubuntu or windows (I assume for my machine as I haven't actually tried with windows).  I am sending this note through it, but his computer can not concurrently connect.

---

### Post by ssavelan on 2007-01-21
and I don't really know how to subscribe to a thread without posting.

---

### Post by teaker1s on 2007-01-21
thread tools top right

---

### Post by ssavelan on 2007-01-21
Thanks a lot, teaker, it will be a lot easier to participate, now! lol  I have left a lot of posts that I have not seen the replies too:( and will not be able to find (or will I?).

---

### Post by teaker1s on 2007-01-21
you can advance search by user, also in user cp you can set it to subscribe automatically,on the odd time you don't want to just scroll right down on reply page and change it:guitar:

---

### Post by ssavelan on 2007-01-21
Very cool of you to help me out with these simple processes.  I am kind of autistic when it comes to computers.  I can set anyone up with the latest ALSA, video drivers, access to all content streams, printer drivers.

I have another ridiculously simple question:

Where is the best place to start a thread/ask a question?

For instance,

How do I remove old operating systems (partitions have already been reformatted but not removed from GRUB)?

Or,

Hey, anyone out there making extensive use of JACK and MIDI with ubuntu?  We may be able to help eachother/diagnose.

I have never started a thread before.

Thanks,
biouser

---

### Post by willuminate on 2007-01-22
Ok, after more fiddling it's a bit clearer now.
I assumed that
> Ignoring unknown interface eth0=eth0.
is because I did not have any eth0 entry in my **/etc/network/interfaces** file.
I put in
> auto eth0
iface eth0 inet dhcp
Now **sudo ifup eth0** gives proper output.

However, to make my box access the wireless network, I need to
> sudo ifdown eth0
and
> sudo ifup ath0
Clearly the box thinks that it should be connecting through eth0 and would only try to connect if the eth0 interface is put down. Now my queston is, how do I make it so it would try to use ath0 first?

---

### Post by ssavelan on 2007-01-22
I might be putting my nose in where I don't belong, but...

have you tried the kde network manager?  It has a super little gui and seems to work very conveniently on a number of different wireless systems that I have witnessed without any configuration required.:-\"

---

### Post by willuminate on 2007-01-22
> **ssavelan said:**
> have you tried the kde network manager?  It has a super little gui and seems to work very conveniently on a number of different wireless systems that I have witnessed without any configuration required.:-\"
Well I used Xubuntu so I can have a lighter system. Personally if I have to use a gui network manager I'd try to stick with something that does not require me to install extra KDE library. It still won't solve my current problem, though.

---

### Post by nsleiman on 2007-01-22
> **ssavelan said:**
> 

For instance,

How do I remove old operating systems (partitions have already been reformatted but not removed from GRUB)?


sudo nano /boot/grub/menu.lst

---

### Post by ssavelan on 2007-01-22
I hear you; i run xubuntu on my laptop and desktop (I run gnome-ubuntu on my best machine).  The KDE network manager, though, doesn't have an elaborate system of dependencies (I am not a KDE fan, generally), it stands alone quite nicely.  Your question is about whether or not your system defaults to ethernet or wireless and how to conveniently choose/default to either?

---

### Post by ssavelan on 2007-01-22
sudo nano /boot/grub/menu.lst

I am currently in the non-default OS (I tried kubuntu and didn't like it as much as ubuntu or xubuntu).  There may be miscellaneous GRUBs running around.  Do you think that I should execute this command from the default operating system (partition that GRUB is directed to?).

Thanks for the off-subject info.  Speaking of which, how do you start a thread?

---

### Post by willuminate on 2007-01-22
> **ssavelan said:**
> Your question is about whether or not your system defaults to ethernet or wireless and how to conveniently choose/default to either?
Yeah.
I just tried to install network manager and knetwork manager. None of them work properly.
After restart, wireless still doesn't work. I tick/untick Network manager wireless option, still doesn't work. Knetwork manager doesn't even recognise any device. No matter what, I still have to ifconfig eth0 down and ifdown and ifup my ath0.

---

### Post by ssavelan on 2007-01-22
what happens when you launch?

Can you right click the panel icon and see wireless possibilities in range?

---

### Post by corax on 2007-01-22
Hi willuminate !

As I said above:

"And maybe switch off the wired ethernet if you don't use it sometimes it helps for me...

It can be done automatically if you comment the lines in the same file (/etc/network/interfaces) connected with eth0 for me it looks like this :

```

#iface eth0 inet dhcp 
#auto eth0

```

You can uncomment it if you need it or switch it back manually using :

```

sudo ifup eth0

```
"

Please don't be write-only next time :-)

bye & good luck

---

### Post by willuminate on 2007-01-22
I have said in previous reply that I got this error message when I tried to ifup eth0:
> Ignoring unknown interface eth0=eth0. and explained that this might be because originally I [COLOR="DarkRed"]do not have an eth0 entry[/COLOR] in my **/etc/interfaces**. Now if I did it your way, by adding "#" in front of eth0, wouldn't it be just like the configuration originally? But hey, I don't want to be write-only, so I figured I tried it anyways...
Nope, didn't work.

Just to clear things up, here's my** /etc/network/interfaces** look like before:
> #This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf managed
wpa-ssid xxxxxxx
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxxxxxxxxx
The problem is I do not have an eth0 entry, yet my ifconfig does. So I can't ifdown eth0 because there interface eth0 was not configured. Instead, I had to ifup eth0 so that it actually ignores eth0 as unknown interface. Only then can I ifdown and ifup ath0 to renew the IP address for my wireless.
then I add eth0 entry:
> #This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet dhcp
auto eth0

iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf managed
wpa-ssid xxxxxxx
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxxxxxxxxx
Now, the problem is still the same, but it's more logical now to get connected. I ifdown eth0 to disable it, then ifdown & ifup my ath0 (as opposed to ifup eth0 to force the box to ignore eth0).
I put the comment tag as you suggested:
> #This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#iface eth0 inet dhcp
#auto eth0

iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf managed
wpa-ssid xxxxxxx
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxxxxxxxxx
so it's pretty much back to the original problem...

---

### Post by corax on 2007-01-22
So if you don't have an eth0 interface by default why do you want to switch it on (ifup eth0) ? :)  

And if you do have an interface you can switch it off if you insert the comment sign (#) as I mentioned :-)

the machine says :

```
Ignoring unknown interface eth0=eth0 
```

Because you don't have an eth0 interface. I said to turn it off because I thought you have one ... (I don't know your machine specs but you were switching it back and forth ;-) ) If you don't have then you don't have ... 

I think it shouldn't matter if you type:

```
ifup eth0
```

because you don't have any :)

Have you tried to connect it with WEP or without encryption with no hidden ESSID ? Is it working well (out of the box) ?

WPA is still not well supported under linux works only with certain cards and settings ...

bye & sorry I miss understood your eth0 hacking ... :-P

---

### Post by willuminate on 2007-01-22
> **corax]So if you don't have an eth0 interface by default why do you want to switch it on (ifup eth0) ? :)  

And if you do have an interface you can switch it off if you insert the comment sign (#) as I mentioned :-)

the machine says :

```
Ignoring unknown interface eth0=eth0 
```

Because you don't have an eth0 interface. I said to turn it off because I thought you have one ... (I don't know your machine specs but you were switching it back and forth  said:**
> 
Well, yeah this is a weird behaviour, because I do have an eth0.
I had to to switch it on because it forces the computer to ignore the interface. If I switch it off it'll just say eth0 was not configured. If it doesn't ignore eth0 interface, ath0 can't get the IP. This behaviour only happens when I don't have an eth0 entry in my **/etc/network/interfaces**.
[QUOTE=corax]WPA is still not well supported under linux works only with certain cards and settings ...

bye & sorry I miss understood your eth0 hacking ... 
It's ok. I guess I just have to deal with this. I can still connect to the network, just a bit fussy.
Maybe I should just prevent eth0 driver from being loaded at all at startup? How would I do that?

---

### Post by corax on 2007-01-23
Ok let's make it clear for me once more :) 

You can connect  to the router but you don't get any IP right ? :)

I think you should try this :

```
sudo dhclient ath0
```

right after the system boots up (without messing with ifups and ifdowns)

Post me the results :)

ad please also post me what does

```
iwconfig ath0
```

looks like BEFORE you enter what I mentioned above :)

bye & good luck

---

### Post by willuminate on 2007-01-24
> 
$iwconfig ath0
ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$sudo dhclient ath0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   LPF/ath0/00:0f:b5:8b:fa:2d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There you go.

---

### Post by sardeenz on 2007-01-24
I have the exact same problem with Xubuntu Edgy.  I can only get ath0 up when eth0 gets up first.

I've edited my /etc/network/interfaces and will post back my results, but I wanted to post here so you wouldn't think you were alone or so that others don't think you don't know what you are doing.  Something strange is going on here.  I've fiddled with this for 3 days now.

---

### Post by VorDesigns on 2007-01-24
I did this for WEP

Hi, 
I have had similar distractions for the last three weeks trying to get my D-Link DWW-G650 card working until today.

My Interfaces config for ath0
auto ath0
iface ath0 inet dhcp
### Below added as per another thread, didn't help
pre-up ifconfig ath0 up
pre-up ifconfig ath0 down
pre-up ifconfig ath0 up
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
### below added as per another thread, doesn't seem to be
### of much value
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX // expunged
wireless-ap 00:00:00:00:00:00  // expunged
wireless-channel 0 // expunged
wireless-essid my_ap_name
wireless-mode managed

While I already had the key, ap MAC, channel, name and mode in hand, it is good to know that you can scan for ap in the area using 
iwlist scanning // for a list of other capabilities, just type iwlist.

None of the above seems to have done any good but I didn't want to remove any of it since I don't know if it didn't do some of the necessary tasks needed to ultimately connect.

Finally, I do the following ever time I boot
From a terminal window
sudo iwconfig ath0 key XXXXXXXXXXXXXXXXXXXXXXXXXX // my key
sudo iwpriv ath0 authmode 2 // sudo may not be necessary since it was just entered.
sudo dhclient ath0 // ibid.

Viola!  the blinky lights go from alternating (zombie mode) to synchronous (linked mode).
I distilled the commands above from the MadWiFi documentation bouncing around between turtle (newbie) and WEP and troubleshooting and so forth

I'm running Dapper Drake 6.06 LTS.

Some time in the future, I will see if I can figure out how to get this to load via script but I'm geek enough to bring the interface up the rest of the way manually and it's only a minor annoyance

What is clear to me is that the System networking control panel in Dapper doesn't work very well for wireless and I also note that MadWiFi on Dapper doesn't seem to be completely implemented as some of the commands that I was lead to believe should produce a result through a what am I talking about error.

Anyway, I want to thank all of the people who use DWL-G650 in their posts because it gave me lots of things to try and the MadWiFi folks for their documentation although I find it novel that they don't tell you where their application is usually installed and then expect you to know where the /scripts directory for the installed application is when the document was supposed to have been written for a turtle.

I did try KUbuntu (Blue) for about two hours before going back Ubuntu (Brown) after having the same luck with only marginally more informative GUI information "Connection failed".

---

### Post by sardeenz on 2007-01-24
Ok, now I feel like an idiot.  All I did was modify my /etc/network/interfaces file to look like this and it (wireless only, ethernet cable is unplugged) came up perfect on reboot.   Now, just as a disclaimer, my hdd freaked out after my IBM thinkpad t22 had been on all day, and I cold booted a couple of times, lost my xfce start menu, put it back etc, but all that is probably unrelated.  Here's my interfaces file, note that all is commented out except the first part, and I've got all security turned off, no wep, no wap, nothing, nada, totally open.  I'll reboot again in a few and if there's any problem I'll post back.  Don't give up, I'm curious as to how you fix your problem.  So far I think I can stick with Edgy, working pretty darn good.  btw, I've got a netgear wg511t pcmcia using madwifi atheros, hooked to a linksys wrt54g router

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid putyourshere
wireless-mode managed

#iface eth0 inet dhcp
#auto eth1
#iface eth1 inet dhcp
#auto eth2
#iface eth2 inet dhcp
#iface wlan0 inet dhcp
#wireless-essid linksys
#auto wlan0
#iface dsl-provider inet ppp
#provider dsl-provider
#iface ath1 inet dhcp
#wireless-essid linksys
#auto ath1
#address 192.168.1.105
#netmask 255.255.255.0
#gateway 192.168.1.1
#auto eth0

keep us posted, buy the moko (Neo1973) phone on 2/11, and go Ubuntu!

Update, 4 hours later
--Ok, 4 sudo shutdown -P now later, I've had ath0 come up automatically.  So I'll take it.   Maybe it's working.  All systems are different so tell us if there's any news.

---

### Post by dannyboy79 on 2007-02-08
this issue is due to dapper was using madwifi-old and edgy uses madwifi-ng. you need to update your madwifi-ng drivers to the latest. it states it here, [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)
madwifi fixed this issue around 2/6/07 for the wg511t.

---

### Post by ssavelan on 2007-02-09
I thought that, because I'm a noob, I should be conservative and use Dapper and the most stable releases of everything.  I've found that Edgy runs everything better though.  Is there any reason to stick with Dapper?  Also, the latest release of ALSA always seems to be the best and very stable.  My general feeling is that Ubuntu too often over-does the stability thing in my case.  Ubuntu is ridiculously stable on my machine.  Sometimes it's hard to undo the overly stable to get to the cutting edge.

---

