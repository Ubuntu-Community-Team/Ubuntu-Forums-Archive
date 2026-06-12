---
title: "Ubuntu 20.04 - Unable to negotiate ... no matching key exchange method found"
date: 2020-04-24
forum: Networking &amp; Wireless
---

### Post by renecek on 2020-04-24
hey guys, yesterday installed new ubuntu 20.04 into empty SSD. Works fine, just have a problems with connecting to ssh (servers, switches).
Unable to negotiate with xxx.xxx.xxx.xxx port 22: no matching key exchange method found. Their offer: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1


already added this in ~/.ssh/config
Host abcdef
HostName xxx.xxx.xxx.xxx
User myusername
KexAlgorithms diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1


it works fine now. But is there any way to connect to ssh without using ~/.ssh/config?

Tried to add it into /etc/ssh/ssh_config - ciphers, didn't help it.
We have about 300 switches, don't want to add every switch into ~/.ssh/config.
ssh worked fine with ubuntu 18.04

Thank you for any help.

---

### Post by renecek on 2020-04-27
fixed by me

---

### Post by c4f4s0g0 on 2020-04-27
> **renecek said:**
> fixed by me

I am having the same issue. Can you share how did you solve it?

---

### Post by mucm on 2020-08-03
I had this problem too after upgrading to Ubunte 20.04 and trying to ssh to my dd-wrt and openwrt routers.

There is no command line flag for this, but, as per the man page,
-o option
             Can be used to give options in the format used in the configura&#8208;
             tion file.  This is useful for specifying options for which there
             is no separate command-line flag.
so...

ssh -o "KexAlgorithms diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1" user@host

...worked for me.

---

### Post by cjrnz on 2021-01-11
Since 20.04 you can configure non standard client options by creating a file in [FONT=trebuchet ms]/etc/ssh/ssh_config.d/[/FONT]
A quick permanent fix might be;
[FONT=trebuchet ms]echo "KexAlgorithms diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1" >>/etc/ssh/ssh_config.d/weak.conf[/FONT]

---

### Post by cloud81 on 2021-03-02
> **cjrnz said:**
> Since 20.04 you can configure non standard client options by creating a file in [FONT=trebuchet ms]/etc/ssh/ssh_config.d/[/FONT]
A quick permanent fix might be;
[FONT=trebuchet ms]echo "KexAlgorithms diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1" >>/etc/ssh/ssh_config.d/weak.conf[/FONT]

thanks!

---

