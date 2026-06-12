---
title: "Can't find all proxy settings"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by labrat256 on 2009-11-12
I am currently behind a university's proxy server, and I'm having a few related problems. As I use my laptop both inside and outside the university, I have to frequently change the proxy settings. 

I've just updated to 9.10 from 9.4 and I'm trying to run "apt-get install xbindkey" in the terminal. Its not working at all, and is returning many 409 errors, for example "  409  Conflict [IP: 194.117.143.72 80]
Err [http://ubuntu.virginmedia.com](http://ubuntu.virginmedia.com) karmic/multiverse Sources". I had a similar problem before, and it was due to me not setting all of the proxy settings (I'd set it in firefox, and system/administration/network proxy, but not in the synaptic package manager). This time, I've set the proxy settings in every location and application I can find and it still isn't working!

Does anybody know of anywhere else I should input the proxy settings, or could there be any other reason this is happening? Also, is it possible to easily set up 2 separate proxy settings depending on what network I'm on?

Thanks

Labrat256

---

### Post by labrat256 on 2009-11-13
Bump to see if anybody knows?

---

### Post by joekeno on 2009-11-14
> **labrat256 said:**
> Bump to see if anybody knows?
I'm totally stuck on this one too. Had the laptop set up somewhere else and now I cant figure out where to reset all the proxy settings as well. 
Stuck in the same place. Reset web browser, reset synaptic settings, and system preferences network proxy... someone pls help us

---

### Post by LinGNUbie on 2009-11-17
users/roots .profile, .bashrc perhaps?

---

### Post by joachimrs on 2010-01-03
I checked roots .bashrc and .profile.

In roots .synaptic there is an entry of the old proxy, but it reads UseProxy "0"

  useProxy "0";
  httpProxy "proxyuhh.uni-hamburg.de";
  httpProxyPort "3128";
  ftpProxy "proxyuhh.uni-hamburg.de";
  ftpProxyPort "3128";
  noProxy "";

I don't know where the proxy comes from. Set Network Proxy Preferences to "Direct connection" and Apply System-wide

no idea what else I can do :(

---

