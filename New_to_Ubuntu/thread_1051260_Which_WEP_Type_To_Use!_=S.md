---
title: "Which WEP Type To Use?! =S"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by wildfire95 on 2009-01-26
In vista it only has the WEP key option... but on Ubuntu it has 128bit and more, which 1 is the one to use? 

Or is there a tool to use?

---

### Post by kingmonkey on 2009-01-26
Depends on your wireless connection settings.

Generally 
WPA2 is better than WPA is better than WEP is better than nothing

---

### Post by billgoldberg on 2009-01-26
> **wildfire95 said:**
> In vista it only has the WEP key option... but on Ubuntu it has 128bit and more, which 1 is the one to use? 

Or is there a tool to use?

Depends, see what works.

If you router supports WPA or WPA2, use that.

Wep can be hacked in a few minutes.

Then again I don't use wireless encryption anymore. Just some mac filtering.

---

### Post by Coreigh on 2009-01-26
Vista supports a number of different wireless security protocols. Though different options seem to be available based on how you are connecting or creating the wireless account. I had been using WEP first in 64bit then 128bit but recently switched to WPA. Then I had to re-connect one just today and I did have some difficulty getting Vista to show me the options I needed.

This all assumes you are using Vista to manage wireless networks and not a 3rd party application that came with the router / access point.

You best bet is likely to go to the router manufacturer's website and look for help or directions.

---

### Post by Hospadar on 2009-01-26
I say no wireless security!

Here's my deal:
Any skilled "hacker" (and/or person who has downloaded the correct programs) can break a wep key in <5 minutes usually.
WPA keys take longer, but are still breakable.
If you are just worried about those pesky neighbor kids hogging your bandwidth, just block their mac addresses, if they are determined enough to spoof a mac address, they are probably not too far off cracking your password anyways.

Any site that uses ssl (a site that starts with http**s**) is going to be secure whether or not your wifi is encrypted, and you should't be putting sensitive information (bank password, credit card numbers) into a non-ssl site anyways, as someone not parked outside your house in a scary van could still eavesdrop on this information.

Now of course, you may just like using a wifi password, which is fine.  In that case, for a wep password, the more bits, the more secure (although all wep passwords are relatively easily broken).  If you go into your router's config (which is typically accessed through a web browser when connected to your router, at some address like 192.168.0.100, check your manual) and go to the wireless security settings, you'll be able to see what type of password you are using.  if it's a wep key (big long nasty string of 0-9, a-f) you are probably using 128 bit wep.  if it's a password, probably wpa.  If you have the option to use wpa, it's much more secure, and you should absolutely use it.  not to mention the fact that generally you can use a more normal password (although a cryptic combination of letters is more secure)

Besides, in the futuristic land of broadband in which we currently reside, I think it's a very neighborly thing to do to leave your wifi available for your neighbors and friends in case they need it.

I've cheaped of many a wifi in times of need and been greatful for it.  Just make sure you put a password on your router so people can't monkey with your setup.

---

### Post by Hobgoblin on 2009-01-26
> **Hospadar said:**
> 
If you are just worried about those pesky neighbor kids hogging your bandwidth, just block their mac addresses, if they are determined enough to spoof a mac address, they are probably not too far off cracking your password anyways.


WPA2?

Are you sure.

Back on subject.

Vista does have WPA and WPA2 options, sometimes they can be hard to find.  Especially if you use the software which comes with the network adapter.  Go to Start > Connect to.... instead.

---

### Post by webdevelopment on 2009-09-16
new to ubuntu and my xp computer that's hooked up to the wireless just says its using WEP and i have the long hex code... but...

which WEP do i select in ubuntu?

how do i view all available networks like in windows?

why can't i just type an ascii word instead of a mile long hex code like in windows?

i still cant get connected to wireless on my ubuntu machine... why is this so darn difficult?

are there any add-ons that would do the things i want? (view available networks like in vista, be able to type ascii instead of hex password)

thanks in advance....

---

### Post by webdevelopment on 2009-09-16
> **webdevelopment said:**
> new to ubuntu and my xp computer that's hooked up to the wireless just says its using WEP and i have the long hex code... but...

which WEP do i select in ubuntu?

how do i view all available networks like in windows?

why can't i just type an ascii word instead of a mile long hex code like in windows?

i still cant get connected to wireless on my ubuntu machine... why is this so darn difficult?

are there any add-ons that would do the things i want? (view available networks like in vista, be able to type ascii instead of hex password)

thanks in advance....

im saying that my vista doesnt say which type of WEP, just plain old WEP

---

