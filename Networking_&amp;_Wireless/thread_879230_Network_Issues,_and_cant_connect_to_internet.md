---
title: "Network Issues, and cant connect to internet"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by AlexisMclovin on 2008-08-03
I am running Ubuntu Hardy and i cant connect to the internet. When i first installed Ubuntu my network settings were completely default and they worked fine, but then i left with my computer to North Carolina for the summer. I had my computer connect to the internet up there just fine. I have just gotten back and i cant connect to the internet back at my house. I have my network setting on roam and it shows that a wire is connected but i cant get on the internet. I tried to do everything visually in the network settings app and i havent tried to use Terminal. Any solution would be greatly appreciated.

---

### Post by superprash2003 on 2008-08-04
presuming its a wired connection.. please post output of ifconfig.. are you able to ping your router?

---

### Post by AlexisMclovin on 2008-08-04
ifconfig? how do i access that? I tried to ping the router it sent the packages but i recieved none. So none are successful.
Dont know if ifconfig was supposed to fix my problem , but it did so thanks.

---

### Post by AlexisMclovin on 2008-08-14
Havent had this problem in a while, but its back again and i cant fix it

---

### Post by Iowan on 2008-08-14
> **AlexisMclovin said:**
> I tried to do everything visually in the network settings app and i havent tried to use Terminal. **ifconfig** will require the terminal...
**ifconfig** wasn't supposed to fix the problem, just provide information about it. (glad it worked once, though). **ifconfig** will show which interfaces have addresses, whether they're static or DHCP, and (this one's important) which ones are set to initiate automatically on startup. I haven't used "roaming", my machines are all pretty much stationary.

---

### Post by AlexisMclovin on 2008-08-14
> **Iowan said:**
> **ifconfig** wasn't supposed to fix the problem, just provide information about it. (glad it worked once, though). **ifconfig** will show which interfaces have addresses, whether they're static or DHCP, and (this one's important) which ones are set to initiate automatically on startup.

Well if they were wrong how would i go about changing the network settings. ( sorry if i made you roam >.>)

---

### Post by AlexisMclovin on 2008-08-14
i thought roaming mode automatically set up your internet and stuff, so i just left it on there.

---

### Post by Iowan on 2008-08-14
> **AlexisMclovin said:**
> Well if they were wrong how would i go about changing the network settings. I'm kinda old school... I prefer to edit **/etc/network/interfaces** directly (although I DO use **nano**).
Roaming?  Dunno, don't use it - although my understanding (such as it is) suggests it is intended for you mobile-types.  I don't know how it decides which settings to use - guess I need to find a good "How-To Roam".

---

