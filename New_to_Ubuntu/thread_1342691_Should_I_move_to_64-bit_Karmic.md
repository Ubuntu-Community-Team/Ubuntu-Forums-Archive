---
title: "Should I move to 64-bit Karmic?"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by bilalakhtar on 2009-12-01
I have been using Ubuntu for the last 9 months, and have used Intrepid, Jaunty and now using Karmic (all 32-bit). My CPU and all other hardware support 64-bit, so I was thinking whether I should make the move or not.
First of all, my computer is configured in dual-boot with Windoze XP 32bit (iHate Windows, but my family members use it) using GRUB as bootloader. So, if I install ubuntu 64bit, will it affect Windoze XP?
Second question:-RAM. I have a 1GB RAM in my machine. There are two slots for RAM and the second one is empty. So, should I make it 2GB or 3GB? (I wont like to make it 4gb as it would involve removing the 1GB module).RAM is a bit expensive over here in Saudi Arabia. I multitask a bit, synaptic keeps running in the background along with openoffice and empathy when I am browsing with Firefox. 
Please recommend me the amount of RAM I should have in my PC.:popcorn:

---

### Post by YosefKaro on 2009-12-01
I have read it elsewhere in the forums that one should not use 64-bit unless they have 4gb of RAM.  That is why I stay on 32-bit.

-Yos

---

### Post by bilalakhtar on 2009-12-01
> **YosefKaro said:**
> I have read it elsewhere in the forums that one should not use 64-bit unless they have 4gb of RAM.  That is why I stay on 32-bit.

-Yos

Well, even I read on some forum that 2GB RAM is enough for 64bit. On some other thread I also read that 4GB RAM is not necessary, its just that 64bit OS can utilize 4GB RAM.

---

### Post by Sef on 2009-12-01
> I have read it elsewhere in the forums that one should not use 64-bit unless they have 4gb of RAM. That is why I stay on 32-bit.

Not correct.

> Well, even I read on some forum that 2GB RAM is enough for 64bit. On some other thread I also read that 4GB RAM is not necessary, its just that 64bit OS can utilize 4GB RAM.

32-bit can only use about 3.2 gb ram no matter how much is installed.  

As for 64-bit, if you only do word processing, surfing, and other nonintensive cpu uses then you won't see much of a difference.  If you do things that are cpu intensive then it can make a difference.  For example, i had a friend who would come over to download his photos to a usb stick because my machine with 2 gb ram could download his 400 photos in about 20 minutes.

---

### Post by SteelCore on 2009-12-01
Salaams Bilalakhtar,

It is very unlikely that a dual boot of xp with Karmic would cause any problems although I haven't personally tried it. Starting with 9.10 I stopped dual booting and have my very rarely needed xp in VirtaulBox inside Ubuntu which is really much neater as you can have both OSes running at the same time. I even have a friend who told me that running xp virtually performs better than a dual boot. Make sure you back up ur xp before trying 64 just in case. In terms of processing the 64 definitely outperforms the 32 but there are some glitches such as the not so good Adobe flash support, at least in my case. One benefit of 64 is that it can see RAMs in excess of around 3.2 Gb which is the limit for 32bit operating systems.
As for the amount of RAM, it is really up to u. You're likely to see performance improvements if you upgrade to 2 or 3 but that is optional. Ubuntu can run with even less than 1 Gb of RAM.

---

### Post by daveisearly on 2009-12-01
I have just moved over from Fedora - where I ran 64-bit versions for a while.  I decided to install the 32-bit version of Karmic for three reasons:
1.I hadn't found any noticeable performance improvement on the 64-bit version
2. The 64-bit architecture is more complex, as it has to run 32-bit libraries in parallel for some applications - e.g. so you end up with both /usr/lib and /usr/lib64
3. 64-bit applications have not been as widely available or well supported as 32-bit (although this is improving over time). There are some 3rd party applications that are not available for or well-configured for a linux 64-bit system - such as Google Gears (not available) and Adobe Flash (beta version for 64 bit is available and requires some custom configuration to run properly).

