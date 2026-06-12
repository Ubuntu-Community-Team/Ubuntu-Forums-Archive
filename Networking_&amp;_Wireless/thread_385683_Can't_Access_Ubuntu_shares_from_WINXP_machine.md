---
title: "Can't Access Ubuntu shares from WINXP machine"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by harpman on 2007-03-16
Set up new machine with Ubuntu Linux. 
Seems to be working fine and going online.
I can see other machines on the network (all windows XP) and access their files.
I can see the Linux machine from my Windows XP machines:
However when I attempt to access the Linux machine from the Windows XP machine, a username and password is requested. I put in my Linux username and password and it keeps asking again.
How do I make the Linux machine happy from the Windows XP machine so that I may access the Linux folders from there?

Thanks.


harpman

[email]pae422@yahoo.com[/email]

---

### Post by gradedcheese on 2007-03-16
You need to add yourself (and any other users you need) to smpasswd, I wrote instructions about this [over here]("http://andrey.thedotcommune.com/samba.html") but basically:

```

sudo smbpasswd your_user_name

```

and then:

```

sudo /etc/init.d/samba restart
```

---

### Post by techboyjk on 2007-03-16
Have you created your samba login? 

If your windows username is John, you might want to try creating a samba account on the linux machine that matches that account...  setup the account with the same username/pw as the windows user. then you might have to define that user in your smb.conf if you are restricting users...

sudo smbpasswd john
-enter your pw

sudo /etc/init.d/samba restart

---

### Post by techboyjk on 2007-03-16
> **gradedcheese said:**
> You need to add yourself (and any other users you need) to smpasswd, I wrote instructions about this [over here]("http://andrey.thedotcommune.com/samba.html") but basically:

```

sudo smbpasswd your_user_name

```

and then:

```

sudo /etc/init.d/samba restart
```

beat me to it....

---

### Post by harpman on 2007-03-16
Thank you.
Adding the username on the command line did it.

---

