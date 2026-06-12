---
title: "No working leases in persistent database - sleeping."
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by gvgerman on 2006-09-24
Yet another noob w/ wireless problems (note that wired ethernet works well).
The Dell Latitude D600 laptop internal wireless ethernet device is Broadcomm which I've completely given-up on.  
I'm now trying to get a Linksys WPC11 working and am close (I think; I hope).
I've followed the trouble shooting guides and have the following:

iwconfig
eth2      IEEE 802.11b  ESSID:"2WIRE763"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:95:DB:BD:61
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=127/153  Noise level=107/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw
description: Wireless interface
       physical id: 2
       logical name: eth2
       serial: 00:03:2f:02:db:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmwa re=Intersil 0.8.0 ip=192.168.1.103 link=no multicast=yes wireless=IEEE 802.11b

sudo iwlist eth2 scan
eth2      Scan completed :
          Cell 01 - Address: 00:14:95:DB:BD:61
                    ESSID:"2WIRE763"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:122/153  Noise level:107/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s

sudo dhclient eth2
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:03:2f:02:db:51
Sending on   LPF/eth2/00:03:2f:02:db:51
Sending on   Socket/fallback
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.1.66
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.

--- 192.168.1.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


I'd appreciate it if someone could suggest what is (might be) going on and what the next step(s) might be.

Thx,

---

### Post by kidders on 2006-09-25
Yep, you're close alright ... all the hard graft is over :-) It looks as though your WLAN adapter is up and talking to your access point.

The problem seems to be DHCP-related, in that nothing seems to want to give your card an address. If memory serves, that suggests you haven't got a DHCP server at all ... if one were there, it would at least take the time to say "No!" to you.

To be 100% certain that's what's going on, try to assign yourself an address manually. Take a look at the kinds of addresses in use elsewhere on your LAN, and "guess" one. If Ubuntu suddenly discovers how to ping other computers/etc. on your network, then you're in business. If not, your problem is probably something else :-(

---

### Post by gvgerman on 2006-09-25
Thank you for the reply. Much appreciated.

First off, sorry about the smilies in the original post. I had no idea they'd populate themselves.

The PC also runs windows so I've looked at the TCP/IP properties: both IP and DNS are obtained automatically, DHCP is enabled, WINS is not specified.  I thought about setting the connection to static in Ubuntu and played with it a while last night to no avail.

Also, I found the following info here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

for the WPC11 PCMCIA ethernet card using the orinoco driver:  

"run "cardctl ident" and add info to /etc/pcmcia/config under wireless network adapters section. Be sure to include manfid and bind to orinoco_cs. Then just reboot and run "gksudo network-admin" in console and configure eth0...works like a champ!"

I've run "cardctl indent" and rec'd info but I don't know how to  "include manfid and bind to orinoco_cs".  Do you think this might be an issue and, if so, would you happen to know how to do this?

Thank you,

---

### Post by wieman01 on 2006-09-25
_Two suggestions:_

1. Shut down your firewall (e.g. Firestarter) if you happen to have one.
2. Kill wpa_supplicant if it's installed (sudo killall wpa_supplicant).

Could be a quick win.

---

### Post by wieman01 on 2006-09-25
I see you're using WEP. Please post the contents of:
> /etc/network/interfaces
That'll help understand what the problem is.

---

### Post by gvgerman on 2006-09-25
Thanks, weiman01.

I'm not using a firewall on the PC that I know of.
I've not tried the "sudo killall wpa_supplicant" yet.
Contents of /etc/network/interfaces is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid 2WIRE763
wireless-key 2056490388

auto eth2
iface eth2 inet dhcp
wireless-essid 2WIRE763
wireless-key 2056490388

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Regards,

---

### Post by quickgun on 2006-09-25
Just a hunch, but is the card still in Mode Master?

---

### Post by gvgerman on 2006-09-25
In "Mode Master" - ?
I'm don't know what Mode Master is.
Thanks,

---

### Post by quickgun on 2006-09-25
My mistake, I re-read your original post.

---

### Post by vynsane on 2006-09-25
i'm getting the same thing

"No working leases in persistent database - sleeping."

with a linksys WPC54G ver.4 and WRT54GL wireless router. i'll keep plugging away at it, as i'm sure you will too... let me know if you find out anything, and i'll be sure to do the same!

---

