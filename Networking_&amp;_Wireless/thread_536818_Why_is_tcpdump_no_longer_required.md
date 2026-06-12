---
title: "Why is tcpdump no longer required?"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by oldcpu on 2007-08-28
I was uninstalling cron because of the annoying tasks running in the background hourly and daily.  I do not need my files to be indexed every hour or have the package manager updated daily.

So while I was confirming the uninstallation, I get a:
```
The following packages were automatically installed and are no longer required:
  tcpdump
Use 'apt-get autoremove' to remove them.

```
I do not know what that does exactly.  But it appears to be a "powerful" network/security tool.  ([http://packages.ubuntu.com/feisty/net/tcpdump](http://packages.ubuntu.com/feisty/net/tcpdump))

Why does apt-get tell me that it is no longer required?

---

### Post by spd106 on 2007-08-28
Perhaps the ubuntu-standard meta package was removed along the way at some point. This would usually ensure tcpdump is installed as a dependency. As far as I know it's not a critical package and most people will never need to use it directly, but it's sometimes useful to keep around regardless.

---

