---
title: "No Wifi adapter found | Ubuntu 18.04.1 LTS | Intel-corporation-wireless-7260"
date: 2018-08-16
forum: Networking &amp; Wireless
---

### Post by tehseen2 on 2018-08-16
[COLOR=#242729][FONT=Arial]I installed my Ubuntu 18.04 two days ago and it was working fine until I installed VMware in it as I had to install MAC.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It was working fine after the installation of vmware but the problem appears when I restart my laptop. [Here is a link]("http://paste.ubuntu.com/p/X3YJMMYyW3/") to the pastebin output.

I tried many solution from AskUbuntu & ubuntu forums but no one work in my case. I'm listing down some of the solutions which I tried. [1]("https://askubuntu.com/a/760913/858316"), [2]("https://askubuntu.com/a/573083"), [3]("https://ubuntuforums.org/showthread.php?t=2392454&p=13769188#post13769188")[/FONT][/COLOR]

---

### Post by praseodym on 2018-08-18
Are you really using a pppoeconf connection (DSL) or did you add the connection details in your router? Lets try

```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot

---

