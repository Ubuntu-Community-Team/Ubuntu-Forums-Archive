---
title: "Help updating Play on Linux"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by mikebilak on 2011-09-06
I keep getting a message that there is a new version of PlayOnLinux but I can't seem to either update or upgrade it.  I've tried both apt-get update and apt-get upgrade...What do I try next???

---

### Post by pappusarkar on 2011-09-06
I hope this helps if you are on natty

wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget [http://deb.playonlinux.com/playonlinux_natty.list](http://deb.playonlinux.com/playonlinux_natty.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

---

