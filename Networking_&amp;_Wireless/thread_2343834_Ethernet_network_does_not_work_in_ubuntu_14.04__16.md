---
title: "Ethernet network does not work in ubuntu 14.04 / 16.04"
date: 2016-11-19
forum: Networking &amp; Wireless
---

### Post by rajamondal369 on 2016-11-19
When i install ubuntu 14.04 and 16.04 on my desktop , ethernet network does not shown . After long internet search when i put the command in terminal :  #"sudo ethtool -s enp2s0 speed 100 duplex full autoneg off"     for ubuntu 16.04 and   #"sudo ethtool -s eth0 speed 100 duplex full autoneg off"     for ubuntu14.04 ,   Then it will find ethernet network and connect to internet automatically . After every restart ,i have to do so to find ethernet network . Please help me.

---

### Post by chili555 on 2016-11-19
Please see: [http://askubuntu.com/questions/850921/network-connection-not-linking-permanently/850927#850927](http://askubuntu.com/questions/850921/network-connection-not-linking-permanently/850927#850927)

Of course, substitute eth0 here.

---

### Post by rajamondal369 on 2016-11-20
Sir , i follow the instruction given above . But it is not working , only if i put the command manually from terminal then ethernet starts working , otherwise it is disabled always .

---

### Post by rajamondal369 on 2016-11-20
This problem with ubuntu starts only few months ago .Before that all versions of ubuntu always connect to my ethernet . Besides ubuntu i have installed windows 8.1 , that works very well with same ethernet . What's the problem i can not find .

---

### Post by Hadaka on 2016-11-20
Hi, please open a terminal ...ctrl/alt/t.. and copy and paste..
This will insure that ethtool will load the parameters  automatically
 when you boot or restart your computer.
*For Ubuntu 16.04
```
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e "sudo ethtool -s enp2s0 speed 100 duplex full autoneg off\nexit 0" | sudo tee -a /etc/rc.local
```
*For Ubuntu 14.04
```
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e "sudo ethtool -s eth0 speed 100 duplex full autoneg off\nexit 0" | sudo tee -a /etc/rc.local
```
boot and test

---

### Post by praseodym on 2016-11-20
Which hardware is in use?
```

lspci -nnk
lsmod
```

---

