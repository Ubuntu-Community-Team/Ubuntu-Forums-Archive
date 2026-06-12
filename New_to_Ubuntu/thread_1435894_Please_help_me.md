---
title: "Please help me"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by charan1983 on 2010-03-22
I want to install xrdp on ubuntu 9.10 to be able to run my thinclients on ubuntu.
I am doing with:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get install libpam0g-dev
sudo apt-get install libssl-dev
sudo apt-get install tightvncserver

tar xvzf xrdp-0.4.1.tar.gz
cd xrdp-0.4.1
make
sudo make install

gconf-editor
apps / gnome-setting-deamon / plugins / keyboard / To set "active" to Disable
Start XRDP Sudo /usr/local/xrdp/xrdp_control.sh start


after it when i turn on my thinclient it does not login to ubuntu. please help me???????

---

### Post by pastalavista on 2010-03-22
You might want to try it the Ubuntu way ```
sudo apt-get install xrdp
``` or Open Software Center or Synaptic Package Manager and search for it.

ps- Welcome to the forums! You seem familiar with hardcore Linux. Ubuntu is a more kind and gentle distro.

---

