---
title: "MY  System is very  slow"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Siva Sankaran on 2011-03-25
I have Dual boot in my system Windows XP along with ubuntu 10.10
ram size is 1 GB
Processor : Pentium Dual Core 2.7 GHz
disk space : 100 GB
 I don't know how to describe information about network.My Pc is connected to Internet using external ADSL modem with 512 Kbps bandwidth

   The problem is If I click any application it is appeared after 5 or 10 seconds until busy cursor is showing in taskbar. Firefox is crashed once. How to troubleshoot the system  and improve system performance

---

### Post by clhsharky on 2011-03-25
Siva Sankaran


You might need to install video driver.
Whats your video chip?

Terminal
```
lspci | grep  VGA
```



Sharky

---

### Post by Arijit_Kundu on 2011-03-25
also post the output of

cat /etc/hosts

---

### Post by NightwishFan on 2011-03-25
Ubuntu is getting to be fairly new end for a 1gb machine. It may take a bit to start applications however once launched they should perform admirably.

---

### Post by Siva Sankaran on 2011-03-25
Thank you for reply

Output for :cat /etc/hosts

192.168.1.2    workstation    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    workstation    localhost6.localdomain6    localhost6
127.0.1.1    cvam-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


 Output for : lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

---

### Post by NightwishFan on 2011-03-25
My chip is similar:
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

And it works fantastic with Ubuntu. You are already using optimal drivers for it.

---

### Post by Arijit_Kundu on 2011-03-25
first take a back up of your /etc/hosts file. (copy it after opening nautilus with sudo)
then you can try the following:
sudo gedit /etc/hosts

then edit the file to look like following

192.168.1.2 workstation # Added by NetworkManager
127.0.1.1 localhost cvam-desktop
127.0.1.1 cvam-desktop

# The following lines are desirable for IPv6 capable hosts
#::1 localhost ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts


but i never did this, so, if it does not help, replace the file with the backed up file.

---

### Post by Siva Sankaran on 2011-03-29
I have gone thru the wikipedia . According to it  host file is used to map the hostnames to IP adddress. What'll happen when I make change as you've said. Please explain your logic to my problem

---

