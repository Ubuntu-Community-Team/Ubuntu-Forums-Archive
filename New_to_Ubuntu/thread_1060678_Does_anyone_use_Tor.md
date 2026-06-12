---
title: "Does anyone use Tor?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Gotaro on 2009-02-05
I can't get Tor to work..  Would anyone know how to help me?  I've configured the privoxy config file, though I'm not 100% sure it was correct.  I'm connected through a network, but I can't actually find where it shows my IP from in Linux.  The reason I think I might need to know is to change this line:
listen-address  127.0.0.1:8118
to my IP assigned from the network..  But if that isn't what I'm supposed to do, then I don't know..

I don't even know how to tell if Tor/Privoxy are running!  I can sudo privoxy, and it will start..  but if I try to run Tor from a terminal, it says it can't bind to the port and is probably already running?

(Forgot to include this: the symptom I have is no apparent connection to the internet after enabling Torbutton.)

---

### Post by cmnorton on 2009-02-05
For starters, I would look in your logs to see when your network connection is  dropping. 

Start with sudo tail /var/log/syslog and sudo tail /var/log/messages right after you lose your network.

Edit:

You've probably already been to this site, but just in case you have not, here is a link.

[http://www.torproject.org/documentation.html.en](http://www.torproject.org/documentation.html.en)

---

