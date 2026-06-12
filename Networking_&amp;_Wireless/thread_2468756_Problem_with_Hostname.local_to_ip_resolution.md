---
title: "Problem with Hostname.local to ip resolution"
date: 2021-11-09
forum: Networking &amp; Wireless
---

### Post by janderion on 2021-11-09
I have recently set up 2 raspberry pis running Ubuntu Server on both, and when I SSH into either, I can only do so by their IP addresses within my house network. I cannot contact these servers using "username@Hostname.local". Even on the RPi 3 which is running a webserver, I can only access the webserver using the server's IP address. Is there something that I am missing, or perhaps something may be broken?

Tech Info/Context:
RPi 2 Ubuntu Server 20.04 LTS 32bit
RPi 3 Ubuntu Server 20.04 LTS 64bit

---

### Post by TheFu on 2021-11-10
{hostname}.local only works if avahi is running, which isn't part of most server installs.
There are multiple solutions.  The easiest is to create a stanza in the ~/.ssh/config file for each system.

```
host xubu-2110
  user tf
  hostname 172.22.22.88
  port 22

host xubu-2110-ext
  user tf
  hostname thefu.domain.com
  port 63022
```

Then on the other system, use the other IP and change the "host" alias to be something that makes sense.  I show using a LAN and WAN connection ... this can be handy if you want to allow internet access using a non-standard port.  If the userid is the same on the client machine as on the remote system, that doesn't need to be added. But sometimes we need to use a backup userid or deployment userid for servers and I'd rather not need to know it.


The other answer is to setup proper name resolution on each system. That can be with the /etc/hosts file or by running a DNS on the LAN.

Avahi has some uses, but it also causes some problems. Best NOT to use it on servers.  Also, you'll want to configure each server to have static IPs. That shouldn't need to be said, but I'm always amazed at people when they don't do that.

---

### Post by Morbius1 on 2021-11-10
```
sudo apt install avahi-daemon
```
Do that on both servers.

---

### Post by janderion on 2021-11-10
So I have done that, and also followed another step that a tutorial online gave me in regards to Avahi, and it works. Thanks guys.

---

### Post by praseodym on 2021-11-12
Please use Thread tools at the top of the thread and mark it solved

---

