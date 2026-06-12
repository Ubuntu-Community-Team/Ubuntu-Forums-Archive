---
title: "Install VMware Server"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by Ragnoral on 2010-12-16
Hi there.

Im new to ubuntu, i have just installed 10.04 server. how do i install vmware server onto it.

I have searched everywhere and they say to download it. but how do i download it throught the terminal?


Thanks

---

### Post by mendhak on 2010-12-16
There are instructions on doing it here:

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

You may also want to consider virtualbox which is from Oracle and is free.  Popular too.  You can get it by opening Synaptic Package Manager and searching for virtualbox

---

### Post by Paqman on 2010-12-16
Looks like it's a bit of a kludge: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

To download things through the terminal you can use wget:
```
wget http://internet.com/file
```

---

### Post by Ragnoral on 2010-12-16
> **Paqman said:**
> Looks like it's a bit of a kludge: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

To download things through the terminal you can use wget:
```
wget http://internet.com/file
```

i have tried that from the vmware website but it came up with ERROR 403: Forbidden

---

### Post by Ragnoral on 2010-12-16
think ill give virtualbox a go if it is easy enough to get

---

### Post by mendhak on 2010-12-16
Hi Ragnoral, even though you sent me a PM, I'm replying here to make it visible. 

Go to System > Administration > Synaptic Package Manager

Wait for it to load

The in the search box at the top, type

virtualbox

and you should soon see "virtualbox-ose" in your list. 

Right click, install.  Then click Apply button at the top. 

HTH

---

### Post by Ragnoral on 2010-12-16
is there an easy way through the terminal. i only finished installing ubuntu an hour ago. i dont have any gui

---

### Post by Paqman on 2010-12-16
The version of Virtualbox that's in the Ubuntu repos is the Open Source version, which lacks several features. For the full-fat version you can do the following:

```
sudo nano /etc/apt/sources.list
```
then paste in this line:
```
deb http://download.virtualbox.org/virtualbox/debian maverick non-free
```
Ctrl-X, then Y to save and quit. Then:
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

This adds the Virtualbox repository and allows you to install it with:
```
sudo apt-get update
sudo apt-get install virtualbox-3.2 dkms
```

All this info is available at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

---

### Post by Ragnoral on 2010-12-16
Thanks

> =```
deb http://download.virtualbox.org/virtualbox/debian maverick non-free
``` i would assume i would change maverick with lucid


> ```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
``` i get "gpg: no valid OpenPGP data found."

---

### Post by Paqman on 2010-12-16
> **Ragnoral said:**
> 
 i would assume i would change maverick with lucid


You would indeed. My mistake.

> 
 i get "gpg: no valid OpenPGP data found."

Make sure you've not got a typo or something, the key is there. Just cut and paste the command in if possible.

---

