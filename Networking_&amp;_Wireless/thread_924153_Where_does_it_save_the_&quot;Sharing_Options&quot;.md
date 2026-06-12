---
title: "Where does it save the &quot;Sharing Options&quot; ?"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Cobra_Fast on 2008-09-19
Hi,

i want to use my old Ubuntu (8.04) Computer as a Network Storage Server.
That for i created some sharing folders with Nautilus.
Now i want to add a sharing folder, but i cannot find the configuration-file over SSH.
And i dont want to build around with my Hardware to get it runnig with my screen, mouse, keyboard and everything.

I looked in /etc/samba but there is nothing that has to do with the shares i created.

---

### Post by Cobra_Fast on 2008-09-23
*push*
i'd really like to know this

---

### Post by issih on 2008-09-23
I'm pretty sure the file you are after is smb.conf, which is just in the /etc directory.

i.e. its full path is:

```
/etc/smb.conf
```

A better option might be to start a vncserver and connect with vncviewer from another machine...that way you can get a gui interface without having to connect stuff up to the machine.

Edit: I was wrong it is in /etc/samba/smb.conf

---

### Post by Cobra_Fast on 2008-09-23
Thanks,

but now i found them in
```

/var/lib/samba/usershares/

```

---

