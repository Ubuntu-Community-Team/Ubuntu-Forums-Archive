---
title: "OpenSSH / PUTTY hangs at connection from network client"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by sp4zzj4zz on 2011-04-11
I haven't seen this specific problem before, and its driving me up the wall.

I've just started on a fresh install of Ubuntu Server 10.10 with hopes of running a headless file / media / torrent / usenet / dlna server, but I'm hitting a road block right from the start.

My install went smoothly, along with OpenSSH...

I am able to login via a loopback on the server (ssh localhost) and I was able to login via a web client when I tried that, but using Putty on my Windows 7 and Vista machines, it just hangs once it connects (not login) to the ubuntu machine. The weird part is that out of the 100s of times I've tried from these machines, I actually HAVE connected and logged in a couple of times.

Here is the complete Putty log from a successful attempt:

```
2011-04-11 18:16:40	Looking up host "192.168.1.101"
2011-04-11 18:16:40	Connecting to 192.168.1.101 port 22
2011-04-11 18:16:40	Server version: SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
2011-04-11 18:16:40	We claim version: SSH-2.0-PuTTY_Release_0.60
2011-04-11 18:16:40	Using SSH protocol version 2
2011-04-11 18:16:53	Doing Diffie-Hellman group exchange
2011-04-11 18:17:06	Doing Diffie-Hellman key exchange with hash SHA-256
2011-04-11 18:17:12	Host key fingerprint is:
2011-04-11 18:17:12	ssh-rsa 2048 25:20:93:20:f1:k7:wr:f2:b4:l2:3e:42:cd:4a:cb:4b
2011-04-11 18:17:12	Initialised AES-256 SDCTR client->server encryption
2011-04-11 18:17:12	Initialised HMAC-SHA1 client->server MAC algorithm
2011-04-11 18:17:12	Initialised AES-256 SDCTR server->client encryption
2011-04-11 18:17:12	Initialised HMAC-SHA1 server->client MAC algorithm
2011-04-11 18:17:30	Sent password
2011-04-11 18:17:30	Access granted
2011-04-11 18:17:31	Opened channel for session
2011-04-11 18:17:31	Allocated pty (ospeed 38400bps, ispeed 38400bps)
2011-04-11 18:17:31	Started a shell/command
```

Normally, though, it hangs at "Using SSH protocol version 2" or either of the Diffie-Hellman exchanges. 

My network setup is a Linksys WRT54G as the main router, with an Asus WL-500W running DD-WRT setup as a Repeater Bridge. I have also tried it in a Client Bridge Mode to no avail. I am able to access the router fine, and also the USB flash drive connected as a share on the WL-500W. The Ubuntu server itself has no problems connecting to internet for apt-get installs, updates and upgrades and I am able to ping websites from the server.

I honestly have no idea what the problem is or where it lays. If anyone has any ideas or advice, I'm all ears. TIA.

--------------------------------------------------------------------------
EDIT:

After further testing, pings started to finally stop responding, etc, changed out the NIC, problem solved. Thanks to....pfft.

---

