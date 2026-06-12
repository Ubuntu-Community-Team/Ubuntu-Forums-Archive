---
title: "Looking for Video Card Reccommendations....."
date: 2009-04-02
forum: New to Ubuntu
---

### Post by suomalainen on 2009-04-02
Ubunteros,

I'd like to request information and recommendations on video cards. I know I need one that has 2 DVI-D (Dual link) ports. I attached a pic of what the connector on the monitor looks like. I have the HP 1907w.

I do not do any gaming. However, I do watch steaming videos and news sites and watch DVD's.

I would also like to get the cube plugin so I can use compiz.

I also attached a pic of the DVI-D (single Link) cable that I already have. Will this work in conjunction with the monitor and card or do I need a new cable?

Finally, I would like to have a plug and play video card that would work out of the box with 8.04LTS....

Any references or success stories welcome!!!

---

### Post by skymera on 2009-04-02
Any new graphics card comes with two DVI ports :)

An Nvidia or ATi graphics card will do. Note: Nvidia has slightly better support for Linux than ATi currently.

An Nvidia 9600GT would be plentiful powerful for Compiz and some great games like Sauerbraten :)

---

### Post by suomalainen on 2009-04-02
Thanks Skymera! Is compiz a hog on the ram? I got 4GB right now.

---

### Post by Therion on 2009-04-02
Your RAM config is fine.  

How much do you want to spend (or not spend) on this video card?

---

### Post by suomalainen on 2009-04-02
Therion, I think that will be dictated by what I'm doing now. I'm not into gaming so I don't have that requirement. But I do watch the news and DVD's.

I'd also like to learn more about compiz.

---

### Post by Therion on 2009-04-02
> **suomalainen said:**
> Therion, I think that will be dictated by what I'm doing now. I'm not into gaming so I don't have that requirement. But I do watch the news and DVD's.
Okay... But I can't really recommend a card unless I have some idea of what your budget is.  Are we talking >$100 or what?

> **suomalainen said:**
> I'd also like to learn more about compiz.
Okay... What would you like to know?

Somewhere to start:  [http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

---

### Post by suomalainen on 2009-04-02
Thanks for the url Therion! Regarding price it seems to me that the higher the price the more you can do. But I don't necessarily do that much.....

Anyway I guess we can hoover aroud $1oo. Is that ok?

---

### Post by Hospadar on 2009-04-02
Take a look in the community docs in my sig, I think they have pages on different video cards and how well they work. also just googling "<the name of the card you are thinking about> in ubuntu" will usually turn up helpful results.

I agree that nvidia is probably a little more strongly supported, but in recent times, I've not had any major ati issues.  I put ubuntu on a laptop with an ati card and had no trouble getting 3d working.  Since I've only noticed maybe one issue with it (google earth has a wierd flashing situation).

Also, I might reccomend you look into an ati card with good reviews, because nvidia drivers replace a large portion of the video software stack with their own software, making some generic configuration tools not work (although nvidia provides an excellent config tool of their own, "nvidia-settings").

I think with a newer card from either manufacturer, you'd be pretty happy.

---

### Post by suomalainen on 2009-04-02
Thanks for the link and insight Hospadar!

---

### Post by Therion on 2009-04-02
> **suomalainen said:**
> Thanks for the url Therion! Regarding price it seems to me that the higher the price the more you can do. But I don't necessarily do that much.....

Anyway I guess we can hoover aroud $1oo. Is that ok?
For what you want to do $100 is *overkill*.  For $50 (after a $5 rebate) and free shipping this is pretty decent:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130394](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130394)

Not top of the line, mind you, but for $50 it's a lot of card.  It'll certainly crush Compiz and render your NY Times online with alacrity.  This all assumes you have a PCI-e slot though.  That's something we haven't covered come to think of it: Your interface.  If your PC isn't ancient you should have a PCI-e slot.  We'll need to confirm that though.

---

### Post by suomalainen on 2009-04-02
Therion,

Thanks for the prompt support.

I opened my box up just to be sure I have the required slots open. As you can see from the attached pic I have one still open.

I read the feedback on this card that you provided and the question about power supply came up. since I had my box open I took a pic of that too.

Now I wonder that I may not have enough juice?????

Do you also think I need new cables???

Thanks again!!!

---

### Post by Therion on 2009-04-02
> **suomalainen said:**
> Therion,

Thanks for the prompt support.
You're welcome.  Please feel free to demonstrate your gratitude by dropping off suitcases full of small, non-sequential, unnmarked bills.  Come alone.  Details to follow via PM.   

