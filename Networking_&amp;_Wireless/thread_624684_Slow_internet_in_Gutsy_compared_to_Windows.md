---
title: "Slow internet in Gutsy compared to Windows"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by mawxcarroll on 2007-11-27
Hi,
  My internet connection is slower in Ubuntu (7.10) than in Windows XP.  There are a number of solutions in the forums, none of which have worked for me.  Hopefully, I can provide an additional piece of information that might help someone figure this out.  First, here's the problem:

This is all about WIRED connections - I don't use wireless with my Gutsy laptop very often.

I have my laptop set up to dual boot XP and Gutsy (unfortunately I need XP for a couple pieces of windows-only work software).  When at work, I have download speeds of about 8k/s in Gutsy and about 300k/s in Windows!  Also, normal web-browsing in Gutsy is much slower (more noticeable on some sites, particulary Gmail, which is instantaneous in XP and takes about 1 minute in Gutsy).

HOWEVER -  When I'm at home connecting to my Comcast cable internet connection through my netgear router, there is NO difference between Gutsy and XP.  Both are quite fast.

This makes no sense to me.

I have tried disabling IPv6 in every place it was suggested, to no effect.
I have tried switching to OpenDNS, which might have made things moderately faster, but it's hard to tell.
I have tried a few other "long shots" that didn't work either.

I've included the output of some potentially useful info at the end of this message (for my slow work connection).

thanks!
tom

```

tcarroll@grayzy:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes


```

```

tcarroll@grayzy:~$ sudo ip route
192.204.148.0/25 dev eth0  proto kernel  scope link  src 192.204.148.9 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.204.148.1 dev eth0 

```

---

### Post by mawxcarroll on 2007-11-28
Hi again,
  My slow network problems are (mostly) solved.  I found a solution in the forums that I hadn't actually tried yet.  Give this a try if you're having similar problems.

I haven't tried optimizing the settings yet.  I just pasted these in and my download speed went from a best of 8k/s to about 35k/s consistently.  This is still below my WinXP speeds of 300k/s, but I'm hopeful that I can optimize it.  Page loads in Firefox are noticeably faster.

Since this problem only happens on my network at work, does any expert want to speculate on what could be the cause?  Is their some packet-shaping or optimization going on that works great for windows machines (the vast majority of machines here at work) that works terribly for ubuntu?

(This solution originally comes from [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=251509[/COLOR]]("http://ubuntuforums.org/showthread.php?t=251509"))

**Add the following to /etc/sysctl.conf **

```

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1


```

[B]Then to have the settings take effect immediately, run:

sudo sysctl -p[/B]

Thanks,
tom

---

### Post by mawxcarroll on 2007-11-30
Ok, thought I'd add one more last update.

A colleague of mine had the same problem and it seems that he needed both the fix in this thread AND the IPv6 fix to get everything working.

Also, by tweaking the numbers in the above fix, I was able to get ~350 kb/s transfers.  So, my Gutsy is now about 10% faster than my WinXP. (I replaced every instance of 524288 with 131072)

That is all.

-tom

---

### Post by defZA on 2007-11-30
I have an application that fails to work unless the tcp_rmem value is changed as described on this page.

I filed a bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/173126](https://bugs.launchpad.net/ubuntu/+bug/173126)
Check it out and confirm it so that it's fixed in Ubuntu and seen as a problem.

---

### Post by daimengrui on 2008-01-17
> **mawxcarroll said:**
> Ok, thought I'd add one more last update.

A colleague of mine had the same problem and it seems that he needed both the fix in this thread AND the IPv6 fix to get everything working.

Also, by tweaking the numbers in the above fix, I was able to get ~350 kb/s transfers.  So, my Gutsy is now about 10% faster than my WinXP. (I replaced every instance of 524288 with 131072)

That is all.

-tom

how do you know what number to put in?

---

### Post by thered on 2008-01-19
First impressions are that it has helped.

Posting this so I can find thread again :)

---

### Post by Chappy7777 on 2008-01-24
Well, I am still, in my mind at least, a NooB in Linux/Ubuntu. I had intended to ask "how do I get more speed from my internet conneck/setup?" until I read this.
I use the speed I get when downloading files, usually MP3s, to calculate my download speed. Like I said, I ain't no superGeek in Feisty. Anyhow, I just downloaded a tune at 128K, which is FAST!! to me since I am new to high speed. I live in deep sticks Ontario, and we have only had dialup until a couple months ago. It used to take me 20 mins to download a 3 minute MP3, now it takes less than a minute. 

So, point being, I guess my PC is and Feisty have set themselves up pretty well by default. 

Besides, when I read your posts w/all the command lines, I get dizzy. Frontal lobe goes dead.

---

### Post by slarrabe on 2008-01-28
I tried editing my /etc/sysctl.conf file but it wouldn't let me save it.  I got the following error:

Could not save the file /etc/sysctl.conf.
You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again.

---

### Post by ferd on 2008-02-05
Try  sudo gedit  /etc/sysctl.conf .

---

