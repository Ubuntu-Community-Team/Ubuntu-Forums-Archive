---
title: "How to kill NetworkManager and/or disable it [K]Ubuntu 14.04"
date: 2018-11-20
forum: Networking &amp; Wireless
---

### Post by firehammer047 on 2018-11-20
Basically I wanted to disable NetworkManager for a particular wifi device. I was OK with disabling it temporarily as well and then re-enabling it. Searching for "kill NetworkManager" and "disable NetworkManager ubuntu 14.04" gave lots of results but not exactly what I wanted.

I am running Kubuntu 14.04.5. It's also called "Trusty" in case you forget the names like I do.

MY Kubuntu uses upstart. It does not use systemctl as pointed out in some other posts. Nor do I have /etc/init.d/network-manager as suggested in other posts. The process I see with "ps fax" is "NetworkManager" and if you try to kill it, it respawns.

SOLUTION #1:
As pointed out here [https://edulab.unitn.it/tecnici/how-to-disableremove-network-manager-in-ubuntu-or-debian/](https://edulab.unitn.it/tecnici/how-to-disableremove-network-manager-in-ubuntu-or-debian/) , here [https://tweenpath.net/disable-network-manager-linux/](https://tweenpath.net/disable-network-manager-linux/) and here [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager) the correct way to stop NetworkManager (and it's parent service network-manager) is with:

```
sudo service network-manager stop
```
or
```
sudo stop network-manager
```

That will stop NetworkManager temporarily and allow you to configure your devices manually.

*Note it's also here [https://askubuntu.com/questions/266767/how-to-stop-networkmanager](https://askubuntu.com/questions/266767/how-to-stop-networkmanager) but NOT specific to 14.04.

SOLUTION #2:

What I REALLY want to do is disable it for a specific device but I don't like the old-style editing /etc/network/interfaces (it reminds me of the 90s).[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR]After reading this [http://manpages.ubuntu.com/manpages/bionic/man5/NetworkManager.conf.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/NetworkManager.conf.5.html) and this [https://support.qacafe.com/knowledge-base/how-do-i-prevent-network-manager-from-controlling-an-interface/](https://support.qacafe.com/knowledge-base/how-do-i-prevent-network-manager-from-controlling-an-interface/) it's easy with NetworkManager.conf.

Edit /etc/NetworkManager/NetworkManager.conf and add:

```
[keyfile]
unmanaged-devices=mac:xx:xx:xx:xx:xx:xx

```

as pointed out here also [https://stackoverflow.com/questions/5321380/disable-network-manager-for-a-particular-interface](https://stackoverflow.com/questions/5321380/disable-network-manager-for-a-particular-interface) but again NOT specific to 14.04. And this post [https://ubuntuforums.org/showthread.php?t=2298853](https://ubuntuforums.org/showthread.php?t=2298853) was not useful.


Hope this helps others trying to stop NetworkManager from taking over ALL your devices.

---

### Post by TheFu on 2018-11-20
At this point, it is time to be moving off 14.04. Support ends in about 6 months.

If you don't want an interface to be managed by network-manager, but don't just want to purge that tool from your system (which is what I do), then you can put a stanza into the /etc/network/interfaces file with the specific interface and NM will ignore it.

There's something beautiful about device management with config files.  Simple, effective. Why having something more complex to have bugs?

---

### Post by firehammer047 on 2018-11-27
> **TheFu said:**
> At this point, it is time to be moving off 14.04.


Dear TheFu,
I strongly, yet respectfully disagree. There are many scientists and other enthusiasts that develop code/systems for a particular purpose and have absolutely NO need to upgrade, and NO desire to maintain the code/systems they've spent countless hours developing.

In short I will refer you to the old saying, "if it ain't broke, don't fix it."

I still use WinXP for research and even the IT department at my workplace was unable to stop me from using it after the argument I just wrote.

I also still use Ubuntu 12.04 on a few other machines and I think it's still my favorite.

Regards.

---

### Post by TheFu on 2018-11-28
Running unsupported OSes is fine, provided those machines aren't connected to a network with risks like the internet or internal LANs with systems. If you have air-gapped networks, go ahead and run unsupported OSes.

But most people aren't willing to do this.

There are often other considerations too.  For example, corporate liability insurance requires running fully patched, currently supported software as part of their cyber protection policies.  A single unmanaged system can void that policy and don't expect the premium payments to be returned.

There are other business reasons TO and NOT TO run unsupported OSes, but usually the risk acceptance decision needs to be made by someone with the legal authority.  That legal authority is unlikely to be the admin or dev working on the system daily, unless you are a 1-man shop or working on your own equipment at home.

Just some other things to consider.

---

