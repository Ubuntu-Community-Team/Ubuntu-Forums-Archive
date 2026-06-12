---
title: "just installed ubuntu linux and google chrome but youtube videos wont play?"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by paulh1974 on 2010-07-09
hi guys, how do i get youtube videos 2 run? iv just installed ubuntu linuxs latest version with google chrome but the vidoes wont play . thanks

---

### Post by Andrew-J on 2010-07-09
Hello again, I think generally adding the medibuntu repositories works for most people, did for me at least, but there is lots of documentation on this topic in the forum archives and even just through google. 

Here is a link to medibuntu: [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by cj13579 on 2010-07-09
You probably need to enable a flash plugin.

---

### Post by audiomick on 2010-07-09
Hi.
I suspect you are missing Flash or something like that. Go to the software centre and install
ubuntu-restricted-extras

---

### Post by Aquatic Fist on 2010-07-09
I think this should work. Atleast for Firefox.

```
sudo apt-get flashplugin-nonfree
```

---

### Post by Evgeny on 2010-07-09
```

sudo apt-get install flashplugin-installer

```

fixed for ya ... :)

---

### Post by paulh1974 on 2010-07-09
> **audiomick said:**
> Hi.
I suspect you are missing Flash or something like that. Go to the software centre and install
ubuntu-restricted-extras

yeh that done the trick. thanks michael

---

### Post by Paqman on 2010-07-09
> **Aquatic Fist said:**
> I think this should work. Atleast for Firefox.


Chrome gets it's Flash from Firefox, so it'll work for both.

---

