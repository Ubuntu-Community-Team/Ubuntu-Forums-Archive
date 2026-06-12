---
title: "Using SADMS on Ubuntu. Need Help"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by iano.it on 2007-11-07
Hello,
         First let me introduce myself.  Im Ian, pleased to meet you all.

I have installed Ubuntu server 7.04 .  My goal is to use it as a network storage point and in time replace my terastation.  Im a fairly new to linux and its ways so any help would be great.
I need to join the Ubuntu server onto my windows server 2003 domain.  The recomended program to use was SADMS.  Anybody on this forum know and understand this program or anybody with experience in its use.
Basically I can configure it up to the point where it needs installed I enter the information correctly and I have reset my password on active directory once like it asks.  However when i click install I get following error messages.

could not acquire kerberos
+warning
Kerberos requires administrators password
to have been reset once since domain install
in order to add DES encryption keys to user
account which only has a rc4 key when
initially created

returned error code 6

Thnaks in advance for any replies.

---

### Post by iano.it on 2007-11-08
I will stick to my own rules and only bump once.  Then if still nobody replies I shall go elsewhere.
Peace.

---

### Post by ferrymulyanto on 2007-11-22
iam also get error message like that, my suggest is, you must configure manually file krb5.conf, tu suite your configuration

---

