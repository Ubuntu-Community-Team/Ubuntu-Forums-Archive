---
title: "Linksys USB Wifi (v2) driver problem"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by duckysrmyfriends on 2009-01-06
Hi, 

I'm having the same problem. I've used Ubuntu on my laptop for about 3 years now, so I haven't had much trouble with wireless there. However, I just installed Ubuntu to a second hard-drive on my desktop, and although internet works fine with an ethernet connection, I can't get the Linksys wireless adapter to pick up the wireless signal at my house. I was able to download the driver for the adapter (it's an older version: 2.8), but is there some way that I can use the USB adapter to pick up a wireless signal for my desktop?

Thanks so much for your help!

---

### Post by linuxford on 2009-01-08
I think step one is that you got to get the "build-essential" package and its dependencies installed. This package has the c compiler and make program that can take your source code, and compile it into the proper binary code that your computer uses. 

After you have the build-essential, I believe then it is a matter of discovering what drivers you need to install, finding them and then to install them.

---

### Post by linuxford on 2009-01-11
> **linuxford said:**
> I think step one is that you got to get the "build-essential" package and its dependencies installed.

To get build essential, trying inserting your Ubuntu Linux CD that you used to originally install Linux, mine has the build-essential package, yours may too. Then load the package manager by doing this

```
System~> Administration~> Synaptic Package Manager
```

This will open the Package Manager

```
Edit~>Add CDROM
```

After it loads, click ```
Search
``` then type ```
build-essential
``` then Left-mouse-button on it, and mark it for installation and then click apply

---

