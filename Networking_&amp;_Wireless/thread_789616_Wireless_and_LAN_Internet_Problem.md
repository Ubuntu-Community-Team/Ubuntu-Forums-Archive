---
title: "Wireless and LAN Internet Problem"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by filam on 2008-05-10
I am not able to connect to internet using my laptop. I am currently using Ubuntu Gutsy Gibbon 7.10. I am having trouble connecting to my office wireless network and hard line. I can locate the office wireless signal, along with other signals. I could connect to a wired network about one day ago. Do you have any ideas what might be wrong?

When I plug in the hard line it searches for a few minutes (much longer than normal) and then connects, but I am unable to access any websites. It simply states server not found in my browser. While searching the gnome-panel applet states "searching for network key." It always appears to fail at this. Another point of concern is that it appears it is attempting to connect at 128 bit, but the router's frequency should be 54.

When I try and connect to the wireless network I type in the correct password. Then it searches for a few minutes and finally gives up.

I am using a Dell Inspiron 6000.

Any help would be greatly appreciated.

---

### Post by nixscripter on 2008-05-11
The office connection sounds like it might be a DHCP problem. If you connect to the office wired, to where it says you have a connection but can't find any server, what is the output of the command: ```
ifconfig -a
```

---

