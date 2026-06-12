---
title: "Networking Karmic and XP and Vista"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by WordConjurer on 2009-11-18
Hello,

I am completely new at this, and am quite unsure of what to do now. 

I am working on establishing a home network, and here is the set up:

XPPC=wired to 2wire router
LINLT=wired to 2wire router
VISLT=wireless connection to 2wire router

On both my XP and Linux machines, I can access shared files. Furthermore, I have installed LLTD on my XP machine--making my XP computer show up in my Vista Network map. However, I am unable to ping my XP computer from my Vista. I am also unable to access the XP machine from my Linux--because of a failure to mount--so I'm not sure what's going on.

On another note, I also believe I need to change the hostname of my linux machine--although I am unsure of how to go about doing that.

I can follow instructions, and post all output. Please help, I've been trying to do this for the last 5 days...My work and my school are my computers...

---

### Post by harfa on 2009-11-25
XP and vista use different default workgroups. XP uses MSHOME i think where as Vista uses WORKGROUP. try making all 3 machines part of the same workgroup is a good start.

---

### Post by ukripper on 2009-11-25
Have you got any firewall program running on XP machine?

what you get in routing table on XP machine/ go to cmd prompt and run ```
route PRINT
```

To change hostname on linux machine:
follwo this link [http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html](http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html)

---

### Post by WordConjurer on 2009-12-03
> **harfa said:**
> XP and vista use different default workgroups. XP uses MSHOME i think where as Vista uses WORKGROUP. try making all 3 machines part of the same workgroup is a good start.


Hello harfa, all computers share the same Workgroup name. Thank you.

---

### Post by WordConjurer on 2009-12-03
> **ukripper said:**
> Have you got any firewall program running on XP machine?

what you get in routing table on XP machine/ go to cmd prompt and run ```
route PRINT
```To change hostname on linux machine:
follwo this link [http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html](http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html)


On my XP machine, Webroot is my antivirus software, but I'm not sure if there is a firewall established. (I know...:confused:)

I am looking to properly configure my network, and would not be opposed to step-by-step instructions on how to at least create a network between my XP and Ubuntu laptop so that they can share the printer used by my XP.

---

### Post by WordConjurer on 2009-12-05
> **ukripper said:**
> Have you got any firewall program running on XP machine?

what you get in routing table on XP machine/ go to cmd prompt and run ```
route PRINT
```To change hostname on linux machine:
follwo this link [http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html](http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html)


My machine is properly named (a fresh install helps!), but I'm not sure what do do with route PRINT results to determine if a firewall is running.

My XP can ping Ubuntu, but Ubuntu cannot ping XP.

---

### Post by ukripper on 2009-12-07
> **WordConjurer said:**
> My machine is properly named (a fresh install helps!), but I'm not sure what do do with route PRINT results to determine if a firewall is running.

My XP can ping Ubuntu, but Ubuntu cannot ping XP.

From your ubuntu machine, can you ping your XP machine by its ip address and not by name and see if it still can't ping.

---

### Post by WordConjurer on 2010-01-25
route PRINT in cmd prompt returns the following output:


Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Valued Customer>route PRINT
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 08 74 37 ba 0a ...... Intel(R) PRO/1000 MT Network Connection - Packet
 Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    192.168.1.254    192.168.1.64       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      169.254.0.0      255.255.0.0     192.168.1.64    192.168.1.64       20
      192.168.1.0    255.255.255.0     192.168.1.64    192.168.1.64       20
     192.168.1.64  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.1.255  255.255.255.255     192.168.1.64    192.168.1.64       20
        224.0.0.0        240.0.0.0     192.168.1.64    192.168.1.64       20
  255.255.255.255  255.255.255.255     192.168.1.64    192.168.1.64       1
Default Gateway:     192.168.1.254
===========================================================================
Persistent Routes:
  None

---

