---
title: "Does Ati fglrx work in 9.04?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-27
Does anybody have fglrx working in 9.04 with any cards? Is this a severe 9.04 bug or is it just because I have an bit older card that is no longer supported and considered a "legacy" card now. If I get a 4850 will I be able to install the fglrx with "hardware drivers" under "system" and "administration"?

---

### Post by Xenomorph05 on 2009-04-27
I have an ATI HD 3850 and I had to install the fglrx for it to work normally. I am using 9.04 and it seems to be working just fine but I can't seem to get my HDMI audio working. I don't know if that a driver issue or not though.

---

### Post by teamkiller87 on 2009-04-27
I have an X1600 and from what I've read ATI has dropped the support for it along with other cards from that time period. I did install fglrx but it didn't take me far. I couldn't even get an X session started, so I gave up.

---

### Post by Didius Falco on 2009-04-27
It may be because your card had support dropped by ATI - hard to say, since you didn't include what card you have in your post, though.

More information is the best bet for getting help.

I'm using the ATI fglrx driver under 9.04 with an  ATI Radeon 4870, and it rocks. A 4850 should work well too.

---

### Post by Trebaruna on 2009-04-27
If AMD have stopped supporting your card then their driver will not support your card. Unfortunately, because it is a closed source driver, there's nothing Ubuntu's developers can do about this.
However, older cards should work with the open source drivers that also come with Ubuntu. If they do not, perhaps you need to yell at AMD to release more documentation.

Buying a new card will solve the problem, if indeed your card will not work. Only you can decide whether such a purchase is worth it.

---

### Post by kellemes on 2009-04-27
> **teamkiller87 said:**
> I have an X1600 and from what I've read AMD has dropped the support for it along with other cards from that time period. I did install fglrx but it didn't take me far. I couldn't even get an X session started, so I gave up.

Having a X1650 I gave up on fglrx some time ago..
I'm going open-source all the way, not issues, no worries..
Next card will be "NO ATI" for sure, AMD doesn't seem to be interested/able in creating a high grade linux driver for there products.

---

### Post by Duskao on 2009-04-27
Awesome. That is exactly what I wanted to hear. I have a Radeon X1950 and I have been having one heck of a time with it. I even tried to manually install the 9.3 fglrx drivers for it in 9.04 but with no avail. I'm really glad to hear that the 4870 is working so well, in fact I would totally buy it instead of the 4850 because there is a wicked sale on them near where I live, but I would need to pick up a new power supply to go with it so I'm settling for the 4850, now I just have to decide for the 512 or the 1 gig versions. Only 20 bucks difference. Gonna stick with Ati cause of the long term support that is going to happen once they release the drivers open source. Plus they keep improving the drivers steadily that I'm sure they will be fairly close to the windows drivers (which despite what some people say are quite good) soon.

---

### Post by teamkiller87 on 2009-04-27
> **kellemes said:**
> Next card will be "NO ATI" for sure, AMD doesn't seem to be interested/able in creating a high grade linux driver for there products.

Tell me about it... I knew from the moment I bought my laptop that I'd regret the ATI video card but for that particular sum of money, at that time, it was a better option than NVidia... IN WINDOWS. But, never again.

---

### Post by Duskao on 2009-04-28
This is just a heads up to the guys that aren't overly happy with their Ati support, I completely feel your pain, but you gotta do some more research. Since AMD bought out Ati they certainly had their work cut out for them with getting any linux support out there, and its finally starting to show. But the problem at this point in time is that so many of us with a wee bit dated cards have just been dropped out of the support list just when the drivers are starting to get better. In the last 6 months or so the Ati drivers have come a long way from where they were, but they are almost at par now with nvidia, and soon the Ati drivers will overtake the nvidia ones, not necessarily because of Ati so much as all the wicked awesome linux enthusiasts out there that will work their butts off making the absolute best drivers available once Ati releases their official drivers to the open source community. But please don't in any way get me wrong, nvidia at this point in time is likely the way to go. I have heard and read very few bad things about the nvidia cards and drivers with linux except for the 2D display lagging behind a bit. On the other hand I have heard and read very little (recent) bad news about the newer Ati cards and drivers, except for anything at and under the x1xxx cards being dropped from support. Just my two cents.

---

