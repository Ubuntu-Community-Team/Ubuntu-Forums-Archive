---
title: "permissions problem in transmission"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by onthejazz on 2010-12-29
so far I have

sudo mkdir ~/dl/seeding

 sudo usermod -a -G debian-transmission gareth

chgrp debian-transmission ~/dl/seeding

chmod 770 ~/dl/seeding

and then the output from /etc/transmission-daemon/settings.json

{
    "alt-speed-down": 500,
    "alt-speed-enabled": true,
    "alt-speed-time-begin": 480,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": true,
    "alt-speed-time-end": 0,
    "alt-speed-up": 10,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "dht-enabled": true,
    "download-dir": "/home/gareth/dl/seeding",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "encryption": 2,
    "incomplete-dir": "/home/gareth/dl/downloading",
    "incomplete-dir-enabled": true,
    "lazy-bitfield-enabled": true,
    "lpd-enabled": false,
    "max-peers-global": 200,
    "message-level": 2,
    "open-file-limit": 32,
    "peer-limit-global": 240,
    "peer-limit-per-torrent": 60,
    "peer-port": 20509,
    "peer-port-random-high": 20599,
    "peer-port-random-low": 20500,
    "peer-port-random-on-start": true,
    "peer-socket-tos": 0,
    "pex-enabled": true,
    "port-forwarding-enabled": false,
    "preallocation": 1,
    "proxy": "",
    "proxy-auth-enabled": false,
    "proxy-auth-password": "",
    "proxy-auth-username": "",
    "proxy-enabled": false,
    "proxy-port": 80,
    "proxy-type": 0,
    "ratio-limit": 0.2500,
    "ratio-limit-enabled": true,
    "rename-partial-files": true,
    "rpc-authentication-required": true,
"rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-password": "password",
    "rpc-port": 9091,
    "rpc-username": "transmission",
    "rpc-whitelist": "192.168.1.64, 192.168.1.65",
    "rpc-whitelist-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "speed-limit-down": 1500,
    "speed-limit-down-enabled": true,
    "speed-limit-up": 50,
    "speed-limit-up-enabled": true,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 2,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 4,
    "watch-dir": "srv/samba/downloads",
    "watch-dir-enabled": true
}


In transmission I then get the following error message "Permission denied (/home/gareth/dl/seeding/linux_distro.iso)

I have got an encrypted hd this may be the problem? Is there anything I can do

---

### Post by Verbeck on 2010-12-29
could you try chmod-ing it to 776 instead of 770

---

### Post by onthejazz on 2010-12-29
> **Verbeck said:**
> could you try chmod-ing it to 776 instead of 770

I'm afraid that did not work.

---

### Post by gordintoronto on 2010-12-29
Perhaps you could tell us what you are trying to do? I've used Transmission, and I never had to enter any commands.

---

### Post by Bucky Ball on 2010-12-29
I've used Transmission too and it has been fine. What release of Ubuntu are you using? I now use Azureus which I find a heap better. It is available in the repositories (Synaptic Package Manager).

---

### Post by onthejazz on 2010-12-30
> **Bucky Ball said:**
> I've used Transmission too and it has been fine. What release of Ubuntu are you using? I now use Azureus which I find a heap better. It is available in the repositories (Synaptic Package Manager).

I'm using the latest stable release.

---

### Post by yetiman64 on 2010-12-30
You didn't need to use sudo to make a directory in your home folder (doing so has likely left the ownership to root for the ~/dl/seeding folder).

Try changing the ownership of this folder with
```
sudo chown <yourusername>:debian-transmission ~/dl/seeding
```replacing <yourusername> with your actual user name.

The permissions, as is, should then work for both yourself and the debian-transmission group.

---

