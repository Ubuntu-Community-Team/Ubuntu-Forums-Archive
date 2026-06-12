---
title: "Problem with sudo and RubyGems"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by jas1290 on 2010-06-24
Whenever I use **sudo gem install** I get this error:

[B]ERROR:  [http://gems.rubyforge.org/](http://gems.rubyforge.org/) does not appear to be a repository
ERROR:  could not find gem json_pure locally or in a repository[/B]

I've had recommendations to check the proxy configuration for sudo.  I used the command **sudo nano /etc/apt/apt.conf** and this showed up:

[B]Acquire::http:: proxy "http://gatekeeper.mitre.org:80/";
Acquire::ftp:: proxy "ftp://gatekeeper.mitre.org:80/";
Acquire::https:: proxy "https://gatekeeper.mitre.org:80/";[/B]
NOTE: I had to put a space between the : and the p in the above proxies because it made a smiley face (:p).

These are the three proxies that my work uses.  They were already set.  In addition I also set the proxies for my Ubuntu environment (running in VMware player) in **System -> Preferences -> Network Proxy**.

---

### Post by jas1290 on 2010-06-24
bump

---

