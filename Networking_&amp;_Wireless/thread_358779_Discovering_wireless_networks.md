---
title: "Discovering wireless networks"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by tsmets on 2007-02-11
I every once in a while visit places where I dunno the wireless config ...
What I usually need to do, is to start XP see the open network configurations and then reboot in Ubuntu to adapt the configuration... 

Is there a tool that ollows me to discover the available *wireless* networks & their protections ... (WEP/WPA/open) ?

\T,

---

### Post by corax on 2007-02-11
Hi 

Maybe you can try iwlist :
```
iwlist eth1 scan
```

(where eth1 is the network interface is you have other for example wlan0 or ath0 ... replace it with the correct one.)

This program lists the wireless lan access points around you (essid, mac address, encryption type (if any)...)

i think all the information you need (except the WEP/WPA key of course :) ) is listed there ...

if you have problems please read the iwlist manual

```
man iwlist
```

if you have more problems post it here :)

good luck

---

### Post by tsmets on 2007-02-11
As far as I can see, it is not yet available as a package ... ?
Synaptic did not return anything relevant :(
Apparently :
[http://forums.debian.net/viewtopic.php?t=4021](http://forums.debian.net/viewtopic.php?t=4021)
it expects a manual install ... ?

\T,

---

### Post by corax on 2007-02-13
Hi

That is true it is not a package but it is a command in a package ... so google is you friend :) and let me introduce a friend of mine :)

The debian package search ! :)

[http://www.debian.org/distrib/packages#search_packages](http://www.debian.org/distrib/packages#search_packages)

To the lower search field enter :"iwlist"

Then under the textbox choose : "packages that contain files or directories whose names contain the keyword "

Hit ENTER and wait for the response ... :P

By the way it should be on your machine since the package that contains it is installed by default ...

good luck :)

---

