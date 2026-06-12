---
title: "Upgrade, Install, or Leave it Alone"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by CheshireMac on 2009-11-06
Hey folks. I'm running 9.04 right now, and I've made a few mistakes in my install. My plan is to clean the slate and start over. 
Aptitude is offering an upgrade, but I've been told its usually better to install from a clean slate. 
So my options right now are to do either method of installing 9.10, or sticking with 9.04 and cleaning up the system from inside. 
I need advice with the latter if 9.10 isn't stable enough yet. One thing I need is a good sources list for my Aspire One netbook (I hate the netbook remix), and I desperately need to fix the issue with my wireless, which keeps dropping. A hard-wire connection is constant and fast, but whenever I try to download anything significant, or even when I'm surfing for extended periods, the wireless drops. I can reconnect, but how lame is that, right? 
So, to sum it up, I need advice on which distro I should use, how to set it up, and how to make my computer operate properly with it, including my wireless.
Any thoughts would be apprectiated. Thanks for the help.

---

### Post by gatorbrit on 2009-11-06
I ended up doing a clean install and wiping 9.04 on my dual boot laptop.  The process was flawless.  Before that I had tried doing the upgrade and had run into problems with my touchpad.

I'm very happy with 9.10.  I'm running it on two different machines now.

---

### Post by yeats on 2009-11-06
> Hey folks. I'm running 9.04 right now, and I've made a few mistakes in my install. My plan is to clean the slate and start over.
Aptitude is offering an upgrade, but I've been told its usually better to install from a clean slate.
So my options right now are to do either method of installing 9.10, or sticking with 9.04 and cleaning up the system from inside.

Fresh installs are usually preferred over upgrades - less can go wrong (generally).  If this is a new 9.04 install, you don't have much to lose by trying 9.10, IMHO.

> I need advice with the latter if 9.10 isn't stable enough yet. One thing I need is a good sources list for my Aspire One netbook (I hate the netbook remix)

You can use the "regular" version of Ubuntu on a netbook - aside from the clutter menu, there's not much difference between those two (as far as I know).

> and I desperately need to fix the issue with my wireless, which keeps dropping. A hard-wire connection is constant and fast, but whenever I try to download anything significant, or even when I'm surfing for extended periods, the wireless drops. I can reconnect, but how lame is that, right?

This may or may not be fixed with a reinstall - without more details, there's not much to recommend...

> So, to sum it up, I need advice on which distro I should use, how to set it up, and how to make my computer operate properly with it, including my wireless.
Any thoughts would be apprectiated. Thanks for the help. 

You might do better to break this into specific questions (one per thread) :-)

---

### Post by frankelr on 2009-11-06
Hi, So far I have done three 9.04 upgrades and 4 9.10 new installs.  All worked, as hoped for, except for a computer with server and desktop: the sql server took a hit.  So its just what you feel like and how brave you are. BTW I tried both ext3 and ext4 on a 1005 netbook: both seemed to work OK. On the netbook I finally decided to use 9.10 ubuntu not the REMIX; I wanted the normal workspaces and a trash icon


Bob

---

### Post by presence1960 on 2009-11-06
I would do a clean install, why? Just go through the forums and see how many people have had problems upgrading to karmic. The same happened with jaunty.

---

### Post by ranch hand on 2009-11-06
There are a lot of changes "under the hood" on 9.10 compared to 9.04.  We had FUN going through them in alpha testing.

Back up your data and do a clean install.

That said, if 9.04 is working, I would wait another week or two to let the dust settle on some outstanding problems.

You could use that time to consider your partition table and figure out the best way for it to be.  A separate /home partition is your friend.

---

### Post by Joe420 on 2009-11-26
I did a clean install of netbook remix 9.10 and am quite happy after getting rid of the desktop and putting the GNOME desktop on.  Wireless works better with Kharmic

---

### Post by ukripper on 2009-11-26
Clean install i'd suggest.

you can also try eeebuntu NBR or Moblin 2

---

### Post by Norm24 on 2009-11-26
I personally have never had issues with upgrading but I did a clean install for Karmic so that I could have the benefit of Grub2 and Ext.4 partitioning.

Having read many threads about disastrous upgrades I'm now of the opinion that its safer to do a clean install.

Don't forget to backup /home(or anything else important) before installing.

---

### Post by Jive Turkey on 2009-11-26
If Jaunty didn't work flawlessly with your wireless chip I reccomend a fresh karmic install.  The wireless problems might disappear, or maybe not.  With an upgrade there is a higher probablity that they will linger.

---

