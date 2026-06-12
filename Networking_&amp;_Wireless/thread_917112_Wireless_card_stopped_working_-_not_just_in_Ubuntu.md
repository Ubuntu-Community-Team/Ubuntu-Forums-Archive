---
title: "Wireless card stopped working - not just in Ubuntu"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by vigliarb on 2008-09-11
Hello everyone - 

I'm in need of some help.  I have had no problems with Ubuntu since installing it this summer, but ran into a problem last night with my wireless card.

I wasn't doing anything out of the ordinary, and when I checked the status of a download I was working on, I noticed the connection had died, and my wireless seemed to have quit.  My eee PC was sitting next to me and was working just fine, so I figured it was a driver issue and not the router/modem.  I booted into windows to see if it was working there, but Windows didn't seem to be recognizing the wireless adapter either!  I had made a couple changes to Windows (including a system update), but since Ubuntu is running on a completely separate hard disk that Windows doesn't even recognize due to the formatting difference, I wasn't thinking that it was the system update that could have done it.  Besides, the failure in the wireless seemed to happen in the middle of an Ubuntu session, and not at start up. 

I did a system restore to Windows, and it made no difference.  Ubuntu doesn't show a wireless adapter in ifconfig either - neither OS seems to think the wireless card is there.  

If this helps anyone, here is a list of what I had run/installed right before the card died:

-GTKpod
-One other Linux iPod manager that I can't recall the name of
-iTunes 8 in Windows
-Whatever update Windows barked at me to install.

I rolled back Windows (upon further reflection, iTunes 8 is still installed) and uninstalled the iPod managers for Linux, but still nothing.  Does anyone know what the problem could be?  I'm hoping my wireless card didn't die.  I don't think I can afford a new one right now!

Thanks for any help you all can give, and I hope this wasn't too long of a post.

---

### Post by tgalati4 on 2008-09-11
In Ubuntu, you can check your hardware listing as follows: (in a terminal)

>hwinfo --short

It's possible that your card overheated during a download of iTunes8.  It may be temporary (wait for it to cool down) or permanent--warpage of the dsp chip that runs the wireless.  

If it's a pcmcia card, take it out and see how warm it feels.  If it's built into the motherboard, then go into the bios and try shutting it off, boot up, then shutdown, then turn back on in the bios, then reboot.  (Windows users seem to like to reboot often.)

Try removing the battery for a few minutes. This can sometimes reset the sticky settings in the wireless chipset.

How bad is iTunes8?

---

### Post by vigliarb on 2008-09-11
iTunes 8 is just as horrible as the previous versions - luckily it will install music to an iPod that wasn't purchased via the store.

The only reason I even downloaded it was because a friend of mine got an Apple laptop and gave me his free iPod touch.  The 2.1 firmware came out the day I got the damn thing from him, so when it updated I lost the ability to jailbreak it until someone cracks the code. 

I'm at work now, but I plan on messing with it when I get home - it's been off since last night, so maybe it will be one of those miracle fixes.  Either that, or it's time to haul the darn thing out from under my desk and start unscrewing the case!  

Ugh...

---

### Post by vigliarb on 2008-09-11
I tried what you said to do, and yes - it is a motherboard card.  No fix, though.  I decided to relocate my router and modem to my bedroom instead of the living room, so I'm attached via cable now, and everything is working fine.  I don't like giving up on a problem, but I might just have to get a new wireless card.

If anyone else has any suggestions, please let me know.  I would like to resolve the issue without having to resort to purchasing a new card if I can.

---

### Post by Turwaithien on 2008-09-11
My wireless card just did the same thing...I was installing a bunch of programs at the time and it just stopped. Do you think I should just give up on it? Or perhaps there is (please let there be) a way to fix my card?

---

### Post by warsql on 2008-10-06
FYI, my wife's 3 year old Compaq had its wifi card die a couple months ago. It is a known issue and Compaq fixed it for free, including postage, despite being well out of warranty.

---

