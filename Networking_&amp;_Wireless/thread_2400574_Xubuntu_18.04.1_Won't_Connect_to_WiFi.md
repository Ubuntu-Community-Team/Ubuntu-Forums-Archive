---
title: "Xubuntu 18.04.1 Won't Connect to WiFi"
date: 2018-09-07
forum: Networking &amp; Wireless
---

### Post by klaipedaville on 2018-09-07
Hi everyone,

I have just installed Xubuntu 18.04. I have no problems connecting  to the internet via cable / plugged in / wired but it won't connect to wifi. When I check my available networks,  the available wifi networks are showing but when I try to connect  it seems to hang for about 30 seconds before I get the message;  "Disconnected - you are now offline".

Can anyone walk me through / advise how do I get my wifi working?

Many thanks in advance!


Here is the "sudo lshw -C network":

*-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 02
       serial: 00:1a:73:b9:b8:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f6000000-f6003fff

and "iwconfig" looks like this:

enp0s10   no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

