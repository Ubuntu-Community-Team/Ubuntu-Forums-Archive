---
title: "having trouble installing ubuntu 10.04 Server Edtion 64 bit on external hard drive"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by computerguts on 2010-07-29
Hi, I am trying to install ubuntu 10.04 server edition 64bit on my computer. I burned the iso image file to a cd-r and booted from the cd to install ubntu on an external hard drive that I have. (it is a small 160GB Verbatim external hard drive) I go though the installer and it installs to the external hard drive, I then boot from the external hard drive. When I boot it boots in terminal mode and not in the graphical interface with the desktop and applications. I selected "format this disk" so that I would erase all the currently existing data that I did not need and it installs perfectly but when I try to book it boots in terminal mode. I am currently running windows seven home premium 64 bit as the operating system on the internal hard drive, so I know that my current hardware configuration supports 64bit operating systems. In conclusion, what I am trying to do is to get my computer to boot into the login screen and the desktop so that I can actually use it. Any help would be greatly appreciated, thanks

---

### Post by Naitsirhc Hsem on 2010-07-29
server edition default comes with CLI interface, terminal.  to install a gui, sudo apt-get install ubuntu-desktop.  reboot.  for ethernet in command line, sudo ifconfig eth0 up, sudo dhclient.

---

### Post by computerguts on 2010-07-31
Thanks

---

