---
title: "cant get wireless internet to work"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by ireallydontcare on 2009-02-08
hey
ive tried pretty much everything to get my wireless internet working and its getting really annoying.
i installed the driver for my atheros wlan card and when i go to hardware drivers it says the driver is activated and currently in use.
read somewhere that i need to install "linux-backports-modules" but synaptic manager thing doesnt have it and when i download it, it doesnt let me for some "dependency is not satisfiable" reason

use ubuntu 8.10

what do i doooooooooooo

---

### Post by zipperback on 2009-02-08
Please open a terminal window and issue the following command:

```

lspci

```

Then provide us with the output.

Thank you.

- zipperback
:popcorn:

---

### Post by nothingspecial on 2009-02-08
Go to system > administration > software sources and enable everything in the third party tab. Then -

Go to system > administration > hardware drivers then disable anything in there.

Then

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver


```
sudo modprobe ath5k
```

To make it load everytime you boot
Code:

```
gksudo gedit /etc/modules
```

and add
```


ath5k
```

To the end of the file

save
close
reboot

---

### Post by ireallydontcare on 2009-02-08
haha after i did

sudo apt-get install linux-backports-modules-intrepid-generic

it all installed and thats all g but told me to reboot which i didnt, but the second thing with the modprobe ath5k didnt work so i rebooted, and now it wont start up, it says this:

 * starting Avahi m/DNS/DNS-SD Daemon avahi-daemon [fail]
Timeout reached while wating for return value
Could not recieve return value from daemon process

haha sorry

---

### Post by ireallydontcare on 2009-02-08
oh and then the next line is some Cupsd thing and then doesnt do anything

---

