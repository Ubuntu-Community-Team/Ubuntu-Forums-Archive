---
title: "wireshark setup"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by cf0531 on 2010-11-20
I just installed Kubuntu and am still getting familiar with it. I'm trying to get wire shark to work. Unlike when I was using ubuntu i can't login as a root user to a desktop environment which is what i did to use wireshark in ubuntu. Is there a way to do this or to get it working as my regular user account. 

I'm new to linux so the simpler the solution the better. I appreciate the help. Thanks.

~Chuck

---

### Post by marin123 on 2010-11-20
run "kdesu wireshark" from Alt+F2 and type in your password... thats it. you MUST be sudo user if you want to use wireshark because it has to have access to your network device.

---

### Post by Rubi1200 on 2010-11-20
Running Wireshark as root is completely unnecessary!!!

After installation:
```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```Run the commands separately.

(courtesy of forum member cdenley)

From the security stickies by bodhi.zazen:
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)
> **Please do NOT run wireshark as root !!!**

---

