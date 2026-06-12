---
title: "bluetooth nightmare connection refused (111)"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by bbmak on 2007-07-08
Using Xubuntu 7.04

i keep getting the connection refused (111).  

here is the log
> bbmak@ubuntu:~$ sudo hidd --search
Searching ...
bbmak@ubuntu:~$ sudo hcitool scan
Scanning ...
        00:16:DB:1A:7F:CD       BBMak
bbmak@ubuntu:~$ sudo hcitool cc 00:16:DB:1A:7F:CD
bbmak@ubuntu:~$ sudo hidd --search 00:16:DB:1A:7F:CD
Searching ...
bbmak@ubuntu:~$ sudo hidd --connect 00:16:DB:1A:7F:CD
Can't connect: Connection refused (111)

The phone popups and asks me to enter the pin. I enter '1234,' the default key, but it is still saying 'connection refused (111).'

Does anyone how do i fix this?

---

