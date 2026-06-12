---
title: "Unable to connect to wireless network"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by walshie616 on 2007-07-14
Hello,

I have manged to get my wireless card working on ubuntu :) However although i can see my wireless netowork and the strenght of it I am unable to connect to it :confused: I have no idea what the problem could be, please help!

Thanks :KS

---

### Post by apoth on 2007-07-14
What's the IP address of your Ubuntu machine?
What's the IP address of another machine on the network?
What's the output of running 'ping othermachineip'?

If you don't know how to do any of these, just ask.

---

### Post by walshie616 on 2007-07-14
No idea how to do those sorry :(

---

### Post by 5-HT on 2007-07-14
In addition fo apoth's questions, are you trying to connect to a secured (WPA/WEP) connection using NetworkManager? As long as your wireless driver is setup correctly, and all the settings for NetworkManager are correct for the network (dhcp/static IP, psk if applicable, etc...) but you still can't connect, I'd give wifi-radar a try. It's a GUI app that lets you connect to open/restricted wireless networks. 

NetworkManager can be really hit and miss depending on the drivers used and types of networks one's connecting to.

---

### Post by 5-HT on 2007-07-14
> **walshie616 said:**
> No idea how to do those sorry :(
To get some of the info apoth was looking for, enter the following in a terminal and paste the output:

```
iwconfig
ifconfig -a
```

Are you using NetworkManager to connect? If so, you'll be needing to use dhcp so as long as the router is configured for dhcp there wont be any worries there.

---

