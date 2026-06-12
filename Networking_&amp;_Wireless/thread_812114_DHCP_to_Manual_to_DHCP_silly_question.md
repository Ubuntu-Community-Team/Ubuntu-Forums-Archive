---
title: "DHCP to Manual to DHCP silly question"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by dwanders on 2008-05-29
I am sure that this is a silly question but I'll be buggered if I can figure out why this is happening. Here at my work, we have multiple ways to get to the Internet:

1) is our standard way - all set up with DHCP 
2) is a fail-safe way (in case the first fails) we can re-route throught the private network and piggy back on one of our sister companies
3) is a second fail-safe through a second ISP (much smaller and normally only used in extream cases)

Any way - in the past, if my main (DHCP setup connection) breaks for what ever reason [typically a fiber cut], I use to just manualy configure things to point to the correct gateway & DNS settings of one of the alternates and had smooth sailing. Ever since the IP6 and the Roaming Mode stuff that has been added to the GUI - my ship has been experiencing troubled waters to say the least. When I turn off roaming and try to set a Static IP address, the network just breaks and I cannot ping anything on my subnet. 

I have noticed that when I ifconfig things after I manually make the change, there is an inet6 addr: field, but no inet addr: as is normally present while I am in roaming mode via DHCP. 

If anyone can let me know why this is breaking, or better a way for me to be able to manually switch through these connections I would be forever in your debt.

---

### Post by superprash2003 on 2008-05-29
could you post your ifconfig output.. to setup DNS permanently read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

