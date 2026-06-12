---
title: "Ubuntu how to set up admin permissions for users"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by Tszar on 2014-02-02
hi,
So I have a ubuntu local file sharing server. I want to be able to give admin or highest permission to some people. Im running on command line and not the GUI.
Thanks

---

### Post by Ubi_one_2014 on 2014-02-02
i believe you have to add the username's in the sudoers list

---

### Post by steeldriver on 2014-02-03
You add the user to the sudo *group*

There are several utilities to do that (adduser, usermod) - my favorite is gpasswd

```
sudo gpasswd --add *username* sudo
```

---

