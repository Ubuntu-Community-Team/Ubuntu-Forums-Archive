---
title: "Another newbie, print server problem with Gutsy"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by danparkcityut on 2007-11-12
The print server works fine with my XP boxes, it's an AirLink model APSUSB201.  The printer is an all in one from Epson, model RX680.

I've looked here (and other places) for two days and tried everything I have found, but still cannot figure out how to print from this Gutsy system on this server / printer..

Some solutions actually started making sense to me, but none have actually worked.

I'm not PC illiterate, but am quite new to Linux, so I don't even know how to do an "APT-GET" procedure.  Seems every place I look, Linux folks assume we all know all that kind of jargon... but I don't.  I can't even figure out how to cancel about 15 print jobs in the queue (due to all the things I tried and generated all those test pages that never printed) without having to resort to command line stuff (like I remember how to do it in dos, never mind a whole new environment)... I admit it, I'm a GUI junkie these days.

First, is there a primer for learning that stuff (Jargon, and what it means)?

Second, Is there a way to find, in step by step English, how to get this setup to work for me?

Third, any ideas how to cancel all pending print jobs in less than an afternoon (I've added too many new printers in my experimenting, deleted all of them, but still seem to have piled up a bunch of print jobs)?

I know I must be missing something (probably about 10 years' experience on Linux LOL ), but I'm an old guy.  That's my excuse and I'm sticking to it ;)

TYVM

By the way, I'm sure happy to see what is happening with Linux, and Ubuntu in particular.  I would like to be Gate$ free by this time next year (next week would work too)...

Thanks again,

Dan

---

### Post by keyboardashtray on 2007-11-12
I was having a hard time finding the definitive source trying to set up my printer, was on an Ubuntu machine, to accept print jobs from an XP laptop. 

I found some article called I believe GutsyPrintingHowTo. I don't go to the wikis much, but the two relevant ones I've found there now seem to be 

[NetworkPrintingFromWinXP ]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP?highlight=%28printing%29%7C%28gutsy%29")and [NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?highlight=%28printing%29%7C%28gutsy%29")

Yes it is difficult to know what the console commands like apt-get (which is a program for downloading and installing something) mean at first. There are a million primers, most as good as the next, search linux commands or any variation and you'll get more tutorials than you can handle. Some of the best ones I tend to find are usually in people's signatures here at the forums. 

While most directions you will see from posts here, that contain commands, usually don't include details of what the command actually does (the burden is supposed to lie with the receiver to look up that which he might have doubts on), usually, if you are reading a post here, and the problem described is almost exactly like yours, or it is a direct response to your question, it is usually a safe bet to simply copy and paste the command character for character into the terminal and hit enter. The proper thing to do would be look it up at the same time, but in all reality that doesn't happen much. Just know at least to start that commands sudo and gksudo are going to prompt you for a password (and if it is sudo, the password entry in the terminal won't provide graphic feedback (asterisks) for each keystroke). sudo is the generic all purpose version, that runs something as the super user, and gksudo is the same except for graphic programs. Both of these commands are *supposed* to be weighed with some gravity, i.e., they do have potential to damage your installation if used improperly. But you will see them a ton anyway. People posting here will not in general post a sudo command that will wipe your hard drive, etc. 

Edit: But it can happen - someone has been running around telling people a command to wipe their hard drives. *Never*  type  sudo rm -rf. A good idea when you get a console command advice reply that you are unsure of, wait til another person or two has commented, or its gotten a bit more views, so that others are double-checking it.

You can find your terminal in the accessories menu.

Sorry, I don't know how to cancel the print queue - hopefull someone else can help with that.

---

### Post by danparkcityut on 2007-11-13
Keyboardashtray, I really like that handle and thank you very much for your help :)

I can't believe some of your advice, especially on the jargon topic, hits the nail right on the head (and I should have thought of some of it long before now ;)

I'm off to get that education...

Thanks again!

Dan

---

### Post by keyboardashtray on 2007-11-13
Thanks :) Did you get your printer up and running then?

---

### Post by danparkcityut on 2007-11-13
Not yet, I just got back in.  I'm hoping to work on it this afternoon...

Thanks again, and I'll post my results back ASAP

:popcorn:

---

### Post by danparkcityut on 2007-11-29
Update:  I've been off line for a while due to the wife having some routine surgery that got complicated..

I'm back and trying to follow through now, I'll post my results as they develop...

:popcorn:

---

### Post by danparkcityut on 2007-11-29
Wow,

That was quick!

I had picked up a copy of Ubuntu Hacks by Oxer, Rankin, and Childers... One page after the index, I was up and running!

I saw where I would be printing not via my old mini server, but from my main Windoze machine.  On the other hand, I'm not having to share anything but the printer (news to me, as I recall W98 wasn't as user friendly on that point), and if I ever have any other machines on to print from, the main Winoze box is already on anyway...

So this headache went away pretty quickly, once I got on the right track.

Thanks again keyboardashtray, I really appreciate the help you offered and learned a lot from it!

I hope this might help other folks, and ROCK ON:guitar::guitar::guitar: Ubuntu!

Dan

---

