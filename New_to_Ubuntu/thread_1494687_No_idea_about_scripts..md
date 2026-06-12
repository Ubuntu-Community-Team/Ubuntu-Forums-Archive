---
title: "No idea about scripts."
date: 2010-05-27
forum: New to Ubuntu
---

### Post by InsaniaEx on 2010-05-27
I have no idea what I am doing. I want to run these commands at startup 
```
 ifconfig eth0 up 
ifconfig eth0 192.168.2.1 
echo "1" > /proc/sys/net/ipv4/ip_forward 
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE 
```
I'm sure someone knows how!

---

### Post by pavel989 on 2010-05-27
why do u want to script it? u can just add the first two into the interfaces, actually do the edit on the third, and im pretty sure u can include the 4th in the interfaces too.

unless you want to run this as a script on a few box.

but if u make the scripts executable, im pretty sure u can either add them to /etc/init.d/

follow this:

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by InsaniaEx on 2010-05-27
So to make it a script, do I just have a text file with those commands, make it executable, and save it in /etc/initd/ ?

---

### Post by dustinmarlowe56 on 2010-05-27
i'm not completely sure about start up scripts, all my custom scripts are saved in /usr/bin (if i can remember correctly, i'm not on my ubuntu machine at the moment), but that is the basic formula: save into a text file, chmod +x 'script name', save in correct directory.

---

### Post by pavel989 on 2010-05-27
what your talking about is a bin, sh, or bash file, however u wanna call it.

u can realistically end it however u want it

however to execute, the file must begin with 

"#!/bin/bash" and u must chmod u+x it so that it can execute

but yeah u have a textfile, of your commands, and preceding the commands u have "#!/bin/bash" on its own line

then u chmod it, and then cp/mv it to /etc/init.d

---

