---
title: "[SOLVED] Ubuntu &amp;quot;Paging/page files?&amp;quot;"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by projecthikari on 2008-12-22
Does Ubuntu have these? If they do where are they.
I'm aware that they are a windows thing, and I've only heard them mentioned in conversations about Windows, never Linux.

What I'm trying to do, is basically make my computer faster. Removing all the fancy riffraff is my goal. I want to "Up" the "Paging files", Increase the memory, so it's like I have more RAM. (Sorry, I must sound like an idiot.)

Treat me as if you're talking to a monkey here. It would be appreciated. :KS

---

### Post by nhasian on 2008-12-22
you dont want the computer to use the hard disk as extra ram.  that will *slow* down your computer.  here's more info on the swap partition.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by mbsullivan on 2008-12-22
Hi projecthikari,

Linux has a space called the "swap disk" or "swap file" to support demand paging, analogous to the page file in Windows.

nhasian's link should help.

> What I'm trying to do, is basically make my computer faster. Removing all the fancy riffraff is my goal. I want to "Up" the "Paging files", Increase the memory, so it's like I have more RAM. (Sorry, I must sound like an idiot.)

Upping the swap space really shouldn't help, necessarily. This is because the hard disk is so much slower than the RAM that you don't want to swap at all unless you have to.

For a desktop installation, it generally makes the most sense to avoid swapping whenever possible, even if you're trying to work with a small amount of RAM. Carefully minimizing the running processes can help you to do so.

That being said, for some *very specific* usage patterns (having many programs open but only using one at a time, for instance) you might see some improvement from upping the "swappiness" factor. See nhasian's link for more info. This generally applies more to server installations, rather than desktop usage.

In general (as a rule of thumb), keeping as much swap space as you have RAM is a good idea, in order to support suspend-to-disk (hibernate).

Mike

---

### Post by snova on 2008-12-22
In Ubuntu, it's typically called swap instead of page files, but it's the same concept.

It will not make anything faster. If your computer ever starts using swap, it will be slower.

But yes, it does exist. It's typically its own partition rather than a file, though.

---

### Post by Skripka on 2008-12-22
> **projecthikari said:**
> Does Ubuntu have these? If they do where are they.
I'm aware that they are a windows thing, and I've only heard them mentioned in conversations about Windows, never Linux.

What I'm trying to do, is basically make my computer faster. Removing all the fancy riffraff is my goal. I want to "Up" the "Paging files", Increase the memory, so it's like I have more RAM. (Sorry, I must sound like an idiot.)

Treat me as if you're talking to a monkey here. It would be appreciated. :KS

As others  have already said, regarding swap.


Unless you are doing computationally demanding tasks where your system is FORCED into paging-you won't notice more memory except on boot....I can think of very few Linux apps that force my system into paging (I have 2GB of RAM).

---

### Post by mbsullivan on 2008-12-22
> But yes, it does exist. It's typically its own partition rather than a file, though.

I believe that this only used to be true. Swap files incur only a nominal performance hit, and will become the norm in the future.

I'd go with a swap file over a disk at this point, if given the chance.
Mike

---

### Post by projecthikari on 2008-12-22
So, simply: I shoulden't even bother with it.

My computer was just being a bit sluggish. I was watching Dexter's Lab videos. XDD

---

### Post by mbsullivan on 2008-12-22
> So, simply: I shoulden't even bother with it.

Probably, yes. 

It really depends on your usage patterns and amount of RAM. But, undoubtedly, paging out should be a last resort. Swapping is not a panacea!

Mike

---

### Post by scorp123 on 2008-12-22
> **projecthikari said:**
>  What I'm trying to do, is basically make my computer faster.  If my "making faster" you mean "more responsive", then please read this article. It may help on older systems with 2GB or less RAM:

[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

On my old Pentum-4 system I set **"vm.swappiness=10"** ... the default is 60! (please see the link above, it's all explained there).

Another thing that may help is to change your kernel scheduler. That's the mechanism that decides which task gets how much CPU time. I personally have had good experience with the **"deadline"** scheduler, but that doesn't necessarily mean it is right for you. Best thing would probably be if you experiment with it. Don't worry, switching the scheduler isn't too hard, it's just a boot parameter that needs to be set (and other than that it does not have any side effects). It's also easy to undo the change and get the default behaviour. Please read here:

[https://wiki.ubuntu.com/CFQbyDefault](https://wiki.ubuntu.com/CFQbyDefault)

Nowadays Ubuntu Desktop defaults to the **"CFQ"** ("completely fair queueing") scheduler, whereas Ubuntu Server defaults to the **"deadline"** scheduler, but it's easy to switch the behaviour regardless whether or not you installed Ubuntu Desktop or Ubuntu Server. So if you want to try out the **"deadline"** scheduler you'd follow the guide above, except you'd put **"elevator=deadline"** where the guide says that you should put **"elevator=cfq"** ... the instructions are identical aside from that. If you find that the "deadline" scheduler doesn't help in your case you can simply remove the 'elevator=deadline' entry from the boot config file again ... reboot ... voila done, your Ubuntu Linux should be back to its default behaviour.

As for the schedulers, their differences, and so on, there is an older article from 2005 written by Red Hat that is worth reading:
[http://www.redhat.com/magazine/008jun05/features/schedulers/](http://www.redhat.com/magazine/008jun05/features/schedulers/)

As I said above, my experience with the "deadline" scheduler has been very positive so far and IMHO it's worth trying.

---

