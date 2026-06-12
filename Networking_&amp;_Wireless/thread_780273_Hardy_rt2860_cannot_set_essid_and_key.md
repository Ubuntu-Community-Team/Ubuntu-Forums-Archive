---
title: "Hardy rt2860 cannot set essid and key"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by laoshi on 2008-05-03
Am using Hardy on Znote 3215W with zpro2 wireless card. For the last 14 days I have tried to get it to work, searched forums and tried solutions, but to no avail. At the moment the situation is this: I have installed windowsdrivers from ralinktech with ndiswrapper. 

$ndiswrapper -l tells me:
rt 2860 driver installed
device (1814:0781) present

After trying network tools and wicd I have stuck with wicd. It is able to find wireless networks, included my own, but not to connect. The problem seems to be that essid is set to "any" and encryption to "off". But not in the GUI - essid and key show up! I try to set essid and key with
iwconfig, and I get no error messages. But when checking again with iwconfig nothing is changed. It is still essid any and key off.

Any suggestions as to how and where I can set the correct parameters?

Luckily my cabled network is ok - but I'd like to get rid of the cables...

---

### Post by xodeus on 2008-05-05
I've had the same problems on the same laptop, but I've tried the ralinks own driver compiled on my machine. Networks showing fine in wicd, but can't connect, even to a network without encryption...
That's too strange...

---

### Post by chili555 on 2008-05-05
Please detach the cable, so NetworkManager doesn't get confused and do:```
sudo iwconfig ra0 essid <ur_essid>
sudo iwconfig ra0 key <ur_key>
sudo dhclient ra0
```I don't believe *iwconfig* will show the details until you actually connect. Substitute your wireless interface if it's not ra0.

---

### Post by laoshi on 2008-05-05
Thanks for your advice. I have tried, but no luck.
iwconfig still says:

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point:Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And I get no connection.

When trying to set the key I get the following message:

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
And when after all trying dhclient wlan0 I am told:

Listening on LPF/wlan0/00:15:af:9e:89:de
Sending on   LPF/wlan0/00:15:af:9e:89:de
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have tried editing /etc/network/interfaces like this:

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless-key <my_key>
wireless-essid <my_essid>

but still no luck.

---

### Post by chili555 on 2008-05-05
Sometimes wireless cards respond better to:```
sudo iwconfig ra0 essid <ur_essid>
sudo iwconfig ra0 key <ur_key>
sudo ifup ra0
```You might also try:```
sudo /etc/init.d/networking restart
```Is your router set up with 'Shared Key?' If it is, amend *interfaces* thus:```
auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless-key <my_key> **restricted**
wireless-essid <my_essid>

