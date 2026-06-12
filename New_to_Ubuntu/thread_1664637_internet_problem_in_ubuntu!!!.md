---
title: "internet problem in ubuntu!!!"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-11
actually i have a dual boot system with windows 7 along ubuntu 10.10... i have an evdo modem which is actually kinda in between 2g and 3g.. the problem is when i use the same modem on windows  browsing and download speed is fantastic but when i switch on ubuntu and use same modem the speed is very poor..often i have to boot in windows only because ubuntu at that time is giving really poor speed and take minutes to download a single ubuntu forum post.. so anybody pls tell me how can i improve this speed so that i need not go to windows..

---

### Post by vivek.pandey on 2011-01-12
somebody please give a solution

---

### Post by sikander3786 on 2011-01-12
Hi.

What is the make of your modem? Are you taking about PTCL Evdo? How did you install the drivers for your modem?

---

### Post by vivek.pandey on 2011-01-12
the company is capitel..connection bsnl..about drivers..its drivers were preinstalled in ubuntu 10.10..i just need to insert the modem..
connections are made as follow
vpn connection->broadband->i enter the user name and password->this is a 1 time setting.. on regular basis i just insert it in usb..i get an option in the notification area and click on connect..

---

### Post by ubaidillah on 2011-01-12
> **neo_aryan said:**
> actually i have a dual boot system with windows 7 along ubuntu 10.10... i have an evdo modem which is actually kinda in between 2g and 3g.. the problem is when i use the same modem on windows  browsing and download speed is fantastic but when i switch on ubuntu and use same modem the speed is very poor..often i have to boot in windows only because ubuntu at that time is giving really poor speed and take minutes to download a single ubuntu forum post.. so anybody pls tell me how can i improve this speed so that i need not go to windows..

You can try this one 

disable ipv6  :gksudo gedit /etc/default/grub


search code GRUB_CMDLINE_LINUX, and change it to  : 
GRUB_CMDLINE_LINUX="ipv6.disable=1"

Save and update grubsudo update-grub2
restart you computer and let us know if this work.

Cheers

---

### Post by vivek.pandey on 2011-01-13
thanx for your method.. i tied but doesnt seem like speed has changed much..i think it is still same very slow on ubuntu

---

### Post by vivek.pandey on 2011-01-13
any suggestion pls!!!!!!!!!!

---

### Post by mooscape on 2011-01-13
Hi Neo_aryan

I have had similar problems once before. My suggestions:

1. There may be a problem with your settings for DNS resolution that is sending the requests in a loop and stalling your system. I highly recommend moving your settings to OpenDNS. I do this as a matter of course on all my machines. You will find full instructions here: 

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

2. I recommend that you do not use dual boot setup. Rather reinstall the latest version of Ubuntu on your machine and run windows within Ubuntu on Virtual Box (PUEL). See: 

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Remember that ubuntuforums and google can get you out of any problems in Ubuntu.... 

Good luck

---

