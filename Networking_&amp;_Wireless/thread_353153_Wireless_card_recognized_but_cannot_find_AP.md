---
title: "Wireless card recognized but cannot find AP"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Fonzy0814 on 2007-02-04
Hey,

I installed Ubuntu AMD 64 yesterday and it works fine.
I saw it had a handy little "Networking" function in the Administration menu
so I thought this time wireless set up would be nice and easy.

I used ArchLinux before where it wasn't that much ... 'fun'.
Now, it recognizes I have a wireless card, and I installed ndiswrapper
and that recognizes the following as well:

```
Installed drivers:
bcmwl5         driver installed, hardware present
```

but when I try scanning for Access Points:

```
fons@ubuntu:~$ iwlist eth2 scanning
eth2        No scan results
```

The AP is working seen as I'm using this laptop with Windows at the moment,
so the problem isn't there.

There's a WEP key on it, and some people (and from what i've read) recommend taking
it off, but I've tried that and doesn't work either. 

I've tried setting my ESSID using:

```
sudo iwconfig eth2 ESSID <myessid> 
```

and all of those options, nothing so far :(

The card is a PCI WMP54G Linksys card.

Any help?
Thanks in advance

---

### Post by chili555 on 2007-02-04
Are you certain the interface of interest is eth2? Please let us see the output of sudo iwconfig.

---

