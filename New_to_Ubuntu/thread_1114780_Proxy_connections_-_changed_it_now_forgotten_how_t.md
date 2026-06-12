---
title: "Proxy connections - changed it now forgotten how to change it back"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by loobyloo on 2009-04-03
Hi
I need to edit some mp3s so I thought I'd use Audacity. When I go to install it from the terminal using apt-get I get the following error: 

cliff@cliff-laptop:~$ sudo apt-get install audacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libflac++6 libwxbase2.6-0 libwxgtk2.6-0
Suggested packages:
  ladspa-plugin
The following NEW packages will be installed
  audacity libflac++6 libwxbase2.6-0 libwxgtk2.6-0
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 6547kB of archives.
After this operation, 18.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to wwwcache.lancs.ac.uk (194.80.32.8)]
---------------------
It's that last line that's the problem: that's the proxy server which we have to use at university, but I'm at home now.  I cannot for the life of me remember how to change it back.  

I've got my browser set up to connect without a proxy, likewise in System > Preferences > Network Proxy that's also got Direct Connection to the Internet ticked.  But obviously something's telling it to use the Uni's proxy.  Could anyone remind me where to change the proxy so that I can install this program?  Thank you.

---

### Post by loobyloo on 2009-04-03
OK, no ignore that!

System > Preferences > Network Proxy > Direct Connection > Apply Systemwide? > Apply

Done.

---

