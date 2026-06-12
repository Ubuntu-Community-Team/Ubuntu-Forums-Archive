---
title: "Synaptic Package Manager - very slow"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by mrfotheringham on 2009-06-24
I am having problems downloading packages. My download speed is between 8 and 11 meg. But when I try to download Flight of the Amazon Queen the transfer speed drops massively and says it will take a day to download. Only been using broadband for two weeks so a bit clueless as to the problem. Any advice

---

### Post by fooman on 2009-06-24
have you tried a different server?

open synaptic and in the toolbar click settings > repositories

under the ubuntu software tab,  click the little arrow at the right end of the "download from" space and try a different one....if you choose "other",  then "select best server",  it should find the fastest one for you.

hope that helps.

---

### Post by mrfotheringham on 2009-06-24
> **fooman said:**
> have you tried a different server?

open synaptic and in the toolbar click settings > repositories

under the ubuntu software tab,  click the little arrow at the right end of the "download from" space and try a different one....if you choose "other",  then "select best server",  it should find the fastest one for you.

hope that helps.
You are a star fooman. Now using mirror in s.africa and running at 10meg which is amazing. Many thanks!!!

---

### Post by kako13 on 2009-12-07
yep that solved my problem on Ubuntu 9.10

---

### Post by bsman2.0 on 2009-12-13
I am having very slow downloads through synaptic.  When I attempt to pick the best server it says that there is no best server for me.  I was getting 1-2 K download speeds, I picked a random different server and now I am getting up to 9K, still very very slow, but 9 times better than I was.  Any ideas?  The select best server tool tells me that I should check my internet connection, but I can get a speed test (speakeasy.net/speedtest) of more than 2000K while downloading from synaptic.  So I think that my internet connection is working.  

I am using Ubuntu 9.10 on an HP Nx9600 laptop dual booting with XP.  XP downloads are fine, and donwloads through firefox in Ubuntu are plenty fast.  I have tried hard wired to my router and over wireless and I have the same results.

Any thoughts on what to do about this?

---

### Post by mikewhatever on 2009-12-13
> **bsman2.0 said:**
> I am having very slow downloads through synaptic.  When I attempt to pick the best server it says that there is no best server for me.  I was getting 1-2 K download speeds, I picked a random different server and now I am getting up to 9K, still very very slow, but 9 times better than I was.  Any ideas?  The select best server tool tells me that I should check my internet connection, but I can get a speed test (speakeasy.net/speedtest) of more than 2000K while downloading from synaptic.  So I think that my internet connection is working.  

I am using Ubuntu 9.10 on an HP Nx9600 laptop dual booting with XP.  XP downloads are fine, and donwloads through firefox in Ubuntu are plenty fast.  I have tried hard wired to my router and over wireless and I have the same results.

Any thoughts on what to do about this?

2000Kbts (I assume) isn't too shabby. The best general practice it to select a geographically closest server.

---

### Post by bsman2.0 on 2009-12-13
I think I solved my own problem.  I started randomly downloading packages from mirrors on packages.ubuntu.com and found a server that worked quickly.  I am now getting 200k from synaptic.  It seems odd that the best server tool did not find a good server for me.  But I am happy with what I have now.

Thanks for your help!

---

### Post by mikewhatever on 2009-12-13
The best server tool? What's that?

---

### Post by bsman2.0 on 2009-12-13
in synaptic package manager, click on settings, then repositories.  then where you pick your download server, click on other... a new window opens and you can click on the select best server button.  It is supposed to ping all of the possible servers and report back with the best one.  Mine unfortunately told me that there were no best servers.  Turns out there is at least one okay server.

---

