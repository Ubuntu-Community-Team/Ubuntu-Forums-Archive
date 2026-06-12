---
title: "User authentication error - su"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by CSHANKY on 2010-04-30
When I try to do su . I get "su: Authentication failure" using my regular password.

Can someone please help solve this issue?

---

### Post by wojox on 2010-04-30
Have a read here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jrothwell97 on 2010-04-30
su does not work, it asks you for the super-user's password (which doesn't exist since the super-user is locked).

I suggest using sudo -i instead to get a root shell.

---

### Post by nitstorm on 2010-04-30
sudo gives you temporary superuser priveleges. better use that .

but if u really really want to be a superuser ( i.e., root) you need to set a root password

```

sudo passwd root

```

first you'll be asked for the sudo password and then u'll have to set the root password by typing it in twice. After that when you execute *su *punch in the unix root password you just set.

---

### Post by Paddy Landau on 2010-04-30
> **nitstorm said:**
> but if u really really want to be a superuser...
This is strongly discouraged for Ubuntu.

Best to stay with sudo (or gksu with GUI programs).

---

### Post by nicfallenangel on 2010-04-30
**This is the correct way to get su working, but *not* the right way as per Ubuntu:**

> **nitstorm said:**
> sudo gives you temporary superuser priveleges. better use that .

but if u really really want to be a superuser ( i.e., root) you need to set a root password

```

sudo passwd root

```

first you'll be asked for the sudo password and then u'll have to set the root password by typing it in twice. After that when you execute *su *punch in the unix root password you just set.

**This way is more secure than su and *should* be used to gain root access in Ubuntu and other linux distros. From what I remember, this method gives you root access, but protects system files from a careless command. I could be wrong about that though. Always use root privileges cautiously.**
> **jrothwell97 said:**
> su does not work, it asks you for the super-user's password (which doesn't exist since the super-user is locked).

I suggest using sudo -i instead to get a root shell.

---

### Post by jrothwell97 on 2010-04-30
> **nicfallenangel said:**
> **This way is more secure than su and *should* be used to gain root access in Ubuntu and other linux distros. From what I remember, this method gives you root access, but protects system files from a careless command. I could be wrong about that though. Always use root privileges cautiously.**

Yes.

Bottom line: use sudo, don't assign root a password. If you need a root shell, use sudo -i.

---

