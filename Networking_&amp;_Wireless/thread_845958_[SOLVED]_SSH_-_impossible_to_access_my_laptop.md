---
title: "[SOLVED] SSH - impossible to access my laptop"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by herger on 2008-07-01
Hi all. Hope this is the right place to post... :)
I have a problem: on my Dell XPS 1330 with Gutsy, I have ssh properly functioning (I can connect to every pc in my office).
The vice-versa is impossibile: I cannot access my laptop via ssh from anywhere.
I have NO routers, just direct LAN connection.

I post You some information that may be useful

```

$ nmap -p 22 <ip_address>

Starting Nmap 4.20 ( http://insecure.org ) at 2008-07-01 10:27 CEST
Interesting ports on <ip_address>:
PORT   STATE    SERVICE
22/tcp filtered ssh

Nmap finished: 1 IP address (1 host up) scanned in 10.364 seconds


```


then


```

$ nmap -P0 localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2008-07-01 10:34 CEST
Interesting ports on localhost (127.0.0.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE
538/tcp open  gdomap
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.072 seconds


```

what can I do?
I have already tried

```

$ sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 22 -j ACCEPT

```

but nothing chanced: I need to access my laptop from another pc to back up some large files....

Thanks in advance and regards

Herger

---

### Post by superprash2003 on 2008-07-01
are you trying to access via LAN?? if so are you able to ping successfully?

---

### Post by herger on 2008-07-01
Hi! Thanks for Your reply.
The internet access (from my laptop) has no problems: I can ping to every pc in the office...
I can also access from my laptop to my pc, but I can't do the opposite...
Thanks and regards

Herger

---

### Post by kevdog on 2008-07-01
Obviously the port is filtered -- most likely be a firewall.  The rule you appended to the iptables will be no good if there is a rule higher up in the chain that drops any incoming tcp connection on port 22 (or whatever port).

Do you have a firewall running or did you maniputlate iptables prior to messing with this setup?

I'm sure if you flush all the firewall rules as a test:
sudo iptables -f
sudo iptables -X

And then redo a port scan the ssh port will be open?  My guess is that you are automatically blocking port ssh somewhere else!

---

### Post by herger on 2008-07-01
Hi. Thanks again.
Here are the posts:

```

sudo iptables -f
[sudo] password for ------:
iptables v1.3.6: no command specified
Try `iptables -h' or 'iptables --help' for more information.
$ sudo iptables -f
iptables v1.3.6: no command specified
Try `iptables -h' or 'iptables --help' for more information.
$ sudo iptables -X
$ 

```

then I went to [www.canyouseeme.com](www.canyouseeme.com) BUT

```
Error: I could not see your service on xxx.xxx.xxx.xx on port (22)
Reason: Connection refused
```

I do not know if I have a firewall running: I have always kept the default settings of Gutsy, and never manipulate iptables or anything else...

Thanks and regards

Herger

---

### Post by kevdog on 2008-07-01
Sorry itd
sudo iptables -F
This is of course on the server machine or the ssh server

Can you post:

sudo iptables -L

Also are you running ssh server on port 22?

---

### Post by herger on 2008-07-01
Hi.
The reply with sudo iptables -F and sudo iptables -X is the same, on the site [www.canyuseeme.com](www.canyuseeme.com)... 

Then, 

```
~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```


Sorry for my deep ignorance: what do You mean with "*> running ssh server on port 22*"?

Thanks and regards

H

---

### Post by kevdog on 2008-07-01
Hold on


Do you have the openssh-server installed?  Is it listening on port 22?  Note that it can be listening on a different port if you want -- just substitute your port number of your ssh server for 22 in the commands I list below.

netstat -lnptu

Within the output you should have a line similar to:
tcp6       0      0 :::22           :::*             LISTEN  2335/sshd

That line above would state the sshd (ssh server daemon is LISTENING on port 22).

Your firewall policy is wide open, so this isn't blocking it.

From a different computer on the LAN, what is the output of

nmap -p22 <LAN ip address of ssh server>

Just kind of confused about your setup.

---

### Post by hyper_ch on 2008-07-01
did you actually install a ssh server?

```

sudo apt-get install openssh-server

```

---

### Post by herger on 2008-07-01
HI! IT works!!
I installed openssh-server, and now I can access to my laptop.
Thanks again!!!!  :)

Herger

---

### Post by kevdog on 2008-07-01
Hmm, the one-and-only "I forgot to install the server so why isn't it working" bug.  I've fallen victim to this myself before!! :D

---

### Post by herger on 2008-07-01
:D
Thanks again!!

---

### Post by hyper_ch on 2008-07-01
install script... always use an install script to install your fav. apps ;) that way you won't forget anything ;)

---

### Post by kevdog on 2008-07-01
Have any examples? or a master install script?

---

### Post by hyper_ch on 2008-07-01
something like:
```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f backup_files/sources.list /etc/apt/sources.list
cp -f backup_files/secring.gpg /etc/apt/secring.gpg
cp -f backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

apt-get update
apt-get -y upgrade

# Skype/amsn
apt-get -y install skype amsn

# Java
apt-get -y install sun-java6-jre sun-java5-jre

# Postfix
apt-get -y install postfix

#KDE Appz
apt-get -y install kopete konversation konqueror k3b amarok krfb ktorrent kftpgrabber kate kontact kdepim-kio-plugins kgpg akregator gdb

# Burn Programs
apt-get -y install gnomebaker

# IRSSI / OpenSSH/gnump3d
apt-get -y install irssi openssh-server gnump3d

# OTR
apt-get -y install python-glade-1.2 python-gtk-1.2

# VmWare
apt-get -y install linux-headers-`uname -r` build-essential xinetd

# Browsers
apt-get -y install kazehakase opera flashplugin-nonfree

# Codecs
apt-get -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

# OpenOffice
apt-get -y install openoffice.org openoffice.org-gtk

# Various
apt-get -y install vlc mc unrar gparted chkrootkit rkhunter imagemagick numlockx msttcorefonts ntp ntpdate whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev adesklets d4x googleearth htop traceroute libjack0.100.0-dev


#######################
#######################

# Restore other files

#cp -f backup_files/sysinfo /usr/share/apps/konversation/scripts/sysinfo
#cp -f backup_files/screenshot /usr/bin/screenshot

```

---

### Post by kevdog on 2008-07-01
Nice

I thought that xinetd was dead?

---

### Post by hyper_ch on 2008-07-01
vmware still likes to have it... although I have to try if it goes without it also ;)

but basically list your fav. applications that you're going to install anyway, split it up into different sections or let it all go in one turn, and then after installation just run the script ;)

---

