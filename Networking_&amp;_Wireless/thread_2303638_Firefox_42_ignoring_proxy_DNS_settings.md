---
title: "Firefox 42 ignoring proxy DNS settings"
date: 2015-11-20
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2015-11-20
In Firefox 42 in Ubuntu 14.04, if one is running a SOCKS proxy there is a setting in Preferences -> Network -> Settings -> Remote DNS to route DNS lookups through the SOCKS proxy instead of directly over the local interface.  This setting seems to be ignored, as shown by monitoring with tcpdump.  

```

sudo tcpdump -i wlan0 'port 53'

```

Previously, one could go to about:config and set *network.proxy.socks_remote_dns* to true.  According to tcpdump this does not work either.  

Has something broken in Firefox?  How can it be set to run the DNS queries over the SOCKS proxy?

( Perhaps this belongs in security instead of networking.  )

---

### Post by adagio on 2015-11-21
Odd, but it seems as though addons are making the requests, and also if the first URL loaded is a search using the address bar (but not subsequent browsing by the looks)?

---

### Post by untrustytahr on 2015-11-21
It seems to be working fine for me.  tcpdump isn't capturing when checked and does capture when unchecked.  Are you sure you have proxy setup correctly?

---

### Post by Lars Noodén on 2015-11-21
Yes, I've tried checking the box described above.  And I've tried the setting in about:config.  No dice.  I haven't tried restarting Firefox yet though.  I would not expect that the changes require the application to restart.

---

### Post by untrustytahr on 2015-11-21
I meant wrt server side.  I'm no network guru, so i'll lay out what i did to see if you can reproduce (or if my logic is incorrect).  I fired up a tor browser bundle.  Opened an additional Firefox window (42.0).  Changed the proxy settings on that additional window to point to localhost (127.0.0.1) port 9150.

---

### Post by Lars Noodén on 2015-11-21
> **untrustytahr said:**
> I fired up a tor browser bundle.  Opened an additional Firefox window (42.0).

Is that additional window part of the TBB or a separate instance of Firefox?  I am experiencing the problem with regular Firefox, not the TBB.

---

### Post by untrustytahr on 2015-11-21
> **Lars Noodén said:**
> Is that additional window part of the TBB or a separate instance of Firefox?  I am experiencing the problem with regular Firefox, not the TBB.

It's a separate instance (ff 42.0).  Latest TBB is based on ff 38.4.

---

### Post by adagio on 2015-11-21
I think this is a problem with addons - try starting in '-safe-mode'.

[https://ipleak.net](https://ipleak.net)
[https://www.dnsleaktest.com/](https://www.dnsleaktest.com/)

---

### Post by Lars Noodén on 2015-11-21
Yes, I think that is it.  Starting it with -safemode appended gets rid of the problem but may introduce others. 

Is there a way to narrow down the offending "third-party add-on" that safemode is disabling?

---

### Post by adagio on 2015-11-22
Either TBB has isolated addons to prevent leaks or includes security vetted addons only.

Apart from which I have both dnscrypt installed (reconfiguring the Internet network interface to bypass DHCP DNS using dnscrypt instead - can be done with the gnome network manager), and openvpn running (which _should_ configure its own DNS, wise to check though - google 'dns leak test').  For the adventurous I have in the past configured unbound and ssh to forward TCP DNS requests to google DNS servers.

[Edit] [https://ipleak.net](https://ipleak.net) - DNS leak test and other utils.

---

