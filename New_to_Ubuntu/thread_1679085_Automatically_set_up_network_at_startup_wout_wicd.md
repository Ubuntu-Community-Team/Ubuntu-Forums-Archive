---
title: "Automatically set up network at startup w/out wicd"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Deadboy420 on 2011-01-31
I basically need to set up my network via the command line with the following commands:
```
sudo ifconfig <interface> down sudo dhclient -r <interface>
 sudo ifconfig <interface> up
 sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
 sudo iwconfig <interface> key HEX_KEY 
sudo iwconfig <interface> mode Managed
 sudo dhclient <interface>

```every time kubuntu starts up. The main reason I have to do this is because even with wicd configured to connect to my wifi automatically, I still have to manually enter "iwconfig wlan0 key #########" or it won't connect sucessfully. So, all I need is a way to execute the above commands when KDE loads automatically. Shouldn't be difficult but I'm a noob at this. Thanks ;)

---

