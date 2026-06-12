---
title: "repo access through vpn"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by iago4096 on 2008-08-23
Hi there!

I am running Hardy (technically Ubuntu-eee) on my eeepc (more or less everything runs fine) and I connect to my university server through a vpn. My uni won't let you access otherwise. The way it has been set up I have to adapt my browser to go through a specific http-proxy and a specific port, which also works fine.

My problem is that I cannot access repos through this connection, the update manager will tell me things like > The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

sudo apt-get update returns things like
> Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                        
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB                                          
  Unable to connect to archive.canonical.com http:
etc.


I did an update in my workplace network yesterday, which went perfectly fine, I just can't access repos through the university network. Am I right to believe that this is because of the vpn? Is there something obvious I am missing?

**[COLOR="Red"]I[/COLOR]ago4096**

---

