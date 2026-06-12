---
title: "Networking between Ubuntu and XP SP2"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by BorgCymru on 2005-11-25
Laptop has Ubuntu installed

Desktop has XP SP2 installed

Both can ping each other

When I try to use Places/Network Servers to connect from the lappy to the desktop i get a log in box.

Login details are

Desktop
Name: Richard
Password:********
IP: 10.0.0.7
Sub Net 255.0.0.0


Lappy
Name: richard
Password: ********
IP: 10.0.0.33
Sub Net 255.0.0.0

Password are the same

The network on the desktop is called BRYN

When I try these details into the login box it wont allow me to log in, it just keeps going back to the log in box.

Netwok is working fine between desktop and other XP lappy.

Any tips for a Ubuntu newbie please ?

thanks

---

### Post by cdhotfire on 2005-11-26
I think you need Administrator password to get into windows box.  Thats what happened when I was doing this.  Once you get it, just put Administrator in username and then put password.  Otherwise, I have no idea.:confused:

---

### Post by Corvillus on 2005-11-26
In nautilus, hit ctrl-L, type smb://host/c$ where host is the hostname or IP address of your Windows box, then when prompted, login to the Windows box with an account that has administrator priveleges. If everything is working properly, you should now be in C:\ on the Windows box. Otherwise, you might need to install samba.
```
sudo apt-get install samba
```

---

### Post by akseli on 2005-11-27
[QUOTE=BorgCymru]Laptop has Ubuntu installed

Desktop has XP SP2 installed

Both can ping each other

When I try to use Places/Network Servers to connect from the lappy to the desktop i get a log in box.

Login details are

Desktop
Name: Richard
Password:********
IP: 10.0.0.7
Sub Net 255.0.0.0


Lappy
Name: richard
Password: ********
IP: 10.0.0.33
Sub Net 255.0.0.0

Password are the same

The network on the desktop is called BRYN

When I try these details into the login box it wont allow me to log in, it just keeps going back to the log in box.

Netwok is working fine between desktop and other XP lappy.

Any tips for a Ubuntu newbie please ?

thanks[/QUOTE]

IF you want an even easier way of accessing your shares install a program called LinNeighborhood

If you need help getting it drop me an email

---

### Post by Ozitraveller on 2005-11-27
[quote=BorgCymru]Laptop has Ubuntu installed
 
Desktop has XP SP2 installed
 
Both can ping each other
 
When I try to use Places/Network Servers to connect from the lappy to the desktop i get a log in box.
 
Login details are
 
Desktop
Name: Richard
Password:********
IP: 10.0.0.7
Sub Net 255.0.0.0
 
 
Lappy
Name: richard
Password: ********
IP: 10.0.0.33
Sub Net 255.0.0.0
 
Password are the same
 
The network on the desktop is called BRYN
 
When I try these details into the login box it wont allow me to log in, it just keeps going back to the log in box.
 
Netwok is working fine between desktop and other XP lappy.
 
Any tips for a Ubuntu newbie please ?
 
thanks[/quote]
 
I have it working.
 
I find the biggest problem is with firestarter (firewall) blocking the network. SO I usally disable it first to get the network going, and restart firestarter and adjust the settings.
 
This might help to get you going:
[http://ubuntuguide.org/#sambaserver]("http://ubuntuguide.org/#sambaserver")
 
But if you haven't got samba installed, do it you need it. Here's how:
 
sudo apt-get update
sudo apt-get install samba
sudo apt-get install smbfs

---

