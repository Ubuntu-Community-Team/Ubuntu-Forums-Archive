---
title: "creating a folder under root"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by bigboy7foru on 2009-09-18
Can someone just tell me the command for making a folder under root
 
thats the command that i type in
 
/var/log/openvpn[COLOR=#ff0000](i need to create this folder)[/COLOR]/openvpn-status.log

---

### Post by halitech on 2009-09-18
you would need to use sudo to do anything outside your /home folder

```
sudo mkdir /var/log/openvpn
```
to create the file
```
sudo touch /var/log/openvpn/openvpn-status.log
```

---

### Post by LewRockwell on 2009-09-18
> **bigboy7foru said:**
> Can someone just tell me the command for making a folder under root
 
thats the command that i type in
 
/var/log/openvpn[COLOR=#ff0000](i need to create this folder)[/COLOR]/openvpn-status.logCheerios Mates!

nevermind.

Good Day Mates!

.

---

### Post by Mobil1 on 2009-09-18
Hi if it helps I use Pc Man File Manager which is a file manager you can select to run as root from the Tools open "open current folder as root" 

This might help if you want a really easy graphical way (or just lazy like me) to create and
move folders as root.

Try sudo apt-get install pcmanfm. You'll find it under System > Accessories. :)

---

### Post by bigboy7foru on 2009-09-18
Thanks mobil1 that helps alot  :)

---

