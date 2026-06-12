---
title: "Bandwidth priority"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by kane77 on 2008-08-02
Lately I have been using bittorrent a lot to download Ubuntu 8.10 iso. And that made me think about one thing, is it possible to "nice" program's bandwidth? Let me explain, for example my max bandwidth is 60KB/s so I would like to set bittorrent program to lower priority so when I would like to listen to internet radio it would play OK (and torrent program would use remaining bandwidth), and when I'm not listening to radio it would use all available bandwidth..

I tried using trickle but no matter what the settings are I always get very low speeds (4-8KB/s). (I tried playing with trickled -p option).

Is there any program like that? (Or can trickle do it, if so, with what settings?)

---

### Post by phipps_2000 on 2008-09-09
I was wondering about this myself. This would be so welcome by me as I like to browse while trying to download large files. Anyone have any ideas.

Was thinking of something like QoS for an individual computer with out the need of a physical router (I do have a router but no QoS).

So any ideas/suggestions are welcome.


Thanks,
[COLOR="White"]james[/COLOR]

---

### Post by Cmndr Hippofiralkus on 2008-09-09
Thankfully as a stop-gap measure until you find a solution, nearly all Torrent Clients come with bandwidth utilization regulators built-in to them. The only clients i'm unsure of are transmission and bitlord.

I did find a old bandwidth allocation progam knocking around the net somewhere, but i am unsure as to it's name or status.
Anyone Know?

---

### Post by phipps_2000 on 2008-09-09
I would like something not only for file sharing applications but for any application or process that would happen to be using excessive bandwidth.

---

### Post by fugazi32 on 2010-03-17
^^ Bump! I am also looking for a program to allocate bandwidth on my router, my housemates are clogging it up with Xbox Live & Torrents all the time, and I keep getting disconnected! ^^

---

### Post by harisund on 2010-03-17
I believe this is possible when you are using Linux itself as a router, or you are running a router with more powerful Linux firmware. But otherwise, sorry I have no idea :(

---

### Post by ethanay on 2010-05-23
I've been wondering the same exact thing, and I think backend support that allows the OS to "nice" bandwidth coupled with a front-end tool that lets the user easily configure.  But I would be happy with sane defaults.

something like "Dynamic Bandwidth Allocation" makes a lot of sense given how the internet and bandwidth have become so central to user productivity and experience.

as Kane77 said, it would be similar to how "nice" manages CPU scheduler priorities

default configuration for a desktop would probably put Firefox ahead of Transmission, for example.  So if Firefox requests bandwidth, the kernel allows it to hog available bandwidth until it finishes its request.

complicating factors:
1. is driver support necessary?
2. is priority tied to amount?  for example, would Firefox be allowed to hog 100% of available bandwidth?  that could cause problems in other programs that need some minimal (but constant) connectivity.
3. should it follow window focus to determine whether something is a "background activity?"

I also like this idea because it values the principle of "use what we have more effectively" over the growth principle "let's just wait for faster internet connections."

I know nothing about programming.

---

