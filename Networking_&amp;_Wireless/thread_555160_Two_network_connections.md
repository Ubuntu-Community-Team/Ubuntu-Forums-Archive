---
title: "Two network connections"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2007-09-19
Hi, does anyone know how to get ndiswrapper to load on startup. i know where the sessions thingy is, but it doesnt work when i add ''modprobe ndiswrapper'' to it. when i boot up i have to go to terminal and login as root and type ''modprobe ndiswrapper'' then scan and connect from terminal.
  Also is there a way to have my wifi connection and my wired connection enabled and connected at the same time. i get my internet via wifi and i cant get it via ethernet.  please help me.

---

### Post by noob12 on 2007-09-20
Just add a line **ndiswrapper** to **/etc/modules**.

---

### Post by Dwiman89 on 2007-09-20
I couldnt find modules under etc. how do i add the line when i find it too.

---

### Post by noob12 on 2007-09-20
That's odd.  There's a default one installed with Ubuntu.
```

cat /etc/modules

```

This will create one with the single line in it, or append to that file, so you can run it in either case.
```

echo "ndiswrapper" | sudo tee -a /etc/modules

```

---

