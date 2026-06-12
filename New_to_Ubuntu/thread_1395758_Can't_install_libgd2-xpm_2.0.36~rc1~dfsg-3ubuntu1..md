---
title: "Can't install libgd2-xpm_2.0.36~rc1~dfsg-3ubuntu1.9.04.1_i386.deb"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by abybaddi on 2010-02-01
As said in the title when I manually try to install libusplash-dev_0.5.31_i386.deb it shows the dependency for libgd2-xpm_2.0.36~rc1~dfsg-3ubuntu1.9.04.1_i386.deb and when I open this file for installaion it shows conflicts with libgd2-noxpm installed in the system.

I went to synaptic, marked it for removal and it says it will remove ubuntu-desktop too. What should I do?

I want to create and modify usplash themes on my ubuntu.

Thanks in advance.

---

### Post by Bachstelze on 2010-02-01
Are you sure you need to install that package? Usually, when two packages conflict, it's because they provide the same functionality.

---

### Post by abybaddi on 2010-02-01
I need that package to install "libusplash-dev_0.5.31_i386.deb" and change usplash themes as I like them.

Is there any other option?:confused:

---

### Post by Bachstelze on 2010-02-01
Just install [font=monospace]libusplash-dev[/font] from the repos:

```
sudo apt-get install libusplash-dev
```

or with your favourite package manager...

---

### Post by abybaddi on 2010-02-01
But I have no internet at home due to incoming annual exams. And right now I'm at a cyber cafe.

:sad:

---

### Post by Bachstelze on 2010-02-01
You can get it from [http://packages.ubuntu.com](http://packages.ubuntu.com)

The package you are trying to install is for an older release of Ubuntu, that's why it's not working on your system.

---

### Post by abybaddi on 2010-02-04
Ok. I'll get 'em.

---

