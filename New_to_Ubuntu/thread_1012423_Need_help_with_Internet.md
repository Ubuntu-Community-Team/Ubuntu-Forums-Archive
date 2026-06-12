---
title: "Need help with Internet"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Shakey1994 on 2008-12-15
I am working with Execulink, on a GNet DSL Modem, I need to get it connected to the internet. I tried Sudo PPPoeConf. Please help!](*,)

---

### Post by jbrown96 on 2008-12-16
Are you using 8.10? If so, the new network-manager should be able to handle DSL connections. If you right click on the network icon, choose "edit connections" and then select the DSL tab. I've never used DSL that needs account info, but I believe you should be able to set it up.

Welcome to Ubuntu.

---

### Post by Shakey1994 on 2008-12-16
8.04 I tried everything

---

### Post by eraker on 2008-12-16
In the terminal, have you entered the command: ifconfig. 

If this gives you eth0 and lo output, then your network hardware should be working. The next step is to check the contents of the file /etc/network/interfaces, which describes the way in which linux will attempt to connect to the internet. What is the output of the following:
```
cat /etc/network/interfaces
```

---

