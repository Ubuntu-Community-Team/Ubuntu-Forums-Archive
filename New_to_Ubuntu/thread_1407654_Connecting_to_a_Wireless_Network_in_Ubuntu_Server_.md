---
title: "Connecting to a Wireless Network in Ubuntu Server 9.10"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Vorksholk on 2010-02-15
Hello, good day. I have recently set up an Ubuntu Server (9.10) on a Dell Latitude CP*x*. I have no wireless card in the computer, so have a wireless USB card (b/g) plugged in. I want to connect to my router, which has WPA security. How would I go about this? Thanks! :D :popcorn:

---

### Post by cariboo on 2010-02-16
If you need to setup your wireless connection from the command line, have a look [here]("http://ubuntuforums.org/showthread.php?t=571188").

If you are running a gui on your server, just use Network-Manager.

This assumes your wireless device is detected and the driver loaded, to check form the command line type:

```
sudo lshw -C network
```

---

