---
title: "trouble with terminal server client"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by underdog512 on 2006-10-27
I am am trying to connect to a fedora box via terminal server client and I keep getting a "No route to host error"  what does this mean?  is there another way to connect to a remote machine, perhaps through the terminal?

---

### Post by scxtt on 2006-10-27
what type of connection are you trying to make?  VNC, SSH, RDP, etc. ... ?

---

### Post by underdog512 on 2006-10-28
I can ssh through the terminal just fine, but I would like to do rdp

---

### Post by scxtt on 2006-10-28
AFAIK, there's no RDP *server* for linux (there may be, not entirely sure :p) ... you should use VNC for a GUI connection to fedora ... just start a **vncserver** on your fedora box and use a vnc client (krdc or some terminal server client w/ VNC support) to connect to it.

---

### Post by gerowen on 2006-10-28
If you want to change the port your vncserver runs across you can start one in the command line with:

```
vncserver :displayhere rfbport:enterporthere
```

For example if I wanted to start one on display 1(so it wouldn't interfere with current on-screen activity) and on port 8000, it would be:

```
vncserver :1 rfbport:8000
```

I believe that's right, been a while since I've done it via the terminal.

---

