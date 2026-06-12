---
title: "Set WEP key index automatically"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by dulljeff on 2006-11-05
Hello,

after installing XUbuntu 6.10 I noticed my wifi adapter was installed fine yet I didn't have a connection to the internet or the router.

After trying and searching I found out this was because of my WEP key being set at second index. Now I can set up my wlan manually by typing the following commands:
```
iwconfig eth1 key [2] xxxxxxxxx
iwconfig eth1 key [2]
dhclient eth1
```
How can I have this be done automatically at startup or is there another way to apply these settings?

Cheers,
Dulljeff

---

### Post by dulljeff on 2006-11-10
Come on, this must be an easy task for most of you guys.
Can I somehow put this into an automatically starting script?

---

### Post by FrodoB on 2006-11-10
Post the contents of /etc/networks/interfaces

---

### Post by dulljeff on 2006-11-10
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by FrodoB on 2006-11-10
OK, that was not what I had expected, please post the output from dmesg and iwconfig before you manually fix it. 

Thanks,

FrodoB

---

### Post by dulljeff on 2006-11-10
Ok, here's the output of iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

The dmesg output is a little long, so I attached it (zipped).

Thanks for your helpfulness btw.

---

### Post by FrodoB on 2006-11-10
OK, this is Xubuntu not Ubuntu. I don't know what utility you may have to setup you network, but just hand edit the /etc/network/interfaces file and put in a record like this and remove any other references to eth1 (backup the original before doing this!):

iface eth1 inet dhcp
wireless-essid Actual_ESSID_NAME
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto eth1

Change the ESSID and key to suit your situation.

Put this in a terminal window to edit it:

sudo gedit /etc/network/interfaces

Save a copy as interfaces.org then browse back and edit interfaces.

Reboot and lets see what happens.

---

### Post by dulljeff on 2006-11-10
Thanks for the hint, I looked a it in the man pages for wireless and interfaces. Also wireless-tools readme was helpful.
My interfaces file looks like this now: ```
iface eth1 inet dhcp
wireless-essid my_essid
wireless-key2 abcdefgh
wireless-defaultkey 2
wireless-keymode open
```
Unfortunately it still doesn't work and I cannot figure out what I'm doing wrong. I tried to only request an IP address but there doesn't seem to even be a physical connection to the router.

Do you have a further hint? Shall I post any other output or configuration?

---

### Post by FrodoB on 2006-11-10
Did you try exactly what I told you to do and then test it? 

You do not have to call it wireless-key2 on the client side, just make wireless-key exactly the key that is active on the access point.

iface eth1 inet dhcp
wireless-essid Actual_ESSID_NAME
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto eth1

Also, you should probably just turn off WEP on your access point router and then you just need:

iface eth1 inet dhcp
wireless-essid Actual_ESSID_NAME
auto eth1

That should connect from what you say.

Let's see what iwconfig shows.

---

### Post by dulljeff on 2006-11-11
No, I didn't, but now I did.
It still doesn't work :mad: 

It is not my WLAN, I am just granted access to it, otherwise I would have switched to first key long ago.

The output of iwconfig is:```
eth1    IEEE 802.11b  ESSID:"StArLiGhTcommand"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:BF:47:7F:E4   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Btw, I switched to Ubuntu from XUbuntu if that is of any interest. Network manager doesn't do the trick though.

---

### Post by FrodoB on 2006-11-11
Well it says that you are connected now. What does netstat -rn show? Seems to be doing what we were wanting so far.

---

### Post by dulljeff on 2006-11-11
```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
```This is what it says.

---

### Post by FrodoB on 2006-11-11
Have you tried a:

$ sudo dhclient eth1

Hopefully it will get an address from your router's dhcp server. Let's see the output.

---

### Post by dulljeff on 2006-11-12
Yes, I've tried that, but I don't receive an IP address.
The output is:```
sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:80:01:27
Sending on   LPF/eth1/00:04:23:80:01:27
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.2.106
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

---

### Post by FrodoB on 2006-11-12
Have you checked your router to see if you have MAC filtering on or dhcp turned off?

---

### Post by dulljeff on 2006-11-12
WLAN works fine in Windows. There is no MAC address filter and with a Windows PC I receive an IP address.

---

### Post by dulljeff on 2006-11-12
It works now! Finally! Man, I'm so glad!

The relevant part of my interfaces file looks like this now:```
auto eth1
iface eth1 inet dhcp
        wireless-essid my_essid
        wireless-key2 my_second_key
        wireless-defaultkey 2

```

And it works fine after startup.

Thanks for your patient help, FrodoB! You gave me valuable hints.

---

### Post by FrodoB on 2006-11-12
Wow! That is great. Document what you had to do. Good job.

---

### Post by Oblivionvlad on 2007-08-31
Ok, I know this is a very old topic but maybe someone will bother answering this question:

I have kubuntu 7.04. I need to have wireless access in two networks, one at home and one at work. The one at work needs a key index different from 1 so the configuration wizard in knetworkmanager doesn't work. So I need to manually configure the key and index in the /etc/network/interfaces file. The network at work starts ok but now I can't connect to the one at home automatically. If I let the config file alone and use the graphical wizard I can connect to any normal network except the one at work.

Can I manually configure two networks in the /etc/network/interfaces file so that the laptop connects automatically to the one where it is located (home or work)? Is there any way to achieve what I want?

Is there a patch for the knetworkmanager to get the setting for the index key? It really seems like an extremely easy change to do to add that setting. As an aside question: where does knetworkmanager store it's settings?

---

