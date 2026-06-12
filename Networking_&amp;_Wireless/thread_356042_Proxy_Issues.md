---
title: "Proxy Issues"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by djboonie on 2007-02-08
Hi all,

Relative n00b here!

I have installed 6.10 on a machine here at work for my own pleasure and experimentation, (attempting to install Rt) however I really am trouble getting the settings right to be able to access the ubuntu repositories.  I can access webpages using firefox, however if  I try anything from the command line I get proxy errors 407.

the recommended syntax is [http://[](http://[)[username][:passwd]@]proxy[:port]/

I even tried using apt and aptitude, same probs.

Is there a central location where the proxy is configured that I cannot find?

HELP

---

### Post by jan247 on 2007-02-10
for the terminal

```

export http_proxy=http://yourproxy:1234/
export ftp_proxy=http://ftpproxy:1234/

```

for Gnome apps (such as the apt gui)

System->Preferences->Network Proxy

---

