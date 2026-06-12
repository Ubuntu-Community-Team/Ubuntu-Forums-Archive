---
title: "Edgy Wireless help"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by sdmike on 2006-12-28
Ok I have a compaq presario v2000 laptop. When I would install Dapper everything would work %100 and I never had to use ndiswrapper like on my old gateway.

So how come when I installed Edgy my wireless doesn't work. eth1 is my wireless but it is not shown here, Here's my ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:16:36:2C:CD:96  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2c:cd96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:283437 (276.7 KiB)  TX bytes:51818 (50.6 KiB)
          Interrupt:217 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

So what is the dealio here?

---

### Post by c.dric on 2006-12-28
which wireless card do you have in your laptop ?

---

### Post by sdmike on 2006-12-28
I believe it's a Brodcom which is integrated into to it. I remember when I used kubuntu I used a brodcom driver bundle with ndiswrapper that installed everything. But I can't find it.

---

### Post by c.dric on 2006-12-28
could you do 

lspci 

to find out the exact model you're using ?

---

### Post by sdmike on 2007-01-02
I'm using Broadcom 4318

---

### Post by sdmike on 2007-01-02
Ok so I found the combo of ndiswrapper and the driver I used before on kubuntu which can be found here:
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

Ok so when I go the directory were the file is stored and type, "sudo ./ndiswrapper_setup"

The terminal tells me command not found but I always use that command (./) when I compile my code.

So what am I missing here.

---

### Post by TCrush on 2007-01-02
Hmm... the command works for me... it should be correct...Or maybe you can change to superuser first then run the script (Note: I'm a noob, I copied from somewhere):
  sudo -s -H
  <Move to directory where the file is>
  ./ndiswrapper_setup
  exit


I am also trying to get my WLAN to work "normally" on my Compaq v2000... The method you are trying did not work for me... tried with the fwcutter method on a upgraded kernel, it works now, but the performance sux... I can only connect only when I am near to my router although there is signal when using wifi-radar...

Did you mentioned that Dapper works 100%? If so, I think I would go for that... Pls confirm, thanks.

---

### Post by sdmike on 2007-01-03
Dapper works %100 without using ndiswrapper.

---

### Post by sdmike on 2007-01-03
this is what I get:

jack@desktop:~$ sudo -s -H
Password:
root@desktop:/home/jack# cd /home/jack/Desktop/bcm4318.all.tar.gz_FILES
[email]root@desktop:/home/jack/Desktop/bcm4318.all.tar.gz[/email]_FILES# ./ndiswrapper_setup
bash: ./ndiswrapper_setup: Permission denied

---

### Post by TCrush on 2007-01-03
From a noob's point of view, maybe you should check the permissions of the file?
  ls -l

If it's a permission problem or what... (maybe you are not allowed to execute the file or what... ), you can use chmod to change the permissions, as in:
  sudo chmod 777 ndiswrapper_setup

Hope this helps!

---

### Post by sdmike on 2007-01-03
that did not work either.

---

### Post by sdmike on 2007-01-03
I'm still not understanding why it just didn't work in the first place with Edgy because it worked automatically with Dapper without having to use ndiswrapper. Is there someone file I'm missing here?

---

### Post by sdmike on 2007-01-03
Ok New problem I can see text but I can't type in the boxes? 

Just when I think I'm almost there. lol

---

### Post by sdmike on 2007-01-03
I couldn't delete this comment so yeah

---

### Post by sdmike on 2007-01-04
I fallowed the tutorial here and everything worked in the end.

[http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)

---

