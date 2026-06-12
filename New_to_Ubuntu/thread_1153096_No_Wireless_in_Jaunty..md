---
title: "No Wireless in Jaunty."
date: 2009-05-08
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-05-08
I haven't installed Jaunty but tried a LiveCD run yesterday.

Things were pretty much the same as in Ibex. The things I did notice were the Open Office was 3.0, there were extra programs, and... my wireless didn't work.

I'm wondering if I upgraded to Jaunty via the internet would my wireless be broke???

---

### Post by billgoldberg on 2009-05-08
Not sure.

It could work, maybe the drivers are in "Hardware Drivers".

It's no big deal, you can most likely get it working with Ndiswrapper any way.

---

### Post by emeraldgirl08 on 2009-05-08
The Wireless card is an Cisco Aironet 350 and as far as I know it's a little buggy sometimes. 

Not in my current setup but as far as using WPA-PSK encryption and when I ran a LiveCD of Heron.

I'd like to think that there is a legion of diehard Thinkpad users out there and someone is savvy enough to code their way to 100% compatibility with my kinda card.

---

### Post by tomszyszko on 2009-05-08
New kernel was missing a restricted modules package -- Now been fixed - if this doesnt work now after update use ndiswrapper. Jaunty is worth it finally can drop critisisms from windows users that ubuntu "boots slowly", because they assume that when you see the desktop in winblows its done.

Finally I can get jaunty down to the speeds of my FC6 install

---

### Post by superprash2003 on 2009-05-08
if it worked with the previous versions.. then it most likely should work in jaunty as well.. getting wireless to work via LIVE cd is very tricky

---

### Post by emeraldgirl08 on 2009-05-08
> if it worked with the previous versions.. then it most likely should work in jaunty as well.. getting wireless to work via LIVE cd is very tricky
I knew there would be some kind of limitation on LiveCd'ing. I just know that I probably would have a nightmare of time if I did upgraded my Ibex and it would not work.

> Jaunty is worth it finally can drop critisisms from windows users that ubuntu "boots slowly", because they assume that when you see the desktop in winblows its done.
Is there a faster booting time???

---

### Post by superprash2003 on 2009-05-09
yes.. 15-20secs i believe.

---

### Post by swoody on 2009-05-09
I had the same issue - I've never had wireless work on my laptop on the liveCD, but once installed my drivers have always been in "Hardware Drivers" Also, yes Jaunty does boot a bit quicker by itself. It can boot even faster if you use the ext4 file system :)

---

### Post by Scunnered on 2009-05-09
It was the fact that I could have a wireless connection from the Jaunty live CD that convinced me to do a full install.  When I connected via the network manager I received an immediate connection

It may be that you would be better looking at whether you can afford / install a better card than suffer having to mess about.

---

### Post by -kg- on 2009-05-09
One more thing:

Can you see your wireless network with the widget (top menu to the right)?  If so, do you have WEP or WPA enabled?  You'll need to enter your security key in order for the wireless to connect with the network.

Sorry if you already know what you're doing, but you wouldn't believe how many problems that have been found by my asking obvious questions.:P

And this very same thing caught me a couple of times before I figured it out! ](*,)

---

### Post by emeraldgirl08 on 2009-05-10
> Can you see your wireless network with the widget (top menu to the right)? If so, do you have WEP or WPA enabled? You'll need to enter your security key in order for the wireless to connect with the network. I'm  new to Ubuntu....linux in general and the first version of Ubuntu I tried was with a LiveCD of Intrepid. My wireless was showing but I could not get a connection established. Knowing that I could at least see my network I installed it anyway. At the time we were using a WPA-PSK encryption and because of my Cisco Aironet 350 I could not use the WPA. I had a couple of people tell me they just switched over to WEP so that's what I'm begrudingly using now! I'd prefer the WPA but still need more info on compatible cards with my Thinkpad.

> It can boot even faster if you use the ext4 file system
I need to read more about this. I've seen a thread or two describing something like this. I'm expecting a new HD early next week is why I was asking. Oh and you're from Chicago??? I used to live in Broadview for awhile :) Miss the food and vibe there!

---

### Post by swoody on 2009-05-11
> **emeraldgirl08 said:**
> I need to read more about this. I've seen a thread or two describing something like this. I'm expecting a new HD early next week is why I was asking. Oh and you're from Chicago??? I used to live in Broadview for awhile :) Miss the food and vibe there!

Well here's a little reading for you on ext4 benchmarks:
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks)

Yeah, Chicago is a pretty nice town. Always something going on, the people are great here, and you'll never be able to find better food than in Greektown ;) Where are you at in AZ now? I have a friend who went to a culinary school out there, and moved out there after he graduated.

---

