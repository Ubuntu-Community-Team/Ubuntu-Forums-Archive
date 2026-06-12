---
title: "ftp: connect: Connection timed out"
date: 2018-09-18
forum: Networking &amp; Wireless
---

### Post by gigamike2 on 2018-09-18
Guys,

Im using ubuntu 16.


I have a VPC in Ireland region then on my EC2 instance under London region i can connect via FTP. But when ftp put or ls directory its always "ftp: connect: Connection timed out"


Im sure i setup my Ireland EC2 security groups allowing FTP port i.e.
20 - 21 0.0.0.0/0
1024 - 1048 0.0.0.0/0


sudo vi /etc/vsftpd.conf
pasv_enable=YES
pasv_min_port=1024
pasv_max_port=1048
port_enable=YES
write_enable=YES


Quite stuck already although other EC2 instance under my VPC in Ireland can connect and ftp put.


Hoping for your response

---

### Post by QIII on 2018-09-18
Hello!

Which release of Ubuntu 16?  16.04?  16.10?

---

### Post by gigamike2 on 2018-09-19
Hi,

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.5 LTS
Release:	16.04
Codename:	xenial

thanks

---

