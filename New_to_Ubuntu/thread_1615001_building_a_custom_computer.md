---
title: "building a custom computer"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-11-06
this is my first computer build  and i think this would be the place to post it 

i aiming for a gaming pc that i wont have to upgrade for a while  so far i have the case  that has seven drive ports and i wanted to have a couple of TB of memory to play with.

i need help with picking the motherboard cpu and other specs for the pc those i have the most trouble with.

any ideas or suggestions?

---

### Post by Windows Nerd on 2010-11-06
You're going to be a bit more specific: what case have you got?

If this is a gaming computer that you won't need to upgrade for a while, you may be spending a bit more than the average consumer on a computer. You have been warned.

Just wondering if you plan to over-clock at all, as this influences many decisions for hardware. Are you planning to go AMD or Intel? 

Graphic card: For a gaming computer, the graphics card is an important consideration. For gaming on Linux, you want an Nvidia GPU, for sure, as the ATi (now being re-branded as AMD) drivers for Linux just suck at the moment, and don't support most newer cards.

If you plan on running Windows to game, you will have to consider if you want an ATi graphics card or an Nvidia. Both run just fine on Windows, and ATi has slightly better hardware, and suck less power and generate less heat. 

Note that if you really want to splurge and get a multi-gpu configuration, let me know. But the performance to price ration of such a configuration is not as great. 

Hard drives: you want a few terabytes of storage to play with. There are 2 tb drives on the market for around $150. However, some reviews on newegg have been claiming that some of these larger drives are not as reliable as the 1 TB ones. If you wish (and know how to), you could just RAID two 1TB drives for almost the same price and improved performance. 

CPU: Can't really advise much on this just yet because you haven't specified if you want an AMD-based system or an Intel-based system. 

Motherboard: Since the choice of motherboard relies heavily on you choice of CPU, and whether you wish to overclock or not, I cannot advise much on this yet either.

RAM: How much do you want? 4 GB of 1330 or 1600 MHz RAM is fine for most gaming applications. However, if you also plan to do some video/photo editing, you may want a larger amount of RAM. The choice of RAM is somewhat dependent on your motherboard/cpu choice: Intel boards support triple-channel ram, AMD boards only have dual channel as of yet. Make sure to get a good name-brand ram, such as Corsair, G-skill, Patriot, etc (they are somewhat more reliable than their generic OEM counterparts, but also a bit more expensive.

Cooling: Unless you overclock, stock coolers are fine.

Optical drives: Unless you really need it and want to spend a bit on it, a generic DVD combo drive is fine. If you want to spend your money, a blu-ray drive may be needed. But chances are, not so much.


That should be it. If you have any other requirements out of your computer, let me know.

Scott

---

### Post by pyrofreak99 on 2010-11-06
i am going to go amd  for the most part (sorry i wasn't very specific)  the case i have  i cant really remember what its called  but it has like seven drive ports  and i also forgot to mention that it has to be budget  and it dont have to be top of the line just as long as i can play most games and be able to upgrade later. i would like to overclock as well that would be a good thing to do.  (man i fogot to mention alot of things)

---

### Post by arrimapirate on 2010-11-06
Try newegg.com they have a great selection of computer parts. 

Pick out the mobo/processor first. The mobo will decide what type of case you need such as ATX or microATX.

The ram comes next. If your Motherboard supports tri-channel memory, you want your ram in multiples of 3 like 3gb 6g or 9gb. Dual-channel should be in  2s like 2gb 4gb 6gb. 

Then the graphics card (I recommend ATI. They tend to be a few hundred dollars cheaper than Nvida and run faster) The PSU you get is mostly based off the power consumption of of your graphics card. An ATI card will make use of a lower power PSU and can use a cheaper one. Nvida cards will need a more expensive and powerful PSU.

Hard drive, cd drive, and any other parts like that would come last. 

Just to brag a little here are the specs on my home build:
CPU: Intel Core i7 920
Mobo: Foxconn FlamingBlade GTI
Graphics: Ati Raedon 4890
Hdd: 1tb Western Digital
Ram: 6gb Pqi

---

### Post by oldfred on 2010-11-06
Before a build I like to go to review sites. They may not always discuss if components are linux compatible but usually they are. I particularly like the discussion of alternatives and then like to see the differences they have in different price points. 

[http://arstechnica.com/gadgets/guides/2010/09/the-ars-system-guide-september-2010-edition.ars](http://arstechnica.com/gadgets/guides/2010/09/the-ars-system-guide-september-2010-edition.ars)
[http://www.tomshardware.com/system-configuration-recommendation-51.html](http://www.tomshardware.com/system-configuration-recommendation-51.html)
I like the last page with the table comparing all cards
[http://www.tomshardware.com/reviews/gaming-graphics-radeon-hd-6870-radeon-hd-6850,2782.html](http://www.tomshardware.com/reviews/gaming-graphics-radeon-hd-6870-radeon-hd-6850,2782.html)

---

### Post by djyoung4 on 2010-11-06
making sure that stuff works with Linux is probably one of the higher concerns.  I just finished my first build and its a HTPC.  Got all the parts for under a grand and putting it together is fairly easy.  You can always add harddrives as you go.  I personally got one of the WD caviar black 2tb drives and its worked awesome so far but I have added a few 1 tb's as my movie and music collection has expanded.  I would just read heavily and ask questions about compatibility and if budget is a concern then definitely use newegg.

---

### Post by Windows Nerd on 2010-11-11
> **arrimapirate said:**
> Try newegg.com they have a great selection of computer parts. 

Pick out the mobo/processor first. The mobo will decide what type of case you need such as ATX or microATX.

The ram comes next. If your Motherboard supports tri-channel memory, you want your ram in multiples of 3 like 3gb 6g or 9gb. Dual-channel should be in  2s like 2gb 4gb 6gb. 

Then the graphics card (I recommend ATI. They tend to be a few hundred dollars cheaper than Nvida and run faster) The PSU you get is mostly based off the power consumption of of your graphics card. An ATI card will make use of a lower power PSU and can use a cheaper one. Nvida cards will need a more expensive and powerful PSU.

Hard drive, cd drive, and any other parts like that would come last. 

Just to brag a little here are the specs on my home build:
CPU: Intel Core i7 920
Mobo: Foxconn FlamingBlade GTI
Graphics: Ati Raedon 4890
Hdd: 1tb Western Digital
Ram: 6gb Pqi

May I just point out that ATi Graphics cards do not run very well at all with games on Linux, and their drivers for Linux are not written very well at all. If you intend to do any gaming in Linux that requires 3D capability, it is _much_ easier to use an nvidia card, and you get much better Linux compatibility.

If you are going to be doing your gaming under Windows, then go ATi: the ATi cards run just perfectly fine for normal desktop use under Linux (I am using one right now, as a matter a fact), and then you can just reboot into Windows when you want to do some more serious gaming. ATi cards are built better, generate less heat and consume less power (in general, however the most recent GTX580 GPU that nvidia _just_ released solves most all of the heat and power problems that plagued the generation of cards before it.

You should consider this before you choose your graphics card, especially if you plan on getting a more spendy higher-end card.

Scott

---

