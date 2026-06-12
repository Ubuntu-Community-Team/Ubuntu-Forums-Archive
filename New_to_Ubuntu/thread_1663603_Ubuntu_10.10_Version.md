---
title: "Ubuntu 10.10 Version?"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by ritation on 2011-01-09
Decided to make the switch, and am going to be downloading ubuntu 10.10 by torrent.
They have a lot of different versions to choose from:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

ubuntu-10.10-alternate-amd64.iso.torrent
ubuntu-10.10-alternate-i386.iso.torrent
ubuntu-10.10-desktop-amd64.iso.torrent
ubuntu-10.10-desktop-i386.iso.torrent
ubuntu-10.10-netbook-i386.iso.torrent
ubuntu-10.10-server-amd64.iso.torrent
ubuntu-10.10-server-i386.iso.torrent

My computer specs: intel core 2 duo CPU P9500 @ 2.53GHz, 32bit OS

Which version is correct for my computer? Also, I am currently using windows vista... when I install ubuntu do I just do a regular installation and will it wipe windows?

Thanks,
Ritation

---

### Post by mikewhatever on 2011-01-09
**ubuntu-10.10-desktop-i386.iso.torrent** <- this one.
You don't have to wipe Windows, there is an option of installing Ubuntu 'side by side'. Your choice.

---

### Post by VonFilmjölk on 2011-01-09
and I would suggest that u download and the  amd64 desktop  version since u have a dualcore processor, running a 32bit OS on a dual core (  64bit architecture)  is like driving a race car in first gear.

---

### Post by 3rdalbum on 2011-01-09
Get the AMD64 desktop edition if your computer has more than a gigabyte of RAM, or the i386 desktop edition if your computer has a gigabyte or less. The AMD64 edition is 64-bit, so it can address more than 4 GiB of RAM out-of-the-box and will give you a handy speed boost when doing intensive tasks such as encoding video.

The AMD64 edition is compatible with your Intel Core 2 CPU.

---

### Post by darkhelmetchris on 2011-01-10
I would like to (slightly) disagree with the last two posters, to raise a point of thought:  it appears as if the the user that asked the original question is a new user to Ubuntu, so I would recommend this version:
> ubuntu-10.10-desktop-i386.iso.torrent(the 32-bit edition)

I have enjoyed using Ubuntu for about 4 years now, and while I DO support the idea that a seasoned user with a 64-bit processor probably wants to run the 64-bit edition, I think it's worthy to say that a NEW user should probably start out with the 32-bit edition, whether or not their system supports 64-bit processing.  The reason why I suggest this is that there are some compatibility concerns between 64 and 32-bit software, some extra learning, and I feel that these concerns are better addressed when you "know more about what you're doing."  You can always upgrade to the 64-bit edition at any time later.  I'm only suggesting that it might be easier for a new user to start with the 32-bit edition, unless they are already experienced with such matters.

I currently have BOTH the 32 and 64 bit editions dual-booted on my primary workstation, sharing the /home partition between them - and quite happily.  I use a current 64-bit processor and 4 GB of ram.  Both versions will address all my ram (with a slight performance difference - which is actually quite small in the big picture).  I think it was a good solid learning experience to start with 32-bit and move to 64-bit later when I was ready.  I generally recommend the same for others.

Just because I CAN drive my new race car at top speed, doesn't mean that I SHOULD do so the first time I drive it.

---

### Post by qyot27 on 2011-01-10
> **3rdalbum said:**
> Get the AMD64 desktop edition if your computer has more than a gigabyte of RAM, or the i386 desktop edition if your computer has a gigabyte or less.
Amount of RAM is irrelevant.  The 64-bit version performs well even with less than 512MBs of RAM (I used it on a comp with only 448MBs, since 64MBs was being eaten by the onboard graphics), and you still get the advantage that 64-bit provides.  If something is optimized for 64-bit, you'll get a boost regardless of how much RAM is in there.  More RAM is just a fringe benefit.

