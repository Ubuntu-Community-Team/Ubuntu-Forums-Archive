---
title: "[SOLVED] Change NetBios Name"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by vagelism on 2008-12-14
Hello, is there a way to change my netbios name in linux ?
I would like to do it for a session only and later to use the one i have now.

Thank you ALL.

---

### Post by Dedoimedo on 2008-12-14
In the samba configuration file (/etc/samba/smb.conf), there's a parameter:

netbios name = something

Change it. Exit. Restart samba.

Cheers,
Dedoimedo

---

### Post by bluefrog on 2008-12-14
talking about netbios name is talking about samba (/etc/samba.smb.conf)

changing the name of your computer is changing /etc/hosts and /etc/hostname.

not knowing your way in command line doing this will bring you only trouble.

do not change it.

---

### Post by vagelism on 2008-12-14
Well I found the files that you mentioned.
If I want to change the hostname fros "something" to "something2"
I just need to replace it?
What problems I will have and how can I overcome them?
Thank you.

---

### Post by Dedoimedo on 2008-12-14
Hello,

You can temporarily change the hostname by:

hostname <something>

This will be valid for that session only.

Dedoimedo

---

### Post by vagelism on 2008-12-14
Actually I care to  change the computers name...
So as you said this happents only for the session?
Do I have to restart to take effect? 
I suppose no.
Thank you

---

### Post by Dedoimedo on 2008-12-14
Hello,

1. You can test and see for yourself :) (no, no need for restart).

2. If you want to change the computer name permanently, then you'll have to hardcode the information into a configuration file.

/etc/hostname (if it exists)

On classic Linux, under /etc/sysconfig/network:

HOSTNAME="something"

Cheers,
Dedoimedo

P.S. You can also use GUI ...

---

