---
title: "Acer Travelmate 2410 Broadcomm issue"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by IainPurdie on 2008-07-21
Yes, this chestnut again... I've found a ton of posts about these issues with 8.04 but it's very hard to find any solutions with the threads running into 300+ posts! I've dug and dug, but can't find a solution to this particular issue.

Excuse the lack of copy/pasted results from command line instructions but due to the nature of the problem it's hard to get them onto a machine that I can get online with!

When I installed 8.04, I had a small issue with the wireless card on my laptop (a Broadcomm BCM93418MPG). With a tiny fiddle (I can't recall what, exactly, but the details were from here) I got it going using the default driver. Then "that update" came out and since then I've had no luck.

I followed the instructions on:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

And I've tried the driver file suggested, another from a similar thread, and also the existing Windows driver file from the same laptop which I know to work (under Windows at least). The end result is the same. Running `lshw -C network` gives me an interface that looks like it should work but is displayed as `*-network DISABLED`.

Running `sudo iwconfig wlan0 up` removes the "DISABLED" but still gives me no network to tinker with under network manager.

I have also tried blacklisting "ssb" as mentioned elsewhere, though do note that if (instead of this), I alter the "wirlessfix.sh" file in the main document mentioned to run ssb *before* "ndiswrapper" (i.e. add an extra "modprobe" line) I don't have the issue with the DISABLED message. Still no working wireless, though.

So no joy using "ndiswrapper" and none with the new Native Driver either.

Apologies for repetition of a question, but as I said it's come up buried deep within other threads and I've yet to find a solution if there is one out there. And believe me, I've spent enough hours digging this evening... Worst case, can anyone recommend a USB or PCMCIA wifi card that wil *definitely* work and which is readily available in shops? I'm in Vietnam travelling right now so I can't exactly hop on eBay :)

---

