---
title: "WICD problems on Kubuntu Feisty."
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by keith11 on 2007-04-21
Before I begin typing about the problem I am facing let me mention that I have tried too much to make Knetworkmanager work but it just doesn't work after coming alive from suspend mode on my laptop. Other problem I face with Knetworkmanager is that after coming back from suspend mode, if I try to choose the "go offline" option of Knetwokrmanage by right clicking on the taskbar icon, it just doesn't allow me to make that change. As a mater of fact, it seems stuck because it doesn't allow me to make any changes. If I quit it, and then restart it, it will not detect my wireless card. I have been having similar problems with networkmanager in Ubuntu too and I have filed a bug report on launchpad which is yet to be taken care of.

In order to get rid og the problem I tried wicd on my Kubuntu Fesity installtion. I can connect fine through wicd at my work place where there is no encryption. At my home though, where I have awireless connection with 64-bit WEP encryption, wicd gets stuck at "Generating PSK..." message as soon as I click on "connect" after providing the encyption key for my wireless connection. Wicd remains stuck and never connects. I am using Intel Pro 2200 wireless card so I am assuming I have to use "ipw" in my preferences of wpa_supplicant driver, which is what I did. I have tried choosing another driver, the one which is selected by default and it work too when there is no encryption, but with encryption, it just doesn't connect. Has anyone used wicd on Kubuntu/Ubuntu Feisty and actually got it to work without problems? Could someone tell me why wicd gets stuck with that "Generating PSK..." message and never connects and what's the work around for that? Any help/comments will be greatly sought after and appreciated. Thanks.

Keith.

---

### Post by keith11 on 2007-04-22
Is anyone facing the "generating psk..." problem?

Keith.

---

### Post by whayong on 2007-04-23
I have the same thing.  Trying to connect to WEP at work.  I however am on Xubuntu 6.10 and have a RT61 card so I use the .dat file to connect to WPA network at home.

---

### Post by jtelling on 2007-04-24
> **whayong said:**
> I have the same thing.  Trying to connect to WEP at work.  I however am on Xubuntu 6.10 and have a RT61 card so I use the .dat file to connect to WPA network at home.

I looked at the code, and it seems that whomever made WICD has WEP and WPA going through the same path for encryption -- meaning -- it tries to use the WEP key to generate a PSK, and then fails.

I think WICD needs to TLC in the encryption department.

Honestly, in my very uneducated opinion, I don't think WICD will work with a WEP network until it's fixed.

---

### Post by whayong on 2007-04-25
> **jtelling said:**
> I looked at the code, and it seems that whomever made WICD has WEP and WPA going through the same path for encryption -- meaning -- it tries to use the WEP key to generate a PSK, and then fails.

I think WICD needs to TLC in the encryption department.

Honestly, in my very uneducated opinion, I don't think WICD will work with a WEP network until it's fixed.

Much appreciated info.  I just want to make sure I understand you here, in your opinion, WICD works better with WPA rather then WEP?

---

### Post by keith11 on 2007-04-25
> **jtelling said:**
> I looked at the code, and it seems that whomever made WICD has WEP and WPA going through the same path for encryption -- meaning -- it tries to use the WEP key to generate a PSK, and then fails.

I think WICD needs to TLC in the encryption department.

Honestly, in my very uneducated opinion, I don't think WICD will work with a WEP network until it's fixed.

That's really useful information. I don't know but if you can you may join the forum for wicd and offer your suggestions to Adam (the developer of wicd). 

Keith.

---

### Post by Ripfox on 2007-04-25
Uh, I use wicd on a wep encrypted network all day long everyday. Works fine here...
One thng I have noticed is that you might look in the "Preferences" and make sure you have the right wireless interface typed in. Mine is actually "eth1" for the wireless interface. I know it should  be wlan0 but if its not broke I don't fix t. :lolflag:

---

### Post by keith11 on 2007-04-25
Thanks for that suggestion. Unfortunately I know I can connect on a non-encrypted connection but it's just the WEP thing which I can't connect to. So I do know that I can connect.

