---
title: "random wifi lag"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by freonchill on 2008-11-26
i am trying to diagnose a wireless problem

the problem is that it will randomly lag. i am connected, 90% signal. i can ping the router, i can ping the dns servers (i use opendns) but when i try to surf to anything, it just sits there and does not do much for 1-2 minutes, then either starts to load SLOWLY (read 1min more to load) or does not load anything and stops attempting to load.

i have two laptops with broadcom 43xx cards
after 7.04, it would install through the restricted driver without having to do any "magic" to get the card working.

i have had it working 100% with WPA-TKIP since 7.04

in light of the recent pseudo-crack of wpa-tkip, i changed my router to wpa-aes

i started having problems the next day, but i dont know if its router's aes or ubuntu

router is linksys wrt54g OR buffalo whr-g54s (i have tried both)
with DD-WRT firmware.

i thought it was just b/c i changed to AES over TKIP, so i changed back, and apparently that wasnt the problem. so it makes me think that this has been a problem with ubuntu for a while, but it just happened to manifest during other variables which made me think that it was the other things. i dont have a log (or memory from before this bug showed up, but i have 10-20% packet loss on the wifi connection (this problem?)
 
what makes me think that its a problem with ubuntu is that i have a windows laptop with the same chip right next to it and it does not have the problem, the only difference with the machines is that the linux one is p-4 mobile and the windows is a centrino.

has anyone else had problems with mixed-mode (802.11b & 802.11g) networks using network manager for wpa-tkip or wpa-aes network?

i do not think that changing from network manager to wicd would fix this problem, but i am willing to try it.

thanks.

---

### Post by sonofusion82 on 2008-11-26
i had similar problem with one of my laptop. it is a problem with DNS name resolution.
if you can ping your dns server by IP address, can you ping some other server by their domain name like "ping www.google.com"

---

### Post by freonchill on 2008-11-26
i do not think that is the problem, i use opendns (208.67.222.222 & 208.67.220.220)

i do not see that being the source of the problem. as i have problems even loading the router webpage (local, accessed via IP address)

i just dont know enough about encryption and or latency / signal degradation due to 802.11b & 802.11g either working on the same network and or working in different vectors.

i am away for thanksgiving, but i will definitely try pinging IP vs hostname that when i get back to see if there is any delay that could be attributed to this problem.

---

