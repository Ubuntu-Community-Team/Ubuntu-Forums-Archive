---
title: "Internet not running properly in Wired Connection Ubuntu 16.04"
date: 2017-09-17
forum: Networking &amp; Wireless
---

### Post by rohit129 on 2017-09-17
Hello everyone I am using ubuntu 16.04, When connecting to internet Wired Connection is proper but internet work for few seconds later after sometime internet work for sometime... I have checked internet connection is fine in wireless network.. as well as wired connection in windows is also working fine.. I think something because of " sudo apt-get update " might have updated ethernet driver.
 
The output of $ lshw -C network
attached to this post as "1.png"

Also attached the output of $uname -a 
as "2.png"

Need help !!file:///home/rohit/Downloads/1.png

---

### Post by praseodym on 2017-09-17
Please show the outputs from
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a
dmesg | grep r8
```

---

### Post by rohit129 on 2017-09-17
Thanks for kind support .... But shortly someone told me to forcefully release the ip from dhcp and then reacquire new ip 
 
Solution : 
By using   $ dhclient -v -r eth0
                 $ dhclient -v eth0
             
It worked !

But Thanks to you also for being there to help

---

