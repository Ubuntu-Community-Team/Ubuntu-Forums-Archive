---
title: "graphics card issue??"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by |xem| on 2010-11-30
Hi all, I just installed ubuntu 10.04, first experience with lnux, a few days ago. I actually pulled out my old hp laptop (purchased in 2003) and figured I would play around with it first. Some specs. I have 512 mb ram, and AMD 2200+, pretty weak I know, I will max out the ram to 1 gb soon. And by the way, I am convinced my following problem cant be due to the low ram and old cpu since windows xp runs smooth on it (dual booted). I have a questions which I have tried to solve myself for the last couple f days but to no avail.

So here is the problem. All browsing is very unresponsive and choppy, both Internet and basic tasks such as scrolling through menus on desktop. I originally fixed this by going to System > Preferences > Appearence > Visual Effects=None. But Then I reinstalled ubuntu for other reasons (had to do with networing with a WIndows network) and now that solution does not fix the lags and unresponsiveness. One solution I found online said to install a driver by typing [FONT=Fixedsys][FONT=Courier New]

sudo apt-get install xserver-xorg-video-ati[/FONT].[/FONT]

 I did this, and it  appeared successful, but when I go to System > Administration > Hardware Drivers, it says "No proprietary drivers are in use on this system".



If you need info on my current graphics card I typed[FONT=Courier New] 

lspci | grep VGA[/FONT], 

and it returned

[FONT=Courier New]01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1[/FONT].

Not really sure if this is the info you need, like I said I am completely green to ubuntu. But any help would be appreciated.

---

### Post by mastablasta on 2010-11-30
if it all works what's the problem? :-)
 
You don't have proprietary drivers, because they don't make them anymore for your card. or better yet they don't support latest ubuntu with them. so don't try to install them as it can mess it all up.
 
so you are using opensource drivers instead. if it all works fine, then good for you. i use opensource too. and have no issues so far. some people have them, some people don't. seems to be a hit or miss.

---

### Post by |xem| on 2010-12-01
Maybe I was not clear. I installed the driver, but it did not solve the issue. There is still a huge lag. Thanks.

---

### Post by NCLI on 2010-12-01
> **|xem| said:**
> Maybe I was not clear. I installed the driver, but it did not solve the issue. There is still a huge lag. Thanks.
Hey Xem,

ATi no longer supports your card, so you can't use their driver. The driver you've installed only works for newer cards. What you're using now is a free driver provided by the Linux community. It's still pretty new, so it is slow for some cards.

Try pressing alt+F2, then enter "metacity --replace", and press enter.

If this doesn't work, you can try installing an older version of Ubuntu. The driver may be available for Ubuntu 8.04.

---

### Post by clhsharky on 2010-12-01
> There is still a huge lag.
Sounds like swap being used.

In terminal
```
top
```
if swap is being used your system will lag on slow hdd.
Add more memory or use lighter distro like Lubuntu.

You cannot compare XPs memory requirement to a modern OS that uses a compositor like Vista,Win7,or recent Ubuntu.

My full install of Ubuntu 10.10 with 4 windows open in chromium uses 800 MiB of memory with normal background services in use. 
I have a dedicated graphic card so I'm not sharing system memory with IGP chip.

See where I'm going with memory on modern OS.
Increasing system memory to 1 GiB will help your Ubuntu performance.

Lubuntu will do fine with 1/2 GiB if you don't add any high resource apps.

Sharky

---

### Post by |xem| on 2010-12-04
Thanks for the feedback NCLI and clhsharky.

@ NCLI:  tried metacity --replace but no luck. I think I will wait until I get my 1GB mem and see how it works.

 For what I am doing at the moment, 8.04 may be good enough. But the reason I am playing with Ubuntu in the first place is because I have plans to build a really fast machine for my research. I have heard nice things about linux, and I would prefer to work with the latest version, since this is what I would do if I do decide to go with linux on the new system. So, for that reason, I am just trying to get a feel of the OS before spending big $$ on the project. That whole topic requires a new thread so I wont ask any questions about  it here.

@ clhsharky: Same reason I will probably pass on the Lubuntu. I am not sure what the difference is from Ubuntu, but as I mentioned above, I want to get a good feel of Ubuntu, what it is compatible with, how to navigate throught it, etc. So as long as you think the memory upgrade will help then I will just wait for that (should have the new chips by the end of the month).

---

