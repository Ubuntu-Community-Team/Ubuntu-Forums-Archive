---
title: "&quot;Failed to retrieve share list from server: Connection timed out&quot;"
date: 2021-03-29
forum: Networking &amp; Wireless
---

### Post by jvglynnjr on 2021-03-29
I have three computers running Ubuntu 18.04 on a wifi network. I have set up shared file directories using samba on each, but when I try to connect I get the error message in the title. 

The host names show up in nautilus, but clicking on them produces this error message. I can ping each IP address from any computer. 

I tried to attach wireless-info file but the attachment manager is not working.

Here's pastebin URL:   [http://paste.ubuntu.com/p/zJCtm6wMWv/](http://paste.ubuntu.com/p/zJCtm6wMWv/)

---

### Post by CelticWarrior on 2021-03-29
Probably unrelated with the network shares (and more of that later...) but the AP you're using has the worse possible settings, a mixed WPA/WPA2 and TKIP. Change it to WPA2 and AES only.

If there isn't any Windows involved (or is there?) why are you using samba? There are much better solutions if only sharing for Linux clients.

---

### Post by jvglynnjr on 2021-03-29
> **CelticWarrior said:**
> Probably unrelated with the network shares (and more of that later...) but the AP you're using has the worse possible settings, a mixed WPA/WPA2 and TKIP. Change it to WPA2 and AES only.

I can change to WPA2 but I don't see how to change to AES.

> **CelticWarrior said:**
> If there isn't any Windows involved (or is there?) why are you using samba? There are much better solutions if only sharing for Linux clients.

No windoze, but I have not found anything else that works. Please enlighten me. I don't want to have to have a server that is always on. This is just 3-4 computers that I want to be able to share files with each other whenever they happen to be turned on.

---

### Post by CelticWarrior on 2021-03-29
> [COLOR=#000000]I can change to WPA2 but I don't see how to change to AES.[/COLOR]

Change it to anything else but TKIP. It has been deprecated a long time ago. If the router has no other possibility the router shouldn't be used, it's not safe.

[COLOR=#242729][FONT=Arial][Use NFS to share file between systems if there is no windows involved]("https://askubuntu.com/a/8573").
Also: [/FONT][/COLOR]https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-18-04

---

### Post by philhughes on 2021-03-30
Nautilius has done this for as long as I can remember. Very occasionally it works. The easiest thing is to use the Connect to server box and type in:

```
smb://share/sharename
```

replacing share and sharename as appropriate. You can use the IP address instead of share.

---

### Post by Morbius1 on 2021-03-30
A modern Linux samba server will announce itself to the rest of the network 2 different ways:

[1] By NetBIOS name - aka the "Windows Way".

Has to follow a bunch of rules and even then it may be problematic.

[2] By it's mDNS name.

Regrettably, a given Linux client machine will see both as "Hostname (File Sharing)" so you don't know which one you're using. You could I suppose to through "Windows Network" then you are assured you are using the "Windows Way" but it's best to stick with mDNS in an all Linux / MacOS network.

So the question is can you ping the server not by it's ip address or it's hostname but by it's mDNS hostname ( servers host name with a .local attached at the end ):
```
ping -c3 hostname.local
```

If you cannot disable the firewall on the server and try it again.

Also make sure that both the server and the client have avahi running - this controls mDNS:
```
 sudo service avahi-daemon restart
```

---

### Post by jvglynnjr on 2021-03-30
> **CelticWarrior said:**
> Change it to anything else but TKIP. It has been deprecated a long time ago. If the router has no other possibility the router shouldn't be used, it's not safe.

[COLOR=#242729][FONT=Arial][Use NFS to share file between systems if there is no windows involved]("https://askubuntu.com/a/8573").
Also: [/FONT][/COLOR]https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-18-04

Thanks for the link. I tried NFS a few years ago, but I couldn't get it to work. I'll take another look. 

My router is a Zyxel from my DSL provider. I don't see anywhere on the user interface that mentions TKIP, so I can't change it to AES or anything else.

---

