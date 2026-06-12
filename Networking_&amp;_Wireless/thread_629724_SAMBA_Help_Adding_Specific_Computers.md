---
title: "SAMBA Help: Adding Specific Computers"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by timo1023 on 2007-12-02
Hey,

Im on a Windows network and I want to restrict access to my share to only a few computers. I know the computer names, but I want to add them as samba users without adding them as unix users, and I also think there is a way to only allow access to a certain computer. How can I do this?

Thanks

---

### Post by timo1023 on 2007-12-02
I think I can use the command

```

sudo smbpasswd -a -m COMP_NAME

```

To add a computer to my samba profiles, but that command yields 

```

Failed to modify password entry for user COMP_NAME$

```

I think I have to change my security setting but I can't figure out which one to change to.

---

