---
title: "Hi"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by superfocus121 on 2009-09-28
Hi,

I'm very new to Linus. I've just installed Ubuntu 9.04 and I'm having problems viewing a cam on one of my favourite sites.

Can anyone help?

Thanks

---

### Post by sandyd on 2009-09-28
hi and welcome!

Go to 
Applications -> Accessories -> Terminal\

enter this in
```

sudo apt-get install flashplugin-nonfree

```or to install a whole bunch of codecs along with flash,
```

sudo apt-get install ubuntu-restricted-extras libdvdcss2

```when you get to the SUN java EULA, press TAB to comfirm (ive seen a LOT of people get stuck here wondering how the heck they accept the EULA)

---

### Post by beastrace91 on 2009-09-28
Does your favorite site happen to be stickam?

~Jeff

---

### Post by superfocus121 on 2009-09-28
thanks and wish me luck.

---

### Post by superfocus121 on 2009-09-28
It didn't work for me :(

---

### Post by credobyte on 2009-09-28
```
sudo apt-get install ubuntu-restricted-extras sun-java6-jre sun-java6-plugin

```

Upon finishing installation, restart Firefox and try again ..

---

### Post by sandyd on 2009-09-28
> **superfocus121 said:**
> It didn't work for me :(
are you usin 64 bit?
if you are, beta flash plugin you will need to use.

---

