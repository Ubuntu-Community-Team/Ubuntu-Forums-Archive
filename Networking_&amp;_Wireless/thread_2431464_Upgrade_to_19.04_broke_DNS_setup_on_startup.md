---
title: "Upgrade to 19.04 broke DNS setup on startup"
date: 2019-11-16
forum: Networking &amp; Wireless
---

### Post by Harry66 on 2019-11-16
Hi,

I've seen similar problems, but not been able to fix the problem permanently yet.

My PC is connected by ethernet to my router, which also serves as DNS.

Since I upgraded to 19.04, more often than not DNS has been broken on startup, but external sites can be pinged by ip adresss.
The problem has persisted after I upgraded to 19.10.

**/etc/resolv.conf** is empty

My temporary fix is to restart **NetworkManager**, which seems to regenerate **/etc/resolv.conf ** with

```

nameserver 127.0.0.53
search lan

```

And DNS works from there on, but only until shutdown.

I've tried re-linking **/etc/resolv.conf** using absolute path ( as suggested in [https://www.linode.com/community/questions/17081/dns-stops-resolving-on-ubuntu-1804]("https://www.linode.com/community/questions/17081/dns-stops-resolving-on-ubuntu-1804") ) to no avail:

```

$ sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
$ systemctl restart resolvconf

```

I've tried advice in [https://ubuntuforums.org/showthread.php?t=2403929]("https://ubuntuforums.org/showthread.php?t=2403929") but I'm using DHCP, so wasn't sure how much applied. I didn't have anything in **/etc/netplan**, 
but tried creating the **/etc/netplan/01-network-manager-all.yaml** file as described in that thread, also to no avail.

**/etc/netplan/01-network-manager-all.yaml**
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```

```

$ sudo netplan generate
$ sudo netplan apply

```

Any help would be greatly appreciated.

Harry.

---

### Post by chili555 on 2019-11-16
Instead, please try:

```
sudo rm /etc/resolv.conf
sudo ln -s  /run/systemd/resolve/stub-resolv.conf  /etc/resolv.conf

```

---

### Post by Harry66 on 2019-11-17
That seems to have done it, thank you! (Of course the one thing I hadn't tried, as I'd seen somewhere someone saying it was wrong ...)

My laptop is still on 18.04 and still has /etc/resolv.conf linked to **../run/resolvconf/resolv.conf** I suppose it changed in 19.04?
It's possible I did something in the past that interfered with the upgrade's ability to migrate the link... 

I'm going to watch it for a few reboots, and then mark it solved if it stays fixed. Many thanks again!

---

### Post by Harry66 on 2019-11-17
I might have spoken too soon...

It seems to have helped it connect at startup, but it also seems to have killed network performance.
I look now, and **/etc/resolv.conf** has an extra line that it didn't have before:
```

nameserver 127.0.0.53
**options edns0**
search lan

```

Tried commenting it out, but no luck, as it says, it gets overwritten. Not sure where the source of that setting is yet.

In the meantime, I've linked **/etc/resolv.conf** back to **/run/resolv/resolv.conf** until I can sort out the network performance

---

### Post by Harry66 on 2019-11-17
So, having googled **edns0**, I found:
[https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1817903/comments/6]("https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1817903/comments/6")

> Ok I have found what the problem is, I think; I suspect that you have resolvconf installed on your system, which is taking over the /etc/resolv.conf file, and I think that resolvconf is pulling the edns0 option, but also including external nameserver(s), which is an incorrect configuration, since the edns0 option should only be used when talking to the local stub resolver, because we don't know if external dns server(s) support edns.

The resolvconf package is not installed by default for Bionic (though I am not sure if Mint installs it by default for some reason). Is this system upgraded from a previous release, or did you install resolvconf manually? Unless you specifically need it, can you try unistalling resolvconf and rebooting to see if that fixes the problem for you?

$ sudo apt remove resolvconf
$ sudo reboot

And also please do paste the contents of /etc/resolv.conf here, especially if removing resolvconf doesn't help.


Which rang vague bells. Before I got a pfsense router, which could handle dns caching for me, I tried to get my system to cache dns (this was probably before systemd was as extensive as it is now, and when we still had sub Megabit broadband...) without really knowing what I was doing...

So I've removed **resolvconf**, and I've linked **/etc/resolv.conf** back to **/run/systemd/resolve/stub-resolv.conf** as you've suggested

DNS resolving is back on start up, and network performance is back (Still have **options edns0** but my router looks like it can support edns, and as it works, I'm happy)

Looks good now. Many thanks again. Closing off.

---