### Post by wieman01 on 2006-09-25
There are two wireless network adapters in your interfaces file. This is certainly wrong. Please edit the file so that it looks like this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid 2WIRE763
wireless-key 2056490388
Then save and restart the network:
> sudo /etc/init.d/networking restart
The WEP key does not look right. I assume this is the plain text key that you have entered, correct? If so it needs to look like this (little "s:" in front):
> wireless-key **[COLOR="Red"]s:[/COLOR]**2056490388
But you can equally enter the HEX key given by the router. Then I would look like this (example):
> wireless-key 0971FD2CD297CE1F2686A2396D
Your problem is MOST probably related to wrong credentials i.e. your WEP key.

---

### Post by gvgerman on 2006-09-25
Agreed.
Thx,

---

### Post by gvgerman on 2006-09-25
wieman01,

Thanks.  I'll try the "s:" prefix.

eth1 is the internal wireless ethernet device that uses the Broadcom chipset, which I have struggled with for several days without luck.

eth2 is the WPC11 pcmcia card which is close to working.

I've left eth1 inactive.

Regards,

---

### Post by vynsane on 2006-09-25
don't want to hijack the thread, or anything, but it seems like my problem is closely associated. could be wrong. figured rather than start a new thread, i would jump into this one. my "interfaces" file:

```

auto lo
iface lo inet loopback

auto eht0
iface eht0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Spidey
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX (edited out)

```

do i need something in the "eth" areas? is it normal to not have them populated with anything?

---

### Post by gvgerman on 2006-09-25
All,

I booted Ubuntu to try wieman01's latest suggestion and, for some unknown reason, when I slid the WPC11 card home in the slot, it connected!  In fact I'm sending this reply via the wireless connection!!

For the record, 
- eth1 is still in-place and is set as inactive.
- eth2 is the pcmcia card WPC11
- since the card connected & is communicating w/ the router, I've not tried the "s:" addition to the WEP key 

I am completely baffled, but pleased nonetheless.

kidders & wieman01 & quickgun - Thank you.  Much appreciated

vynsane - best of luck - the only thing I can suggest is if your WPC54G ver.4 is a pcmcia card try booting w/ the card out of the slot and shove it home once Ubuntu has finished loading.  This site may be of help: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Regards,

---

### Post by gvgerman on 2006-09-25
vynsane,
I suspect eth0 is wired
I suspect eth1 and eth2 are wireless.
Try making only 1 wireless ethernet device active and 1 wired ethernet device active.
From this website: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
try to select the wireless device that has the least amount of work to get running.

---

### Post by vynsane on 2006-09-25
> **gvgerman said:**
> vynsane - best of luck - the only thing I can suggest is if your WPC54G ver.4 is a pcmcia card try booting w/ the card out of the slot and shove it home once Ubuntu has finished loading.  This site may be of help: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

yeah, it's a pc/mcia card... they classify it as "very tricky to get working, must have drivers for the SPECIFIC version of the card." i'm pretty sure i have the correct drivers (got them from the ndiswrapper wiki...) so that doesn't bode well... i may just have to bite the bullet and get another card.

tried putting it in after booting up, and still nothing. hrm... guess that magic didn't reach this far... :( 

> **gvgerman said:**
> 
I suspect eth0 is wired
I suspect eth1 and eth2 are wireless.
Try making only 1 wireless ethernet device active and 1 wired ethernet device active.
From this website: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
try to select the wireless device that has the least amount of work to get running.

the machine's only got a 56k modem in it. the only other device is the linksys pc card. should i just delete the other entries? how do you make them "inactive"? comment out? why are they there in the first place? curioser and curiouser.

i can see my router when i do iwlist wlan0 scan, but when i do iwconfig wlan0 i have "ESSID: off/any" "Access Point: Not-Associated" is there something i need to change here?

---

### Post by vynsane on 2006-09-26
just a thought, i have an .inf file loaded in ndiswrapper, but i've read elsewhere you need a .sys file, as well... do i need this? there's also another .inf file in the package i downloaded from linsys... maybe i should use that one? the only thing is that i'm seeing the network, just can't connect. perhaps i need both .inf files?

---

### Post by wieman01 on 2006-09-26
You need only one *.inf file. But when you deploy this file, all other driver files (*.sys, *.cab) need to be present in the same folder.

---

### Post by gvgerman on 2006-09-26
vynsane,

There is a network config gui under Systems > Administration.  This can be used to set "active" or "inactive". 

This won't resolve the card specific items, however, i.e. - those items noted in [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Rgds,

---

### Post by vynsane on 2006-09-26
> **wieman01 said:**
> You need only one *.inf file. But when you deploy this file, all other driver files (*.sys, *.cab) need to be present in the same folder.

are those automagically populated (dumb question... probably not...) if so, that may be my problem! i hadn't read anything anywhere about adding files to the /etc/network/inffile folder, although i wasn't feeling well yesterday - perhaps i just glossed over those instructions...

