---
title: "eth0 disappeared after kernel update to 2.6.17"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by matoxxx on 2006-11-01
Hi there, 
i encountered weird problem after updated to Edgy, all worked fine, except after i installed new kernel 2.6.17 my Prism Intersil 2.5 device eth0 disapeared so no networking for me . 2.6.15 is working fine. What is the problem , no support for wifi in new kernel ?


[HTML]2.6.15
lspci:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:60:B3:64:6D:9F  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1817212 (1.7 MiB)  TX bytes:258148 (252.0 KiB)
          Interrupt:209 Memory:dfeff000-dfefffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

iwconfig:
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"lukromtel"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:4F:62:08:C2:76   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/92  Signal level=-18 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]

[HTML]2.6.17
lspci:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)


ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

iwconfig:
lo        no wireless extensions.

wlan0     no wireless extensions.[/HTML]


Does this problem have something to do with bad symlinking of vmlinuz to new kernel ? (i found this information in forum)[http://www.ubuntuforums.org/showthread.php?t=285230&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=285230&highlight=kernel) 
But i am worried to remove old symlinks and rewrite them as author suggested. Is it safe ?

[HTML]matoxxx@matoxxx-desktop:~$ dpkg -l | grep linux-image
ii  linux-image-2.6.15-27-386              2.6.15-27.48                         Linux kernel image for version 2.6.15 on 386
ii  linux-image-2.6.17-10-386              2.6.17-10.33                         Linux kernel image for version 2.6.17 on i38
matoxxx@matoxxx-desktop:~$ ls -l / | grep vmlinuz
lrwxrwxrwx   1 root root    26 2006-11-01 13:49 vmlinuz -> boot/vmlinuz-2.6.17-10-386
lrwxrwxrwx   1 root root    26 2006-10-28 20:49 vmlinuz.old -> boot/vmlinuz-2.6.15-27-386[/HTML]

---

### Post by matoxxx on 2006-11-01
Sorry for spamming the forum but i realy need to know the answer for my question i posted in original thread.

[http://www.ubuntuforums.org/showthread.php?t=290475](http://www.ubuntuforums.org/showthread.php?t=290475)

thanks in advance.

---

### Post by DarkN00b on 2006-11-01
Most likely you just have to reinstall the drivers for your Prism device. I had to do this with the firmware for my Prism II device after one kernel update. After that I never had to do it again.

---

### Post by DarkN00b on 2006-11-01
See your original post...

---

### Post by matoxxx on 2006-11-01
I'll try

---

### Post by aysiu on 2006-11-01
> **matoxxx said:**
> Sorry for spamming the forum but i realy need to know the answer for my question i posted in original thread.

[http://www.ubuntuforums.org/showthread.php?t=290475](http://www.ubuntuforums.org/showthread.php?t=290475)

thanks in advance.
Next time you want to attract attention to your thread, wait a little bit (say, twenty-four hours, instead of five hours), and then put a new post in **the same thread** and just type > bump I'll give you an example in the next post.

---

### Post by aysiu on 2006-11-01
bump

---

### Post by matoxxx on 2006-11-02
I have downloaded hostap-driver and tried to compile them with 2.6.17-10-386 kernel but i get following error :

m> atoxxx@matoxxx-desktop:~/Desktop/hostap-driver-0.4.9$ KVERS=2.6.17-10-386 make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/matoxxx/Desktop/hostap-driver-0.4.9/driver/modules \
                MODVERDIR=/home/matoxxx/Desktop/hostap-driver-0.4.9/driver/modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
scripts/Makefile.build:17: /home/matoxxx/Desktop/hostap-driver-0.4.9/driver/modules/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/matoxxx/Desktop/hostap-driver-0.4.9/driver/modules/Makefile'. Stop.
make[1]: *** [_module_/home/matoxxx/Desktop/hostap-driver-0.4.9/driver/modules] Chyba 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [2.6] Chyba 2

I am new to compiling, can anyone help me.

---

### Post by matoxxx on 2006-11-02
bump

---

### Post by matoxxx on 2006-11-02
Ahh forget it, moderators pls delete this thread

i am switching back to Dapper, i have no time to solve these types of problems, got work to do.

---

### Post by Ariccanfly on 2006-11-09
I just installed Edgy on a HP pavillion DV2120ca

01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

Default Edgy drivers let me see the green light and other networks, but unable to connect.  
Used "windows wireless driver" to install Bcmwl5.inf
didn't work.


so same problem as our friend here.

---

