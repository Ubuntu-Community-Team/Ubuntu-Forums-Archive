---
title: "Wireless is working...  sometimes..."
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by johnjust on 2007-10-08
Wireless has been on and off with my laptop, and just when I thought I finally had it solved, it's broken again...

I recently reformatted with a Kubuntu disc from Canonical, ditching the .iso I made a couple weeks ago.  While I was using the .iso, the disc checker said it was a valid disc, yet form some reason, my wireless wasn't working, and ndiswrapper wasn't working the way it should (something was messed up from the install, I think the disc was bad even though it said it wasn't).

The new format gave me no wireless out of the box, but I installed ndiswrapper, and I had it working, but my KNetworkManager didn't display any wireless connections, just Wired.  I read up about editing the /etc/network/interfaces file, and uncommenting everything but lo, eth0 (wired), and wlan0 (wireless).  That still gave me no networks.  But I figured, "hey, at least wireless is working."

So this morning, at work, I find that, of course, since I configured my /etc/network/interfaces file, and added the two lines
```

wireless-mode  managed
wireless-essid  linksys

```

that it would be a simple case of merely changing the ESSID.

Boy, was I wrong.

Now, it's not showing any wireless networks (there should be two in the building, let's call them 'linksys1' and 'linksys2', for lack of originality on my part), and I can't connect to them even when I manually enter the wireless-essid.  I also have wifi-radar installed, but it wasn't working.  I found a thread saying to run
```

sudo rm /var/run/dh*

```

which removes 3 files for me: dhcdbd.pid, dhclient.wlan0.pid, and dhclient.eth0.pid (I backed them up before removing them, just in case.

All of a sudden, I have 1 of the 2 networks listed in my KNetworkManager, but it stalls out at 28%.

lspci tells me I have Intersil Prism 2.5 Wavelan Chipset, and I installed the bcmwl5 driver, which was working for me at home.

Any suggestions?  If you need any more info, ask me for it, I'm working on a wired machine, so I'll have to transpose the output from my laptop.

---

