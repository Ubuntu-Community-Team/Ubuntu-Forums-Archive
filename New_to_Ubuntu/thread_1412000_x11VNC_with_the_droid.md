---
title: "x11VNC with the droid"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-02-20
So, I have a droid and they recently released a gpled vnc client which supports x11vnc.
So, how do I set up x11vnc on my desktop so I can control it from my phone?

---

### Post by LunaticHiatus on 2010-02-20
shameless bump

---

### Post by krunge on 2010-02-20
Use 'apt-get install x11vnc' to install it.

For testing, why not just try typing "x11vnc" from inside a terminal window inside your desktop.  Then point the droid vnc client to vnc display "hostname:0" where hostname is the name or ip address of the desktop.

If that works and you'd like to automate the x11vnc startup just ask.

---

