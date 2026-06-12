---
title: "RALink RT61 Monitor mode problem"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by kungphukenobi on 2007-05-07
Hey all, i am running feisty and am experimenting with packet sniffing etc to make my home network more secure.
Things are running great I can do monitoring and packet injection......but only for a little while..

for some reason my rt61 chipset card wont stay in monitor mode and wont stay down.

I type....

```
sudo iwconfig ra1 mode Monitor
```

and it goes into monitor mode and works fine for about 30 seconds (collecting packets etc) before it just goes back to managed mode
I have even..

```
sudo ifconfig ra1 down
```

to take the card completely down, but once again, 30 seconds later it is back up again.  
I am sure there is something really easy that i am missing to stop the card coming active all the time, but i just cant figure it out.  

Any help would be great

---

