---
title: "Automatic proxy for apt/synaptic"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by blazemore on 2010-03-02
Hi all.
My university uses an automatic proxy script:
wwwcache.nottingham.ac.uk/proxy.pac
Firefox can use this no problem, but there's no option for an automatic proxy in synaptic, so apt doesn't work.
Is there any way to make this work?

---

### Post by blazemore on 2010-03-02
Okay what I've done is look inside that .pac file, and get the address and port of the proxy.
Unfortunately, although it now works with Synaptic, it doesn't work with the apt-get command-line tools.

---

### Post by r-senior on 2010-03-02
Have you tried System -> Preferences -> Network Proxy?

Proxy Configuration tab then select Automatic Proxy Configuration with your URI?

If that works, you should be able to set Firefox back to using system proxy settings.

---

### Post by velle frak on 2010-03-02
Have you tried

export HTTP_PROXY="http://your_proxy_ip_adress:proxy_port"

in a terminal window?

---

