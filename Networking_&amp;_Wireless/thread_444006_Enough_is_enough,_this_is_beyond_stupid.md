---
title: "Enough is enough, this is beyond stupid"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by ctsdownloads on 2007-05-14
I have been (was) a happy Linux user since 2003. I have used many, many distros and I have watched excuse after excuse pass by regarding wifi incompatibility. Well today, I can't take it any longer. No more, will I sit here and listen to "the kernel this and the FCC" that. There are wifi drivers available for us to use - today, that work as described. Unfortunately, Ubuntu has worked VERY hard at targeting a "pretty" appearance with that steaming pile of bile we call "network-manager"; which only works if you happen to have a card that is magically blessed to work.

And even if the card should work in NM, you can rest assure that unless your card has the words Intel in it, you will be enslaved by WEP if you are lucky as most wifi cards in Linux do not, in fact, support WPA. And by the off chance you magically get NDISwrapper to work with your card, duplicating this will not happen.

Example, I own 12 wireless cards, ranging from 802.11b to g. One, I repeat ONE card actually works: it is the Gigafast WF728-AEX and of course, you will never see anyone else selling this anyplace.

There is a problem here that Mark Shuttleworth and his ilk have _knowingly ignored_ so that they could slap together the crappiest release of Ubuntu yet. I have read wifi bug report after report, even posts littered with "it used to work in Edgy" type comments. Good god people, what the heck is going on? For the first time in history, Microsoft has released an OS worse than Windows Me and we pass off Feisty as a "usable option for notebooks!!!! We sure missed out on that opportunity...

Want the magic formula for getting wireless to work in Linux? OK, but those cheap skates out there are not going to like it - PICK A WIRELESS VENDOR AND STICK WITH THEM. Stop supporting vendors that do not support us. Spend more time making sure that Ralink, Intel and Madwifi (Atheros) is being properlly implemented. Spend the time working on WPA out of the box, really work over network-manager to get it to support cards that use drivers that are open.

Because folks, as it stands now, guess what your options are: buy a card with the words Intel on it, continue to play musical wifi cards or simply break down and buy a new notebook from a Linux vendor every time Ubuntu devs opt to use a kernel that kicks working wireless to the curb. Stop trying to meet deadlines, consider that some of us are using modern computers that rely on true wireless capabilities. 12cards, and not once did that proprietary driver wizard come up for me. Again, stop trying to please cheap skates, pick a card and force notebook users to spend that whopping $20-30. :mad: 


In the meantime, I am going to take my own money and I am going to hire some people with a clue off of one of those freelance sites to piece together a workable solution for this kind of nonsense that hopefully, can withstand another wondrous "upgrade". (/end rant)

---

### Post by tgm4883 on 2007-05-15
So to sum up the rambling.  "My card doesn't work.  I don't want to buy one that does.  Stop bowing to the cheapskates (even though I don't want to buy another card).  I'm going to fix this problem myself."

Guess I must be one of the lucky ones that has a working card.  Sadly, it does say intel on it, so does that make me a cheapskate for not wanting to buy a card that doesn't work?

---

### Post by buMPer on 2007-05-15
> There is a problem here that Mark Shuttleworth and his ilk have knowingly ignored so that they could slap together the crappiest release of Ubuntu yet. I have read wifi bug report after report, even posts littered with "it used to work in Edgy" type comments. Good god people, what the heck is going on? For the first time in history, Microsoft has released an OS worse than Windows Me and we pass off Feisty as a "usable option for notebooks!!!! We sure missed out on that opportunity...


Amen to that.

Why not look for a card manufacturer who will support the Open community and in return, the community will endorse their product.  It's like good business karma.

---

### Post by ctsdownloads on 2007-05-15
> So to sum up the rambling. "My card doesn't work. I don't want to buy one that does. Stop bowing to the cheapskates (even though I don't want to buy another card). I'm going to fix this problem myself."

