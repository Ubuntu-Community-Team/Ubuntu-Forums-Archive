---
title: "Installing an Application from a Flash Drive"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by macmike on 2010-05-26
Hi I  am trying to install ddclient.tar.gz to my Web server from a flash drive. What is the command to do that? Also is there a way to install it directly to the Web Server by using get-apt and going to the dyndns site? Any help appreciated. Trying to get my DNS to resolve so this thing will work.

Mike Hughes

---

### Post by Paddy Landau on 2010-05-26
Why do it that way?

Just go to the Ubuntu Software Centre (or, if you don't have it, Synaptic) and install from there.

Or click this "[install ddclient]("apt:ddclient")" link.

---

### Post by macmike on 2010-05-26
This is a server only no GUI I can't get to a browser. That was why I wanted to install it that way. How do I use the other program you mentioned? No software Center on the server. I am on an iMac looking at the forum.

---

### Post by Paddy Landau on 2010-05-26
> **macmike said:**
> How do I use the other program you mentioned?
You can use the following command from the terminal.
```
sudo apt-get install ddclient
```

---

### Post by _0R10N on 2010-05-26
It depends on what you have inside the tar file. Untar it and then look for a .deb file, if you find it, then run:
```
dpkg -ivh <your_deb_file>
```

If it isn't one, then look for something like install.bin or install.sh, ddclient.bin or ddclient.sh, and run:
```
./<your_bin_file.bin>
```
or
```
./<your_sh_file>
```

if it isn't a bin or sh file, then look for a README file, it will walk you through the installation steps required to get your program installed correctly.

---

