---
title: "Ethernet connection hangs"
date: 2023-05-29
forum: Networking &amp; Wireless
---

### Post by johnaaronrose on 2023-05-29
I'm now getting my wired (i.e. Ethernet) connection hanging on trying  to connect. I've tried switching ports (on the router) and using a  different cable, but still the same.
 
ifconfig shows for Ethernet:
 enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 50:eb:f6:ef:a4:e6  txqueuelen 1000  (Ethernet)
        RX packets 2779  bytes 250524 (250.5 KB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 355  bytes 72171 (72.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
 
sudo lshw -C enp2s0 shows nothing
 
lspci -nn shows for Ethernet: 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:8125] (rev 05)
 
I found a web page: [https://tutorialforlinux.com/2021/05/03/how-to-add-realtek-rtl8125-driver-ppa-for-ubuntu-based-systems/](https://tutorialforlinux.com/2021/05/03/how-to-add-realtek-rtl8125-driver-ppa-for-ubuntu-based-systems/)
I followed the instructions and installed realtek-r8125-dkms package  OK. On rebooting, I followed the instructed procedure (shown when  installing the package) of creating a password and then entering it when  requested on the reboot. But still same problem. Any ideas what to do?
 PS I've switched Wi-Fi on (though I'd prefer to use Ethernet, as my  Wi-Fi is a little flaky due to walls) in order to post this question.

---

### Post by johnaaronrose on 2023-06-01
More information:
I'm now getting my wired connection option not being available and also not shown with ifconfig. Also, my wi-fi connection hangs on trying to connect. I've tried various answers referred to below. 

ifconfig enp2so:
    enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            ether 50:eb:f6:ef:a4:e6  txqueuelen 1000  (Ethernet)
            RX packets 2779  bytes 250524 (250.5 KB)
            RX errors 0  dropped 1  overruns 0  frame 0
            TX packets 355  bytes 72171 (72.1 KB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ifconfig shows for wlp3s0:
john@Desktop:~$ ifconfig wlp3s0
wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.55.1  netmask 255.255.255.0  broadcast 192.168.55.255
        inet6 fe80::c01f:1a40:87b9:30b5  prefixlen 64  scopeid 0x20<link>
        ether bc:f1:71:6d:25:4f  txqueuelen 1000  (Ethernet)
        RX packets 161344  bytes 196076259 (196.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 88129  bytes 20314740 (20.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

iwconfig shows:
wlp3s0    IEEE 802.11  ESSID:"John's Phone"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 7A:17:94:F3:39:37   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:206   Missed beacon:0

sudo lshw -C enp2s0 shows nothing

sudo lshw -C wlp3s0 shows nothing

lspci -nn shows for Ethernet:
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:8125] (rev 05)
03:00.0 Network controller [0280]: Intel Corporation Wi-Fi 6 AX200 [8086:2723] (rev 1a)

I found a webpage:
[https://tutorialforlinux.com/2021/05/03/how-to-add-realtek-rtl8125-driver-ppa-for-ubuntu-based-systems/](https://tutorialforlinux.com/2021/05/03/how-to-add-realtek-rtl8125-driver-ppa-for-ubuntu-based-systems/)

I followed the instructions and installed realtek-r8125-dkms package OK. On rebooting, I followed the instructed procedure (shown when installing the package) of Enrolling a MOK, creating a password and then entering it when requested on the reboot. But worse in that the Wired option is not shown when trying to connect to internet via router. And my WiFi (using Router) is not working so I'm posting using my Android phone as a Hotspot. Will I have any hair left soon!

I've found another webpage:
[https://askubuntu.com/questions/1287967/cant-get-rtl8125-realtek-driver-working-on-version-20-04/1289417#1289417](https://askubuntu.com/questions/1287967/cant-get-rtl8125-realtek-driver-working-on-version-20-04/1289417#1289417)
I've tried both answer 1 & answer 2. Still no improvement after either. Any ideas what to do?

---

### Post by johnaaronrose on 2023-06-06
> **johnaaronrose said:**
> More information:
I'm now getting my wired connection option not being available and also not shown with ifconfig. Also, my wi-fi connection hangs on trying to connect. I've tried various answers referred to below. 

ifconfig enp2so:
    enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            ether 50:eb:f6:ef:a4:e6  txqueuelen 1000  (Ethernet)
            RX packets 2779  bytes 250524 (250.5 KB)
            RX errors 0  dropped 1  overruns 0  frame 0
            TX packets 355  bytes 72171 (72.1 KB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ifconfig shows for wlp3s0:
john@Desktop:~$ ifconfig wlp3s0
wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.55.1  netmask 255.255.255.0  broadcast 192.168.55.255
        inet6 fe80::c01f:1a40:87b9:30b5  prefixlen 64  scopeid 0x20<link>
        ether bc:f1:71:6d:25:4f  txqueuelen 1000  (Ethernet)
        RX packets 161344  bytes 196076259 (196.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 88129  bytes 20314740 (20.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

iwconfig shows:
wlp3s0    IEEE 802.11  ESSID:"John's Phone"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 7A:17:94:F3:39:37   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:206   Missed beacon:0

sudo lshw -C enp2s0 shows nothing

sudo lshw -C wlp3s0 shows nothing

lspci -nn shows for Ethernet:
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:8125] (rev 05)
03:00.0 Network controller [0280]: Intel Corporation Wi-Fi 6 AX200 [8086:2723] (rev 1a)

I found a webpage:
[https://tutorialforlinux.com/2021/05/03/how-to-add-realtek-rtl8125-driver-ppa-for-ubuntu-based-systems/](https://tutorialforlinux.com/2021/05/03/how-to-add-realtek-rtl8125-driver-ppa-for-ubuntu-based-systems/)

I followed the instructions and installed realtek-r8125-dkms package OK. On rebooting, I followed the instructed procedure (shown when installing the package) of Enrolling a MOK, creating a password and then entering it when requested on the reboot. But worse in that the Wired option is not shown when trying to connect to internet via router. And my WiFi (using Router) is not working so I'm posting using my Android phone as a Hotspot. Will I have any hair left soon!

I've found another webpage:
[https://askubuntu.com/questions/1287967/cant-get-rtl8125-realtek-driver-working-on-version-20-04/1289417#1289417](https://askubuntu.com/questions/1287967/cant-get-rtl8125-realtek-driver-working-on-version-20-04/1289417#1289417)
I've tried both answer 1 & answer 2. Still no improvement after either. Any ideas what to do?

     I've been advised on Launchpad at [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2022826](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2022826) to generate & insert r8169 module (as lsmod shows it's not present), by first downloading GBE  Ethernet LINUX driver r8169 for kernel up to 5.19 (i.e.r8169-6.031.00.tar.bz2 from [https://www.realtek.com/en/component/zoo/category/rtl8110sc-l-s](https://www.realtek.com/en/component/zoo/category/rtl8110sc-l-s) and extracting it to r8169-6.031.00:
john@Desktop:~/Software/Realtek/r8169-6.031.00$ sudo modprobe -r 8169.tar.bz2 & extracting it tor8169-6.031.00 and then doing:
john@Desktop:~/Software/Realtek/r8169-6.031.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory '/home/john/Software/Realtek/r8169-6.031.00/src'
make -C /lib/modules/5.19.0-43-generic/build M=/home/john/Software/Realtek/r8169-6.031.00/src clean
make[2]: Entering directory '/usr/src/linux-headers-5.19.0-43-generic'
make[2]: Leaving directory '/usr/src/linux-headers-5.19.0-43-generic'
make[1]: Leaving directory '/home/john/Software/Realtek/r8169-6.031.00/src'
make -C src/ modules
make[1]: Entering directory '/home/john/Software/Realtek/r8169-6.031.00/src'
make -C /lib/modules/5.19.0-43-generic/build M=/home/john/Software/Realtek/r8169-6.031.00/src modules
make[2]: Entering directory '/usr/src/linux-headers-5.19.0-43-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0
  You are using:           gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0
  CC [M]  /home/john/Software/Realtek/r8169-6.031.00/src/r8169_n.o
  LD [M]  /home/john/Software/Realtek/r8169-6.031.00/src/r8169.o
  MODPOST /home/john/Software/Realtek/r8169-6.031.00/src/Module.symvers
  CC [M]  /home/john/Software/Realtek/r8169-6.031.00/src/r8169.mod.o
  LD [M]  /home/john/Software/Realtek/r8169-6.031.00/src/r8169.ko
  BTF [M] /home/john/Software/Realtek/r8169-6.031.00/src/r8169.ko
Skipping BTF generation for /home/john/Software/Realtek/r8169-6.031.00/src/r8169.ko due to unavailability of vmlinux
make[2]: Leaving directory '/usr/src/linux-headers-5.19.0-43-generic'
make[1]: Leaving directory '/home/john/Software/Realtek/r8169-6.031.00/src'
john@Desktop:~/Software/Realtek/r8169-6.031.00$ sudo make install
make -C src/ install
make[1]: Entering directory '/home/john/Software/Realtek/r8169-6.031.00/src'
make -C /lib/modules/5.19.0-43-generic/build M=/home/john/Software/Realtek/r8169-6.031.00/src INSTALL_MOD_DIR=kernel/drivers/net/ethernet/realtek modules_install
make[2]: Entering directory '/usr/src/linux-headers-5.19.0-43-generic'
  INSTALL /lib/modules/5.19.0-43-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
  SIGN    /lib/modules/5.19.0-43-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
  DEPMOD  /lib/modules/5.19.0-43-generic
Warning: modules_install: missing 'System.map' file. Skipping depmod.
make[2]: Leaving directory '/usr/src/linux-headers-5.19.0-43-generic'
make[1]: Leaving directory '/home/john/Software/Realtek/r8169-6.031.00/src'
john@Desktop:~/Software/Realtek/r8169-6.031.00$ sudo depmod -a
john@Desktop:~/Software/Realtek/r8169-6.031.00$ sudo modprobe r8169
modprobe: ERROR: could not insert 'r8169': Key was rejected by service
john@Desktop:~/Software/Realtek/r8169-6.031.00$

 I have Secure Boot enabled in the BIOS.
As I don't want to make things worse, how do I fix missing 'System.map'  file and "modprobe: ERROR: could not insert 'r8169': Key was rejected by  service"?
PS there is the correct System.map in /boot:
root@Desktop:/# ls boot
config-5.15.0-73-generic      initrd.img-5.19.0-43-generic           System.map-5.15.0-73-generic
config-5.19.0-43-generic      initrd.img-5.19.0-43-generic.old-dkms  System.map-5.19.0-43-generic
efi                           initrd.img.old                         vmlinuz
grub                          memtest86+.bin                         vmlinuz-5.15.0-73-generic
initrd.img                    memtest86+.elf                         vmlinuz-5.19.0-43-generic
initrd.img-5.15.0-73-generic  memtest86+_multiboot.bin               vmlinuz.old

---

### Post by johnaaronrose on 2023-06-06
Just tried a USB wifi device. It also hangs while trying to connect to router.

---

### Post by johnaaronrose on 2023-06-09
Tech Support Realtek told me to disable Secure Boot which I have done. I  was then able to compile & install r8125, r8128 & r8128 modules  obtained from Realtek website. 'lsmod | grep r81' showed all 3 modules.  ifconfig showed the ethernet interface Ok (as enp3s0). However,  ethernet still hung on connection. So I rebooted and did 'lsmod | grep  81' only showed r8125! 'modinfo r8169 | grep 8125' showed nothing. Help  please!

---

### Post by johnaaronrose on 2023-06-09
My mistake, previous comment should have said r8168 & r8169 as the 2nd & 3rd 'r81' things on the first line.

Also r8169 installs Ok as shown by below even though ethernet connect hangs, but modinfo 'data' disappears on reboot:
$ modinfo r8169 | grep 8125
firmware: rtl_nic/rtl8125b-2.fw
firmware: rtl_nic/rtl8125a-3.fw
alias: pci:v000010ECd00008125sv*sd*bc*sc*i*

The firmware is present as shown by ls -la /lib/firmware/rtl_nic/rtl8125*

Is there a BIOS parameter or a missing Ubuntu package that would cause this?

---

### Post by #&amp;thj^% on 2023-06-09
**What kernel **are you using? Mine works OOTB:
```
inxi -N | grep  r8169 && inxi -N
  driver: r8169 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  Device-2: NetGear A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU] 
  type: USB driver: rtl88XXau 

```
And:
```
&#9474;~ 
&#9492;&#9472;> ls -la /lib/firmware/rtl_nic/rtl8125*
-rw-r--r-- 1 root root  3456 May  5 03:57 /lib/firmware/rtl_nic/rtl8125a-3.fw
-rw-r--r-- 1 root root 10128 May  5 03:57 /lib/firmware/rtl_nic/rtl8125b-1.fw
-rw-r--r-- 1 root root  3328 May  5 03:57 /lib/firmware/rtl_nic/rtl8125b-2.fw
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
Nope nothing in my Bios had to set beforehand.
Also I had problems with:
```
apt policy r8168-dkms
r8168-dkms:
  Installed: (none)
  Candidate: 8.051.02-2
  Version table:
     8.051.02-2 500
        500 http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu lunar/universe i386 Packages

```
Just how you describe now, is "r8168" still in place?
If so you will have to remove it then.

---

### Post by johnaaronrose on 2023-06-12
Using 'sudo smartctl -i -a /dev/sda', it shows for '202 Percent_Lifetime_Remain' the number 1. Does this mean that I should change my SSD ASAP? 
PS I've been having lots of problems connecting to my router and even my Phone as a Hotspot.

---

### Post by johnaaronrose on 2023-06-14
Apologies to everyone trying to help. It turns out that the problem is the computer: a 4 month old Asus mini PN50-1. I suddenly remembered that the same thing had happened last August and that the supplier had given me a replacement after I returned the original.

---

