---
title: "Network Connection configuration"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by MakubeX on 2010-08-10
Hi everyone! It has been a very long time since I last visited this forum.

Anyway, it was my first time to install Ubuntu 10.04 via Wubi. (install on Windows without reformatting). I was the one setting up our lab and it's now running dualboot Ubuntu & Windows.

Everything was going fine although I instructed my students how to configure the network. When I rebooted some of their PCs, I found out that there were some conflicts with the configuration file. It seems that the settings are not permanent (so I had to reconfigure it again).

I was wondering if there's a way via terminal (or some configuration file) to make sure that the network config doesn't get messed up after reboot. 

I'm familiar with restarting the network via (/etc/init.d/networking). However, I had to right click the toolbar above just to disable/enable the network. Sometimes, after reboot, there were 2 eth's (eth0, eth1) that were reflected on the Network Connections list.

Thanks so much!

---

### Post by c9-3Rr0r on 2010-08-10
To make your changes to be permanent edit file 

**/etc/network/interfaces**

---

### Post by dineshs on 2010-08-10
pl try this
First backup configurations using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
then configure static IP via NM following this (use your IP /DNS while configuring)
[http://ubuntuforums.org/showpost.php?p=9693408&postcount=3](http://ubuntuforums.org/showpost.php?p=9693408&postcount=3)

---

### Post by MakubeX on 2010-08-10
thanks so much!

my linux skills have broken down because my primary computer is a mac while my secondary one is ubuntu. i use ubuntu for teaching. :)

so does this mean that there's no config file where i can simply put the ip,subnet, and gateway just like how i configure DNS's on /etc/resolv.conf?

thanks again.

---

### Post by dineshs on 2010-08-11
If you are using NM you shold enter IP mask,DNS etc as mentioned in that link via GUI.The details can be seen in /etc/NetworkManager
(I think there is a folder system-connections).May be you can edit the files
For restarting NM the command is different

---

### Post by MakubeX on 2011-01-11
> **dineshs said:**
> If you are using NM you shold enter IP mask,DNS etc as mentioned in that link via GUI.The details can be seen in /etc/NetworkManager
(I think there is a folder system-connections).May be you can edit the files
For restarting NM the command is different

Hi, I'm just bumping this old thread (related from [http://ubuntuforums.org/showthread.php?t=1660966](http://ubuntuforums.org/showthread.php?t=1660966)). It seems that there's a problem for Ubuntu to keep to values of the network configuration. In this old thread, I was using Ubuntu 10.04, but now I'm using Ubuntu 10.10 and it's still the same. I already tried creating the interfaces file and I already tried the GUI method as well. The network configuration of my lab would've been easy if it's just DHCP but unfortunately it isn't.

Is this a Network Configuration bug?

---

