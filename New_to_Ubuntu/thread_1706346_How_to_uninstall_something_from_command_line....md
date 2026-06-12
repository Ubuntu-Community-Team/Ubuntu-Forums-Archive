---
title: "How to uninstall something from command line..."
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Jim2029 on 2011-03-13
So I installed this game from [http://wildfiregames.com/0ad/](http://wildfiregames.com/0ad/) and I had to use the command line and a bunch of things. Well I want to remove it but i have no clue how to. Any ideas? I also want to remove it from the Games Menu as well.

Thanks.

---

### Post by Wobblybob on 2011-03-13
The instructions to install are

sudo apt-get install 0ad

so to remove use

sudo apt-get remove --purge 0ad

this will remove the program and it's files.

If you are using the Gnome desktop then right click on the Applications menu and select editor to look at removing items and menus.

---

### Post by Jim2029 on 2011-03-13
> **Wobblybob said:**
> The instructions to install are

sudo apt-get install 0ad

so to remove use

sudo apt-get remove --purge 0ad

this will remove the program and it's files.

If you are using the Gnome desktop then right click on the Applications menu and select editor to look at removing items and menus.

Thanks, but I'm not sure it worked...

jim@jim-HP-Pavilion-dv6700-Notebook-PC:~$ su
Password: 
root@jim-HP-Pavilion-dv6700-Notebook-PC:/home/jim# sudo apt-get remove --purge 0ad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 256 not upgraded.
root@jim-HP-Pavilion-dv6700-Notebook-PC:/home/jim#

---

### Post by Wobblybob on 2011-03-13
no looks like it has not worked perhaps this prog has no de install route, check the synaptic package manager to see if it shows it as installed.

---

### Post by Jim2029 on 2011-03-13
> **Wobblybob said:**
> no looks like it has not worked perhaps this prog has no de install route, check the synaptic package manager to see if it shows it as installed.

Thanks. i forgot about the Synaptic Package Manager... Found it in there and un-installed it. I only check the Ubuntu Software Center before.

---

