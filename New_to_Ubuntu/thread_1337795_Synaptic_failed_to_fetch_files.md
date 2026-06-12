---
title: "Synaptic failed to fetch files"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by labrat256 on 2009-11-25
I frequently use Ubuntu 9.10 on my laptop both on and off my university campus and when it is used on campus, it has to go through their proxy server. When I use it at home, I (obviously) do not want it to go through the proxy server, so I set the proxy settings to "Direct connection to the internet". I have set the proxy settings in Firefox, in System>Preferences>Network Proxy and in Synaptic Package Manager>Settings>Preferences>Network.

Yet when I try to download any files through the package manager, it takes a long time and brings up this report:

W: Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/main/n/nspr/libnspr4-dev_4.8-0ubuntu1_i386.deb](http://ubuntu.virginmedia.com/archive/pool/main/n/nspr/libnspr4-dev_4.8-0ubuntu1_i386.deb)
  Could not connect to wwwcache.lancs.ac.uk:8080 (194.80.32.9), connection timed out [IP: 194.80.32.9 8080]

where wwwcache.lancs.ac.uk is the proxy server. 

Where have I forgotten to change back? What else is there to change in order to make it stop trying to find the proxy server and to try to directly link?

---

### Post by oldos2er on 2009-11-25
If you're using Synaptic, check the menus Settings, Preferences, Network tab.

---

### Post by pi.boy.travis on 2009-11-25
You shouldn't have to have all those settings.  The settings in Network Proxy should apply globally. . .

---

### Post by labrat256 on 2009-11-25
I did change the settings in synaptic, as I said in my original post. As for globally changing the settings, I thought so too! It seems not though, even after pressing "apply systemwide" on the network proxy preferences. 

I was on campus when I updated from 9.04 to 9.10. Could this be a cause?

---

### Post by Shpongle on 2009-11-25
try changing your download server location

---

### Post by Shpongle on 2009-11-25
system ->admin-> software sources , the server location is on the first tab

---

### Post by labrat256 on 2009-11-25
Nope, changing my server just makes it look for a different server behind the same non-existent proxy server, as shown by this response:

W: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.2-1karmic1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.2-1karmic1_i386.deb)
  Could not connect to wwwcache.lancs.ac.uk:8080 (194.80.32.8), connection timed out [IP: 194.80.32.8 8080]

---

### Post by labrat256 on 2009-11-30
Does anybody else have any further help, or should I place this into a 'main support' forum?

---

### Post by andywilko on 2009-12-02
Hey, I'm at Lancs uni too and have just installed Ubuntu. To update successfully, I went to System>Preferences>Network Proxy and selected manual proxy config, using wwwcache.lancs.ac.uk and port 8080, and then added *lancs.ac.uk to the ignored hosts list. Maybe this is where you can change the proxy settings to Direct or Auto, I'm pretty new to this but hope it helps.

Andy

---

### Post by totality on 2009-12-24
Well im not at a uni but have moved to a different wireless point and I get the same problem.  Changing servers makes no difference!  Connection times out on updates or trying to install programs from the respository.

Absolutely shocking that simple things like this dont work!  I am behind a home router for each thing so no network settings have needed to be configured.  Only thing could be the internal ubuntu firewall which Iturned on but is now off?  Cant see any difference though?  Internet works fine apart from that on this laptop so its not the access point.

---

### Post by youknowit on 2010-01-09
> **andywilko said:**
> Hey, I'm at Lancs uni too and have just installed Ubuntu. To update successfully, I went to System>Preferences>Network Proxy and selected manual proxy config, using wwwcache.lancs.ac.uk and port 8080, and then added *lancs.ac.uk to the ignored hosts list. Maybe this is where you can change the proxy settings to Direct or Auto, I'm pretty new to this but hope it helps.

Andy
andywilko/ Thanks. Your suggested solution worked for me.  I also have had the same problem.  I used to go to a text console (by pressing ctrl+alt+F1), and used apt-get or aptitude.  Now setting the Network Proxy to "direct connection to Internet" resolved the issue.

---

