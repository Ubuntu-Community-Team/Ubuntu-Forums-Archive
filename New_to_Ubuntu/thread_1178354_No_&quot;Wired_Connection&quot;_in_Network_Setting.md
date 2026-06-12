---
title: "No &quot;Wired Connection&quot; in Network Settings"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by warjw on 2009-06-04
I have just installed Ubuntu on my Dell laptop.
I do not see the "Wired Connection.." in Network settings. Only "Point to point conn..". Is it that my network adapter is not identified; why?
 
How to solve this?

---

### Post by Celauran on 2009-06-04
Can you post the output of the following commands?

```
ifconfig
sudo lshw -C network
```

---

### Post by warjw on 2009-06-04
[FONT=Courier New][SIZE=2]rajitha@rajitha-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83388 (81.4 KB)  TX bytes:83388 (81.4 KB)

rajitha@rajitha-laptop:~$ sudo lshw -C network
[sudo] password for rajitha: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0[/SIZE][/FONT]

---

### Post by Celauran on 2009-06-04
Looks like it might be a missing driver. As near I can tell, that card requires the e1000e driver. Try:

```
sudo lsmod | grep e1000
```

---

### Post by warjw on 2009-06-04
it does not return anything.

---

### Post by Celauran on 2009-06-04
You'll need to add the kernel module, though I'm not certain if you need the e1000 module or e1000e.

---

### Post by LewRockwell on 2009-06-04
I just had a Dell in that was built in early 2005 and it worked perfectly right out of the box. Wired LAN, wifi, interwebs, everything...wonder what happened with yours?

---

### Post by warjw on 2009-06-04
This is a quite high spec machine (bought in 2009). Could it be that the Ubuntu doesnot come with the driver for GigEthernet.

Thanks [Celauran]("http://ubuntuforums.org/member.php?u=188172") for the advise.

---

### Post by Celauran on 2009-06-04
Like I said, I'm pretty sure you just need to load the appropriate kernel module, I'm just not certain which one it is; either e1000 or e1000e. Googling the card name might help.

---

