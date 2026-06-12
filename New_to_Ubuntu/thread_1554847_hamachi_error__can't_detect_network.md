---
title: "hamachi error :: can't detect network"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by AlexenderReez on 2010-08-17
> crownclown@millionaire:~$ sudo modprobe tun
[sudo] password for crownclown: 
crownclown@millionaire:~$  sudo gedit /etc/modules
crownclown@millionaire:~$ ls /dev/net/tun
/dev/net/tun
crownclown@millionaire:~$ sudo mknod /dev/net/tun c 10 200
mknod: `/dev/net/tun': File exists
crownclown@millionaire:~$ sudo gpasswd -a user hamachi
gpasswd: user 'user' does not exist
crownclown@millionaire:~$ sudo gpasswd -a crownclown hamachi
Adding user crownclown to group hamachi
crownclown@millionaire:~$ sudo gpasswd -a root hamachi
Adding user root to group hamachi
crownclown@millionaire:~$ sudo chmod 760 /var/run/tuncfg.sock
crownclown@millionaire:~$ sudo chgrp hamachi /var/run/tuncfg.sock
crownclown@millionaire:~$ sudo apt-get install upx-ucl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
upx-ucl is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono-system-runtime2.0-cil libnunit2.4-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
crownclown@millionaire:~$ cd /usr/bin
crownclown@millionaire:/usr/bin$ 
crownclown@millionaire:/usr/bin$ sudo upx -d hamachi
                       Ultimate Packer for eXecutables
                          Copyright (C) 1996 - 2009
UPX 3.04        Markus Oberhumer, Laszlo Molnar & John Reiser   Sep 27th 2009

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
    830676 <-    331144   39.86%    linux/386    hamachi

Unpacked 1 file.
crownclown@millionaire:/usr/bin$ sudo hamachi-init -c /etc/hamachi
Initializing Hamachi configuration (/etc/hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making /etc/hamachi directory .. ok
  saving /etc/hamachi/client.pub .. ok
  saving /etc/hamachi/client.pri .. ok
  saving /etc/hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.

crownclown@millionaire:/usr/bin$ sudo hamachi -c /etc/hamachi start
Starting Hamachi hamachi-lnx-0.9.9.9-20 .. ok
crownclown@millionaire:/usr/bin$ sudo hamachi -c /etc/hamachi set-nick radzi
Setting nickname .. ok
[B]crownclown@millionaire:/usr/bin$ sudo hamachi -c /etc/hamachi login
Logging in ... failed[/B]
crownclown@millionaire:/usr/bin$ hamachi-init
hamachi-init: path /home/crownclown/.hamachi already exists (use -f to force using it)
crownclown@millionaire:/usr/bin$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:60:b0:ce:de  
          inet addr:165.0.2.2  Bcast:165.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:feb0:cede/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:341792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58161755 (58.1 MB)  TX bytes:2143918 (2.1 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:8a:f3:93:23  
          inet6 addr: fe80::202:8aff:fef3:9323/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:236 dropped:0 overruns:0 frame:236
          TX packets:6 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:396 (396.0 B)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

[B]crownclown@millionaire:/usr/bin$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
165.0.2.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         165.0.2.254     0.0.0.0         UG    0      0        0 eth0[/B]


please help :)

---