```We're close!

---

### Post by laoshi on 2008-05-05
I sure hope we are.... but it still doesn't work. 
However, when restarting networking this is what I get:

Listening on LPF/wlan0/00:15:af:9e:89:de
Sending on   LPF/wlan0/00:15:af:9e:89:de
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072

Does the error ring a bell for you?

What I don't understand (among so much else) is the fact that whatever I put into the /etc/network/interfaces file does not show up in iwconfig - it is still essid any and key off! 
Midnight is approaching in Denmark and I have to get up in the morning, so I am logging off for now - but will return for more inspiration tomorrow

---

### Post by chili555 on 2008-05-05
> Does the error ring a bell for you?Slightly. Please comment out mode thus:```
auto wlan0
iface wlan0 inet dhcp
#wireless_mode managed
wireless-key <my_key> 
wireless-essid <my_essid>
```Restart networking and let's see what happens.> whatever I put into the /etc/network/interfaces file does not show up in iwconfigI don't believe it's going to appear until you actually connect.

Have a good evening and we'll check in tomorrow.

---

### Post by laoshi on 2008-05-06
OK - i have been at it again:
[LIST]
[*]Outcommented wireless-mode in /etc/network/interfaces
[*]Did ifdown eth0 and then ifup wlan0 and got message:
[/LIST]
> ifup: interface wlan0 already configured
[LIST]
[*]Then ifdown eth0 and wlan0
[*]Then /etc/init.d/networking restart
[/LIST]
Absolutely no change in message

> Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
...
and then listening and sending, and no dhcpoffers received and No working leases in persistent database - sleeping.

--

I think that we need to fix the reported error:

> Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
	There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072 
What i&#347; the invalid argument, and where does the set command come from?

By the way the set failed message is identical to the one I get when using iwconfig.
> iwconfig wlan0 essid XXXXXX 
returns a blank prompt - 
but > iwconfig wlan0 key XXXXXXX returns the error message

But I have no clue as to where and how to fix this error.

---

### Post by chili555 on 2008-05-06
> Error for wireless request "Set Encode" (8B2A)Are you sure your encryption is WEP? This command, and the corresponding lines in *interfaces* file, is appropriate for 64- or 128-bit HEX (not ASCII) WEP, using 10 or 26 characters. Is that what you have?

---

### Post by laoshi on 2008-05-06
The router is Linksys WRT54G, mixed mode, mac-filter off, dhcp enabled, ssid used not to be broadcast but is at the moment. And encryption is WEP 64bits 10 hexdigits. I have input the key in ascii but prefaced by s: which should work. But will try to convert keystring to hex and see if that works.
For your information I have gathered this from netstat route table:

> Destination	Adgangspunkt	Netmaske	Grænseflade
192.168.1.0	0.0.0.0		255.255.255.0	eth0
169.254.0.0	0.0.0.0		255.255.0.0	wlan0
0.0.0.0		192.168.1.1	0.0.0.0		eth0
0.0.0.0		0.0.0.0		0.0.0.0		wlan0

How destination 169.254.0.0 for wlan0 comes into the picture I don't see.

---

### Post by chili555 on 2008-05-06
> encryption is WEP 64bits 10 hexdigits. I have input the key in asciiThese two are inconsistent. I won't say this will *never* work, but probably never.

I have a WRT54G as well. What you want is in the administration pages [http://192.168.1.1](http://192.168.1.1), probably, under Wireless -> Wireless Security. If, after Key 1, the little box has, as an example, 98b7a2311f, then you want in your command and in *interfaces* 98b7a2311f. No more, no less. If Key 1 is not checked as the transmit key, but, for example, key 3, then add the identifier thus:```
auto wlan0
iface wlan0 inet dhcp
#wireless_mode managed
wireless-key  [3] 98b7a2311f
wireless-essid <my_essid>
```169.254.x.x is a placeholder the system assigns when a valid outside IP address cannot be obtained. I call it '169.254.boo.hoo.'

---

### Post by laoshi on 2008-05-06
YES. This is it. Everything is working just fine now. The problem was different notation of the key. In the router setup it is output as a series of 10 ordinary letters and digits - so when I tried to set the key in iwconfig (or network-tools) I put them in as an ascii string (prefixed by s: in iwconfig, and with the choice of WEP ascii in network-tools). The moment I chose WEP hex in network-tools the connection worked like a dream.
So thank you chili555 for your patience and assistance.

---

### Post by chili555 on 2008-05-06
Glad it's working! WEP and patience are my specialties!

---

### Post by zacktu on 2008-05-06
I have a Cisco WRT54G also.  I've been using the router with MS Windows computers and WEP with no difficulty. I can connect my laptop running xubuntu with wired and wireless as long as I don't use WEP.   

In my case, Network Manager appears to be setting the interfaces file exactly as you have specified.  (In my case, wireless mode is not set to managed in the interfaces file, so I don't need to comment it out.)  Nevertheless, when I execute iwconfig, it reports that the wireless mode is managed.  Is that set somewhere else?

If you'd like to see the response that I get when i try to restart networking, I'll reproduce it for you. 

Thanks for your help.

---

### Post by chili555 on 2008-05-06
> the wireless mode is managed. Is that set somewhere else?Yes, it's set by default; you only need to specify 'mode' if you are doing something unusual, like making you Ubuntu box into an access point, and if your wireless card and driver support it.> If you'd like to see the responseMay I assume it just doesn't connect? When you check your administration page in the router, is it set to transmit key #1? Shared Key or Auto? WEP key and ESSID double-checked?

---

### Post by zacktu on 2008-05-07
May I assume it just doesn't connect? When you check your administration page in the router, is it set to transmit key #1? Shared Key or Auto? WEP key and ESSID double-checked?

Yes, it just doesn't connect.

The router is set to transmit key #1.

Authentication type is set to Auto.

I can see the ESSID and WEP key in the interfaces file, and they match the values in the router.

---

### Post by chili555 on 2008-05-07
May I please see your *interfaces* file? Please X-out half of your key. Is the case correct in the ESSID? Linksys or linksys or LINKSYS? All of these are different ESSID's as far as Linux is concerned.

---

### Post by zacktu on 2008-05-07
Here's the *interfaces* file.

[INDENT]auto lo
iface lo inet loopback




iface eth1 inet dhcp
wireless-key FXCXD6X3X4
wireless-essid JuniperRidge

auto eth1[/INDENT]


The hex characters are shown as capital letters on the router.  In actuality, I've tried all caps and all lower case as the key in Network Manager.

---

### Post by chili555 on 2008-05-07
It only looks perfect! This thing ought to connect instantly! Let's take a look at:```
dmesg | grep eth1 | less
```There will be tons of output, but we are looking for this stuff, where it connects, or not:> [  843.071462] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  843.179955] eth1: Initial auth_alg=0
[  843.179964] eth1: authenticate with AP 00:0c:41:19:58:77
[  843.181231] eth1: RX authentication from 00:0c:41:19:58:77 (alg=0 transaction=2 status=13)
[  843.181237] eth1: AP denied authentication (auth_alg=0 code=13)
[  843.181241] eth1: set auth_alg=1 for next try
[  843.187269] eth1: authenticate with AP 00:0c:41:19:58:77
[  843.187922] eth1: RX authentication from 00:0c:41:19:58:77 (alg=1 transaction=2 status=0)
[  843.187928] eth1: replying to auth challenge
[  843.189629] eth1: RX authentication from 00:0c:41:19:58:77 (alg=1 transaction=4 status=0)
[  843.189635] eth1: authenticated
[  843.189639] eth1: associate with AP 00:0c:41:19:58:77
[  843.191119] eth1: RX AssocResp from 00:0c:41:19:58:77 (capab=0x411 status=0 aid=2)
[  843.191125] eth1: associated
[  843.194669] ADDRCONF(NETDEV_CHANGE): eth1: link becomes readyI hope we can see what's going awry.

---

### Post by zacktu on 2008-05-09
Here's what dmesg shows:

[   59.791246] udev: renamed network interface eth0 to eth1
[   69.084634] airo(eth1): cmd:103 status:7f03 rsp0:2 rsp1:21c rsp2:0
[   70.288888] airo(eth1): cmd:21 status:7f21 rsp0:4 rsp1:21c rsp2:0
[   80.190325] eth1: no IPv6 routers present

I hope that's helpful.  Is this an xubuntu problem?

By the way, this laptop has PCMCIA cards that I must physically swap when using wired or wireless.  It's only when using the wireless card with WEP encoding that I have a problem, however.

I also have a ubuntu cd that I used a modern laptop (running from the CD -- no install) with the same router.  I set up WEP with the network manager and had no problem connecting.

---

### Post by chili555 on 2008-05-09
airo? Did you say Aironet? This is, I believe, very helpful. Please see here: [http://ubuntuforums.org/showthread.php?t=409247&highlight=Aironet](http://ubuntuforums.org/showthread.php?t=409247&highlight=Aironet)

Post #9 is what got my Aironet working well. Please try it and let us know.

---

### Post by zacktu on 2008-05-10
Everything works now.  *ifup* reads the interfaces file, and all the parameters are set correctly.  I'm posting this from my laptop using wireless with encryption! 

Thanks for helping me.  Because someone replied to my forum post, a favorite old laptop of mine will have a new life!

---

### Post by maryyeta on 2008-06-12
Sadly, I've not so much luck!

I've bought a medion sim210 laptop with the card Realtek RTL8111/8168B.
I've managed to install the drivers from realtek (following your nice tips) and now I've got my interface ra0 configured. HOWEVER, I'm unable to connect to my wifi network.

iwconfig shows essid:"", key:off. When I try to configure it, iwconfig ignores the commands, but iwlist scan detects my wifi network, wifi key (WEP hex), and even que quality of the signal, all assigned to my ra0.

Quite bizarre all that, isn't it?
I dont know what to do... any ideas? I need my wifi network...

thanks in advance

---

