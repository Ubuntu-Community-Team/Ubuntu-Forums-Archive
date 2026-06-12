---
title: "No dial up connection 6.10"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2006-11-24
I have install the drivers for my modem card from Linuxant and it is a Conexant chipset.  I have contacted Linuxant and they sent me to the page below to correct the problem. I don't have any file on my drive that is OPTIONS.  They said it was a known flaw in Ubuntu 6.10.  Anyone know how I can fix the problem.

Hi,

the source of the problem is:

---
Nov 23 18:29:34 ronbrooks-desktop pppd[11072]: The remote system is 
required to authenticate itself
Nov 23 18:29:34 ronbrooks-desktop pppd[11072]: but I couldn't find any 
suitable secret (password) for it to use to do so.
Nov 23 18:29:34 ronbrooks-desktop pppd[11072]: (None of the available 
passwords would let it use an IP address.)
---

This is a known problem on Ubuntu 6.10 and this problem is not related 
to the modem driver. Perhaps that the following information will help 
you solve the problem:

[http://docs.kde.org/stable/en/kdenetwork/kppp/faq.html#id2560641](http://docs.kde.org/stable/en/kdenetwork/kppp/faq.html#id2560641)

Even if you are not using kppp as a dialer, since this is a generic 
problem, the solution described will probably work.

Alternatively, you should contact other Ubuntu 6.10 users or 
developers, 
it is possible that they have a very specific fix for this known 
problem.


10.1.2.	pppd died - The remote system is required to authenticate itself ...
	Typical error message in system log:
pppd[699]: The remote system is required to authenticate itself
pppd[699]: but I couldn't find any suitable secret (password) for it to use to do so.
pppd[699]: (None of the available passwords would let it use an IP address.)
As far as I can tell there are two causes for this problem: 
•	/etc/ppp/options contains the auth option. Simply put a # comment in front and try again. 
•	Your system already has a default route. Have you set up a local network? In this case recent versions of pppd will behave as if auth had been specified. To override this you may add noauth to the pppd arguments in kppp' setup dialog. Alternatively you could take down the local network prior to dialing in. I'd be thankful if someone could provide instructions on how to peacefully combine the two network connections.

---

