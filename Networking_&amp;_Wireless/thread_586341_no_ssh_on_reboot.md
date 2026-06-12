---
title: "no ssh on reboot"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by bigbadsi on 2007-10-22
I've installed openssh-server on a fresh Ubuntu 7.04 install, following these instructions: [mythtvinstall]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend#head-84a927a780adeeb37e41907044fc1b4ecb061d33").

After I reboot the machine I cannot ssh into the box without geting a "connection refused" message, without first going:

```
sudo /etc/init.d/ssh restart
```

I've had NIC issues with this machine (Windows XP will also only run at 10Mbps) and networking wouldn't work without first going:

```
mii-tool -F 10baseT-FD
```

Can anyone tell me why ssh isn't running after a reboot?

Thanks.

---

