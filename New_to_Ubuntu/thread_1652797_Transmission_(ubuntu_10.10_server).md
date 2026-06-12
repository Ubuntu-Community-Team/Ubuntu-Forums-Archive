---
title: "Transmission (ubuntu 10.10 server)"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by onthejazz on 2010-12-25
I followed the instructions from the following website to set-up transmission on my ubuntu server.

[http://1000umbrellas.com/2010/10/04/updated-transmission-installationconfiguration-on-ubuntu-server](http://1000umbrellas.com/2010/10/04/updated-transmission-installationconfiguration-on-ubuntu-server)

I have also forwarded the relavant ports on my modem. However when I type in my static ip address 

[http://192.168.1.220:9091](http://192.168.1.220:9091)

into my browser I simply get an error message? Can anyone help me?

---

### Post by onthejazz on 2010-12-25
restarting bittorrent daemon transmission-daemon

JSON parser failed in /var/lib/transmission-daemon/info/settings.json at line 64, column 1: ""watch-dir": "/h"

---

### Post by onthejazz on 2010-12-25
"watch-dir": "/home/gareth/dl/watch",

---

### Post by mikewhatever on 2010-12-26
... and what's the output of **ls -l /home/gareth/dl/watch** ?

---

### Post by onthejazz on 2010-12-26
> **mikewhatever said:**
> ... and what's the output of **ls -l /home/gareth/dl/watch** ?

I don't know what 'output' means?

---

### Post by davidmohammed on 2010-12-26
... I assume he is asking what happens when you type that command in your terminal session i.e. what is displayed on the screen.

---

### Post by onthejazz on 2010-12-26
it says 'total 0'

---

### Post by davidmohammed on 2010-12-26
before he asks I recommend you also report the output of the following command

ls -ld /home/gareth/dl

and

ls -ld /home/gareth/dl/*

---

### Post by onthejazz on 2010-12-26
> **davidmohammed said:**
> before he asks I recommend you also report the output of the following command

ls -ld /home/gareth/dl

and

ls -ld /home/gareth/dl/*

drwxr-xr-x 5 root root 4096 2010-12-25 12:33 /home/gareth/dl

and

drwxr-xr-x 2 root debian-transmission 4096 2010-12-25 12:27 /home/gareth/dl/downloading

drwxrwx--- 2 root debian-transmission 4096 2010-12-25 12:28 /home/gareth/dl/seeding

drwxrw--- 2 root debian-transmission 4096 2010-12-25 12:33 /home/gareth/dl/watch

---

### Post by mikewhatever on 2010-12-26
Well, the directory exists which is ok. Can you also post the output (that word again, sorry) of

tail /var/lib/transmission-daemon/info/settings.json

---

### Post by onthejazz on 2010-12-26
> **mikewhatever said:**
> Well, the directory exists which is ok. Can you also post the output (that word again, sorry) of

tail /var/lib/transmission-daemon/info/settings.json


"upload-slots-per-torrent": 4
"watch-dir": "/home/gareth/dl/watch",
"watch-dir-enabled": true

is there an easy way to copy the text from putty?

---

### Post by onthejazz on 2010-12-26
> **onthejazz said:**
> "upload-slots-per-torrent": 4
"watch-dir": "/home/gareth/dl/watch",
"watch-dir-enabled": true

is there an easy way to copy the text from putty?

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
    "peer-port": 20500,
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
    "rpc-whitelist": "127.0.0.1,192.168.1.210",
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
    "upload-slots-per-torrent": 4
"watch-dir": "/home/gareth/dl/watch",
"watch-dir-enabled": true
}

---

### Post by mikewhatever on 2010-12-26
The only thing that might be missing is the comma (,) at the end of this line: <"upload-slots-per-torrent": 4> . If it's really not there, try adding it.

---

### Post by onthejazz on 2010-12-26
> **mikewhatever said:**
> The only thing that might be missing is the comma (,) at the end of this line: <"upload-slots-per-torrent": 4> . If it's really not there, try adding it.


I've now got the following error message in my browser

**403: Forbidden**

 Unauthorized IP Address.
 Either disable the IP address whitelist or add your address to it.
 If you're editing settings.json, see the 'rpc-whitelist' and  'rpc-whitelist-enabled' entries.
 If you're still using ACLs, use a whitelist instead. See the  transmission-daemon manpage for details.

---

### Post by mikewhatever on 2010-12-26
Are you on the computer with an authorized IP?

---

### Post by onthejazz on 2010-12-26
It is now asking me for a username and password but mine will not work

---

### Post by mikewhatever on 2010-12-26
You are using the ones specified by "rpc-password" and "rpc-username", right?

---

### Post by onthejazz on 2010-12-26
Thanks, I was using the wrong password. 

I notiched that 'blocklist' was an option when configuring transmission. Is there an easy method of generating and installing a blocklist?

---

### Post by mikewhatever on 2010-12-26
Check out the wiki some useful blocklist info.
[https://trac.transmissionbt.com/wiki/Blocklists](https://trac.transmissionbt.com/wiki/Blocklists)

> Using Blocklists in transmission-daemon

transmission-daemon doesn't have an "update blocklist" button, so its users have two options. They can either copy blocklists from transmission-gtk's directory to transmission-daemon's directory, or they can download a blocklist by hand, uncompress it, and place it in the daemon's blocklists folder. In both cases, the daemon's settings.json file will need to be edited to set "blocklist-enabled" to "true". 

---

### Post by onthejazz on 2010-12-27
My files do not appear to be moving from my seeding directory to my watch directory. 


{
    "alt-speed-down": 500,
    "alt-speed-enabled": true,
    "alt-speed-time-begin": 480,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 0,
    "alt-speed-up": 10,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": true,
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
    "peer-port": 20539,
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
    "rpc-authentication-required": false,
"rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-password": "{e7d284dfd7618d27ea53fd328d5ff9e9574837833HUcPF7w",
    "rpc-port": 9091,
    "rpc-username": "transmission",
    "rpc-whitelist": "192.168.1.64",
    "rpc-whitelist-enabled": false,
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
    "watch-dir": "/srv/samba/share",
    "watch-dir-enabled": true









/etc/samba/smb.conf

[downloads]
comments = ubuntu file server share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755

[watchlist]
comments = watchlist
path = ~/dl/watch
browsable = yes
guest ok = yes
read only = no
create mask = 0755

---

### Post by onthejazz on 2010-12-27
I think it may be a permissions problem because when I try and move the file to the smb folder I need to be in root.

---

### Post by mikewhatever on 2010-12-27
> **onthejazz said:**
> My files do not appear to be moving from my seeding directory to my watch directory. 

...


Not quite following you, why do you expect filed to move from ~/dl/seeding to ~/dl/watch? The watch directory is supposed to be for torrent files (.torrent) that you want to start downloading, isn't it?

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> Not quite following you, why do you expect filed to move from ~/dl/seeding to ~/dl/watch? The watch directory is supposed to be for torrent files (.torrent) that you want to start downloading, isn't it?

ah, ok! I thought the watch folder was for completed downloads? Is there a way to automatically move my downloaded files to a smb folder?

---

### Post by mikewhatever on 2010-12-27
No, probably not, at least not with the transmission daemon. The way it is currently setup is that files are downloaded into ~/dl/downloading, and when done, they are moved into ~/dl/seeding. If afterward, you want them moved elsewhere, that's fine, but it is beyond the scope of the howto that you follow.
You could set up a cron job to automate the moving.

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> No, probably not, at least not with the transmission daemon. The way it is currently setup is that files are downloaded into ~/dl/downloading, and when done, they are moved into ~/dl/seeding. If afterward, you want them moved elsewhere, that's fine, but it is beyond the scope of the howto that you follow.
You could set up a cron job to automate the moving.

ok, I will research 'cron jobs'. I am still trying to to set-up the blocklist. In the wiki that you posted it says the blocklists are located in transmissions configuration file. However, I'm having trouble using cd to find the directory. Is it /home/gareth/.configuration/transmission? I've tried a number of different combinations and non of them appear to work.

---

### Post by mikewhatever on 2010-12-27
Blocklists should be in ~/.config/transmission/blocklists by default. Once enabled in the client's preferences, the default list will get downloaded to that location.

For cron jobs, use gnome-shedule on the desktop or the crontab command on the server.

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> Blocklists should be in ~/.config/transmission/blocklists by default. Once enabled in the client's preferences, the default list will get downloaded to that location.

For cron jobs, use gnome-shedule on the desktop or the crontab command on the server.

Is there a way to set-up a cron job to occur immediately. Cron jobs appear to all be time specific. (I will need to use cron tab on my server)

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> Blocklists should be in ~/.config/transmission/blocklists by default. Once enabled in the client's preferences, the default list will get downloaded to that location.

For cron jobs, use gnome-shedule on the desktop or the crontab command on the server.

I don't appear to have the blocklist folder? I've tried both cd ~/.config/transmission/blocklists and

cd /home/gareth/.config/transmission/blocklists

---

### Post by mikewhatever on 2010-12-27
Cron jobs are to automate things. If you want a command to run now, just run it manually.

The blocklist feature is not enabled by default. You'll have to turn it on in Edit->Preferences->Privacy tab. Then the blocklist folder will be created and the blocklist downloaded.

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> Cron jobs are to automate things. If you want a command to run now, just run it manually.

The blocklist feature is not enabled by default. You'll have to turn it on in Edit->Preferences->Privacy tab. Then the blocklist folder will be created and the blocklist downloaded.


I want the command to run everytime a file is downloaded to the directory so an automated command sounds great. Also, I'm running ubuntu server so I don't know how to find the privacy tab

---

### Post by mikewhatever on 2010-12-27
I've no idea how to make commands run every time a file is downloaded. A cron job could sync two folders every X minutes or hours, but that may be not quite the thing you are looking for.

As the blocklists wiki explains, the ~/.config/transmission/blocklits location related to the desktop client, not the daemon. Since you don't have the desktop client, just "download a blocklist by hand, uncompress it, and place it in the daemon's blocklists folder".

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> I've no idea how to make commands run every time a file is downloaded. A cron job could sync two folders every X minutes or hours, but that may be not quite the thing you are looking for.

As the blocklists wiki explains, the ~/.config/transmission/blocklits location related to the desktop client, not the daemon. Since you don't have the desktop client, just "download a blocklist by hand, uncompress it, and place it in the daemon's blocklists folder".

so I mk ~/.config/transmission/blocklist and manually install a blocklist into it? Is that the correct directory for the daemon?

---

### Post by mikewhatever on 2010-12-27
The daemon configuration directory is either /etc/transmission-daemon or /var/lib/transmission-daemon/, not quite sure. Enabling <&#8220;blocklist-enabled&#8221;: false,> and reloading the daemon should create the blocklists directory, then place your blocklists there.

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> The daemon configuration directory is either /etc/transmission-daemon or /var/lib/transmission-daemon/, not quite sure. Enabling <&#8220;blocklist-enabled&#8221;: false,> and reloading the daemon should create the blocklists directory, then place your blocklists there.

I have set 'blocklist-enabled: true,' and reloaded the daemon. However in /etc/transmission-daemon/ there is only settings.json. and in the other directory there is only downloads info.

---

### Post by mikewhatever on 2010-12-27
Ok, so try creating it manually, it's not a big deal.

```
sudo mkdir /etc/transmission-daemon/blocklists
```

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> Ok, so try creating it manually, it's not a big deal.

```
sudo mkdir /etc/transmission-daemon/blocklists
```

Ok, I've made blocklists in both of the directories you suggested and populated them with a .dat blocklist. How do I know if the blocklist has installed?

---

### Post by mikewhatever on 2010-12-27
Good question. I don't know how to check if blocklisting works. From 'man transmission-daemon', it looks like there is no option to log events, but who knows, there might be other ways.

Yep, apparently.
[https://forum.transmissionbt.com/viewtopic.php?f=2&t=10537](https://forum.transmissionbt.com/viewtopic.php?f=2&t=10537)
> transmission-daemon --logfile /your/path/to/transmission.log

---

### Post by onthejazz on 2010-12-27
> **mikewhatever said:**
> Good question. I don't know how to check if blocklisting works. From 'man transmission-daemon', it looks like there is no option to log events, but who knows, there might be other ways.

Yep, apparently.
[https://forum.transmissionbt.com/viewtopic.php?f=2&t=10537](https://forum.transmissionbt.com/viewtopic.php?f=2&t=10537)


I'm having trouble locating the log file, could you help me? I've tried "transmission-daemon -e" but it just gives me the help menu

---

### Post by mikewhatever on 2010-12-27
Well, the log file isn't there until something is logged. You need to launch the daemon with the '--logfile' option, for example:
```
transmission-daemon --logfile ~/dl/downloading
```

---

### Post by onthejazz on 2010-12-28
> **mikewhatever said:**
> Well, the log file isn't there until something is logged. You need to launch the daemon with the '--logfile' option, for example:
```
transmission-daemon --logfile ~/dl/downloading
```

I've tried the above code but I'm told "~/dl/downloading/" is a directory

---

### Post by mikewhatever on 2010-12-28
Oh yeah, sorry, my bad.

```
transmission-daemon --logfile ~/dl/downloading/transmission.log
```

---

### Post by onthejazz on 2010-12-28
> **mikewhatever said:**
> Oh yeah, sorry, my bad.

```
transmission-daemon --logfile ~/dl/downloading/transmission.log
```

[09:11:58.599] Transmission 2.04 (11151) started (session.c:622)
[09:11:58.599] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:767)
[09:11:58.599] RPC Server Serving RPC and Web requests on port 9091 (rpc-server.c:940)
[09:11:58.599] RPC Server Whitelist enabled (rpc-server.c:944)
[09:11:58.599] DHT Reusing old id (tr-dht.c:374)
[09:11:58.599] DHT Bootstrapping from 58 nodes (tr-dht.c:146)
[09:11:58.599] Using settings from "/home/gareth/.config/transmission-daemon" (daemon.c:443)
[09:11:58.599] Saved "/home/gareth/.config/transmission-daemon/settings.json" (bencode.c:1651)
[09:11:58.599] Port Forwarding (NAT-PMP) initnatpmp succeeded (0) (natpmp.c:67)
[09:11:58.599] Port Forwarding (NAT-PMP) sendpublicaddressrequest succeeded (2) (natpmp.c:67)
[09:12:00.600] Port Forwarding (UPnP) Found Internet Gateway Device "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1" (upnp.c:113)
[09:12:00.600] Port Forwarding (UPnP) Local Address is "192.168.1.210" (upnp.c:115)
[09:12:09.601] Port Forwarding (UPnP) Port forwarding through "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1", service "urn:schemas-upnp-org:service:WANIPConnection:1".  (local add$
[09:12:09.601] Port Forwarding (UPnP) Port forwarding successful! (upnp.c:205)
[09:12:09.601] Port Forwarding State changed from "Not forwarded" to "Forwarded" (port-forwarding.c:89)

I can't see a blocklist loading anywhere

---

### Post by mikewhatever on 2010-12-28
Was that all? The log you posted seems like an exchange between transmission and the router. Was a torrent going at that time?
Enabling blocklisting doesn't mean you'll see something blocked every 20 lines in the log.

---

### Post by onthejazz on 2010-12-28
> **mikewhatever said:**
> Was that all? The log you posted seems like an exchange between transmission and the router. Was a torrent going at that time?
Enabling blocklisting doesn't mean you'll see something blocked every 20 lines in the log.


log file from ~/dl/seeding/transmission.log


[14:26:24.691] Transmission 2.04 (11151) started (session.c:622)
[14:26:24.692] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:767)
[14:26:24.692] RPC Server Serving RPC and Web requests on port 9091 (rpc-server.c:940)
[14:26:24.692] RPC Server Whitelist enabled (rpc-server.c:944)
[14:26:24.692] Couldn't bind port 51413 on 0.0.0.0: Address already in use (Is another copy of Transmission already running?) (net.c:381)
[14:26:24.692] Couldn't bind port 51413 on ::: Address already in use (Is another copy of Transmission already running?) (net.c:381)
[14:26:24.692] Using settings from "/home/gareth/.config/transmission-daemon" (daemon.c:443)
[14:26:24.692] Saved "/home/gareth/.config/transmission-daemon/settings.json" (bencode.c:1651)
[14:26:24.692] Port Forwarding (NAT-PMP) initnatpmp succeeded (0) (natpmp.c:67)
[14:26:24.692] Port Forwarding (NAT-PMP) sendpublicaddressrequest succeeded (2) (natpmp.c:67)
[14:26:27.692] Port Forwarding (UPnP) Found Internet Gateway Device "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1" (upnp.c:113)
[14:26:27.692] Port Forwarding (UPnP) Local Address is "192.168.1.210" (upnp.c:115)
[14:26:30.693] Port Forwarding (UPnP) Port forwarding through "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1", service "urn:schemas-upnp-org:service:WANIPConnection:1".  (local add$
[14:26:30.693] Port Forwarding (UPnP) Port forwarding successful! (upnp.c:205)
[14:26:30.693] Port Forwarding State changed from "Not forwarded" to "Forwarded" (port-forwarding.c:89)
[14:47:45.511] Transmission 2.04 (11151) started (session.c:622)
[14:47:45.512] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:767)
[14:47:45.512] RPC Server Serving RPC and Web requests on port 9091 (rpc-server.c:940)
[14:47:45.512] RPC Server Whitelist enabled (rpc-server.c:944)
[14:47:45.512] DHT Reusing old id (tr-dht.c:374)
[14:47:45.512] DHT Bootstrapping from 55 nodes (tr-dht.c:146)
[14:47:45.512] Using settings from "/home/gareth/.config/transmission-daemon" (daemon.c:443)
[14:47:45.512] Saved "/home/gareth/.config/transmission-daemon/settings.json" (bencode.c:1651)
[14:47:45.512] Port Forwarding (NAT-PMP) initnatpmp succeeded (0) (natpmp.c:67)
[14:47:45.512] Port Forwarding (NAT-PMP) sendpublicaddressrequest succeeded (2) (natpmp.c:67)
[14:47:47.512] Port Forwarding (UPnP) Found Internet Gateway Device "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1" (upnp.c:113)
[14:47:47.512] Port Forwarding (UPnP) Local Address is "192.168.1.210" (upnp.c:115)
[14:47:57.514] Port Forwarding (UPnP) Port forwarding through "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1", service "urn:schemas-upnp-org:service:WANIPConnection:1".  (local add$
[14:47:57.514] Port Forwarding (UPnP) Port forwarding successful! (upnp.c:205)
[14:47:57.514] Port Forwarding State changed from "Not forwarded" to "Forwarded" (port-forwarding.c:89)

---

### Post by onthejazz on 2010-12-28
> **mikewhatever said:**
> Was that all? The log you posted seems like an exchange between transmission and the router. Was a torrent going at that time?
Enabling blocklisting doesn't mean you'll see something blocked every 20 lines in the log.


both were recorded after a download had just taken place. 

~/dl/downloading/transmission.log 

[09:11:58.599] Transmission 2.04 (11151) started (session.c:622)
[09:11:58.599] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:767)
[09:11:58.599] RPC Server Serving RPC and Web requests on port 9091 (rpc-server.c:940)
[09:11:58.599] RPC Server Whitelist enabled (rpc-server.c:944)
[09:11:58.599] DHT Reusing old id (tr-dht.c:374)
[09:11:58.599] DHT Bootstrapping from 58 nodes (tr-dht.c:146)
[09:11:58.599] Using settings from "/home/gareth/.config/transmission-daemon" (daemon.c:443)
[09:11:58.599] Saved "/home/gareth/.config/transmission-daemon/settings.json" (bencode.c:1651)
[09:11:58.599] Port Forwarding (NAT-PMP) initnatpmp succeeded (0) (natpmp.c:67)
[09:11:58.599] Port Forwarding (NAT-PMP) sendpublicaddressrequest succeeded (2) (natpmp.c:67)
[09:12:00.600] Port Forwarding (UPnP) Found Internet Gateway Device "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1" (upnp.c:113)
[09:12:00.600] Port Forwarding (UPnP) Local Address is "192.168.1.210" (upnp.c:115)
[09:12:09.601] Port Forwarding (UPnP) Port forwarding through "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1", service "urn:schemas-upnp-org:service:WANIPConnection:1".  (local add$
[09:12:09.601] Port Forwarding (UPnP) Port forwarding successful! (upnp.c:205)
[09:12:09.601] Port Forwarding State changed from "Not forwarded" to "Forwarded" (port-forwarding.c:89)
[09:54:34.754] Reloading settings from "/home/gareth/.config/transmission-daemon" (daemon.c:124)
[09:54:34.754] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:767)
[09:54:34.754] RPC Server Serving RPC and Web requests on port 9091 (rpc-server.c:940)
[09:54:34.754] RPC Server Whitelist enabled (rpc-server.c:944)
[14:15:50.855] Reloading settings from "/home/gareth/.config/transmission-daemon" (daemon.c:124)
[14:15:50.855] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:767)
[14:15:50.855] RPC Server Serving RPC and Web requests on port 9091 (rpc-server.c:940)
[14:15:50.855] RPC Server Whitelist enabled (rpc-server.c:944)
[14:17:10.608] Transmission 2.04 (11151) started (session.c:622)
[14:17:10.608] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:767)
[14:17:10.608] RPC Server Serving RPC and Web requests on port 9091 (rpc-server.c:940)
[14:17:10.608] RPC Server Whitelist enabled (rpc-server.c:944)
[14:17:10.608] DHT Reusing old id (tr-dht.c:374)
[14:17:10.608] DHT Bootstrapping from 112 nodes (tr-dht.c:146)
[14:17:10.608] Using settings from "/home/gareth/.config/transmission-daemon" (daemon.c:443)
[14:17:10.608] Saved "/home/gareth/.config/transmission-daemon/settings.json" (bencode.c:1651)
[14:17:10.608] Port Forwarding (NAT-PMP) initnatpmp succeeded (0) (natpmp.c:67)
[14:17:10.608] Port Forwarding (NAT-PMP) sendpublicaddressrequest succeeded (2) (natpmp.c:67)
[14:17:12.609] Port Forwarding (UPnP) Found Internet Gateway Device "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1" (upnp.c:113)
[14:17:12.609] Port Forwarding (UPnP) Local Address is "192.168.1.210" (upnp.c:115)
[14:17:21.610] Port Forwarding (UPnP) Port forwarding through "http://192.168.1.254:80/upnp/control/igd/wanipc_1_1_1", service "urn:schemas-upnp-org:service:WANIPConnection:1".  (local add$
[14:17:21.610] Port Forwarding (UPnP) Port forwarding successful! (upnp.c:205)
[14:17:21.610] Port Forwarding State changed from "Not forwarded" to "Forwarded" (port-forwarding.c:89)

---

### Post by mikewhatever on 2010-12-29
The way I see it, there are three options:

1. Blocking doesn't work.
2. Blocking works but there was nothing to block.
3. Blocking events aren't logged.

Really don't know which one applies here.

---

