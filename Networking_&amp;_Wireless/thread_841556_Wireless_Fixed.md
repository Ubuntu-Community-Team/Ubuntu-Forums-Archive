---
title: "Wireless Fixed"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Don DeGregori on 2008-06-26
I have been trying to get wireless to work on my Fujitsu laptop P5010D, off and on for months. Spent many hours with not much success,following the various "step by steps", and "how to". It uses the infamous BCM43xx chip set, which is a tough nut to crack. My laptop has the 4306. (Found out, it's really BCM4306legacy).

Here is what I did:

1.  Fresh installed Ubuntu 8.04 on the laptop. Downloaded all the updates.
2.  Immediately did dmesg on the terminal. Found many errors indicating   the b43legacy firmware never got loaded. It said to go here to correct the problem.  [http://linuxwireless.org/en/users/Drivers/b43#firmware](http://linuxwireless.org/en/users/Drivers/b43#firmware)
3.  I found the section and code for b43legacy. I noticed a make command, so went Synaptic and installed build-essential.
4.  Then, proceeded to follow the code as shown for b43legacy. Everything went smoothly.
5.  Did a Restart. Right after desktop screen was up, I disconnected the LAN cable, I clicked on the Network Icon, and proceeded to fill in requested info. Got the blue spinning dots and it connected. Went on Internet, no problem. Just to be sure, went back to the LAN, OK.

I can't say this procedure will work for other computers. Many have found the various How To's have worked for them, others, the various suggestions and steps have not. The above steps worked for me !

I can say this: THE DMSEG COMMAND IS YOUR FRIEND! It sure helped me. I should do this more often. It's best right after a problem shows up.

Good luck to all you BCM'ers !

Don

---

