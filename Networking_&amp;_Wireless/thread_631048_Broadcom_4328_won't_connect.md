---
title: "Broadcom 4328 won't connect"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by sanketmedhi on 2007-12-04
Hi,

I am using Ubuntu Gutsy Gibbon 7.10 x86_64 on my HP Pavillion dv9000 entertainment laptop. It has a Broadcom 4328 wireless adapter.

$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I have successfully installed drivers for the card, the wireless indicator on my laptop glows. I see wireless connections available around me including my home connection, 2WIRE388. I tried selecting my connection using the Network Administrator, then entering my key, and Configuration to DHCP. See image:
[[IMG]http://img214.imageshack.us/img214/6716/screenshotwlan0propertijd5.th.png[/IMG]](http://img214.imageshack.us/my.php?image=screenshotwlan0propertijd5.png)

After all this, I am still not able to connect to the Internet. 

iwconfig shows:

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"2WIRE388"
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Someone please help me with this problem. Thanks in advance.

---

### Post by kevdog on 2007-12-04
can you post lshw -C network?

---

### Post by sanketmedhi on 2007-12-04
> **kevdog said:**
> can you post lshw -C network?

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:1a:73:5c:d3:68
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.49+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by sanketmedhi on 2007-12-04
Also, when I restart networking, it looks like I am not assigned an IP, check this...

[http://pastebin.com/m28c458af](http://pastebin.com/m28c458af)

---

### Post by kevdog on 2007-12-04
Im not sure what this part means:

#
send_packet: Network is unreachable
#
send_packet: please consult README file regarding broadcast address.
#
Error for wireless request "Set Encode" (8B2A) :
#
    SET failed on device wlan0 ; Invalid argument.

Can you connect without any type of encryption to verify a working connection?

---

### Post by sanketmedhi on 2007-12-04
No, I cannot connect without my WEP encryption key. I am guessing that the problem is with authentication itself, but I am not able to resolve it.

---

