---
title: "vnc/vino - encryption"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by benfindlay on 2006-08-23
Hi there

Ive just installed ubuntu 6.06 on my old computer and am wanting to set up remote connections that are encrypted. I have managed to get the unencrypted version to work (I think its vino as opposed to vnc), but when I connect, the vnc client says the connection is unencrypted. Is there an easy way for me to change this? Ive read stuff about tunneling vnc through ssh, will this work for vino too?

Cheers in advance!

---

### Post by motin on 2006-10-08
Sure it will. Just forward the port that VINO uses over ssh. 

What port?
```
sudo netstat -ap | grep LISTEN | grep -v LISTENING
```

How?
HOWTO: Tunnel VNC through SSH from a windows machine - [http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)

---

