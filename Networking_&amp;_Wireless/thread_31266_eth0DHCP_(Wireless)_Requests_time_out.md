---
title: "eth0/DHCP (Wireless) Requests time out"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by ifrflyer on 2005-05-02
After posting [here](http://ubuntuforums.org/showthread.php?t=25398), [here](http://ubuntuforums.org/showthread.php?t=30856) and [here](http://ubuntuforums.org/showthread.php?t=30671) and emailing and chatting with others, I have now disabled Ubuntu's  "automatic" configuration and several third party GUI attempts to work around my inability to reliably connect to a simple wireless network with or without encryption. 

My card is supported (it is an  Intel PRO/Wireless 2200 (Centrino) ipw2200 which, according to the [Ubuntu Hardware Suport Wifi Network Cards wiki](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards), works out of the box, works on installed systems and works for network installs and is, "Automatically detected since the first installation steps, even asking for the WEP key") and functions perfectly well until it does not. This is excrutiating.

I am doing the following to get eth0, which is my wifi card, to connect with intermitent and unpredictable success and, frustratingly, mystifying disconnects followed by inability to reconnect by any means short of restarting the machine:

```
iwconfig eth0 essid MY-ESSID
iwconfig eth0 key WEP-KEY
iwconfig eth0 key restricted
iwconfig eth0 ap ACCESS-POINT-MAC
```

then when I do

```
iwlist eth0 scanning
```

And I see a list of four networks, one of them corresponding **precisely** to the settings in the essid above. I then hit


```
sudo /sbin/dhclient eth0
```

And then... 

```

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All Rights Reserved.
For info, please visit http://www.isc.org/prodcts/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:12:f0:0c:59:1a
Sending on LPF/eth0/00:12:f0:0c:59:1a
Sending on Socket/Fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFES received.
Trying recorded lease 192.168.1.163
PING 192.18.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.18.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
Trying recorded lease 192.168.1.161
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

Understand, this is the *SAME* code which provided a working connection YESTERDAY. 

This is so *fiendishly* , keenly frustrating that I am really at a loss as to how to proceed. Some other things which do nothing to rectify the situation:

```
sudo /etc/init.d/networking restart
```

or

```
sudo ifdown eth0 && ifup eth0
```


In fact the only thing which seems to work *more often than not* yet not always, is restarting the machine. 

Frankly there are other operating systems out there which offer that as an alternative, and I don't choose them.

There are no pertinent lines in /var/log/dmesg. 

The only pertinent message in /var/log/messages, as I posted in [this thread](http://ubuntuforums.org/showthread.php?t=30856) are:

Apr 30 15:53:51 localhost kernel: eth0: duplicate address detected!
Apr 30 15:53:54 localhost kernel: eth0: duplicate address detected!
Apr 30 16:51:45 localhost kernel: eth0: duplicate address detected!
Apr 30 16:52:02 localhost kernel: eth0: duplicate address detected!
Apr 30 17:56:29 localhost kernel: eth0: duplicate address detected!
Apr 30 17:56:50 localhost kernel: eth0: duplicate address detected

The connection was up and running for 20 hours from yesterday to today, and there are *no such lines* in the /var/log/messages from that period explaining the sudden loss of networking this morning.

I am fairly desperate for assistance, and I have been posting here for some days with no solution as of yet. I am willing to blame myself, to look things up, to admit user error, to believe without question that it is my ignorance at fault. 

But I honestly would appreciate it if some knowledgable user could please point me in the right direction.

---

### Post by Xerampelinae on 2005-05-02
Is the DHCP client failing to get an IP address, and instead falling back on a previous one... but while using the previous IP address it finds conflicts preventing your machine and another somewhere with the same IP from accessing the net?

If you are in control of this network maybe try a (nonconflicting) static IP as a test.

---

### Post by ifrflyer on 2005-05-02
Actualy I don't have the ability to change this to a static IP here. However I tried it on another networjk and I was able to log in using a static IP address. It seems to be a dhcp issue. But It is intermittant, EXTREMELY frustrating.

This is STILL a Major, and unsolved issue and I would truly truly appreciate any and all help anyone can offer. I am really frustrated. 

Please can anyone offer any assistance?

---

### Post by ifrflyer on 2005-05-09
THis issue is still unsolved. I would really appreciate some help

---

### Post by ifrflyer on 2005-05-09
Another detail: when I run 

```
sudo /sbin/dhclient eth0
```

I get 

```
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776

Listening on LPF/eth0 /00:12:f0:0c:59:1a
```

Before it all craps out yet again after not beng to get a DHCP IP address.

A little help please?

---

### Post by Xerampelinae on 2005-05-09
Maybe try dhcpcd

sudo apt-get install dhcpcd
sudo dhcpcd eth0

Sorry, I'm running out of ideas... :\

---

### Post by ifrflyer on 2005-05-09
Thanks, will try it soon!
I just installed netapplet, but don't hve much faith. . . .  . 

I'll give dhcpd a try. though come to think of it, locate dhcpd shows me

/usr/share/setup-tool-backends/scripts/dhcpd-conf
/usr/share/setup-tool-backends/scripts/dhcpd-pl

So I guess it's here already!

---

### Post by ifrflyer on 2005-05-09
I get: 

dhcpcd - DHCP client for automatically configuring IPv4 networking. 

This requires removal of dhcp3-client ubuntu-base

Not that I'm in any way against that (I'd welcome it) but I wonder if this is dangerous or whether I might be better off with pump?

I'm not asking a loaded question: I honestly have no idea!

Thanks in advance

---

### Post by Psquared on 2005-05-09
Have you checked out the thread about the outdated ipw2200 driver that comes with ubuntu. You can download and install the newer one from source.

Do a search for the thread using "ipw2200" in the search window.

---

### Post by ifrflyer on 2005-05-11
I believe I have the answer and I have written a how to to share it. I can only hope someone makes a sticky 

Problem:
Users of Ubuntu 5.04 with computers which use the Intel® Pro/Wireless 2200 802.11B/G WLAN experience troubles including:

    * Intermittent connectivity
    * Inability to switch between networks or regain a lost network connection without rebooting
    * Inability to configure wireless connection using Network Connection GUI 

Cause:
Ubuntu 5.04 Hoary Hedgehog ships with version 0.19 of the driver for this card. The current version is 1.0.3. The stable version is 1.0.0, and this is the version it is recommended to use with Ubuntu. Of course, you can try any version you like!

Solution:
Remove completely version 0.19 and upgrade to version 1.0.*


HOW TO:
[http://nickselby.com/articles/technology/index.htm?a=1807](http://nickselby.com/articles/technology/index.htm?a=1807)

---

