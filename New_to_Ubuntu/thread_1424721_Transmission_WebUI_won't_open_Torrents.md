---
title: "Transmission WebUI won't open Torrents"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Cuco3 on 2010-03-08
Hello.  I have a headless Ubuntu 9.04 server running Transmission WebUI properly configured for over a year already. About 3 days ago, I decided to update Ubuntu for the first time in over 2 months. After the update, and I'm not saying that it is the culprit, but around that time the Transmission WebUI will not open torrents that I want to download.  Nothing has been changed, all settings and file permissions are the same since the day I set it up.  Has anybody had the same problem?   I've tried tried uninstall Transmission and then reinstalling it, but nothing changes.  Any help is appreciated.

---

### Post by Cuco3 on 2010-03-08
anyone?

---

### Post by Charles Kerr on 2010-03-08
I don't know the answer yet, but I do have a couple of thoughts --

1. Are you trying to add torrents by telling Transmission their remote URL, or are you downloading the torrents and then telling Transmission their filename?  If it's by URL from a private tracker, it's possible that the Transmission server just doesn't have the right cookies for permission to download the .torrent.

2. Does adding torrents via some other Transmission remote control work?  For example, does "transmission-remote --add filename.torrent" work?

---

### Post by Cuco3 on 2010-03-08
Thanks for your reply Kerr.

1. No, I just download the torrent file to my desktop, open the WebUI, and point it to the file, then press the "Upload" button.

2. Yes, I was able to open a torrent file via transmission-remote to the torrent server and it showed up on the WebUI. It still doesn't work if I try to open it up through the WebUI, though.

---

### Post by Cuco3 on 2010-03-08
Here is a copy of my settings.json for the transmission user (although nothing has been modified since I first set up transmission-daemon)
> 
{
    "blocklist-date": 1256292536,
    "blocklist-enabled": 1,
    "blocklist-updates-enabled": 1,
    "download-dir": "\/media\/disk\/Torrents",
    "download-limit": 800,
    "download-limit-enabled": 1,
    "encryption": 1,
    "inhibit-desktop-hibernation": 0,
    "lazy-bitfield-enabled": 1,
    "main-window-height": 516,
    "main-window-layout-order": "menu,toolbar,filter,list,statusbar",
    "main-window-width": 469,
    "main-window-x": 0,
    "main-window-y": 222,
    "message-level": 2,
    "minimal-view": 0,
    "open-dialog-dir": "\/home\/john\/Desktop",
    "open-file-limit": 32,
    "peer-limit-global": 500,
    "peer-limit-per-torrent": 100,
    "peer-port": 49151,
    "peer-port-random-enabled": 0,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 1024,
    "peer-socket-tos": 0,
    "pex-enabled": 1,
    "port-forwarding-enabled": 1,
    "preallocation": 1,
    "prompt-before-exit": 0,
    "proxy": "",
    "proxy-auth-enabled": 0,
    "proxy-auth-password": "",
    "proxy-auth-username": "",
    "proxy-enabled": 0,
    "proxy-port": 80,
    "proxy-type": 0,
    "recent-download-dir-1": "\/media\/disk\/Torrents",
    "recent-download-dir-2": "\/home\/john",
    "recent-download-dir-3": "\/home\/john\/Desktop\/My Shared Folder\/Torrents",
    "recent-download-dir-4": "\/media\/disk\/My Shared Folder\/Torrents",
    "rpc-authentication-required": 0,
    "rpc-enabled": 1,
    "rpc-password": "",
    "rpc-port": 9091,
    "rpc-username": "transmission",
    "rpc-whitelist": "127.0.0.1,192.168.0.*",
    "rpc-whitelist-enabled": 1,
    "sched-begin": 195,
    "sched-download-limit": 800,
    "sched-end": 945,
    "sched-limit-enabled": 1,
    "sched-upload-limit": 40,
    "show-desktop-notification": 1,
    "show-filterbar": 1,
    "show-notification-area-icon": 1,
    "show-options-window": 1,
    "show-statusbar": 1,
    "show-toolbar": 1,
    "sort-mode": "sort-by-age",
    "sort-reversed": 0,
    "start-added-torrents": 1,
    "statusbar-stats": "total-ratio",
    "trash-original-torrent-files": 0,
    "upload-limit": 40,
    "upload-limit-enabled": 1,
    "upload-slots-per-torrent": 14,
    "watch-dir": "\/home\/john\/Desktop",
    "watch-dir-enabled": 0
}

---

### Post by Cuco3 on 2010-03-08
solved by installing the latest transmission (go here: [https://edge.launchpad.net/~transmissionbt/+archive/ppa]("https://edge.launchpad.net/%7Etransmissionbt/+archive/ppa")    

> 1. add the sources then add the pgp key 
2. run in terminal: sudo apt-get update && sudo apt-get upgrade 
3. you might need to modify the /var/lib/transmission-daemon/info/settings.json file after upgrading.

---

