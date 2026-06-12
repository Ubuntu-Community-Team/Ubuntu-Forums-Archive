---
title: "Can't find cable modem"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by Pocketghost1 on 2008-07-31
My cable modem died and it was replaced with a Motorola surfboard cable modem. Now I can get on the internet with my XP computer but cannot with my Ubuntu 8.04 computer. Both computers were working fine before the modem was replaced. Also I have a Netgear RP614v2 router that I was using to share the internet connection. I am by-passing that now and going directly from the cable modem to the computer. Also when I installed 8.04 it found the router and old modem by itself.

I did ipconfig on the Windows platform:
Windows IP Configuration

        Host Name . . . . . . . . . . . . : scotts-computer
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : sd.cox.net
        Description . . . . . . . . . . . : Intel 21041-Based PCI Ethernet Adapter (Generic)
        Physical Address. . . . . . . . . : 00-E0-29-25-6A-2F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 72.199.10.90
        Subnet Mask . . . . . . . . . . . : 255.255.252.0
        Default Gateway . . . . . . . . . : 72.199.8.1
        DHCP Server . . . . . . . . . . . : 172.19.97.28
        DNS Servers . . . . . . . . . . . : 68.105.28.12
                                            68.105.29.12
                                            68.105.28.11
And for Ubuntu:
eth0:avahi
      inet: 169.254.5.85
      bcast: 169.254.255.255
       mask: 255.255.0.0
      upbroadcast running multicast mtu:1500 metric:1
      int:19 base address:0xe800
lo: inet:127.0.0.1
    mase:255.0.0.0
    inet6: ::1/128

I have gone to admin>network and the wired connection has roaming checked. The DNS server is 192.168.0.1

Can anyone help?

---

### Post by superprash2003 on 2008-08-01
what is the ip of the modem you have?? instead of setting it to roaming mode.. try static ip and set it to 192.168.0.2(if modem ip is 192.168.0.1) or 192.168.1.2(if modem ip is 192.168.1.1) .. set gateway as modem ip.. and in the terminal type ping 192.168.0.1 or ping 192.168.1.1 whichever is your modem ip.. and see if you are getting a reply.. then go to the terminal and type sudo pppoeconf to create a dialer

---