There may be some advantages to 64-bit if you are running extremely large jobs regularly - such as working with high-res video or querying terabyte data sets.  Otherwise, I would advise staying with 32 bit.

---

### Post by megamania on 2009-12-01
I use Karmic 64-bit and have no problems with it.

---

### Post by expxe on 2009-12-01
> **megamania said:**
> I use Karmic 64-bit and have no problems with it.

same

i recommend 64 bit, and if you have more than 4gb of ram you will need to

---

### Post by pi4r0n on 2009-12-01
I used to had Ubuntu 9.10 32bit but as every one had only 3.2GB of RAM :( so I installed **linux-generic-pae** module gave me 4GB and do you know what. I am really happy with it and don't have any issues :):):)

---

### Post by benmoran on 2009-12-01
I've used 64-bit exclusively for about a year and a half. No problems. I have 2-gigs of ram, and that is plenty.

---

### Post by Kevbert on 2009-12-01
If you're using 32 bit Karmic with no problems I suggest you stay with it as you'll see very little difference in 64 bit (with your current amount of memory).  If you decide to increase the RAM to 4Gb then install 64 bit Karmic.

---

### Post by simonjk on 2009-12-01
I think it depends on the availibility of 64Bit Drivers for your computer and all it's hardware,the main sticking point is that there are not that many drivers availible,and that is because manufacturers aren't willing to put money and time into developing 64 bit drivers because the 64 bit platform isn't that popular only because of a lack of drivers,bit of a chicken and egg scenario,and trying to get drivers for Ubuntu linux is frustrating in the least.


I just wish that there was a global coalition of people to sort this situation out once and for all.



Just been trying to find a suitable Linux driver for my Basecom HS-USB Modem 9000 that will enable it to work in Ubuntu,and I've had very little success so far,if anyone can suggest anything to help me out,that would be much apreciated,thanks in advance.

---

### Post by howefield on 2009-12-01
> **bilalakhtar said:**
> My CPU and all other hardware support 64-bit, so I was thinking whether I should make the move or not.

Rather than try to come up with a reason to use 64 bit, I think the question these days is do you have a reason NOT to use 64 bit. There used to be a section on these forums specifically for 64 bit related questions, it was recently retired. 64 bit is now considered "business as usual", and not the "special case" it previously was. That says something for the maturity of 64 bit, for me, at least.

> So, if I install ubuntu 64bit, will it affect Windoze XP?

No, you could even triple boot if you wanted.

> So, should I make it 2GB or 3GB?

Generally, more is better. Having said that, 1 gig should comfortably deal with your needs, but more memory would open your computer up to further possibilities like virtualisation, as well as probably, increased performance.

---

### Post by Spiritof76 on 2009-12-01
Although the topic has been well covered in this thread, there are a few things worth noting. 

The 32 bit system can only address 4 gigs of mmemory without PAE.  The OP  doesn't have any intention of increasing his memory usage to more than 3 gigs, and it sounds likely he will be happy with 2 gigs.

While most apps and extentions have been been ported over to 64, some have not. If one would like the most trouble free and easy user experience 32 bit is strongly advised. using 643  bit will complicate installations in the search for drivers and extentions. running 64 bit will not make running a desktop easier, but may very well make things difficult.  

32 bit is not likely to become unsupported in a very long time.

2 or 3 gig is a lot of memory for most casual usage.   

check out <system> 
32 bit ?? It works 
64 bit??  it works with a little more tweaking, and a few less apps and drivers and with more memory than many of us will never have.

---

### Post by Grenage on 2009-12-01
> 32-bit can only use about 3.2 gb ram no matter how much is installed.

That isn't true.  The theoretical max is 4GB, but depending on hardware (and it's address allocation), you must also factor in video memory.  Your usable RAM can be anywhere from 3.2 to 3.8 on a 32 bit OS.

