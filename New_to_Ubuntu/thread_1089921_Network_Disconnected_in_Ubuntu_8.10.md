---
title: "Network Disconnected in Ubuntu 8.10"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by LiviooT on 2009-03-07
This is my second thread on this subject since the first one was unsuccessful.

I recently installed Intrepid Ibex on my desktop so I can fiddle with it. I dual booted with Windows 7 Beta. After the initial install, I had a few problems with my network: Ubuntu seemed to search in vain for network settings only to notify that "the network has been disconnected". After a few restarts, the Internet worked just fine :popcorn:.

Now the Internet stopped working again... Network manager tries to retrieve automatic settings but ends up telling me "Network has been disconnected" all over again :(. 

I tried entering the settings manually - no good. The network works just fine in Windows and keep in mind it worked just fine in Ibex as well... I even connected my old cellphone and it identified my Orange carrier network and gave me GPRS-powered Internet :confused: But wired broadband doesn't work?? WTF!

Here's what the terminal said after I ran *lshw -C network*:

```
*-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:f4:2a:6a:ce:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

So? what's the problem? Please give me a solution... I'm a fairly new user btw so keep it simple, please!

Thank you!

---

### Post by LiviooT on 2009-03-07
thank you... very helpful forum... I can see the ubuntu love... spreading :D

think I'm gonna put my 4 muscles to good use :)

---

### Post by Iowan on 2009-03-07
Sometimes it takes more than an hour to get a response - it may take more than 3 to get a "good" one, and more than 4 muscles to get more than 4 muscles back ;)
If you're running Gnome, Network Manager stores its files in a different place - check /etc/NetworkManager/nm-system-settings.conf.

---

