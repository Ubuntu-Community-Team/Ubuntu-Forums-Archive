---
title: "Broadcom 4318 Wireless problem"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by skirk on 2007-06-13
I'm running Fiesty on a Gateway laptop.
I don't have a network connection, only a wireless (which I can run in Windows) and dial up modem.
So I can't use repositories for my install.
I've downloaded the bcm43xx-fwcutter....deb (in windows) and have the local copy of bcmwl5.sys, so I believe I have the 2 files needed.
When I run "sudo dpkg -i bcm43xx-fwcutter...deb"
I get the error: parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name

It appears that it's trying to access the net, but as I said I don't have a network connection.

So is there a way to install bcm43xx-fwcutter and then bcmwl5.sys without using repositories, and the network?
Thanks,
Steve

---

### Post by VON_CAPO on 2007-07-10
To use bcm43xx-fwcutter, you will need a second file called " wl_apsta.o "

I had use this combination and it works right away, but it has a downside ---> the network is unstable and you will suffer from periodic disconnections.

By the other hand, you have the NDISwrapper method, you will need 2 files to make it work ---> " bcmwl5.sys " and " bcmwl5.inf ".
This method is sometimes hard to setup. But it is the best.

---

### Post by kevdog on 2007-07-10
First try the bcm43xx way.
[COLOR="Red"][U][https://help.ubuntu.com/community/Wi...river/bcm43xx/]("https://help.ubuntu.com/community/Wi...river/bcm43xx/")
[http://linuxwireless.org/en/users/Drivers/bcm43xx]("http://linuxwireless.org/en/users/Drivers/bcm43xx")
[/U][/COLOR]
Download this driver [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o) and this package [COLOR="Red"][U][URL="http://packages.ubuntu.com/feisty/ut...m43xx-fwcutter"]http://packages.ubuntu.com/feisty/ut...m43xx-fwcutter
[/URL][/U][/COLOR]
Then install the bcm43xx-fwcutter by double clicking on it or use this command.

```
sudo dpkg -i bcm43xx-fwcutter_006-1_i386.deb
```

Now extract the firmware from the driver straight into the correct folder with this command.

```
sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` wl_apsta.o
```

---

