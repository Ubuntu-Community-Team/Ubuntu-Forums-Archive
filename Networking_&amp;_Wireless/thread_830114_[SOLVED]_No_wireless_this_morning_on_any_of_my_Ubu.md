---
title: "[SOLVED] No wireless this morning on any of my Ubuntu's"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by causeitsme on 2008-06-15
My wireless network has been working just fine on my laptop and on my daughters desktop.

Has been working for over week.

Just this morning I opened up my laptop, which I had put into suspend last night, I hit a key to get it to start up and it went to a black screen with a message about test bios. I'm not sure exactly what it said but it was a short little message something like this:
RS(some numbers)    Test BIOS.....

After about 2 or 3 minutes when nothing else happened I did a hard restart by holding down the power button. GRUB started up, I selected Ubuntu and it started doing it's thing, I got the normal message about BIOS Bug #81 (which it always shows). Then Ubuntu started up. Everything was fine except, no wireless. So, I had my wife (who was sitting next to the router in the office) unplug it and plug it back in. Then my wireless came back up, but only for a couple of minutes and then went down again. Two more times I reset the router, no luck. No wireless.

So, after a couple of attempts to get it to connect to my wireless I gave up and went into the office and plugged in the ethernet cable. Wired network fired up just fine. So, I was wondering if maybe the router was bad. 

So, I went into my daughters room to check her Ubuntu wireless. I went to turn it on but, it was already running, apparently she didn't shut down when she left for vacation 3 days ago. Anyway, she wasn't connected either. So, I tried to get hers to connect, it wouldn't. All you get is the connecting icon and when you hover over it you get this message: "Waiting for Network Key for wireless network 'Belkin54g'" It's been saying that for thirty minutes now.

So, to check if it was a problem with the router, I shut down Ubuntu on the laptop and fired up Vista. Once started up, Vista wasn't online. So, I clicked connect to network, it only showed my Sprint Mobile Broadband as a connection, it didn't show the belkin54g. So, I closed that and opened network connections, nothing, Vista said to connect to a network to view other computers......  So, I closed that and went to Network and Sharing, Once there it showed no connection for about 10 seconds and then all by itself it showed the belkin connection and said it was connected but only locally. Then about 2 minutes later, it showed connected to internet also.

I'm lost, Ubuntu won't connect at all and vista took way long to connect, Normally, Vista and Ubuntu, connect to the network as soon as the desktop loads.

Any ideas why Ubuntu would do this? Could it be something with the router? (Vista didn't find it right away either)
btw: Under Ubuntu Hardware Drivers, it shows the wireless driver to be fine.

---

### Post by damis648 on 2008-06-15
I would say a router issue. You said you got Ubuntu to connect for a few minutes, and Vista connected, but only after a while when it finally found the network. You said your computer was a laptop? Do you have anywhere else you can go to try connecting to another wireless network and see if it works. If it does, your router is bad.

---

### Post by causeitsme on 2008-06-15
> **damis648 said:**
> Do you have anywhere else you can go to try connecting to another wireless network and see if it works. If it does, your router is bad.

That's a good idea, but I live in a pretty rural area so I won't be able to just run out and do that. 

One other thing, the desktop shows 'belkin54g' and also shows about half signal strength (it normally shows 90%+ signal strength).
The laptop, under Ubuntu, showed 'belkin54g' but with no signal strength. Vista is showing 'excellent' strength and I'm further away from the router than I was when reading the Ubuntu signal.

---

### Post by damis648 on 2008-06-15
> **causeitsme said:**
> That's a good idea, but I live in a pretty rural area so I won't be able to just run out and do that. 

One other thing, the desktop shows 'belkin54g' and also shows about half signal strength (it normally shows 90%+ signal strength).
The laptop, under Ubuntu, showed 'belkin54g' but with no signal strength. Vista is showing 'excellent' strength and I'm further away from the router than I was when reading the Ubuntu signal.

That is pretty interesting... did you install any recent updates?

---

### Post by Ayuthia on 2008-06-15
You might also try changing the channel on your router.  Sometimes that helps because there might be some interference in the air.

---

### Post by causeitsme on 2008-06-15
> **damis648 said:**
> That is pretty interesting... did you install any recent updates?

yes I did last night, I got the little 'Packages Available' icon so I clicked and they installed. I don't remember right off but they were some kind of lib, there were two of them. Is there a history somewhere so I can look them up?

No updates on hers though, as it has just been sitting there, she hasn't been home in the last 3 days.

btw: I 'fixed' my daughter's compuuter, just reinstalled. (Her's is really just a browser, im, and email tool for her.)
I really don't want to do that to the laptop though, it's all set up the way I like.

Sorry if I'm a little slow between posts, doing other stuff around the house in between.

Thanks

---

### Post by causeitsme on 2008-06-15
> **Ayuthia said:**
> You might also try changing the channel on your router.  Sometimes that helps because there might be some interference in the air.

Okay, I may try that, however, right now both the computers hooked up to the router through vista and worked fine.

---

### Post by causeitsme on 2008-06-17
Well, it started working all by itself. I used Vista for a while and rebooted into Ubuntu and it worked that time. Weird, I restarted it several times when trying to figure out what was wrong and those reboots didn't resolve anything.

Oh well, computers.....

---

