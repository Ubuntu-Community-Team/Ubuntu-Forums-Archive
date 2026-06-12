---
title: "Installing python module eye3D for gpodder"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by ba0bab on 2009-01-27
Hello,

I am using gpodder for all my podcasting needs. However, it doesn't tag the mp3 files properly. So I found out that under Podcasts->Additional Components, it can enable MP3 tags. But there is a missing dependency - it needs the python module eye3D. So I tried different things, but I can't find that module! when I do:
```

emil@zeptobuntu:~$ sudo apt-get install python-eye3d
[sudo] password for emil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-eye3d

```

So how do I get this module?

Greetings, Emile

---

### Post by Tim Sharitt on 2009-01-27
Mke sure your package list is up to date
```
sudo apt-get update
```

---

### Post by ba0bab on 2009-01-27
It is up to date. It stills says it can't find it. I get this warning though:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
W: You may want to run apt-get update to correct these problems
```

I don't think it is related, but maybe.

---

### Post by Sock puppet on 2009-04-03
It's python-eyed3. So it would be

```
sudo apt-get install python-eyed3

```

---

