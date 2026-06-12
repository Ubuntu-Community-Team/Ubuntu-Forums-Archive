---
title: "Computers in Network"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2011-02-11
I am using Ubuntu 10.10 and how do i see the computers connected to a network even if there are computers running different OS's...

---

### Post by sydbat on 2011-02-11
> **viditgoyal3009 said:**
> I am using Ubuntu 10.10 and how do i see the computers connected to a network even if there are computers running different OS's...Have you tried Places > Network?

---

### Post by viditgoyal3009 on 2011-02-11
> **sydbat said:**
> Have you tried Places > Network?
yeah but it didn't work.. It shows "Windows Network" but when i double click it, it starts giving error messages...

---

### Post by aeiah on 2011-02-11
are you wanting just to scan the local network for connected computers? if so this will give you a list of IP addresses of computers in your subnet:
```


sudo nmap -sP -oG 192.168.1.0/24
```

change 192.168.1.0 according to what ip range you use.


if you want to see shared files and folders and all that stuff then the likely cause for 'places' hanging is because of a workgroup name mismatch i think, although ive never done that sorta thing with computers running none-linux operating systems

---

### Post by viditgoyal3009 on 2011-02-12
> **aeiah said:**
> are you wanting just to scan the local network for connected computers? if so this will give you a list of IP addresses of computers in your subnet:
```


sudo nmap -sP -oG 192.168.1.0/24
```

change 192.168.1.0 according to what ip range you use.


if you want to see shared files and folders and all that stuff then the likely cause for 'places' hanging is because of a workgroup name mismatch i think, although ive never done that sorta thing with computers running none-linux operating systems
what does /24 stand for here???

---

### Post by lisati on 2011-02-12
> **viditgoyal3009 said:**
> what does /24 stand for here???
An approximate translation is "use the first 24 (binary) digits of the IP address".
Have a look here for a slightly longer explanation: [http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)

---

### Post by Cracklepop on 2011-02-12
> **viditgoyal3009 said:**
> yeah but it didn't work.. It shows &quot;Windows Network&quot; but when i double click it, it starts giving error messages...

That happens to me too.  I saw someone say somewhere it's a known bug.  To get around it find the IP address of the computer you want to see, then go to Places > Connect to Server, set Service Type to Windows Share, and type in the IP address.

 Remember to Bookmark it in Nautilus to add it to Places for next time.

---

### Post by viditgoyal3009 on 2011-02-12
> **Cracklepop said:**
> That happens to me too.  I saw someone say somewhere it's a known bug.  To get around it find the IP address of the computer you want to see, then go to Places > Connect to Server, set Service Type to Windows Share, and type in the IP address.

 Remember to Bookmark it in Nautilus to add it to Places for next time.
yeah.. but my question was how to see which all machines are connected...

---

### Post by Morbius1 on 2011-02-12
> **aeiah said:**
> are you wanting just to scan the local network for connected computers? if so this will give you a list of IP addresses of computers in your subnet:
```


sudo nmap -sP -oG 192.168.1.0/24
```change 192.168.1.0 according to what ip range you use.


if you want to see shared files and folders and all that stuff then the likely cause for 'places' hanging is because of a workgroup name mismatch i think, although ive never done that sorta thing with computers running none-linux operating systems
Sorry for the interruption but shouldn't that be:
```
sudo nmap -sP -oG- 192.168.1.0/24
```

---

