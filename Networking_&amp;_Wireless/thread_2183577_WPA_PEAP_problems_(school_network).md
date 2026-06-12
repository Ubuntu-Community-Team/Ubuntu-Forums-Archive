---
title: "WPA PEAP problems (school network)"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by chirpis7 on 2013-10-25
Hi everyone,

My school has 2 wireless networks. One is an open network that uses a web-based login, and the other is a WPA-PEAP network. I can connect to the WPA-PEAP network and load a few pages, but I get kicked off within a couple of minutes. I've searched in /var/log/ for wpa-supplicant, but I'm not getting anything I can understand. I really need your help because the IT department at my school refuses to even consider Linux issues (yeah...).

Here's some info you might need:

Ubuntu 13.04
3.8.0-32-generic x86_64


relevant lspci output:
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)


possibly relevant lsmod output:
iwldvm                241872  0
rfcomm                 42641  14 
iwlwifi               173516  1 iwldvm


lshw output:
*-network
       description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 24
       serial: b4:b6:76:a0:4b:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-32-generic firmware=18.168.6.1 ip=10.250.168.183 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f7c00000-f7c01fff

---

### Post by grahammechanical on 2013-10-25
If you have Network Manager, which you do have as you are running Ubuntu 13.04, then you have WPA-supplicant. Network Manager is designed to do it all for you. Do you have the correct pass phrase to authenticate a connection to that wireless access point? And what do you mean that you "are kicked off within a few minutes?" How? does the connection drop? Or is this done by the wireless access point itself due to some restriction by the school administration. This might help you

[http://askubuntu.com/questions/285234/cannot-connect-to-wpa2-wpa-enterprise-peap-and-mschap](http://askubuntu.com/questions/285234/cannot-connect-to-wpa2-wpa-enterprise-peap-and-mschap)

[http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap](http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap)

Regards.

---

### Post by chirpis7 on 2013-10-25
I'm quite sure that I have the correct username and passphrase. As I stated, I am able to connect to the network. By "kicked off", I mean that I am disconnected from the network after a couple of minutes. As I stated earlier, I have internet access through the network during this couple of minutes. If you have any specific advice based on the actual information I've given, feel free to let me know.
"Regards"
> **grahammechanical said:**
> If you have Network Manager, which you do have as you are running Ubuntu 13.04, then you have WPA-supplicant. Network Manager is designed to do it all for you. Do you have the correct pass phrase to authenticate a connection to that wireless access point? And what do you mean that you "are kicked off within a few minutes?" How? does the connection drop? Or is this done by the wireless access point itself due to some restriction by the school administration. This might help you

[http://askubuntu.com/questions/285234/cannot-connect-to-wpa2-wpa-enterprise-peap-and-mschap](http://askubuntu.com/questions/285234/cannot-connect-to-wpa2-wpa-enterprise-peap-and-mschap)

[http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap](http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap)

Regards.

---

