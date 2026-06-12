---
title: "Computer still responds to ping"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Sarah L on 2008-05-24
Hi,
I've installed Kubuntu Gusty on my computer. Running a GRC ShieldsUP test ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)) shows that all ports are "stealth" but ping requests are still being responded to. I've installed Guarddog and set it up drop ping requests, but my computer still fails the ping test.

What's wrong?

---

### Post by SpaceTeddy on 2008-05-25
i don't know any programms that do the configuration of pakets for you, but - what is the output of the following command
```
sudo iptables -L --vnx
```

let's see if the rules got added properly.
let's see if we can figure this out :)

---

### Post by maugud on 2008-06-18
Hi, try install Firestarter and in Preferences enable ICMP filtering

---

