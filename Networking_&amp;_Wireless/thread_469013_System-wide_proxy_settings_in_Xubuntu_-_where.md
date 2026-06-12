---
title: "System-wide proxy settings in Xubuntu - where?"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by dstubb on 2007-06-09
So I've installed Ubuntu 7.04 on several older iMacs with few problems.  Ubuntu's GUI has a control panel for this. However, I put Xubuntu 7.04 on one and can't find where to enter network proxy settings.  Without it I can't download updates, etc.  Is there a control panel somewhere or do I have to do it from the command line?  If the latter, how?  Thanks

---

### Post by airtonix on 2007-06-15
to change ip settings of your network card : 

system -> admin -> network

or to manually edit : 

> sudo nano /etc/network/interfaces

to change the proxy that you want to use : 

system -> preferences -> network proxy

not sure what to edit manually here.

---

### Post by xtalker on 2007-07-09
Using **Xubuntu 7.04**, still can't figure out how to set the network proxy!!

>> *system -> admin -> network*

I only see *System -> Network *and no mention of the proxy setting.

>> *system -> preferences*

I don't see this menu at all.

I'm sure that I'm missing something real basic here, please help!

Bob

---

### Post by Glenhawk on 2007-08-02
I am running into this problem as well.
Would I be correct in assuming that Xubuntu does not actually have a "Network Proxy" GUI?
I am now trying to configure it manually

---

### Post by kalin_s on 2008-02-29
The thread is old, but on Xubuntu 7.10 you can go to 
Accessories>Appfinder
and Network Proxy is in the list of applications.

---

