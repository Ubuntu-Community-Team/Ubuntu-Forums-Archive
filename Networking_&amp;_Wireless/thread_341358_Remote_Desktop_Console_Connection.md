---
title: "Remote Desktop Console Connection"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by cabbage on 2007-01-18
Hi,

Does anyone know how to connect to the console (id0) of a windows server 2003 machine over rdp using Ubuntu?

In windows you would run "mstsc.exe /console" but I can't work out the equivalent...


Many thanks,

Cabbage.

---

### Post by featherking on 2007-01-18
have you tried running

```
rdesktop <ipaddress of server>
```

that is basically the same as running remote desktop from an xp machine? but if you just need the terminal, that may be more functionality than you need?

---

### Post by cabbage on 2007-01-18
I can connect to the server OK, but in Windows Server 2003 it is possible to attach to the actual console i.e. the physically connected screen, mouse and keyboard.

Some messages are only ever displayed on the console so it useful to be able to remotely attach to it. I do this at work a lot, but recently needed to do it from home over VPN and I couldn't figure out how.


Hope that makes sense,

Cabbage.

---

### Post by featherking on 2007-01-18
Looking through the man page for rdesktop..

if you run rdesktop with a zero switch:

```
rdesktop -0 <ipaddress of server>
```

that is supposed to connect to the console (win2k3 server and newer), give that a try?..

---

### Post by dbott67 on 2007-01-18
I think the issue that cabbage is referring to is that RDP connects to a "virtual desktop" and logs out the current user.

If you look under the "Performance" tab in the Terminal Server Client, there is an option to "Attach to Console" that I just tried, but it still logged out my XP computer.

Also, looking in **man tsclient** revealed no options for this.

-Dave

EDIT: of course, you guys have had a few posts clarifying all of this while I was testing it! :)

---

### Post by dbott67 on 2007-01-18
Actually, both featherking's and my suggestions may work... I was trying to connect to the console of Windows XP and I do not think this is an option.

So, as featherking suggests, try: **rdesktop -0 ip.address.of.server** or try my suggestion in post #5.

-Dave

---

### Post by cabbage on 2007-01-18
The "rdesktop -0" does the trick!

I have a slight confession to make though. I'm a KDE user and so have been using krdc (a frontend to rdesktop) to get this to work. It never occurred to me to check the man page for rdesktop!

In future I'll just run rdesktop by hand... 

Thanks for all your help.

---

### Post by featherking on 2007-01-18
"I have a slight confession to make though. I'm a KDE user and so have been using krdc (a frontend to rdesktop) to get this to work."

We wont hold that against you... Glad you got it going :)

---

