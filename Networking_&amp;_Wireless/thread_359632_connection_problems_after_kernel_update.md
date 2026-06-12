---
title: "connection problems after kernel update"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Hollunder on 2007-02-12
Hi,
my internet connection doesn't work anymore after the latest kernel update.
The script that establishes the connection doesn't work with the new kernel.

It's a DSL connection using an Alcatel Speedtouch 330 usb modem and pppoa afaik

The script that does works with the old kernel but doesn't with the new:
```

plugin pppoatm.so 
noipdefault 
defaultroute 
user 'user@provider' 
noauth 
updetach 
usepeerdns 
8.48 

### You may need to uncomment these 
### options to connect with some ISP's. 
### They disable compression. 

#noaccomp 
#nobsdcomp 
#nodeflate 
#nopcomp 
#noccp 
#novj 

### If the firmware loads and pppd won't 
### connect uncomment this option to make 
### pppd be more verbose in the system log 

debug 

### For more details (and more options) 
### Read man pppd

```

Here's what happens when I call the script with the new kernel:
```

user@computer:~$ sudo pppd call speedtch 
Password: 
Plugin pppoatm.so loaded. 
connect(8.48): No such device 

```

It would be great if someone could help me,

Hollunder

---

### Post by Hollunder on 2007-02-12
Problem solved, the firmware for the modem had to be copied to the firmware directory of the new kernel.

---

