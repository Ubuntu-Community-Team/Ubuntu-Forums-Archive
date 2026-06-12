---
title: "Impossible to get ivp4 LAN connection"
date: 2017-11-24
forum: Networking &amp; Wireless
---

### Post by bricole666 on 2017-11-24
Hi everyone ! 

I have spent thousands hours in my life reading conversations in this forum and always found my answers but today no other way .....

I saw many people with the same probleme like me but all the solution they gave were non-suitable yet so let explain :

I have PC (no laptop) and connected to a router by a 40m ethernet wire.
When everything is reset (router + computer) the DHCP program can connect and obtain an ipv4 address and establish the LAN connection, and the connection is excelent.
However, after few restart or after one night usually, the Internet connection stop working. Ethernet DHCP return that the network is connected, but no internet.
Before i was able to have temporary fix by disconnect and reconnect the ethernet wire several times until it work, but it became with the time longer and longer to come.
I also tried to provide a static ipv4 address from the computer and also from the router, tried to remove ipv6 protocol use only ipv6 enable disable things reset many times, had this problem on windows and now have this also on ubuntu 16.04 exactely the same ....

After all of that i tried to look at the hardware, so i connected a laptop with my long wire and it works, moreover i now use a USB wifi connection to type this message, and it work ( never any ip problem) however i am far from the router so the connection is not as good as an ethernet one.

my thinking is now that my ethernet card doesn't work properly and need to be changed.

it's been one month i am looking for a solution i have big hope on linux users ;)

Any idea ?

---

### Post by The Cog on 2017-11-26
It is possible that the length of the cable is causing problems, although 40m is well within the maximum length for 100Meg (not gigabit) speeds. 
Cab you post the output of the command **ifconfig** so we can have a look for errors or other signs of problems?

---

