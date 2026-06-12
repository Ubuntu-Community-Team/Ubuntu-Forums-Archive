---
title: "100% Compatible Cards?"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by k2pow on 2006-12-23
So after much time trying to use ndiswrapper with my broadcom dell, I have decided to go to bestbuy and get a new card(non broadcom). Does anybody have a card that works out of the box that way it can save me a whole lot of time?

---

### Post by tturrisi on 2006-12-23
D-Link DWL G630 works after installing the restricted modules, has an atheros chipset and even works w/ kismet too.  Most new Linksys cards have broadcom chipsets.  Check chipsets here first:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
Atheros chipsets are the probably the best way to go today in linux because the drivers are robust and well developed.

---

### Post by az on 2006-12-23
The Realtek chipsets are 100 percent free-libre GPLed software.

You should really be asking the people at BestBuy.  That's their job.  

Users should not have to worry about this stuff anymore.

---

### Post by tturrisi on 2006-12-24
> **azz said:**
> The Realtek chipsets are 100 percent free-libre GPLed software.

You should really be asking the people at BestBuy.  That's their job.  

Users should not have to worry about this stuff anymore.
The people at Best Buy do not know what chipset a wifi device has inside it, and that is the key to knowing if the device will work with linux.  It's not really their job to know what the chipsets are because the chipset is not shown on the box or on the device.  Stores that wish to make money selling hardware cater to Windows, there's no real money or profit to be made by specializing in linux just yet.

---

### Post by k2pow on 2006-12-24
Ive been thinking about getting linksys wmp54g or the D-link WDA-1320, and one know if those work perfectly out of the box?

---

### Post by az on 2006-12-24
> **tturrisi said:**
> The people at Best Buy do not know what chipset a wifi device has inside it, and that is the key to knowing if the device will work with linux.  It's not really their job to know what the chipsets are because the chipset is not shown on the box or on the device.  Stores that wish to make money selling hardware cater to Windows, there's no real money or profit to be made by specializing in linux just yet.

It's their job more so than mine!  They get paid for being knowledgeable about their products, don't they?

I used to do my own homework until I realised that I shouldn't.  I visited stores and asked about linux compatibility.  I walked out and told them why, when they couldn't help me.

Before I moved from Montreal, I was able to go into a few different computer stores and ask not only for linux-friendly stuff, but stuff with free and open drivers as well.

You must ask.  If you don't you will never recieve.

---

### Post by tturrisi on 2006-12-24
> It's their job more so than mine! They get paid for being knowledgeable about their products, don't they?
As a matter of fact, no, that's not what they are paid to do.  They are paid to assist customers in where to find a product in the store, to retrieve the product the customer selects and where the cashier is loacted!  They are lower on the rung than a salesman.  These folks are not technicions, it's not a part of their job description.

However, best Buy & Circuit City now have help desks with technicians, some of which are knowledgable, most are not.  let's face it, any technician worth his salt is not working at a Best Buy or Circuit City.  It's kind of like saying that the burger slingers at McDonalds are chefs.

The 3 points I am stressing here are:
1. Chain stores don't hire real technicians; consumers should not expect the guys on the flooor there to know anything at all about Linux.
2. 99.99% of all computers sold in stores are built for the Windows operating system (or MAC), don't expect manufacturers of comps-comp hardware & stores to support Linux.
3. It is the consumer's responsibility to do his own research prior to purchasing; the degree the consumer neglects this responsibility is directly proportional to the degree of problems he gets with his purchases.  Neither the store personell or the customer have a higher degree of responsibility, both are 100% responsible.  Having THAT viewpoint allows one to make the best decisions.

k2pow  is a smart consumer, he is doing his research by asking questions here.  That's what this forum is all about!

> Ive been thinking about getting linksys wmp54g or the D-link WDA-1320, and one know if those work perfectly out of the box?
The WDA-1320 has an atheros chipset and will work fine after you:
1. enable the MultiUniverse repositories in Synaptic.
2. install the linux-restricted-modules that match your current kernel.
The restricted modules contain the madwifi driver, which is the driver for atheros chipset devices.

---

### Post by az on 2006-12-24
> **tturrisi said:**
> As a matter of fact, no, that's not what they are paid to do.  They are paid to assist customers in where to find a product in the store, to retrieve the product the customer selects and where the cashier is loacted! ... let's face it, any technician worth his salt is not working at a Best Buy or Circuit City.  

I would never buy anything for my computer from someone who was not a computer geek.

If you walk into a compter store and ask about wireless and the person you are talking too looks scrared, just walk away.

> **tturrisi said:**
> 
The 3 points I am stressing here are:
1. Chain stores don't hire real technicians; consumers should not expect the guys on the flooor there to know anything at all about Linux.
2. 99.99% of all computers sold in stores are built for the Windows operating system (or MAC), don't expect manufacturers of comps-comp hardware & stores to support Linux.
3. It is the consumer's responsibility to do his own research prior to purchasing; the degree the consumer neglects this responsibility is directly proportional to the degree of problems he gets with his purchases.  Neither the store personell or the customer have a higher degree of responsibility, both are 100% responsible.  Having THAT viewpoint allows one to make the best decisions.

1.  I don't expect every BestBuy to be able to give you the same level of service  ( I only mentioned BestBuy because that is what k2pow first mentioned).  I am saying that you should ask for it.  I let my wallet let them know if they are doing something right.
2.  Manufacturers do get the point, but linux does not have the market share for them to make it as easy as it is to buy stuff for windows.  Market share is climbing fast, though.  My point is that if you don't ask, you will never receive.  

I have walked out of a few stores in the past.  I encourage everyone else to do so as well.  But that's the same thing with any computer-related purchase.  You need to find a store that you can trust and that can serve your needs.  In my case, I need them to do the legwork for me.

3. I have never had any trouble returning goods that I purchased on the basis that they did not work with linux.  They just looked at me blankly and continued to fill in the paperwork.  Often times, this approach is far easier than printing out the list of compatible hardware and fumbling with papers looking for the chipset serial numbers, all the while, trying to pry open the box (without ripping it) so that you can see the chipset on the device, looking nervously over your shoulder in case someone thinks you are wierd or trying to shoplift.


> **tturrisi said:**
> 
k2pow  is a smart consumer, he is doing his research by asking questions here.  That's what this forum is all about!



I have nothing against doing research.  I just don't think we always need to do that anymore.

---

