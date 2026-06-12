---
title: "URL based firewall"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by siva214215 on 2007-06-12
In windows there are software which provide blocking of sites  based on URL content.  Are there any available firewall for linux also.  It should block the request if it matches any regular expression/keyword.

---

### Post by Sendervictorius on 2007-06-12
I'm not quite sure what you are trying to do.

If you want to block web sites (e.g. advertising) when you are browsing the internet, then firefox has a plug-in (tools menu) called Adbloc Plus which will screen out URLs. You can set up your own patterns to match if you like.

Firewalls operate at the Internet Protocol packet level. You can stop individual IP addresses (or specify a domain name (such as ubuntuforums.org) which can resolve to an IP address, but you can't set up firewall rules based on the URL.

---

### Post by siva214215 on 2007-06-12
I want to block the sites based on their urls.
for eg. if it contains/ends with .mp3 it should be blocked.
I know that some of the firewalls in windows provide this feature.
Adbloc is somewhat useful.  But not at full level.  I want to do this system wide.  It could be firewall or any other software. 
However thank you for your help.

---

### Post by Sendervictorius on 2007-06-12
Again, firewalls don't operate at this level.

Sounds like what you may be after is a proxy server. I think you could set one up using squid for example. The proxy-server acts like a gateway to the internet. You can set up rules in the proxy server, set up caching etc. You can then set up your firewall to only allow access to the internet from your proxy.  Not sure if you can do this all on the one machine however, so as to force a browser to use the proxy, but prevent someone changing the configuration to access the internet directly.

Maybe someone else has other ideas?

---

### Post by alanandhispc on 2007-06-12
if you can't set up a proxy, you could alternativly try [www.opendns.com](www.opendns.com)
by pointing your DNS setting to them, you can also enable filtering settings with them.

---

### Post by siva214215 on 2007-06-12
Thank you SenderVictorious & alanandhispc.
Maintaining proxy server on each system may not be desired one.
Is there any lightweight proxy server which can be easily configured.  It does not required to cache files.  Just forwarding is required.  It should be able to monitor urls.  I saw squid.  Seems complex.  Can I do all the above with squid.

---

### Post by t4thfavor on 2007-06-12
IpCop has an addon that does just this, and it can block files based on extension. It is called copwatch., or cop+ im not sure. But I use it. You can set up custom url regular expressions, as well as download 3rd party blacklists to stop people from getting access to all kinds of stuff. The app is configured in a web gui. I had it installed and set up in a few minutes. 

Also there is a method for allowing certain computers full access, and others limited access, while others will be completely blocked. Great for allowing supervisers access to everything while the rest of the company is limited. 

This app also keeps complete logs of who tried what url.

Its a great system if you ask me, and very easy.

EDIT:
I believe it uses squid as its underlying engine. But it is not hard to config.

---

