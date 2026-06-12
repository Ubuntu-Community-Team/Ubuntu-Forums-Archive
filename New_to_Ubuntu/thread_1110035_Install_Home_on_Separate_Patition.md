---
title: "Install Home on Separate Patition"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Dr Mac 24 on 2009-03-29
I've previously installed the Alternate AMD 64 8.10 SO on partition 1. Then tried to move /Home to partition to allow me to screw up and not loose data. This move was a disaster, thankfully I backedup personal info. Now downloaded Desktop AMD 64 and going to reinstall. 

Question 1 Can I create home on partition 2 during installation? If so how?

Question 2 If the above is not possible is there an idiots guide to moving home from partition 1 to 2? I've tried following the tutorial on Psychocat but I struggle with the terminology being used to Windows I guess.

---

### Post by Lisa Y on 2009-03-29
I found this guide, let me know if it helps you

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Elfy on 2009-03-29
Yep - when you get to the partition part of the install choose manual. You can then specify which partition for / and /home - select each partition and then edit - in new screen use Mountpoint to set each as you wish

---

### Post by egalvan on 2009-03-29
I go one step further, and apply a descriptive **LABEL** to the '/home' partition...

such as 

home-8.04-32

home-8.10-64

makes it easier to identify different installs on my hardrive...
(along with descriptive **LABELS** for the /boot partitions...)

Just some ideas to toss out there...

ErnestG

---

### Post by Elfy on 2009-03-29
> **egalvan said:**
> I go one step further, and apply a descriptive **LABEL** to the '/home' partition...

such as 

home-8.04-32

home-8.10-64

makes it easier to identify different installs on my hardrive...
(along with descriptive **LABELS** for the /boot partitions...)

Just some ideas to toss out there...

ErnestG

Never thought of doing that - I have to remember which partition has which install - something I don't always manage ;)

---

### Post by egalvan on 2009-03-29
> **forestpixie said:**
> Never thought of doing that - I have to remember which partition has which install - something I don't always manage ;)

Yeah. since my memory leaks more than the computer's RAM,
this has been a great tip...

picked it up from the "/rant" column that used to run on the last page of Linux Journal...
The author was "ranting" about how Fedora 32 & 64 bit installs would clobber each other...or something to that effect...
but his solution was to use descriptive labels...

I really miss that column, it was always very well written.
mainly about some of the silly, idiotic and sometimes just plain stupid things done in the Linux and OSS/FOSS communities/
But he always desctribed 'why' he though they were bad...
and always gave good ideas or thoughts as to fixes that might work.
Very balanced.

can't remember the author's name,
he is fairly well-known in the Linux community...
the column didn't run many months.
maybe he stepped on too many sacred cows... :)

---

### Post by Dr Mac 24 on 2009-03-29
Egalvan,

I really like this idea and will implement. Setting up a couple of OS's and Home all in different partition. Seen this else where I think but never thought to apply to my own PC. Thanks.

QUOTE egalvan;I go one step further, and apply a descriptive **LABEL** to the '/home' partition...

such as 

home-8.04-32

home-8.10-64

makes it easier to identify different installs on my hardrive...
(along with descriptive **LABELS** for the /boot partitions...)

Forestpixie, I'll have a bash at this i.e. specify partition 1 as / ( for OS 64)and partition 2 as /home. Thank. I'll let you know hows things go in a few days. Say I wanted to also install the 32 bit version of 8.10, how would I set up the / ? Or is there only ever one / on each hardisk?

---

### Post by Elfy on 2009-03-29
Seperate / and /home if you can do so - which is where it can get confusing :)

That said I no longer use seperate /home and in fact ony use it for configs - all my data now resides on it's own hdds/partitions and then available after I edit fstab.

My /home at the moment is less than 200MB - all I would need to copy to a new install is much less than that.

---

