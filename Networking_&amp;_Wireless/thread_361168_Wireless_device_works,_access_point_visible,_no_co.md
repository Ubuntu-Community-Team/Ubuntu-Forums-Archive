---
title: "Wireless device works, access point visible, no connection"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by wej1971 on 2007-02-14
I have a Belkin wireless USB dongle and have made considerable progress getting it to work since I started, but I'm still stuck at the final step. I can see the wireless device on wlan0 and everything seems to be set correctly: -

sudo iwconfig wlan0 gives: -

IEEE 802.11g ESSID: "conexant"
Mode: Managed Frequency: 2.437 GHz Access Point: 00:0A:E9:02:1F:A6
RTS thr: off Fragment thr=2346 B
Encryption key: off

sudo iwlist scan: -

wlan0 Scan completed
Cell 01 - Address 00:0A:E9:02:1F:A6
ESSID: "conexant"
Mode: Master
Frequency: 2.437 GHz
Encryption key: off

Any ideas why I can see the access point but get no connection? Is there an easy way (from terminal) to test the connection, or is the fact that a browser won't resolve any urls proof enough. Is the fact that the wlan0 says 'Mode: Managed' and the access point says 'Mode: Master' a problem, and if so, what do I do about it?

Help gratefully received...

---

### Post by erkki70 on 2007-02-14
Hi there,
Have you tried to connect like this?
```
sudo dhclient wlan0
```
or if you have a static ip
```
sudo ifconfig wlan0 {IP ADDRESS} up
```
what do you have in the file located at /etc/network/interfaces?

Cheers

---

### Post by wej1971 on 2007-02-14
/etc/network/interfaces gives (relevant bit): -

iface wlan0 inet dhcp
wireless-essid conexant

iface wmaster0 inet dhcp
wireless-essid conexant


sudo dhclient wlan0 gives lots of DHCPDISCOVER messages followed by: -

No DHCPOFFERS received
No working leases in persistent database - sleeping

---

### Post by sdide on 2007-02-14
Can you ping the accesspoint?

---

### Post by wej1971 on 2007-02-14
No, I get connect: Network is unreachable

What other information would be useful to try and determine the cause?

---

### Post by erkki70 on 2007-02-14
> **wej1971 said:**
> /etc/network/interfaces gives (relevant bit): -

iface wlan0 inet dhcp
wireless-essid conexant

iface wmaster0 inet dhcp
wireless-essid conexant


sudo dhclient wlan0 gives lots of DHCPDISCOVER messages followed by: -

No DHCPOFFERS received
No working leases in persistent database - sleeping

Ok, I have a Dlink card with the ralink RT61 driver and from another thread this solution wa given:
```
 sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv wlan0 set AuthMode=SHARED
sudo iwpriv wlan0 set EncrypType=NONE
sudo iwpriv wlan0 set Key1=<my wep key>
sudo iwpriv wlan0 set SSID=<my essid>
```Adapt to your needs.

The original thread is here:
[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

Hope it helps.

---

### Post by wej1971 on 2007-02-14
Before I type this in, a couple of questions: -

What is NetworkType=Infra and why ra0?
I have no encryption - just skip this line?

---

### Post by wej1971 on 2007-02-14
1st command gives: -

ra0          No private ioctls

---

### Post by wej1971 on 2007-02-14
If I do sudo iwpriv wlan0 set <....> i get 'Invalid command: set'

---

### Post by erkki70 on 2007-02-14
Oops!
Sorry ra0 is for my card yours should be wlan0, so:
```
sudo iwpriv wlan0 set NetworkType=Infra
```

---

### Post by erkki70 on 2007-02-14
> **wej1971 said:**
> Before I type this in, a couple of questions: -

What is NetworkType=Infra and why ra0?
I have no encryption - just skip this line?

ra0 in your case is wlan0
Keep the line even though you don't have encryption. Mine reads EncrypType=WEP.

---

### Post by wej1971 on 2007-02-14
sudo iwpriv wlan0 set NetworkType=Infra gives me 'Invalid command: set'

---

### Post by wej1971 on 2007-02-14
I get 'Invalid command: Set'

---

### Post by wej1971 on 2007-02-14
I appear to have hit a dead end - anyone got any last things I can try?

---

### Post by erkki70 on 2007-02-16
> **wej1971 said:**
> I appear to have hit a dead end - anyone got any last things I can try?
Not yet a dead end ;-)
You could try to follow the instruction from the following post:
[http://www.ubuntuforums.org/showthread.php?t=134458](http://www.ubuntuforums.org/showthread.php?t=134458)
Even though it's not the same USB adapter it should also work for you as Belkin USB adapter is found to be working using ndiswrapper driver.
Have a look here:
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Sorry for misleading at the beginning of the post.
I think you should try ndiswrapper, it should work this way.

Good luck and please report any success :-)

