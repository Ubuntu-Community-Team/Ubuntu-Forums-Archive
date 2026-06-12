---
title: "Ubuntu Telnet Error (Mozilla Firefox)"
date: 2015-01-12
forum: Networking &amp; Wireless
---

### Post by Muhammad_Ausaf_Ali on 2015-01-12
I am running Ubuntu 14.04 in VMWare Player with a bridged Adapter. I installed another VM in Ubunutu which can be accessed from Mozilla Firefox. The web page opens but when I click certain links in that webpage (which require telnet client to open automatically) no client opens and Firefox gives the error:

The address wasn't understood

Firefox doesn't know how to open this address, because one of the following protocols (telnet) isn't associated with any program or is not allowed in this context.

    You might need to install other software to open this address.

Whereas I have installed putty in Ubuntu...

Waiting eagerly for your kind reply.

---

### Post by bashiergui on 2015-01-13
The changes in Firefox 3 broke links using telnet and ssh. See this for instructions on how to configure ff to use telnet links:
[http://www.tolaris.com/2010/08/23/enabling-telnet-and-ssh-urls-in-firefox-for-linux/](http://www.tolaris.com/2010/08/23/enabling-telnet-and-ssh-urls-in-firefox-for-linux/)

Or see your parallel thread ;)
[http://askubuntu.com/questions/572751/ubuntu-14-04-mozilla-firefox-telnet-error](http://askubuntu.com/questions/572751/ubuntu-14-04-mozilla-firefox-telnet-error)

---

