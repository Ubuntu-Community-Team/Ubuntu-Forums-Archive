---
title: "Synaptic GUI won't start"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Majic Walrus on 2011-06-06
Synaptic GUI won't start and Update manager times out and tells me I'm not connected to the internet.

I've been lurking on the Ubuntu forums for a while anyway and I tried a couple of solutions that other people have tried, but no luck. I'm running 10.10. 

If I go into a terminal and run 

> synapticI get a read only gui.  If I try

> gksudo synapticThen I get nothing

If I try 

> gksudo -d synapticThe output is this:

[I]No ask_pass set, using default!
xauth: /tmp/libgksu-qwY7Ot/.Xauthority
STARTUP_ID: gksudo/synaptic/3985-0-LSullivan-lap_TIME7381419
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: -No protocol specified-
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
No protocol specified
(synaptic:3987): Gtk-WARNING **: cannot open display: :0.0
xauth: /tmp/libgksu-qwY7Ot/.Xauthority
xauth_env: /var/run/gdm/auth-for-lsullivan-2OMrqj/database
dir: /tmp/libgksu-qwY7Ot
[/I]




Any suggestions?

---

### Post by Majic Walrus on 2011-06-06
Update:

I got aptitude to run via terminal.  I do not like aptitude running via terminal.  GUI still won't work.

---

### Post by wildmanne39 on 2011-06-06
> **Majic Walrus said:**
> Update:

I got aptitude to run via terminal.  I do not like aptitude running via terminal.  GUI still won't work.
Hi,try
```
gksu synaptic
```then it should ask for your password.

---

