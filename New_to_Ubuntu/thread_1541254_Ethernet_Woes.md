---
title: "Ethernet Woes"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by dmaxel on 2010-07-28
Hi everyone,

I'm trying to get Ubuntu running on a machine of mine, but the ethernet seems to not work. Well, actually, it does work, but Ubuntu can't find it. Typing in lspci doesn't spit out any ethernet controllers, not even unknown ones. If it'll help anyone, the motherboard is an ECS P4M800-PRO.

In case it's impossible that get that exact ethernet port working, I do have an ethernet PCI card in my server that works for sure. Thing is, the server is using it right now because it couldn't find the ethernet on the same motherboard when it was first installed. I recently switched out most of the hardware on that server, so it has a fresh motherboard. Is there any way to make Ubuntu "search" for any new ethernet ports and allow me to use that one instead? That way I could take the card out and use it on my spare box.

Thanks in advance.

---

### Post by jms1989 on 2010-07-29
Why not just purchase another card for about $20 usd?

---

### Post by dmaxel on 2010-07-29
If there's a way to save $20, I will. I'm almost out of money doing those hardware upgrades to my server anyways.

---

### Post by jtarin on 2010-07-29
From what I can tell this ethernet chip uses the via-rhine module

You can check to see if the module is already loaded (which I doubt) by running the following command from the command line:


```
lsmod | grep via-rhine
```
If it's not loaded, you can try this command to load it:


```
sudo modprobe via-rhine
```
Now run the first again and see if it loaded. Yes? Good!
You'll probably need to restart your network for the newly loaded module to work. If its needed, you can try putting the module in your /etc/modules file so that it loads automatically at boot time.
__________________

---

### Post by dmaxel on 2010-07-29
> **jtarin said:**
> From what I can tell this ethernet chip uses the via-rhine module

You can check to see if the module is already loaded (which I doubt) by running the following command from the command line:


```
lsmod | grep via-rhine
```If it's not loaded, you can try this command to load it:


```
sudo modprobe via-rhine
```Now run the first again and see if it loaded. Yes? Good!
You'll probably need to restart your network for the newly loaded module to work. If its needed, you can try putting the module in your /etc/modules file so that it loads automatically at boot time.
__________________
Hahaha, oh yay. None of those commands gave me any output whatsoever. It just returned straight to the next line for me to type a new command. :/

EDIT: It worked when I used *via_rhine*, so basically it was already loaded, which is surprising.
EDIT 2: My bad, apparently it was loaded because I ran the command to load the module. However, it still doesn't work even with the module loaded and network restarted (using sudo /etc/init.d/networking restart command)

---

### Post by jtarin on 2010-07-29
I Googled that board and chip for quite awhile and there were even some links back to this site. Some links on problems with that chip go back several years with never anything substantial in the way of a fix. A batch of hit and miss. If you get another card try to disable that in the bios and if not possible set your other up as eth1. I saw one reference to setting via_rhine up as eth1 and getting it to work.

What's the output of the command ```
ifconfig -a
```

---

### Post by dmaxel on 2010-07-29
Well, it's hard to copy and paste from a machine that can't share its output well, so I'll have to keep it simple.

Basically, there were two interfaces. One was lo, the Local Loopback. Then there was```
pan0        Link encap: Ethernet        HWaddr: xxxxxxxxxx
```except there was actually something placed in the hardware address spot.

---

### Post by jtarin on 2010-07-29
That more than likely is a bluetooth device. Ubuntu recognizes that. I've no experience, but I've read that those can be configured and used like an ethernet card. I wouldn't know how though.

---

### Post by dmaxel on 2010-07-29
> **jtarin said:**
> That more than likely is a bluetooth device. Ubuntu recognizes that. I've no experience, but I've read that those can be configured and used like an ethernet card. I wouldn't know how though.
Sigh, it would only make sense if I even had anything that uses bluetooth in my room. I hate this motherboard hahaha

---

### Post by jtarin on 2010-07-29
I see your from the Dallas-Ft. Worth area. I used to live in Midlothian...about 30 miles south of Dallas on 67. Then just before I moved to my present location I was in Cleburne Tx.....anyways...This was about 8-9 yrs ago Goodwill had a large store in Ft. Worth where they sold used computers and parts. It was a goldmine then. Real nice guy ran it...stuff was super-cheap. I used to buy memory and video cards hard drives and _ethernet cards_ from him for a dollar or so for my old Pentiums that I would refurbish and sell for .Hell you could by a complete computer for about $10-15 if you weren't too particular:D

---

### Post by dmaxel on 2010-07-29
Haha, wow! Maybe I'd look by at our Goodwill here in McKinney, but I heard the people who run it are definitely **not** nice. Plus I doubt they'd have too many computer parts anyways. But yeah, if I could make simple computers for $10-15, I'd do it. Make 'em all run Xubuntu or something. xD

BTW, I'm writing this from my machine I finally got ethernet for. Since you told me to check ifconfig -a, I decided to see if I could do the same on my server in order to get that ethernet card out and use the new OnBoard LAN. Sure enough it worked, and after lots of screws here and there I put that sucker in there. At least now it works. :D Thanks for your help the whole time hahaha.

---

### Post by jtarin on 2010-07-29
Yea this wasn't a "regular" Goodwill.......this place only had computers. Glad you got it running.Southern engineering.

---

