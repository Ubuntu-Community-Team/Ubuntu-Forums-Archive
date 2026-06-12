---
title: "Looking for a password generator/manager"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Zeikcied on 2010-12-18
I'm running Kubuntu 10.10 64-bit.  The recent Gawker leak (which affected me, unfortunately) has me on edge about my passwords, and another site I frequent had one of its admin accounts compromised (likely due to the Gawker leak).

I'm curious if there is a program, preferably Qt4-based, that can not only generate passwords but also let me store them and list them based on what sites they belong to.  It will also be great if there's a Firefox add-on that does the same thing.

I have difficulty remembering complex passwords, but I'm getting really paranoid about my password security, and I think I need a better solution than what I'm doing now.  I need more secure passwords, but I also need a way to easily look them up.

---

### Post by karthick87 on 2010-12-18
For password generator you can use pwgen
```
sudo apt-get install pwgen
```

I personally prefer keepassx for storing my passwords.You can try it,```

sudo apt-get install keepassx
```

---

### Post by kostkon on 2010-12-18
keepassx can also generate passwords. And, obviously, I would also recommend it.

---

### Post by Zeikcied on 2010-12-18
Thanks. :)

---

### Post by lovinglinux on 2010-12-19
> **Zeikcied said:**
> I'm curious if there is a program, preferably Qt4-based, that can not only generate passwords but also let me store them and list them based on what sites they belong to.  It will also be great if there's a Firefox add-on that does the same thing.

Firefox built-in password manager can do that. The only thing it doesn't do is generate random passwords. You can do that with [Hash Password Generator]("https://addons.mozilla.org/en-US/firefox/addon/52490/")

However, since you are using KDE, you already have an excellent password manager, that integrates with the platform. It is called KWallet.

You can even store Firefox's passwords in Kwallet, using [KDE Wallet password integration]("https://addons.mozilla.org/en-US/firefox/addon/49357/"). However, I would be cautious about that extension, because it doesn't work on Firefox 4 and that was a version that deleted Firefox passwords. So, backup your profile before using it.

---

