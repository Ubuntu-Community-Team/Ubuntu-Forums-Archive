---
title: "OpenVPN client for Ubuntu 13.10."
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by hrnsk77 on 2013-12-03
Hi, i cant use network-manager for my OpenVPN connection and haveing a hard time finding a good replacement.

Cant find any good sites on the subject, so i was wondering if any of you have any experience with alternative OpenVPN Client for Ubuntu 3.10?
or maybe a good link to get me going?

thanks in advance.

---

### Post by rossguil on 2013-12-04
Hello!

I am not sure if you would prefer to use a graphical tool, but I use vpnc to connect to my university's vpn:
```
~$ sudo apt-get install vpnc
```

Then you just have to create a configuration file depending on your server's requirements, copy it to vpnc's configuration folder (/etc/vpnc) and invoke the command either manually or via a script:
```
~$ sudo vpnc-connect {your hostname here}
```

The link I used is in french (yep, first language here) but the code is still valid and you can use google translate to help you a bit:[http://ulavalgeek.blogspot.ca/2011/09/connexion-au-vpn-de-luniversite-laval.html](http://ulavalgeek.blogspot.ca/2011/09/connexion-au-vpn-de-luniversite-laval.html)

Good luck with your vpn experiences!

---

### Post by eva-evapz on 2013-12-04
Hi,

you can try Gopenvpn, which is a very easy graphical gui to use vpn server(s).
you can download it here : [https://launchpad.net/~gopenvpn/+archive/gopenvpn/+build/2462465](https://launchpad.net/~gopenvpn/+archive/gopenvpn/+build/2462465)

I'm using it on ubuntu 12.04 but It seems to work as well with ubuntu 13.10 but need some few manipulations to install all it needs to get it work, but quite doable steps !

So let me know if you are interested to choose this solution, so i'll guide you in the different steps, cause all the tuto i found are in french, so i'll have to translate it for you :-)

Once you downloaded the deb file (amd 64bit) you'll just have to double click it, and it'll get install automatically using the software center.
But after that you'll have to make the icon appear in the system tray to be able to use it.

So let me know.

---

