---
title: "eth0: no link during initialization"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by compu73rg33k on 2008-09-04
I just moved into a dorm at college. I initially plugged my laptop into the network and it got an IP address fine and everything worked. Then I plugged my desktop in. The next time I booted up my laptop, it refused to get an IP address. I ran dmesg | tail and got the following:
```
eth0: no link during initialization
ADDRCONF(NETDEV_UP): eth0: link is not ready
```

if I run ifup eth0 it outputs:```
Ignoring unknown interface eth0=eth0
```

I saw somewhere that restarting the forcedeth module could help. It did in the beginning (two times) but since then I've re-installed Ubuntu 8.04 and it makes no difference now.

Even weirder, for a while, if I would unplug my desktop computer's ethernet cable and then plug in my laptop, the laptop would instantly get an address. Then I could plug back in my desktop and all would be well until I restarted the laptop and I would have to repeat the process. Now, not even that works!

Then I was going to make sure it just wasn't my room that was causing the problem so I went next door. I plugged in my laptop and the network worked instantly. I went to the library and the wireless works as well (just for reference, I know this probably makes no difference). So essentially the problem only happens in my room on wired networking - unfortunately this is 99% of my usage.

What is going on?! I suspect ADDR_CONF could mean address conflict, but at one point, I set eth0 as a static address in my /etc/interfaces, the same IP address as my desktop, and when the desktop was unplugged, the network worked (as I stated before) and then I could plug in the desktop again - but the desktop was fine, so obviously the network didn't mind. This is the weirdest most inconsistent problem I've ever encountered on Ubuntu. The networking even fails if I boot from the live CD. So then I tried an old Slax live CD and the networking didn't work on there either!

To make matters worse, it works perfectly in Windows XP!

The LEDs on the network card are all off, unless I start in Windows or turn the computer off.

Attached is my lspci -vv

---

### Post by compu73rg33k on 2008-09-08
I wonder if changing the MAC address of the card would make a difference?

---

### Post by compu73rg33k on 2008-09-08
Tried changing the MAC address and it had no effect.

After this weekend, I booted up my laptop and the LEDs were flashing and dmesg | tail said this:```
eth0: link up
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
NET: Registered protocol family 17
eth0: no IPv6 routers present
```

And now an hour later it's back to
```
eth0: link is not ready
```
I wonder if IP6 has something to do with the issue?

---

### Post by compu73rg33k on 2008-09-08
Wow crazy. I switched the hub in our room with the one in the lounge and now it works! Very weird b/c my friend said this hub didn't work with both his and his roommate at the same time but both my linux computers are running fine. I wonder if it was just a problem w/ that specfic port on the hub (but again, it worked in windows!) or if the hub was weird? I donnnnnno I hope it works for good now with this hub.

---

