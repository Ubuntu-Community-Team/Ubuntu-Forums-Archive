---
title: "Swap Partition Sizes"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Zero++ on 2009-07-16
So I've heard some some conflicting wisdom regarding swap partition size and am wondering what you think. Hopefully this discussion will help some beginners. 

The rule of thumb that I have heard is to have a swap file twice the size of your RAM. 

However have also heard people say once you get into the 2 or 3 gig stage you don't need such a big swap partition and to keep it at about 2 gig. Which makes sense especially with how efficient Linux is. 

Now I am seeing people recommend making a swap file twice the size of your ram even with large amounts of RAM.

So what do you think? Do I need to create a 16 gig swap file for my new machine with 8 gig of RAM?

---

### Post by roccivic on 2009-07-16
For 8GB worth of RAM you don't need any SWAP :p

---

### Post by Het Irv on 2009-07-16
> **roccivic said:**
> For 8GB worth of RAM you don't need any SWAP :p

+1, 8 gig should be plenty. But if you want to put a SWAP Partition, 2 gigs should be just about right

---

### Post by halitech on 2009-07-16
with 8gig of ram you shouldn't need it for day to day use but if you plan on using hibernate, you will need at least as much swap as you have ram, otherwise it will have no place to save when you hibernate.

---

### Post by lykwydchykyn on 2009-07-16
The "twice the RAM size" thing is way out of date.  I don't think there's really a good rule of thumb here.  You just have to approach it logically:

 - Swap is an "overflow" for RAM when you run out of memory
 - Swap is also used (in Linux) to hold the state of RAM if you suspend-to-disk ("hibernate")

The questions are (1) are you planning to suspend-to-disk?  If so, you need at least your RAM amount in swap space.  If not -- (2) how likely is it that you're going to use up 8 GB of RAM, and how much overflow space do you think you'll need.

You also have to take into consideration that disks are slow and RAM is fast, so you don't WANT your computer to swap if you can avoid it.  You certainly wouldn't want it swapping out gigabytes of data.

---

### Post by Zero++ on 2009-07-16
Well I hadn't planned on putting a swap file on that particular machine. Just trying to stimulate a discussion. At what point do we not have to make a swap file? At what point do we stop making our swap files twice the size of our system memory?

---

### Post by Cheesemill on 2009-07-16
> **halitech said:**
> with 8gig of ram you shouldn't need it for day to day use but if you plan on using hibernate, you will need at least as much swap as you have ram, otherwise it will have no place to save when you hibernate.
 
Not strictly true, only used RAM is copied to the swapfile when you hibernate, and it is also compressed. So unless all of your RAM is being used then you can get away with alot less than 1x your RAM and still hibernate.

---

