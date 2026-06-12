---
title: "Unable to reconnect after router power cycle"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by aulismedia on 2008-04-14
I use one of the PCs (Windows based) on my home network as a dedicated p2p machine, that generated quite a lot connections and leads to frequent connection drops on the router (Linksys WRT160N, it just not operationable and not pingable from either wired or wireless machines). On a given day, I need to power cycle the router up to 5 times. Most notably and disturbing, I turn it off and on every morning after waking up. Tried many routers, probably a dozen, with no success, they all drop connection after some time. Of course, the more files I have in P2P rooster, the more often it happens. But this is something I already got used to and the problem is such is the following.

On my other laptop I'm using Ubuntu 7.10, and after every router power cycle, Ubuntu can't connect to the wireless network. It does see it in the list of available networks but tries and tries to connect to it indefinitely. I have to reboot the computer in order to make it log into the network again. Whereas Windows box automatically logs into it.

Is there any way to reconnect Ubuntu without having to reboot the computer? Some command line magic maybe?

Thank you.

---

### Post by ryanhaigh on 2008-04-14
iwconfig is the command you want to look at for connecting to a wireless network from the cli. i know it may not be feasible but you might want to look at getting an X10 switch to powercycle your router whenever you can't ping google.com or something using a bash script. You may also want to consider restricting the number of connections in whatever p2p app your using.

---

### Post by aulismedia on 2008-04-14
When the rooter freezes, it's not even pingable and I don't see how X10 can reboot it then.

So, with iwconfig I'll be able to stop unsuccessful attempts to connect, and reconnect using new parameters? And Netwok Manager applet will catch up with the new connection?

Thanks for your reply!

---

### Post by ryanhaigh on 2008-04-14
With X10 you would try to ping google/router and if the ping fails you would use the computer to send a signal to a X10 controlled switch attatched to the router to powercycle it. This thread gives some info on what you might need but also mentions that X10 may be unreliable and you could achieve the same thing with a serial/parallel interface and a relay.

[http://answers.google.com/answers/threadview?id=261662](http://answers.google.com/answers/threadview?id=261662)

As far as iwconfig/network manager I don't think they behave in the manner you are expecting. There are other wireless managers that use iwconfig I think wicd is one such tool but there may be others also.

---

### Post by aulismedia on 2008-04-15
Thsnk you, but this is taking me too far from what I was asking for. I needed some simple console command that would allow me to reboot wireless connection without restarting the PC. 

I'll take a look at iwconfig next time it happens.

---

