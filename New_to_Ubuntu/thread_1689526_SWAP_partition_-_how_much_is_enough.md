---
title: "SWAP partition - how much is enough?"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by nomomikeysoft on 2011-02-16
Hi there,

I'm running 3GB ram on a 64-bit system...  I installed Ubuntu 10.10 to try it out and am really liking it.  However, by default the installation created roughly a 9GB swap partition.  Hard drive space really isn't an issue but I'm wondering if this may be overkill.

I've periodically ran "free" to check memory usage while having an intensive load on my CPU, especially when it seems that things might be slowing down a bit (launching multiple browser windows over and over again while playing music and/or downloading).  I have never seen the swap area even in use.

Here's a sample of what I get from the "free" command:

nomo@mycomputer:~$ free
             total       used       free     shared    buffers     cached
Mem:       3030388    1808280    1222108          0     244704     720100
-/+ buffers/cache:     843476    2186912
Swap:      9212924          0    9212924

I've seen "used" Mem at about 2400000 before, but still the swap area was completely unused.

I plan on reinstalling Ubuntu 64-bit (instead of 32) after a fresh Win XP install soon and am wondering if a 9GB swap partition may be too much considering i'm only running on 3MB ram.  I've heard that the swap should be roughly 1.5x your total installed ram... should I maybe go with a 5GB swap partition?

Also, is it possibly a good thing that I haven't seen the swap area used yet?

I'm running with default settings at the moment -- I believe the swap value is '60'.  Would it be recommended that I change the value to a different number (as I like to have lots and lots of windows open all the time) and could I get by with reducing the size of the swap partition or should I just leave it at 9GB just in case?

Additionally, I should allocate 10-12GB for the / partition and a much larger one for the /home partition?

Thank you.

---

### Post by PunkLV on 2011-02-16
Currently am running debian x64 on 3gb ram and 1gb swap. Never seen it being used over 20%. However, once or twice had major machine slowdowns when moving/copying lots and lots of gig's between 3 HDDs. Swap is rather useless for machines with 1gb+ ram, for home desktops at least.
You may want to consider upgrading CPU/HDDs or RAMs themselves.

Yeah, have forgotten about hibernation - I don't use it.

---

### Post by guilleme on 2011-02-16
Hi, Well, as a "standard" rule, it's said that the amount of swamp you should have should be twice the amount of physical ram in your computer, so, for your case, 6 gb should be enough. That is for being able to "hibernate" the computer, putting all the data actually in ram into the disc, and that way needing no power at all. 
I think 9 gb is a bit too much, but 5 could be not enough if you do "intense" stuff, like, you know, playing warzone 2100 while converting mkv's, writing a DVD iso, flipping the compiz cube and uploading a gb folder into a server while calculating the 10,000 billion digit of pi, at the same time. If your'e doing that, you're going to need something more than a 9 gb swamp, but for normal stuff, it's more than enough :)
Now, freeing memory isn't quite necessary very frequently, I run ubu. in a 391 mb, celeron computer, and I had't ever needed to free memory.
I hope this has been useful;).

---

### Post by Paqman on 2011-02-17
If you want to be able to hibernate then swap should be a little larger than your RAM. Otherwise, I wouldn't bother giving it any more than 1GB. With 3GB you're unlikely to ever be using swap much, if ever.

The default swappiness value of 60 is very, very conservative IMO. You can safely reduce that if you want, and it will improve performance under some conditions.

---

