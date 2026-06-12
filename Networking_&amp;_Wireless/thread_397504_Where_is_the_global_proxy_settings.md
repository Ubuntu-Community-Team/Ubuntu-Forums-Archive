---
title: "Where is the global proxy settings"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by jasonal on 2007-03-30
:mad: 
Hi, I can't remember when and where have i setup the global proxy settings. Could anyone tell me where it is and how can i setup from command line? :confused: :confused: 

The gnome preference network proxy is "direct internet connect" and the environment variable "http_proxy" is also null. However, the applications like qterm, gaim, kopete and cvs can still find the correct proxy settings. But where is the "global" proxy setting? I can't find it anywhere.

---

### Post by Mr. C. on 2007-03-30
I am unaware of any such global networking proxy.  What exact problem are you experiencing?  Exact error messages and behaviors please.

MrC

---

### Post by jasonal on 2007-03-30
Actually this system works fine. 
The problem is with another system without X under VMware. The vmware networking configuration is bridged. So I think the networking circumstance is similar and should use the same proxy server. But I don't know where to setup the proxy settings for apps like cvs.

---

### Post by dfmalh on 2008-07-14
Hi I would also like to know where one can set, if anywhere, the one's proxy that it covers all applications.

Here is my problem. Of course I am behind a firewall that uses a proxy...

I can setup my proxy in Firefox, and I have no problems connecting to the internet.

I can also update/upgrade the Ubuntu repositories from the local mirror.

So, up to here there is no problems.

At this point I added the repositories from Medibuntu. I can not update these repositories, or download packages.

Entering my proxy settings in System, Preferences, Network Proxy does nothing, and I still can not connect to the "outside world".

I got as far as figuring out the if I go to System, Administration, Synaptic Package Manager - then open System, Preferences - and select the Network tab... I can enter the following in the Manual Proxy Configuration box: username : [email]password@proxy.server.com[/email][/email] and the Port for the HTTP Proxy... This works, and only this. It does not work if I enter my UN/PW via the Authentication tab... neither if I enter anything in the FTP Proxy box.

Also, although I have access trough the Synaptic Package Manager, I can do no updates/upgrades via a terminal... and I also have packages "downloading" but not "installinf" (e.g. flasplugin-nonfree and msttcorefonts)

One place to control all would be super!

Can anybody help with this problem?

---

