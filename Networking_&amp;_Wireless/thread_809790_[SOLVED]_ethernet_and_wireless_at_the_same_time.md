---
title: "[SOLVED] ethernet and wireless at the same time"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by bash4fun on 2008-05-27
hello dear friends!

i've got the following problem:
i usually connect to the internet by using my wireless interface which connects to my ap and so on. but lately i had the idea of bridging my ethernet with my wlan connection by using nat and ip masquerading.

however, unfortunately i experience several problems with the network manager, because whenever i connect the LAN cable to my ethernet port on my laptop, network manager seems to cut off my wireless and is trying to receive an ip address from the ethernet LAN. so it is impossible to me to configure both interfaces at the same time because configuring them disables each other.

i wondered if it would be useful to uninstall network manager and only use iwconfig and ifconfig to get my configuration done?

---

### Post by jimv on 2008-05-27
That's odd.  You could try using WICD instead of Network Manager.
```

sudo apt-get install wicd
```

This will get rid of network manager and install WICD

Then to get a tray icon, press alt+f2 and type

```
/opt/wicd/tray.py
```

You can add that to you session so it starts up when you log in.

---

### Post by Iowan on 2008-05-28
Network Manager seems to want only one interface active at a time, but you can *probably* edit **/etc/network/interfaces** to include an "auto <interface>" for both.

---

### Post by bash4fun on 2008-05-29
allright thanks!

wicd works, altough i still have problems connecting to a wireless ad-hoc network. it even didn't work with network-manager. there must be still a problem with the iwlwifi module included in hardy.

---

### Post by bash4fun on 2008-05-29
so to complete this, i also solved the problem of the iwlwifi module by installing the windows xp driver using ndiswrapper.

now everything works fine and wicd is a really nice tool, espacially in handling your profiles for different wlans.

so thanks for your help :)

---

