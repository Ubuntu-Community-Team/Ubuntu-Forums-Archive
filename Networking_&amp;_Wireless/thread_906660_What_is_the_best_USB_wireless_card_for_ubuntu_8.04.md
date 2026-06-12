---
title: "What is the best USB wireless card for ubuntu 8.04?"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by Rain724 on 2008-08-31
Well, because the dell WLAN card in my XPS M1530 isn't supported by ubuntu 8.04 yet :(:(, and the rt73 drivers don't want to work for my linksys WUSB54GC :(:(, i am in the market for a new USB card. What USB cards do you guys use in ubuntu 8.04? Which one seems to be the best?

If you can give me some advice on what i should buy, that would be great!

Thanks in advance,
Rain

---

### Post by battledean on 2008-09-04
I have a Edimax 54 Mbps Wireless USB stick with Antenna.  Initially I had a few problems with it but after following a post here and compiling the latest version of the serialmonkey rt73 drivers it works like a charm and is rock solid.

---

### Post by Michl on 2008-09-18
> **battledean said:**
> I have a Edimax 54 Mbps Wireless USB stick with Antenna.  Initially I had a few problems with it but after following a post here and compiling the latest version of the serialmonkey rt73 drivers it works like a charm and is rock solid.

There's a little hitch with this and other suggestions like
it.  To install the drivers, ndiswrapper, use the scripts in
hendrick's thread, you need linux headers, which do not
install from the disk.  To install you need to be online, 
BUT THE FRICKING PROBLEM IS HOW TO GET ONLINE.

SO:  IS THERE A USB ADAPTER THAT WORKS OUT OF THE BOX
WITH HERON?  Some report that wusb54gc works out of
the box with HArdy, but it doesn't for me.  It is not
a matter of setting it up.  It's a matter of nothing
showing on lsusb.

---

