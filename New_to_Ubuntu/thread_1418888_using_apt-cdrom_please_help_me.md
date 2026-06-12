---
title: "using apt-cdrom please help me"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Fibernet on 2010-03-01
I am using ubuntu server. I am supposed to install the ubuntu-desktop to ubuntu-server from cdrom but when I use the command apt-cdrom I got error karmic main restricted what should I do with this problem

---

### Post by Kakers on 2010-03-01
Have you got cdrom selected in your software sources ?

---

### Post by Fibernet on 2010-03-01
not yet but how to select cdrom sources? im just use the command apt-cdrom add

---

### Post by oldos2er on 2010-03-01
You're using a desktop version CD, right?

---

### Post by Fibernet on 2010-03-02
no im using ubuntu server cd and I download alternate cd and now I insert to cdrom and I use the command apt-cdrom

---

### Post by mikewhatever on 2010-03-02
Are you using <sudo apt-cdrom add> or just apt-cdrom?

---

### Post by oldos2er on 2010-03-02
> **Fibernet said:**
> no im using ubuntu server cd and I download alternate cd and now I insert to cdrom and I use the command apt-cdrom

The server CD doesn't have any Gnome packages that I'm aware of. I have no experience with the alternate CD, but if I had to guess (take that for what it's worth), I'd think it would work.

Edit: The correct command is ```
sudo apt-cdrom add
```

---

### Post by Fibernet on 2010-03-02
I use the command line sudo bash and then "apt-cdrom add" but not work. I try to check the kernel maybe I am not on the right kernel

---

