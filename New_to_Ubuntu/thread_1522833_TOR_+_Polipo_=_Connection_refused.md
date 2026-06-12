---
title: "TOR + Polipo = Connection refused"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by TabbyB on 2010-07-02
I have never set up a proxy before. I'm brand new to Ubuntu. I am trying to use Polipo and TOR withe Firefox.
I am running Ubuntu 10.04 with Firefox 3.6.6.
I have installed TOR and Polipo and set them up per [http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

Whenever I try to use TOR, thru torbutton in Firefox I get the following error when trying to visit a website:

504 Connect to [www.somewebsite.com:80](www.somewebsite.com:80) failed: Connection refused
The following error occurred while trying to access [http://www.somewebsite.com/:](http://www.somewebsite.com/:)
504 Connect to [www.somewebsite.com:80](www.somewebsite.com:80) failed: Connection refused
___________________________________

Generated Fri, 02 Jul 2010 14:45:00 by Polipo on localhost:8118


I've done a little tinkering and reading FAQs for a few hours but I'm at a loss. Any guidance on how to get TOR + Polipo up and running would be appreciated. Thanks!

---

### Post by mkvnmtr on 2010-07-02
I seem to remember that I had to restart to get everything to work.

---

### Post by TabbyB on 2010-07-02
thanks, reboot, system power down/up, log off and back on....all with no luck.

---

### Post by bodhi.zazen on 2010-07-02
> **TabbyB said:**
> thanks, reboot, system power down/up, log off and back on....all with no luck.

I can not determin the problem from what you posted.

Is polipo running ?

How did you configure polipo ?

Honestly, the easiest way to "install" TOR, IMO, is to use the bundle:

[http://www.torproject.org/torbrowser/](http://www.torproject.org/torbrowser/)

Download the lniux bundle. It is sweet =)

---

### Post by stevenwscott on 2011-06-11
If you built/installed TOR manually, you need to start it manually or put it in the system startup ssequence/rc list. 
just run tor to get it going.

---