Guess I must be one of the lucky ones that has a working card. Sadly, it does say intel on it, so does that make me a cheapskate for not wanting to buy a card that doesn't work?

OK, I have a working card. Hell, I even fixed the rt2500 initializing issue that Feisty did a fantastic job at curbing. But the fact remains that collectively, we are so damned busy kissing each other's backsides that the original issue remains - chipset compatibility with each upgrade.

Edgy is a solid distro, never failed me. And with the wiki page listing the cards known to work, we had a shot. Then we have feisty, which single handedly fried that compatibility list's integrity. Sure, some of the cards still likely work. Just remove network-manager, undo that zero-conf beta nonsense and take a few steps back to examine the ongoing issue that wifi compatibility has remained the red headed step child for this distribution.

I had a wifi vendor ready to help me play ball, stick to one of the previously mentioned chipset schemes. But then Feisty decided we were not inconsistent enough any longer. Nope, we have too many cards working and holy crap  - we can begin to figure that certain chipsets and drivers were reliable! Sure, WPA is sorta,not really supported out of the box; even though there are drivers that do support it, but hell, we have a zero-conf solution for that now dormant wireless card! Sure sounds like progress to me!

---

### Post by justin whitaker on 2007-05-15
> **ctsdownloads said:**
> I have been (was) a happy Linux user since 2003. I have used many, many distros and I have watched excuse after excuse pass by regarding wifi incompatibility. Well today, I can't take it any longer. No more, will I sit here and listen to "the kernel this and the FCC" that. There are wifi drivers available for us to use - today, that work as described. Unfortunately, Ubuntu has worked VERY hard at targeting a "pretty" appearance with that steaming pile of bile we call "network-manager"; which only works if you happen to have a card that is magically blessed to work.

This is the first release of network manager, I would give them a break on that. People complained about having to jump through hoops to get networking set up, and now people are complaining that it does not work with all cards or in all situations. So the Devs can't win either way, right?

> Example, I own 12 wireless cards, ranging from 802.11b to g. One, I repeat ONE card actually works: it is the Gigafast WF728-AEX and of course, you will never see anyone else selling this anyplace.

So you have 12 cards, and one works. Most other people have 1 card, and it works, or it doesn't. Consider yourself lucky. 

> There is a problem here that Mark Shuttleworth and his ilk have _knowingly ignored_ so that they could slap together the crappiest release of Ubuntu yet. I have read wifi bug report after report, even posts littered with "it used to work in Edgy" type comments. Good god people, what the heck is going on? For the first time in history, Microsoft has released an OS worse than Windows Me and we pass off Feisty as a "usable option for notebooks!!!! We sure missed out on that opportunity...

Regressions happen...I remember that USB worked in Dapper, not in Edgy, then they fixed it (again) in Feisty. The changes they make each generation can include some quite deep customizations of the kernel...
so stuff breaks. Hopefully, they get it sorted by the next LTS release. 

And Vista is by no means worse than ME. It's annoying, yes, but it's not a bad OS. The opportunity is not whether Vista is good or bad, it's that Microsoft's business tactics are rubbing people the wrong way. Do you think your rant really makes Linux users look good?

> Want the magic formula for getting wireless to work in Linux? OK, but those cheap skates out there are not going to like it - PICK A WIRELESS VENDOR AND STICK WITH THEM. Stop supporting vendors that do not support us. Spend more time making sure that Ralink, Intel and Madwifi (Atheros) is being properlly implemented. Spend the time working on WPA out of the box, really work over network-manager to get it to support cards that use drivers that are open.

Based on my experience, people generally buy their hardware first, then at some point switch to Linux. Hence, so many ATI card threads when those of us that have been around for a while know damn well that drivers for those cards can be problematic. My guess is that the wireless cards have the same issues. 

> Because folks, as it stands now, guess what your options are: buy a card with the words Intel on it, continue to play musical wifi cards or simply break down and buy a new notebook from a Linux vendor every time Ubuntu devs opt to use a kernel that kicks working wireless to the curb. 

