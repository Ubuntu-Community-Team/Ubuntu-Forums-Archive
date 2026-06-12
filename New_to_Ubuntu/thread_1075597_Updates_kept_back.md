---
title: "Updates kept back?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Kareeser on 2009-02-20
```
The following packages have been kept back:
  linux-image-server linux-server
The following packages will be upgraded:
  libapache2-mod-php5 libpq5 php5 php5-cli php5-common php5-dev php5-mysql
  sudo

```

Why would apt-get keep packages back? Might it be because I'm currently using hardy on my server, instead of intrepid?

uname -r = 2.6.24-21-server

---

### Post by taurus on 2009-02-20
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Kareeser on 2009-02-20
I assume that means yes, it's 'cause I'm on Hardy.

Thanks, taurus :)

I don't have the time, currently, since last time I upgraded from 7.04 to 8.04, my system did a double-take and I had to reconfigure a number of programs... sigh

---

### Post by avtolle on 2009-02-20
No, that's not it; IIRC, use dist-upgrade to install kernel version updates, rather than the simple upgrae command. Someone correct me if I'm incorrect.

---

### Post by mcduck on 2009-02-20
dist-upgrade isn't the same as upgrading to the next distribution version.

Normal "apt-get upgrade" only allows updating packages, "dist-upgrade" allows removing packages if necessary to do the upgrade. You get the same effect if you update using Synaptic Package Manager.

---

