---
title: "Finally got my Belkin usb adapter (rt73) to work, but..."
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by iPLAYwithFIRE on 2007-04-25
Ok, I finally have a working connection with my Belkin usb wireless adapter (f5d7050).  But I'm not sure if it was the best way to go at it...

I tried using this walkthrough:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

But, I couldn't follow along very well - I'm fairly new to linux (but I'm not a complete idiot).

I would get hung up on this:
```
sudo aptitude install linux-386
```

It would say something like "Couldn't find any package whose name or description matched 'linux-386'" - I figured it was some incompetence on my part.

I then removed network-manager, network-manager-gnome, dhcdbd, and libnl1-pre6 via Synaptic Package Manager.  Instantly I can open up firefox and browse the web.  But of course upon deletion I can no longer check my signal strength, etc...  **Even though it solved my problem, is it the most viable solution?**  Should I have done something different? It seemed nothing was working to get a connection.  When I first plugged it in, it showed the networks, but it coudln't connect to one.  I thought it was odd since my network is open (no wep key).

So can I continue like this?  Or did I compromise something with the deletion of network manager?  I wouldn't mind seeing my signal strength... but if it works, it works...

---

### Post by chili555 on 2007-04-26
Some people swear by NetworkManager; some people swear *at* it! I have used it successfully, as well as manual configuration and Wicd. All have their advantages and disadvantages. They are all just GUI front-ends for iwconfig and scan. None, as far as I am aware, do anything you can't do yourself at the command line.

I think you will only need a manager if you are roaming from home to school to coffee shop. In my case. I roam from family room to breakfast room to porch. Selecting which network I want to connect to is not an issue.

If you use all the managers, you will see that each seem to have a different idea of signal strength. On my laptop now, Wicd reports 54%. The network icon you can add to your panel reports 87%. Iwconfig reports 'link quality 52/100.' Sounds like Wicd is correct.

You stated it correctly: if it works, it works. If it meets your needs, there is no need to fix it.

---

### Post by iPLAYwithFIRE on 2007-04-26
Well I installed wicd, because I really wanted a graphical UI - because through the terminal I have no idea how to connect to a different network.  And it works without problems (so far, I haven't restarted my comp).  And for some reason I have to unplug my usb adaptor because while it's booting, it hangs when it's plugged in.  I have to wait till it boots, then I plug it in, and then wait about 5 min to get a connection.  But once I get a connection, it stays strong (better than my XP on my laptop!).

---

