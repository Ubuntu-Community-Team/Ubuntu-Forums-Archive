---
title: "How do I un-blacklist a module?"
date: 2015-06-04
forum: Networking &amp; Wireless
---

### Post by godzillathecing92 on 2015-06-04
So I reinstalled Ubuntu today, and did what I usually do to install my wifi drivers (the default drivers work, just less stable), a part of which includes blacklisting the default drivers.
However, this time something apparently went wrong, and the new drivers didn't load up, so I'd like to un-blacklist the default drivers so I can have an internet connection..

Does anyone know how to do that?

(The guide I use to install my wifi drivers is this: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)
The command in particular I use to blacklist the default drivers is this: 
```

 [COLOR=#111111][FONT=Consolas]sudo -i
[/FONT][/COLOR]echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit

```)

Thanks in advance.

---

### Post by steeldriver on 2015-06-04
You just need to open the file (with root permissions) in an editor and remove (or comment out) the line you appended - e.g.

```

sudo nano /etc/modprobe.d/blacklist.conf

```

---

### Post by godzillathecing92 on 2015-06-04
> **steeldriver said:**
> You just need to open the file (with root permissions) in an editor and remove (or comment out) the line you appended - e.g.

```

sudo nano /etc/modprobe.d/blacklist.conf

```

Thanks.

---

