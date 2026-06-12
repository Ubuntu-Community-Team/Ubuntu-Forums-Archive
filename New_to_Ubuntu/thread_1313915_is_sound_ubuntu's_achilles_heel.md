---
title: "is sound ubuntu's achilles heel?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by john1066 on 2009-11-04
I'm a beginner running 9.04 on my acer aspire 6930g with nvidia geforce 9300m gs. Most things go well but plugging in my headphones has no effect - the sound keeps coming from the laptop and not from the headphones. This a showstopper for me since I use the headphone output to play music from my laptop on my hifi system. Having done a quick search on the ubuntu forums I see that this has been a common problem over many versions of ubuntu - and I don't see any solution. I am sort of amazed that something so basic can run across so many versions of ubuntu without a fix.
Now I have run across the skype poll in this forum and see that there are lots of problems there too. 
So my burning question of the moment is - is there any solution to ubuntu's sound problems? I would prefer not to have to stick with Vista but it appears at first sight that ubuntu's got a big manko here.

Thanks,
John

---

### Post by NickJones on 2009-11-04
Hi John,
Sorry to hear you are having problems, try right clicking on the volume icon in the top right, and selecting "Sound Preferences" then "Output" and changing the "Connector" hope this helps, and you do stick with Ubuntu.

---

### Post by trulan on 2009-11-04
Yeah, what he said.

Far from sound being a problem, Ubuntu's superior sound capability is the very reason I left Windows.  Hang in there, you'll be glad you did.

---

### Post by clive littlewood on 2009-11-04
Hi

I've been running Ubuntu on an Acer Extensa laptop for 3 years and have not had any sound problems.

Stick with it i'm sure your fix will be a simple one !!

Clive

---

### Post by 3rdalbum on 2009-11-04
Some people have problems, other people don't. The ability to mute the speakers when headphones are plugged in is specific to the sound chipset, so this functionality must be reverse-engineered for every new sound chip.

It will eventually get fixed for whatever your sound chip is (it might be fixed in 9.10), but by that time there will be new sound cards available that will exhibit this problem.

---

### Post by john1066 on 2009-11-04
This is not so clear for me. I don't get that Vista worked ok from the very beginning (I've had this laptop for six months) and that Ubuntu has to reverse engineer for every sound chip - that would be horrific!


The suggestion above on the volume control doesn't do it. That only seems to allow you to configure which channel the volume control is working on. I don't see anything there that allows me to tweak the headphone socket.


At the moment I'm sort of dissapointed - plugging in the headphones and automatically getting the sound there is something that has always worked on every laptop (and windows version ) I've ever had. I can't imagine there is any rocket science involved here. Yet this topic appears loads of times in the forum with no answer.

Is it clear what the problem is?

John

---

### Post by ikt on 2009-11-04
> **john1066 said:**
> I don't get that Vista worked ok from the very beginning (I've had this laptop for six months) and that Ubuntu has to reverse engineer for every sound chip - that would be horrific!

It's because the people who make the drivers for the sound chip make them windows compatible and forget about everyone else, leave linux users in the dark.

Look at Creative, it took them 4 years to realise they couldn't make a driver good enough for their Sound Blaster X-Fi sound cards, until they gave the specs to 1 guy and he had it in the kernel in <3 months.

If the specifications of the hardware are open, linux supports it faster than any other OS. We were the first to support 64 bit, the first to support USB 3, and we will continue to be the first to support products and hardware which we can actually code for.

> Having done a quick search on the ubuntu forums I see that this has been a common problem over many versions of ubuntu - and I don't see any solution.

Try to submit a bug on launchpad with your problem, this is the quickest way to get your issue fixed.

---

### Post by fela on 2009-11-04
I wouldn't say that sound is Ubuntu's achilles' heel. I don't think that term would really apply to anything in Ubuntu or indeed any OS. Ubuntu has lots of 'bugs' like that due to it not being supported by hardware companies, and indeed the fact that there is no clear cut company or whatever that makes things for Linux - everything is made by everyone and because of that there are often situations such as there being hundreds of mediocre sound drivers for instance, rather than one very good one.

About your problem - sorry but I'm not too sure I'm the one to be giving advice on it, I've never had hardware problems in Ubuntu and therefore have never really found out much about fixing them, although I have a load of information about Linux in general stored in my head.

---

### Post by fela on 2009-11-04
> **trulan said:**
> Yeah, what he said.

Far from sound being a problem, Ubuntu's superior sound capability is the very reason I left Windows.  Hang in there, you'll be glad you did.

Is pulseaudio superior to whatever Windows uses? There's a LOT of bugs with pulseaudio. Sure, there's JACK aswell but I thought JACK was cross-platform? If so, JACK would be the best hands down, I think. If it only runs on *nix or just Linux, then I see your point.

---

### Post by john1066 on 2009-11-07
Didn't have much luck getting the headphone socket to work properly so I decided to upgrade to persistent usb 9.10. Now the headphone socket works fine - sound in the headphones and laptop muted when I plug in. I have some other problems (or maybe just ignorance on my part) but I'll kick of another thread for that since its not related to sound.

John

;)

---

