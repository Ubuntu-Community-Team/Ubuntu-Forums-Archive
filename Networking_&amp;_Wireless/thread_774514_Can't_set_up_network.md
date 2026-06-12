---
title: "Can't set up network"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by AdrianStrays on 2008-04-29
I'm attempting to share files between my Vista Desktop and my Ubuntu Studio laptop. I installed Samba, set up my user, entered in the workgroup, but the Network folder STILL doesn't register my desktop, nor does my desktop register my laptop.

I've followed different guides, talked on the IRC, and just messed around with it myself.  Part of my problem maybe that I'm running Hardy, and all the guides appear to be written for Gusty. (Specifically, on the wiki it talks about sharing with windows under Administration -> Network -> General Tab, but the windows part isn't there.  It also talks about setting it up under shared folders, but that option isn't on the menu either)



I'd appreciate some help.

---

### Post by AdrianStrays on 2008-04-29
Bump

---

### Post by jerome1232 on 2008-04-29
Yeah it's been moved in Hardy. Just navigate to the folder you would like to share and right click it, then click sharing, you will be presented with a simple to use sharing dialog, it may prompt you to install sharing services, go ahead and do so.

Now i had a problem that told me I didn't have permssions to create a share, make sure you are in the samba shares group (I was already, i think the installer took care of it) but I had to log out/in to make the group change take affect, after that it created the share.

This works except for one thing, the only way I can connect to the share on the windows computer is start-run - \\ip.address.of.ubuntu.machine
I'm not in the same workgroup as my win computer and can't figure out how to make myself be in the same workgroup...
found it, it's not exclusive to 7.04 works in 8.04
[http://www.ubuntux.org/change-wrokgroup-in-ubuntu-7-04](http://www.ubuntux.org/change-wrokgroup-in-ubuntu-7-04)

---

### Post by AdrianStrays on 2008-04-29
I'm at work now, so I can't say much about your help thus far. I think I installed the services, although I didn't have the proper information it was asking at the time.

My comp automatically gets its IP Address.  Actually, if I recall correctly there is an "internal" address, right? How can I go about figuring out what mine is?

I can offer you a little something though, specifically to chaning your workgroup.  Just gedit the smb.conf file, it gives you a spot to enter in your workgroup.  I think its located in etc/smamba/smb.conf

---

### Post by jerome1232 on 2008-04-29
as far as the ubuntu machine goes (open a terminal)
you're looking for inet addy
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:7b:7f:9b  
          inet6 addr: fe80::250:8dff:fe7b:7f9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114595 (111.9 KB)  TX bytes:468 (468.0 B)
          Interrupt:16 Base address:0xdd00 

eth1      Link encap:Ethernet  HWaddr 00:11:50:b4:2c:2d  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:feb4:2c2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136620 errors:3501 dropped:123 overruns:0 frame:3393
          TX packets:96397 errors:141 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:194868782 (185.8 MB)  TX bytes:8262383 (7.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:364610 (356.0 KB)  TX bytes:364610 (356.0 KB)

```
gui way you can right click network manager (upper right) and click connection information

vista start-start search (windows key+r) works too
cmd-ipconfig
your looking for ipv4 addy
also see if you can (windows key+r) and type the \\192.168.1.4 (for me)
see if that opens your share :D good luck

---

### Post by AdrianStrays on 2008-04-30
Nope.

---

### Post by AdrianStrays on 2008-04-30
bump

---

### Post by AdrianStrays on 2008-04-30
Bump

---

### Post by AdrianStrays on 2008-04-30
bump

---

### Post by AdrianStrays on 2008-05-03
bump

---

