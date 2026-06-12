---
title: "Windows XP internet connection through Ubuntu Server"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Langr on 2009-02-21
I'm currently installing Ubuntu Server on a computer as I type this. I have a question: Can I have the Ubuntu Server share it's internet connection with a computer running Windows XP. I have the necessary hardware: The Ubuntu Server is utilizing two NICs, one which connects to the household router which it does flawlessly, the other is connected to the back of the Windows XP. I know how to configure Windows XP to get it's internet connection manually, but how do I setup Ubuntu?

Another quick question: Does this require me to setup the Ubuntu Server to also run as a DNS Server?

---

### Post by Iowan on 2009-02-21
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a nice article on connection sharing.

---

### Post by sandyd on 2009-02-21
you can do it via squid proxy

```

sudo apt-get install squid

```
modify the config file a little bit and.... done!

---

