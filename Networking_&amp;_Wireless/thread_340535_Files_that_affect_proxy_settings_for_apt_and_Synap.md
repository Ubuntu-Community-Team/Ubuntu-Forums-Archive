---
title: "Files that affect proxy settings for apt and Synaptic"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by tuqann on 2007-01-17
Hi,

I operate behind a firewall, and for the past four months since I started using Ubuntu 6.06 I've had to regularly and repeatedly change proxy settings for my internet connection. The problem is that now I have a proxy setting setup somewhere and I can't seem to find where it is to change it.

apt-get and wget work in console, Automatix2 connects, starts up BUT cannot seem to be able to install anything because of proxy settings, SAME for Synaptic Package Manager.

Now this is a list of the files I know effect proxy and I changed, but there is nothing in any of them that has to do with the proxy setting blocking Automatix2 and Synaptic:
/etc/apt/apt.conf
/etc/bash.bashrc
/etc/.wgetrc
/home/username/.bashrc
/root/.bashrc
/root/.profile
/root/.synaptic/synaptic.conf

Those are the files according what what I think. Please point me to ANY other files that relate to proxies, I think I forgot a file or two from a while back and the problem is there, because the proxy settings are my own, but for a different network I had a few weeks ago.

Thanks

---

### Post by augur80 on 2007-03-13
The proxy for Synaptic is setup in the Synaptic Package Manager application via the Settings -> Preferences dialog box on the Network tab.

[ATTACH]27297[/ATTACH]

---

### Post by bapoumba on 2007-03-13
> **tuqann said:**
>  Please point me to ANY other files that relate to proxies, I think I forgot a file or two from a while back and the problem is there, because the proxy settings are my own, but for a different network I had a few weeks ago.

Thanks
/etc/environment could be one of them.

---