---

### Post by Ripfox on 2007-04-26
This sounds like it may be a stupid suggestion....but did you double chek your WEP key? Also, do you have the latest wicd installed? [http://compwiz18.ig3.net/wicd/wb/](http://compwiz18.ig3.net/wicd/wb/)

Good luck

---

### Post by keith11 on 2007-04-26
No your suggestion was in no way stupid and thanks for that suggestion. Yes, I have double checked my key and I do have the latest version of wicd.

Keith.

---

### Post by Marsjannno on 2007-05-01
I have problem with "generating PSK" as well.

---

### Post by calgarystevens on 2007-06-06
Hey guys, instead of typing your wep key in like this - thisismywepkey, try adding quotes to it like this - "thisismywepkey". I don't know why it helps, but mine connects perfectly when it's added that way. Good luck.

:D

---

### Post by devnulljp on 2008-06-15
Can I just chime in with a "me too" -- have you figured this out yet? 
I have the same card and the same problem on Kubuntu Hardy with wicd 1.4.2
I have exactly the same problem -- it works fine on an unencrypted network, but I've tried it with both WEP and WPA and it won't connect..gets stuck at the same point. 
I've double (triple or more) checked the WEP key, I've tried it with and without the quotes, there are no characters that need escaping in the key, and still it won't connect. 
Any ideas?

EDIT: I just ran through it again and this time did tail -f /var/log/syslog

```
Jun 15 20:40:38 hostname avahi-daemon[5010]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun 15 20:40:38 hostname avahi-daemon[5010]: Withdrawing address record for fe80::20d:60ff:fec9:9060 on eth0.
Jun 15 20:40:38 hostname dhclient: receive_packet failed on eth0: Network is down
Jun 15 20:40:55 hostname kernel: [ 4286.906607] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 15 20:40:55 hostname kernel: [ 4286.910263] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 15 20:40:55 hostname dhclient: There is already a pid file /var/run/dhclient.pid with pid 3132
Jun 15 20:40:55 hostname dhclient: removed stale PID file
Jun 15 20:40:55 hostname dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jun 15 20:40:55 hostname dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jun 15 20:40:55 hostname dhclient: All rights reserved.
Jun 15 20:40:55 hostname dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun 15 20:40:55 hostname dhclient:
Jun 15 20:40:56 hostname dhclient: Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Jun 15 20:40:56 hostname dhclient: Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Jun 15 20:40:56 hostname dhclient: Sending on   Socket/fallback
Jun 15 20:40:57 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun 15 20:41:01 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun 15 20:41:09 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun 15 20:41:20 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun 15 20:41:27 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Jun 15 20:41:28 hostname dhclient: No DHCPOFFERS received.
Jun 15 20:41:28 hostname dhclient: No working leases in persistent database - sleeping.
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Successfully called chroot().
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Successfully dropped root privileges.
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: fopen() failed: Permission denied
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Starting with address 169.254.4.40
Jun 15 20:41:33 hostname avahi-autoipd(eth1)[7242]: Callout BIND, address 169.254.4.40 on interface eth1
Jun 15 20:41:33 hostname avahi-daemon[5010]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.40.
Jun 15 20:41:33 hostname avahi-daemon[5010]: New relevant interface eth1.IPv4 for mDNS.
Jun 15 20:41:33 hostname avahi-daemon[5010]: Registering new address record for 169.254.4.40 on eth1.IPv4.
Jun 15 20:41:37 hostname avahi-autoipd(eth1)[7242]: Successfully claimed IP address 169.254.4.40
Jun 15 20:41:37 hostname avahi-autoipd(eth1)[7242]: fopen() failed: Permission denied
```

That fopen() failed looks suspicious. It looks like it kinda works, but not quite. It's trying to get an IP address by dhcp, what is weird is that  it gets an IP address of 169.254.4.40, which is not on my network (which is a standard 192.168.1.0/255 private network).
I did a who is on that IP and it bears no resemblance to my ISP / country or anything else either.
Any ideas?

---

