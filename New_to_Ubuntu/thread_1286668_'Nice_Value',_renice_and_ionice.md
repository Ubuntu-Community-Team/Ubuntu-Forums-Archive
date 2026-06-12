---
title: "'Nice Value', renice and ionice"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-09
In another thread, someone mentioned that they set a particular app's 'nice value' to 5, giving it a relatively low priority.

I'd never heard of the term 'nice value', so I found out a little on [wiki]("http://en.wikipedia.org/wiki/Nice_(Unix)").

That page describes how the numbering system works between -20 (highest priority) and +19 (lowest priority), with 0 being the default for most apps as far as I can tell.

It then goes on to talk about two apps that assist in setting nice values - renice (for prioritizing CPU time) and ionice (for prioritizing connectivity).

I would like to set my Deluge app to a low priority for internet usage. Could someone explain to me what I need to do? There doesn't seem to be a package in Synaptic called ionice.

---

### Post by taavikko on 2009-10-09
ionice is installed by default, it comes from util-linux package.
renice comes with bsdutils

```
man ionice
man renice
```

---

### Post by Roger Allott on 2009-10-09
> **taavikko said:**
> ionice is installed by default, it comes from util-linux package.
renice comes with bsdutils

```
man ionice
man renice
```

Could you explain what those commands do, please?

I've just typed 'man ionice' into a terminal window and got some stuff I don't understand. Then, when I tried to close the window it warned me that a process was running and I'd frazzle it if I continued.

---

### Post by taavikko on 2009-10-09
> **Roger Allott said:**
> Could you explain what those commands do, please?

I've just typed 'man ionice' into a terminal window and got some stuff I don't understand. Then, when I tried to close the window it warned me that a process was running and I'd frazzle it if I continued.

"man command" gives you the manual on how to use the command.
One can exit the man pages by pressing "q"

---

### Post by Sarmacid on 2009-10-09
Man pages have lots of stuff, so to simply see what you need to do for a command to work you usually issue it with the -h or --help flags like this```
ionice -h
renice -h
```

---

### Post by the_olo on 2010-09-22
Dudes, you're not helping the guy with his actual problem - renice and ionice aren't the right tools for this specific job. Read the original post:

> **Roger Allott said:**
> It then goes on to talk about two apps that assist in setting nice values - renice (for prioritizing CPU time) and ionice (for prioritizing **connectivity**).

(Emphasis mine) See? Here's the first misconception. Ionice controls process' I/O (Input/Output) scheduling priority. Input/output in this context means **disk** operations - it has almost nothing to do with network connectivity!

Same for renice and CPU priority - as network processing nowadays requires little percentage od CPU power, there's little that renice could do to influence your network usage, you'd only make the application run more slowly (for you) than usual.

> **Roger Allott said:**
> 
I would like to set my Deluge app to a **low priority for internet usage**. Could someone explain to me what I need to do? There doesn't seem to be a package in Synaptic called ionice.

Considering that Deluge is a BitTorrent client, if I understand your question correctly, you're trying to limit the amount of network traffic that Deluge generates so you can e.g. browse the web without noticeable slowdowns, right?

In such a case, 2 possible solutions come to mind:

1) The easy one - if the application has relevant  setting (which I know Deluge has - see [http://dev.deluge-torrent.org/wiki/UserGuide/BandwidthTweaking](http://dev.deluge-torrent.org/wiki/UserGuide/BandwidthTweaking)), you should configure the application to limit its network bandwidth usage by itself. In Deluge this is controlled by the global "Maximum Download Speed" and "Maximum Upload Speed" settings. This solution is only possible if the application has bandwidth limiting functionality built in - which, luckily, Deluge has.

2) The hard one - configure system level network bandwidth limiting/traffic shaping on Linux (see [http://lartc.org/howto/lartc.qdisc.html](http://lartc.org/howto/lartc.qdisc.html)) - this is for skilled network administrators only and is only a chapter in a much larger book ([http://lartc.org]("http://lartc.org")), so I assume that this isn't the right solution for you, although you might learn lots of useful stuff this way.

---

### Post by freak42 on 2010-09-22
+1 for olo's post above...
you can't use ionice for limiting deluge's internet traffic. ionice is strictly for disk access scheduling only. but you can set the relevant settings within deluge itself.

hth
m

---

### Post by Roger Allott on 2010-09-24
> **the_olo said:**
> 
Considering that Deluge is a BitTorrent client, if I understand your question correctly, you're trying to limit the amount of network traffic that Deluge generates so you can e.g. browse the web without noticeable slowdowns, right?


Many thanks for actually addressing my question.

My actual problem wasn't as simple as trying to limit bandwidth usage. What was happening was that when Deluge was open as a window, Firefox just stalled on me and I couldn't do any browsing. However, when I closed Deluge so that it continued to run in the background (and thus use both up and down bandwidth exactly as it had been previously) my Forefox browsing abilities would return.

That was true whatever limitation I placed on Deluge's use of bandwidth.

So I concluded that bandwidth usage wasn't the cause of my problem, and I guessed that Deluge (when in window mode) must be utilising the same system resources (e.g. CPU, memory) that Firefox wanted.

Anyway, the problem seems to have now resolved itself, probably as a result of upgrades to Deluge (and/or Firefox).

---

