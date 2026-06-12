---
title: "Best strategy for serving DNS from ubuntu 13.04 desktop?"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by James_Foote on 2013-10-18
I'm running Ubuntu 13.04 desktop and would like to configure a local dns server so that the other machines on my local nat protected network can use this dns server to resolve local hostnames.  

My current setup uses NetworkManager with a static IP address set.  Now I'd like to set up a local dns server.  I found several writeups for using dnsmasq by first uninstalling NetworkManager, configuring the static ip settings for eth0 in /etc/network/interfaces, then installing dnsmasq (or I suppose bind instead) and configuring it to provide dns services with fallback to my isp's dns servers.  But all the guides I can find were written for 12.04 and it looks like significant changes to NetworkManager and resolvconf have happened in the interim.  

Is it possible to use both NetworkManager and a local dns server at the same time?  NetworkManager actually does solve some tricky problems, so I don't want to abandon it if I don't have to.  Is there a better strategy?  Are there any current writeups for this?  It seems unlikely that I'm the first one on 13.04 desktop that wants to set up something like this for a home network!

Is there a NetworkManager forum somewhere that would be a better place to ask?

Thanks.

---

