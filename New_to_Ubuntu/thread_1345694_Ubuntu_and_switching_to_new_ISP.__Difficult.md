---
title: "Ubuntu and switching to new ISP.  Difficult?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by whitefort on 2009-12-04
Hi.

Today I had a letter from my ISP telling me that I can:
 a) accept some phone services (which I really, REALLY don't want) and keep paying them the same monthly price, or
b) Just continue with Broadband only, but with a 25% price increase.

(this is because my ISP has been bought by another company - I've had trouble with this company in the past and I don't want them anywhere NEAR my phone lines.

Anyway, I've asked for my MAC code, and I'm ISP shopping... hence my question.

When I first got broadband, I recall that I had to run some startup software to get things up and running.  And it was Windows/Mac only software.  Back then I had a windows PC, so it wasn't an issue.

Now I'm Ubuntu only - so my question:

If I switch ISPs, am I going to have problems getting connected without a Windows computer?  I know it can be done (obviously!) but I don't know if ***I'M ***capable of doing it, if it requires lots of Linux know-how.  Especially as I wouldn't be able to Google for help without an internet connection.

Would I be safer to just grit my teeth and pay the 25% price hike?  I've never switched ISPs before, but I keep hearing horror stories, and I'm scared!

Help!?

(oh, if it matters, I'm in the UK)

---

### Post by lotharmat on 2009-12-04
It should be relatively straight-forward.

Once you get your new provider; you should just have to change some details in the ADSL Modem/router (usually just login/authentication details). The modem/router should then detect a new network on the end of the phone line and authenticate accordingly and route your stuff to the right places


(Stuff - Because I couldn't think of the correct term)

Oh - I'm assuming you are using a generic ADSL modem/router like Netgear or the like

---

### Post by coffeecat on 2009-12-04
> **whitefort said:**
> (oh, if it matters, I'm in the UK)

Gathered that from the 'Location: N Ireland' under your name. :wink:

Do you have your own modem-router? If so, it's a simple matter of going into the web interface of the router and re-configuring it with the username and password that your new ISP will give you. The username looks vaguely like an email address of the [EMAIL="somethingorother@somethingelse.co.uk"]somethingorother@somethingelse.co.uk[/EMAIL] variety. Check also the VPI and VCI values are correct, although every connection I've helped set up for friends with a variety of ISPs have had 0 and 38 respectively.

Most of the UK uses PPPoA (under encapsulation) but I noticed that AOL was using PPPoE. Trust AOL to be different. :roll:

That Windows/Mac only software business is to do with the allegedly easy setup wizards that come with most (all) routers. Believe me, it's easier in the long run simply logging into the web interface with Firefox and doing it that way - the OS you are running is then irrelevant.

To help you further - what ISP are you fleeing? What ISPs were you thinking of looking at? What is the make/model of your modem/router? Also, while ISP shopping, you'll see that some are now offering 'free' modem-routers - often wireless. These are often pre-configured for you.

A useful information resource for you:

[http://www.thinkbroadband.com/](http://www.thinkbroadband.com/)

---

### Post by whitefort on 2009-12-04
Thanks, guys - this is all very reassuring.

So I can just do the usual browser [http://192.168.0.1](http://192.168.0.1) into my router settings, change username and password, and I'll probably be OK?  That's a huge relief.  Even*** I ***should be able to manage that.

Coffeecat, I'm fleeing Tiscali/TalkTalk.  I know they get a shocking rep, but I have to say I've had very few problems with Tiscali, and they really don't seem to have any download limits, or I would have hit them more than once.

To be honest, I'm HALF tempted to pay the price increase and stick with them - especially as even with the increase they'll still be cheaper than most others.

Also (to be even more honest), there's always that feeling that the devil you know might be better than the devil you don't.  And I haven't a clue where else to look yet. 

My wife is putting me under serious pressure to sign up with BT (simply because it's a name she recognises and 'trusts', but I REALLY went off BT during that whole Phorm thing.)

My router is a Netgear.  I was recently given a Linksys, but it's still in the box, unused.

I'll do some comparisons on Thinkbroadband - thanks for that link!

---

### Post by ukripper on 2009-12-04
Accept AOL i guess you shouldn't have much problem with other ISPs except few bandwidth problems. AOL are pain in the ars*! in london so far i think cable broadband supplied by virgin seems to be good all others just lie for fast internet connections. however sadly, i am on BT broadband coz my mum is using btinternet.com email address for her business emails so can't change until i move her to my own domain soon. BT sucks though when comes to download/upload speeds.

---

### Post by coffeecat on 2009-12-04
> **whitefort said:**
> Coffeecat, I'm fleeing Tiscali/TalkTalk.

I thought as much. :) Good move. Is that Tiscali for BB and TalkTalk for phone? Because I thought TalkTalk was owned by AOhelL and therefore a different company. Whatever - my rule of thumb when advising others is avoid AOL, Tiscali, and BT. BT are OK, so I hear, until you have to call customer-unservice which is when you wish you had gone with someone else - allegedly. :wink: Also - take care to avoid the subsidiaries of AOL and Tiscali - there are quite a few. Pipex for example - owned by Tiscali.


> **whitefort said:**
> they'll still be cheaper than most others.

Old adage: you get what you pay for.


> **whitefort said:**
>   And I haven't a clue where else to look yet. 

Start with the compare broadband page on that link I gave you. Tick up to six providers and look at the bar charts. It's quite an eye opener. Try AOL, BT, NewNet, O2, Tiscali, Zen. I bet that surprised you. :) Now try some more and price out the ones with the good scores.

---

