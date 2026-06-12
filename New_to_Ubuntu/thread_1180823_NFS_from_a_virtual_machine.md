---
title: "NFS from a virtual machine"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-06-07
Question:

I have a synology disk station set up in my network at address 192.168.1.8

Furthermore I've configured NFS to have complete access to the synology disk station via NFS.

The problem I have is that I also (involuntary have to) work under Vista (Business Edition).
Now the problem is Business Edition can't run the Windows Services for UNIX (that would need Ultimate edition...), which is the only way to get a free working NFS client for Vista.

Now I've set up a Ubuntu Box in a Virtual Machine on Vista (networking works fine, I write this form the VM Ubuntu), which should make me capable of using Ubuntu's NFS to access the synology disk station without having to shut down windows.

My /etc/exports
```

/volume1/web    192.168.1.*(rw,no_wdelay,root_squash,insecure_locks,anonuid=1024,anongid=100)
/               192.168.1.*(rw,no_wdelay,insecure_locks,anonuid=0,anongid=100)

```I added another line, for experimentation:
```

/volume1        192.168.1.*(rw,no_wdelay,insecure_locks,anonuid=0,anongid=100)

```and restarted the nfs daemon.

Now the problem is no mater what IP i set into the experimentation line, I always get this answer:
```

root@ST-LAPTOP:~# mount 192.168.1.8:/volume1 /mnt/synology
mount.nfs: access denied by server while mounting 192.168.1.8:/volume1

```The mount directive however works fine under my debian system, which is NOT virtualized.

I set up a PHP script on the diskstation which gives me the IP the synology disk station gets when I access a PHP site on the diskstation via Ubuntu on the VM in Vista,

The address I got is 192.168.1.2

THE php script:

index.php
[php]
<HTML>
<HEAD>
<TITLE>The Vir(t)ual IP</TITLE>
</HEAD>
<BODy>

<? echo getenv('REMOTE_ADDR'); ?>

</BODY>

</HTML>
[/php]
The IP config from windows:
> 
Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation. Alle Rechte vorbehalten.

Windows-IP-Konfiguration


Ethernet-Adapter VirtualBox Host-Only Network:

   Verbindungsspezifisches DNS-Suffix:
   Verbindungslokale IPv6-Adresse  . : fe80::4523:934c:b228:5535%19
   IPv4-Adresse  . . . . . . . . . . : 192.168.56.1
   Subnetzmaske  . . . . . . . . . . : 255.255.255.0
   Standardgateway . . . . . . . . . :

Drahtlos-LAN-Adapter Drahtlosnetzwerkverbindung:

   Verbindungsspezifisches DNS-Suffix:
   Verbindungslokale IPv6-Adresse  . : fe80::2898:a93b:c885:42ad%13
   IPv4-Adresse  . . . . . . . . . . : 192.168.1.2
   Subnetzmaske  . . . . . . . . . . : 255.255.255.0
   Standardgateway . . . . . . . . . : 192.168.1.1

The ifconfig output on the virtual box:
> 
root@ST-LAPTOP:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:58:f5:15  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe58:f515/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27627759 (27.6 MB)  TX bytes:1410444 (1.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7492 (7.4 KB)  TX bytes:7492 (7.4 KB)

I also tried setting 10.*.*.* and *.*.*.* as the IP in the experimental config line, but it never worked...


Anybody can tell me what is wrong here?
Could it have anything to do with username/password?

---

### Post by WitchCraft on 2009-06-08
Problem solved.

You need to tell VirtualBox to forward all ports, that is to say put the network adapter in VirtualBox into bridge mode (and you need to choose the right adapter, the one of the local machine, not the one created by VirtualBox - logical, but since it is a GUI, you can you can easily overlook that config dropdown, and sure, by the very sane VirtualBox defaults, that means it chooses the /dev/NULL adapter...) .

---

