---
title: "sharing internet"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by linux noooob on 2008-04-07
can i have an internet connection through wireless on my ubuntu laptop and have it share through the eithernet to my router wan?

---

### Post by kevdog on 2008-04-07
Yes it depends how you want to do it?

Here are two links to two different methods:
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=733868](http://ubuntuforums.org/showthread.php?t=733868)

---

### Post by MrFSL on 2008-04-07
Install firestarter. It is a frontend to your firewall and supports "ICS" (Internet Connection Sharing) just by checking a box.

```
sudo apt-get install firestarter
```

---

### Post by SpenceMakesSense on 2008-04-07
I have to admit, me and my linux nerd friend went at this topic for hours and got nowhere. I tried firestarter and didnt particularly get anywhere. But I am trying to connect it to my xbox which probably doesn't help.

---

### Post by superprash2003 on 2008-04-08
this is another ICS guide [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by linux noooob on 2008-04-08
Btw i thought you all might want to know why i ant this wll it is becaue 1 i want my server to b first so i on't have to do any annoying port forwarding, 2 because i want the extra firewall and stuff, 3 because my new vista laptop has so many problems i can't even use the wireless it connects then disconnects so ya vista sucks but ya i wanted to have a more mobile way of internet then just wireless (even though i have to move 2 computers so it isn't as mobile)

---

### Post by MrFSL on 2008-04-09
> Can an Ubuntu laptop with eth0(LAN ethernet) and eth1(WiFi ethernet) be configured as an Ad-Hoc access point, gateway, and/or router.
I do it all the time.

I suggest using WICD: [http://wicd.sourceforge.net](http://wicd.sourceforge.net) to setup the ad-hoc connection

And using firestarter:```
sudo apt-get install firestarter
``` to setup internet connection sharing

---

### Post by SyberKowboy on 2008-04-10
How do you bridge the two nework adapters? Is it as easy as setting up the Ad-Hoc and setting up connection sharing through Firestarter?

Thanks

---

### Post by MrFSL on 2008-04-10
As long as you use static IPs thats it!

---

