---
title: "HP tx2 Tablet PC concerns."
date: 2009-03-07
forum: New to Ubuntu
---

### Post by tsao on 2009-03-07
Hello all, I don't know much about linux but I'd like to install it on my new tx2 laptop. I have a few concerns though. First, I read that most linux don't support the touch screen or have the drivers. Also, I've heard of people having problems with the finger print reader and features like that. I was just wondering what version or type of linux will get me up and running the easiest way possible. I know you can add codes or something to set up hardware?? but I have no clue how to do that or any other settings stuff except for actually installing the OS. Any help is appreciated, Thanksss:D

---

### Post by yeats on 2009-03-07
I would recommend doing some serious research before embarking on this.

> First, I read that most linux don't support the touch screen or have the drivers. Also, I've heard of people having problems with the finger print reader and features like that.

There are sites on the web that have hardware compatibility reports (Google will help here).  However, one glance at the posts on these forums should tell that things do not always "just work."  I would recommend running the Ubuntu Live CD to test your hardware - you might be surprise at what *does* work.

> I was just wondering what version or type of linux will get me up and running the easiest way possible.

Not surprisingly, I will recommend Ubuntu.  But I want to caution you that what I consider "easy" may not be the case for you. Linux is entirely different from Windows in most respects.  I think you should do some reading and research, and burn yourself some Live CDs to test different Linux distributions.  You can also use VirtualBox ([http://www.virtualbox.org/]("http://www.virtualbox.org/")) to install Ubuntu or some other Linux to see what you like and what you can figure out.

> I know you can add codes or something to set up hardware?? but I have no clue how to do that or any other settings stuff except for actually installing the OS. Any help is appreciated, Thanksss

Not sure what you mean about "codes"... there are certain types of hardware that you have to configure specially though.  I would run Live CDs to see what works, then see how involved the solutions are, then make my decision about installing on my hard drive.

In any case - good luck, and welcome to the forums!

---

### Post by Favux on 2009-03-07
Hi tsao,

When you say "tx2" do you mean a TX2z or do you mean one of the earlier HP TX models like the TX2000 or TX2500?  It makes some difference because the TX2z has the N-trig digitizer rather than a Wacom one.

That said you can get just about everything set up including your tablet features in Intrepid (8.10) with a little work.  With the N-trig support has only been recently added for it to linuxwacom.

By "codes" I assume you mean commands in a terminal.  There are good HOW TO's that walk you through that sort of thing.

Support promises to be better for N-trig in Jaunty as the newer kernel has more support for N-trig.

Unfortunately the fingerprint reader is one of the few things difficult to setup.

---

### Post by tsao on 2009-03-07
> **Favux said:**
> Hi tsao,

When you say "tx2" do you mean a TX2z or do you mean one of the earlier HP TX models like the TX2000 or TX2500?  It makes some difference because the TX2z has the N-trig digitizer rather than a Wacom one.

That said you can get just about everything set up including your tablet features in Intrepid (8.10) with a little work.  With the N-trig support has only been recently added for it to linuxwacom.

By "codes" I assume you mean commands in a terminal.  There are good HOW TO's that walk you through that sort of thing.

Support promises to be better for N-trig in Jaunty as the newer kernel has more support for N-trig.

Unfortunately the fingerprint reader is one of the few things difficult to setup.

I have the newest tx2, not the tx 2500 or anything. It's the one that supports multiple touch. Sorry you kind of lost me with Intrepid and Jaunty, not familiar with what those mean.

---

### Post by Favux on 2009-03-07
Hi again tsao,

By the latest with multi-touch it should then be the TX2z with the N-trig digitizer.  You should confirm that.  On the bottom of the laptop should be a plate with the model number, etc.

Intrepid Ibex (8.10) is the current release of Ubuntu.  Jaunty Jackalope (9.04) is the upcoming release.  The numbers are the year and the month of the release, so 8.10 is 2008 and October.

To get your tablet working you will have to use the CLI (command line interface) some but like I said there are some good threads and HOW TO's, so once you get over the "hump" it isn't that hard.

---

### Post by ARXD on 2009-03-22
Hi
I have the HP TouchSmart TX2-1020CA Tablet. 
(and yes, TX2 is the model name, no TX2z or tx2000, tx2500 etc)
I got mine from Best Buy:
[http://www.bestbuy.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0926INGFS10118242&catid=20354](http://www.bestbuy.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0926INGFS10118242&catid=20354)

I can't even install Ubuntu on it...  [COLOR="Red"](*Solved)[/COLOR]
The laptop always get stuck in the installing part. 
for more info about my problem see this thread:
[http://ubuntuforums.org/showthread.php?t=1103304](http://ubuntuforums.org/showthread.php?t=1103304)
](*,)

[COLOR="Red"]*edit:
From some reason the V8.10 live cd won't run on my laptop.
**But!!!**
I manage to install Ubuntu using the **V8.04 live cd** :)
everything is working great![/COLOR]

---

### Post by leonardo_neo on 2009-03-22
I was planning to buy this comp, but before buying I read the customers reviews, and one of the customer was complaining that this machine was not compatible with Linux and it has some issues.

At that very moment I abandoned the idea to buy this machine.

But since you have already bought it, you should of course give the Live CD a shot, and there is of course some way to solve the issues.

Best of luck.

---

### Post by gorg0th on 2009-07-07
> **leonardo_neo said:**
> I was planning to buy this comp, but before buying I read the customers reviews, and one of the customer was complaining that this machine was not compatible with Linux and it has some issues.

At that very moment I abandoned the idea to buy this machine.

But since you have already bought it, you should of course give the Live CD a shot, and there is of course some way to solve the issues.

Best of luck.

I have a tx2 running Jaunty right this moment and I've gotten just about everything worked out using this posting:
[http://ubuntuforums.org/showthread.php?t=1038898&highlight=jaunty+tx2](http://ubuntuforums.org/showthread.php?t=1038898&highlight=jaunty+tx2)

It's soo worth it, the machine is fast and lovely and it's tablet features are well supported once you've gone through the proper steps...In every case good luck!

~gorg0th

---

