---
title: "Connecting to windows network"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by hzrunner on 2009-04-05
I am trying to connect my Ubuntu Dell Inpiron 2650 to my Windows XP home network (main computer there is a Gateway) and I am using a US Robotics router (wireless and wired). The connection to the router works wireless and wired and I can access the internet, but I cannot access my Gatewa. I have tried some of the suggestion in two of the other threads but I am still stuck.
One suggestion was to download Samba and winbind, which I did, but I cannot find winbind to follow that option. How do I get to it? The next step was to change a code line, how to I get to the edit part of it?
I also tried to follow another option: Places -> Connect to Server -> Server Type: Windows share, For server, I tried to enter the name of the Gateway computer and the IP address, both were not recognized.
Help is most appreciated.

---

### Post by tarps87 on 2009-04-06
I'm not sure exactly what you have tried so we'll start from the beginning.
First can the computers talk to each other:
```
ping -c 3 *ip_address_of_gateway*
```
You should get a reply.
No check if samba works.
```
smbtree
```
If you share has a password on you will need to enter it.

Can you post the output from these to commands and then we will go from there

---

### Post by superprash2003 on 2009-04-06
try accessing via ip address instead of hostnames.. check to see if any firewall is disabling access

---

### Post by billgoldberg on 2009-04-06
Install Samba, lots of guides on setting it up.

---

### Post by MarcyOne on 2009-04-06
> **billgoldberg said:**
> Install Samba, lots of guides on setting it up.

follow the instruction in there. it will tell you what to do next and its compatibility.

---

### Post by hzrunner on 2009-04-06
I pinged on my Ubuntu computer and got a reply. When I entered smbtree it asked for the password (the Ubuntu one, I guess), but that didn't lead anywhere. I have Samba installed, but couldn't try out the instructions that billgoldberg has listed (it took a while to find the one I seem to need. Need to grab some sleep now.

---

### Post by lisati on 2009-04-06
> **billgoldberg said:**
> Install Samba, lots of guides on setting it up.

Here's the one I used: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by tarps87 on 2009-04-07
> **hzrunner said:**
> I pinged on my Ubuntu computer and got a reply. When I entered smbtree it asked for the password (the Ubuntu one, I guess), but that didn't lead anywhere. I have Samba installed, but couldn't try out the instructions that billgoldberg has listed (it took a while to find the one I seem to need. Need to grab some sleep now.

This is the password of you windows share, if you don't have one then just hit enter

---

### Post by superprash2003 on 2009-04-07
you dont need to install samba if you want to connect to windows shares

---

