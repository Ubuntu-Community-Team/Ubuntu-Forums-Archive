---
title: "Failed to add/activate connection. (32) Insufficient privileges."
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by Nickolai_Leschov on 2015-09-02
I am doing a fresh install of a minimal Ubuntu system with MATE desktop environment. When I click on NetworkManager's icon and then a wireless network to connect to, I receive a dialog box that says:

> Connection failure

Failed to add/activate connection

(32) Insufficient privileges.


I am doing a clean reinstallation of Ubuntu 14.04 with Lubuntu 14.04.1 alternate installer and choose `F4` -> "Install a basic command-line system", then install X, MATE and NetworkManager manually like this:

> ```

sudo apt-get install software-properties-common -y
sudo apt-add-repository ppa:ubuntu-mate-dev/ppa -y
sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate -y
sudo apt-get install xorg mate-core --no-install-recommends -y
sudo apt-get install network-manager network-manager-gnome --no-install-recommends -y

```

If that helps, when I install Ubuntu that way, it asks for password upon attaching and unmounting a USB flash drive. Also, when I am creating a shortcut for `shutdown` command, to be able to shut down my computer with a click on an icon, I have to alter permissions for `/sbin/shutdown`:

> ```

chmod u+s /sbin/shutdown

```

Maybe something similar is going on with Wi-Fi and I need to alter some permissions for it to work properly?

---

### Post by v3.xx on 2015-09-02
I do have mate-core loaded up.  I just wanted to see if it worked and have not used it at all.

Did it on a terminal install with only the one line.
 ```
sudo apt-get install xinit mate-core --no-install-recommends
```
I didn't spend time researching it, but it may not be necessary to do xinit or xorg.  Like I said, just wanted to see it work.

Anyhow, I did have internet conductivity out of the box.  So I'm wondering why the extra package/ppa on yours.

Also the mini-install has been discussed in the developmental forum @
[https://ubuntu-mate.community/](https://ubuntu-mate.community/)

May also want to give them a visit.

---

### Post by Nickolai_Leschov on 2015-09-02
> Anyhow, I did have internet conductivity out of the box.
Wired? Wired works; wireless doesn't. (it shows available networks, but apparently I have 'insufficient privileges' to join them)
I'm adding the extra ppa's because MATE wasn't part of Ubuntu, at least as of 14.04, so one *needed* to add them to install MATE. I'll double-check what the situation is now.

---

### Post by v3.xx on 2015-09-02
> insufficient privileges
When that pops up on mine, it usually means I'm trying to access some other wireless in the area.

On a side note, my main install is ubuntu mate and it was necessary to add a wireless driver to mine.

---

### Post by steeldriver on 2015-09-02
It may be an issue of Mate not providing a suitable policykit (polkit-1) configuration for the nm-applet?

---

