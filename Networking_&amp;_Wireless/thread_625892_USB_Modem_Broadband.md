---
title: "USB Modem Broadband"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by urinnersmile on 2007-11-28
Hello all,

I am from India and my ISP is BSNL Dataone ( A broadband service). I have been provided with a modem from Quidway(WA 1003 A) with a driver CD that works only on Windows. It's a USB modem. 

I don't know how to set up a connection, now that I dont have a driver for Ubuntu.

Please help. Anyone here from India using Dataone?

---

### Post by timcredible on 2007-11-28
no ethernet port on the device?  if not, you may want to look at what i did with verizon's wireless broadband card to see if any of it will apply to you:
[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=19&Itemid=27](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=19&Itemid=27)

---

### Post by yellowbread on 2007-11-28
This describes how I recently set up a usb modem on 7.10 without drivers:

[http://ubuntuforums/showthread.php?t=603590]("http://ubuntuforums/showthread.php?t=603590")

It was with a different modem and different ISP, but some of it might help.

Edit: Sorry, I can't figure out how to get the link to work. Looking at the last post's link, 
the information there is esentially the same as what I did.

---

### Post by juano420 on 2007-11-30
where can i find the info to access the internet via usb without drivers

---

### Post by fineas on 2007-12-01
I 'm not from India, but this "dataone" reminded me this:
[http://ubuntuforums.org/showthread.php?t=217976](http://ubuntuforums.org/showthread.php?t=217976)

---

### Post by dineshs on 2007-12-03
Quidway 1003 has ethernet port.Connect via ethernet port,Assign IP 192.168.1.100          mask 255.255.255.0  gateway 192.168.1.1  then configure modem as follows.
Open browser
Type 192.168.1.1  on the address bar – click go
username  <admin>
password   <admin>
click setup then PVC0  on left
select  PPPoE  in type
Enter username and password  in the fields
Go to tools
click system commands
click save all 
click restart
wait till reboot complete say 3 minutes

Now you can directly access internet

---

