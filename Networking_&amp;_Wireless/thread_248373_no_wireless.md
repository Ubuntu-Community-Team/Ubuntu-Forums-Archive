---
title: "no wireless???"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by nitrostealth on 2006-09-01
Ok, so here's the deal. I had ubuntu 6.06 working just fine earlier today. I had everything working in tip top shape. Then, I decided to run "faster-dapper" (if you havent heard of it- it's a script that removes/changes some settings around to make dapper run faster) I thought this sounded pretty neat, so i ran the script, and restarted like it said. But now the little wireless icon doesnt show up in the top right of the screen (ya know the little green signal icon?) the network icon shows up, but is black.
  The device that seems to be in use is called "Lo" ...I guess that means local?......::confused:  But anyway it used to be eth1 i think that was the wireless card.  It wont let me change the settings, or use eth1. ( I havent yet tried to see if a wired connection would work either)
  Anyway- I figured it was faster-dapper script that had screwed this up. So naturally I inserted the ubuntu live cd and sure enough, wireless WOULD NOT work from there either:!:  So I then reinstalled ubuntu and again it WOULD NOT show up. The strange thing about this is that BEFORE installing the faster-dapper script, wireless would show up right away on my laptop.....(its a toshiba satellite m35-s320) but now nothing at all. 
 So then i put windows xp (god i hate it) back on the laptop and sure enough wireless WORKED....So i put the ubuntu live cd in and NOTHING! 
  But in the network devices area or what ever its called, the wirelss card shows up, as well as the normal wired connection.  

Anyone know why it isnt connecting through wireless?? The card is internal. and it worked fine before running faster-dapper....could it have screwed something up in the bios??? Im not too familiar with that type of thing.

Any ideas, or help would be appreciated...thanx.  

PS i just registered today because my i forgot to activate my last account.....stupid me.

---

### Post by natrixgli on 2006-09-01
```

~$ sudo ifconfig eth1 up
~$ sudo iwconfig

```

this should show your wireless card. if your wireless card turns up, then you can configure it. If not, then repost. This is pretty basic stuff, have you tried searching the forum for a solution?

if your wireless card turns up, then you can configure it as follows: 

```

~$ iwconfig eth1 essid "youressid"
~$ iwconfig eth1 key "yourWEPkey"
~$ iwconfig eth1 channel 6 (or whichever channel your AP is on.)
~$ dhclient eth1

```


-n8

---

### Post by nitrostealth on 2006-09-01
Thanx for the reply n8!! I know it's basic stuff- but I thought  it might have been deeper than that. Guess I was wrong. Anyway, thanks again! I didnt even think about searching too much, but whenever i did, i could only find what i thought were unrelated problems. sorry about that.

---

