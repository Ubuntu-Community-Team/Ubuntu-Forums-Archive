---
title: "Switching from 9.10 Netbook Remix to 9.10 Desktop"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by lucasg123 on 2009-12-29
Hi, I am trying to switch from 9.10 netbook remix to 9.10 desktop edition. I do not have access to Cd's, DVD's, or a flash drive. Is there any way to do this in the terminal? Any help would be much appreciated.

Thanks!

---

### Post by nothingspecial on 2009-12-29
```
sudo apt-get remove go-home-applet human-netbook-theme maximus ume-launcher window-picker-applet
```

That will remove the netbook remix packages.

---

### Post by lucasg123 on 2009-12-29
I ran that through the terminal without any error messages and the netbook remix interface is still there. Any ideas?

---

### Post by junapp on 2009-12-29
does this help:
[https://answers.edge.launchpad.net/netbook-remix/+question/90183](https://answers.edge.launchpad.net/netbook-remix/+question/90183)
or are you wanting to completely reinstall without cd/flash drive?
In synaptic, is 'ubuntu-desktop' installed? Just curious - not suggesting that will do what you want.

---

### Post by nothingspecial on 2009-12-29
You might have to
```

sudo apt-get install ubuntu-desktop
```

But I can`t remember. Look into it before you do.

---

### Post by LowSky on 2009-12-29
> **lucasg123 said:**
> I ran that through the terminal without any error messages and the netbook remix interface is still there. Any ideas?

reboot

---

