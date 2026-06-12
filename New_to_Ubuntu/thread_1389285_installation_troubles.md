---
title: "installation troubles"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-01-24
sometimes back i downloaded the deb packages for limewire.but i am not able to install and it show a error that "only one software management tool is allowed to run" help me out 
thank you

---

### Post by halitech on 2010-01-24
you cannot run Synaptic, apt-get and any other package manager at the same time. How were you trying to install it?

---

### Post by 1991sudarshan on 2010-01-24
but i was shown that error but no other installation program was running then!

---

### Post by halitech on 2010-01-24
so how were you trying to install it?

---

### Post by howefield on 2010-01-24
> **1991sudarshan said:**
> but i was shown that error but no other installation program was running then!

Update manager maybe ?

Try rebooting and installing.

There is a linux equivalent to Limewire called Frostwire.

---

### Post by 1991sudarshan on 2010-01-24
i downloaded the .deb installation file for limewire. i opened the .deb package after some times it show that error!!!

like wise i face the same problem in the update manger also 
it is again showing an error there also!!!!

---

### Post by 1991sudarshan on 2010-01-24
sreenivassudarshan@ubuntu:~$ sudo apt-get install vlc-nox
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by mcduck on 2010-01-24
> **1991sudarshan said:**
> sreenivassudarshan@ubuntu:~$ sudo apt-get install vlc-nox
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

just do what the error message tells you to do:
```

sudo dpkg --configure -a
```

---

### Post by 1991sudarshan on 2010-01-24
got this one in the terminal 



sreenivassudarshan@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for sreenivassudarshan: 
Setting up java-common (0.30ubuntu5) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

---

### Post by 1991sudarshan on 2010-01-24
after that what should i do?

---

### Post by mcduck on 2010-01-24
no errors there, seems to be working just fine. :)

---

### Post by 1991sudarshan on 2010-01-24
but still i am getting that error message!!!

---

### Post by 1991sudarshan on 2010-01-24
now it is working properly i think so!!!

---

### Post by 1991sudarshan on 2010-01-24
another error 
it show that failed to instal all dependencies

---

### Post by halitech on 2010-01-24
why not use Frostwire instead of limewire?
```
sudo apt-get install frostwire
```should do it

---

### Post by mikechant on 2010-01-25
> another error 
it show that failed to instal all dependencies

Can you post the full message? Does it list the dependencies?

---

### Post by Muskegman on 2010-01-25
i agree, install FrostWire its almost the same as LimeWire

---

