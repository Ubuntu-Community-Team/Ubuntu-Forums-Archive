---
title: "Wireless Help Requested"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by fireball47 on 2006-11-29
I've read through all of the guides and forums, and I am still having wireless troubles. I hope somebody can help me.

I have a Dell Inspiron 1501 laptop with an internal Broadcom DW1390 wireless minicard. I have an AMD-64 chip. I installed Edgy for AMD-64 very recently.

My access point is a Netgear router with open key 128-bit WEP encryption. I have been able to connect to the router wirelessly with the same laptop running Windows XP.

First off, I had to use ndiswrapper to get my wireless card to do anything, and now I actually get results when I do a scan. It finds my access point no problem:

eth1    Scan completed:
        Cell 01 - Address: 00:09:5B:3A:74:FC
            ESSID:"Taub"
            Protocol:IEEE 802.11b
            Mode:Managed
            Frequency:2.437 GHz (Channel 6)
            Quality: 100/100  Signal level:-21 dBm  Noise level:-96 dBm
            Encryption key:on
            Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
            Extra:bcn_int=100
            Extra:atim=0

I have configured eth1 to match up with the access point's SSID and WEP key using iwconfig, and my /etc/network/interfaces now contains the following entry:

auto eth1
iface eth1 inet dhcp
wireless-essid Taub
wireless-key 99999999999999999999999999

Running iwconfig eth1 gives me the following:

eth1   IEEE 802.11g  ESSID:off/any
       Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
       Bit Rate=54 Mb/s  Tx-Power:32 dBm
       RTS thr:off  Fragment thr:off
       Encryption key:9999-9999-9999-9999-9999-9999-99  Security mode:restricted
       Power Management:off
       Link Quality:0  Signal level:0  Noise level:0
       Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0  Missed beacon:0
       
Running dhclient eth1 gives me the following:

There is already a pid file /var/run/dhclient.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
...

Listening on LPF/eth1/00:16:cf:a5:fb:da
Sending on   LPF/eth1/00:16:cf:a5:fb:da
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have tried various restarts such as "/etc/init.d/networking restart" and ifdown/ifup to no avail.

It can see the access point, but it can't associate with it. Can anybody help me? Thank you so much in advance for your time.

---

### Post by fireball47 on 2006-11-29
By the way, I've also tried using the GUI tools to no avail. I have tried in the past to use the "System -> Admin -> Networking" program to configure the wireless connection, but I still had no connectivity.

I also tried installing and using the Network Manager, but it simply tells me "No network devices have been found"

---

### Post by trubblemaker on 2006-11-29
K.I.S.S. start with un-encrypted, once that's working without issues then move to wep.  You can see your network, so I think you got everything installed correctly just in need of some fine tuning.

---

### Post by fireball47 on 2006-11-30
I tried disabling the encryption at the AP and turning off the encryption of eth1 (both with "iwconfig eth1 key off" and by changing my /etc/network/interfaces file). It still can't connect, even with no security enabled (WEP or otherwise). Thanks, though, any other ideas?

---

### Post by rgutierrez on 2006-11-30
I have the same problem, and in my troubleshooting, I found that my wireless problem exhibits the exact same behavior as my LAN adapter when my LAN adapter cable is disconnected from my computer.

So, what's the wireless equivalent of disconnecting your LAN adapter cable? I wonder if answering this question will solve the problem.

---

### Post by trubblemaker on 2006-11-30
ok so do :
```
 iwconfig 
``` to make sure encryption is off.  if you altered the /etc/network/interfaces file then you can use
```

sudo ifdown eth1
sudo ifup eth1

```
see if it get an ip,

NO? ok try this
```

sudo iwlist scan
iwconfig
sudo iwconfig eth1 essid any
sudo iwconfig eth1 ap any
sudo dhclient wlan0

```

Did that work? NO?
look through dmesg for anything related to bcm43xx or network related.

---

### Post by fireball47 on 2006-11-30
First of all, thanks for trying to help me.

I will try your suggestions this evening on my home network (here at work we use WPA, which I hear is a whole different beast). But I feel like I have already tried those commands before...

Last time I looked at my dmesg logs, it was overrun with "unexpected IRQ trap at vector b0" statements due to the fact that I had to add "acpi=force irqpoll" to my boot options to get Edgy to recognize my SATA hard drive [http://ubuntuforums.org/showthread.php?p=1786658](http://ubuntuforums.org/showthread.php?p=1786658) -- I don't know if that would have anything to do with my wireless networking problems though.

Also, I read somewhere that ndiswrapper was only a viable solution for x86, but I am using AMD-64. Is it possible that my driver is still messed up, or does the fact that I can scan and see my network prove that my driver is working fine?

But I'll try your suggested commands again tonight and post my results. I really hope I don't have to buy a new MiniCard or go back to using Windows.

---

### Post by fireball47 on 2006-11-30
Success! I am up and running wirelessly! I am not sure of which these actions actually fixed the problem, but I did the following:

1. rebooted
2. sudo modprobe ndiswrapper
3. removed /var/run/dhclient.eth1.pid
4. ifdown and ifup

I think that step 3 might have been what I needed. When I tried to do certain commands (like ifdown/ifup), it always said something like "There is already a pid file..." at the top of the output, so I removed the file that it was complaining about.

Now, I will try getting WEP working, but for all intents and purposes, my problem is solved! Thanks to trubblemaker for help, and good luck everyone else.

---

