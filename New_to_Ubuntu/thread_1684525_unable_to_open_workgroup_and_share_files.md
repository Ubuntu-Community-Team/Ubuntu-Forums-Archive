---
title: "unable to open workgroup and share files"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by elchago on 2011-02-09
OK i am new using ubuntu 10.10 and so far i like it but the only thing i have problems is to be able to connect to the network ,,,,, i am running Windows 7 on the main pc and when i try to connect to the network (Click on Places, Network, Windows Network "icon appears" "right click on it" and get message Unable to mount location, "Failed to retrieve share list from server" ,,,,,,,,, i have try many solutions for the last 3 days but no luck ,,,,,, can somebody help me ,,,,,, i just want to share some music files and be able to connect to sound system and play the music ,,,,, thank you all in advance for the help ,,,,,,,

---

### Post by elchago on 2011-02-09
i got this 


chago@chago-mini:~$ sudo ufw status
[sudo] password for chago: 
Status: active
chago@chago-mini:~$

---

### Post by elchago on 2011-02-09
ok i did try to install samba again but got this 

root@chago-mini:~# sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



then i try 


root@chago-mini:~# sudo /etc/init.d/samba stop
sudo: /etc/init.d/samba: command not found
root@chago-mini:~# sudo /etc/init.d/samba stop
sudo: /etc/init.d/samba: command not found


why is the command not found ,,,,,, need some help

---

