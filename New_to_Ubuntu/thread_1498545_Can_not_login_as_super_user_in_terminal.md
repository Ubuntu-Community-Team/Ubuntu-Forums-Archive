---
title: "Can not login as super user in terminal"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by rudysuryanto on 2010-05-31
I can not login as super user in terminal on ubuntu 10.04, in terminal I type su, then I type password, although I typed the correct password, but appear display, authentication failure. Where is the problem? Thank's.

---

### Post by lisati on 2010-05-31
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2010-05-31
> **rudysuryanto said:**
> I can not login as super user in terminal on ubuntu 10.04, in terminal I type su, then I type password, although I typed the correct password, but appear display, authentication failure. Where is the problem? Thank's.
If you're too lazy to read lisati's link, just use ```
sudo -i
``` instead of *su*

---

### Post by YWELLC on 2010-05-31
sudo -i is safest/most accepted way.

Short of that, to enable access to root enter in terminal:

```

sudo passwd root

```

enter password
re-enter password.

Root is enabled, you can su if you please...

---

### Post by aysiu on 2010-06-01
> **YWELLC said:**
> sudo -i is safest/most accepted way.

Short of that, to enable access to root enter in terminal:

```

sudo passwd root

```

enter password
re-enter password.

Root is enabled, you can su if you please...
Please do not tell people to enable the root account for login. It is almost always *wholly unnecessary*, and it also renders useless a lot of tutorials asking users to boot into recovery mode (which can't be done if one has both set and forgotten one's root password).

---

### Post by Ozymandias_117 on 2010-06-01
> **aysiu said:**
> Please do not tell people to enable the root account for login. It is almost always *wholly unnecessary*, and it also renders useless a lot of tutorials asking users to boot into recovery mode (which can't be done if one has both set and forgotten one's root password).

Then we would have to tell people how to boot to a LiveCD and modify certain files which we don't want to do. ;)

---

### Post by aysiu on 2010-06-01
> **Ozymandias_117 said:**
> Then we would have to tell people how to boot to a LiveCD and modify certain files which we don't want to do. ;)
Exactly.

I can't tell you how many times I've told someone to boot into recovery mode only to be told "I'm asked for a root password," which the user understandably might have forgotten, since Ubuntu almost never prompts you for a root password.

Better not to set it in the first place *unless there is a good reason*.

---

### Post by Ozymandias_117 on 2010-06-01
> **aysiu said:**
> Exactly.

I can't tell you how many times I've told someone to boot into recovery mode only to be told "I'm asked for a root password," which the user understandably might have forgotten, since Ubuntu almost never prompts you for a root password.

Better not to set it in the first place *unless there is a good reason*.

I wish I understood better how they did that so I could set my Debian box up like that :D

---

### Post by peterpan7191 on 2010-06-01
even using 
'sudo su'   does the work..

---

