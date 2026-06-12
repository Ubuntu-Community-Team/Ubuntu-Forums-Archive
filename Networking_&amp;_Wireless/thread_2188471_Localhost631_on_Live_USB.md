---
title: "Localhost:631 on Live USB"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by ekhalkov on 2013-11-17
Hello,
I use Live USB to boot my Ubuntu 13.10
I'm trying to add a network printer via **localhost:631**, but I need to provide username & password to do so. I've tried ubuntu as username with password field empty - didn't work.
Could you please help me with that issue?

---

### Post by steeldriver on 2013-11-17
Is the default live USB ubuntu user a member of the lpadmin group?

```

$ id ubuntu

```

If not, 

```

$ sudo gpasswd --add ubuntu lpadmin

```

You may need to log out and back in for the group membership to take effect.

---

