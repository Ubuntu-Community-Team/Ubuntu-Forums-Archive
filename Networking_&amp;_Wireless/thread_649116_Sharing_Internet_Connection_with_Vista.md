---
title: "Sharing Internet Connection with Vista"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by sabresong on 2007-12-24
Hi.

I'm running Kubuntu on an AMD64 machine, and I need to share my internet connection with my wife's computer, which is running Vista.  I've searched the forums and Google, but none of the suggestions I've found seem to work.  I've followed the instructions at [www.openfree.org/forums/forumdisplayphp?f=73](www.openfree.org/forums/forumdisplayphp?f=73), which are apparently copied from a post in these forums.  I've installed and reconfigured dhcp and uninstalled it again at least three times.  At best my Kubutnu machine can connect but the Vista machine can't.  At worst, neither machine connects.

Each machine has both wireless and ethernet cards.  I'm trying to share the connection via wireless.  I'm not using a router, because we've had really bad luck with routers --- three in the past two years, and the most recent died after only five months.

I'm not really sure what other information might be needed, but I'd be happy to provide anything that might help someone help me figure this out.

---

### Post by mellowd on 2007-12-24
How is your linux box connected? i.e. do you have the wired cable into your linux box, then trying to share that connection via wireless or another way? It's 100 times easier to just get a decent wireless router.

---

### Post by sabresong on 2007-12-24
The Linux box is wired directly to the cable modem.  And I realize it's easier to buy another router, but I've spent close to $200 on routers in the past 2 years, and can't justify spending more on this, so I thought I'd try it without the router.

---

### Post by mellowd on 2007-12-24
I haven't done this myself yet, but I plan it doing it eventually for a laptop I'll buy soon. I'm going to do a bit of research but it's going to have to wait until after Christmas. Sorry I couldn't help sooner :/

---

### Post by sabresong on 2007-12-24
> **mellowd said:**
> I haven't done this myself yet, but I plan it doing it eventually for a laptop I'll buy soon. I'm going to do a bit of research but it's going to have to wait until after Christmas. Sorry I couldn't help sooner :/

Thank you for that.  I hope your research is more fruitful than mine has been.

---

### Post by mellowd on 2007-12-24
> **sabresong said:**
> Thank you for that.  I hope your research is more fruitful than mine has been.

I've heard it possible. You're essentially turning the server into a wireless access point. I'll post any results I get

---

### Post by sabresong on 2007-12-25
> **mellowd said:**
> I've heard it possible. You're essentially turning the server into a wireless access point. I'll post any results I get

Cool.  I'll do the same.  Hopefully one or both of us will figure this out.

---

### Post by mellowd on 2007-12-27
I've found this out so far:

[http://www.linux.com/articles/55617](http://www.linux.com/articles/55617)

This is getting it working on Debian, so I expect it to be similar to doing it on Ubuntu.

The most important part is getting a wireless card that can act as an AP, not all of them can. Unfortunately I cannot try this yet as I don't have a wireless card to use (Also, I don't need it until about 2 months time)

---

### Post by mips on 2007-12-27
> **mellowd said:**
> 
The most important part is getting a wireless card that can act as an AP, not all of them can

I actually think it is possible without turning the wireless card into a AP. I've been meaning to try this for the last 3 weeks but never got around to it.

Edit:
To turn a wireless card into an AP you need to put it into Master mode which is not the same as Ad Hoc mode.

---

### Post by mellowd on 2007-12-28
> **mips said:**
> I actually think it is possible without turning the wireless card into a AP. I've been meaning to try this for the last 3 weeks but never got around to it.

Edit:
To turn a wireless card into an AP you need to put it into Master mode which is not the same as Ad Hoc mode.

As far as I'm aware, not every card out there can go into master mode (I may be wrong, I did this before in XP about 3 years ago and I remember you had to have the correct card to work)

---

### Post by mips on 2007-12-28
> **mellowd said:**
> As far as I'm aware, not every card out there can go into master mode (I may be wrong, I did this before in XP about 3 years ago and I remember you had to have the correct card to work)

Very true. The other option is using Ad-Hoc mode but then again not alll cards supports this either by the looks of things.

I'm currently battling with my rt2500 using the rt2x00 drivers trying to get it into master or ad-hoc mode which is supported by the driver.

---

### Post by mellowd on 2007-12-28
Do me a favour, if you manage to get it working let me know which card you used :)

---

### Post by mips on 2007-12-28
> **mellowd said:**
> Do me a favour, if you manage to get it working let me know which card you used :)

Sure thing but it will be a while though. Leaving for the Berg tomorrow and will only be back next week some time.

I have 3 cards, rt2500(PC), ipw2200 & prism2 (Laptop) so thic should be fun.

---

### Post by mellowd on 2007-12-28
> **mips said:**
> Sure thing but it will be a while though. Leaving for the Berg tomorrow and will only be back next week some time.

I have 3 cards, rt2500(PC), ipw2200 & prism2 (Laptop) so thic should be fun.

No problem, I'm only planning to do this when I get a new laptop. And currently thats only going to be in about 4 months.

---

### Post by sabresong on 2008-01-15
I'm not getting anywhere with this.  I tried the link given previously, but all that did was lose me all connectivity.  Had to work my way back to the beginning just to get back here.

The good news ... the wife has given up Vista.  She's made the switch to Kubuntu.

Now, how to get these two desktop computers communicating and sharing an internet connection using the wireless cards?  Both computers have wired and wireless capabilities, but we need to use the wireless to network and share the Internet connection that's wired to my machine.

Suggestions?  Anyone?

---

### Post by mips on 2008-01-15
Lol, I still have not gotton round to this. I wiped my desktop & laptop to install arch. My laptop is done and I'm busy with the install on my desktop as I type this.

So hopefully I will look into this real soon as I really need to get my laptop working from anywhere in the house.

What wireless chipsets are you using on the two computers?

---

### Post by sabresong on 2008-01-18
The wireless that we're using is Ralink vendor specific, according to the Kubuntu Device Database.  The machines are HP Slimline s3100n AMD64.

---

### Post by mips on 2008-01-18
> **sabresong said:**
> The wireless that we're using is Ralink vendor specific, according to the Kubuntu Device Database.  The machines are HP Slimline s3100n AMD64.

I also have a Ralink rt2500. Problem is the old drivers rt2500 are legacy drivers now and the new rt2x00 drivers are not in the kernel yet. They will be incorporated in 2.6.24 which is currently at rc8 and according to Linus 2.6.24 will probably be out next weekend.

I have not quite figured out whether the rt2x00 drivers support master & ad-hoc mode as from all accounts I heard that was disabled for now because it does not work so well and they are consentrating on more important stuff first.

I will keep looking into this and hopefully come up with a solution.

---

### Post by mellowd on 2008-01-20
Sorry guys I've been away studying. I haven't had time to even begin focusing on this. As I was only going to start doing this when I got around to getting a new laptop, and this hasn't happened yet, I wno't be for a while still. Sorry I couldn't be of more immidiate help.

---

### Post by sabresong on 2008-01-20
Ok ...  I've found that the wireless interface is a RaLink 2501 (RT73).  I also found the drivers and firmware here ... [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

I tried to follow the directions provided, but I'm not all that knowledgeable when it comes to compiling from source, and these are the most confusing instructions I've followed to date.  But I tried, then decided to take a break when I realized I was in over my head.  I shall wait for wiser heads to take this one on.

---

### Post by mips on 2008-01-21
Those drivers listed are old legacy drivers and are being replaced by the rt2x00 driver.

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

---