> **suomalainen said:**
> I opened my box up just to be sure I have the required slots open. As you can see from the attached pic I have one still open.
Yep, you're good to go!

> **suomalainen said:**
> I read the feedback on this card that you provided and the question about power supply came up. since I had my box open I took a pic of that too.

Now I wonder that I may not have enough juice?????
You have a 450W power supply that puts out 24 amps on the +12v rail.  You're golden.

> **suomalainen said:**
> Do you also think I need new cables???
Do you WANT new cables?  

Sometimes I want new cables and I just go out and buy them for the thrill of it.  So, yeah...  If you think you need new cables, you probably do.  Your new video card will draw juice from the PCI-e socket and and an existing six-pin connector off your current PSU (or maybe a four-pin molex, who knows these days, that's part of the excitement).

---

### Post by suomalainen on 2009-04-02
Therion,

Do you think heating will be an issue with this card? I found a review on the same site you quoted which stated:

Cons: Heats up pretty good... Nothing an EVGA precision software download can't fix which let's you adjust the fan speed to keep it cooler. As well make sure you case has decent airflow and your Good to go!

Will Ubuntu allow me to control fan speed?

This card has 256 MB. What am I losing by not using a 512 card? I guess to re-word this statement I could say "how close am I in doing other things I may be interested in, if I were to go the 512 route?"

As per my cable question. the cable pic I posted have never been used so I was wondering if they would work in this application. I believe they will....

Once the cube plugin and compviz are installed how drastically will they draw on the graphics card....?????

I guess I'm asking what I can expect it to do and what it cannot do????
Setting expectations I think you can say......

Take your time getting back and Thanks for the advice thus far!!!

---

### Post by Therion on 2009-04-02
> **suomalainen said:**
> 
Do you think heating will be an issue with this card?
Impossible to say.  I'm sure if you look around enough you'll find someone who has had a problem with just about any piece of hardware you could find.  Relax.  One person mentioning the card gets warm is no reason to panic.  

> **suomalainen said:**
> Will Ubuntu allow me to control fan speed?
Deep breathes.  Don't Panic.

> **suomalainen said:**
> What am I losing by not using a 512 card? I guess to re-word this statement I could say "how close am I in doing other things I may be interested in, if I were to go the 512 route?"
You're losing some memory you were probably never using.  Are you playing Crysis?  BioShock?  No... You want to spin the Desktop Cube in Compiz, watch YouTube videos and read your Times online.  If you want 512MB of memory I can find you a card that has it.  But bear in mind more is not always better.  256MB is good deal of dedicated memory for a video card and it's pretty quick RAM at that (DDR3). It's also a $50 solution.  If you WANT to spend twice as much I can get you into a "sporty" model, sure, no problem there.  I don't know what other things you might be interested in, but reviewers report playing BioShock and Crysis with full eye-candy turned on.  That takes some muscle.  You've got room to expand with this card.

> **suomalainen said:**
> As per my cable question. the cable pic I posted have never been used so I was wondering if they would work in this application. I believe they will...
Your power supply, I'm quite sure, will have a spare six pin connector hanging around.  If not, you can use a four-pin molex connector that's not being used along with the adapter that comes with the card. 

> **suomalainen said:**
> Once the cube plugin and compviz are installed how drastically will they draw on the graphics card....?????
With this video card you won't have aaany problems running Compiz.  Other than that, I really can't say.  Compiz WILL put a hit on your video memory, but seriously, this card can handle it.  Compiz is not that big a drain on your systems resources.

> **suomalainen said:**
> I guess I'm asking what I can expect it to do and what it cannot do????
Setting expectations I think you can say......

Take your time getting back and Thanks for the advice thus far!!!
Deeeeep breathes... Believe me.  This card has plenty of muscle to get you through what you tell me you want to do and then some. As I've already pointed out, reviewers are reporting playing Crysis and BioShock with all the eye-candy turned on using this card.  Take a look at some trailers for those games and see what they look like and decide for yourself.

Then too, don't do anything you're not comfortable with.  Take your time, do your own research, get some other opinions.  This is one good card out of several that are available.  I was trying to hit a "sweet spot" between price and performance and while there might be better solutions out there, this is still a very, very good solution nonetheless.  Any way you slice it, that's a _LOT_ of video card for fifty bucks.

---

### Post by doas777 on 2009-04-02
> **Therion said:**
> 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130394](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130394)


