---
title: "SSH server question"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by hookitup on 2011-07-21
hello folks, so on this page [https://help.ubuntu.com/8.04/serverg...sh-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html")
if u go to the bottem where SSH key is , is this done on the server or  the computer thats going to be remoteing into the server ?????



oh and also i am trying to edit something in etc/ssh/sshd_config ,,, 
how do i get into the folder? 

if i do gedit ~/etc/ssh/sshd_config 
or      gedit /etc/ssh/sshd_config
or      gedit ~/.etc/ssh/sshd_config

they open a blank file ,,

if i go to my hold folder in the gui form and then go to etc then ssh,  then open the sshd_config file i can view whats in it but its read only  .. i am looking to edit this to set a banner and disable password and  all that good stuff


thanks for the help

---

### Post by stlsaint on 2011-07-21
try command: 

#this will make a backup of your file before you start editing it
```
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.orig
```

then run:

to open the file in gedit with write privileges
```
gksudo gedit /etc/ssh/sshd_conf
```

---

### Post by hookitup on 2011-07-27
oh it worked , thanks

---