I've not had any problems with compatibility when using 64-bit, but others' mileage may vary (and quite frankly, there's nothing wrong with grabbing both the 32-bit and 64-bit versions and testing them individually).  It certainly wouldn't be as bad as whatever problems were there ~3 years ago or so.  The best test for compatibility is to get out and test.  If you pop in the 64-bit Live CD and see that certain things don't work, but they do with the 32-bit, then you have your answer (or the motivation to learn how to fix the issue with the 64-bit).  It'll happen sooner or later, and if one is willing to try any version of Ubuntu, and knows this forum is here, I would think they'd already be willing to seek help on the off-chance a problem arises.  But then again you may not find any compatibility conflicts with the 64-bit version, in which case just go for it.

Also, depending on how large your harddrive is, you could install both the 32- and 64-bit versions (although if you do install both like that, I would actually recommend doing it using Wubi - it'd be easier to reverse the decision when you find out for certain whether you'll have deeper problems with 64-bit or not).

---

### Post by mikewhatever on 2011-01-10
Let's not turn this into yet another 32 vs 64 bit discussion. The OP is obviously new, and didn't ask which of the versions is faster. There is also no indication that he is writing a dissertation on the version of Ubuntu. Try thinking like a new user, not like a Linux junky. ;)

---

### Post by VonFilmjölk on 2011-01-10
about compatibility except for a small initiall apci hickup, I have actually had less compatibility issues with the 64bit version. and that I about not needing to drive a sports car at top speed, I didnt really mean it like that, I meant that if u have a higher gear u should utilize it when the situation calls for it. why should it be better for an unseasoned user to only use one core?

---

### Post by VonFilmjölk on 2011-01-10
> **mikewhatever said:**
> Let's not turn this into yet another 32 vs 64 bit discussion. The OP is obviously new, and didn't ask which of the versions is faster. There is also no indication that he is writing a dissertation on the version of Ubuntu. Try thinking like a new user, not like a Linux junky. ;)


well he asked which version he should use for his hardware and in the case of having a 64bit architecture which a dual core have,  amd64 is the one. but of course a 32bit version will also run on a dual core.

---

### Post by mikewhatever on 2011-01-10
> **VonFilmjölk said:**
> about compatibility except for a small initiall apci hickup, I have actually had less compatibility issues with the 64bit version. and that I about not needing to drive a sports car at top speed, I didnt really mean it like that, I meant that if u have a higher gear u should utilize it when the situation calls for it. why should it be better for an unseasoned user to only use one core?

I am afraid you are badly misinformed thinking that 32bit versions don't utilize two processor cores. They do.
... and if you want a race car, get [Tiny Core]("http://distrowatch.com/table.php?distribution=tinycore"), cause Ubuntu is not a race car.

---

### Post by VonFilmjölk on 2011-01-10
> **mikewhatever said:**
> I am afraid you are badly misinformed thinking that 32bit versions don't utilize two processor cores. They do.
... and if you want a race car, get [Tiny Core]("http://distrowatch.com/table.php?distribution=tinycore"), cause Ubuntu is not a race car.

I wouldn't call my self badly informed, just because i left out that some of the newer 32bit operating system some times can use the second core for certain jobs. since this is irrelevant. 
and since you apparently got lost in the race car metaphor, i will clarify ,  running a high end graphic-card with plug-and-play default drivers will work, but its not optimal. and I know that ubuntu isn't a graphic-card driver,  Its a metaphor.

"I'am not saying that one is better than the other,  it all depends on your hardware, im running 32bit on my thinkpad since its a1,6Ghz singlecore and on my desktop which is a 2,40Ghz quadcore im running 64bit."

---

### Post by dBuster on 2011-01-10
> **VonFilmjölk said:**
> desktop which is a 2,40Ghz quadcore im running 64bit."

So in order to achieve the maximum do you install the 64bit version twice to use the quad core?  

Just kidding!!!!!  TFF

---

### Post by VonFilmjölk on 2011-01-10
> **dBuster said:**
> So in order to achieve the maximum do you install the 64bit version twice to use the quad core?  
Lmao :D
 
I stand in aw my good sir, But be care full next time so you dont accidentally divide by zero.

---

