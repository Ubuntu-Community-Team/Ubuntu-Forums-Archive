---
title: "Network Dead on Ubuntu Server 20.04 LTS"
date: 2021-04-13
forum: Networking &amp; Wireless
---

### Post by bsab5 on 2021-04-13
I've been unable to connect to my server over my network for the past few days. I've been playing with it and can temporarily assign an IP, but can't get it to download or update packages. From what I've pieced together the issue has something to do with a netplan.io update being out of sync with libnetplan0. I saw a post that stated I could fix by manually downloading some packages, but I've never manually downloaded anything. 

I used the following to temporarily assign an IP: 
sudo ifconfig ens160 up
sudo ip addr add xx.xx.xx.xx/24 dev ens160
sudo ip route add default via xx.xx.xx.1 dev eth0

When I attempt an update or upgrade command I get errors stating Temporarily failure resolving 'archive.ubuntu.com'. I'm at a loss on how to fix this. My system tells me I need to update network.io and I'd guess it will fix the issue, but not certain and don't know how to manually update it.

---

### Post by cipherboy_loc on 2021-04-14
Modern Ubuntu server releases use [netplan]("https://netplan.io/examples/") by default. If everything is configured properly, it should set the DNS configuration in [systemd-resolved]("https://wiki.archlinux.org/index.php/Systemd-resolved") and you'll be able to see the DNS servers in `cat /etc/resolv.conf` and `ls -alh /etc/resolv.conf` should point to a file under /run/systemd.

Edit:

Note that due to a [bug]("https://github.com/systemd/systemd/commit/ca8b81d923f34ec4bdaafe472f083059873b9793") in this release of systemd, if you've manually set DNSStubResolver=no in /etc/systemd/resolv.conf, it won't automatically switch to the other file, so you'd need to do so manually.

Otherwise, I'd post contents of:

```

ls -alh /etc/resolv.conf
cat /run/systemd/resolve/resolv.conf
cat /run/systemd/resolve/stub-resolv.conf
resolvectl status

```

If it isn't too long (and put them in code blocks please :-) ).

---

### Post by bsab5 on 2021-04-14
I only have access to a terminal that won't let me copy text or maybe I don't know how. It was too much text to retype everything into code snippets. I took screenshots of the last 3 results. 

```
ls -alh /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Feb 14 2019 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolve.conf
```

cat /run/systemd/resolve/resolv.conf
[ATTACH=CONFIG]288305[/ATTACH]

cat /run/systemd/resolve/stub-resolv.conf
[ATTACH=CONFIG]288309[/ATTACH]

resolvectl status
[ATTACH=CONFIG]288307[/ATTACH]

---