### Post by Elep.Repu on 2009-07-16
[http://linux.com/news/software/applications/8208-all-about-linux-swap-space](http://linux.com/news/software/applications/8208-all-about-linux-swap-space)

> **Cheesemill said:**
> Not strictly true, only used RAM is copied to the swapfile when you hibernate, and it is also compressed. So unless all of your RAM is being used then you can get away with alot less than 1x your RAM and still hibernate.

Also, who uses 8 GB of RAM at once and then hibernates?

---

### Post by HiImTye on 2009-07-16
of course having more than 3gigs of memory is only useful if you're using a 64 bit processor AND a 64 bit operating system. but really, do you even *need* more than 3 gigs of memory? most times you won't even touch the last 4 gigs even on a 64 bit processor/OS

---

### Post by Zero++ on 2009-07-16
You all are fixating on the specifics on the 8 gig of RAM. I am looking for more general answers. What about someone with 3 gig or 1.5 etc. etc. what size should their swap file be. I'm not looking for a specific answer to a problem I'm having.

---

### Post by HiImTye on 2009-07-16
I would say that for normal day to day computing 1.5-2gb would be the most you would ever need (ever ever ever). even that probably won't ever get fully used

---

### Post by Elep.Repu on 2009-07-16
Why does it matter that much?
Use as much swap as you will be using in RAM, so when you hibernate, you're pretty covered...

Check out [Swappiness]("http://www.google.com/search?q=swappiness&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").

---

### Post by philinux on 2009-07-16
I have 2 gig ram and made the swap file 2 gig. Hibernate and suspend work just fine. If I had more ram i think I'd leave it at 2 anyway.

---

### Post by HiImTye on 2009-07-16
> **Elep.Repu said:**
> Why does it matter that much?
Use as much swap as you will be using in RAM, so when you hibernate, you're pretty covered...

Check out [Swappiness]("http://www.google.com/search?q=swappiness&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").


you're not seriously suggesting that someone will ever need more than 3gb swap for normal computing? I mean unless you're working on a large project (which you would probably do best just saving) while running fifty different programs you probably won't even use 2gb of ram

[Overkill]("http://bigbolshevik.blog.friendster.com/2008/10/the-overkill-one-or-the-ridiculously-overkill-one/")

---

### Post by bodhi.zazen on 2009-07-16
The general rule of thumb I advise for swap is 

RAM X 2 max 1 Gb (some say max 512 Kb, but that may be too low if your ram is between 512 Kb and 1.5 Gb )

If you hibernate try Swap = RAM.

It is interesting that some people can hibernate on less RAM, so it sounds as if even the swap = RAM may need modification.

If you want to know, Linux uses RAM very different then Windows and it depends on what you are doing and "normal" varies.

Example :

> root@banshee~# free -m                                        07/16/09  3:56 PM
             total       used       free     shared    buffers     cached
Mem:         16036      14568       1467          0        881      11379
-/+ buffers/cache:       2307      13728
Swap:        15359          0      15359Yes that is 16 Gb of ram on a server. As you can see, Linux is "using" 14 Gb RAM, but 13 Gb are "free". And yes it is "normal" for this server to use 14 Gb RAM.

Yes the swap is way wayyyyyyyyyy too big, bad choice of "defaults" on the installer, and no options to change it (poor design of the base OS + sys admin too lazy to modify it post install). Also, as you can see it is not used at the moment (which kind of proves the point, swap is not strictly necessary on high RAM systems, I would say anything larger then 2-3 Gb can probably run with no swap if you are short on HD space).

Unused RAM is wasted ram, lol.

If you want to calculate how much swap you "need" see :

[http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

And if you are interested in how Linux uses RAM see :

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by roccivic on 2009-07-16
Ok, my main PC has 512MB of RAM and a 256MB SWAP partition (Ubuntu 8.04), still I cannot recall ever using any more then a few MB of SWAP at any given time. But then I'm not a guy that uses resource hungry apps.

On one of my older PCs I have 384MB of RAM and 512MB of SWAP (Puppy linux 4.10), and there at times it was half-full.

---

### Post by bodhi.zazen on 2009-07-16
Take a look at the links I gave you. Yes it is most heavily dependent on the applications you use, but linux will use all available RAM.

I see this all the time in virtual guests. Give Apache (in a VPS) 256 and it uses 256, give it 512 and it will use 512, give it 16 Gb and it will use 16 Gb. (Yes, Apache benefits from some tweaks in a 256 or 512 VPS).

Linux uses RAM very different then Windows and it depends on what apps you use and how.

---

### Post by mcduck on 2009-07-16
> **HiImTye said:**
> you're not seriously suggesting that someone will ever need more than 3gb swap for normal computing? I mean unless you're working on a large project (which you would probably do best just saving) while running fifty different programs you probably won't even use 2gb of ram

[Overkill]("http://bigbolshevik.blog.friendster.com/2008/10/the-overkill-one-or-the-ridiculously-overkill-one/")

If that somebody thinks he's needing 3GB of RAM, it only makes sense to assume he might actually also use all that RAM. And in that case he'll need that 3GB of swap to suspend the machine. Simple as that.

It just doesn't make sense to build a machine with 8GB of memory and then count on never using it. Doing that means you are either wasting your money by buying more RAM than you need, or risking the stability of your system by intentionally creating a setup that will fail in some situations.

---

