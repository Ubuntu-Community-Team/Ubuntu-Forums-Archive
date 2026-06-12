---
title: "ethrnet modem not working"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by DiLu11o on 2008-05-26
I have a motorolla surfboard modem connected through the ethrnet cable. I ran the trial disk and the internt worked. After I installed Ubuntu the internet still worked, I then downloaded some updates and halfway through it came up with an error and now my intrnet won't work. What can I do?

---

### Post by superprash2003 on 2008-05-26
go to the terminal and type ifconfig and post output here

---

### Post by DiLu11o on 2008-05-27
tony@tony-desktop:$ifconfig
eth0   Link encap:Ethernet HWaddr 00:1e:8c:4e:26:5f
      inet6 addr: fe80::21e:8cff:fe4e:265f/64 Scope:Link
      Up BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:0 errors:0 dropped:4294967259 overruns:0 frame:0
      TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0B) Tx bytes:0 (0.0B)
      Interrupt:218 Base address:0x4000

eth0:avahi Link encap:Ethernet Hwaddr 00:1e:8c:4e:26:5f
      inet addr:169.254.4.148 Bcast:169.254.255 Mask:255.255.0.0
      Up BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      Interrupt:218 Base address:0x4000

lo    Link encap:Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:1590 errors:0 dropped:0 overruns:0 frame:0
      TX packets:1590 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      Rx bytes:79872 (78.0KB) TX bytes:79872 (78.0KB)


wlan0   Link encap:Ethernet HWaddr 00:16:44:82:ca:11
      Up BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0B) TX bytes:0 (0.0B)

wmaster0  Link encap:UNSPEC Hwaddr 00-16-44-82-CA-11-00-00-00-00-00-00-00-00-00-00
      Up BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0B) TX bytes:0 (0.0B)

tony@tony-desktop:$


Format might be off had to tybe it all
Thanks for the help

---

### Post by jrusso2 on 2008-05-27
You don't seem to have in IP address.  Are you using DHCP or are you running a static IP?

---

### Post by DiLu11o on 2008-05-27
under wired connection it just says free roaming

---

### Post by DiLu11o on 2008-05-27
i tried the Automatic DHCP it didnt work so i changed it back

---

### Post by DiLu11o on 2008-05-27
My internet provider said my modem couldnt grap an IP adress

---

### Post by superprash2003 on 2008-05-27
any idea what the ip address of your modem is?

---

### Post by DiLu11o on 2008-05-27
dont know

---

### Post by superprash2003 on 2008-05-27
My computer keeps pulling a 169.254.x.x IP address, the modem has been reset and power cycled and the computer is still getting the same IP address, how do I correct this?
Disconnect the Coax cable from the modem and restart it. Once the "Receive" light begins flashing reboot your computer. If the modem and the computer are communicating, the computer will get a 192.168.100.11 IP address (192.168.0.x with the SBG900) from the cable modem. Shut down your computer. Connect the Coax cable to the cable modem, restart it, and wait for the modem to sync up with the cable company. Once the modem is in sync (Power, Receive, Send, On-line are all illuminated) restart the computer. Once the computer has restarted check the IP address. The computer should have a valid IP address from the cable company. Computers attached to the SBG900 will always get a private (192.168.0.x) address regardless of whether or not the SBG900 is registered on the cable system.

from [http://broadband.motorola.com/consumers/support/faqs/surfboard_faq.asp#wrong_ip](http://broadband.motorola.com/consumers/support/faqs/surfboard_faq.asp#wrong_ip)

---

