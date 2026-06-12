---
title: "[SOLVED] Firefox sssssslllllllooooooooooooowwwww"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Wildboar on 2008-01-12
From windows, works fine
From Ubuntu Gutsy used to work fine before wiping partition and starting over (Different issues)
Now...
Ping Router, Ok, 1-2 ms
Ping google, little slow but in range of last time I checked, 130 ms or sol
Synaptic and Add/Remove downloading 92 kb/s, seems about normal
Firefox wicked quick managing router, geologic scale as it hits WAN

Other computer Cat5'ed to router is working fine (Windows XP)

I'm running a Netgear WG311V3 with the drivers straight from Marvell (Same files I used last time)

I'd be pulling my hair out if I had any left after trying to get my last fancy keyboard to work. (It's back at the store)

---

### Post by desertphotog on 2008-01-12
Search for a post on how to disable IPv6 in Firefox.  That worked for me.

---

### Post by sports fan Matt on 2008-01-12
in Firefox try this:

In the address bar type about:config
then type in network disable IPV6 set it to true

See if that helps also try this article [http://rangit.com/web-browsers/13-tweaks-to-further-accelerate-your-firefox-20/](http://rangit.com/web-browsers/13-tweaks-to-further-accelerate-your-firefox-20/)
to see if doing any one of those steps helps..

---

### Post by twright on 2008-01-12
also try a webkit based browser (epiphany webkit, konquror webkit)

they run very, very fast :)

---

### Post by HermanAB on 2008-01-12
You may also have a lame DNS in /etc/resolv.conf.  Test the DNS response time with dig, then put the fastest one at the top of the list.

Cheers,

Herman

---

### Post by Wildboar on 2008-01-12
Tried everything above.  No Joy and actually caused it to go straight to "Could not find server" vice glacial page loading so I set everthing back to the way is was.

I forgot to past it into another file before switching to windows but the /etc/resolv.conf said approximately:

Invalid server list
192.168.1.1
Some other IP address

Is that what it should look like?

---

### Post by HermanAB on 2008-01-12
The minimum contents of resolv.conf is:
nameserver w.x.y.z

Where w.x.y.z is the nameserver of your ISP.  If you don't have it, get the addresses from the Windows machine.

---

### Post by Wildboar on 2008-01-13
Wow,
  Took a nap while my son played WOW on the windows machine.  Figured I'd try again and it works great with all my settings restored just as it was after the NDISWRAPPER install.

  Moral of the story?  World of Warcraft is not a waste of time...

Thanks for the ideas guys.

---

