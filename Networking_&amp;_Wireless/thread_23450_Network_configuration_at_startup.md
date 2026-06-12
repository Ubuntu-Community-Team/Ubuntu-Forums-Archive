---
title: "Network configuration at startup"
date: 2005-04-02
forum: Networking &amp; Wireless
---

### Post by Shaggy on 2005-04-02
Is there anyway to turn it off safely before boot, and turn on what I want in Gnome.

I notice that during boot time my laptop hangs for a while during the setting up network interfaces.  This might be because it tries to set up first the normal nic, and waits for it to time out, and then tries for the wireless card.  But even if it does that it slows down a lot what would be a normally fast boot time.

I've tried to just remove the references to the cards in /etc/network/interfaces, and that sped up my boot time perfectly.  But then when setting up the wireless card in the gnome config utility it gave me an error.

---

### Post by fdoving on 2005-04-02
Instead of removing the references from /etc/network/interfaces you can use update-rc.d to disable the service at boot.

Disable:
```

sudo update-rc.d -f networking remove

```
 
Enable:
```

sudo update-rc.d networking defaults 35

```

(The 35 is a priority number.. lower numbers starts first.. 20 is default. We'd like networking to be started after most of the other stuff like firewalls and everything. 99 is the lowest priority.. started last. As for the symlinks.. S is start, K is kill..)

Enjoy.

---

### Post by somuchfortheafter on 2005-04-02
or you can press ctrl then c during bootup when it gets to there.... just a quick fix if you are not online then.

---

### Post by Psquared on 2005-04-02
I had the same problem. It seemed like it hung for a minute or so at Network configuration. I just went into my network settings and disabled the NIC and now it only hangs for a second or two.

---

### Post by Shaggy on 2005-04-03
[QUOTE=fdoving]Instead of removing the references from /etc/network/interfaces you can use update-rc.d to disable the service at boot.

Disable:
```

sudo update-rc.d -f networking remove

```
 
Enable:
```

sudo update-rc.d networking defaults 35

```

(The 35 is a priority number.. lower numbers starts first.. 20 is default. We'd like networking to be started after most of the other stuff like firewalls and everything. 99 is the lowest priority.. started last. As for the symlinks.. S is start, K is kill..)

Enjoy.[/QUOTE]

Perfect worked just like I wanted it too, thanks.

---

### Post by Manuel Siggen on 2005-04-07
[QUOTE=fdoving]Instead of removing the references from /etc/network/interfaces you can use update-rc.d to disable the service at boot.

Disable:
```

sudo update-rc.d -f networking remove

```
 
Enable:
```

sudo update-rc.d networking defaults 35

```

(The 35 is a priority number.. lower numbers starts first.. 20 is default. We'd like networking to be started after most of the other stuff like firewalls and everything. 99 is the lowest priority.. started last. As for the symlinks.. S is start, K is kill..)

Enjoy.[/QUOTE]

What does this solution change precisely ? Is that networking initialization is discarded at boot time, and is only applied at Gnome startup ?

Thanks in advance.

---

### Post by sMell on 2005-04-07
[QUOTE=Shaggy]I've tried to just remove the references to the cards in /etc/network/interfaces, and that sped up my boot time perfectly.  But then when setting up the wireless card in the gnome config utility it gave me an error.[/QUOTE]

You can set up interfaces so that the card won't be automatically brought up at boot.
Remove it from "auto" or comment the line out if it's hte only interface

---

### Post by jcookeman on 2005-04-08
Isn't their a way to background dhclient so it doesn't wait for an IP address?  Suse does this and it's a wonderful thing IMO.  

Maybe I will search this later if I have time.

&#1076;&#1086; &#1089;&#1074;&#1080;&#1076;&#1072;&#1085;&#1080;&#1103;

---

