---
title: "open utorrent x-window using ssh"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Sceiron on 2009-01-11
Hello,

by remoting my ubuntu homePc using openssh i can open any x-window from my windows comp at work.
But i cant find a way to open the utorrent window, since its running under wine.

On the windows comp i'm using X-ming and putty to forward the X-windows.
Anyone know how i can open a "running" utorrent session throug ssh and forward the X-window to my xp-laptop?

---

### Post by nothingspecial on 2009-01-11
No I don`t sorry.

But I use the latest transmission which has a web interface to manage my torrents remotely.

Add these to your /etc/apt/sources.list

```
deb http://ppa.launchpad.net/transmissionbt/ubuntu <ubuntu_release_name> main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu <ubuntu_release_name> main
```

Then ```
sudo apt-get update && sudo apt-get upgrade
```

Start Transmission and you will be able to access it through ipaddress:9091.

---

### Post by rollinginsanity on 2009-01-11
You can also set uTorrent to use a webUI, then just forward the port at your router so you can access it externally. I'm not sure if it has a password though, as it's been ages since I've used it.

---

### Post by Sceiron on 2009-01-21
I prefer to use utorrent, so other clients is not an issue.
Still looking for a way to launch a running utorrent-session in a xwindow from the command line...

---

### Post by Sceiron on 2009-01-22
bump

---

