---
title: "Networking ubuntu to XP through a Cross-over cable"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by Nomy321 on 2007-12-13
Well, I am a recent convert to Ubuntu on my primary system. I have another workstation with XP installed on it. I am new to ubuntu so I have not been able to share:

1: My internet connection on ubuntu system with the XP.
2: My files on both systems.

I tried the steps explained by "storm bringer" in one of his posts about Samba, but the PCs are not connecting somehow. During the process, I have installed Samba, DHCP3-server, and IPmasq on my system.

I need some basic "from scratch" steps so that I could get both the systems to talk to each other. Better if someone suggest an easy GUI gadget for the same.

Thanks and regards.

---

### Post by jonandrews on 2007-12-13
I've made a simplified illustrated guide to XP / Ubuntu networking that might shed some light on the issue

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

(It was  Stormbringer's guide that first got me networked, but, as a Windows guy, at the time I must admit I found it hard to understand the overview of what I was doing !)

Hope it helps

---

### Post by Nomy321 on 2007-12-14
Thanks for your reply, 

The problem that Iam facing right now is , after following Storm Bringer's steps, I have successfully installed Samba , and even configured smb.conf to be used with it. I even created Users and Passwords for MyFiles in ubuntu. Moreover, I configured XP system for WINS and its having same workgroup i.e Mshome , as it is in Samba's configuration file. 
But I cant see XP system from ubuntu and neither can I see ubuntu from XP. and both systems aint sharing internet as well...

Please help!!!

---

### Post by tech0007 on 2007-12-14
Hi,

We basically have the same setup so hope this might work for you.  I got this from a post.

ethX - NIC to the XP machine
ethZ - NIC to the internet

sudo ifconfig ethX 192.168.0.1
sudo iptables -t nat -A POSTROUTING -o ethZ -j MASQUERADE
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sudo apt-get install dnsmasq ipmasq
sudo /etc/init.d/dnsmasq restart
sudo dpkg-reconfigure ipmasq
Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

To share files with XP thru samba:

sudo apt-get install samba smbfs
sudo mkdir /home/public
sudo chmod 777 /home/public/
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo nano /etc/samba/smb.conf
  workgroup = WORKGROUP
  security = share
  printing = cups
  printcap name = cups
[public]
  comment = Public Folder
  path = /home/public
  guest ok = yes
  read only = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

sudo /etc/init.d/cupsys restart
sudo testparm
sudo /etc/init.d/samba restart

Good luck.

---

### Post by Nomy321 on 2007-12-15
Thnks for the reply .
 I have done everything you mentioned ...and then configured XPs NIC to automatic detect settings ...The XP machine is now getting IP address and a subnet mask but still, it is not connecting to internet .....

Any Solutions???

---

