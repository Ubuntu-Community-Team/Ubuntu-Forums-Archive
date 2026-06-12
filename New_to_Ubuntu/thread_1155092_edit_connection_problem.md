---
title: "edit connection problem"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by nayeem007 on 2009-05-10
Hi
When I open edit connection menu to edit Auto Ethernet connection settings, I cant set ip address manually. When i select manual option the "apply" button at right bottom corner of the box becomes fade and doesnt work. So i cant save ip address. What can I do??

---

### Post by Triptol on 2009-05-10
You might need to edit the menu option to have it run as root. Or start the program manually with gksu.

---

### Post by nayeem007 on 2009-05-10
How can I do that? im a novice.

---

### Post by Triptol on 2009-05-11
Another thought: does the apply button change color as soon as you fill in some fields? 

And did you create your user after the installation of Ubuntu, or was it created during the installation?

---

### Post by Peter09 on 2009-05-11
Why do you want to do this - are you sure?

---

### Post by tarps87 on 2009-05-11
I believe you have to enter a valid ip and subnet before the button is enabled, then it will ask for your root/sudo password, I believe it will do this even if you don't have permissions and will allow a user that does to enter the name and password but I will just check this.

If you can't change it this way you can use the terminal
```
sudo ifconfig
```
if the interface name, usaly eth0 for wired connections
```
sudo ifconfig eth0 *new_ip*
```
```
ifconfig -h
```
For more commands


Edit:
You can do it with any user, you need to add a new address with a ip address, netmask and gateway. If you don't have a gateway 0.0.0.0 should work

---

