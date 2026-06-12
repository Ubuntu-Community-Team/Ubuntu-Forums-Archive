---
title: "What is ppa?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by melon1234 on 2010-02-10
Hi,

What is ppa? Some people use it to share packages. It seems ppa is a  personal-signed package source. Would you please give me a detailed description?

Thanks,

--
ShenLei

---

### Post by spiderbatdad on 2010-02-10
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by lyall on 2010-02-10
> **melon1234 said:**
> Hi,

What is ppa? Some people use it to share packages. It seems ppa is a  personal-signed package source. Would you please give me a detailed description?

Thanks,

--
ShenLei

see the following link [https://help.launchpad.net/Packaging/PPA]("https://help.launchpad.net/Packaging/PPA")

it should answer your question

good luck and have fun learning

---

### Post by bruno9779 on 2010-02-10
PPAs are [personal package archives]("https://launchpad.net/ubuntu/+ppas").

they are quickly added to your sources.list by:

```
sudo add-apt-repository *[ppa address]*
```

for example, cool themes from some bisigi fellow:

```
sudo add-apt-repository ppa:bisigi/ppa 
```

once you add a repository, its packages will be available in apt.

NOTE: You are adding an unofficial source for your packages, so you should add only sources you trust (like the ones listed in lauchpad).

---

### Post by melon1234 on 2010-02-10
Thank you very much! I just now linked to directhex and upgraded mono-develop from 2.0 to 2.2. Feel very happy to use the latest mono IDE. :popcorn:

---

