---
title: "why is wireless support so poor for ubuntu?"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Griffiss on 2007-03-11
I have an ASUS WL-138G wireless LAN card. Trying to make it work on ubuntu (edgy) has been amazingly difficult (I still haven't succeeded). From looking at the forums it seems to be a common problem. Why is it so hard?

Is it an effect of the non-commercial nature of ubuntu? I can't think why harware manufacturers would resist making their products available to as wide a market as possible - unless perhaps they were being pressurized by some large commercial software company/ies to make their products difficult to use for those with a free OS.

Just a thought really. Other than the massive problems I've been having with wireless, I really like ubuntu.

Griffiss

---

### Post by zorkerz on 2007-03-11
I agree although i have had less problems than most useing wireless it needs help. I think feisty makes big improvements in this area especially with the switch from network monitor to network manager if i am correct.

---

### Post by Mr. C. on 2007-03-11
Without making any judgment on the quality of wireless support for Linux in general, it shouldn't be a stretch to understand that a product produced by a team of (well) paid, dedicated developers (eg. driver writers for Windows/Mac) will likely out pace software being developed by a small number of unpaid developers.  One also has to understand the size of the target audience.  All Unix and Linux stations combined is only a small fraction of the overall Windows market.  Where do you think companies are going to focus their resources?

The concept of open, "free" software is fantastic.  However, like the age-old adage that there is no such thing as a free lunch, this free software you get comes at a price.  That price is fewer man hours of development, testing, marketing, support, etc.  That translates into the user having to pay via time spent working out the kinks.

MrC

---

### Post by Lord Illidan on 2007-03-11
> **Mr. C. said:**
> Without making any judgment on the quality of wireless support for Linux in general, it shouldn't be a stretch to understand that a product produced by a team of (well) paid, dedicated developers (eg. driver writers for Windows/Mac) will likely out pace software being developed by a small number of unpaid developers.  One also has to understand the size of the target audience.  All Unix and Linux stations combined is only a small fraction of the overall Windows market.  Where do you think companies are going to focus their resources?

The concept of open, "free" software is fantastic.  However, like the age-old adage that there is no such thing as a free lunch, this free software you get comes at a price.  That price is fewer man hours of development, testing, marketing, support, etc.  That translates into the user having to pay via time spent working out the kinks.

MrC

Not neccessarily. Quality does not depend on whether developer is paid or not.. It is a factor, but not decisive.

What is decisive is how much the manufacturer helps the developers in driver development. There are manufacturers like Ralink who actually go the whole hog and opensource their drivers, manufacturers like Nvidia who develop their drivers inhouse and make them propietary and manufacturers who don't give a fig about Linux and thus the drivers have to be reverse engineered from scratch, which is much, much harder.

---

### Post by Griffiss on 2007-03-11
Of course you're right mrC, even software developers need to eat after all. It's just that I'd got the impression that there was resistance on the part of some hardware manufacturers to making their products compatible with an open source OS. But maybe this is really just not having the resources to spare rather than active resistance.

It's just that 2 days of solidly inputting commands in the terminal, installing, uninstalling, changing config files and still not getting where I want to be at the end of it is taking its toll. I think a break is in order.

---

### Post by Mr. C. on 2007-03-11
> **Lord Illidan said:**
> Not neccessarily. Quality does not depend on whether developer is paid or not.. It is a factor, but not decisive.

What is decisive is how much the manufacturer helps the developers in driver development. There are manufacturers like Ralink who actually go the whole hog and opensource their drivers, manufacturers like Nvidia who develop their drivers inhouse and make them propietary and manufacturers who don't give a fig about Linux and thus the drivers have to be reverse engineered from scratch, which is much, much harder.

I never meant to imply any such thing.  My statements were speaking as a collective whole, not on a case by case basis.  It should be fairly obvious that the number of man hours of developement and testing  done for Windows drivers and software far exceeds that if Unix or Linux.  For every nVidia-like exception, there are a dozen WinModem-like propriety vendors.  In sheer numbers, there can be no argument.

It can also safely be stated that many companies do not share 100% of their IP with the open source community, thus leaving much reverse engineering and incomplete implementations.  Look at Samba - its been around for ages, and is still nowhere near complete.

I don't think there's much to discuss here.
MrC

---

### Post by Mr. C. on 2007-03-11
> **Griffiss said:**
> ...even software developers need to eat after all.

Its really not even this so much as a pure numbers game.  The total volume of developers, testers, test and regressions suites, dedicated hardware to test drivers in the Windows world is staggering.  And when problems do occur, there are typically dedicated peopled to track those problems, isolate them, debug, and resolve them.  Let's look at your case - perhaps you've encounted a dozen bugs along the way.  Did they get reported?  Is anyone tracking them?  Did you have a way to input them somewhere?  Would you have even been able to so anyway, given the complexity of this software.   I think you see where this is going...

> **Griffiss said:**
> 
It's just that I'd got the impression that there was resistance on the part of some hardware manufacturers to making their products compatible with an open source OS. But maybe this is really just not having the resources to spare rather than active resistance.

You are correct... there is much resistance on the part of companies to give away what the feel is their bread and butter.  And they will expend a great deal of effort to ensure that certain IP does not leave the doors. I know this for a fact.  

I hear you - it can be very, very frustrating.  It happens in all things computer.  Be patient, and someone will be able to get you going.

MrC

---

### Post by novice1 on 2007-03-11
I posted this in another thread and quoted it here in order to add comments.


"Why wireless support for Ubuntu is so poor is a good question. I come from a DOS/Windows Novell network support background and was a Certifed Network Engineer - I started fooling around with Linux out of curiosity since I had read so much about it. For the past year and a half I was running a Linux Linspire desktop computer using the same wireless card I am now using with Ubuntu -- Linsipire installed itself completely and properly configured the network card with out a hitch -- I have never heard of Ubuntu until Linspire announced that they and Ubuntu were going collaborate -- a few weeks ago. I gather they are both based on Debian Linux. I did not care for Linspire's KDE interface and the software/application packages they distribute via their CNS system. I do prefer the Ubuntu GUI and the Synaptic package update approach -- I at least can find what I am looking for there. However, with Ubuntu every thing I want to do entails searching for help and troubleshooting till it works. I never ever had to do that with Linsipre --all my video, audio, multimedia and wired/wireless networking stuff worked right out of the box with a generic install. But Linspire is NOT FREE -- one must buy the OS from them and then annually subscribe at additional cost to CNS for applications and software - most of which did not cost any thing in addition to the annual fee.

So my question is if wireless and multimedia stuff works well right out of the box for Linspire - why is it so challenging to make this stuff work in Ubuntu. I believe the answer may lay in Linspire being a commercial product and Ubuntu is over all not a commercial enterprise in the same sense. I am not faulting or criticizing all the good people that develop and support Ubuntu it is just that their focus is different from a fully commercial effort. Over all I much prefer Ububtu over Linspire -- it even seems to run faster on my computer than Linspire did."

My purpose here is not to tout Linspire but I must press the question as to why there is no  tinkering needed to get wireless working in Linspire and little to no need to go hunting for the right libs and drivers and codecs etc, just to get multimedia running?  It appears from my limited and very humble opinion that if these problems have already been addressed in Linspire (Debian based as is Ubuntu) why does the wheel have to be reinvented for these things to work in Ubuntu?  I am very new and very green to this Ubuntu and Linux community -- I don't mean to be throwing rocks at any one -- I m just confessing my ignorance and lack of understanding how it all comes together.

---

### Post by Mr. C. on 2007-03-11
> **novice1 said:**
> So my question is if wireless and multimedia stuff works well right out of the box for Linspire - why is it so challenging to make this stuff work in Ubuntu.

Your assumption and thesis is incorrect.  Go evaluate Linspire's "compatible" hardware list. You will find many products missing.

There is no free lunch.  All the drivers that you've taken for granted as just working in Windows need to be ported to Linux, and this takes an enormous amount of effort.  Given an order or two of magnitude fewer developers, one can readily understand why things take longer, and why the road can be rockier.

Until you've successfully written, debugged, documented, tested, and supported, a single Ethernet driver, for example, please try to avoid the "it should be easy" mentality. 

MrC

---

### Post by dmizer on 2007-03-12
here's a fantastic, in depth assessment of the problem: [http://andrey.thedotcommune.com/wireless.html](http://andrey.thedotcommune.com/wireless.html)

---

### Post by Mr. C. on 2007-03-12
It's a bullseye.

---

### Post by novice1 on 2007-03-12
> **Mr. C. said:**
> Your assumption and thesis is incorrect.  Go evaluate Linspire's "compatible" hardware list. You will find many products missing.

There is no free lunch.  All the drivers that you've taken for granted as just working in Windows need to be ported to Linux, and this takes an enormous amount of effort.  Given an order or two of magnitude fewer developers, one can readily understand why things take longer, and why the road can be rockier.

Until you've successfully written, debugged, documented, tested, and supported, a single Ethernet driver, for example, please try to avoid the "it should be easy" mentality. 

MrC

I see your point but I don't believe that I implied that I thought "it should be easy" at the very least that was not my intention nor my thinking. The only point I was trying to  make was that I had a run-of-the-mill No Name desktop computer and that Linspire worked fine on it and I did not have to spend hours trying to find "the right" driver, library, codec, etc. for all of it to function nominally. I am not a programmer of any sort but I can and do appreciate the effort and the time it takes to write a single driver. I have written rather complex database programs and know how complicated such efforts are  and can fully appreciate what it takes to produce one successful Ethernet driver without ever having written one myself. My remarks were not intended as criticism but as observation and pondering of the situation. Simply because I am not a programmer should not disqualify me from making observations and comments.   I have have no wish to be contentious here nor to put anyone or any group of people down. I have no doubt that many good, capable, sincere, passionate and hardworking people have put one heck of a lot of effort into getting Ubuntu where it is today.  I tip my hat to them all and am enjoying the benefits of their efforts and the fruits of their labor.

---

### Post by qamelian on 2007-03-12
> **novice1 said:**
> So my question is if wireless and multimedia stuff works well right out of the box for Linspire - why is it so challenging to make this stuff work in Ubuntu. I believe the answer may lay in Linspire being a commercial product and Ubuntu is over all not a commercial enterprise in the same sense. I am not faulting or criticizing all the good people that develop and support Ubuntu it is just that their focus is different from a fully commercial effort. Over all I much prefer Ububtu over Linspire -- it even seems to run faster on my computer than Linspire did."

My purpose here is not to tout Linspire but I must press the question as to why there is no  tinkering needed to get wireless working in Linspire and little to no need to go hunting for the right libs and drivers and codecs etc, just to get multimedia running?  It appears from my limited and very humble opinion that if these problems have already been addressed in Linspire (Debian based as is Ubuntu) why does the wheel have to be reinvented for these things to work in Ubuntu?  I am very new and very green to this Ubuntu and Linux community -- I don't mean to be throwing rocks at any one -- I m just confessing my ignorance and lack of understanding how it all comes together.

I'd love to answer your question, but since Linspire won't even install or boot (live CD) on my laptop and Ubuntu works flawlessly on the same unit, I'm pretty much unable to make the comparison. All things considered, I found Ubuntu to be the easiest distro I've tried in the last two years as far as getting wireless working. That's one reason why I keep sticking with Ubuntu, even though I continue to test other distros.

---

### Post by Ek0nomik on 2007-03-12
Why is wireless support so poor?

Blame the people who make the support.

---

### Post by Mr. C. on 2007-03-12
> **novice1 said:**
> ...but I don't believe that I implied that I thought "it should be easy" at the very least that was not my intention nor my thinking.

I appreciate your comments, and empathize with your frustrations.  While I believe you are very sincere in desire not to make an "it should be easy" implication, I'm my opinion, some of your language hinted otherwise.

In the end, all is fine.
MrC

---

### Post by Mr. C. on 2007-03-12
> **Ek0nomik said:**
> Blame the people who make the support.

Huh?

---

### Post by randell6564 on 2007-03-12
> **Griffiss said:**
> 
Is it an effect of the non-commercial nature of ubuntu? 
Griffiss

EXACTLY!  Example:  Linksys does not support Linux because there is no money in it for them.
So, the good folks out there in the Linux community have to create free drivers from scratch that HOPEFULLY will make your particular wireless card work!

Just try and talk to the support people that work for the company that makes your card.  Mention the fact that you use Linux and they will quickly end the conversation.

---

### Post by randell6564 on 2007-03-12
> **Mr. C. said:**
> Huh?

What ek0nomick is saying is; the folks who make your card do not support Linux..they do not make drivers for Linux users.  So.,place the blame on them not Linux.

---

### Post by Mr. C. on 2007-03-12
> **randell6564 said:**
> What ek0nomick is saying is; the folks who make your card do not support Linux..they do not make drivers for Linux users.  So.,place the blame on them not Linux.

Got it.  One cannot blame a manufacturer for their choices as to the products they decide to build and offer.  One can only blame the CONSUMER of those products.

MrC

---

### Post by rjfioravanti on 2007-03-12
Just wanted to comment about something somebody said 

> 
The concept of open, "free" software is fantastic. However, like the age-old adage that there is no such thing as a free lunch, this free software you get comes at a price. That price is fewer man hours of development, testing, marketing, support, etc. That translates into the user having to pay via time spent working out the kinks.


I really don't believe people like microsoft have more time in development and testing

check out this link [http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

specifically the paragraph about souce code analysis in the Intellectual Property section

---

### Post by randell6564 on 2007-03-12
> **Mr. C. said:**
> Got it.  One cannot blame a manufacturer for their choices as to the products they decide to build and offer.  One can only blame the CONSUMER of those products.

MrC

No.  Thats NOT what I meant.  BLAME the manufacturer, NOT the consumer!  The manufacturer is the one who is not supporting your decision to use Linux with the card that THEY built.  They are very aware that Linux exsists, but CHOOSE not to support Linux by creating drivers for Linux.  So, you are left to your own devices.  Find one out there somewhere through a Repository, or use a distro that packages what you need to get your card working.

---

### Post by Mr. C. on 2007-03-12
Your comparison is too general and ambiguous to be meaningful.  My comments are targeted at the entirety of the Windows platform development eco-system.  The number of developers in that eco-system is staggering; much larger than most would guess.

I will give you an example of real world scenarios, names changed to protect the innocent.

Company X develops hardware Z.  They staff the effort to develop, test, and support Z with approximately 50 employees, including 5-10 full-time, senior developers.  Company X decides to get into the open source/Linux game.  They staff that effort to develop Z for Linux with 1 junior engineer, and perhaps 1 part-time tester, and approximately 20 people include marketing, IP lawyers, architects, managers, support, documentation, consultants, etc. all to just work over the details of what they should and should not disclose in terms of IP, what their risks are, how their Windows customers will respond, etc.

Consider the MacOS from years ago.  Windows to Mac developers was like 500 to 1.  It doesn't take a genius to see the scales of economy and impact here.

This is just the tip of the iceberg.

MrC

---

### Post by Mr. C. on 2007-03-12
> **randell6564 said:**
> No.  Thats NOT what I meant.  BLAME the manufacturer, NOT the consumer!

I understood what you meant.  You need to learn some basic business, and learn about the phrase Caveat Emptor, and learn that  CONSUMERS are responsible for the choices they make.  Businesses are responsible to their share-holders.  It is an entirely reasonable and often prudent to support only a given platform.

Will you blame the manufacturer if you are a stock holder and they are not profitable and your stock losses money, because they dedicate a percentage of their staff to an unprofitable venture?

Plenty of local schools offer Business or Economics 101.  Have a look.

MrC

---

### Post by randell6564 on 2007-03-12
> The concept of open, "free" software is fantastic. However, like the age-old adage that there is no such thing as a free lunch, this free software you get comes at a price. That price is fewer man hours of development, testing, marketing, support, etc. That translates into the user having to pay via time spent working out the kinks. 

I disagree.  It has nothing to do with man hours, testing, marketing, support etc..

The key word here is "Free".  That word is a BIG turn-off to the major companies who build the hardware that we use.

---

### Post by randell6564 on 2007-03-12
> **Mr. C. said:**
> I understood what you meant.  You need to learn some basic business, and learn about the phrase Caveat Emptor, and learn that  CONSUMERS are responsible for the choices they make.  Businesses are responsible to their share-holders.  It is an entirely reasonable and often prudent to support only a given platform.

Will you blame the manufacturer if you are a stock holder and they are not profitable and your stock losses money, because they dedicate a percentage of their staff to an unprofitable venture?

Plenty of local schools offer Business or Economics 101.  Have a look.

MrC

Dude.  There is no reason to get rude because someone disagrees with your comments.  I don't think that providing drivers for the hardware that one builds to someone who uses a different OS is going to result in a loss of profits to shareholders!  In FACT, it could ONLY result in a profit since you are reaching those who use an OS other than Windoze.

If you walk into a 'Best Buy'  looking for a wifi card, are you going to avoid the brands that you know do not support Linux?  And look to the brands that DO?  I would!  Do the math.

---

