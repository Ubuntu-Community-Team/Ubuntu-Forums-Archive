---
title: "How to permanently keep &quot;Enable Wireless&quot; unchecked ?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by viridity on 2008-12-24
I searched this forum. Someone asked this question but the answer he got was simply "uncheck the checkbox". Yeah right...

OK I unchecked the checkbox but next time I login it's checked again. So my question is, how to make this a "setting", i.e. keeping it unchecked permanently?

The reason is, I don't want to get into other people's wireless network. I have my own wired connection.

Thanks very much.

---

### Post by Titan8990 on 2008-12-24
Post the results of this command:

cat /etc/network/interfaces

---

### Post by hyper_ch on 2008-12-24
maybe try an alternate network manager. I use now WICD

---

### Post by Xiong Chiamiov on 2008-12-24
You don't actually need network manager running at all if you're not going to use your wireless.  However, I'm not quite sure how the procedure works on Ubuntu, but to connect manually,
```

sudo dhcpcd eth0

```
should do the trick.

---

### Post by Keen101 on 2008-12-24
yeah, if you don't want it at all i think this command will remove it.

```
sudo apt-get remove nm-applet
```

---

### Post by newbee70 on 2008-12-24
> **viridity said:**
> I searched this forum. Someone asked this question but the answer he got was simply "uncheck the checkbox". Yeah right...

OK I unchecked the checkbox but next time I login it's checked again. So my question is, how to make this a "setting", i.e. keeping it unchecked permanently?

The reason is, I don't want to get into other people's wireless network. I have my own wired connection.

Thanks very much.

have you left clicked on the network icon and manually configured your connections?

---

