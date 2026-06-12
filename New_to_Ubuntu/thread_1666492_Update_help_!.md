---
title: "Update help ?!"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by stfn94 on 2011-01-13
I have problem , i was update nvidia drivers and when i reboot ubuntu starts and he wants Ubuntu login : 
Password : 


i tipe correct and he say


Welcome to ubuntu 
* Documentation :   [http://help-ubuntu.com/](http://help-ubuntu.com/)


216 packages can be updated
71 update are security updates.

bla bla 

bla bla


To tun a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.



Sry im noob , what next ? ?


Please help ? :S thanks

---

### Post by Ocxic on 2011-01-13
seems the drivers didn't install properly, type this without quotes:

"sudo apt-get update && sudo apt-get dist-upgrade"

then reboot

"sudo reboot"

---

### Post by Rex Bouwense on 2011-01-13
Did you just install your operating system?  If that is the case, it is merely telling you that there are that many updates to the system and programs that are installed.  To install them just enter in a terminal:
sudo apt-get update
sudo apt-get upgrade
The first command will update the packages and the second will download and install the updates.  You will be asked for your password.  Type it in.  The flashing curser will not move.  Just hit enter.  That will begin the update process.  It will take a while so relax and have a cup of coffee or two.

I was under the impression that the OP wanted to update not upgrade the distribution.

---

### Post by stfn94 on 2011-01-13
> **Ocxic said:**
> seems the drivers didn't install properly, type this without quotes:

"sudo apt-get update && sudo apt-get dist-upgrade"

then reboot

"sudo reboot"


Same again ! :(

---

### Post by stfn94 on 2011-01-13
> **Rex Bouwense said:**
> Did you just install your operating system?  If that is the case, it is merely telling you that there are that many updates to the system and programs that are installed.  To install them just enter in a terminal:
sudo apt-get update
sudo apt-get upgrade
The first command will update the packages and the second will download and install the updates.  You will be asked for your password.  Type it in.  The flashing curser will not move.  Just hit enter.  That will begin the update process.  It will take a while so relax and have a cup of coffee or two.

yes i have installed then i go to adapter manager and download and install driver for my nvidia graph card  , then i restart and i got this screen ... :(

---

### Post by stfn94 on 2011-01-13
Bump when i tipe 

sudo apt-get update

he say 
W: failed to fetch <adress> could not resolve 'us.archive.ubuntu.com'
and than spamm x 1000 times :S
then i tipe 
sudo apt-get upgrade

he asked me for downloading 200 mb of upgrade i press y and he again start spamming same ! :( i can reinstall ubuntu becouse i have windows7 as dual boot but i also need driver for my graph ! if have one way to get it but without this ? thanks !

---

### Post by Morrad on 2011-01-13
> **stfn94 said:**
> Bump when i tipe 

sudo apt-get update

he say 
W: failed to fetch <adress> could not resolve 'us.archive.ubuntu.com'


Is this a laptop you're talking about?  It sounds like it's not connected to the network (presuably, you're hoping you're connected wirelessly).

I'm not sure how wireless works from the command line, but if you have an ethernet cable, you can connect to the internet by just plugging that in.  That would let you be able to actually connect.

---

### Post by stfn94 on 2011-01-13
> **Morrad said:**
> Is this a laptop you're talking about?  It sounds like it's not connected to the network (presuably, you're hoping you're connected wirelessly).

I'm not sure how wireless works from the command line, but if you have an ethernet cable, you can connect to the internet by just plugging that in.  That would let you be able to actually connect.
You are right ! i just put ethernet , he downloaded and now work fine thanks ! :)

---

