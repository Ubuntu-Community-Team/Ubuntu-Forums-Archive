---
title: "another wireless not working plz help!"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by cubanhotman on 2007-10-06
ok here is the deal i can see the driver i can click properties and i can put the name of my network but i does not connect i dont know what is wrong i dont have a network key or anything alse

i run 7.04 and my card is a 802.1 from hp are my doing something wrong?

---

### Post by Lambert on 2007-10-07
Network manager (the default wireless application with ubuntu) is still a little buggy and doesn't work with all drivers.

Open up a terminal and try to connect via command line.

```

sudo iwconfig wlan0 essid _____
sudo dhclient wlan0

```

replace wlan0 with what ever your interface is named. If you don't know just run iwconfig by it self and look at the output.

What chipset and driver are you using anyway?

---

