---
title: "Continual &quot;package operation&quot; pop-up after every removal/installation"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-05
> 
Setting up sun-java6-plugin (6.26-1natty1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so doesn't exist.
dpkg: error processing sun-java6-plugin (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up eclipse (3.5.2-8ubuntu3) ...
Errors were encountered while processing:
 sun-java6-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)


Something about Java keeps popping up, everytime I try to install or remove something from my computer.

---

### Post by cariboo on 2011-08-06
From you error message it seems sun-java6-plugin didn't get installed properly, you can use synaptics broken package filter to remove it or from the command line use:

```
sudo apt-get purge sun-java6-plugin
```

---