Cheers,

---

### Post by [L2G] Slapshot on 2007-02-16
Can you do lsusb from a cli window and tell us the vendor id.
This is my output and I use a Belkin wireless g usb stick to connect also with wep encryption.

Bus 005 Device 003: ID 050d:705a Belkin Components

If yours ends in the same as this :705a

I use the rt73 driver from Ralink and use it with ndiswrapper 1.8 and it's fine. The big thing to get it working is the Ralink driver for these treat the device as a real plug and play so you have to boot without it and let the entire boot process finish even till you have logged in and have the desktop up then plug it in and it should start to flash the green light as it talks to the router.Then  use wireless assistant ( I use this ) to scan and connect to the network. Set it up without wep encryption first and then when it's working add encryption later.

Hope this helps mate
Jacko

---

### Post by wej1971 on 2007-02-19
Interesting - never thought to boot without it plugged in (to be honest it's a pain to get to my usb sockets but I'll try).

The bizarre thing is that sometimes it does work, but then it dies and either never recovers or connects and then disconnects during downloads/browsing.

Oh, and to the previous poster - these problems are with ndiswrapper 1.8 and the rt73 driver - I had no luck at all using the built in drivers.

Let me try a reboot without it plugged in...

---

### Post by wej1971 on 2007-02-19
Ok, I booted without it in and it wasn't working straight off, but then again it seemed to have lost the essid.

I then did this: -

sudo iwconfig wlan0 essid conexant

And it still wasn't working so I did: -

sudo dhclient wlan0

And it worked (and I'm browsing as we speak).

However, the big test will be downloading, because previously this has killed it so we will see....

---

### Post by tyres on 2007-02-19
Hi,

Just to add to what has been said about Ralink drivers for the Belkin G USB (705a) adapter, there is a native Linux Ralink driver (rt73) for this. It means downloading the source (from the Ralink site) and compiling it, but you then don't need to use ndiswrapper. I'm using that successfully myself.

Colin

---

### Post by wej1971 on 2007-02-19
Just out of curiosity, this is my /etc/network/interfaces now - does this look ok?

auto wlan0
iface wlan0 inet dhcp
wireless-essid conexant
wireless-ap 00:0A:E9:02:1F:A6
wireless-freq 2.437G
wireless-key off

Unfortunately it never seems to get the access point without manually specifying the address. 

Given that I'm not going to have it plugged in when I boot, what will i need to do to get it working assuming these settings take? Will it just be sudo dhclient wlan0?

---

### Post by erkki70 on 2007-02-19
> **wej1971 said:**
> 
Given that I'm not going to have it plugged in when I boot, what will i need to do to get it working assuming these settings take? Will it just be sudo dhclient wlan0?

Hi again!
Good to know you got working ;-)

```
sudo ifup wlan0
``` should do the trick once you plug the adapter in I suppose...

---

### Post by wej1971 on 2007-02-19
Scarily it's still working, despite having done some serious downloading and switching from Gnome to Kubuntu desktops.

The real test will be to reboot without it in, do the ifup and see what happens.

For the moment /me is happy.

Oh, and I may try the native ralink driver, but while things are working... ;)

---

### Post by tyres on 2007-02-19
Your interfaces settings look about right. I have 'auto wlan0' at the end, rather than at the start. Not sure if that makes any difference. 

What happens if you set a static IP address, netmask and gateway, as it looks like maybe dhcp isn't working properly?

Colin

---

### Post by wej1971 on 2007-02-19
Thing is, dhcp *is* working because I'm getting an IP address allocated, it just seems to require me to assign the access point mac address and essid manually each time. Still, if it does it consistently then I don't care.

What does auto wlan0 do and does it make a difference whether it's at the beginning or the end of the configuration settings?

---

