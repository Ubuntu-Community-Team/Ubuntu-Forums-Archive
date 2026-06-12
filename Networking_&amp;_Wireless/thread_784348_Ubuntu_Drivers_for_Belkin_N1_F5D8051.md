---
title: "Ubuntu Drivers for Belkin N1 F5D8051?"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by Mikeyspike on 2008-05-06
Hey guys, first post here.

Now before I go any further I'd just like to say that I have only just managed to get Ubuntu working on my computer so I have no clue on what to do, and where the hell things are :(

Also I do not have any internet connection so I can't get any apps Via the "terminal" (I have no clue on where that is either)

Ok, here goes:

I am in need of a Ubuntu driver for my wireless adapter, the F5D8051.I've had a quick search on google looking for one but still no luck. Do any of you guys know of any places where I can get a driver install for it? Remember, I have no internet connection what so ever. This is  what I need my driver for, so my wireless adapter turns on.

Thanks in advance :)

---

### Post by Jackie999 on 2008-05-06
First thing is you need to find out the chipset of your stick.

I have the F5D8053 and the chip is rt2870 and there are a load of posts here on how to get it running with the native linux drivers (which I haven't been successful with)...searching for info on the chip rather than the device model will help.

As an alternative you can install ndiswrapper  and  then use your windows .inf file (from the CD that came with your device)

To install ndiswrapper, if you aren't online, you can do it with the system/administration/synaptic package manager - search it and install - you may need to go into filters and tell it to search from the linux CD, rather than online.

After that's installed you'll see in System->Administraion->Windows Wireless Drivers ..this is where you point to the windows .inf file on the CD.

Hope this is of some help..I've only been using linux a few days myself :)

---

### Post by Mikeyspike on 2008-05-07
Thanks for that :) I shall try  that in a few minuets.

Also, a quick question.. How would I find out my Chipset?

---

### Post by Jackie999 on 2008-05-07
Well...google helped me find my chipset by searching the model...if I remember it brought me back to these forums.

But I think the files on the windows install disk were named rt2870.inf etc ...so, just install the ndiswrapper..point to the windows .inf file and see if that works.

---

### Post by lefterist on 2008-06-19
[http://linux-wless.passys.nl/query_alles.php]("http://linux-wless.passys.nl/query_alles.php")

---

