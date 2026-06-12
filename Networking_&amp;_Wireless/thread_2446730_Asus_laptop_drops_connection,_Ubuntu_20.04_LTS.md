---
title: "Asus laptop drops connection, Ubuntu 20.04 LTS"
date: 2020-07-05
forum: Networking &amp; Wireless
---

### Post by wxarmstrong on 2020-07-05
I have an ASUS F510UA-AH51. It was originally installed with Windows 10 but I installed Ubuntu as a dual boot. Initially the only issue was that the times were out of sync which I fixed by setting Windows to UTC. After that both partitions worked fine and connected to my home network with no problem. Then I moved to a new house. My desktop & phone are connecting to the home computer fine but neither Windows or Ubuntu's internet is working properly when I connect. Specifically, what happens is that I have about a five second window where I can load sites before my browser gives a "No Internet' message. On Ubuntu sometimes I'm able to access some sites but not most sites (i.e. Google but not Twitter) which is apparently an IPv4 vs IPv6 thing. I can't remember how I did this exactly but messing around with configuration trying to find a solution I once got that to flip (i.e. was able to access Twitter but not Google).

Here is my data from running the offline wireless-info program:
[URL="https://pastebin.ubuntu.com/p/63tf4J2fSC/"]https://pastebin.ubuntu.com/p/63tf4J2fSC/

[/URL]Edit: I have solved the problem, it ended up being an issue with the router itself, after reconfiguring it everything is working perfectly.

---

### Post by gdesilva on 2020-07-06
I notice that you are connected to your MySpectrumWiFi2A-5G network. See whether it would make any difference if you disable this network, activate MySpectrumWiFi2A-2G network instead and reconnect.

---

### Post by wxarmstrong on 2020-07-06
I have the same problems with both networks.

---

### Post by gdesilva on 2020-07-07
I came across the following on Intel forum but it says the driver should work on Kernel 4.6 on wards -  which should not be applicable in your case anyway as you are running 5.4

[https://community.intel.com/t5/Wireless/intel-wireless-8265-8275-iwlwifi-not-working-in-linux/m-p/282892#M4073](https://community.intel.com/t5/Wireless/intel-wireless-8265-8275-iwlwifi-not-working-in-linux/m-p/282892#M4073)

Since you have issues with both Windows and Ubuntu, it may be worthwhile checking the router settings - as you had both working at your previous premises. Perhaps, running Wireshark on the wlp2s0 may give you some clues as to why the connection is dropping out?

Another option may be to install the firmware provided by Intel here [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)

---

