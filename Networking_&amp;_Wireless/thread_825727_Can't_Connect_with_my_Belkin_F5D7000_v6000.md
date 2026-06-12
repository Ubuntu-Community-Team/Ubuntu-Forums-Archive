---
title: "Can't Connect with my Belkin F5D7000 v6000"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by adamtheestimator on 2008-06-11
I can't say that I have tried it all, because if I had, it would probably be fixed, but I have searched and, apparently, 
no one has the exact version that I do.  
I have followed a well laid-out instruction to set up in Terminal.  
I have totally flushed my Xubuntu and reloaded after getting only one response on my last plea for help. [-o< 

[ see my post: *Noob F5D7000 installation woes*]("http://ubuntuforums.org/showthread.php?t=761098")

I don't know what to do.  
I really want to get into Linux via Xubuntu and possibly dump my Vista from my laptop and use Ubuntu, 
but without wireless, that will never happen.

_Here's what I am seeing:_
My Belkin F5D7000 version 6000 is recognized by the system.
My SSID is recognized by my wireless card.
I have no security set up on my router to make it "easy". :rolleyes:
In the top right hand corner I have an X through my connection.
When I right click there, it shows my SSID with a selection circle next to it.
When I click it - I get a "working" motion icon, then back to the no connection icon.

I would appreciate some help.  I will not give up on this, and use Bill's crap forever, 
but without help, it will take me a lot longer than the few WEEKS I have needlessly 
wasted on trying to get this wireless card up and connected.

BTW I am at work, 8-[ :-$ doing this from memory, so I can't give you any Terminal command lists, 
but ask anyway and I will get them for you when I get home.
Thanks in advance for your help.

---

### Post by chewearn on 2008-06-11
Since nobody has replied, I thought I make one.  More as moral support than anything else.  To be frank, I'm a noob when it comes to wireless.  I'm lucky because two of my wireless set-ups worked out of box, without fiddling.

In your other threads, you mentioned following a howto by Kevdog, but you failed to include a link.  I thought I mentioned it, since it might be helpful to trace your troubleshooting thus far.

Secondly, about 50% of people think wicd is better than the ubuntu's default network manager.  You could investigate on replacing the nm with wicd.

Finally, this turns up after some google-fu 
[http://ubuntuforums.org/showthread.php?t=617297](http://ubuntuforums.org/showthread.php?t=617297)

What's the difference between v6000 and v7000?

---

### Post by adamtheestimator on 2008-06-12
Thanks for the quick reply, Astala!

I haven't researched the differences between the v6000 and the v7000
past the NDISwrapper website list of cards supported.  
When doing so, I got all excited as I went down the list..."rev2"..."v5000"..."v7000uk"...
...huh?...where's my v6000?
Story of my life.

Anyway, I will look into WCID, though I have no idea what it is.
Thanks for the new direction to look in!

[Here's the link to Kevdog's 'how to' for your perusal.]("http://ubuntuforums.org/showthread.php?t=574511") 

Back to work, now... :-|

---

### Post by adamtheestimator on 2008-06-14
Ok. So, I tried WICD.  I just knew it would be my savior!  But alas, not so. :sad:

Now that I have WICD installed and Network Manager is gone, I can connect with my wired connection, but it doesn't recognize ANY wireless signals.  On top of that, the program  s e e m s  t o  b e  r u n n i n g  i n  s l o w - m o t i o n . . . :shock:
I am looking at the screen right now and it is hung up on the main WICD screen...and has been for about 15 minutes... ](*,)

H E L P .

---

### Post by adamtheestimator on 2008-06-14
Just you can see what I see...


**lshw -C network**

*-network [COLOR="Red"]**DISABLED**[/COLOR]    
description: Wireless interface
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: b
bus info: pci@0000:00:0a.0
logical name: wmaster0
version: 00
serial: 00:11:50:db:ee:f7
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g


**iwconfig**

lo no wireless extentions

wmaster0 no wireless extentions

wlan0 IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Retry min limit:7 RTS trh: off Fragment thr=2346 B
Link Quality:0 Signal Level:0 Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


**lspci -n**

00:00.0 0600: 1106:0598 (rev 04)
00:01.0 0604: 1106:8598
00:07.0 0601: 1106:0686 (rev 15)
00:07.1 0101: 1106:0571 (rev 06)
00:07.2 0c03: 1106:3038 (rev 06)
00:07.4 0600: 1106:3057 (rev 10)
00:08.0 0300: 1002:4755 (rev 9a)
00:0a.0 0280: 1814:0301


Alrighty, then.  Who can tell me why my network is DISABLED
and how do I alleviate that?

Step right up!  Who's first?

<<crickets chirping...>>  :-s

---

### Post by adamtheestimator on 2008-06-23
...anyone?...

...anyone?...

...Bueller?...

:-\"

---

### Post by adamtheestimator on 2008-07-06
Okee-dokee.
I guess I am basically going through this alone (except for your suggestion AstalaVista - thanks), and this is my online diary so that when someone finds me with my face on the keyboard, dead - they will know what I have been going through, and understand why I gave up the ghost.
So...
I have tried NDISwrapper - no dice.
I have tried it without NDISwrapper - no dice.
I have tried WICD - no dice.

What now?

I think I am going to try to re-install the Network Manager (since I had to get rid of it to install WICD) and do it all again.  I have a hard head, and butting it against this thick Xubuntu wall hurts, but it will break first... ](*,)

Again, I welcome any ideas...  _*** A N Y  ideas...***_

---

### Post by xboxmods3077 on 2008-07-06
Hi. I was browsing here because I too, have a problem with my wireless networking. I saw your post and figured I would give some insight. First, If I remember correctly, the wireless device you are using is the belkin USB wireless adapter, True? Ok. I haven't backtracked all over the internet to read all your progress so I will post covering a few scenarios. I owned one of those belkin USB devices, the v5000 and the v4000. At the time, I was running ubuntu gutsy.(laptop) The v5000 did not work for me. So then I got ahold of a v4000, which worked (chipsets were changed), for about 2 days. So I then plugged the belkin into my desktop, (windows XP). Worked, but very intermittently. Long story short. The belkin USB thing is junk. Soon you will have to replace it anyway as they have died on 3 people I know. Why else would they change chipsets like, 7 times in 2 years? Windows don't like it much, and ubuntu hates it. Scenario 1: If your computer is a laptop, bite the bullet, spend a few buck on amazon like I did and get a minipci card. It solved all my problems. I got lucky, I found one on amazon ($24.99) and it turns out, It was a atheros chipset 108mbps wireless G!! Awesome card for ubuntu and windows (my laptop dual boots either), and way better then that shoddy belkin. Scenario 2: If you computer is a desktop, It's pretty much the same idea, Look around for a cheap hardware alternative but try to stick to KNOWN brands, linksys, netgear, companies like that. I know, ya walk into walmart looking for a quik fix and there it is. You can't resist the price. Belkin, cheap, easy, USB. NOT!! They SUCK!! Any operating system you ever use will become incapable of error you if you get rid of it.

Just my 2 cents

---

### Post by emi41142 on 2008-07-09
I have a belkin f5d7000 v7000 or some such thing I can´t remember at the moment.  On the ndiswrapper website pages I read that the driver that came with the card would not work and it gave a suggestion which I then tried, long story short it worked but momentarily froze the computer every 5 seconds or so, which obviously is not an applicable solution.  Though the ndiswrapper site said that my drivers would not work I tried them anyways.  They do work, I still could not connect with network manager, which imo is a crap.  Now this was back when I was running regular ubuntu, not xbuntu and it worked great displayed ok etc.  I switched to xubuntu because ubuntu was so slow, and did exactly what I did with ubuntu.  In xubuntu wicd appears to freeze, b ut I noticed that both the orange light signal light and the green connected light were lit, so I just closed wicd and voilá I am indeed connected.  So I would ask if you had gone ahead and closed the apparently frozen wicd and pulled up a browser page.  I read about this not showing connected error in a search I did on the forums awhile back and it may be a common issue.  I also would reccomend that if you have not tried the drivers the card came with that you do, mine do indeed work, if a bit wonky.  just as a side note, I have also made it work this way in kubuntu, yes I know OS ADD.

---

### Post by adamtheestimator on 2008-07-12
Thanks for your respective replies *xbox* and *emi*!  My Belkin isn't a USB adapter, though, its a pci card.  And I have already tried replacing my Belkin F5D8000 pre-N card (which had NO support) with the F5D7000 v6000 wireless-G card (which I gathered, from the wiki site, to be out-of-the-box usuable) - of course, if it had been, I wouldn't have this wonderfull "blog".  

I am in the middle of my 4th re-install of Xubuntu, wiping everything clean and starting completely over...
Here we go again...

---

### Post by emi41142 on 2008-07-13
I hope that a fresh new install will help some, I think I have gone through about 5 of them at this point. This is my first foray into linux and I´m trying to learn how to do things by the seat of my pants so needless to say I am alternately breaking things and making them work.  I do want to mention that in xubuntu there is no tray icon for wicd.  there is apparently a way to get it up there but the only instructions I found to do so, require you use the command line and were for an earlier version, I have no idea how to adapt them for the current version, if I figure it out I will post though.  I just wanted to let you know that not having the icon doesn´t mean it isn´t working, it seems to still run in the background even without it displaying.  I wish I had some fresh ideas for you to try, but I hope the moral support is at least a help.  I will mention that it took me 15 days of trying to do things I didn´t understand to get the wireless working, and I would recommend that you download the graphical interface for ndiswrapper, that was a big help for me, I tried to use it in the command line with very little success.  I´m keeping my fingers crossed for you, it´s a challenge but for me at least it was worth it.

Emi

---

### Post by ubume2 on 2008-07-13
I have an F5D7050 USB adapter from Belkin. I have got it working great. Not exactly "out of the box", though.

I discovered when I went through the ndiswrapper routine (and failing to get a connection), that I didn't need to go through that process at all.
Your mileage may be different, however.

You might read Wieman01's howto. Especially, pay attention to the section
Setting the Wireless to Connect at Boot
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I didn't have to blacklist anything to get mine going.

---

### Post by emi41142 on 2008-07-16
I said before that if I figured out how to get the tray icon for wicd to appear I would post it, so just in case you do decide to use wicd, I found in their faq the instructions for getting the tray icon to appear without needing to use the command line.  It can be found at [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)  I have tried this on my laptop and so far it is working, I do have to say it is nice to finally have a visual on the screen that shows my wireless is up and running.  Also just to update on my own experience, and I´m not really sure why (maybe an update fixed it?) wicd is no longer hanging up when I connect to my wireless network, it´s now running flawlessly.


Good Luck
Emi

---

