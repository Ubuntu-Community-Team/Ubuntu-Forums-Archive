---
title: "/etc/apt/sources.list: ??"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-03
can anyone please tell me where to find this.... /etc/apt/sources.list:
i am trying to install remastersys and cant find this to add the file

---

### Post by 3rdalbum on 2010-12-03
Don't modify this file directly.   Instead, go to Synaptic Package Manager and Settings > Repositories.

---

### Post by bananas4370 on 2010-12-03
> **gmenfan83 said:**
> can anyone please tell me where to find this.... /etc/apt/sources.list:
i am trying to install remastersys and cant find this to add the file

Just download the deb file and install using gdebi. If you don't have gdebi then

```
sudo apt-get install gdebi
```

Firefox gives me the option of installing deb files I go to download.

Cheers
Patrick

---

### Post by uRock on 2010-12-03
I add repos via GUI. Go to System> Administration> Software Sources, then click on the "Other Software" tab, then click the add button and add your line.

---

### Post by jplo on 2010-12-03
Well, I've attempted to add it, but, it would seem that it is impossible to connect to this repository. Instead, you can download the current version. [This link]("http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb") leads to it now. To download more future versions, go to [http://www.geekconnection.org/remastersys/repository/karmic/](http://www.geekconnection.org/remastersys/repository/karmic/) in your web browser.

---

### Post by gmenfan83 on 2010-12-03
> **uRock said:**
> I add repos via GUI. Go to System> Administration> Software Sources, then click on the "Other Software" tab, then click the add button and add your line.
this way was actually how i was going to originally install but got to this step and i realize i dont have software sources?

---

### Post by jplo on 2010-12-03
> **gmenfan83 said:**
> this way was actually how i was going to originally install but got to this step and i realize i dont have software sources?
  In 10.10 software sources was moved into the Ubuntu Software Centre's edit menu. However, this repository cannot be accessed,[ so use this link for the current version 2.0.17.]("http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb")

---

### Post by gmenfan83 on 2010-12-03
> **gerbilschool said:**
> Well, I've attempted to add it, but, it would seem that it is impossible to connect to this repository. Instead, you can download the current version. [This link]("http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb") leads to it now. To download more future versions, go to [http://www.geekconnection.org/remastersys/repository/karmic/](http://www.geekconnection.org/remastersys/repository/karmic/) in your web browser.
thank you i did this and it installed just fine!

---

