---
title: "Help me find out what is randomly slowing down my system until it stops"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by nbj on 2009-04-05
I have had a strange problem ever since I installed kubuntu (8.10). Every now and then my PC suddenly begins to slow down and increasing HD activity until it eventually becomes unusably slow but still maintains the high disk activity. I can't e.g. change to a virtual console and log in to run top since whilst I get to the console and can type in my user name, I cannot type the password until it has timed out. I haven't been able to determine exactly when this happens and have no idea what causes it but it is extremely annoying since it effectively is a crash because the only way out of it is to press reset. Since I considered it possible that it was a database update or something that is going on even though I'm unaware of anything like that being installed, I once let it run for a long, long time but after one hour of continuous disk activity, I decided to reset (my biggest HD is 200 gb in two partitions).

In order to track it down I've - when I've remembered to - had one console with top running in it so that I can switch to it immediately if I notice this problem and see what is running and once it did happen under such circumstances but CPU activity wasn't high according to top and nothing seemed unusual but I didn't really know what to look for.

The disk activity makes me think that my system is doing something with swap but I don't know what since this has occurred when I've been engaged in a "normal" task for quite some time already - such as web browsing or playing a game.

So can anybody give me some advice how to track down what is causing this and stop it? Can it be some (practically neverending) database update that is running and that I'm unaware of (I have a typical desktop install but don't know if something is installed and scheduled to run by default)? Or can it be some swap use for some strange reason - I've got 1 GB RAM and 2 GB swap.

---

### Post by taqkavar on 2009-04-05
This is probably not the most elegant way to go about it, but you can always have the following running while you go about your business.

iotop -b -o > iotopLog.txt

iotop shows what is using the HDD, do the same for top

top -b -i > topLog.txtg

top also shows your swap usage at the very bottom. Wait until you crash, restart and review the last couple of lines in your logs, each iteration represents one second, so you would know roughly where to look. I'v never done this myself, so sorry in advance if it does not work.

---

### Post by |Porsche on 2009-04-05
Sounds like a memory leak. although, the ones I have experienced are usally pretty quick at halting my system. I use conky to monitor both process and ram usage and that is how I was able to see which application was causing it.

---

### Post by nbj on 2009-04-05
Now that I think about it, I have firefox open all the time and whilst a memory leak in firefox is unlikely I also have plugins like mplayer and flash and they don't close until firefox closes completely so it could be one of them.

---

### Post by rustutzman on 2009-04-05
I've got a couple of TB storage on pretty healthy system but Tracker(trackerd) would bring it to it's knees in much the way you mentioned. 

Check under sessions (ubuntu) and un-tic tracker and tracker applet and see if it still happens.

Russ

---

### Post by Net_Resident on 2009-04-05
Mal-designed Flash ads in Firefox can create this type of problem. Also, it helps to limit your history tracking in Firefox. I have mine down to five days because I do so much browsing.

---

### Post by nbj on 2009-04-06
I don't quite understand how to check that tracker(d), can you elaborate?

And about mal-designed flash ads: I use flashblock so I avoid most ads and only activate the flash content I'm interested in and would at least like to think that it isn't mal-designed because it's not ads or complete garbage but instead video or (very rarely) some game that I've been convinced to try.

---

### Post by Sef on 2009-04-06
In Konsole, run this command:

```
top
```It will show you what is running and how much.

> Now that I think about it, I have firefox open all the time and whilst a memory leak in firefox is unlikely I also have plugins like mplayer and flash and they don't close until firefox closes completely so it could be one of them.

FF 3.xx does not have memory problems like FF 2.xx.  However, one of your plugins could be the reason.  I would turn them off, then turn them on again one at a time and see when the problems occurs.

---

### Post by theozzlives on 2009-04-06
I had a simular prob on a low memory system, turned out my /swap was too big.

---

### Post by megamania on 2009-04-06
As weird as it may seem, the last time I had a similar problem it was a faulty hard disk cable.

---

### Post by Net_Resident on 2009-04-07
> **nbj said:**
> I don't quite understand how to check that tracker(d), can you elaborate?
In Firefox: Tools>Options. Then on the Privacy tab you will see the History section in the top section. By default it is 30 days. If you're a very heavy user like I am the history tracking can bog down Firefox in my experiences and I have a modern & fast system. So I reduced my tracking to a week.

---

### Post by nbj on 2009-04-07
It is this trackerd that I'd like to have better explained to me:

> **rustutzman said:**
> I've got a couple of TB storage on pretty healthy system but Tracker(trackerd) would bring it to it's knees in much the way you mentioned. 

Check under sessions (ubuntu) and un-tic tracker and tracker applet and see if it still happens.

Russ

I've begun to suspect that it is indeed something like that which causes it since it happened again and I noted the time - it was precisely 2.30 am it began.

@Sef Did you read my initial post? The one in which I state that I checked with top.

---

### Post by nbj on 2009-04-11
I have to bump this since the problem is unsolved and I'm really curious about that trackerd but hasn't figured it out yet.

---

### Post by nbj on 2009-04-21
Another bump.

---

### Post by skymera on 2009-04-21
System > Prefs > tracker

Disable it :) See if it helps

Also system > prefs > session
untick tracker etc

---

### Post by shadowlands on 2009-04-21
this answers here-- i think would solve my problem.  Can someone tell me what to do in plan English step by step so I can figure out what is causing my problem?

I think it is the foxfire thing because my problem started after i installed it.

---

### Post by laluz on 2009-04-21
> **shadowlands said:**
> this answers here-- i think would solve my problem.  Can someone tell me what to do in plan English step by step so I can figure out what is causing my problem?

I think it is the foxfire thing because my problem started after i installed it.
I think you will be better off, if you would learn how to do things that are described here yourself. Like for instance how to install flashblock add-on for firefox.

---

### Post by shadowlands on 2009-04-22
If I understood how to work the stuff and where to look. I would not be on this board. I think it would be better if folk who did not want to help others find a sight for those who know it all and have a site for folk without a clue but who are willing to learn if folk will take the time to explaine stuff in simple English. > **laluz said:**
> I think you will be better off, if you would learn how to do things that are described here yourself. Like for instance how to install flashblock add-on for firefox.

---

### Post by megamania on 2009-04-22
> **shadowlands said:**
> If I understood how to work the stuff and where to look. I would not be on this board. I think it would be better if folk who did not want to help others find a sight for those who know it all and have a site for folk without a clue but who are willing to learn if folk will take the time to explaine stuff in simple English.
I agree. People who have no time to help should have no time to say they have no time.

I'm not sure I can help you, but I'll try.
If you want to disable the tracker too, refer to the post by skymera. It should be enough to open the System menu, select the Preferences item, and then Tracker. When you're there, deselect it if it is activated.
Then, go again to the System menu, then Preferences, then Startup Applications (or something like that, my system is not in english). If there's a Tracker entry and it is checked, uncheck it.

Hope that helps. I'm not sure though, because tracker is not activated by default on my Jaunty install.

---

### Post by shadowlands on 2009-04-22
There is no tracker on mine. hummmm? and thank u for assisting me.:)

---

### Post by nbj on 2009-04-25
I must ask: Did you describe how to find it in Ubuntu? The thing is that I run Kubuntu (as I've said) and have no idea where to find that.

---

