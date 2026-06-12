---
title: "Change desktop to overcome RAM shortage"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2008-12-22
Hi,  

I've installed a standard Ubuntu 8.10 with Gnome desktop on a partition of my 3 year old Acer laptop that has 248Mb available RAM.   It's not running too comfortably, though, and I suspect that's due to my shortage of RAM.   I'll probably go in for a new laptop next year, so rather than upgrade my RAM,  in the meantime,  I'd like to try to reduce my Ubuntu's heavy swapfile use by reducing its overall demand for RAM.   

I've heard of xubuntu desktop and xfce4 and am wondering how effective it would be to just replace Gnome with one of these and keep everything else.   I've read that these lighter desktops are suitable for use on old computers with much less RAM than my 248Mb,  so I imagine they'd work well in my case,  but I haven't come across any assessment that shows how they actually compare with Gnome a far as their demand on RAM goes.    

So I'm looking guidance on the relative demand for RAM between Gnome,  xubuntu-desktop  and xfce4 and any views about how effective from a RAM point of view it would be to replace Gnome this way.

Or can anyone suggest other simple alternative ways I could go a little lighter without losing the benefit of my available 248Mb RAM :?:

---

### Post by SlidingHorn on 2008-12-22
This might offer some insight: [http://ubuntuforums.org/showthread.php?t=371041](http://ubuntuforums.org/showthread.php?t=371041)

You can also look at other light(er)weight managers like IceWM or JWM

---

### Post by mbsullivan on 2008-12-22
> my 3 year old Acer laptop that has 248Mb available RAM

What do you mean by this? Do you mean that you have 256MB of RAM, total, or that you have 248MB available after you startup Gnome.

Also, using a little "b" normally means "mega-bits", where there are 8 bits in a byte. I'm assuming that you meant MB.

> 
So I'm looking guidance on the relative demand for RAM between Gnome, xubuntu-desktop and xfce4 and any views about how effective from a RAM point of view it would be to replace Gnome this way.

Changing desktop environments can help a LOT for somebody with limited RAM. I'm not sure how little memory XFce uses for a fresh boot. However, both Fluxbox and Openbox (which are very light window managers) boot with < 100 MB of memory usage, so you can use that as your lower bound.

If I were to harbor a guess, I'd say that XFCE will use 160MB or thereabouts to boot, leaving you about 100MB free to play with. 

All of this begs the question, however... Why not save yourself some time and buy some more RAM? It's very cheap right now. You may be able to pick 1GB up for about $20 if you look for it online. 256MB of RAM is a tiny amount for computers, nowadays.

Mike

PS: You can try XFce, or any other DE/WM, for that matter, without re-installing the entire OS (from an Xbuntu CD, for example). Simply install the package from the repositories:

```
sudo aptitude install xfce4
```

Then "log out" and select the other desktop environment in the menu to the lower left-hand side.

---

### Post by Sleepy-zz-John on 2008-12-22
Mike,
      Thanks for your prompt and helpful response.

> [QUOTE]my 3 year old Acer laptop that has 248Mb available RAM  

What do you mean by this? Do you mean that you have 256MB of RAM, total, or that you have 248MB available after you startup Gnome.[/QUOTE]

I guess I mean an installed total of 256MB of which 248MB is available to the OS. 

> Also, using a little "b" normally means "mega-bits", where there are 8 bits in a byte. I'm assuming that you meant MB.

Ah yes,  sorry.  Humble apologies! Of course that Mb should have been MB 

Changing desktop environments can help a LOT for somebody with limited RAM. I'm not sure how little memory XFce uses for a fresh boot. However, both Fluxbox and Openbox (which are very light window managers) boot with < 100 MB of memory usage, so you can use that as your lower bound.

> If I were to harbor a guess, I'd say that XFCE will use 160MB or thereabouts to boot, leaving you about 100MB free to play with. 

That sounds quite reasonable so I think I'll give it a try.   I just wonder how that compares to Gnome, though. 

> All of this begs the question, however... Why not save yourself some time and buy some more RAM? It's very cheap right now. You may be able to pick 1GB up for about $20 if you look for it online. 256MB of RAM is a tiny amount for computers, nowadays.

Fair comment,  but I'm in Thailand, so prices,  quality and availability may not be the same here.   I'll investigate.

  Thanks again,    +  SzzJ

---

### Post by hyper_ch on 2008-12-22
well, turn off compiz and desktop effects... then also change to xfce or maybe even fluxbox.

However ram is cheap and another 256mb will do miracle.

---

### Post by Sleepy-zz-John on 2008-12-22
I've now installed the Xubuntu-desktop package by using Gnome's Synaptic Package Manager,  I've selected Xfce4 after a restart and I'm now working on Xfce4,   but there are a couple of problems:

FIRST PROBLEM:   Instead of decreasing RAM useage,  which was the whole purpose of my changing to Xfce,  it's marginally increased it!   With just the desktop and system monitor running on Xfce4 I get Mem 207 and Swap 73.  With just the desktop and system monitor running on Gnome I get Mem 197 and Swap 74.   I wonder if some old RAM-hungry Gnome elements could still be running and whether I really need to completely delete everything associated with Gnome in order to benefit from Xfce being lighter?

SECOND PROBLEM:  With Gnome,  I can see and access two other partitions on my HD.   They appear in 'Places' or in 'Computer'.    With Xfce,  these two partitions don't show up at all.  My DVD drive and a USB flash drive show up OK,   but not my HD partitions. 

If I can solve these two problems I guess I'll be quite happy with Xfce until I get some more RAM or maybe a new computer.   
 
Appreciate any suggestions.

---

