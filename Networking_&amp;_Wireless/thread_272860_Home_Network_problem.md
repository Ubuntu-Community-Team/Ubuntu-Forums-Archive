---
title: "Home Network problem"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by case_uk on 2006-10-07
I'm a Newbie to linux, so please bear with me.

what i'm looking todo is have a linux machine on my home network, it will be used for printing and holding music files aswell as a php/mysql/apache server for web-desvelopment.

I have installed Ubuntu 6.06 LTS and sofar everything is working fantasticaly, the problem i'm having is that the linux machine can see all the windoze pc's on the network, but the  windoze XP machines cannot 'see' the linux machine.

I've had little experience with Linux, and even less with networking, so any help would be greatly recieved.

---

### Post by bigken on 2006-10-07
in a terminal type 

sudo aptitude install samba
sudo smbpassswd -e (your name)
sudo smbpasswd -a (yourname )

---

### Post by bigken on 2006-10-07
oh and to add files just go to system/aministration/shared folders ;)

---

### Post by foxmulder881 on 2006-10-07
> **case_uk said:**
> what i'm looking todo is have a linux machine on my home network, it will be used for printing and holding music files aswell as a php/mysql/apache server for web-desvelopment.

Just an observation that I wouldn't recommend using a single machine for both web serving, print serving and also music file serving. It's too many different tasks for the one system to handle. Unless you have top of the range specs of course.

---

### Post by case_uk on 2006-10-07
Sorry, my mistake.

the machine wont be a print server or file server, it will have the printer attached and hopefully printing can be done from other machines and as for the files, i'm planning to attach an external 320gb hard-drive and share it so the music can be access by anyone on the network.

ps. 

is there any way for my linux mcahine to be made visable in the windoze workgroup screen ?

---

### Post by spd106 on 2006-10-07
You need to change the workgroup name in the /etc/samba/smb.conf file. It may be worth having a read through this wiki page [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by clgent on 2006-10-07
I am also having the same issue; however, I am running linux in a mac os x 10.4 environment.  I tried the samba method, and it worked great, so thanks.  But I would rather use something us something other than samba as Windoze is now dead to me and I would rather use something Windoze unrelated.

---

### Post by foxmulder881 on 2006-10-08
> **case_uk said:**
> the machine wont be a print server or file server, it will have the printer attached and hopefully printing can be done from other machines and as for the files, i'm planning to attach an external 320gb hard-drive and share it so the music can be access by anyone on the network.

If it was me, I would have a seperate machine for the printer and external HDD. And leave the other machine for web serving and web serving only.

---

