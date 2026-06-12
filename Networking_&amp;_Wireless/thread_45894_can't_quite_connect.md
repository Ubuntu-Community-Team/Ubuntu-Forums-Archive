---
title: "can't quite connect"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by westoncb on 2005-07-02
After much, much trouble (netgear drivers didn't work with 64-bit ubuntu), I finally got my netgear ma101 device setup, and recognized by network-admin. From network-admin I can now configure the properties for my wireless device (wlan0). I tried a few different configurations using the static ip address option as well as DHCP, with all of these configurations firefox would give me an error message when trying to connect to google, showing that it was not connected. I eventually found a configuration (using static ip) that causes slightly different (improved I believe) behavior. Now Firefox just hangs there saying Searching for [www.google.com](www.google.com)... in the status bar. I tried a few other programs and they all get stuck trying to connect to whatever it is they are connecting to (xchat irc for example). So I think I'm connected to my home network now, but I have no idea what to do next... any suggestions?

---

### Post by skipper on 2005-07-02
Sounds like you might have an IP connection, but you may not be pointing at a name server.

What does iwconfig tell you (or ifconfig for that matter)?
Do you know any of the addresses in your local network? Can you ping them?

Take it step at a time (the steps below assume that you are using the command line and either have sudo privs or are logged in as root):

1) verify your local interface is set up (using iwconfig or ifconfig)
2) verify that you can ping an address inside your network (using ping)
3) try to ping an address outside of your network using an ip address rather than a name (e.g. ping 66.102.7.99 - this is one of the google addresses)
4) if this works, check your /etc/resolv.conf for a valid nameserver address.

Good luck!

---

