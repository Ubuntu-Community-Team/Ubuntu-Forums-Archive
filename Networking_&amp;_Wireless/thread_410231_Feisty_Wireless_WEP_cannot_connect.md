---
title: "Feisty: Wireless WEP cannot connect"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by crackerdog2 on 2007-04-15
I have an HP Pavilion Laptop dv8000 running Kubuntu.

I have finally got my wireless card enabled but cannot seem to get it to connect to the network with WEP. I have not tried turning wep off since it is being used by others.

When running ifconfig I get the following information:

[INDENT]eth1      Link encap:Ethernet  HWaddr 00:14:A5:74:62:F6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:21231 (20.7 KiB)
          Interrupt:10 Base address:0xc000

eth1:avah Link encap:Ethernet  HWaddr 00:14:A5:74:62:F6
          inet addr:169.254.9.17  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xc000[/INDENT]

I have tried setting it by running the following:
[INDENT]iwconfig eth1 key <key> open
iwconfig eth1 essid <ssid>
dhclient eth1[/INDENT]

That didnt work either the last command came back with:
[INDENT]Listening on LPF/eth1/00:14:a5:74:62:f6
Sending on   LPF/eth1/00:14:a5:74:62:f6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/INDENT]

My wireless card is a Broadcom BCM4318 (Airforce One 54G). Which is currently enabled.

Thanks,
David

---

### Post by thriff on 2007-04-16
I have the exact same problem on my HP Pavilion ze2000 series laptop with the same Broadcom card.
What's with this extra interface name ( eth1:avah ) ? Didn't have it in Edgy where the card worked fine.

---

### Post by crackerdog2 on 2007-04-16
> **thriff said:**
> I have the exact same problem on my HP Pavilion ze2000 series laptop with the same Broadcom card.
What's with this extra interface name ( eth1:avah ) ? Didn't have it in Edgy where the card worked fine.

I actually ended up getting it to work. After banging my head many times. The problem ended up being with my interface file. It had the ASCII value that I had used to set up my linksys router. After looking at another web page that had an interface file listed, I compared it to mine and found the value. Took out that value and replaced it with the hexadecimal value and it worked :D 

As far as the eth1:avah, I have no clue what that is about. I am still relatively new to linux and ubuntu/kubuntu. Although I am not a newby to UNIX. So, just trying to figure things out.

---

### Post by thriff on 2007-04-17
yeah I've got it working too now, following this guide: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")
Though i can't seem to get wifi-radar to work anymore, i can connect with iwconf.

---

