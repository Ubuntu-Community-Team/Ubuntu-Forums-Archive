---
title: "no external Internet access behind MS proxy"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by rs98 on 2007-04-25
Just installed Feisty Fawn using Alternate Install CD.  During install, I entered username/password/proxyname for my work's MS proxy so that apt-get could do its thing - which was nice.  Now that the OS is fully installed, the Update Manager and Synaptic Package Manager are working as expected behind the proxy server.  I have also specified the proxy server info (with user and pass) in the NETWORK PROXY preference utility.

My problem is that I can't get Firefox to access any external web sites (Server Not Found error), even if I specify the proxy info in Firefox's preferences.  This is what I have done previously and it has always worked.

I noticed that there is an ACQUIRE::HTTP::PROXY statement in my apt.conf, which I assume was placed their during the install procedure.  Is this somehow affecting Firefox?  Note that I can access web sites that are internal at work.  It is only external sites that I cannot access.

Any ideas?

---

### Post by rs98 on 2007-04-25
correction - Synaptic Package Manager is not working - I get proxy authentication errors when it tries to download a package.

I have since been able to get Firefox to access external web sites using NTLMAPS, however, it does not seem to be helping with the package manager's access to external sites.

---

### Post by rs98 on 2007-04-25
looks like I have been able to fix the issue using NTLMAPS and setting every app that has a proxy server option to 127.0.0.1 and the associated port.  looks like I'll just need to invoke NTLMAPS everytime and I will be able to properly access external web sites through my work's MS proxy.

---

