---
title: "CPU scaler not working"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-04-12
I did some sensor applet installing and I cannot adjust my CPU frequency now (via the scaler I have at the top of my desktop). Before this worked just fine, but now it does nothing. 

1. How can I find out what the problem is?
2. How can I correct it?

-Justin

---

### Post by duanedesign on 2009-04-12
In Terminal run:

```
sudo dpkg-reconfigure gnome-applets

```
and make sure you have SUID enabled (which means you will not need to be root to use it)

so if it asks : Should cpufreq-selector run with root privileges? Yes

 "The applet will continue to work if you choose to disable SUID for cpufreq-selector, but only for monitoring the CPU clock frequency. The applet may need to be restarted for a change to take effect."

---

