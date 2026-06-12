---
title: "Wireless issue with DNS and with Intermittent Connection"
date: 2005-05-08
forum: Networking &amp; Wireless
---

### Post by grakhul on 2005-05-08
I have a laptop with a pcmcia card.  Make and Model is a AT&T 6500 802.11 b/g card. The card pretty much works with no problem.  I am able to surf the net.  I have two problems that continue to plague me though.
Issue #1: My internet connection keeps dropping on me.  This will usually happen once every hour and it last for about 1 minute.  
Issue #2: No matter how many times I go into the network settings and edit my DNS server then save.  Once I open up the network settings again, the DNS servers have reverted back to 192.168.10.1.  This is the IP of my motorola router.  I also think this is the reason my internet connection is slower than average and why I keep getting dropped every hour.

I have edited the Resolv.conf file many times through the terminal.  Then when I go into the graphical network settings, the new dns servers are usually there.  About 5 minutes go by and I will check the DNS servers and they have reverted back to my routers IP 192.168.10.1.   

Why is Ubunut hell bent on using my router as the DNS server?  It does work, but I think this is why I keep getting dropped.  Not to mention that it seems that the routers DNS is slow.

Why do I keep dropping a connection every hour?

Why is my Broadband connection so slow.  It seems that it is slow when resolving domain names.  Any help would be appreciated.

This does not happen when I am "hardwired" to my router through my ethernet interface (802.2 RJ 45)

---

### Post by grakhul on 2005-05-09
I fixed it.  I pretty much followed a tutorial that I found on another page and it worked fine.
DIsabled all of the protocols I dont use IP v 6, IPX, apple talk etc...

And then I modified a script that rewrites the resolv.conf file by the system.

---

### Post by speckone on 2005-05-20
Could you post the page where you found the resolution to this issue?  I am having a similair problem and would really appreciate it.  Thanks.

---

### Post by grakhul on 2005-05-20
First do this:
> OK, this disabled ipv6 for me:

Created a /etc/modprobe.conf file with the following lines:
alias net-pf-10 off
alias ipv6 off

Now I do not have ipv6 module loaded! Hosts seem to resolve much faster now. 

Also do this:
> in firefox address field type **about:config**.  This will bring up your firefox config file.  Do a search in the filter field for **ipv6**.  This will bring up the ipv6 settings.  Make **network.dns.disableIPV6  TRUE** 

There is also an alias file in your /etc directory that will have to be edited to disable IP v6.  I forget off of the top of my head.  You will have to place comments in front of the protocols you want to disable.  **#**

Keep in mind that it may not be IPv6 causing the issue in UBUNTU.  Appletalk, IPX/SPX is also enabled and that is not causing any problems.  If this does not solve your issue, you may have to look elsewhere.

---

