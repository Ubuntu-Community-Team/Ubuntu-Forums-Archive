---
title: "about ufw"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by smokystone on 2009-11-18
Hi all, 

I am using ubuntu 9.10 and set up the ufw as my firewall. I just found that I cannot use firefox to watch the video by windows media player totem plugin and cannot open .asx file in browser. I guess this is caused by firewall, but not sure that. 

Does anyone have any idea? byw, I'd like to ask how to check what port or ip address is blocked in iptables.

Thanks. :p

---

### Post by MonoDeem on 2009-11-18
```
sudo ufw status

```

Anyhow, firewall have nothing to do with WMV or any other file formats ( no matter from where and how they are being opened ).

---

### Post by stlsaint on 2009-11-18
> **smokystone said:**
> Hi all, 

I'd like to ask how to check what port or ip address is blocked in iptables.

```
 iptables -L 
```

---

### Post by 3rdalbum on 2009-11-18
The firewall only blocks incoming connection requests. It doesn't attempt to read the contents of files and block them depending on what sort of file it is. It doesn't block outgoing connections either.

So no, the firewall is not the problem. I'd suggest removing the Totem plugin and using the VLC plugin instead.

---

