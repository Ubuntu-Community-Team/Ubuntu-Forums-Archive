---
title: "can't Analysis of Internal IP address"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by millercn on 2008-06-12
I used Ubuntu 8.04. I can browse website by firefox .but I can't access my internal website or ftpserver ,the firefox tell me  can't analysis this website to ip address . I can get the right ipaddress when I use "nslookup" . 

My net interface is "DHCP" ,and get the internal DNS. 

who can tell me why is this ?

---

### Post by superprash2003 on 2008-06-12
does it work via ipaddress? when you type [http://127.0.0.1](http://127.0.0.1) or [ftp://127.0.0.1](ftp://127.0.0.1)

---

### Post by millercn on 2008-06-12
> **superprash2003 said:**
> does it work via ipaddress? when you type [http://127.0.0.1](http://127.0.0.1) or [ftp://127.0.0.1](ftp://127.0.0.1)
yes,firefox can access web/ftp by ip address .

e.g:
One Site URL :[www.my.local](www.my.local) ,ip:192.168.0.1
If I type [www.my.local](www.my.local) in firefox ,then display "can't find this site";
If I type [http://192.168.0.1](http://192.168.0.1) in firefox ,then display webpage.

---

### Post by cpetercarter on 2008-06-12
What happens if you type [http://localhost](http://localhost) ?

---

### Post by millercn on 2008-06-12
> **cpetercarter said:**
> What happens if you type [http://localhost](http://localhost) ?
I can't test [http://local](http://local) . but I have two computers have this "bug" ,One is Laptop,another is a Dell pc .

The ubuntus pc is't in my beside . I will try it tomorrow.

---

### Post by millercn on 2008-06-12
> **cpetercarter said:**
> What happens if you type [http://localhost](http://localhost) ?
Can't display anything .I have't webservice .

---

### Post by millercn on 2008-06-12
I can't ping ,but  I can nslookup .

Look attachemnts.

---