It's not like wireless is the only way to connect to the internet. I find it very hard to believe that because wifi does not work in some cases, the notebook is now a brick. There is this thing called ethernet, I bet you have heard of it? Cable? FiOS? Dialup? 

Now, it might not be your PREFERRED way of getting online, but I do not think that it is some Laptop doomsday scenario as you want to paint it. 

> Stop trying to meet deadlines, consider that some of us are using modern computers that rely on true wireless capabilities. 12cards, and not once did that proprietary driver wizard come up for me. Again, stop trying to please cheap skates, pick a card and force notebook users to spend that whopping $20-30. :mad: 

Linux users don't buy anything, we all know that! :) 

You know, I can't help but point out that the 6 month deadline is one of the things that keeps Ubuntu fresh. It could go annually, but many distributions that do that become increasingly irrelevant over time. I would suggest, though, that you take a look and see if one of the 500+ other distribution might solve your issue. 

> In the meantime, I am going to take my own money and I am going to hire some people with a clue off of one of those freelance sites to piece together a workable solution for this kind of nonsense that hopefully, can withstand another wondrous "upgrade". (/end rant)

Great! At least you are doing something proactive!

---

### Post by ctsdownloads on 2007-05-15
> Based on my experience, people generally buy their hardware first, then at some point switch to Linux. Hence, so many ATI card threads when those of us that have been around for a while know damn well that drivers for those cards can be problematic. My guess is that the wireless cards have the same issues.

I have been studying the issue since 2003. Yes, the end user has to buy the right hardware, then install. Hardware before software, etc. I can do this with my everything from scanners to printers; and used to be able to a limited extent with wifi cards. But when people start pointing to solutions with "revision numbers" on them (any big-box wifi card vendor), we continue to ignore the vendors that out out chipsets and actual cards that are supported, using open drivers and do not ever plague us with "revision number" nonsense. And the WPA issue is frankly, ridiculous and preventable.

---

### Post by ctsdownloads on 2007-05-15
> Great! At least you are doing something proactive!

All sarcasm aside, I am hoping to get something in place that examines the system state after an upgrade, then makes the appropriate changes to up and down the card to get it working. Just like with RT2500, the driver was there, they just hosed the initialize process.

---

### Post by justin whitaker on 2007-05-15
> **ctsdownloads said:**
> All sarcasm aside, I am hoping to get something in place that examines the system state after an upgrade, then makes the appropriate changes to up and down the card to get it working. Just like with RT2500, the driver was there, they just hosed the initialize process.

I wasn't being sarcastic. Ok, maybe a little. :) 

It's good to see someone put their money where their mouth is and, you know, do something, instead of stomping off in a huff and leaving the problem festering. If more people did what you are doing, Linux would 100% rock, all the time, instead of 100% depending on the hardware you use, what distro you are using, and the phase of the moon.

---

### Post by DarkN00b on 2007-05-15
Wow. All it took for me was a five minutes of research and I bought a Broadcom 4318 based Linksys card that works just by installing some firmware. Research I would have done with Windows as well because I want the most compatible card I can get.

---

### Post by ctsdownloads on 2007-05-15
> It's good to see someone put their money where their mouth is and, you know, do something, instead of stomping off in a huff and leaving the problem festering. If more people did what you are doing, Linux would 100% rock, all the time, instead of 100% depending on the hardware you use, what distro you are using, and the phase of the moon.
Reply With Quote

Thanks, actually I have done this with a few projects. I support a number of projects financially as I cannot rightfully complain without having my wallet involved. What I should have made clear is that I am not trying to fix these issues for myself, hell that would be easy. My goals are much larger and far reaching. Can't really talk about it, but I believe you will know it when you see it surface. ;) 


> Wow. All it took for me was a five minutes of research and I bought a Broadcom 4318 based Linksys card that works just by installing some firmware. Research I would have done with Windows as well because I want the most compatible card I can get.

