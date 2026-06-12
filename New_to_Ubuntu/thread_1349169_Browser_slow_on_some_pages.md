---
title: "Browser slow on some pages"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by randumnumber on 2009-12-08
I have a strange issue going on with my laptop 

ubuntu 9.10
firefox 3.5.5

I recently updated my system with a fresh install of 9.10 it came with firefox 3.5.5, the install went fine my wifi card was recognized all is good, minus one very strange issue.

When i browse to any site, even very lite sites like google firefox hangs at the "waiting for _____" the blank being whatever site im trying to goto, if i try to goto the site a few times it will finally load the site, but sometimes it is slow. sometimes it is fast, and sometimes the site loads just fine the very first try. this happens with all sites. ebaumsworld, youtube, textsfromlastnight. its so strange and i have no idea where to begin trying to fix the problem.

also after the site loads most of the content some things just dont load, like thumbnails of videos on youtube, and the working icon on the tab (the little circle that rotates) continues for about 2 minutes, if i leave the tab alone and wait about 5 minutes it will load the site. 
i tried using seamonkey to web browse, but it has the same problem.

when i was using 8.10 ubuntu it ran flawlessly. no issues. 

if anyone can help please email me @ [EMAIL="randumnumber@gmail.com"]randumnumber@gmail.com[/EMAIL] or respond here. thank you.

---

### Post by lovinglinux on 2009-12-08
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

If that doesn't fix the problem (most likely it will), then try [this](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/).

---

### Post by randumnumber on 2009-12-08
Thank you for the fast reply, I had already tried to switch off ipv6 but it still acts odd, for instance the second site you linked to me, will only load the top graphic i installed the toolbar to tell me how fast the site was loading and what not and it has stuck at "waiting for google.g.doubleclick.net" and just sits, waiting for something to happen, other sites it will load fully all content but continue to give me the swirlying icon on the tab as if it hasn't loaded all content. 

like i said before the same thing seems to happen when i use seamonkey, which has got me freaked that it might be the new 9.10 giving me trouble.

im going to work this guide you sent me from the top to the bottom hoping it will work somehow. thanks for sending it along.

p.s. i have also just noticed that the sites that take forever to load run at 0-10 kbp/s im on a broadband network and can run things such as transmission @ 500-800 kbp/s. its weird that i can request a site 2 or 3 times and the speed will be higher the 3rd time and the site will load. if i let a site sit long enough it will load in 4-5 minutes depending on the size.


any other advice?

-randum

---

### Post by dansar99 on 2009-12-08
There are other browsers like Opera,SeaMonkey and Google chrome. I just downloaded Chrome and I'm loving it. Dan

---

### Post by Sir Jasper on 2009-12-08
Hi,

Whilst this idea may not lead to a solution it may be of interest to you:

The Windows versions of 3.5.5 (portable from PortableApps or permanent) run really well using Wine 1.0.1. 

Personally, I would try that and if it works well for you; then whatever add-ons you have in your ´buntu version I would add one at a time and retest after each and every addition. Then, if the slowness is replicated, disable that add-on in your ´buntu version.

My regards

---

### Post by randumnumber on 2009-12-08
thanks for that idea, the problem began before i had ever installed any extensions - add-ons to the system, and just to test i uninstalled the 2 plugins i had and restarted...no fix.

right now ubuntu forums is still trying to load and says it is waiting for [www.google-analytics.com](www.google-analytics.com), but the speed is 58.45 kb/s its been waiting for google for 1 and a half minutes, is it possible that servers dont want to talk to my new setup is some way, dns or something? also when i type in ebaumsworld.com it doesnt load...but if i type in [www.ebaumsworld.com](www.ebaumsworld.com) it loads almost instantly. i can browse the site for a few minutes watch maybe 2 videos or so and after the 3rd or 4th it wont load any pages, it wont even go back when i hit the back botton, but if i type the url in again and refresh a few times the page will load again and i can browse again for 2-3 videos. 

once again, this is just a plain jane install of firefox on ubuntu, the only thing i did is install flashplayer when i first got it. so i could view flash.

---

### Post by randumnumber on 2009-12-08
> **dansar99 said:**
> There are other browsers like Opera,SeaMonkey and Google chrome. I just downloaded Chrome and I'm loving it. Dan


sea monkey does the same thing. i will try to use chrome.

i had 8.10 and it worked perfectly. i did a clean install formated and everything of 9.10 and its broken somehow.

---

### Post by Sir Jasper on 2009-12-08
Hi,

I may well be wrong but I think you have to use www when typing that address.

You could perhaps load gnome-system-monitor to check ram and cpu loads when it slows. There are far lighter options, but I find it easy read. 

My regards

---

### Post by randumnumber on 2009-12-08
ive check the lan cpu and mem load when this phenomenon happens, they are all normal, i am having the same issue on 2 other browsers, it must be a system issue, something network/ request related, i am going to disable ipv6 systemwide and see what happens

---

### Post by Sir Jasper on 2009-12-08
Hi,

I don´t have any more ideas so I will just wish you well.

My regards

---

### Post by the.phantom on 2009-12-08
i am not a expert but

> 58.45 kb/s if that is a lowercase "B" then that is at dialup speeds?

