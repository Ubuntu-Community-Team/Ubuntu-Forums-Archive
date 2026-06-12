---
title: "I deleted my network manager, now can't reconnect to internet to redownload it"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by dpashkin on 2007-05-30
so i deleted network manager, because i'm dumb. Now I can't reconnect to the internet, tried using system=>administration=>Network, but my home is wpa and that option isn't there and my wired connection isn't there to connect. will try to disable security on my home network and redownload, meanwhile i'd really appreciate any help...


BTW Linux rocks!!!!

---

### Post by obrient on 2007-05-30
Do you still have a network cable? Hook it up and see if it sees it. If it doesn't reboot. If that fails then you should check out the ```
/etc/networks/interfaces
``` file and see if there is an entry like 

```
auto eth0
iface eth0 inet dhcp
```

If not then add it using your preferred text editor and the sudo command. Then do an ```
sudo ifup -a
```. This should bring up the network interface and then download Network Manager.

Hope it helps!

---

### Post by dpashkin on 2007-05-30
got it, thanks!!!

Once again, i love ubuntu, even though it's a bit hard at times transitioning from windows, but the ease of fixing own screw ups is through the roof!!!!

---

### Post by ryanVickers on 2007-05-30
Interesting, I deleted it on purpose because I thought the few pixels of wasted space it made in the notification area were driving me insane :p

And my network still works fine!

---

### Post by obrient on 2007-05-30
That doesn't delete Network Manager it just takes away the notification. It would still be in Synaptic. If you uninstall it then your network might not work. I know if I don't have network manager my wireless doesn't work.

---

### Post by ryanVickers on 2007-05-30
Are you sure, it's totally unchecked in the package manager!  And in previous versions of ubuntu, I don't believe it's been installed by default and things went ok...

---

### Post by obrient on 2007-05-30
I am pretty sure. If your driver is supported in linux you would see something like this I think in the /etc/network/interfaces file you would see 

auto wlan0
iface wlan0 inet dhcp

But I have been wrong before :)

---

### Post by ryanVickers on 2007-05-30
Hmm, ok, anyways, I just didn't like the trey icon - never did. :)

---