> **gvgerman said:**
> vynsane,

There is a network config gui under Systems > Administration.  This can be used to set "active" or "inactive". 

This won't resolve the card specific items, however, i.e. - those items noted in [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Rgds,

ah, i thought it was using iwconfig or something else... the modem is the only other thing showing up here, and it is deacivated.

thanks, both.

---

### Post by vynsane on 2006-09-26
the files i have in the wlipnds (name of the .inf file) folder are 17FE:2220.5.conf, 17FE:220:1737:0029.5.conf, i220ntx.sys and wlipnds.inf. i didn't put any of those in there physically, so i can't really think i need anything else there.

when i view the dmesg log after doing sudo modprobe ndiswrapper, it looks like everything is in order, until i get to the last line: 

```

ndiswrapper: using irq 11
wlan0: vendor: 'INPROCOMM IPN2220 Wireless LAN Adapter'
wlan0: ndiswrapper ethernet device 00:0f:66:3a:6f:fa using driver wlipnds, 17FE:2220:1737:0029.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
ndiswrapper (set_essid:61): setting essid failed (00010003)

```

i've tried all kinds of permutations of "iwconfig wlan0 essid ESSID"

i've also tried to associate with the essid through the "Network Settings" app to no avail. i'm getting really frustrated with this crap...

---

### Post by wieman01 on 2006-09-26
Da@# it. And you will continue to fail unless your network shows when you run "iwlist wlan0 scan".

Another thought. It could be that your network has been disabled. That means you have (physically) switched it off. Is there any switch on your keyboard or any sort of key combination that you would enable it? 

Have you got the same problem in Windows? Perhaps boot it and enable wireless there, then boot back to Ubuntu and see if your card is activated. I really think it's turned off.

---

### Post by vynsane on 2006-09-26
i can see all the available routers, including mine (Spidey,) when i scan... just can't connect to any of them. i have four computers and a VoIP router attached to this router, but this is the only machine with wireless, and all it has on it at this point is ubnutu. i could do a fresh install of XP, but then i'd have to go through a bunch of stuff to get the card working in that, as well, and in addition... why bother? 

what i see when i "iwlist":
 
```

wlan0  Scan completed:
Cell 01 - Address: {edited}
ESSID:"Spidey"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:0/100  Signal level:-10dBm  Noise level:-256 dBm
Encryption key:on
Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s;
           24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s;
           12 Mb/s; 48 Mb/s;
Extra:bcn_int=100
Extra:atim=0

```

i see other networks when they're available, but that's the one i want to connect to, so i'm not going to type all of them...

i got excited when i logged into the router from another box and saw that there were four address there, but then i realized it was the three machines i have hooked up wired, and the VoIP... DER!

the wireless worked in the past in win98, both at home and at one of my jobs the other day, where i transferred the entire contents of the hard drive to my webserver in order to backup all my wife's data (it's her old laptop...)

like i said, i see my router when i "iwlist," but when i "iwconfig wlan0" i get

```

IEEE 802.11g   ESSID:off/any
Mode:Managed   Frequency:2.462 Ghz   Access Point: Not-Associated
Bit Rate:1 Mb/s
RTS thr:2347 B   Fragment thr:2346 B
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```

???

> **wieman01 said:**
> Another thought. It could be that your network has been disabled. That means you have (physically) switched it off. Is there any switch on your keyboard or any sort of key combination that you would enable it?  ...

...I really think it's turned off.

the card's power light is on all the time, and every once-in-a-while the "link" light will burst a couple of times... i've tried "Fn+F2" to "turn on" the wireless, but i don't really know if that's doing anything...

---

### Post by wieman01 on 2006-09-26
Ok, then let's start all over again... Perhaps I have missed something and have confused your post with the previous ones.

Could you also post the contents of:
> gedit /etc/network/interfaces
Encryption has been turned on so I assume you're using WEP? Can you turn it off for the time being? That'll make it easier.
> Encryption key:on
Then post the mentioned file and we try again.

---

### Post by vynsane on 2006-09-27
my /etc/network/interfaces is still similar to the one in post 14 of this thread...

