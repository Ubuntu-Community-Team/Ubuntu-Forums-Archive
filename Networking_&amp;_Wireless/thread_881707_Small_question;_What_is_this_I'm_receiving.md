---
title: "Small question; What is this I'm receiving?"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Jojan on 2008-08-06
What is this I'm receiving? Marked with red in the picture. It comes frequently, as you can see. I don't have a clue what it is.

---

### Post by scorp123 on 2008-08-06
Sorry to say so but that screenshot is pretty much useless as it does not contain any information about what we are looking at.

If you want to find out what's going on inside your network: forget about that fancy GUI stuff and start looking at log files and packet sniffers ;)

---

### Post by wannadumpwindows on 2008-08-06
You can install a program called "etherape". It will show you where every connection from your machine is going. It's a nice little tool for situations like this.

Turn it on, select your network interface in the drop down menu, and everything that your machine is connected to will come up by ip address or hostname.

And then you can go from there.

---

### Post by scorp123 on 2008-08-06
> **wannadumpwindows said:**
> You can install a program called "etherape". Good idea. Another good one is "tcpdump", but that is for terminals only. But then again you can copy & paste terminal output here into the forum in case you see anything strange.

---

### Post by wannadumpwindows on 2008-08-06
Thank you.

I just figured, with the vagueness of the question, etherape might be a little easier to grasp for the OP. And it's the only one I could come up with right off the top of my head.

---

### Post by Jojan on 2008-08-07
Thanks for the replies.

Both thoose software you recommended said that "no suitable device found". What device are they looking for and how do I help them find it?

---

### Post by wannadumpwindows on 2008-08-10
> **Jojan said:**
> Thanks for the replies.

Both thoose software you recommended said that "no suitable device found". What device are they looking for and how do I help them find it?

Open up a terminal, and in it type:

```
iwconfig
```

And whatever interface you're using for your network connection, just select that one in the dropdown list.

P.S. You also need to be running etherape as root. There should be two choices in your menu, one for "etherape" and one for "etherape (as root)". Choose the one for root. After that you should be all set.

---

### Post by Jojan on 2008-08-11
Works just fine now. Thank you. I'll quit some stuff and then I'll see what it is. I might post here what it is.

---

### Post by Jojan on 2008-08-12
This is what I get. I know that 192.168.0.1 is our router, but not what 239.255.255.250 is.

After a bit of Googleing It seems to have something with Windows XP to do, which is what three other computer in this house run.

---

### Post by wannadumpwindows on 2008-08-13
> **Jojan said:**
> This is what I get. I know that 192.168.0.1 is our router, but not what 239.255.255.250 is.

After a bit of Googleing It seems to have something with Windows XP to do, which is what three other computer in this house run.

That's probably what's called the broadcast address for your network. The one xp uses anyways. It's how computers on the network "know" when something else is there with out having to actually send something to each host.

---

### Post by sandysandy on 2008-08-13
> **Jojan said:**
> but not what 239.255.255.250 is.



thats the subnet mask.

[http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)

[http://www.webopedia.com/TERM/S/subnet_mask.html](http://www.webopedia.com/TERM/S/subnet_mask.html)

[http://www.webopedia.com/TERM/S/subnet_mask.html](http://www.webopedia.com/TERM/S/subnet_mask.html)

regards

---

### Post by Jojan on 2008-08-14
Thank you.

---