AMD64 is great if you have 4GB+, if you have less then stick with 32.  The speed increase is minimum (usually none), and there are some kinks that need ironing out.

---

### Post by 3rdalbum on 2009-12-01
> **simonjk said:**
> I think it depends on the availibility of 64Bit Drivers for your computer and all it's hardware,the main sticking point is that there are not that many drivers availible,and that is because manufacturers aren't willing to put money and time into developing 64 bit drivers because the 64 bit platform isn't that popular only because of a lack of drivers,bit of a chicken and egg scenario,and trying to get drivers for Ubuntu linux is frustrating in the least.

All drivers in the Linux kernel must compile and work on eleven different CPU architectures; they are very well tested on 64-bit. So your argument only works when you're talking about proprietary drivers (and even then, a lot of them come in 64-bit versions). Or if you're talking about Windows.

My father uses 64-bit Jaunty in dual-boot with XP 32-bit, and his computer only has 1.25 GiB of RAM.

---

### Post by anaconda on 2009-12-01
> **Kevbert said:**
> If you're using 32 bit Karmic with no problems I suggest you stay with it as you'll see very little difference in 64 bit (with your current amount of memory).  If you decide to increase the RAM to 4Gb then install 64 bit Karmic.

I agree with Kevbert :D

If you have already installed a 32-bit system, and it works well, then why would you want to change to 64-bit. It would only work about the same.  An hour of "work" with no benefit.

But the next time you install ubuntu (next version) try 64-bit version.

And 1GB of RAM is enough for your purposes. But RAM is so cheap, that you can buy more  if you like.
I have 512MB of ram, and it has been enough so far... Swap is used only very rarely, and because my machine is quite old I don't want to spend any money on it. I wont buy more ram to it. I would rather buy a new machine..

And installing 64-bit linux wont affect your windows in any way.. (unless you screw up and install it on top of windows, and overwrite it.)

---

### Post by insane_alien on 2009-12-01
if what you have just now works fine thne just leave it.

if you ever have to reinstall it though, might as well go for 64-bit.

there really isn't any reason against 64-bit now. all the programs are stable(and you can install the 32-bit versions of software on the 64-bit OS if you still don't believe everyone else.

the only viable reason i can think of for not going 64-bit in software is that you're still using some legacy 32-bit hardware. my server is the only computer i have that's 32-bit in software. petium III's were never 64-bit.

---

### Post by bilalakhtar on 2009-12-02
> **benmoran said:**
> I've used 64-bit exclusively for about a year and a half. No problems. I have 2-gigs of ram, and that is plenty.
Thank you, benmoran! I will upgrade my RAM to 3GB and try out Karmic 64 bit from live CD first before moving on to it.

---

### Post by jrrader on 2009-12-02
I use 64 with 2 gigs of ram, sometimes with VB running XP, music playing, internet going and a few other things.  My only problem with 64 bit is that I can not get flash working properly on youtube and hulu.  Hulu isn't really a problem because I use the Hulu desktop application now but I still can't press buttons in youtube.  No other flash video websites are problematic for me - just those two.

---

### Post by Some Penguin on 2009-12-02
> **jrrader said:**
> I use 64 with 2 gigs of ram, sometimes with VB running XP, music playing, internet going and a few other things.  My only problem with 64 bit is that I can not get flash working properly on youtube and hulu.  Hulu isn't really a problem because I use the Hulu desktop application now but I still can't press buttons in youtube.  No other flash video websites are problematic for me - just those two.

 Interesting.  I'm a Gentoo user, not a Ubuntu user, but I am using the amd64 build, and controls seemed to work fine for me in hulu at least for a tiny bit of testing (full-screen or windowed, either way).  Some poking around suggests that I'm using version 10.0.32.18 of the Adobe Flash Player plugin, -- from  [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)  specifically.  Granted, that's a tarball of binary code, not a .deb, but what's relevant is that it's straight from Adobe, not some mutant Gentoo-specific fork.  And my Firefox is a presumably ordinary 3.5.4 amd64 build.

