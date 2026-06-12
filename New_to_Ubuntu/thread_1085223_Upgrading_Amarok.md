---
title: "Upgrading Amarok?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by cptrohn on 2009-03-02
I am also wanting to try and upgrade to the new version of Amarok tonight as well....

Is there a Wiki for this on Amarok's website?

---

### Post by sandyd on 2009-03-02
[http://amarok.kde.org/en/node/482](http://amarok.kde.org/en/node/482)

google is your friend

```

sudo gedit /etc/apt/sources.lst

```add
this to the end 
```

deb http://ppa.launchpad.net/project-neon/ubuntu hardy main
```[I][U]then
[/U][/I]```
sudo apt-get update
``````
sudo apt-get install amarok-nightly
```

---

### Post by hockeyhead019 on 2009-03-02
this doesn't work as it says that the package is no longer available :( anything else... and i've googled my face off and have found nothing helpful haha

i'm running on ubuntu 8.10

---

### Post by sandyd on 2009-03-02
fixed and updated my instructions ;)
forgot 1 line.....

---

### Post by hockeyhead019 on 2009-03-02
ok cool and will this let me update when amarok gets a new release... ex 2.1.0 to 2.1.1?

---