Definitely, but again, it's unneeded. Broadcom is a problem chipset. You can "make it work", but I believe we can become easier than Vista; not like this is a stretch anyway...lol.

---

### Post by tgm4883 on 2007-05-15
> 
Definitely, but again, it's unneeded. Broadcom is a problem chipset. You can "make it work", but I believe we can become easier than Vista; not like this is a stretch anyway...lol.

Wait im confused now.  Are you saying because he has a problem chipset that it shouldn't work at all?  It seems that way because your rant reads as it should work either OOB or not at all.

---

### Post by darkworld on 2007-05-15
Im a newbie but from what i have read Linux is falling behind on the WiFi stakes. How on earth are people going to get into Linux when the first thing they discover is there hardware is unsupported.

---

### Post by chili555 on 2007-05-15
And what, exactly, is wrong with buying equipment based on compatability, even if the wireless card says Intel? Why on earth would I buy a $1400 laptop and settle for a "maybe it works, maybe not" wireless chipset?

I started in Linux in 2001; basically, everything I owned, including my CD burner and my soundcard, was incompatible. I learned my lesson.

---

### Post by ctsdownloads on 2007-05-15
> Wait im confused now. Are you saying because he has a problem chipset that it shouldn't work at all? It seems that way because your rant reads as it should work either OOB or not at all.
Reply With Quote

My bad, let me clarify.

It would be great to see Ubuntu support whatever they can. Broadcom, etc. But thanks to the reluctance of most wifi card manufacturers, we do not have this luxury. We are deluting ourselves into believing that wifi vendors care - trust me, I have spoken to three at the "suit" level and only one of them gave a rats butt about the Linux user. And that manufacturer, was Edimax w/Ralink chipsets.

That said, at some point, because of the painfully obvious nightmare involved with working with the number of chipsets and drivers we are now (just search the forums for examples), favorites will have to take exception here. 

Now for the off-topic point: Why doesn't Apple have these types of problems? Well, it's nothing to do with the OS folks, its the control of the hardware. So while I certainly hate to take that extreme of an approach, getting onboard with chipsets that have produced a stronger track record of success will yield less frustration.

So basically, we have a choice: continue with with wireless progress that has made us look very silly. We point to FCC regulations, we exclaim there are not open source drivers, all sorts of fun nonsense that we cling to in an effort to support as many chipsets as possible. And to this day, the results speak for themselves. We have  hundreds upon hundreds of people asking the same questions over and over.

Because I can buy a Broadcom card from the store, complete with those wonderful revision numbers on the card models that ensure there is no true support to be given to the new user, we will continue to sit here in a haze of denial so that users of problem chipsets can potentially, maybe, probably not, have a card that works without a trip to an online store to by one that is supported with a better track record.

Let's review: Support everyone;s chipset, advocate the ndiswrapper LCD trip as a "fix", further supporting Windows created drivers 

or

Pick two or maybe three chipsets. March over to these manufacturers and basically lay the Linux wireless world in their laps if they stick to our requested chipsets. We then, support our own drivers as we have always (rt2x00.serialmonkey, Madwifi, etc) and from release to release, for a one time card purchase - we know that our wireless works.

it's simple, clean and we can remain in control as a community because we control the drivers. I cannot see a single problem with this. If someone else wants to use ndiswrapper, wonderful - good luck with it as always. But instead of putting new money and effort into 50% solutions, let's take an approach with a clear head and less hype of success. It's simply a matter of commonsense.

---

### Post by ctsdownloads on 2007-05-15
Hi Chili, 

who were you referring to?

---

### Post by ctsdownloads on 2007-05-15
At the end of the day, this speaks for itself:

