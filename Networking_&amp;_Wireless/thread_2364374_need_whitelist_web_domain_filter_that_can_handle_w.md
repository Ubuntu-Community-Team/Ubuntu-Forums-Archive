---
title: "need whitelist web domain filter that can handle wild cards (setup via script)"
date: 2017-06-22
forum: Networking &amp; Wireless
---

### Post by ben5 on 2017-06-22
I have 300 Ubuntu 14 PC's that I block all internet except a whitelist - I do this by disabling dns, and have central server do dns lookups for everything on whitelist and put it in a hosts file and have all the hosts use that.   Obviously this is a bit hacky but it worked. 

Problem now - I have a need to whitelist *.slack.com.   Slack says subdomains change too much, they cant provide a static list, or even a current list and then let me update it.  

So I guess I need to enable DNS - what might be easy ways to still restrict to a whitelist of domains?  I can easily run shell scripts on all 300 machines.  (they check in with central server and grab a script and run it regularly).   So anything I can install/configure via script is an viable option...

If it's not too hard I could set up an ubuntu machine to be a dns server.  

Basically what I want is whatever is easiest so that I can just provide a whiltelist, that is allowed to have wild cards like *.slack.com and block everything else.  I suppose it doesn't actually have to be a DNS based block if there is some client app. 

Whatever it is, I am OK to set up a server myself - but the clients, it needs to be scriptable install/config.  

I want to be able to update the whitelist easily/quickly. 

Any ideas/suggestions?

---

### Post by TheFu on 2017-06-22
Seems like the hard way to solve this issue.

I would
* setup a transparent proxy - squid and changed gateway settings on each client.
* only allow DNS from the proxy - now your 300 system problem is 1 system problem.
* Pull the complete list of subdomains using dig for all the white list you want 1 or 2 times daily.
* shove those domain entries into the /etc/hosts on the proxy only.

Be happy.

Oh - and don't let the workstations have any access (direct, IP, or DNS) to the internet. They must use the proxy server for all access - PERIOD.

Anyway, that's how I'd do it.

---

### Post by ben5 on 2017-06-22
thanks!  sounds good - any tips on how to use dig to get a full whitelist based on the wildcard list?

---

### Post by TheFu on 2017-06-22
> **ben5 said:**
> thanks!  sounds good - any tips on how to use dig to get a full whitelist based on the wildcard list?

That was a rough outline for how I'd look to solve it.

Spent the last 30 min trying to solve the DNS subdomain problem. There isn't any solution - at least nothing that will work to fill in all the subdomains.  Perhaps squid will allow some regex matching?

---

### Post by ben5 on 2017-06-22
wow - thanks for the effort!  Ill see what I can figure out.

---

### Post by TheFu on 2017-06-22
> **ben5 said:**
> wow - thanks for the effort!  Ill see what I can figure out.

All the suggestions I saw required brute-force guessing for the 3rd level.  I tested with some of my domains and none of the supposed solutions actually worked.  There are public DNS records, but no external searches are allowed, so nobody finds those DNS names.  No zone transfers allowed, so walking the DNS tree isn't possible for outsiders either.

Google found this "squid whitelist"
[https://steelmon.wordpress.com/2009/11/22/setting-up-a-strict-whitelist-proxy-server-using-squid/](https://steelmon.wordpress.com/2009/11/22/setting-up-a-strict-whitelist-proxy-server-using-squid/) skimmed it. Haven't tried it. It is a few years old, so some config changes might not work.  OTOH, it does seem to work as you'd like based on the comments.

---

### Post by SeijiSensei on 2017-06-23
> **TheFu said:**
> Oh - and don't let the workstations have any access (direct, IP, or DNS) to the internet. They must use the proxy server for all access - PERIOD.
Unless you intend to block outbound HTTPS access, to do this requires some fancy footwork in Squid.  See [http://wiki.squid-cache.org/Features/SslPeekAndSplice](http://wiki.squid-cache.org/Features/SslPeekAndSplice) for details.

You'll need to create a self-signed certificate on the proxy host and install it on all the clients.

---

### Post by TheFu on 2017-06-23
> **SeijiSensei said:**
> Unless you intend to block outbound HTTPS access, to do this requires some fancy footwork in Squid.  See [http://wiki.squid-cache.org/Features/SslPeekAndSplice](http://wiki.squid-cache.org/Features/SslPeekAndSplice) for details.

You'll need to create a self-signed certificate on the proxy host and install it on all the clients.

[https://turbofuture.com/internet/Intercepting-HTTPS-Traffic-Using-the-Squid-Proxy-in-pfSense](https://turbofuture.com/internet/Intercepting-HTTPS-Traffic-Using-the-Squid-Proxy-in-pfSense) might be easier. It is a dedicated system that becomes the router, gateway, proxy.  I use pfSense, but not for squid due to limited storage on the embedded device.

Just another option to consider, but pfSense is a different OS.

---

