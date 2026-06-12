---
title: "anyremote client issues"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by NikS on 2011-07-28
Hi all,
I have installed anyremote on my ubuntu 11.4 machine and the client on my Nokia N78 phone. The problem is, I don't understand how to use the client. It starts properly. Then I select search and it lists some 70 or so options..something like: comm:USB1, comm:COM1, comm:IR1, and comm:BT1, comm:BT2 upto comm:BT64. What do I select of these? I wish to connect it over bluetooth.

Weird thing is, these options are shown even when there is no other bluetooth device in the vicinity, let alone anyremote server!

Tried all the BT/USB/COM options (with bluetooth and anyremote turned on on my PC).. every time get the same thing: openConnection Exception. IR causes my device to hang.

Have searched the internet and found most people face issues on the server side of this.. The only reference to such an issue was in [anyremote FAQs]("http://anyremote.sourceforge.net/faq.html#faq16") but following the instructions there to yields the same problems!

Anyone able to get past this? Can someone guide me through?

---

### Post by Wim De Winter on 2012-03-21
I solved your ussue like this:

In terminal I typed ```
hcitool dev
``` and your BT "address" appears (e.g.: AB:12:CD:34:EF:56)

I used that information that's shown to manually enter a BT address like this: AB12CD34EF56:19, where 19 is the channel I use.

Then enter this in terminal: ```
anyremote -s bluetooth:19 -f /location/of/your/config/file
``` See where I mentioned channel 19?

That did it for me. Now I only need some tweeks to my config file to make it actually work. Sigh...

---

