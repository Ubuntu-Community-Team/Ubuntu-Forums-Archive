---
title: "Hardy Heron Wireless issues!"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by ajwak95 on 2008-06-13
Hi, I just recently upgraded to Hardy Heron, and my wireless doesn't work. It can detect the networks, and when I type in the correct password for the wireless, it gives me the connectivity bars, but connectivity is at 0%. When I do this wireless on Ubuntu, it crashes my 2WIRE Home Portal, and I have to stop trying to connect. I am not able to download any drivers as I can't even get Ethernet to work. Please help me.

---

### Post by rlzyoner on 2008-06-13
Sounds like a driver issue.

Are you sure you still have the drivers for your wireless card installed on the machine

---

### Post by ajwak95 on 2008-06-13
Well, I don't know where to get the Drivers for it. Right now im updating Vista, so I cant boot into ubuntu. I didn't think that I needed drivers. My wireless card on my laptop is showing its working. Like I already stated, my card works, it just isn't letting me go to the network, it shuts down the network.

---

### Post by rlzyoner on 2008-06-13
I had a similar issue a while back whereby I installed ndiswrapper but had not set it [correctly] to point to the windows drivers for my wireless card.
Doing so corrected the issue.

Like you my network manager indicated that a signal was being received but when I input the WEP key, it remained at 0% and did not connect.

---

### Post by ajwak95 on 2008-06-13
> **rlzyoner said:**
> I had a similar issue a while back whereby I installed ndiswrapper but had not set it [correctly] to point to the windows drivers for my wireless card.
Doing so corrected the issue.

Like you my network manager indicated that a signal was being received but when I input the WEP key, it remained at 0% and did not connect.

So I need to install NDISwrapper?

---

