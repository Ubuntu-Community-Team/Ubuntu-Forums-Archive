---
title: "please help!"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by acerpc on 2009-03-14
I have installed kubuntu
the internet is not working
on opensuse I disabled ipv6 and uses ifup instead of network manager and it worked
I dont know how to do it on kubuntu
on opensuse i did it from yast , without using terminal
I hate terminal, really I hate it
I searched alot on the forum but doing something I dont really understand just make a big mess
please help

---

### Post by carml on 2009-03-14
To set up a particular IP,DNS,etc go on System->Administration->Network.
All without using the terminal :).

---

### Post by acerpc on 2009-03-14
> **carml said:**
> To set up a particular IP,DNS,etc go on System->Administration->Network.
All without using the terminal :).

I tried that befor
as I said it is about disabling ipv6 and using ifup instead of network manager
but how to do it
I tried what they said on many posts but it always fails

---

### Post by kukibird1 on 2009-03-14
> **acerpc said:**
> I tried that befor
as I said it is about disabling ipv6 and using ifup instead of network manager
but how to do it
I tried what they said on many posts but it always fails

To disable ipv6  in a terminal or run dialog  type the following: 
 
kdesu kate /etc/modprobe.d/blacklist  

add blacklist ipv6 to the end of the file .

---

