---
title: "Wireless cards that DO HAVE DRIVERS ????"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Greg Mueller on 2008-01-20
Are there any brands of Wireless card that do come with Ubuntu drivers?
If there are I will buy one and reward that company with my purchasing dollars.

Maybe that would encourage other companies to do the same.

---

### Post by innocentson67 on 2008-01-20
I have a Broadcom 4318 that works great....I installed it in my laptop then after the Ubuntu updates went to system-administration-restricted drivers manager and enabled it.

---

### Post by Greg Mueller on 2008-01-20
Well what I meant was, ones that come with a disk that you put in the computer and it works.
No BSing around

<Put in card>
<Put in disk>
it works

That's what I want as messing with wireless cards is not my hobby. I just want to use one to get info from the internet.

If I am grouchy sounding it is because I am grouchy because of my wireless card, sorry

---

### Post by bus_ter on 2008-01-20
Anything with a Prism chipset?

Look at list of compatible cards at the top of the forum page. Look for ones that have a tick of 'work out the box'. This means Linux has unbuilt drivers for the card and you don't have to mess around downloading Windows drivers (and using ndiswrpper) or trying to find firmware etc

---

### Post by Greg Mueller on 2008-01-20
Looking at the list I see that my card (Linksys WMP54G) works out of the box. Mine don't
I am using 7.1
As far as I can tell it is V4

> Detected in Network Settings as ra0 and started working after WAP details were input

Where do I find WAP details?

---

### Post by Orian.au on 2008-01-20
As I know WAP settings is a type of connection, it's name, and key. (All this you chose yourself when you set you wireless connection)

---

### Post by Greg Mueller on 2008-01-20
Seems like some kind of game...

No one seems to talk in any terms other than secret codes. 
No instructions anywhere that are complete. Always esoteric mumbo jumbo that you have to go find definitions for. 
WPA
essid 
etc etc etc

no wonder windoz is so popular. It just works

---

### Post by Orian.au on 2008-01-20
> **Greg Mueller said:**
> Seems like some kind of game...

no wonder windoz is so popular. It just works

Well. After  days of trying to connect to the wireless internet with no success, I'm also starting to think so.

But actually, to work in windows you also need all this WPA, essid, data encryption etc, etc,etc.

---

### Post by Greg Mueller on 2008-01-20
I finally got it to work almost by accident.
I rebooted to my installed system (7.10)
I right clicked on the two monitors icon in the task bar and unchecked the "Enable Wireless" then rechecked it. It started working

Or the secret explanation

&@(!~^$%##@)*%#!@$^*)!!!!!

---

### Post by Lord Illidan on 2008-01-20
> **Greg Mueller said:**
> Seems like some kind of game...

No one seems to talk in any terms other than secret codes. 
No instructions anywhere that are complete. Always esoteric mumbo jumbo that you have to go find definitions for. 
WPA
essid 
etc etc etc

no wonder windoz is so popular. It just works

If you're lazy, and can't be bothered, don't blame us.
As for the card, my laptop intel 3945 worked out of the box with Ubuntu, too.

---

### Post by Greg Mueller on 2008-01-20
Obviously I am not lazy as I have been at this for more time than I should have had to been.
It's just that I see no reason to speak cryptically when you can speak plainly. After all it is the job of the speaker to make his thoughts known to the listeners. (basic speech class). 

Thanks for the antagonistic thoughts though.

---

### Post by Lord Illidan on 2008-01-20
I'm sorry I came off that way. But, yes, I stand to what I said, when I refer to this post : 
> Seems like some kind of game...

No one seems to talk in any terms other than secret codes. 
No instructions anywhere that are complete. Always esoteric mumbo jumbo that you have to go find definitions for. 
WPA
essid 
etc etc etc

no wonder windoz is so popular. It just works
Just because you have to go learn something doesn't mean that Ubuntu just doesn't work. Anyway, glad you got your card working.

---

### Post by clsgis on 2008-01-20
My generic USB wireless-G dongle from an Ebay dealer in Hong Kong worked right out of the blister pack.  It said works with Linux on the blister card, but I didn't have to use the CD.  Later I looked there and it did indeed come with Linux drivers compiled for the 2.6 kernel.

The device has no name.  No manufacturer.  They don't want you contacting them.  I guess the Ebay dealer is supposed to support it.  Har har har har.

Consumer electronics come with CDs for MS-Windows because they could not sell any without them.  That is one of the forces which keep the monopoly strong.  Economists call it "network effects."  Consumer electronics hardly ever come with Linux support because so few consumers ask for it that it doesn't pay, yet, to do it.  

But that is changing.  You can help it change by relaxing.  Just accept the situation.  Linux will never be problem free.  Nor will MS-Windoze or Mac OS.  All we can do is trade one set of problems for another.  And we advocates of software freedom believe our set is more manageable over the long run.

Wireless client stuff is especially bad.  The models change all the time.  The designs change with no change in model number.  The manufacturers will never tell you what chip they used.  My advice: don't waste time looking for a Linux driver.  If you are lucky (research notwithstanding) the thing will just work.  If not, install the ndiswrapper package and have it absorb the Windows XP driver off the CD that came with the device.  It's easier.

Professional networking gear typically works with Linux *before* it works with Windoze.

I sure wish there were an ndiswrapper for gutless modems.  I finally broke down and bought the Linuxant driver for that.

---

### Post by clsgis on 2008-01-20
> **Greg Mueller said:**
> Obviously I am not lazy as I have been at this for more time than I should have had to been.
It's just that I see no reason to speak cryptically when you can speak plainly. After all it is the job of the speaker to make his thoughts known to the listeners. (basic speech class). 

That's the Achilles heel of truly free software.  The people who write the code are the ***only*** people who don't need good instructions about how to use it.  Most of them don't speak English or don't write it very well or just don't like writing.

Lord grant me the wisdom to change what I can and accept what I can't.  Pointing out the problem will not motivate anyone to write better.  You'll be happier if you learn to work with the community.  Never whine.  Always state your problem as if you're the only one who's ever seen it, even if you think it *must* be afflicting everyone.  Give us enought detail to reproduce the problem.  Take time out and read Eric Raymond's great essay "[How to Ask Questions the Smart Way]("http://catb.org/~esr/faqs/smart-questions.html")."

---

### Post by Greg Mueller on 2008-01-21
Gee thanks for the lecture

---

