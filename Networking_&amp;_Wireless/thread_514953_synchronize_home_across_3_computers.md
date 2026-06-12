---
title: "synchronize home across 3 computers"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by eentonig on 2007-08-01
Hi, 

[COLOR="Red"]**What's in Windows?**[/COLOR]
I've been thinking about a functionality that I would like to be available. When in windows I connect to the network at work, all my settings and files (Desktop layout, shortcuts, specific folders) are being transferred from a network server. 

If I use this computer afterwards disconnected from the network, it has kept these settings. So, no matter which pc I start at work, as long as I connect it to the network during my first login, I get the same environment to work in. 

[COLOR="Red"]**What I want**[/COLOR]
Now, for my personnal use, I'm thinking of being a new laptop. This would make my my HW total to be:

(- Old laptop : home server)
- Desktop PC
- Heavy laptop (from work) which isn't very transportable
- Little laptop : for the road.

When I'm on my desk, I use the Desktop. But sometimes, I use the 'heavy' laptop to work on the dinnertable, in the garden, ... anywhere around the house. It gives me freedom to move away from the desk.

And when I go onsite (hikes, clients, ...), I like to travel light and only take the little laptop.

Now, what I would like, is to have the same desktop environment on all three desktops. And to keep them synchronised. So, if I create a symlink on the desktop... it should show up on both laptops when I use them.

Also, some folders should be kept synche'd as well. Say. I'm working on the Desktop on a presentation, but my little boy needs the computer. So I log off and continue on the heavy desktop. Few hours later, I'm late for the presentation, so I lock my screen, grab the little laptop and head off to my client. I open the laptop and start my presentation (which is off course up to date with the latest changes I made at home).

Ok, it will never work that seamlessly. But it should be more or less possible. But what should I need to get it working?

I thought to make one of those three the "Master" home. And let the others synchronize against that one.

But then. What would be the best way to achieve a seamless environment? 
- sync /home every x amount of time?
- only sync on certain events? (log off, log on, lock, ...)?
- Manual sync?

- rsync?

---

### Post by frafu on 2007-08-01
Hello, 

I have moved your thread to the Networking forum that is more appropriate to its topic. 

Have a nice day. 

Francesco

---

### Post by kevdog on 2007-08-01
Sounds possibly like a job for unison, however it can handle only two replicas at once, so basically your would have to sync A to B, and then A to C (something like that).

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

---