[http://ubuntuforums.org/showthread.php?t=419905](http://ubuntuforums.org/showthread.php?t=419905)

---

### Post by ctsdownloads on 2007-05-15
As for my point about Broadcom...

[http://ubuntuforums.org/showthread.php?t=445202](http://ubuntuforums.org/showthread.php?t=445202)

---

### Post by SirShaggy on 2007-05-15
> **ctsdownloads said:**
> As for my point about Broadcom...

[http://ubuntuforums.org/showthread.php?t=445202](http://ubuntuforums.org/showthread.php?t=445202)

I have to say I agree with you completelt! :) I am by no means a master Linux user but can accomplish almost
everything myself with little to no help. Wireless, not a chance. It varies so much and gets changed in every release. I was actually glad to see this post. Yes, I was a Windows user previously to Linux. I used Solaris at work. I was a Telephone Engineer for several years and all of my work was on a Sun. I liked it better than Windows and started looking around. I used Suse an Fedora on and off for  16-18 months and then found Ubuntu 5.10. I loved it. I still do. I hate Wireless setup though, I always will I'm sure.
Yes, my card was a revision 5. I live in a small town who has just 2 places to get hardware. You get what they have. The average user will just buy what is on the shelf, that is what Windows tought us to do. No I don't like Windows or the support they give their customers, but hardware support is better in Windows. I have a copy of Vista that was for an upgrade of the XP on my machine. I installed it onto a seperate partition to check it out. My hardware was MOSTLY supported out of the box. A couple of things required a driver disk, no big deal. Yes I removed Vista, still don't like it. I have Linux on every PC I own. Some of them are old, some new. 1 of them has XP on it so I could download BIOS zip files and unpack them to place on a floppy. I still use it for that and nothing else. I love what Linux has become. It always gets better for me. Just not the wireless issue. Who fault is it? Mine for the card I bought, Corperations building the chipsets and cards, software writers???
Yes my card works. It has a broadcom chipset. It installs differently in every version of Ubuntu and other distro out there. Why? Anyway, this is a good post. Maybe it will light a fire. Yes, I am staying put. I am afterall, a Linux user. I will continue to look up hardware before purchasing and HOPE that Linux doesn't change too much between versions, kernels and distro's.

SirShaggy

---

### Post by chili555 on 2007-05-15
> Hi Chili, who were you referring to?To anyone who will listen.

As you can see by my bean count, I have answered a few posts here, almost all on wireless, a particular fascination of mine. I have a few hundred posts over on fedoraforums as well.

I think the card maufacturers believe they have a great self-interest in keeping their "trade secret" chipset behind the veil. As well, as we know, they have exactly no interest in providing drivers to the Linux community, although Realtek and Intel, and maybe another, at least make an effort. 

So what can we do? We can write the drivers ourselves or troubleshoot the drivers in the kernel now, and there are some real dogs in there. We can beg the card manufacturers to come to our rescue; good luck to you on that one.

We can buy based on compatability; that's my choice.

We can struggle along with ndiswrapper. It works reasonably well, very few cards have not been able to be coaxed to life with it. 

Frankly, I'm hopeful, but skeptical, that wireless will get fixed any year soon. Please prove me wrong.

---

### Post by ctsdownloads on 2007-05-15
> We can buy based on compatibility; that's my choice.

No arguments there, now if we can stop breaking what worked only one release ago....RT2500 initializing, for one, among other chipsets from what I have seen. With rt2500, I can "up_down" it to get it going from a bash script, then use WiFi-Radar to make it work, but why should I have needed to do this when in Edgy - no "bashing" was needed. Again, devs are getting a free pass here, and I cannot let this slide as it is was not the only chipset to get the finger.

---

### Post by Ateo on 2007-05-17
LMAO. *IF* you have really been using linux for years (I think you're lying and just want attention) you would know to RESEARCH before buying right? Then, you would have known to invest in an Intel card right?

But no, it's Ubuntu's fault even though it's really a PEBKAC...

Would you like some cheese with that wine?

---

### Post by digitalbenji on 2007-05-17
This is not productive.  It just sounds like you don't know what you are doing/talking about.  I've been able to get WPA working on 2.4 and 2.6 kernels using a Debian, Slax, Suse, Red Hat, Gentoo, and Ubuntu.  All on the same laptop, and all using Ndiswrapper.

---

### Post by tgm4883 on 2007-05-17
> **Ateo said:**
> LMAO. *IF* you have really been using linux for years (I think you're lying and just want attention) you would know to RESEARCH before buying right? Then, you would have known to invest in an Intel card right?

But no, it's Ubuntu's fault even though it's really a PEBKAC...

Would you like some cheese with that wine?

Nice, did you even read any of this thread before posting?  He is talking about how OOB the cards worked in edgy and now they do not work in feisty OOB.  

Hell, if you had even read the post above yours (the last post before you posted) you would see what he is talking about.  Grab a pair and stop being a dick

---

### Post by tgm4883 on 2007-05-17
> **digitalbenji said:**
> This is not productive.  It just sounds like you don't know what you are doing/talking about.  I've been able to get WPA working on 2.4 and 2.6 kernels using a Debian, Slax, Suse, Red Hat, Gentoo, and Ubuntu.  All on the same laptop, and all using Ndiswrapper.

Again, read the thread, he is talking about wireless cards that natively worked in edgy no longer in feisty.

---

### Post by ctsdownloads on 2007-05-18
> This is not productive. It just sounds like you don't know what you are doing/talking about. I've been able to get WPA working on 2.4 and 2.6 kernels using a Debian, Slax, Suse, Red Hat, Gentoo, and Ubuntu. All on the same laptop, and all using Ndiswrapper.

> LMAO. *IF* you have really been using linux for years (I think you're lying and just want attention) you would know to RESEARCH before buying right? Then, you would have known to invest in an Intel card right?

But no, it's Ubuntu's fault even though it's really a PEBKAC...

Would you like some cheese with that wine?

Again, read the *blanking* posts, people. Don't just glaze over them with fanboy eyeballs, **really** read them. Yes, I am aware of what I am talking about, yes, I am competent with a number of popular Linux distros, and yes, WPA is SPOTTY at best - this is Linux 101, if you seriously believe that most "working" cards support WPA with native drivers, then you are apparently living in a wonderland. And yes, ndiswrapper is yet another example of the kool-aid truck making its rounds to support Windows supportive hardware rather than supporting hardware vendors that has been supportive of us.

Look, ndiswrapper is at best, a 70% fix with some cards and is not a solution, it is  a form of denial. Supporting hardware that supports us is apparently, a four letter word around here which answers yet, another question that I have been wondering about - are we ready to grow up and play in the big leagues? Today, I am seeing that there is still work to be done within the ranks of people who react more like Mac fans than Linux users interested in seeking solutions to existing challenges.

No offense, but RTP next time... :roll:

---

### Post by ctsdownloads on 2007-05-18
> Again, read the thread, he is talking about wireless cards that natively worked in edgy no longer in feisty.

Definitely,man. But I am also touching on this "blanket clenching mentality" we see from some of the users out there. They are so afraid of someone pointing out a string of reality; a preventable reality I might add, that they would rather attack than actually make a valid point in disagreement.

Look, I love Linux, I love Ubuntu. I do not spend my days working in Windows, as I do not even have it installed on anything other than VM. So I feel fairly confident in my points and also, thank for tgm4883 for following the thread. Always refreshing to know that reading is still happening in here from time to time. :)

---

### Post by tgm4883 on 2007-05-18
> **ctsdownloads said:**
> Definitely,man. But I am also touching on this "blanket clenching mentality" we see from some of the users out there. They are so afraid of someone pointing out a string of reality; a preventable reality I might add, that they would rather attack than actually make a valid point in disagreement.

Agreed

> **ctsdownloads said:**
> 
Look, I love Linux, I love Ubuntu. I do not spend my days working in Windows, as I do not even have it installed on anything other than VM.
Same here

> **ctsdownloads said:**
> 
 So I feel fairly confident in my points and also, thank for tgm4883 for following the thread. Always refreshing to know that **reading** is still happening in here from time to time. :)

Now you take that back, I won't have people think i'm reading.  :p

---

### Post by Henry Rayker on 2007-05-18
This is actually the number one reason why I jumped ship and headed over to Fedora. I struggled to get any of my (at the time) 2 cards to work AT ALL in Breezy, then spent some time trying to get either of them to work in Dapper (any time the card was in the slot, my laptop would hard freeze.) When Edgy rolled around, I hoped for some advances....nope. I actually ended up blacklisting the modules installed and installing myself in order to just get a connection. I NEVER had any protection on an Ubuntu wireless connection...

When I installed Fedora, every single card I have worked out of the box (I now have 3...I finally got around to getting a built in card which gave me some trouble in Ubuntu). Not only this, but the default NetworkManager applet installed by Fedora actually works with my ralink cards (something the one installed from the Ubuntu repos never felt like doing).

Another little quirk that came about was my OS is just faster...everything in Fedora feels much faster than any of the Ubuntu installations I ever had...I honestly think that Ubuntu just blows seriously when it comes to laptops.

---

### Post by yavez on 2007-05-18
Agree with the original poster wholeheartedly.  My Ralink card worked great in Edgy, and then in Feisty it's completely b0rked.  And don't get me started on i915resolution.  That some serious hair-pulling on Ubuntu for me (and I'm already bald).  I jumped over to PCLINUXOS and lo-an-behold, Ralink wireless works out of the box, my graphics card detected and a nice little pop-up box informed me that I should download i915resolution - did so and I could set any resolution I wanted (all from within the same window).  Now if it only had a Gnome desktop I'd switch full time.

What's the deal with Ubuntu lately?  I had more success in the Hoary days than anything of late.

---

### Post by jglen490 on 2007-05-18
> **ctsdownloads said:**
> Definitely,man. But I am also touching on this "blanket clenching mentality" we see from some of the users out there. They are so afraid of someone pointing out a string of reality; a preventable reality I might add, that they would rather attack than actually make a valid point in disagreement.

Look, I love Linux, I love Ubuntu. I do not spend my days working in Windows, as I do not even have it installed on anything other than VM. So I feel fairly confident in my points and also, thank for tgm4883 for following the thread. Always refreshing to know that reading is still happening in here from time to time. :)

ctsdownloads --

You seem to have a strong grasp of the obvious.  You did some homework, and then made a choice; that choice being to switch distros.  Yep, you did switch between Ubuntus and were disappointed.  Too bad it had to happen, but it did.  Don't blame Mark S. because he provides a free product that requires considerable effort to improve with each new iteration.  Instead, find something that works and stick with it for a while.  Your computing experience will be much more satisfying.

I picked Kubuntu 6.06 LTS just before 6.10 came out.  The "LTS" part, plus good user reviews, is what grabbed me.  LTS = Long Term Support.  There is a commitment behind this one, and it works well.  I got my "problematic" Buffalo (Broadcom 4318) cardbus adaptor to work via ndiswrapper (the version that came on the Dapper CD) and I keep up with the updates that announce themselves on a regular basis.  When the LTS commitment runs out, I'll be looking for a replacement - another long term commitment - whether its Gutsy Gibbon or Hungry Hippo or Jocular Jackal or even some other distro maker completely.  I'll also be checking up on user satisfaction.

Linux space is not the monolithic universe that Windows chooses to be.  That's both good news and bad.  The good news is you have numerous choices, the bad is that you are quite often at the mercy of obstreperous hardware vendors.  Just live with it, or work with an open source developer to fix it.

---

### Post by ctsdownloads on 2007-05-19
> You seem to have a strong grasp of the obvious. You did some homework, and then made a choice; that choice being to switch distros. Yep, you did switch between Ubuntus and were disappointed. Too bad it had to happen, but it did. Don't blame Mark S. because he provides a free product that requires considerable effort to improve with each new iteration. Instead, find something that works and stick with it for a while. Your computing experience will be much more satisfying.

I picked Kubuntu 6.06 LTS just before 6.10 came out. The "LTS" part, plus good user reviews, is what grabbed me. LTS = Long Term Support. There is a commitment behind this one, and it works well. I got my "problematic" Buffalo (Broadcom 431 cardbus adapter to work via ndiswrapper (the version that came on the Dapper CD) and I keep up with the updates that announce themselves on a regular basis. When the LTS commitment runs out, I'll be looking for a replacement - another long term commitment - whether its Gutsy Gibbon or Hungry Hippo or Jocular Jackal or even some other distro maker completely. I'll also be checking up on user satisfaction.

Linux space is not the monolithic universe that Windows chooses to be. That's both good news and bad. The good news is you have numerous choices, the bad is that you are quite often at the mercy of obstreperous hardware vendors. Just live with it, or work with an open source developer to fix it.

I appreciate your point of view, but do most definitely disagree with support for Broadcom adapters; mainly because other previously better supported adapters paid a price with dev attention it seems.

We'll see what the next version of Ubuntu looks like. Edgy and Feisty have made some great strides over that of Dapper, and we'll see if Gusty can bring back the love felt by many we found with Edgy's wifi support. 

Regarding the idea of bringing some level of wifi card standards to Linux distros as as whole, it will eventually have to happen. Ubuntu is simply becoming too popular amongst people who demand it, regardless of what I think. And that will require drivers supporting WPA across the board (years away) or picking a few companies that will help to make this happen (already done, but we ignored them).

Much like the insanity of seeing a growing number of consumer based proprietary applications in a Linux distro - they said that would never happen ,either, now we have Linspire's release of CNR, Automatix among others, "selling" closed source software. 

Purists are none to happy about the changes happening, but regardless, these types of events are coming to pass. So it will be interesting to see what will happen on the wifi front. Oh, one last thing. The guy who begins to sell a PCMCIA wifi cards designed* just for Linux users* will become a very wealthy man as the distros continue to see new migrants coming over from the Windows side of the fence (with enough time given). I really believe this. It will not be a matter of "if", it will be a matter of when enough is enough and users have had enough of feeding the "wireless networking" thread at this fantastic forum. It's simply a matter of time well spent.

---

### Post by jglen490 on 2007-05-19
> The guy who begins to sell a PCMCIA wifi cards designed just for Linux users will become a very wealthy man as the distros continue to see new migrants coming over from the Windows side of the fence (with enough time given).

There are infact wifi card makers who do support Linux to some degree or other, there's none of them getting rich just from Linux, however.

Part of the joy of Linux is seeing folks move up to challenges, like the wifi issue.  Instead of screaming an yelling about stupid wifi chip makers (which would be entirely justified), there are some who say, "O.K. I can play with this and beat you at your own game".  Thus, products like ndiswrapper and fw-cutter and others, too.  O.K., so they're not perfect.  The joy was in seeing my Buffalo card, which almost went to the trash can, light up after just one more try.  I unplugged my ethernet cable and carry my laptop around now.

Why did I buy a Buffalo card?  It was cheap.  I like cheap, when it works.  I stick with Linux, I buy used hardware.  I've kept both Linux and my IBM T20 for several years now.  Why?  They work.  I think it would be a bad thing for there to be no challenges in this world`, and I'm glad there are people who try to put up a good product with little hope of riches from that product, but maybe a little fame.

I don't care that Broadcom doesn't support open source, but I'm grateful that they have a product that does allow me to access wifi.  I do care and am very grateful that there are bright, talented people who can make a Broadcom chip work with an open source operating system.

I hope the next *buntu LTS distro will be as good and satisfying as Dapper Drake, and I hope that Canonical will keep on doing their R&D work with Linux for years to come.

---

