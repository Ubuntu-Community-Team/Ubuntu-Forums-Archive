---
title: "network UNCLAIMED (Intel I219-V) --ubuntu 16.04.2LTS"
date: 2017-03-21
forum: Networking &amp; Wireless
---

### Post by syruprise on 2017-03-21
[SOLVED]

I'm at a loss right now.  Built new PC.  Installed Win10 and  everything is working fine (posting this from Win10).  Got ubuntu up and  running with internet working just fine.  Not sure what happened but at  some point lost my ethernet connection.
  
Booted into ubuntu no internet.  Booted into ubuntu liveCD no internet.  Booted into Manjaro liveCD no internet.  Bunsenlabs, etc.

```


      blank@blank:~$ ifconfig -a
      lo    Link encap:Local Loopback      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
      RX packets:3380 errors:0 dropped:0 overruns:0 frame:0
      TX packets:3380 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1 
      RX bytes:249984 (249.9 KB)  TX bytes:249984 (249.9 KB) 
```

```

blank@blank:~$ sudo lshw -C network 
   *-network UNCLAIMED     
   description: Ethernet controller
   product: Ethernet Connection (2) I219-V
   vendor: Intel Corporation
   physical id: 1f.6
   bus info: pci@0000:00:1f.6
   version: 00
   width: 32 bits
   clock: 33MHz
   capabilities: pm msi cap_list
   configuration: latency=0
   resources: memory:dff00000-dff1ffff 
```

The only thing I did between installing ubuntu and it working just  fine and ethernet connection getting borked was update my BIOS for the Asus Prime  270a.  Poured through BIOS settings to try and find any LAN conflicts  and reset defaults to try and fix.  No go.  Not sure how or why a BIOS update could screw up linux ethernet that badly though.  ***I h******ave not tried rolling back BIOS yet as I cannot find the  original version of the BIOS I had running yet.  Might try an older  version soon.  ***

  Trying building Intel drivers for ethernet was a no go as well.

```


   root@blank:/home/blank/etho/e1000e-3.3.4/src# make install
make -C /lib/modules/4.8.0-36-generic/build SUBDIRS=/home/blank/etho/e1000e-3.3.4/src modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-36-generic'
  CC [M]  /home/blank/etho/e1000e-3.3.4/src/netdev.o
In file included from ./include/linux/kernel.h:13:0,
                 from ./include/linux/list.h:8,
                 from ./include/linux/module.h:9,
                 from /home/blank/etho/e1000e-3.3.4/src/netdev.c:24:
/home/blank/etho/e1000e-3.3.4/src/netdev.c: In function â€˜e1000e_dumpâ€™:
/home/blank/etho/e1000e-3.3.4/src/netdev.c:250:25: error: â€˜struct net_deviceâ€™ has no member named â€˜trans_startâ€™
    netdev->state, netdev->trans_start, netdev->last_rx);
                         ^
./include/linux/printk.h:283:34: note: in definition of macro â€˜pr_infoâ€™
  printk(KERN_INFO pr_fmt(fmt), ##__VA_ARGS__)
                                  ^
/home/blank/etho/e1000e-3.3.4/src/netdev.c: In function â€˜e1000_xmit_frameâ€™:
/home/blank/etho/e1000e-3.3.4/src/netdev.c:6545:8: error: â€˜struct net_deviceâ€™ has no member named â€˜trans_startâ€™
  netdev->trans_start = jiffies;
        ^
scripts/Makefile.build:289: recipe for target '/home/blank/etho/e1000e-3.3.4/src/netdev.o' failed
make[2]: *** [/home/blank/etho/e1000e-3.3.4/src/netdev.o] Error 1
Makefile:1491: recipe for target '_module_/home/blank/etho/e1000e-3.3.4/src' failed
make[1]: *** [_module_/home/blank/etho/e1000e-3.3.4/src] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-36-generic'
Makefile:247: recipe for target 'default' failed
make: *** [default] Error 2 
```
 
Not sure what to do next.  What gives me pause is that I had internet  up and running on ubuntu which makes me think it's fixable. But the fact  that all livecd's internet connection are not working either makes me think it's  hardware/BIOS problem.  But again ethernet works fine in win10.  I can post ethernet.txt or whatever else might be needed for assistance.
 
Only bonus out of this is that I really got to brush up on my terminal skills.  Any help would be much appreciated.

 -JB

---

### Post by ZhurX on 2017-03-21
I have exactly same problem. Except my MB is Asus ROG STRIX Z270G GAMING :mad:

---

### Post by ZhurX on 2017-03-21
Turns out this problem is quite old. Here's how I solved it.

There is an error message in dmesg:

> [    1.216090] e1000e 0000:00:1f.6: The NVM Checksum Is Not Valid


Download driver here: 
[https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-?product=71307](https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-?product=71307)

(I used version 3.3.5.3)


Extract & cd into e1000e-3.3.5.3/src


Edit nvm.c, function e1000e_validate_nvm_checksum_generic (line 563) to:


```
s32 e1000e_validate_nvm_checksum_generic(struct e1000_hw *hw)
{
[COLOR=#ff0000]**    /***[/COLOR]
    s32 ret_val;
    u16 checksum = 0;
    u16 i, nvm_data;


    for (i = 0; i < (NVM_CHECKSUM_REG + 1); i++) {
        ret_val = e1000_read_nvm(hw, i, 1, &nvm_data);
        if (ret_val) {
            e_dbg("NVM Read Error\n");
            return ret_val;
        }
        checksum += nvm_data;
    }


    if (checksum != (u16)NVM_SUM) {
        e_dbg("NVM Checksum Invalid\n");
        return -E1000_ERR_NVM;
    }
[COLOR=#ff0000]**    */**[/COLOR]


    return 0;
}

```


Build & install
```
make


sudo rmmod e1000e
sudo make install
sudo modprobe e1000e
```

It should work now :D


Source: [https://unix.stackexchange.com/a/295052/23506](https://unix.stackexchange.com/a/295052/23506)


P.S. Checked on: 

  % lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial


  % uname -a
Linux 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:29:05 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by syruprise on 2017-03-21
Much love & many thanks ZhurX!!!!  :P  That worked like a charm!!!
[EDIT]
I gotta rmmod; modprobe every time I restart but whatever... it works!

---

### Post by ZhurX on 2017-03-22
> [COLOR=#000000]I gotta rmmod; modprobe every time I restart but whatever... it works![/COLOR]

Yeah, that's weird. AFAIK the change should be persistent since the make install runs depmod. Anyhow, I fixed it by running

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by Tereza_Simcic on 2017-09-23
Thank you so much !!
I bought a new computer and having the same issues, now works like a charm :)

Ethernet controller: Ethernet Connnection (S) 1219 LM

---

### Post by feynstein on 2018-08-13
Thanks, ZhurX!!  I'd just bought a new Lenovo and partitioned it for Ubuntu.  I've never had trouble with the e1000 driver before; this was a new one for me.  Thanks for tracking this down (I did _not_ get an error in the system logs).

---

### Post by wildmanne39 on 2018-08-13
Back to sleep old thread!

---

