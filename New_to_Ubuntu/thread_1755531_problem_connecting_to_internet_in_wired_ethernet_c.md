---
title: "problem connecting to internet in wired ethernet connection"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by naved ..... on 2011-05-11
hi ..i m using ethernet to connect to internet in ubuntu 10.10
i have wired connection at my home .....i dont use any modem like phone to connect to internet .
its just 1 wire is plug into the ethernet socket and device type that i use to connect to internet in pppoe . which has my username and password which my isp has provided me ...
 now plz help me to connect to the internet 

check the below attachment for all the details of ipconfig /all

---

### Post by TheNerdAL on 2011-05-11
Try ```
sudo dhclient eth0
```

---

### Post by naved ..... on 2011-05-11
> **TheNerdAL said:**
> Try ```
sudo dhclient eth0
```
what this ll do u didnt mention dude.
lets see what it pulls out ?

---

### Post by TheNerdAL on 2011-05-11
You are either missing the auto eth0 line in your /etc/network/interfaces file, or you are trying to connect manually. Either way the line dhclient eth0 asks your dhcp server or router to give you a dynamically assigned IP address. Obviously you get one, and then can use the internet.

---

### Post by naved ..... on 2011-05-11
> **TheNerdAL said:**
> You are either missing the auto eth0 line in your /etc/network/interfaces file, or you are trying to connect manually. Either way the line dhclient eth0 asks your dhcp server or router to give you a dynamically assigned IP address. Obviously you get one, and then can use the internet.
so i just have to enter the dhcp server details and i can use internet ?

---

### Post by TheNerdAL on 2011-05-11
Did you try 
```
sudo dhclient eth0

```
yet?

---

### Post by dineshs on 2011-05-11
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by naved ..... on 2011-05-11
> **dineshs said:**
> [http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
following o/p occured after trying what u said look out

---

### Post by dineshs on 2011-05-12
> **naved ..... said:**
> following o/p occured after trying what u said look out
Click on the link  	
[http://ubuntuforums.org/showpost.php...50&postcount=2](http://ubuntuforums.org/showpost.php...50&postcount=2)

---

