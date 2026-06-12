---
title: "Terminal command for update manager"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by 10.04newbie on 2010-12-05
Can some kind soul tell me what it is please?

---

### Post by Penguin=) on 2010-12-05
Yes

```
sudo apt-get update
```


tell me how it goes ok?

---

### Post by lindsay7 on 2010-12-05
also try

sudo apt-get upgrade

---

### Post by Chrissd on 2010-12-05
Hi, if you were looking to start the update manager from a command line, then try:

```

gksudo update-manager

```

---

### Post by Penguin=) on 2010-12-05
> **lindsay7 said:**
> also try

sudo apt-get upgrade



Hehe! =)

---

### Post by LinuxCharms on 2010-12-05
The two commands you want are:

sudo apt-get update
sudo apt-get upgrade


Do them separately, then you're all good to go.

---

### Post by Penguin=) on 2010-12-05
> **LinuxCharms said:**
> The two commands you want are:

sudo apt-get update
sudo apt-get upgrade


Do them separately, then you're all good to go.



Yup, you said it all =)

---

### Post by 10.04newbie on 2010-12-05
> **Chrissd said:**
> Hi, if you were looking to start the update manager from a command line, then try:

```

gksudo update-manager

```

Thanks **Chrissd**-That did the trick.

---