---

### Post by oldos2er on 2009-12-02
> **jrrader said:**
> I use 64 with 2 gigs of ram, sometimes with VB running XP, music playing, internet going and a few other things.  My only problem with 64 bit is that I can not get flash working properly on youtube and hulu. 

 You might want to look at [http://astoryworthtelling.wordpress.com/2009/11/09/cant-click-in-flash-using-ubuntu-9-10-karmic-try-this/](http://astoryworthtelling.wordpress.com/2009/11/09/cant-click-in-flash-using-ubuntu-9-10-karmic-try-this/)

---

### Post by philinux on 2009-12-02
Everyone should read this.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by QIII on 2009-12-02
My two (or three) cents:

64 bit architecture is the way the industry is moving.  

The 4GB memory limit is not an issue if you want to use less than 3.2GB.  BUT:  The fact is that the industry is moving towards greater and greater memory capacity.  4GB was phenomenal three years ago.  It's *de rigueur* today.  8GB and 16GB machines are common.  I have a 16GB machine.  I doubt that I will ever have a motherboard that will allow me to use the theoretical limit of 16EB of memory, but who knows?  If someone finds a way to make the modules and someone else figures out how to make the motherboard use it...

64 bit processing may not be necessary for many applications today, but it will be necessary as software developers move to it.  The fact that there are 32 bit libraries to run 32 bit software is not bad.  It is simply a pragmatic response to the fact that there are still 32 bit apps to be run on 64 bit machines.  

64 bit software, despite what others are saying, is NOT something the software developers are loath to do.  Take a look at my profile.  I think I have a good insight here.  You might not see it.  Yet.  It is being developed.  Software developers are not ignoring it.  Hardware OEMs are not ignoring 64 bit drivers.

As mentioned, the 64 bit benchmarks are significant, if not yet breathtaking.  They will become so.

The bottom line is this:  64 bit machine architecture is here and growing.  Sticking with 32 bit OSs and software will be like have stuck with 8 bit architecture when 16 bit architecture became available.  Or sticking with 16 bit architecture when 32 bit architecture became available.  The door is closing.  You will be left in the cold.

---

### Post by pqwoerituytrueiwoq on 2009-12-02
> **Sef said:**
> Not correct.



32-bit can only use about 3.2 gb ram no matter how much is installed.  

As for 64-bit, if you only do word processing, surfing, and other nonintensive cpu uses then you won't see much of a difference.  If you do things that are cpu intensive then it can make a difference.  For example, i had a friend who would come over to download his photos to a usb stick because my machine with 2 gb ram could download his 400 photos in about 20 minutes.would flash performance improve?
or does adobe 64bit linux support suck so much it counters the effect?

---

### Post by QIII on 2009-12-02
Your mileage may vary, but I have noticed a significant improvement using the 64 bit Alpha version of Flash.  Particularly in full screen.

---

### Post by bilalakhtar on 2009-12-03
I think the alpha of the flash player for linux 64bit is available for download on this page. Still, its only an alpha!!!:p

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by Soul-Sing on 2009-12-03
If you have the "machine", the hardware you should really give 64 bit Ubuntu a try, its faster, and very, very faster with/when converting stuff.

---

### Post by Soul-Sing on 2009-12-03
> **bilalakhtar said:**
> I think the alpha of the flash player for linux 64bit is available for download on this page. Still, its only an alpha!!!:p

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
But this alpha works very fine!

---

### Post by michaelzap on 2009-12-08
> **leoquant said:**
> But this alpha works very fine!

Google Gears (necessary for offline Gmail storage) does not work at all on 64-bit Linux systems, however (much to my dismay).

---

