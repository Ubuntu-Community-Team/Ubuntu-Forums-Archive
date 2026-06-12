---
title: "Ethernet adapter not connected"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by wiggy25 on 2010-12-21
Hi Guys.

I new it was going too well!!
Was surfing around this morning and everything was working fine.
I went to click on a bookmarked site and nothing happened, tried lots of other sites and Firefox justs sits there trying to access the page, eventually showing page not available.

Rebooted PC and opened email, strangely no password was asked for, clicked send/ receive and it sat there waiting.

Restarted again, same thing, but this time the notification icon flashed up saying wired network connection not connected.

Rebooted into Vista same problem, came up with Ethernet connection fault, which it couldn't repair.

The PC has an internal Ethernet card which is connected to my speedtouch router with an Ethernet cable.

Restored Vista to a previous date hoping that would at least get me online.
Rebooted directly into Ubuntu and this time password was asked for and notification pops up saying wired connection active.

Is there anyway I can see what has happened, I did read something about logs being stored, I just want to make sure I know how to sort this out if it happens again.
If I didn't have a spare laptop I would be a bit snookered as I would have been unable to get online.

I take it the first thing I would need to have done was reboot then select the safe mode from the boot-up screen.
I now have three showing on there.
The first is Ubuntu on Kernel 2.6.35-24-generic 
the next is the same but safe mode, the other two follow the same order with different Kernel versions.

From this point I would have been lost!!

Any help/advice would be great.

Cheers

Ian


EDIT:-

Happened again!
Seems to be happening on the carphonewarehouse website.
Spend 10 mins or so scrolling around looking at the different phones and then it disconnects the Ethernet.
I have to switch off the router and reboot all then seems to be ok and I can then go on any of the forums or web sites.
Just seems to be that one that kills the connection...luckily don't need to go on it again.

Must be something to do with the flash/firefox under Ubuntu causing it to drop out.

Cheers

Ian

---

### Post by Old_Man_Unix on 2010-12-21
> **wiggy25 said:**
>  
...Must be something to do with the flash/firefox under Ubuntu causing it to drop out...
 

 
Highly unlikely.
 
Trying not to get too technical here, so my apologies to the networking dweebs.
 
Internet connections work in "layers". The upper layers - where Firefox, Flash and such things reside - "use" the lower layer - where your HW resides. But the upper layers don't really control the lower layer.
 
So if your Ethernet connection is truly 'turning off' - as you stated - something is doing it directly. Or some part of the downstream chain is failing for some reason. I'd suggest you contact your ISP support to ensure that the problem is not with their portion of the chain.
 
If there are status lights on your modem /router/adapter port, it would also help to know what they are showing when the Ethernet 'turns off'. 
 
I know this is negative advice rather than positive, but it's all I can say without knowing a lot more about your connections.

---

### Post by wiggy25 on 2010-12-21
All LED's are showing green,

So we have Power, Ethernet, WLAN,DSL and Internet.

I can still access the internet via my works laptop running Vista, which is connected to the same router but as a wireless connection.

It's a bit odd.

Cheers

Ian

---

### Post by Lateralis on 2010-12-21
Try plugging your work's laptop into the router via an ethernet cable.  It is not impossible for one part of the router to go wrong whilst the other works fine.  For instance, my old router's wifi went but the wired ports worked fine.  Was thus OK if I only wanted to use my home desktop, but if I wanted to use my laptop around the house or connect my phone up to the internet using the wifi then I was stuffed!  

Thus... if your work laptop which works fine over wifi also works flawlessly and without hitch over the ethernet then the problem is probably with your hardware. 

The other thing to do, is try restarting the router when your internet drops again.  Again, it has happened before that the lights can be on but there's nobody home, i.e. it looks like everything works but actually it doesn't.  Restarting the router may just help.

---

### Post by wiggy25 on 2010-12-21
Thanks.
The laptop works fine, as does the PC when running Vista.
Using Firefox went to the same web sites on both Laptop and PC and all perfectly OK.
 
Do the same thing running Ubuntu and at some point the notification that there is no connection.
 
Switch off router and reboot PC all is well again.
 
Very odd.
 
Cheers
 
Ian

---

