---
title: "Sudden loss of internet, but not completely, after installing wicd"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by Luxx on 2014-04-05
My network connection was driving me nuts. For some reason it started trying to connect by wired connection even though it NEVER has. The wireless connection kept disconnecting and Network would show my network as being out of range. This is a dektop. Nobody is moving it. I Had to connect to my network as though it were a hidden network, which it isn't, but after an hour or so it would disconnect again and I would find a computer icon with an x on it saying my wire was disconnected. 

So I installed Wicd and removed Network Manager. I didn't realize until later that Network was a different thing. I was able to stream a tv show from my PLEX server to my Roku last night without interruption. But this morning I can't connect to anything. I am connected and can download torrent files, but can't get Google to come up in a web browser, or most websites, but I CAN get my web-based email to open in a browser. All other pages I've tried are unavailable. I can't install Network Manager or anything else in Software Center or by Terminal. I can't figure out what is going on. I have internet access but can't use it except for email and torrent downloads?

I have spent the day looking for similar issues online and can't quite find the same thing. I can't find anything that looks wrong, it just doesn't work. It was fine last night. What could have happened and how do I begin to get it working again?

My housemate's computer on the same network is working just fine in XP.

---

### Post by steeldriver on 2014-04-05
If you can connect to some places / service but not others, the things I would start checking are

[LIST=1]
[*]name resolution 
[*]routing 
[*]MTU 
[/LIST]

---

### Post by Luxx on 2014-04-05
OK .... I've been at this all day. What specifically would you suggest I look at?

I couldn't find anything that looked wrong. It all seems normal, except I no longer have access to any websites.

I'm connected to the network, the network is connected to the internet, but I can't access the internet. I can download old torrents, but VERY slowly.

I saved all the crap I tried in gedit and was going to paste it in an email and save it, then open my email on this other computer and paste all that stuff here, but I can't get into my email anymore either. It's 8 pages printed out. I wouldn't mind starting all over again, but "check stuff" doesn't really help. I have been checking everything I can think of and I just can't think anymore.

---

### Post by Iowan on 2014-04-05
"Check stuff" isn't the advice offered. Specifically, if you have partial Internet access, we need to learn where the breakdown occurred. 
Can you "ping" by IP address (e.g. 8.8.8.8)?

---

### Post by steeldriver on 2014-04-05
1. pick a website that isn't loading and try to resolve its hostname using dig, and/or ping it by hostname
```

dig google.com

ping google.com

```

2. look at the routing table with route and/or ip route - is there anything funny about the masks? sometimes a mistyped mask octet can cause intended external traffic to be routed within the LAN instead

```

route -n

ip route show

```

3. either just keep reducing the connection MTU to see if it helps, or actively probe the maximum unfragmented size using ping

```

ping -s **1472** -c 4 -M do google.com

```

(the number after the -s is the MTU minus 26 bytes i.e. 1472 above corresponds to MTU = 1500)

---

### Post by Luxx on 2014-04-05
Holy crap, your suggestion to check stuff DID help. I really didn't think I had it in me to make any more synaptic connections in my brain at this point, but you got me there. Although I have been looking at everything my network could possibly be doing, the fix was simple.

So before anybody goes through eleven hours of hell, PLEASE try reconfiguring resolvconf first.
```
sudo dpkg -reconfigure resolvconf
```

---

### Post by Iowan on 2014-04-05
When/if you decide a solution has been found:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Luxx on 2014-04-05
So, yeah..... I'll mark this solved in a bit here, but first to answer the questions above.

I could not ping names, but I haven't been able to ping names in Terminal for about 4 years. Today I was having intermittent success with IP addresses, which was more confusing than conclusive. 

The masks looked normal.  I was not familiar with steeldriver's #3.

I suspected the problem was somewhere in that ballpark. That can seem like a pretty big ballpark. Thanks for your help.

---

