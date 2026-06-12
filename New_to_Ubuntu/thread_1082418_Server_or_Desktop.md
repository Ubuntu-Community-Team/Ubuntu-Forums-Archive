---
title: "Server or Desktop"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by sleestak on 2009-02-27
So I did a search and didn't really find the answers I was looking for...just so you know I did actually try first :)

I am a web designer who has dabbled a bit with webmin, worked in an SVN environment and such....so I am hoping that I can learn a bit more about the server end of things, but at the same time have a desktop to play around with or let a guest use it to surf the web and such.

I just picked up a p4 and I would like to:
[LIST]
[*]Use it as a Web testing enviro (LAMP install and possibly Ruby and such later on)
[*]Use it to serve music/files to the computers in my home network (SAMBA)
[*]Get more familiar with web server admin thangz without blowing up my live web box and probably pissing off my hosting provider
[/LIST]

I think it would be nice to still have some of the desktop apps as well...like I said, others may use it and it would just be nice to have another desktop in general.


So my questions are:
**Would it be better to install desktop and then the server apps I would like to have, or vice versa?**

**Are there any advantages either way?**

**File/folder structures, HD formatting, etc. Any distinct differences between going one way or the other?**

Thanks for reading my n00bness!

---

### Post by blueridgedog on 2009-02-27
> **sleestak said:**
> 

So my questions are:
**Would it be better to install desktop and then the server apps I would like to have, or vice versa?**

**Are there any advantages either way?**

**File/folder structures, HD formatting, etc. Any distinct differences between going one way or the other?**

Thanks for reading my n00bness!

I would install server, then when booted

```
sudo apt-get install ubuntu-desktop
```

The advantage I see is that you will have an environment similar to what you will be writing for.  Note that I do not say this will be easiest, just best...you will have to install many desktop items, but you will learn more that way.

I would take the defaults for the drives as it is likely to make /swap and / and that will be fine for a test environment.

---

### Post by indytim on 2009-02-27
Welcome to the world of Linux!  To briefly answer your question, yes it is entirely possible to run the standard bill of servers in a desktop environment.  Since you were referencing multiple users, this would be the recommended path vs command line only as found in the server editions.

I have been running exclusive desktop environments in Linux for close to 5 years.  In that time period, I have always had at least a LAMP server running (needed for work-related that I do at home plus personal development).  I am also running a SAMBA server which is utilized by my wife's XP PC.

There's tons of ways to install and configure the servers (as you are soon to find out...:P).  You can visit my website for an easy way to build a LAMP Server if your interested.

Good Luck,

IndyTim

---

### Post by sleestak on 2009-02-27
Thanks for the replies :P

My guess was that I should probably do the server first, but I knew it would be a bit more work and thought the other route might be faster and easier. I just wasn't sure how different they would be vs. real world. Would be a bit lame to do it the easy way only to find out later on down the road, in a job situation, that the file structures or something are not quite what I should have been getting used to.

I will certainly check out your homepage before diving in, just to get more of a background on what's in store.

Thanks to the both of you!


"punky" (my future "beater" box) thanks you too! 
[img]http://www.bonzermedia.com/misc/punky.jpg[/img]

---

