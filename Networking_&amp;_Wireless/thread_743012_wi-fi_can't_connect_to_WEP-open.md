---
title: "wi-fi: can't connect to WEP-open"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by meep_meep on 2008-04-02
Hi guys and girls,

I've been trying for a while now to connect to WEP-open with my belkin rt2500 card using Rutilt.

I can connect to any open networks but when I change my router back to WEP-open encryption then it doesn't connect any more.

when running rutilt, the terminal gives this

```

There is already a pid file /var/run/dhclient.pid with pid 21065
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/**mac address**
Sending on   LPF/ra0/**mac address**
Sending on   Socket/fallback
DHCPREQUEST on ra0 to **ip address** port 67
DHCPREQUEST on ra0 to **ip address**  port 67
DHCPDISCOVER on ra0 to **ip address**  port 67 interval 8
DHCPDISCOVER on ra0 to **ip address**  port 67 interval 15
DHCPDISCOVER on ra0 to **ip address**  port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease **ip address** 
PING **ip address**  (**ip address** ) 56(84) bytes of data.

--- **ip address**  ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


```


I don't know much about networking so I didnt include any of the addresses just in case...

Is my problem to do with my wi-fi card or my router?

any help would be greatly appreciated!

---

### Post by dannyboy79 on 2008-04-02
what key are you using within your /etc/network/interfaces file? I had to make sure I was using a HEX key that my router came up with. Mine is 128bit WEP encryption, so there's 26 hex characters.

it looks like this:

auto wlan0
iface wlan0 inet static
address 192.168.0.6
netmask 255.255.255.0
network 192.168.0.1
gateway 192.168.0.1
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid ?????????
        pre-up iwconfig wlan0 mode Managed
        pre-up iwconfig wlan0 key xxxxxxxxxxxxxxxxxxxxxxx

I also use static IP because it's a server. Your's would just have auto ra0 instead of wlan0.

Are you sure that driver works on open networks because I use the rt73 module and te rt73usb module that comes with Ubuntu hasn't worked ever, they are still even having issues with it in Hardy. Here's a thread about using the serialmonkey drivers for your rt61 wifi adapter

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by meep_meep on 2008-04-02
Thanks dannyboy79 for the quick response!

I tried it on a network which was completely open with no security what so ever and that worked.

I installed the new drivers using this 
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#compile](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#compile)

I set my /etc/network/interfaces file to 'auto ra0'  but I changed it using the network manager applet.

```


iface ra0 inet dhcp
wireless-essid *network name*
wireless-key s:*key*

auto ra0

```

my network using a password of 11 numbers, so I'm guessing that its a ascii key and not a hexadecimal one.

---

### Post by dannyboy79 on 2008-04-02
so is it working? if it's 11 digits than it's possible that you're using 64bit encryption. also, I think you need to auto ra0 before everything just like my example.

---

### Post by meep_meep on 2008-04-02
I moved the auto ra0 before everything  but that didnt help.

I still cannot connect.  You're probably right that I have 64-bit encryption but I cant see any options to choose between different types of encryptions.

btw I've got two wireless cards, the other one is 'eth1' and is an intel card but i've never got it to work.  Even in windows with the official drivers.

When using RutilT, my card shows up under Network Tools as ra0:avahi not ra0.

Is there anything else that I can try?

Thanks for you help

Meep

---

### Post by meep_meep on 2008-04-02
woooooohooooo

I just got it to work, 

I changed my 'interfaces' file to include

```

auto ra0:avahi
iface ra0:avahi inet dhcp
wireless-essid ********
wireless-key s:*******

```


and it worked!!!!!

Thanks for you help btw

---

### Post by dannyboy79 on 2008-04-02
glad you got it sorted out. can you mark it solved?

---

### Post by meep_meep on 2008-04-02
i think that I was a noob earlier.  I actually got it to work because my key is ascii but it was in numbers or something.  So i entered it as numbers with the ascii box unticked in RutilT and it was then convert to some other odd symbols but it works now!!  

I also have to enter my password every time I log on which is a bit annoying.

---

