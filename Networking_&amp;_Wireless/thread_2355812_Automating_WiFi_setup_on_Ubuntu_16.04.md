---
title: "Automating WiFi setup on Ubuntu 16.04"
date: 2017-03-16
forum: Networking &amp; Wireless
---

### Post by efonseca on 2017-03-16
Hello Everyone, 

I'm trying to automatically setup user wireless connection on login, and for that, I've tried different approaches:

[LIST]
[*]Generating the configuration file manually under /etc/NetworkManager/system-connections 
[*]Creating the connection with nmcli 
[*]Creating the connection via dbus python script 
[/LIST]

Connection details:

wpa + peap/mschapv2 with NO CA Cert required.

All the three methods above work to a certain extent, connection gets created, but then users cannot save the password, because of a very trivial detail: the GUI interface does not pick up the "No CA Cert is required" checkbox.

[ATTACH=CONFIG]274182[/ATTACH]

Another option I have, is to also set the user password when I create the connection, but then I have another issue, the option expose_authok for pam_exec.so fails with exit code 2...

So here are my questions:

1. Where does the Network Manager GUI stores that checkbox value ? Because it is not on the configuration file, and FALSE (check box checked) is actually the default value (I can see that when I do a nmcli con show [connection_name]) 

2. What does it take to setup ubuntu to allow pam_exec to expose the user password so I can read it on my scripts and add it to the connection setup ?

Thanks,
Esteban.

---

### Post by efonseca on 2017-03-27
I've finally solved this by exposing the user password to a script that configures the wifi connection if it does not exist, reset password if changed, delete the connection and setup again if a different user logs into the machine. 

Cheers,
Esteban.

---

