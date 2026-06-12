---
title: "Cisco VPN client for 64-bit"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by bonusiso on 2007-10-01
i need to use cisco vpn client but, there is no version for 64-bit linux. 

so i dont want to emulate 32-bit os :D

how could i install 32-bit version to my 64-bit linux?..

---

### Post by js_fr on 2007-10-01
if you have a .deb package, lets say "cisco-vpn-32bit.deb",  try (in a terminal):
```
sudo dpkg --force-architecture --force-depends -i cisco-vpn-32bit.deb
```

---

### Post by bonusiso on 2007-10-01
if i dont have a debian package???

i have libs and the make file...

[http://cc.hogent.be/public/HOGENT/vpn/software/vpnclient-LATEST-linux.tar.gz](http://cc.hogent.be/public/HOGENT/vpn/software/vpnclient-LATEST-linux.tar.gz) only this one

---

### Post by js_fr on 2007-10-01
Make sure that the ia32 libraries are installed:
```

sudo apt-get update
sudo apt-get install ia32-libs
 
```

Then install the tar.gz as you would do on a 32bit machine (unzip the tar file, run "sudo ./vpn_install", ...) By the way, there seems to be a patch necessary if you want to use the Cisco VPN client on a recent kernel: [http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

If this still doesn't work you can try to install an ia32 chroot system and run the Cisco VPN client inside: [https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292205](https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292205)

---

### Post by bonusiso on 2007-10-02
thank you very much for the information...

it is not about being 64... the problem is about kernel as you said... 

thanks to this link below i installed, and tomorrow i will check if i could connect or not :) ... i need to wait until going school...

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

---

### Post by tlongren on 2007-10-04
Guys, please visit this post again:
[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/#newclient](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/#newclient)

Cisco has released a new version of the VPN client that compiles right out of the box on these recent 2.6.xx kernels.  In other words, no more patching is required.

There's a download link for the  new version at the URL I listed above.

---

