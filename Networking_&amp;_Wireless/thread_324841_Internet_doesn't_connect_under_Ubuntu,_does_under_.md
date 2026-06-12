---
title: "Internet doesn't connect under Ubuntu, does under Windows..."
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by shubox357 on 2006-12-24
Using 6.06 i cannot connect to the internet via ethernet. i have the ethernet on my computer plugged into my router {which is plugged into the modem[cable(internet) modem]} and configured it. i enabled the connection and selected DHCP as teh address or whatever. (just as i have done on my 6.06 iMac, which works). Anyone know what i can do to get online? thanks!

---

### Post by disabled_20220313 on 2006-12-24
Have you tried using the command line?

You may have more success using ```
ifconfig
``` and see if they ethernet device is actually "up"

If you get an output that loots like "eth1" then a box of information, then your hardware is up and running. If not try the command ```
ifconfig eth1 up
``` or maybe ```
ifconfig eth0 up
```

The previous commands will activate the networking hardware, up. If you ever wish to turn them off you use ```
ifconfig eth1 down
```

Hope this helps.

---

### Post by TMMM on 2006-12-24
If you are using a dual boot system, I ran into a similare problem which turned out to be the fact that I had ocnfigured my adapter in windows to be a static ip and then in ubuntu it was dhcp and wouldnt pull.

I had to then configure ubuntu adapter to be the same static ip as the windows to make it work. Kinda odd if you ask me.

If you had them configured both for dhcp I would imagine that owuld work aswell.

Hope it helps.

---

### Post by shubox357 on 2006-12-28
i typed in ifconfig and its working, and connected. i am not sure if the internet is configured as  DHCP on windows, it runs through a router though.

I was checking around in "Network Devices" and discovered that the ethernet is configured as loopback. each time i tried to change it to eth0 it wuold not stay that way once i closed out, and the itnernet doesnt work when the device is changed and the devices box is open. how can i get rid of "lo"? thanks!

---

### Post by dannyboy79 on 2006-12-28
you don't want to ever get rid of lo, that's your loopback interface. you just need to make sure your /etc/network/interfaces file is correct as well as your /etc/resolv.conf which is your dns settings. these are the 2 most common issues with people not being able to connect to the internet. if you don't know if windows is static or dhcp than it is dhcp cause you'd remember setting it to static. so just make sure that your ubuntu box is dhcp as well and that you put your routers ip address within the dns servers box within the networking gui under system, admin, networking. make sure your interfaces file only has the interface your using to connect, normally eth0 or eth1 as well as lo, lo should be first. good luck

---

