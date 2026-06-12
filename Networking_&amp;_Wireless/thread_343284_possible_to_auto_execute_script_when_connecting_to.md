---
title: "possible to auto execute script when connecting to a certain network?"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by bernstein on 2007-01-21
hey folks
does anyone know if it is possible to automatically execute a shell/python script when one connects to a specified network?

for example, if i connect to my home network "homeNET" i would like to automatically run "mountserver.sh" and when connectiong to "university" i'd like "checkmessages.py"

network names would be based on their SSID

does anyone know how to do this?

---

### Post by IntuitiveNipple on 2007-01-21
Create the script in **/etc/network/if-pre-up.d/**. You might need to create the directory. Make sure to do all this as root so the correct permissions are set:
```
$ sudo su
```
(Enter your own password)

You'd have to tailor your script to check that the ESSID of the connecting network is the one you want, but that is pretty easy to do, and will make a good Sunday afternoon project for you :)

Edit the text configuration file **/etc/network/interfaces** and add the **post-up** directive to the appropriate network connection, for example:
```
auto eth0
iface eth0 inet dhcp
name WiFi
post-up /etc/network/if-up.d/myscript.sh
```
Restart the networking component:
```
$ /etc/init.d/networking restart
```
You can do the same thing in reverse for when the network goes down, using the **pre-down** directive. The range of options is **pre-up post-up pre-down post-down**. For more information read the manual:
```
$ man interfaces
```

---

### Post by bernstein on 2007-01-21
wohhhhhaaaaa man your the king!!!!

it works, and it works so flawlessly and it's so easy.... Linux is a charm!!! :-)

just made a wiki entry.... [OnNetworkConnectionRunScript]("https://wiki.ubuntu.com/OnNetworkConnectionRunScript")

---

### Post by megandy on 2008-03-28
Nice script. Thank you two!

How can the manual be modified to recognize a network not by it's ESSID e.g. when I want to connect to a wired network ?

I think about a use case where a sync will be performed (with Unison) when I connect my laptop to home lan.

Do you have any suggestions?

---

### Post by bernstein on 2008-03-28
mabye just try to ping your server once and if successful mount it... this would certainly work when your server is pingable by an unique name like server.local (look at /etc/hostname & /etc/hosts and maybe /etc/dhcp3/dhcpd.conf on how to set your network up correctly)

---

### Post by chilinski on 2008-03-28
You could also add it to .bash_profile in your home directory on the machine to which you are connecting.

---

### Post by Whiffle on 2008-03-28
Also, WICD provides an option to do this as well, it can run a script before connection, after connection, and after disconnection.

---

