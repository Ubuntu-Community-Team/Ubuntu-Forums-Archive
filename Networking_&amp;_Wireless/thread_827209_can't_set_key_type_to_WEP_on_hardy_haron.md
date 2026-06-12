---
title: "can't set key type to WEP on hardy haron"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by mirna on 2008-06-12
Hi,

I have a problem establishing wireless internet connection on my ubuntu 8.04 hardy haron. I have an IBM T30 Thinkpad, and the wireless connection service provider requires the  WEP password type. The network manager sets the password type to WPA Personal and does not allow me to change the network settings. More precisely, when I try changing the password type to WEP key (hexadecimal) and click OK, and immediately afterwards look at the properties on my wlan0, the network manager shows that the connection is WPA Personal. No matter how many times I tried changing the password type, the network manager always resets it to WPA personal.
With this setting my connection to internet stalls, I cannot get to the internet providers login website, even though it looks like firefox is trying to connect there, it reports loading the page in the left bottom corner of the browser. I would be very grateful for any help in fixing this problem so that I can set the key type to WEP and connect to internet. I am using Netgear wg111.v3 USB card as wireless card, and the internet service  does not require any key.
(My configuration is the standard one that came from the alternate CD, the computer has not been connected to the internet yet, except that I had an apperently standard issue to resolve concerning T30, boot stall, and defect network settings that initially offered no wireless even as a possibility. I followed the solution offered by Fred L at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398)
and afterwards I installed the wg111.v3 using ndiswrapper)

Please help!
mirna

---

### Post by dmedell on 2008-06-24
You seem to have the exact opposite problem of other t30 users.

please refer to :
[http://ubuntuforums.org/showthread.php?t=822098&highlight=thinkpad+t30]("http://ubuntuforums.org/showthread.php?t=822098&highlight=thinkpad+t30")

I found that using a WEP 64/128 hex key that I made up, made all the difference for me. Please see the 2 posts that I put at the end of that thread.:)

---

