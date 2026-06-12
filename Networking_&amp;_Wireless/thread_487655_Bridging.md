---
title: "Bridging"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by ErusGuleilmus on 2007-06-29
I have an old box running Ubuntu 7.04, and am trying to use it as a free router. I put four LAN cards in, and Ubuntu does detect them, but I don’t know how to bridge them. To give you a better idea of what I’m trying to get at, when in Windows, you can go to Network connections and highlight all of the network cards and then right click and press bridge connections. Windows then creates a network bridge. If it is at all relevant, I am using this to connect four Xbox 360's for LAN play. In my experience right after you create the network bridge in Windows, you can simply plug in the Xbox's and play some LAN games right off the bat, with no further modification to network settings.

           Thanks for all the help.

---

### Post by t4thfavor on 2007-06-29
whats wrong with a regular hub, or switch? you can get them for like $5.00 on ebay.

What you seek is bridge-utils.
sudo apt-get install bridge-utils

Then proceed to set up the bridged interfaces (you can get like 1 million tutorials online by searching "brctl")

I am still not sure this idea would work without crossover cables unless your nics are auto uplink capable. better to buy a cheapo hub, and save on electricity.

---

### Post by ErusGuleilmus on 2007-06-29
Thanks. The reason I don&#8217;t just go out and buy a cheap hub is because I have quite a few. I was just curious on how to do a bridge.  I also use the computer I was talking about as a teamspeak server, any way, its location is at my friends house, so who cares about how much electricity it uses. :)

P.S. My freinds and I have a ton of x-over cables.

---

### Post by t4thfavor on 2007-06-29
Sweet then your all set. I just wanted to make sure you knew what you had to do to get it to work.

---

