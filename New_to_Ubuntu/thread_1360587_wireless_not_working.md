---
title: "wireless not working"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-21
my wireless connection is not working ... it's 'disabled' when i select 'manage connections' in order to try to create a new wireless connection.

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9d:c0:88
          inet addr:172.22.36.195  Bcast:172.22.39.255  Mask:255.255.252.0
          inet6 addr: fe80::21f:29ff:fe9d:c088/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:31789895 (31.7 MB)  TX bytes:6317372 (6.3 MB)
          Memory:e4600000-e4620000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

any ideas?

---

### Post by jb1299 on 2009-12-21
What wireless card do you have? Do this from terminal
```
lspci
``` to find out

---

### Post by muteXe on 2009-12-21
Do it as root.

---

### Post by rkakkar on 2009-12-21
> **jb1299 said:**
> What wireless card do you have? Do this from terminal
```
lspci
``` to find out

```

$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


```

---

### Post by Extract_Here on 2009-12-21
> **rkakkar said:**
> my wireless connection is not working ... it's 'disabled' when i select 'manage connections' in order to try to create a new wireless connection.

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9d:c0:88
          inet addr:172.22.36.195  Bcast:172.22.39.255  Mask:255.255.252.0
          inet6 addr: fe80::21f:29ff:fe9d:c088/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:31789895 (31.7 MB)  TX bytes:6317372 (6.3 MB)
          Memory:e4600000-e4620000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)

``````

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```any ideas?

[FONT=Lucida Sans Unicode][SIZE=4]I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.

-may the source be with you[/SIZE][/FONT]  
 		                   		  		  		 		 			[FONT=Lucida Sans Unicode][SIZE=4] 				__________________[/SIZE][/FONT]

---

### Post by bkratz on 2009-12-21
> **rkakkar said:**
> ```

$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


```


Before you try the ndiswrapper route please see post two of this thread


[http://ubuntuforums.org/showthread.php?t=1358084](http://ubuntuforums.org/showthread.php?t=1358084)

---

### Post by rkakkar on 2009-12-21
> **bkratz said:**
> Before you try the ndiswrapper route please see post two of this thread


[http://ubuntuforums.org/showthread.php?t=1358084](http://ubuntuforums.org/showthread.php?t=1358084)

i tried it but it's not allowing to activate the damn driver! :P

---

### Post by bkratz on 2009-12-21
> **rkakkar said:**
> i tried it but it's not allowing to activate the damn driver! :P



Do you have a wired connection?  I believe you have to have one to activate.



Also, if you have a Dell Mini you might want to see the comments here (found with Google)

[http://blog.garethj.com/2009/10/wireless-on-a-dell-mini-10v-in-ubuntu-9-10/](http://blog.garethj.com/2009/10/wireless-on-a-dell-mini-10v-in-ubuntu-9-10/)

---

### Post by rkakkar on 2009-12-22
> **bkratz said:**
> Do you have a wired connection?  I believe you have to have one to activate.



Also, if you have a Dell Mini you might want to see the comments here (found with Google)

[http://blog.garethj.com/2009/10/wireless-on-a-dell-mini-10v-in-ubuntu-9-10/](http://blog.garethj.com/2009/10/wireless-on-a-dell-mini-10v-in-ubuntu-9-10/)

still doesn't do anything when i click activate :(

is there any other way to activate it?

i have a hp compaq 6720s

---

