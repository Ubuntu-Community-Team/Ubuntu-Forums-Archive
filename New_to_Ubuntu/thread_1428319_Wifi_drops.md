---
title: "Wifi drops"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by snippyv on 2010-03-12
Hello.

Im a total newbie.....only had Linux for 2 days!

I tried a USB boot of UNR and it worked like a charm.

I did a  Karmic install on a Advent 4211 (MSI U100 clone)and I am having problems with the wifi.

It connects....but it drops the wifi...it still shows a connection but it stops. 

I have read a few things on the Forum...Ive checked iwconfig and the connection drops to 2mbs.....its 54mbs when running normally.

It looks as tho I have a RTL 8187SE wifi ( but not 100% sure)

So..I sort of guess that that the RTL is supported in Linux....but how do I stop the wifi signal dropping?

I really really want to get on with Ubuntu...but dropping wifi is a big stumbling point.

Thanks

---

### Post by hhh on 2010-03-12
I don't know why this works, but it did for me... open a terminal and enter (change wlan0 to whatever your card is, you can find out by just entering iwconfig with nothing else)...
```
sudo iwconfig wlan0 rate 11M
```
You can set different rates, I've found that 11M gives me the fastest connection (speakeasy.net/speedtest is showing my download rate at almost 16Mbps on my 802.11bg adapter, again I have no idea what's going on, it just works for me). Some possible rates are listed here...
[http://compnetworking.about.com/od/wirelessfaqs/f/dynamicscaling.htm](http://compnetworking.about.com/od/wirelessfaqs/f/dynamicscaling.htm)

Since that worked for me using Network Manager and I didn't want to have to open a terminal and reset the rate after every login, I used the instructions in the second post of this thread I started...
[http://ubuntuforums.org/showthread.php?t=1370481](http://ubuntuforums.org/showthread.php?t=1370481)

Maybe someone with more technical knowledge can tell me why this works. Hope it works for you.

---

### Post by snippyv on 2010-03-15
Ive tried this but it does not help......it still drops.

It never did it under XP.

What else can I try???

I must admit that this is quite depressing.....I thought UNR was optimised for netbooks.

If this cannot be fixed.......can anyone suggest a replacement wifi card that is compatible with Ubuntu.....and can be purchased in the UK????

---

### Post by cloyd on 2010-03-15
I have a similar issue.  The wireless is in one end of the house.  Everything works fine, unless I am working in the _other_ end of the house. Half way through the house, things are OK, but in the _far _end of the house, the signal starts out at about 40%, then quickly drops to 20% or thereabouts. 

To make matters more confusing, things may work fine at 20, or they may just stop . . . can't load a new page.  Usually, it works fine for just surfing and reading web pages, like the forums, but if I want to do updates, or pay a bill, or download music or videos, I'd best move to the middle of the house. The signal may drop very low, 17, 10% or below. Things just do not work then, at all.  Sometimes, the network manager says I have 20-25% but things don't work.

If I am just surfing, I can get the signal back up by re-booting. Doesn't take long in Ubuntu like it does in windows. But the signal quickly drops. If I need to download, or view videos, I need to change location. This iwconfig command didn't work for me, but I may not have the right speed yet.  I'll play with it some more. This gives me something to think about.

I have wondered if I could somehow reset network manager w/o rebooting.  To click on it and disconnect and then reconnect does not work.

One more interesting thing. When my wife and I are travelling, and she is using an identical machine but with windows, in a hotel room, I do better with Ubuntu than she does with Vista.

---

### Post by cloyd on 2010-03-29
bump

I've noticed something really interesting. I have trouble with my wifi in the far end of the house, farthest away from the router. It works, then drops over a short time . . . can use it longer at night than daytime. May get 5 minutes, may get 30, then must reboot to get a strong signal.  

This is what I've noticed. If I go back and book on 2.6.31-15 kernal, it work better. . .  30 minutes or more w/o rebooting. The newer kernals work the worst.  Any ideas?  I regret that the oldest kernal I had ws 2.6.31-14, and I deleted it because my boot menu was scrolling off the screen. It may have been even better.  I do remember that wifi performance was better when I first started using Ubuntu back in November.

---

### Post by Directive 4 on 2010-03-29
i fixed the wifi signal to the far end of the house by putting the router in the focus of a old satellite dish and aiming it. 

maybe get a boost from ~20% to ~40%

but alias, have no info for the op...

---

### Post by clancymf on 2010-03-29
Im not at my UNR but i beleive the command to reboot networking is:

sudo /etc/init.d/networking restart

something like that.

I have a rather good sized house and my wifi signal in the basement.  I purchased a linksys router for about $20 (from newegg : USA based)and installed dd-wrt on it and turned it into a wireless repeater.  Fixed my range issue.

---

