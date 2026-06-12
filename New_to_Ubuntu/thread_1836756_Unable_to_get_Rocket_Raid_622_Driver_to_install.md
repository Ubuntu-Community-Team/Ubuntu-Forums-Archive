---
title: "Unable to get Rocket Raid 622 Driver to install"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by giddyup306 on 2011-08-31
I have a Sans Digital TRM4 bay RAID enclosure that I want to use as external storage.  I cannot figure out how to install the RocketRaid 622 driver for the life of me!  I found a couple of downloads on their site, and the one for non-raid (JBOD).  Is in binary.  

[http://www.sansdigital.com/towerraid/tr4mb.html](http://www.sansdigital.com/towerraid/tr4mb.html)

I called Sans Digital, and the instructions they sent me didn't make any sense, and they wanted me to install Ubuntu Server.  I then read the Ubuntu Rocket Raid docs below and it didn't help.

[https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver](https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver) 

Right now I'm seeing all 4 2TB discs as an 8TB JBOD, so I would be happy in this config or in Raid 0.  Whatever is easier.

---

### Post by giddyup306 on 2011-09-02
I've been trying to get this to work for the past three days and still no go. :confused:

I'm getting closer, but something is still amiss. Here's what the instructions told me to do.,..

```

mkdir /tmp/dd
tar xzvf rr.tgz -C /tmp/dd
cd /tmp/dd
sh install sh

```So I put the file on the desktop, and here's what I got...

```
billy@billy:~$ cd Desktop
billy@billy:~/Desktop$ tar xzvf rr.tgz -C /tmp/dd
boot/
tar: boot: Cannot mkdir: Permission denied
boot/rr62x2.6.31-14-genericx86_64.ko.gz
tar: boot: Cannot mkdir: Permission denied
tar: boot/rr62x2.6.31-14-genericx86_64.ko.gz: Cannot open: No such file or directory
boot/rr62x2.6.31-14-serverx86_64.ko.gz
tar: boot: Cannot mkdir: Permission denied
tar: boot/rr62x2.6.31-14-serverx86_64.ko.gz: Cannot open: No such file or directory
install.sh
tar: install.sh: Cannot open: Permission denied
postinst2.sh
tar: postinst2.sh: Cannot open: Permission denied
postinst.sh
tar: postinst.sh: Cannot open: Permission denied
preinst.sh
tar: preinst.sh: Cannot open: Permission denied
readme.txt
tar: readme.txt: Cannot open: Permission denied
tar: Exiting with failure status due to previous errors
billy@billy:~/Desktop$ clear

billy@billy:~/Desktop$ sudo su
[sudo] password for billy: 
root@billy:/home/billy/Desktop# mkdir /tmp/dd
mkdir: cannot create directory `/tmp/dd': File exists
root@billy:/home/billy/Desktop# tar xzvf rr.tgz -C /tmp/dd
boot/
boot/rr62x2.6.31-14-genericx86_64.ko.gz
boot/rr62x2.6.31-14-serverx86_64.ko.gz
install.sh
postinst2.sh
postinst.sh
preinst.sh
readme.txt
root@billy:/home/billy/Desktop# cd /tmp/dd
root@billy:/tmp/dd# sh install sh
sh: Can't open install
root@billy:/tmp/dd# 

```What am I doing wrong?

---

