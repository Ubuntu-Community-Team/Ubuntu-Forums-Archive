---
title: "Add/Remove not working"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Sheneron on 2008-12-19
Hey, new to ubuntu so I don't really know whats going on.  I just installed ubuntu ultimate 1.4.  I wasn't really sure what it was but alot of people downloaded it and the normal ubuntu install didn't really work.

So anyway this ubuntu is working well except that the Add/Remove isn't properly working.  I get this error message:

W: Failed to fetch archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ktron_3.5.6-0ubuntu2_i386.deb
  404 Not Found [IP: 91.189.88.31 80]

Now I know my internet connection is working.  If anyone can help me I would appreciate it.  Thank you.

---

### Post by Sheneron on 2008-12-19
Oh and this may be helpful.

There is also this error message:

mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found

I think it may be because in the dists folder it is feisty instead of the new one.

---

### Post by donkyhotay on 2008-12-19
Sounds like a network connection problem. If the rest of the internet works for you it might be something with that specific server. Try selecting a different one and see what happens. If that doesn't work it may be a temporary network problem at which point I'd just wait an hour or so.

---

### Post by Michael.Godawski on 2008-12-19
> **Sheneron said:**
> Hey, new to ubuntu so I don't really know whats going on.  I just installed ubuntu ultimate 1.4.  I wasn't really sure what it was but alot of people downloaded it and the normal ubuntu install didn't really work.

So anyway this ubuntu is working well except that the Add/Remove isn't properly working.  I get this error message:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ktron_3.5.6-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdegames/ktron_3.5.6-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

Now I know my internet connection is working.  If anyone can help me I would appreciate it.  Thank you.

well the requested file is really not on the archives
> The requested URL /ubuntu/pool/main/k/kdegames/ktron_3.5.6-0ubuntu2_i386.deb was not found on this server.You can try to change the download server. But I do not know if the ultimate version is supported by canonical.
I would always try to use the latest version of Ubuntu or a long term support LTS version so 8.10 or 8.04 LTS.

Have you tried to install the one and only original Ubuntu with the Alternate CD?

What difficulties did you have with the Ubuntu installation? Which version did you try to install?

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

---

### Post by Sheneron on 2008-12-19
Yes I think I will just try to reinstall the real ubuntu again.  What is the difference between  the LTS version and the other one?

---

### Post by donkyhotay on 2008-12-19
LTS stands for Long Term Support, it's a version that usually older but recieves updates for longer. The other version is going to be the newest but will need to be upgraded more recently. Generally if this is going to be a regular desktop I recommend using the latest version and updating/upgrading frequently, but thats just my opinion.

---

### Post by roshanjose on 2008-12-19
before you plunge yourself into installing a new distro, check your network settings and check whether you have entered the DNS setting.

And let me know the result

---

### Post by Sheneron on 2008-12-19
Not really sure what exactly your looking for... but under network settings I see a DNS server that says 10.0.0.2

---

