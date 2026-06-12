---
title: "[SOLVED] Can someone help me diagnose SLOW Transmission?"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by NEUR0M4NCER on 2008-10-14
Hi all - pleasingly, this is the first post i've had to make in quite some time (i'm sure that'll change when Ibex comes out :p).

My problem is that i'm getting - on average - about 5KB/s download speed in Transmission BT... I've been through the help pages on the [Transmission](http://www.transmissionbt.com/) site, but no luck.

The torrents i'm d/l'ing are popular, with plenty of seeds (also similar number of leechers, so no issue there either). I've set my wireless router to forward the port to Transmission, which confirms this in EDIT > PREFERENCES > NETWORK... When downloading from repo's I get 850KB/s and above... Am I missing something?

Several hurdles that might be causing an issue: Ubuntu64, RT2500 Driver (compiled from source, working fine), Broadband Provider? Sky (UK).

---

### Post by anoble66 on 2008-10-14
sounds as if your ISP is throttling back your bitorrent downloads....its fairly common for an ISP to do this.  Some providers will let you download a certain amount before throttling your connection back, some will be instant.

---

### Post by NEUR0M4NCER on 2008-10-15
Thanks for the reply - does anyone know if this is a known issue with Sky Broadband in the UK?

**edit**
Okay, so I checked around a little, and it *appears* that Sky does not use traffic throttling or shaping for any application... Don't know whether I believe that, but, maybe it's better to look at something else as the culprit first?

---

### Post by NEUR0M4NCER on 2008-10-16
Does anyone else have a clue as to the poor speeds?

---

### Post by NEUR0M4NCER on 2008-10-20
... help?

---

### Post by guitsy on 2008-10-20
change ur browser to seaMonkey.sometimes this will help u.

---

### Post by NEUR0M4NCER on 2008-10-22
Thanks for the suggestion, but i'm not too sure how changing my browser would affect the transfer rate of the Transmission BitTorrent client?

---

### Post by WingZero624 on 2008-10-23
1. Try manually setting your upload and download speeds to 70-80% of your total bandwidth.  I'm not sure exactly how this works, but someone on another forum stated that this did the trick.

2. Try experimenting with checking the "ignore unencrypted peers" box, and see if that will change your speed. Alternate between these two, and then try them both. The only downside to enabling it is that you could lose potential remote connections to you, but this is also to cover the base if by some strange perchance, that your ISP is indeed throttling you.

3. Disable UPnP. I'd try this as well, because you have manually forwarded your ports. Enabling this, tells Transmission that you are wanting it to talk to your wireless router make the forwarded ports, and it might be confusing Transmission.

If all else fails, the only other option is to either try another BT client.
Generally people have good luck with Deluge, and uTorrent if they want to run it under Wine. 
Last I remember, TrBT doesn't support Mainline DHT trackerless support..unlike Azureus and uTorrent/BitTorrent, so that might be part of the problem there.

Hope this helps.
Mario

---

### Post by caleb12 on 2008-10-23
Just out of curiosity, are the slow speeds only in Transmission or is it consistent in all apps. 

I happen to end up on a lot of different networks for work, and this last one was using a Cisco router that had not been configured to handle TCP Window Scaling. After pounding my head against the wall for several hours, I came across this thread:

[http://forums.fedoraforum.org/showthread.php?t=181399&page=3](http://forums.fedoraforum.org/showthread.php?t=181399&page=3)

which offered a simple solution:

```
edit /etc/sysctl.conf and add the following lines

#Control TCP Windows Scalling
net.ipv4.tcp_window_scaling = 0

```

Apparently, Ciscos don't support TCP Window Scaling by default so if it is not enabled (as was my situation this week) it will pretty much bring your connection to a grinding halt. 

Don't know if this is your situation or not, but hey... it's worth a try.

---

### Post by isparkes on 2008-10-24
Just to add my 2p...

I also have the same symptoms, also on x64, also with a wifi driver compiled from source (madwifi).

My provider is Tele2 in Italy.

I'm going to play around with different torrent clients and move over to a wire connection to see if I can get behind what is going on.

---

### Post by NEUR0M4NCER on 2008-10-26
Thanks all for the input.


@ WingZero

1. Yeah, set the upload speeds to 70% - apparently, it can overload the router at 100% (so I read)...

2. Tried 'Ignore Unencrypted Peers' - doesn't seem to make any difference, although I left it on, as it doesn't *harm* d/l speeds either.

3. Now this is interesting - you say that manually forwarding ports whilst using uPNP at the same time might cause an issue - i'll look into that one.

Also considering different Torrent client, although I had similar speeds with the old default client in Feisty and Gutsy.


@ caleb12

The router that Sky provide is a branded Netgear, so i'm not sure if that would help, but i'll add it to the list of 'Things to try if all else fails' - Thanks for the suggestion.


@ isparkes

Let us know if you have any success!

---

### Post by College_Trained on 2008-10-31
I've had the same problem with Transmission. You should use Deluge (deluge-torrent.org). That's what I just switched to and it's literally 15-20x faster. Normally I'm a huge skeptic when someone says something is that much better but it's true. I'm NEVER going back to Transmission. Ever.

P.S. I also tried running uTorrent under Wine but that doesn't work either.
Your best bet is to switch to Deluge.

---

### Post by NEUR0M4NCER on 2008-11-03
Problem (kinda) solved:


[Azureus Vuze](http://www.vuze.com/app) is available for Linux - it's what I always used to use before I made the switch from MS, and it's cracking. Much faster transfer speeds, very configurable, and pretty... but to be honest, it's best to switch to 'classic' view, because the media view is quite slow, and less intuitive.

I highly recommend Azureus to anyone looking to get better torrent speeds.

Marking the thread solved.

---

