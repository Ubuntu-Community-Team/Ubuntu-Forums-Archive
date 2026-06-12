---
title: "Can Ping, Can't Load!"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Devine on 2008-04-10
I just got a brand spanking new - 6 years old - IBM ThinkPad T32 (1.0Ghz, 256MB RAM, Ethernet NIC), removed Win2000 and loaded XUbuntu. I have found that I can ping everything but I cannot actually do any data transfer. 
I have checked the kernel module (e100 - this is popular and still supported I think) was working, and I have tried other kernel modules (eepro100) and I have done lspci, modprobe, lsmod, ifup and ifdown many times along with checking the ifconfig...
I also did try removing the physical Ethernet module twice, which did nothing.

The addresses I have pinged are:
#192.168.0.1 (Ethernet Router)
#-The IP for google.com (no DNS Issues)
#google.com 

...Yes I have been assigned an IP by DHCP - I have tried two different routers.

All tests return a ping however I cannot load web pages or use repositories.

I will now prepare some readouts for the inevitable requests...

---

### Post by superprash2003 on 2008-04-10
probably a DNS problem,
go to the terminal and type 

sudo gedit /etc/dhcp3/dhclient.conf

then add the following line to it

prepend domain-name-servers 208.67.222.222,208.67.220.220;

save the file and close.this should work

---

### Post by Devine on 2008-04-10
Thanks, I will try that in a minute... I'm being flooded with tasks just now.

---

### Post by Devine on 2008-04-10
Ok, it didn't make any difference.

The line was already in the conf, so I changed to your numbers to no avail.

---

### Post by Devine on 2008-04-10
Hang on, I just tried going to the router config page again (after changing back to my origional .conf file) and now I can view it!

---

### Post by Devine on 2008-04-10
It appears that I can now access the router - but not the internet.

This seems a much easier problem to solve... Though I'm not sure how.

---

### Post by Devine on 2008-04-10
I have found an error message when it fails - 
eth0: no IPV6 routers present.

...Yes there is IPV6 routers present, my other computer has no trouble... I am starting to think that replacing my ethernet module (hardware) might be the only answer.

Too bad i can barely afford to eat at the moment.

---

### Post by Devine on 2008-04-11
Ok, for future reference for IBM ThinkPad T23 owners - ETHERNET DOES NOT WORK ON 7.10!

Apparently it worked on 7.04, but I guess e100 and eepro100 are broken in the newer kernels. Explains why I get exact same issue in OpenSUSE 10.3

---

