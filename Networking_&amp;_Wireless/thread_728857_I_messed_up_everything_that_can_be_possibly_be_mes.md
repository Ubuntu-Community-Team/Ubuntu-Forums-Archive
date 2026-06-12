---
title: "I messed up everything that can be possibly be messed up - iptables, dnsmasq etc."
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by thomas7.10 on 2008-03-19
Hi!

All began with a quiet small problem. I had no incomming connections on Bittorrent clients. My computer ran as a router und i had to set up lots of things following HOWTOS to get it to work beside others firestarter.
So now my computer is connected to a router via WLAN and i had all router settings correct when it comes to things like UPnP and port forwarding.
But I still hadn't got incoming connections on bittorent clients.
So i flushed iptables. But then the internet connection didn't work at all. Then i restarted the interface and it worked again but all the iptables appeared again.
That was when i remembered firestarter. I unisntalled it with the standard GUI installation tool and seemed to has been uninstalled. But the iiptables still kept appearing when i restarted the interface. So i installed firestarter again and clicked on Stop firewall on it. It stopped and i got incomming connection. Stupid as i am i wanted to get totally rid of all firestarter stuff. So i used "gksudo gnome-search-tool" and searched for firestarter (even hidden applications). Then i used "gksudo nautilus" to delete all of them even after putting it to the /root/.Trash i deleted them there. I flushed iptables again and started the connection.
The first seconds it seemed to work fine but then i got lot's of package lost and i couldn't connect to the internet.
I'm not quiet sure if this was before or after i was running "dnsmasq --flush" i can't really tell why i was running that. Probably because i was remembering a command from [that]("http://ubuntuforums.org/showthread.php?t=91370") tutorial wrong and mixed it up with MASQUERADE.
So that's where i am now.

It can't depend on the router. I installed two different firmwares and tried with other computers. As well it can't depend on my hardware. I tried with two different ethernet cards in my computer and with a wireless adapter.

I would be unbelivebal thankfull if someone could help me with that.

Thomas

PS: I know it's kind of crossposting but the problemati changed under the time i was dealing with it. My first thread when all started was [that one]("http://ubuntuforums.org/showthread.php?t=727821").

---

### Post by thomas7.10 on 2008-03-19
Ok i have no idea why but when i deactivate apparmor then the internet works. Does any know what apparmor does?

I was just reading about how linux works and i came to the point that everything that runs kind of automatically is in the folder /etc/init.d/ well and there i started with A and looked if the internet works if i stop the service.

But now i have no idea what apparmor is and what it is doing...

---

### Post by notwen on 2008-03-19
[AppArmor]("https://wiki.ubuntu.com/AppArmor") is a pretty solid allow/deny connections application.  Any connection, whether it be outbound or inbound must have permission from AppArmor or else it won't connect.  Read more about it in the Ubuntu Wiki link provided above.  Hope this helps.  =]

---