I had an EVGA Geforce 8500 and it was awful with hardy. terrible underscan, half the settings in nvidia-settings and xorg were ignored, etc.

it's very possible that this 8600 is much more compatible, I have no idea.
I replaced the 8500 with an asus 7950GT and I'm much happier.

---

### Post by Therion on 2009-04-03
> **doas777 said:**
> I had an EVGA Geforce 8500 and it was awful with hardy. terrible underscan, half the settings in nvidia-settings and xorg were ignored, etc.

it's very possible that this 8600 is much more compatible, I have no idea.
I replaced the 8500 with an asus 7950GT and I'm much happier.
Well, no offense, but you are talking about an entirely different video card and an entirely release of Ubuntu.

OP really should do some of his own research... Like here for instance:

[http://www.ubuntuhcl.org/browse/search?offset=0&category=6&manufacturer=&os=1&order-by=rating-desc&keywords=](http://www.ubuntuhcl.org/browse/search?offset=0&category=6&manufacturer=&os=1&order-by=rating-desc&keywords=)

Where the [8600 is reviewed by users](http://www.ubuntuhcl.org/browse/product+nvidia-geforce-8600gt?id=756) and given glowing reports.

---

### Post by jlhaslip on 2009-04-03
> **suomalainen said:**
> Once the cube plugin and compviz are installed how drastically will they draw on the graphics card....?????

I'm running Compiz using the onboard video chip and shared RAM on my 2 year old 1.6ghz laptop. Any video card with 256 Meg will outperform the requirements of Compiz, IMHO.

---

### Post by suomalainen on 2009-04-03
Hello All.....

I didn't mention that I wanted to run dual monitors. Does this effect the performance at all???

---

### Post by Therion on 2009-04-03
> **suomalainen said:**
> I didn't mention that I wanted to run dual monitors. Does this effect the performance at all???
What do you mean by "affect performance"?  Do you mean will it use more RAM and/or CPU cycles?  Yeah, probably. Would that difference show up numerically on a synthetic benchmarking application?  Yeah, it probably would. Will you *notice* the difference on a day-to-day useage basis? Probably not.  Then too using dual monitors draws on more than just your video card.  Your CPU, system RAM and GPU (video card) all pull together in a team formation, remember.

Dude (pardon me if I assume)... There's nothing you're going to throw at an 8600 series card that it can't handle running Ubuntu.  Not Compiz, not Compiz on dual-monitors...  That's not enough to get a card like this so much as *warmed up* much less breaking any kind of sweat.  

Further, there's no point in paying for a Ferrari when the only kind of driving you do is going to the corner grocery store for eggs and milk.  You'd never get it out of second gear.  So don't pay $300 for 512MB of VRAM and such you're never going to touch.

---

### Post by suomalainen on 2009-04-03
Therion,

It's good to know Your part mind-reader as you read my thoughts precisely!

As I've mentioned before, I'm not gonna do any gaming. I'm sure, however, that I'll probably install some sort of game just to see how it looks but gaming doesn't occupy my time. I'm not into it.

Instead, I will be using dual monitors to enter data into a spreedsheet while gathering it from a website opened in another monitor.

I'll also be watching live news streams and DVD's from time to time.

Thus, as I have gathered from your review of the card this may even be a tad of an overkill.... But for the dollar value it's a steal and nothing to complain or worry about....

Here are the details of my system:

Motherboard: DQ965GFEKR
CPU: Intel Core 2 Duo E450
G.SKILL 4GB (4 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory


Thanks again for your continued support!!!!

---

### Post by Therion on 2009-04-03
> **suomalainen said:**
> It's good to know Your part mind-reader as you read my thoughts precisely!
It's what they pay me for.

> **suomalainen said:**
> ... I will be using dual monitors to enter data into a spreedsheet while gathering it from a website opened in another monitor.

I'll also be watching live news streams and DVD's from time to time.

Thus, as I have gathered from your review of the card this may even be a tad of an overkill...
Exactly.  

> **suomalainen said:**
> Here are the details of my system:

Motherboard: DQ965GFEKR
CPU: Intel Core 2 Duo E450
G.SKILL 4GB (4 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory
Your specs were a little difficult to look up since I don't think your CPU or motherboard are common 'Stateside.  From what I was able to gather though, you've got a good system going.  And every good system deserves a good video card to match.

> **suomalainen said:**
> Thanks again for your continued support!!!!
My pleasure.  Now go shopping.

---

