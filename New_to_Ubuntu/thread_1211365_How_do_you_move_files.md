---
title: "How do you move files"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by richie1913 on 2009-07-12
Hi,I need to move my wvdial.conf file from /etc to usr/bin I have tried everything I know whuch I admit Is not a lot can any one help

---

### Post by kellemes on 2009-07-12
> **richie1913 said:**
> Hi,I need to move my wvdial.conf file from /etc to usr/bin I have tried everything I know whuch I admit Is not a lot can any one help

```
sudo mv /etc/wvdial.conf /usr/bin
```

---

### Post by Paqman on 2009-07-12
As a normal user you only have permissions to modify files in your home folder. To move anything outside of your home, you need to take on higher privileges.

You can do this on the command line by prefixing your command with sudo, or using a GUI you can open the file browser as root by hitting Alt-F2 and:
```

gksu nautilus

```
Make sure you close Nautilus as soon as you've moved the files.

---

### Post by nhasian on 2009-07-12
In the future you can run nautilus file manager with root privileges from a terminal or with Alt-F2: 

```
gksu nautilus
```

[COLOR="Red"]WARNING[/COLOR]: with root privileges it is possible to bork your system if you move or delete a system critical file.  Use with caution.

---

### Post by richie1913 on 2009-07-12
Thanks all,sorted now

---

