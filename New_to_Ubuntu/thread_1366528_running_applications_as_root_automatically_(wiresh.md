---
title: "running applications as root automatically (wireshark)"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by RipleyAM on 2009-12-28
I'm forcing myself to use Ubuntu as my main OS.  One of the programs I use on a daily basis is Wireshark which requires root privileges.  Instead of entering "sudo wireshark"  every time I need to use it I want to be able to launch Wireshark as root automatically.  I have allowed my user to connect to wireless and ethernet networks under user setting to no avail.  Is there anything I can do with the exception of using my root account or opening from the terminal.

Thanks
Ripley

---

### Post by thomz92 on 2009-12-28
you want it to open without typing your password everytime? or without using the terminal? You can always make a launcher with the command "gksu wireshark". A window will still pop up and ask you for your password though...

---

### Post by 32034 on 2009-12-28
sudo su -

This will allow you to be root, so you won't be prompted for your root password, but don't accidentally delete things ;-) Thats the risk you take running as root

---

### Post by RipleyAM on 2009-12-28
> **thomz92 said:**
> you want it to open without typing your password everytime? or without using the terminal? You can always make a launcher with the command "gksu wireshark". A window will still pop up and ask you for your password though...

Yeah I should have thought of that.  By the way sorry for being so vague.  Being busy at work effects the thought process a bit.  Thanks. :)

---

