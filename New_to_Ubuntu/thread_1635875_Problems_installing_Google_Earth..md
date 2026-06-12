---
title: "Problems installing Google Earth."
date: 2010-12-02
forum: New to Ubuntu
---

### Post by 6invivo on 2010-12-02
Hi,
I was installing GE with bin file and 
I was able to resolve the connection error with this scenario (combined from different replies on different forums)
 
sudo apt-get autoremove
sudo apt-get install lsb-core
./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
sudo mv setup.gtk2 setup.gtk2.bkup
sudo mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh
 
and I am ignoring ipv6
 
I tried different things, the crucial was installation of lsb-core, IMO

---

### Post by uRock on 2010-12-02
Hello and Welcome to Ubuntu Forums. 

I have moved your post to its own thread.

Kind regards,
uRock

---

### Post by karthick87 on 2010-12-02
[[COLOR=Sienna]**See this thread it may help you.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1633653")

---

