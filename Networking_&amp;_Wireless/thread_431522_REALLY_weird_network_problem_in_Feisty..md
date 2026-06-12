---
title: "REALLY weird network problem in Feisty."
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by bodgetastic on 2007-05-03
So I had Edgy installed on my work laptop, an HP/Compaq nx6325, so far so good.  I was amusing myself by telling anyone who commented on the GNOME look that it was Vista, which seemed to confuse them less. (I'm a combination video editor/cameraman/tech/dogsbody so I work with a lot of the creative types).

Tried an upgrade to Feisty last week, everything looked fine and stable until I tried to access the web.  DNS lookup worked, firefox just hung 'waiting for site xxxxx....'.  So did opera, so did Synaptic when I started trying to muck about with packages to fix it.

The really weird thing is, SSH worked.  FTP worked.  SMB on the internal office network worked.  Avahi worked.  Exchange in Evolution worked. And, the google website worked!  Google search gave me results no problem, my gmail worked.  Try clicking on any links and... nothing.  Just firefox ticking over consuming CPU.  Almost like I'm firewalled out, but checked iptables and found nothing.

Rebooted into my old kernel from Edgy and it worked fine!  But my sound didn't (complaining of missing symbols in relevant ALSA module).  Then the machine started locking up at random - proper, complete kernel buggery (which in over 8 years of using Linux I've never seen before!)  So I'm back on windoze at the moment till I get some bright idea to try to fix it.

Am a little suspicious of the hard-drive because of the lockups and sound module issues, but everything was working fine before.  Have tried re-installing kernel using Synaptic but no cigar.  :mad: 

To be honest, am all out of ideas - guess I'll just blank it and try a clean install when I have time - which will be some time next year at this rate!

Any help gratefully received.

---

### Post by Peque on 2007-05-03
well having the exxact same problem - but if I use kernel 2.6.17.11 it all works - but using v. 2.6.20.15 gives me the same problems aboiut getting the pages ( Even the administration interface on my router) I cannot access - loding like 20% of the site - and just stands there. 

Using the kernel - is a hudge problem caurse I want to use VMware so that I have an Windows machine that I can Use for other purposes during a work day.

So any solution will be gladdly accepted... somewhere somehow there must be a difference between the 2 kernels.

---

### Post by bodgetastic on 2007-05-04
Well, tried something else yesterday - downloaded the 'official' kernel 2.6.21.1 from kernel.org.

Loaded in the default settings from the Feisy kernel (in /boot/) and built it - same problem, system working exactly the same.

Ho hum.  Presumably the error is something in the kernel configuration.

Only clue is, that when I did a 'netstat' it showed some connections from eth1 (my unconfigured bcm43xx wireless) to the website addresses as well.  But removing eth1 from the routing tables didn't help.  Guess this might have something to do with it, if the new kernel configuration is trying to load-balance across the interfaces :confused: No idea if it should or not...  Oddly enough, if I try to 'down' the eth1 interface it tells me that it's not configured, despite showing an IP adress and it's in the ifconfig list.

If I get time then I might try configuring the kernel from scratch, but afraid my schedule's looking so busy I might just downgrade back to Edgy :(  Shame really.

Will keep this thread updated if I find anything else out...

---

### Post by stimpack on 2007-05-04
For me Firefox works, all other network connections work, but Konqeror and Opera fail to laod any website apart from google search.... Problem new in feisty

---

### Post by lkereszt on 2007-05-07
Check this:
[http://kerneltrap.org/node/7962](http://kerneltrap.org/node/7962)

In short:
"Could there be a buggy firewall corrupting your TCP packets?
March 28, 2007 - 1:29pm
farnz

IIRC, the default TCP window has changed in that interval. If there's a buggy firewall between you and your destination, it might be stripping out the TCP window scaling option, breaking TCP badly.

To test this assumption, try echo 0 > /proc/sys/net/ipv4/tcp_window_scaling as root. If this fixes things, there is a firewall or NAT box between you and the destination machine that's badly broken, and that's deliberately breaking TCP for you; you will have to accept lower TCP bandwidth, and higher latencies for interactive work."

It worked for me!

---

### Post by tssooma on 2007-05-07
I have been unable to reliably connect to the network with feisty. Two entirely different machines, which otherwise work perfectly with Puppy.
I reinstalled the earlier version of the network manager (suggested by some bright spark on a Google search) and that sorted the problem The problem is in Feisty in the networking components, probably in the network manager from my experience.
This problem is widespread; why have we not heard anything positive as to how to sort it?

---

### Post by stimpack on 2007-05-10
Update: my problem was related to network-manager. I had set KNetworkManager to offline mode so it used Wired Ethernet instead of auto-using my neighbours open wifi.

Setting it to Online bit Wireless disabled fixed it. Though annoyingly the bar shows me connected to my neighbour, when I am really using good ole wires.

---

