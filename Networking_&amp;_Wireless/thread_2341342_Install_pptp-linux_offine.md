---
title: "Install pptp-linux offine"
date: 2016-10-27
forum: Networking &amp; Wireless
---

### Post by sesamelai on 2016-10-27
I installed an Ubuntu 16.04 server on my HP workstation. However, I am only allowed to connect to the network via VPN. The only way I know to do this via command line is through PPTP-linux([http://serverfault.com/questions/422475/how-do-i-configure-vpn-connections-on-ubuntu-server-with-no-gui](http://serverfault.com/questions/422475/how-do-i-configure-vpn-connections-on-ubuntu-server-with-no-gui)), but pptp-linux is not installed by default. So my question is, is there any way to install it offline? (I have another computer which has network.) It does not have a deb file, so I can not install it by this way: [https://subinsb.com/debian-ubuntu-install-software-offline#article-install-software-with-dependencies-offline](https://subinsb.com/debian-ubuntu-install-software-offline#article-install-software-with-dependencies-offline).

If this is too difficult, is there any other solution to solve my problem? Thanks.

---

### Post by chili555 on 2016-10-27
I suggest that you download the deb files from here: [http://packages.ubuntu.com](http://packages.ubuntu.com) Download the packages appropriate to your architecture:```
arch
```And your Ubuntu version:```
lsb_release -c
```Here, as an example, is the lnk for 16.04, Xenial: [http://packages.ubuntu.com/xenial/pptp-linux](http://packages.ubuntu.com/xenial/pptp-linux) You can see that the dependencies are binutils, libc6 and ppp. I expect that the first two are already installed, by default; check:```
sudo dpkg -s binutils | grep Status
```Download the appropriate deb files and install them:```
cd directory/where/you/downloaded
sudo dpkg -i *.deb
```I know nothing about ppp, so that's it; that's all I know!

---

### Post by sesamelai on 2016-10-27
Thanks. It works.

---

### Post by chili555 on 2016-10-27
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

