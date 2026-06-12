---
title: "virtual server can only be seen on host: invisible to network"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2008-07-12
Hi all.

I've got apache2.2 running on my desktop pc. It runs ubuntu.

I've also got a laptop in my room, and there are other machines in the household, all on the same network and subnet.

All machines can see the apache server's default host.

However, only the actual physical host can see the virtual servers.

All requests for [http://defaulthost](http://defaulthost)
get service from that host

The virtual server is listed in my /etc/hosts file.
So, by my understanding, http requests for [http://virtualserver](http://virtualserver) 
should get service from that server, right?
But only the machine hosting that server can see virtualserver.

Even the virtual windows machine hosted on the desktop can't see [http://virtualserver](http://virtualserver)

What am I doing wrong here?

Thanks

---

### Post by HalPomeranz on 2008-07-12
When you say, "The virtual machine is listed in my /etc/hosts file", which /etc/hosts file are you talking about?  You must have it listed in the hosts file of each machine on your network where you want to use the URL [http://virtualserver](http://virtualserver).  It's not enough to just put it in the /etc/hosts file on the machine where the virtual server is running.

---

### Post by bobdobbs on 2008-07-12
> **HalPomeranz said:**
> When you say, "The virtual machine is listed in my /etc/hosts file", which /etc/hosts file are you talking about?  You must have it listed in the hosts file of each machine on your network where you want to use the URL [http://virtualserver](http://virtualserver).  It's not enough to just put it in the /etc/hosts file on the machine where the virtual server is running.

Thanks Hal.
:)

This of course brings other questions to mind.

Like, how do I keep my hosts file up to date ?

My physical web host will occaisonally drop off the network and come back on. In the process, it will change it's IP address. So I now must find a way to automate this.

Thanks for the advice on the hosts file. I would be further grateful if someone could point me to more information on how to keep my hosts files updated.

Cheers

---

### Post by HalPomeranz on 2008-07-12
> **bobdobbs said:**
> 
This of course brings other questions to mind.
Like, how do I keep my hosts file up to date ?


Thus you have discovered the reason why the Domain Name Service (DNS) was invented back in the early days of the Internet. :-) The idea behind DNS is that you maintain all of your host information in one place and then make that information available to other machines on your network.

I found this thread that might be some help to you:  [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

### Post by bobdobbs on 2008-07-12
Thanks for the pointer.

I may need that information for the future. However, I chose a different solution.

Fortunatly, my DSL modem/router, a Thompson SpeedTouch, by alcatel, has a configuration option that helps.
The Speedtouch has an option that checks the MAC address of a device and then, if so configured, will always give it the same IP address.

This saves me from learning bind.
(As much as I like knowing how to work things under the hood, I also like the option of being dumb and just getting the job done.:) )

Again, thanks for the pointer.

---

