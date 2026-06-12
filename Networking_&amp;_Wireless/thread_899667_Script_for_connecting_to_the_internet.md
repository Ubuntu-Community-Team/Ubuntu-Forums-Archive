---
title: "Script for connecting to the internet"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by m2nmx on 2008-08-24
My internet provider has set its network so that all users must use a "Lan Client" to connect to the internet. For windows this is a small .exe where you enter username, password and gateway and then click connect and you are logged in. For Linux my provider gives this script 'lancl.conf':
```
#server_port=7654
#server_addr=127.0.0.1
#bind_addr=
#key_file=/usr/local/etc/client_key.bin
# This is default
#debug=0
user=user@providername
pass=password
# maxresend=0 means forever
maxresend=100
# quit_on_auth_fail=0
# quit_on_bye=0
# pid_file=/var/run/lancl.pid

```
There are also 2 other files 'lancl-static-Linux2.4' and 'lancl'. After configuring my network card in ubuntu with my real IP, default gateway and DNS servers of my provider I click on 'lancl' and I have access to the internet. 

My questions are: is there any other way of configuring ubuntu to connect to the internet without using this script? Can this kind of connection script be optimized/changed for better connection? 

P.S. In SuSE I have managed to avoid this client by setting up PPoE connection. Below are the 3 files my provider gives the linux users.

---

### Post by m2nmx on 2008-08-26
Any thoughts?

---

### Post by m2nmx on 2008-09-05
Small update to the question:

How to set up ubuntu server using this script?

---