now you are having trouble with all the browsers
what about e-mail ?
have you checked the settings on your net connection?
have you ran any speed test on it"
say 
[http://www.dslreports.com/stest](http://www.dslreports.com/stest)

and try the java and flash and see if any difference?

tried to disable the java you have in firefox and see if java is hanging things?

---

### Post by randumnumber on 2009-12-08
**Last Result:**
Download Speed: **10270** kbps (1283.8 KB/sec transfer rate)
Upload Speed: **3093** kbps (386.6 KB/sec transfer rate)

these are the results of my speed test, i disabled java script in firefox, no changes. my gmail account works perfectly, except when it encounters the same problem i have with every other website, either the page request simply doesnt go though, or it gets halfway to almost all the way and stalls out and takes about 2 or 3 minutes to load. for example i just searched on google and it processed for 2 full minutes then pulled the search page up just fine.

im stumped

---

### Post by the.phantom on 2009-12-09
i am a lightweight on ubuntu
but one question that has not been asked

how much memory do you have and processor speed?
 i have a old "test box" and have noted that each new version of ubuntu slows it down. ( from 7.04 to 9.10)

the o9ld 7.10 would run ok ( acceptable) but with 9.10 it would just be too slow
if you have the accelerat3ed graphics with all the nice graphics, try and disable it

and look in "system manager" and see cpu usage and then look in the running processes and see who is working hard

---

### Post by randumnumber on 2009-12-13
I reverted back to 9.04 it runs flawlessly, i set my visuals to minimum when i was running 9.10, if that was the case it would have had an effect on the system as a whole not just on the web browser, i am now back to using firefox 3.0.15 on 9.04 and the system runs fine, ps i am running 1 gb ram 80gb harddrive 1.6ghz processor, its almost the same thing as one of those netbooks only its older, the os ran fine, i found only a few other people who had the same problem i had, and they said it was a constant slowing of their internet, mine was a request issue, and i still dont know what was wrong.

---

### Post by richard270384 on 2009-12-15
I am having a similar problem since upgrading to 9.10 - I had some problems and had to do a fresh install of 9.10.

I think my problem might be related to DNS issues. When I first try to load a website, firefox will show "Looking for xxxxxxx.com..." in the status bar for ages. Once I load a page from a website once, then that website loads fine until I leave idle for a while, and then it does the same thing.

Just like the guy who started this thread, it happens accross all programs - not just firefox.

Not sure if this gives anybody any ideas:

> richard@richards-laptop:~$ dig [www.internetmusic.tv](www.internetmusic.tv)

; <<>> DiG 9.6.1-P2 <<>> [www.internetmusic.tv](www.internetmusic.tv)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3815
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.internetmusic.tv](www.internetmusic.tv).		IN	A

;; ANSWER SECTION:
[www.internetmusic.tv](www.internetmusic.tv).	14400	IN	CNAME	internetmusic.tv.
internetmusic.tv.	13609	IN	A	89.238.165.210

;; Query time: 465 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Dec 15 16:28:33 2009
;; MSG SIZE  rcvd: 68

richard@richards-laptop:~$ dig [www.internetmusic.tv](www.internetmusic.tv)

; <<>> DiG 9.6.1-P2 <<>> [www.internetmusic.tv](www.internetmusic.tv)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26518
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.internetmusic.tv](www.internetmusic.tv).		IN	A

;; ANSWER SECTION:
[www.internetmusic.tv](www.internetmusic.tv).	14397	IN	CNAME	internetmusic.tv.
internetmusic.tv.	13606	IN	A	89.238.165.210

;; Query time: 35 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Dec 15 16:28:36 2009
;; MSG SIZE  rcvd: 68

richard@richards-laptop:~$ dig [www.internetmusic.tv](www.internetmusic.tv)

; <<>> DiG 9.6.1-P2 <<>> [www.internetmusic.tv](www.internetmusic.tv)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27877
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.internetmusic.tv](www.internetmusic.tv).		IN	A

;; ANSWER SECTION:
[www.internetmusic.tv](www.internetmusic.tv).	14400	IN	CNAME	internetmusic.tv.
internetmusic.tv.	14400	IN	A	89.238.165.210

;; Query time: 1760 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Dec 15 16:40:08 2009
;; MSG SIZE  rcvd: 68

richard@richards-laptop:~$ dig [www.internetmusic.tv](www.internetmusic.tv)

; <<>> DiG 9.6.1-P2 <<>> [www.internetmusic.tv](www.internetmusic.tv)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24958
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.internetmusic.tv](www.internetmusic.tv).		IN	A

;; ANSWER SECTION:
[www.internetmusic.tv](www.internetmusic.tv).	14392	IN	CNAME	internetmusic.tv.
internetmusic.tv.	14393	IN	A	89.238.165.210

;; Query time: 33 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Dec 15 16:40:15 2009
;; MSG SIZE  rcvd: 68


See how the first request takes 465 msec, the second request immediately after took 35 msec, and after waiting a few minutes it took 1760 msec?

I used that website as an example because the time differences are really bad on that website. With Google.com the first request takes about 60 msec and after that takes about 32 msecs.

I think this has to be an issue with Ubuntu because other computers on my network dont have this problem.

Any ideas?

---

### Post by randumnumber on 2010-08-01
Its been nearly a year, but i never did figure out what was wrong, i went back to 9.04 and have had no problems with it.

---

### Post by soldier1st on 2010-08-03
did you try changing dns servers to use opendns's? sometimes your isp's dns servers get overloaded and by switching to another one you may or may not gain some speed, also under the terminal type ping and type say [www.google.com](www.google.com) and report the output, if it is high ping we would need to know your connection type and speed as high ping=very slow and the lower it is the faster it is.

---

