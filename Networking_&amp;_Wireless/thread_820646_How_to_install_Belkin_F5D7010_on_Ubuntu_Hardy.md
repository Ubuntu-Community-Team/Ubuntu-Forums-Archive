---
title: "How to install Belkin F5D7010 on Ubuntu Hardy"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by lloydwood on 2008-06-06
I thought I would post this because I actually found it very easy! There seem to be a few quite complicated guides for this but I found a simpler way that might save people some pain.

I should note I'm using the Belkin F5D7010 v7 on Ubuntu 8.04 (Hardy).

I bought it off the shelf from PC World (although I'm sure there are many other places you could get it!). It comes with a windows installation CD that contains the drivers you need.

**Step 1:**

Plug it in to your card slot and turn the computer on.

**Step 2:**

Go to System>Administration>Synaptic Package Manager
Put in your password

**Step 3:**

Click reload to make sure you have the latest package list
Search for "ndis"
From the search results select and install: ndisgtk, ndiswrapper-common, ndiswrapper-utils-1.9
[B]
Step 4:[/B]

Go to System>Administration>Windows Wireless Drivers (What we just installed)
Click Install New Driver and select blkqgnv7.inf on the driver CD in Files/WINXP/

Then click install and you'll see your driver in added. It should say Hardware present: **Yes**

**Step 5:**
Go to System>Administration>Network
Do the unlock thing.
You should now have a wireless network that you can configure.
Click on it and then on properties.
Select your wireless hub and put in the passcode etc.

Done!

---

### Post by halg69 on 2008-06-17
Hello, I followed your quick guide and it worked the first time, and after configuring the WiFi I forgot to save the config.

Shutdown the machine and when I turned it back on again no WiFi.

Anyway I tried reconfiguring, saving, de & re -install the DRVs, etc and still eveng dough all these changes I still can't get an IP address assigned to the wireless card.

Even when trying to configure it does "see" all the available WiFi's around my home.

Running Ubuntu 8.04 and the same Belkin card.

Any ideas ?

I'll appreciate any feedback you have or anyone reading this thread.

Thank you again!

halg69

p.s.- Just got on the Ubuntu bandwagon and really liking the OS

---

### Post by DavidWilliams on 2008-09-28
I followed your directions correctly and I can't seem to get it to work.

The computer is an old Dell Inspiron 5100 that I've put Ubuntu on.

The router is a Linksys WRT54GL running w/ a WPA Personnal TKIP encryption.

For some reason Ubuntu can't even connect to my network through my wireless card and I really don't want to have the cable running to my laptop.

I'm brand new to Ubuntu and am wondering if you could provide some extra help?

---

### Post by DavidWilliams on 2008-09-28
*** Error w/ Connection ***

---

### Post by Franklin383 on 2011-05-30
Hello I know this is an old thread but I was wondering if some one can send me a link for the blkqgnv7.inf driver I have looked every were and no luck. My wireless card come with the computer and no drivers disk. Tried there website but still no luck.

Thinks For Your Help

---

