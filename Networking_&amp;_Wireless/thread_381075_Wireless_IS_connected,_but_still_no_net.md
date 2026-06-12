---
title: "Wireless IS connected, but still no net?"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by moongo0se on 2007-03-10
Heya all!

I`ve just installed ubuntu for the first time ever on my laptop, and everything went like a dream.
It even found my wireless card, which was no problem configuring either. It connects to my router, tells me signal strenth is between 90% and 100%, but I just can`t get contact with anything. Not even my router ;) (tried pinging it, and connect to it via http)
Running ifconfig shows me that eth1 (wireless card) for some reason has an IPv6 adress. Could that be the reason why it doesn`t work? and if, how do I fix it? ;)

---

### Post by spd106 on 2007-03-10
The IPv6 address is probably self-assigned and can be ignored, unless you have an IPv6 network.

I suggest that you run dhclient to check that you can get an IPv4 address. Perhaps try **sudo dhclient eth1**. If it times out then you are having connection problems. Does iwconfig show your routers mac address in the access point part?

---

### Post by moongo0se on 2007-03-11
Heya!

dhclient times out, and yes, iwconfig shows the mac adress of my router. 
Any other suggestions? Seems i cant get any ip adress from my router. Also tried to manually set a fixed ip adress, which didn`t work either. That is, i got the IP adress, but still no contact with the outside world ;)

---

### Post by moongo0se on 2007-03-11
Thanks for the help, but I actually figured it out, with the help of this thread: [http://ubuntuforums.org/showthread.php?t=381327](http://ubuntuforums.org/showthread.php?t=381327)

See ya!

---

