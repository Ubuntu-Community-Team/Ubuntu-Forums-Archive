---
title: "Network Problems"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by kevbek on 2007-09-29
OK.  I've gone through the various old posts on this and can't find anything quite like it.

I'm a newbie, just installed Xubuntu, Feisty Fawn.  I couldn't connect to the internet.  So after trying the various help things, I decided to put in a different NIC to see if that made a difference.  It made no difference.  "ifconfig" shows all the right stuff.  I see an IP address with the correct subnet mask.  If I ping my router or google or yahoo, I tend to get 33 to 50%  packet loss.  If I ping from another computer to the linux box I get the same thing.  If I try to go to google on firefox, sometimes it will go, but it takes a long time.  If I try to log into my iGoogle page, it actually give me the log in page, then after I enter my info, after a long delay it goes to a blank page and says Done at the bottom left of the page. 

Does anyone have any idea what I can look for?  Any help would be appreciated.

Thanks,

Kevbek.

---

### Post by MobiusNZ on 2007-09-29
> **kevbek said:**
>  I tend to get 33 to 50%  packet loss

Sounds to me like a dodgy network cable. Is it home-rolled, or machine pressed?

---

### Post by noob12 on 2007-09-30
Also sounds like you could have a PCI routing or timing issue at boot.  Can you post the output of the following so we can understand what you have.

```

lspci -nn

sudo lshw -C network

# replace 192.168.1.1 with your actual router address if it is different
ping -c 10 192.168.1.1

# run this soon after the pings finish
tail -50  /var/log/kern.log

```

---

### Post by kevbek on 2007-09-30
Sure enough, that was it.  Wow, what a dork!  I never even thought that could be the problem.  And I do cabling for a living.  How embarrassing.  

Thanks

---

