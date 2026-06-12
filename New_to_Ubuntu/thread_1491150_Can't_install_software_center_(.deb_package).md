---
title: "Can't install software center (.deb package)"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by simpleminds on 2010-05-23
Hello.

I'm using Jolicloud (9.04... Jaunty Jackalope..?) with a HP Compaq Mini 110c netbook and I'm quite a newbie to this. I've tried to install a .deb package (software-center_2.0.2_all.deb) with the package installer, and it's all fine until "Error: Dependency is not satisfiable: python-apt (>= 0.7.13.4ubuntu3)" pops up. Help anyone?

Thanks,
Sam

---

### Post by coolbrook on 2010-05-23
The dependencies are satisfied in 9.10+.

---

### Post by simpleminds on 2010-05-23
> **coolbrook said:**
> The dependencies are satisfied in 9.10+.

Which in newbie language is? I'm sorry, but I'm new to this :P

---

### Post by coolbrook on 2010-05-23
You need at least Ubuntu 9.10 to install that package.

---

### Post by simpleminds on 2010-05-23
> **coolbrook said:**
> You need at least Ubuntu 9.10 to install that package.

Okay, thanks for your quick answers ^^

/Sam

---

### Post by Stancel on 2010-07-03
> **coolbrook said:**
> You need at least Ubuntu 9.10 to install that package.

I tried to install it on 9.10, but the same thing happened to me.
> 
Status:[B][COLOR="Red"]
Error: Dependency is not satisfiable: python-apt (>= 0.7.13.4ubuntu3)
[/COLOR][/B]

^looks like that, happens after you open the deb package.

---

### Post by Evanescence on 2010-07-03
> **Stancel said:**
> I tried to install it on 9.10, but the same thing happened to me.


^looks like that, happens after you open the deb package.
Hi, 
I have experienced such an issue before. Did you download a new .deb package or you used the same one you used before? If you used the same one before installing 9.10, then you may have to download the same .deb package and run the install again - tell me if it works :)

---

### Post by warfacegod on 2010-07-03
Try using Synaptic and installing software-center or in a Terminal:

```
sudo apt-get install software-center
```

---

