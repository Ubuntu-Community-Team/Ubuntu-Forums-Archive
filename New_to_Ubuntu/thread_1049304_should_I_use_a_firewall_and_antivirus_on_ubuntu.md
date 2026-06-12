---
title: "should I use a firewall and antivirus on ubuntu?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by kapi on 2009-01-24
new to ubuntu and hear so much regarding security - wondered what the best protection is for the average computer and ubuntu

thanks

Kapi

---

### Post by gjoellee on 2009-01-24
Your firewall is set up and runs by default in Ubuntu. 
In Linux or BSD you don't need antivirus.

The best protection is staying away from the root/superuser, which is disabled by default in Ubuntu. So in Ubuntu you don't need to do anything to get the security you need. You should rather be worried about people tricking you to do bad commands like "rm -rf" which will delete everything on your harddisk.

Edit: check this link for extra good security: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by diablo75 on 2009-01-24
You actually already have a firewall installed.  It's called iptables.  You can modify it's policy by installing Firestarter (via Applications>Add/Remove...)

There is no need to install any anti-virus software in Linux, unless you're wanting to do fell Window users the favor of filtering stuff you send out to them that doens't harm you, but might harm them.  While looking through the above Add/Remove you can do a search for anti-virus and I think ClamAV will show up.  It's a good one.  But not necessary for Linux.

The primary reason viruses are not a threat is because you are required to type in your password if you want to add/remove/update software.  So the hypothetical virus would have to know your password to even begin to weasel it's way into the system.

---

### Post by kapi on 2009-01-24
thankyou, i thought as much, didn't know about the firewall though. 

very appreciated

kapi

---

### Post by 2hot6ft2 on 2009-01-24
Firestarter is already installed but needs to be setup
System>Administration>Firestarter
it's a simple setup.

Linux doesn't really need an anti virus (seee here [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)) but it is installed by default anyway. If you want a gui for it use this in a terminal
Applications>Accessories>Terminal

```
sudo apt-get install clamtk
```

then it will be in
Applications>System Tools>Virus Scanner

If you want avast or AVG look here. [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Avast and AVG only have 32 bit versions.

And to add avast to the menu the instructions are here. [http://forum.avast.com/index.php?topic=34748.0](http://forum.avast.com/index.php?topic=34748.0)

---

### Post by russu52 on 2009-01-24
if you want to crash your system go ahead and try avg... you've been warned!

---

### Post by Nepherte on 2009-01-24
> **2hot6ft2 said:**
> Firestarter is already installed but needs to be setup.
Firestarter is *not* installed by default, the firewall is. The average user doesn't have to setup the firewall either since no services are listening, hence no ports are opened.

---

### Post by medic on 2009-01-24
suppose i want to use torrent software to download some files then will i have to open some ports to get the software working?

---

### Post by Paqman on 2009-01-24
> **medic said:**
> suppose i want to use torrent software to download some files then will i have to open some ports to get the software working?

Nope, not on Ubuntu. Depending how your router is set up, you may need to fiddle about with that, but probably not.

---

### Post by binbash on 2009-01-24
you may need a firewall according to the usage of the box but you do not need any antivirus unless you are sharing your files with a windows box.

---

