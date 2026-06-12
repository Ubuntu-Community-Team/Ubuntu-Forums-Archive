---
title: "gnome shell"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by hellomoto on 2010-10-28
I have just done a fresh install of lucid. I am trying to install gnome shell. 

I get the following error:
```

The following packages have unmet dependencies.
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages

```

trying to install libgjs gets:
```

The following packages have unmet dependencies.
  libgjs0: Depends: xulrunner-1.9.2 (>= 1.9.2.8) but 1.9.2.3+nobinonly-0ubuntu2 is to be installed
E: Broken packages

```

any ideas. I don't want to install gnome-shell from source. I would like to download it from a repository. I tried installing the following recommended PPA:

ppa:ricotz/testing

This PPA is working fine but I still get the same errors mentioned above.

---

### Post by Ubuntiac on 2010-10-28
That's just saying that the versions of Xulrunner available in your software sources aren't recent enough, meaning you need to get it from somewhere else.

The easiest option is usually to find what you need in a PPA on Launchpad.

---

### Post by roylkenn on 2010-10-28
I just installed gnome-shell on Lucid myself and the following link helped me to do it.

[https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed")

basically it says to enable the Lucid proposed repository then use the following command to install gnome-shell

sudo aptitude install gnome-shell/lucid-proposed.

This is a testing repository so creating the preferences file suggested on the page would be a good idea.

---

### Post by Harry33 on 2010-10-29
> **hellomoto said:**
> I have just done a fresh install of lucid. I am trying to install gnome shell. 
...
. I would like to download it from a repository. I tried installing the following recommended PPA:
ppa:ricotz/testing
This PPA is working fine but I still get the same errors mentioned above.

Well the truth is the testing PPA of ricotz does not work at all because it is empty.

---

### Post by Hippytaff on 2010-10-29
you can try fixing broken packages with
```

sudo apt-get install -f

```might be worth a try :-)

---

### Post by Harry33 on 2010-10-29
> **hellomoto said:**
> I have just done a fresh install of lucid. I am trying to install gnome shell. 
...
trying to install libgjs gets:
```

The following packages have unmet dependencies.
  libgjs0: Depends: xulrunner-1.9.2 (>= 1.9.2.8) but 1.9.2.3+nobinonly-0ubuntu2 is to be installed
E: Broken packages

```

...

In lucid the latest xulrunner-1.9.2 in main repository is
xulrunner-1.9.2 1.9.2.12+build1+nobinonly-0ubuntu0.10.04.1
so dependencies ought to be OK.

---

