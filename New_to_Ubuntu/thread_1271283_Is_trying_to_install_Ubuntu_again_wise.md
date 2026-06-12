---
title: "Is trying to install Ubuntu again wise?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by blakex on 2009-09-20
I'll do my best to make a long story, well, short.

I have an Acer Extensa 4420 that came with Vista. I bought it last September, immediately formatted it and have been using Mandriva 2008 ever since. All of that changed week before last when a co-worker urged me to try Ubuntu 9.04. We did the Live CD deal and I loved it. Also, I never had a problem with this laptop before that. I backed-up everything and went to install Ubuntu last weekend. Well, mid-install the laptop shut off and I got the dreaded "critical temperature reached" errors.

This kept repeating over and over. I finally got it to stay on long enough for me to put XP and/or Mandriva on. When the OS got on, the laptop was okay. The install process was the real b!tch, though.

In the end, the thing died about eight hours later and I had to ship it back to Acer for repair. Should I try again? I looked "critical temperature reached" up and people have been having similar problems when trying to install Ubuntu. I know it's a known bug, but this really KO'd my system. This sucks because I really enjoyed what I saw with Ubuntu that first go around.

---

### Post by Paqman on 2009-09-20
Id wait to see what Acer say about the repair. If you had a hardware fault then you can do whatever you like on the software side.

First i've heard of Ubuntu overheating laptops during install. Is it a problem with a certain model of laptop?

---

### Post by benerivo on 2009-09-20
I probably wouldn't risk it. You could try a command line installation from the alternate cd, which should be a faster and less processor intensive installation. Then just do...```
sudo apt-get install ubuntu-desktop
```from the command line to fully install ubuntu.

---

### Post by blakex on 2009-09-20
> **Paqman said:**
> First i've heard of Ubuntu overheating laptops during install. Is it a problem with a certain model of laptop?

Nah, it just happens with various laptops. I never heard of it beforehand either. Some people can install it, but it'll cut off during random activities like DVD playback, listening to MP3s and so on.

> **benerivo said:**
> **I probably wouldn't risk it.** You could try a command line installation from the alternate cd, which should be a faster and less processor intensive installation.

Ouch. That's what I was afraid of. Thanks for the suggestion.

---

### Post by Paqman on 2009-09-20
> **blakex said:**
> Nah, it just happens with various laptops.

It's probably laptops full of fluff overheating while thrashing the optical drive then.

---

### Post by benerivo on 2009-09-20
What is your core temperature when using Mandriva (after 10 mins or more of normal use)```
acpi -t
```

---

### Post by blakex on 2009-09-20
> **benerivo said:**
> What is your core temperature when using Mandriva (after 10 mins or more of normal use)

I won't get the Acer back until sometime this week... or so I've been told. Sorry, I should've made that clear in the first post.

On a side note: Are those laptop coolers really worth the investment? I had a regular stand for my Acer, but it obviously wasn't doing the job.

---

### Post by louieb on 2009-09-20
> **blakex said:**
>  Are those laptop coolers really worth the investment?

My T30 would overheat from time to time. Got a dual fan cooler over a year ago. Hasn't overheated since.

---

### Post by lswb on 2009-09-20
I've read about a possibly similar problem with some gparted live CDs not properly loading needed modules for certain HP laptops and causing them to overheat. 

Maybe you can wait till January or February and try it outdoors? :)

---

