---
title: "ipw3945 not working"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by dabd on 2007-03-04
Hi,

My wireless is not working even though I upgraded my Xubuntu to Feisty.
I am using kernel 2.6.20-9-386 and I installed the linux-restricted-modules-generic too.
Shouldn't this work out of the box?
This is a brand new fujitsu amilo si 1520 laptop.  I never tested the wireless in Windows, because I immediately wiped out Windows and installed Xubuntu :-)

Here is my lspci output:
```

dabd@qubit-fujitsu:~$ lspci|grep 3945
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

also lsmod:
```

dabd@qubit-fujitsu:~$ lsmod|grep 3945
ipw3945               118304  0 
ieee80211              33480  1 ipw3945
```

and iwconfig:
```

dabd@qubit-fujitsu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```


Some help would be appreciated.
Thanks.

---

### Post by dphoebus on 2007-03-05
Check this article out... [http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754]("http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754")

hope this helps....

---

### Post by dabd on 2007-03-07
solved. thanks

---

### Post by topgi on 2007-03-10
I have the same problem on my ACER 3262. Please can you tell how you made it work ?

Thanks

---

### Post by dabd on 2007-03-14
My laptop had the wireless card turned off all the time.  It was a matter of pressing the button to turn it on!

---