[http://www.ubuntuforums.org/showpost.php?p=1544437&postcount=14](http://www.ubuntuforums.org/showpost.php?p=1544437&postcount=14)

just the WEP key has changed (which is edited out...) as i was trying to figure out if i had typed it wrong or whatnot. i've tried associating without the encryption on, and still nothing, so i don't really want to turn off the security on the router if i don't have to. i'm in brookyn, ny, and i'm sure as soon as someone roving for an open connection finds it, they'll jump on my router...

i'm thinking maybe i screwed the process up by not following the directions to the "T" and may wipe the HDD and re-install xubuntu (had both ubuntu and xubuntu, been switching back and forth to see if one could do it, or the other...) then re-do the ndiswrapper install.

---

### Post by wieman01 on 2006-09-27
No connection even without WEP? Ok, that's a different story then. We need to start tackling the basis... I would still ask you to turn if off while we are doing this. If we get it done, we continue from there, ok?

1. Disable security in the router.

2. Edit "/etc/network/interfaces":
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Spidey
3. Restart the network:
> sudo /etc/init.d/networking restart
...and post the ouput.

---

### Post by wieman01 on 2006-09-27
Also... Do you have any kind of tool such as "wireless assistant" or "wifi-radar" installed? If yes, I would ask you to uninstall it. There are a headache.

---

### Post by vynsane on 2006-09-27
> **wieman01 said:**
> No connection even without WEP? Ok, that's a different story then. We need to start tackling the basis... I would still ask you to turn if off while we are doing this. If we get it done, we continue from there, ok?

1. Disable security in the router.

2. Edit "/etc/network/interfaces":

3. Restart the network:

...and post the ouput.

```

SIOCSOFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0

blah blah internet systems consorium stuff...

Listening on LPF/wlan0/ {MAC address deleted}
Sending on   LPF/wlan0/ {MAC address deleted}
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

> **wieman01 said:**
> Also... Do you have any kind of tool such as "wireless assistant" or "wifi-radar" installed? If yes, I would ask you to uninstall it. There are a headache.

no i don't have either of those. like i said i think i'm going to wipe it all clean and reinstall now that i know exactly what to do. maybe i gunked up the process and confused the hardware somewhere...

---

### Post by wieman01 on 2006-09-27
I am also running out of ideas. I tend to say that your router needs resetting... But that's all I can think of right now. Wireless can be such a b@#$ sometimes.

Another idea before you reinstall: Want to try the Live CD and see if recognizes your card?

---

### Post by vynsane on 2006-09-27
> **wieman01 said:**
> I am also running out of ideas. I tend to say that your router needs resetting... But that's all I can think of right now. Wireless can be such a b@#$ sometimes.

Another idea before you reinstall: Want to try the Live CD and see if recognizes your card?

it didn't initially - i had used the liveCD to find out if the machine would work at all with it... if i do a clean install, follow the procedure of ndiswrapper installation to the letter, and see what happens. most likely i won't get it working and will have to pick up a new card that is deemed easier to install, but you never know. thanks for all your brainpower... i needed it...

---

### Post by vynsane on 2006-09-27
well, did a clean install of xubuntu, ndiswrapper, and wlipnds.inf and still nothing. when i "dmesg" it still says 

```
ndiswrapper (set_essid:61): setting essid failed (00010003)
```

i can still see the networks available when i scan wlan0, i can choose it in the "networking" gui, i can enter my WEP string, but i still can't connect. this is really annoying...

---

### Post by wieman01 on 2006-09-28
Could you please show us your "interfaces" file again? Please also upload a screenshot of your router's wireless security page... Just to get an idea of what's going on.

---

### Post by vynsane on 2006-09-28
tried the other driver that was available on the ndiswrapper installation wiki, and it still won't work... it does all the same stuff that the other driver did: scan shows the networks, but can't connect.

interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Spidey
wireless-key C654AD9154D87A1C051DF274D

```

the screenie of my wireless security page is here

[www.vynsane.com/pictures/linksys.jpg](www.vynsane.com/pictures/linksys.jpg)

also tried to reset the router by unplugging/plugging to no avail. maybe i should play around with firmware on the router - i had hyperWRT tofu installed on it for a while... (bought the router because it ran linux so i could do stuff like that...) it may give me more options that way...

---

### Post by wieman01 on 2006-09-28
Nevertheless, could you show me this once again:
> iwlist wlan0 scan
> sudo /etc/init.d/networking restart
I think we're close. I have the same router and used to use WEP as well.

---

### Post by wieman01 on 2006-09-28
And again...

1. No MAC filering?
2. Definitely DHCP?
3. No "wireless assistant" or "wifi-radar"?
4. No tool called "NetworkManager"?
5. No firewall (e.g. Firestarter)?

---

### Post by vynsane on 2006-09-28
> **wieman01 said:**
> Nevertheless, could you show me this once again:
 
iwlist wlan0 scan

sudo /etc/init.d/networking restart

I think we're close. I have the same router and used to use WEP as well.

you have the WRT54GL? i initially bought it to put HyperWRT on it so i could use it as a wireless ethernet bridge to connect a downstairs network to an upstairs one without running wires all over the place. worked great! i reinstalled the factory firmware when i moved out of there, though.

i'll check that out when i get home. i just got to work. thanks for powering through this with me! ](*,) 

> **wieman01 said:**
> And again...

1. No MAC filering?

nope.

> 2. Definitely DHCP?

yep, should be.

> 
3. No "wireless assistant" or "wifi-radar"?
4. No tool called "NetworkManager"?
5. No firewall (e.g. Firestarter)?

clean install of xubuntu - doesn't have those apps that i know of.

thanks again, wieman01!

---

### Post by wieman01 on 2006-09-28
No problem. Run the 2 commands shown above and we'll see what's going on. Have a good day & see you soon (it's evening here...).

---

### Post by vynsane on 2006-09-28
okay, time for my afternoon and your morning post, wieman...

iwlist wlan0 scan reveals:

```

Cell 01 - Address: 00:14:BF:BA:7B:17
Protocol: IEEE 802.11g
Mode: Managed
Frequency: 2.412 GHz (Channel 1)
Quality:0/100  Signal level:-10 dBm  Noise level:-256 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2Mb/s; 5.5Mb/s; 11Mb/s; 18Mb/s;
          24Mb/s; 36Mb/s; 54Mb/s; 6Mb/s; 9Mb/s;
          12Mb/s; 48Mb/s;
Extra:bcn_int=100
Extra:atim=0

(and the other networks in the area, but i don't want to connect to them...)

```

networking restart yields:

```

 * Reconfiguring network interfaces...
Internet systems blahblahblah...

Listening on LPF/wlan0/00:0f:66:3a:6f:fa
Sending on   LPF/wlan0/00:0f:66:3a:6f:fa
Sending on   Socket/fallbck
internet systems bla blah blah...

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: no such device
Failed to bring up eth0

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: no such device
Failed to bring up eth1

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: no such device
Failed to bring up eth2

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: no such device
Failed to bring up ath0

Listening on LPF/wlan0/00:0f:66:6f:fa
Sending on   LPF/wlan0/00:0f:66:6f:fa
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

now, looking at this and my main configuration page for the router, is this the right subnet mask? my router is set to 255.255.255.0, and i don't have an option for 255.255.255.255. how would i change it to look for 255.255.255.0 if i need to do so?

---

### Post by wieman01 on 2006-09-28
Good morning!

255.255.255.255 is correct. It's different from the subnet mask, confused the hell out of me in the beginning as well. Let me think for a minute though...

---

### Post by wieman01 on 2006-09-28
One thing... Do you know why your router says:
> Quality:0/100
The link quality is 0, plus I cannot see your network's name ("Spidey"). Would restarting/rebooting the router help? Odd... But be careful, if you reboot you lose all your precious settings (WEP, ISP, etc.).

---

### Post by kikos on 2006-09-28
For the past few days my wireless has had severe connection and disconnect problems.  dhclient was the issue for me. By killing dhclient and NOT replugging my ethernet back in, my wireless has been rock solid using ndiswrapper all day today.  Below are some dhclient tips that may help you solve your problem.

Some background on my setup:  My wirelss hardware is Broadcom 4306 a/k/a Dell TruMobile 1450.  I have ndiswrapper bound to the bcmwl5 driver.  I also have the bcm43xx module loaded.  I had tried wifi-radar and network-manager, but they proved problematice, so I removed both of them.  I purely use ndiswrapper.  
---
Basic info about dhclient

I'm not sure if this has been mentioned in the thread or not.  dhclient records the DHCP lease for each interface in var/lib/dhcp3/dhclient.leases and /var/lib/dhcp3/dhclient.*YOUR_INTERFACE*.leases

dhclient writes its log to /var/log/daemon.log which may be useful for debugging purposes

----
Make Sure dhclient Is Not Confused

I've read that dhclient can get confused if you switch between using your ethernet interface and your wireless interface.  The result is frequent dropped wireless connections or the inability to connect wirelessly.   

You can see what interfaces are currently configured by dhcp by looking in the folder /var/run.  In that folder you may see files which indicate that dhclient is currently configured for interfaces.  i.e. you may see /var/run/dhclient.eth0.pid

(1) Bring both the ethernet and wireless interfaces down by using: ```
ifconfig *YOUR_INTERFACE* down
```.  

(2) Kill dhclient to make sure it's not running using:
```
killall -9 dhclient.pid
kill all -9 dhclient.*YOUR_INTERFACE*.pid
```

(3)Also, clean things up by removing the dhclient pid's from /var/run by using:

```
rm -f /var/run/dhclient.*YOUR_INTERFACE*.pid
```

(4) Use a text editor to clear ALL text from var/lib/dhcp3/dhclient.leases and /var/lib/dhcp3/dhclient.*YOUR_INTERFACE*.leases

(5) By now, dhclient should have been thoroughly killed.  Use ifconfig to bring only the wireless interface back up.  If you have a network applet in your task bar, you should notice your wireless interface being set up.  

(6) After a minute or two, check /var/log/daemon.log, var/lib/dhcp3/dhclient.leases, and /var/lib/dhcp3/dhclient.*YOUR_INTERFACE*.leases to see if dhclient is making any progress in getting an ip address from your access point.

---

### Post by vynsane on 2006-09-28
> **wieman01 said:**
> One thing... Do you know why your router says:

The link quality is 0, plus I cannot see your network's name ("Spidey"). Would restarting/rebooting the router help? Odd... But be careful, if you reboot you lose all your precious settings (WEP, ISP, etc.).

good evening!

i've tried unplugging/plugging the router before. might as well try again! or are you saying set it back to "factory defaults"? could try that one...

i find i odd as well that it tunes to the right frequency, but can't access the AP, get the ESSID, or get any link quality at all... although i DON'T find it odd, because that's the whole problem in the first place! it's not getting any signal at all for some reason...

> **kikos said:**
> 
Basic info about dhclient

I'm not sure if this has been mentioned in the thread or not.  dhclient records the DHCP lease for each interface in var/lib/dhcp3/dhclient.leases and /var/lib/dhcp3/dhclient.*YOUR_INTERFACE*.leases

interesting info... but it won't help me because both of those files are empty. i'm not getting any DHCPOFFERS so it won't have anything to write to them!

**EDIT** i'm trying all the different permutations of the iwconfig wlan0 commands and it appears the only thing i can change is from "managed" to "ad-hoc" - all other commands i use say 

```

Error for wireless request "Set Frequency" (8B04) :
   SET failed on device wlan0 ; Invalid argument.

```

or just do nothing at all, like "iwconfig wlan0 essid spidey".

---

### Post by wieman01 on 2006-09-28
Can you unplug and plug in your wireless device? Perhaps that's it then? I don't see any reason why it should not work at this moment...

Please also check if everything seems fine with the router's settings.

---

### Post by wieman01 on 2006-09-28
One important thing: Do other wireless networks around have the same problem (quality = 0)? If NOT, then there is definitely something wrong with your router (can't be the card in this case). You know what I mean?

---

### Post by vynsane on 2006-09-28
> **wieman01 said:**
> Can you unplug and plug in your wireless device? Perhaps that's it then? I don't see any reason why it should not work at this moment...

Please also check if everything seems fine with the router's settings.

i reset to factory settings, and set everything up back to the way it was, anything that was new i tried to change in iwconfig and DID in the "networking" gui... still nothing.

> **wieman01 said:**
> One important thing: Do other wireless networks around have the same problem (quality = 0)? If NOT, then there is definitely something wrong with your router (can't be the card in this case). You know what I mean?

yeah, they're all 0/100.

weird thing that's happening with iwconfig is that i get the error message above, but then it DOES apply the new frequency...but when i check out dmesg, it says 

```

ndiswrapper (iw_set_freq:375): setting configuration failed (C0010015)

```

similar to 

```

ndiswrapper (set_essid:61): setting essid failed (00010003)

```

unlike the essid, however, when i check out iwconfig wlan0 it shows that the frequency HAS changed... at least on screen. so it this a problem with ndiswrapper, or iwconfig? should i be using a newer version of ndiswrapper?

---

### Post by wieman01 on 2006-09-28
I think it now boils down to your wireless card. If all are **0/100** then that's a pretty good sign "ndiswrapper" has failed. All the (wireless & security) settings are definitely correct.

Resetting the router won't help in this case.

Now I suggest that we go through the "ndiswrapper" installation process once again & pay attention to possible error messages, etc. That's the only option we've got right now.

Want to try?

---

### Post by vynsane on 2006-09-28
hey, i'm up for whatever! but tonight i'm decompressing from my wireless woes... by debugging a php script i'm developing to switch stylesheets on my website!

hrm... on second thought that might not be any more relaxing. ;)

---

### Post by vynsane on 2006-09-30
okay, i'm back on the case of this wireless card... i'm thinking it has to do with ndiswrapper, seeing as how i get the error in dmesg that ndiswrapper can't change the essid when i try to do it in iwconfig.

i installed it using the .deb package from help.ubuntu (i think) but i have the tarballed version from the ndiswapper.sourceforge page as well. just couldn't figure out how to install that one...

right now i'm trying to figure out how to delete all the files for ndiswrapper...

**EDIT** deleted all ndiswrapper files, not i have to figure out what the hell 'make install' means and how to do it. i keep getting errors that 'make' isn't a command that's found...

---

### Post by wieman01 on 2006-09-30
Welcome back!

First of all you don't really need to install "ndiswrapper" from source. The debian package is absolutely fine.

As for the error message when you're trying to "make", this has to do with certain packages you'll have to install before you can do that. But that's a different package as we ought to use what's in the repository, ok?

I would guess that something has gone during the deployment of the native Windows driver. Could you try this:

1. Unzip the Windows driver executable:
> unzip <windows_driver>
2. Leave all **ALL** driver files (*.inf, *.sys, *.cab, whatever) in the resulting folder and deploy the *.inf file:
> sudo ndiswrapper -i /path/to/driver/drivername.inf
3. Check if the install has been successful:
> ndiswrapper -l
4. Output should resemble this:
> Installed ndis drivers:
(your driver)  driver present, hardware present
5. The remaining steps (loading driver module) can be found here (*"2.4.2.3. Loading the new driver module"* & below):
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Any error message so far?

---

### Post by vynsane on 2006-09-30
> **wieman01 said:**
> Welcome back!

First of all you don't really need to install "ndiswrapper" from source. The debian package is absolutely fine.

are you sure? i had read somewhere that it wouldn't be the newest version - that the newest version can't be turned into a .deb... i was thinking that it might work with the newer version, but i guess i can retry the install of the .deb.

---

### Post by wieman01 on 2006-09-30
Ok, no, you got me... I am not 100% sure. Ok, give me a few minutes and I tell what packages you need to install for 'make'. :-)

---

### Post by wieman01 on 2006-09-30
This is it:
> sudo apt-get install build-essential

---

### Post by vynsane on 2006-09-30
okay, cool... that worked... but in my zealousness to get rid of ndiswrapper's initial install, i think i deleted a bunch of files i should've left alone. i'm going to do another clean install of xubuntu, and then start on that stuff... i'll get back to you.

thanks again!

---

### Post by wieman01 on 2006-09-30
Oh no... Haha! Ok, no problem. I'll be around. :-) Good luck then.

---

### Post by vynsane on 2006-09-30
yeah, i must have deleted the kernel build file for ndiswrapper... but after a fresh install, i can find it on a "locate ndiswrapper" but i can't point the ndiswrapper v.1.23 installer to get the ndiswrapper.ko file. "make distclean" goes fine, but when i just type "make" i get this error:

```

make -C driver
make[1]: Entereing directory '/home/vyn/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory '/home/vyn/ndiswrapper-1.23/driver'
make: *** [all] Error 2

```

so then i try to point it to the ndiswrapper.ko file (that's what it's looking for, right? not just the base kernel?)

```

vyn@MaryJane:~/ndiswrapper-1.23$ make KBUILD=/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
make -C driver
make[1]: Entering directory '/home/vyn/ndiswrapper-1.23/driver/'
Can't find kernel building files in /lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory '/home/vyn/ndiswrapper-1.23/driver'
make: *** [all] Error 2

```

am i missing the point here? where am i supposed to be sending this thing? and am i doing it right? should it be "make KBUILD=/path/blah/blah" or something else?

---

### Post by wieman01 on 2006-09-30
Yes, you need to install the kernel-headers, etc. Take a glance at the screenshot.

---

### Post by vynsane on 2006-09-30
dang... i'm assuming that's only something that can be installed online? or is it on the ubuntu alt cd? if not, i may have to just go back to the .deb package, as this whole process is trying to get my one working interent connection on this machine up and running! ;)

---

### Post by wieman01 on 2006-09-30
No, it's definitely on the CD... Can you search for the packages?

---

### Post by vynsane on 2006-10-01
which ones of that list do i need? if they're available outside of packet manager, sure...

---

### Post by wieman01 on 2006-10-01
> **vynsane said:**
> which ones of that list do i need? if they're available outside of packet manager, sure...
You definitely need the ones that say *headers*. Try to install them and see if you can compile "ndiswrapper".

---

### Post by vynsane on 2006-10-01
i'm done... i downloaded a bunch of packages, but some of them were dependent on others, and i can't really even be sure that they're the right ones... and this is way too much work to get a card that came free with a router i don't even own anymore to work on a computer that's almost ten years old.

i really appreciate all your guidance, wieman01, but sometimes you gotta know when to throw in the towel... and the time is now. looks like i'll be reading through the list of cards VERY carefully and pick the one with the least painful install.

**EDIT**
okay, well, i just can't admit defeat, so i found linuxant driverloader (unfortunately, you get only a month's worth of testing time, and then you have to buy it...) but it's showing more than ndiswrapper was: i get signal strength recognition when i do iwlist wlan0 scan, and i can change settings in iwconfig, but i still get "no working leases" in dhclient. and my etc/network/interfaces file is strangely absent of any information corresponding to my network.

???

---

### Post by vynsane on 2006-10-01
WOOT! i've got it working now, using driverloader!!! i'm typing this from my laptop right now.

so, for posterity, linuxant.com's driverloader works with the linksys WPC54G version 4 (v.4, ver.4 [- for searches]) using the wlipnds.inf driver.

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

you have to sign up for an account with linuxant to get a free month of testing with the software, after which it's $20 to get the permanent license. but hey, after five re-installs of xubuntu to get a clean base to get this working on, with ndiswrapper not cutting it, for this to work straight away, it's worth the $20.

anyway, after you sign up for the account, they send you a free-trial license that you will use to activate the software for the month. download the .deb package for your chip architecture, and download the driver package for the wpc54g v.4:

[ftp://ftp.linksys.com/pub/network/WPC54G%20v4%20driver%20rev%201.22.1.2004.zip](ftp://ftp.linksys.com/pub/network/WPC54G%20v4%20driver%20rev%201.22.1.2004.zip)

now unpack them both on the computer you want to set up with this card (they're both zip files...) unpack the driverloader .deb (called driverloader_2.34_k2.6.15_26_386_ubuntu_i386 on my machine...) and expand the dialog to watch the terminal process. it will say something about part of the program already installed or something, and you want to tell it to use those. then at the end it will tell you to configure it through your web browser. follow the instructions (you have to go to 127.0.0.1:18020) - this lets you use a graphical install. you can do it through the terminal as well, and there are similar instructions to do so.

after that is done, open a terminal and type "iwlist wlan0 scan" to see if you can access any AP's around you. if you see your router/access point, and all the information is there (especially if it says "link quality: 94/94" or something like that) it's a good sign. mine said 0/100 with ndiswrapper, and i got 94/94 with driverloader.

now go to "desktop menu > system > networking" (in xubuntu, slightly different in k/ubuntu" and you should see "Wireless connection" along with any other internet connections your computer has. you may want to create a name for this profile you are about to create at the top, so you can easily change to another profile when you go somewhere else with a wireless connection.

after creating the profile, select the wlan0, and click on "properties" to configure it: pick the essid of your router, and configure everything you need to (i'm using WEP, so your configuration could be different) and click "OK" - it will give you a progress bar dialogue with the words "activating wlan0" or something to that effect... then click "OK" again to close out the "networking" pane.

open a terminal and run "dhclient" - is should search your AP for an IP address (assuming you have dhcp enabled) and tell you if it does. if it doesn't, you'll get the error that is the name of this thread: "No working leases in persistent database - sleeping" if you get an IP address, you're good to go. if you get the dreaded "no working leases..." then make sure you've got your information correct in the networking dialogue, and make sure your temporary license is correct. also go back to the driverloader config in your browser and check the settings, perhaps something is missing there. you can click on the "advanced" button below the "license key" form field and put right anything that may be amiss. 

anyway, i hope this helps (and makes any sense...) i figure a new card would cost me just as much as registering this software, so i'm happy that i got it working without having to research and find a new card i knew would work.

---

### Post by wieman01 on 2006-10-02
Hello Vynsane, 

What a compelling story indeed! In particular the last bit has been an interesting read. I have never heard of this piece of software called "DriverLoader" but it sounds as if it makes the wireless thing in Linux as easy as it could be. I am impressed.

Glad this has resolved your problem for now. Let me/us know if there is anything else you need. Good fun working with you.

See you! Thread closed I guess?

---

### Post by vynsane on 2006-10-02
yeah, i'm very pleased with the outcome. thanks for sticking it out with me! 

the most interesting part of this "driverloader" is that there are bits of it in the ubuntu installation, apparently... funny that it's not documented more. but i guess full-out support would go against their "totally free" motto. aside from that, and the localhost configuration page, driverloader is very similar in every aspect to ndiswrapper.

at least if nothing else, we have something else to turn wifi woes to!

---

