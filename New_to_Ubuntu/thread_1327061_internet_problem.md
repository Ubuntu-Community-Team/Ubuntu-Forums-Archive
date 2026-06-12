---
title: "internet problem"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by charly555 on 2009-11-15
i am using ubuntu 9.10 and xp on my system.. both works well.. but there is a problem with internet connection. i use a time based internet connection. in xp i need to dial to get my internet connected. that saves my internet usage. but in ubuntu 9.10 it gets connected automatically on boot.so i lose my internet time.. sometimes i have to run the "pppoeconf" command to get connected. how can i connect and disconnect the internet as and when i need it??? is there any program like "dial up" in ubuntu 9.10. 

thanks in advance..

---

### Post by hal10000 on 2009-11-15
```
 sudo apt-get install gnome-ppp
```

---

### Post by Junkieman on 2009-11-25
Hi Charly. 

Is this a 3G / wireless dongle that you use to connect? Did you take any steps to set up your internet connection?

Ubuntu comes with [Gnome Network Manager]("http://www.gnome.org/projects/NetworkManager/"), see the link there's a screenshot of what it looks like. Note that the icon is different when you are connected/disconnected.

By default it's icon is in the task top-right, and clicking on it allows you to create or enable broadband/internet connections.

How does yours connect automatically, after you log in, do you see any popups or messages when it goes up?

---

