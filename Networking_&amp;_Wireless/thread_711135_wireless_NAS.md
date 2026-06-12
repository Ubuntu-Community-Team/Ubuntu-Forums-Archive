---
title: "wireless NAS"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by insane_alien on 2008-02-29
hey guys, recently, my existing NAS(an old box stuffed full of HDD's and a wirelesscard went down for good(data is fine) and i need a new one. i'm not sure whether the best option would be to construct a new box or buy a premade solution. 

i'm looking for one with wireless g capability and enough space for at least 4 drives but the more the merrier. if it can be bought without any existing drives that would be a bonus too because i'd just be replacing them with my current drives.

something reasonably cheap would be good too.

does anybody know if something like this exists?the only ones i have been able to find are enterprise level solutions and quite costly.

---

### Post by mrsteveman1 on 2008-02-29
4 drives + wireless is pretty specific. The stuff available in stores is typically either a single drive sealed device, or a real raid NAS (like infrant etc).

Your best bet may be to go the mATX route and buy a processor+motherboard+case etc.

There are some nice mATX cases out there but i haven't yet found a nice small one with space for 4 drives.

---

### Post by insane_alien on 2008-02-29
right, so its a build it myself job. 

i was hoping there would be something like the drobo but wireless and without all the fanciness as its going to be sitting in my cupboard. damn.

---

### Post by mrsteveman1 on 2008-02-29
[Drobo can be networked]("http://www.drobo.com/products_droboshare.aspx") but apparently not wireless. Thats at least partway there, you can always connect the drobo directly to your wireless router.

They make a little module that sits under it and provides access to the drobos drives over the network. If thats the sort of thing you want, ease of use, small footprint, real redundancy with raid etc, this is the way to go.

---

### Post by VorDesigns on 2008-02-29
Having worked with wireless devices and their idiosyncracies for years, my suggestion would be to buy something wired and plug it into a LAN port on your wireless router.
Consider Thecus from somewhere like [PC Mall Thecus search]("http://www.pcmall.com/pcmall/search/search.asp?search=thecus&NavID_Search=false&CurDSN=simple&calledfrom=1&incimage=on").

---

### Post by insane_alien on 2008-02-29
i'd really rather have wireless. it was working well. my routers LAN ports are already full and i don't want to buy another switch besides, its already pretty crowded near it. 

i think i'll just build my own. i'll get what i want and it'll be cheaper.

---

### Post by jcostom on 2008-02-29
> **mrsteveman1 said:**
> [Drobo can be networked]("http://www.drobo.com/products_droboshare.aspx") but apparently not wireless. Thats at least partway there, you can always connect the drobo directly to your wireless router..

The drobo, while neato and all, is wildly expensive.  $499 for the drobo, plus another $199 for the nas add-on.  And remember gang, that's without drives.  So, for $700, you've got 0 MB of NAS storage...

I think the build is the better option for now...  One possible option for you might be to use one of the Asus routers, like this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320008](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320008)

load up openwrt kamikaze, and the kmod-usb2, kmod-usb-storage, samba, etc. packages and doing a NAS that way.  I did one of those for a friend so he could do Time Machine backups over the network (using iTimeMachine to enable network disks), and it works well.  Of course, the initial backup was done over the wire, but the subsequent ones work well wirelessly.

For giggles, I put together a Linux PC build to do the job.  The stuff I put in there is attached.  It's missing 2 things:

1. RAID controller - use what feels best to you.  A friend recently scored a nice 4-channel 3ware board on eBay for $45.  Keep your eyes peeled and you'll likely scoop up an 8-channel board for something in the $100 neighborhood.

2. Drives.  Add what you need.

I built that machine with a NAS in mind - lots of space in the case for drives, not much cpu demand since you'll (hopefully) use a real raid card.  If you're going to do software raid, get a better CPU, and probably a better cooling rig..

---

### Post by mrsteveman1 on 2008-02-29
Drobo is expensive because it has hot swap ATA hardware and does real RAID. I still wouldn't buy one though.

If i were building a new file server right now, id get an mATX mainboard, a 3ware raid card, and perhaps one of 3wares drive cages too. 

I wouldn't buy one of those so called "network hard drives" maxtor etc make, they aren't worth the cost of the parts they are made of and can't be trusted. 

USB ports on wireless routers are ok but only if you just want to access your stuff once in a while, for real fileserver use they aren't enough and likely aren't very reliable.

---

### Post by insane_alien on 2008-03-01
i'm starting construction. i have a RAID card and i have a lot of bits(RAID card, wireless card, case, fans).

the computer jcostom posted is way overkill for my needs. a 96MB PIII 500MHz was more than adequate for my needs.

i just wanted to know if it would be worth buying a NAS box. and its obviously not as i've had no luck finding anything that fits my needs but doesn't cost an arm, leg and a bollock.

---

### Post by jcostom on 2008-03-04
> **insane_alien said:**
> i'm starting construction. i have a RAID card and i have a lot of bits(RAID card, wireless card, case, fans).

the computer jcostom posted is way overkill for my needs. a 96MB PIII 500MHz was more than adequate for my needs.

i just wanted to know if it would be worth buying a NAS box. and its obviously not as i've had no luck finding anything that fits my needs but doesn't cost an arm, leg and a bollock.

Well, in fairness, you can't buy a P-III 500 without looking to secondary markets. :)

You could surely get the costs down a bit more by going with a lower-end AMD CPU, or having a case & power supply you can use for the project..  Admittedly, I picked an expensive case, but hey, I'm a case snob. :)  Personally, I see value in a high-quality case made with good materials..  I revised a bit to go lower end, and shaved $70 off..  Take off another $150 if you've got a case & power supply to use...

---

### Post by mrsteveman1 on 2008-03-04
The server i use here is an AMD x64 3200+ single core proc, cost me $48. The motherboard is from Abit, it was $59. The ram i got for free from a friend, but otherwise it would have cost somewhere around $50. The drive i already had, but it was $79 when i got it a year ago.

Its pretty easy to get good hardware for stuff like this right now, especially the older AMD chips, which are very very good chips.

---

