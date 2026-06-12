---
title: "Strange Wireless Connection Problem on Thinkpad X201i"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by Andavane on 2011-08-16
Scenario:

This machine is Thinkpad X201i, dual-booted with
Windows 7 Professional and
Ubuntu 11.04.

Recently I've had wireless connection problems with the net.
Just now I had no net connection to server (although router is showing fine in Ubuntu). Connecting ethernet cable, it all works fine.

If I restart into Windows, net connection is fine without the cable. 

So I want to find out how to investigate the problem, which has only started recently.

PS: I enquire initially with my mate in same house. If his isn't working, we know the net is down for good.

---

### Post by lmarmisa on 2011-08-16
These commands could help you:

```

nm-tool
iwconfig
ifconfig
ping -c4 router_private_ip_address
ping -c4 server_ip_address

```

---

### Post by Andavane on 2011-08-16
Update:
The Net is now working with Ubuntu! #-o

In the interim, I restarted into Windows and went on there for a bit.
After a while, a message flashed on the bottom of the screen "The Latest Episode of Torchwood has finished downloading", and then on booting back into Ubuntu, everything ran normally.

So I can deduce that as I shut the OS down while my program was downloading, it had tied up the wireless card in some way.

Any comments welcome.

---

### Post by Andavane on 2011-08-16
> **lmarmisa said:**
> These commands could help you:

```

nm-tool
iwconfig
ifconfig
ping -c4 router_private_ip_address
ping -c4 server_ip_address

```

Thank you, amigo. We both replied at the same time :)
These are the results from those commands (with wireless net working).
Will try again if problem recurs.

> andavane@andavane-think:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:43:DF:F6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto wlan-ap] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        18:3D:A2:22:89:1C

  Capabilities:
    Speed:           162 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKY52126:        Infra, 00:1E:74:4E:CB:9F, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA
    EdgeWireless:    Infra, 22:CB:4E:30:6B:6E, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA
    ThomsonD90FFA:   Infra, 00:1F:9F:87:01:35, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    *wlan-ap:        Infra, 00:04:ED:D4:30:F4, Freq 2412 MHz, Rate 54 Mb/s, Strength 68
    BTFON:           Infra, 12:FE:F4:0E:8A:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    BTOpenzone:      Infra, 02:FE:F4:0E:8A:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 41
    IMTL:            Infra, 00:22:3F:4C:3F:42, Freq 2417 MHz, Rate 54 Mb/s, Strength 37 WEP
    BTHub3-9FTP:     Infra, 00:FE:F4:0E:8A:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


andavane@andavane-think:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"wlan-ap"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:D4:30:F4   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11273  Invalid misc:919   Missed beacon:0

andavane@andavane-think:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:43:df:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:396836 (396.8 KB)  TX bytes:396836 (396.8 KB)

wlan0     Link encap:Ethernet  HWaddr 18:3d:a2:22:89:1c  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1a3d:a2ff:fe22:891c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43546130 (43.5 MB)  TX bytes:8543307 (8.5 MB)

andavane@andavane-think:~$ ping -c4 router_private_ip_address
ping: unknown host router_private_ip_address
andavane@andavane-think:~$ ping -c4 server_ip_address
ping: unknown host server_ip_address


---

### Post by Andavane on 2011-08-17
110817-1432:
How very annoying!
I'd been working in Ubuntu for most of the morning, and now I've booted in again the net has 'gone' in Ubuntu. So I'm back in Windows.
I'll paste of of the commands into a txt file, into a card-slot on this PC, boot into Ubuntu again and read this thread again from there to see what can be done.
As ever, any help or suggestions much appreciated.
PC = Lenovo Thinkpad X201i.

---

