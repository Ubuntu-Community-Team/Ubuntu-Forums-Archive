---
title: "error while installing arora webkit based browser????"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by manuvaidya on 2009-04-25
i am getting this error after i download the debian package of this arora browser... in ubuntu 9.04 on my lappy..

/tmp/arora_0.6-0ubuntu1~jaunty1~upstream1_i386-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

this is the error i am getting... can anyone help me how to install arora on jaunty????

---

### Post by kpkeerthi on 2009-04-25
You probably do not have gdebi installed. You can install with
```
sudo apt-get update && sudo apt-get install gdebi
```

Then download the deb file to your Desktop and just double-click to open.

To install from command-line (assuming the .deb file in on your desktop),
```

cd ~/Desktop
sudo dpkg -i *.deb

```

---

