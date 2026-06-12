---
title: "agere systems Et-131x driver"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by alhebsi on 2007-03-29
hi 

i hope someone can help me with my problem 
i have ubuntu 6.06 and i can not connect to the internet 

my network adapter: agere systems Et-131x PCI-E Gigabit Ethernet Controller

---

### Post by alhebsi on 2007-03-30
some one can help :(

---

### Post by chili555 on 2007-03-30
I found this: [http://sourceforge.net/projects/et131x](http://sourceforge.net/projects/et131x) In addition, you will probably need build-esentials, linux-headers and linux-source and their dependencies to match your running kernel (*uname -r)* from synaptic, if you have internet availability, or you can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com), burn a CD and move them to your Ubuntu machine. Install with *sudo dpkg -i <package_you_downloaded>.deb.*

If you need more help, post back. My dentist reports I have a very high pain threshhold.

---

### Post by chili555 on 2007-03-30
I also found this, which looks more promising, to me: [http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html](http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html) Scroll on down to: **Wired Ethernet**

My novocaine is starting to kick in...

---

### Post by alhebsi on 2007-03-30
thanks Bro :)

first i could not do this comand 
>sudo apt-get install build-essential linux-headers-686

maybe because i don't have the package which you talk about in your first post and i don't know how i can get it :( >> sorry but i am really beginer in ubuntu

---

### Post by chili555 on 2007-03-30
Please run the command in a terminal: *uname -r*. Jot down the information it returns. Boot back into Windows, or however you respond to these posts. Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search, after selecting Dapper (6.06), for build-essential. You will see there are dependencies, signified by a red dot. You probably already have gcc and make. Download all the others and include them on your CD.

Do the same for linux-headers-686. This depends on linux-headers-2.6.15-28-686. Download both. I assume the data you jotted down verifies you have kernel version 2.6.15. Burn your CD and move back to Ubuntu. 

Install all the packages, in lieu of apt-get, with the terminal command: *sudo dpkg -i <each_package>.deb.* Then continue the instructions.

Post back and let us know how it's going.

---

### Post by alhebsi on 2007-03-31
i try and everytime it request many pakege and this is the error i got 



#@make -C /lib/modules/2.6.17-10-generic/build M=/home/hebsi/et131x/et131x/linux/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/hebsi/et131x/et131x/linux/driver/et131x_main.o
In file included from /home/hebsi/et131x/et131x/linux/driver/ET1310_common.h:89,
                 from /home/hebsi/et131x/et131x/linux/driver/ET1310_phy.h:90,
                 from /home/hebsi/et131x/et131x/linux/driver/et131x_main.c:111:
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:115:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:136:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:157:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:178:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:199:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:238:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:293:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:346:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:401:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:456:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:491:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:512:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:537:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:597:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:650:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:671:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:694:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:717:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:762:9: warning: "BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:785:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:808:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:831:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:854:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:936:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1005:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1026:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1047:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1070:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1093:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1138:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1159:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1182:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1205:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1226:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1269:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1290:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1313:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1336:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1357:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1465:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1500:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1525:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1549:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1570:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1591:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1618:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1653:9: warning: "BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1688:9: warning: "BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1740:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1773:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1818:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1839:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1860:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1885:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1919:9: warning: "BIT_FILEDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1944:9: warning: "BIT_FILEDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:1969:9: warning: "BIT_FILEDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2005:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2036:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2061:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2086:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2111:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2136:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2159:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2247:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2296:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2335:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2366:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2401:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2433:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2454:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2483:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2506:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2531:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2552:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2573:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2598:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2649:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2688:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2713:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2774:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:2841:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:3067:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_address_map.h:3100:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/hebsi/et131x/et131x/linux/driver/et131x_adapter.h:84,
                 from /home/hebsi/et131x/et131x/linux/driver/et131x_main.c:116:
/home/hebsi/et131x/et131x/linux/driver/ET1310_tx.h:99:13: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_tx.h:195:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/hebsi/et131x/et131x/linux/driver/et131x_adapter.h:85,
                 from /home/hebsi/et131x/et131x/linux/driver/et131x_main.c:116:
/home/hebsi/et131x/et131x/linux/driver/ET1310_rx.h:138:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_rx.h:169:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_rx.h:245:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_rx.h:284:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/ET1310_rx.h:315:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/hebsi/et131x/et131x/linux/driver/et131x_main.c:140: error: expected &#8216;)&#8217; before string constant
/home/hebsi/et131x/et131x/linux/driver/et131x_main.c:141: error: expected &#8216;)&#8217; before string constant
make[2]: *** [/home/hebsi/et131x/et131x/linux/driver/et131x_main.o] Error 1
make[1]: *** [_module_/home/hebsi/et131x/et131x/linux/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [modules] Error 2

---

### Post by chili555 on 2007-03-31
Did you apply the patches in the instructions here: [http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html](http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html)

I got the same errors until I applied the patches, which are a bit tedious, but afterwards, no errors were encountered and the module made without errors.

---

### Post by alhebsi on 2007-04-01
right now i have wireless connection in my college so i will download the update then i will continue your step :)

---

### Post by alhebsi on 2007-04-02
still it's not work with me :(

---

### Post by chili555 on 2007-04-02
At which point did you get stuck? Where are you unable to proceed?

---

### Post by alhebsi on 2007-04-02
when i did this comman 

 patch new_ver_x86_3-10-06.patch 

i didn't get anything!!

---

### Post by chili555 on 2007-04-02
Try patch < new_ver_x86_3-10-06.patch. Put that little arrow in there.

---

### Post by alhebsi on 2007-04-02
now i hvae error in make command :(

this is the error

[email]hebsi@hebsi-laptop:~/et131x-1.2.2-3.src.tar.gz[/email]_FILES$ make
#@make -C /lib/modules/2.6.17-10-generic/build M=/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/et131x_main.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/et131x_initpci.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/et131x_isr.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/et131x_netdev.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/et131x_supp.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/et131x_config.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/et131x_debug.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_jagcore.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_tx.o
  CC [M]  /home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.o
/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.c: In function &#8216;nic_rx_pkts&#8217;:
/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.c:1476: error: &#8216;pShBufVa&#8217; undeclared (first use in this function)
/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.c:1476: error: (Each undeclared identifier is reported only once
/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.c:1476: error: for each function it appears in.)
/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.c:1670: warning: unused variable &#8216;vlan_tag&#8217;
make[2]: *** [/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.o] Error 1
make[1]: *** [_module_/home/hebsi/et131x-1.2.2-3.src.tar.gz_FILES] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [modules] Error 2

---

### Post by Pringle on 2007-04-03
> **chili555 said:**
> I found this: [http://sourceforge.net/projects/et131x](http://sourceforge.net/projects/et131x) In addition, you will probably need build-esentials, linux-headers and linux-source and their dependencies to match your running kernel (*uname -r)* from synaptic, if you have internet availability, or you can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com), burn a CD and move them to your Ubuntu machine. Install with *sudo dpkg -i <package_you_downloaded>.deb.*

Right, i'm having the same issue with the 131 card. Ubuntu isn't detecting my card and i have no idea what to do. I have searched for the packages on the Ubuntu website and when typing in 'Linux-headers' i get a list of around 29. Which one :confused: Sorry to be such a biff, brand new to it all.

---

### Post by alhebsi on 2007-04-03
>>>>>

up

---

### Post by alhebsi on 2007-04-04
up 

:(

---

### Post by chili555 on 2007-04-04
This has been very difficult, but my poor computer, after trying three different methods, and pouring smoke from the keyboard, finally has a module: ```
/lib/modules/2.6.17-11-generic/extra/et131x.ko
```Now, I have no way to test if it actually works, since I do not have an et131x device, but I can finally build the module with warnings, but without errors! Here is what I did:
1. Download: [http://dadams1969.googlepages.com/et131x_20060131_v1-2-2.tar.gz](http://dadams1969.googlepages.com/et131x_20060131_v1-2-2.tar.gz)
2. Download: [http://dadams1969.googlepages.com/et131x_kernel_2.6.17.patch](http://dadams1969.googlepages.com/et131x_kernel_2.6.17.patch)
3. Extract et131x_20060131_v1-2-2.tar.gz```
tar –xzvf et131x_20050801_v1-2-2.tar.gz
```4. In a terminal:```
cd et131x_20050801_v1-2-2/et131x/linux/driver
```5. ```
mv /home/username/et131x_kernel_2.6.17.patch /home/username/et131x_20050801_v1-2-2/et131x/linux/driver
```6.```
patch  < et131x_kernel_2.6.17.patch
sudo su
make
make modules_install
modprobe et131x
ifconfig eth0
```Substitute your username. Post back and let us know.

---

### Post by alhebsi on 2007-04-05
finally it is work :)

thaaaaaank you very much

i add the comand (i found it in readme file)

insmod et131x.ko
ifconfig eth1 up


I have another problem 
my sound card is not work (realtek) i hope u can help me in this also :)

---

### Post by chili555 on 2007-04-05
You should start a new thread over in the hardware forum. Glad it's working!

---

### Post by mrdelichops on 2007-07-31
I was going to post a new thread, but I figured this was more of an extension of the original problem.

I got the 131x driver working on my Feisty distro, but it I don't think it realized the wireless card uses the same drivers or something

so the ethernet port works, but no wireless =\

either way lspci -nn reads it as RaLink RT2561/RT61 rev B 802.11g
and lshw network -C:

description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 9
       bus info: pci@05:09.0
       logical name: ra1
       version: 00
       serial: 00:13:d3:73:3d:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64
       link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:feaf0000-feaf7fff irq:16

I've been looking around, but I haven't found anything

thanks in advance

---

### Post by slira on 2007-09-06
Hi all
We've just finished the work... the 131x card is now working OK
Thanks to you all!

We did it on a ubuntu dapper drake, freshly installed from the live-cd
we got all needed packages from another machine already linked to the net, and from the live cd
Drivers and patches worked fine! even on a 15 kernel, and not the 17 as it should be (!)

step by step:
1 - in a shell type [FONT="Courier New"]uname -r[/FONT]
2 - you got the kernel version; note it down
3 - pop in the live cd and it will ask you to open the package manger using the cd as the source
4 - accept
5 - search for build-essentials
6 - install; make sure all the dependencies are selected, specially make
7 - using a machine already connected to the net go to [http://packages.ubuntu.com]("http://packages.ubuntu.com") select dapper and go to Development
8 - search for the linux-headers matching your kernel. The syntax should be something along the lines of linux-headers-"uname -r result"-386
9 - download it and the dependency called linux-headers-"uname -r result" do not worry about other dependencies, they were installed from the cd
10 - copy it to your machine (with 131x card) - a usb drive works fine :)
11 - double click the linux-headers-"uname -r result" and install; the same for the other package
12 - download [ the drivers and the patches]("http://dadams1969.googlepages.com/et131x-1.2.2-3.src.tar.gz") and [ this patch for edgy]("http://dadams1969.googlepages.com/et131x_kernel_2.6.17.patch") (it works fine for dapper!) 
13 - get those in the 131x machine and unpack the .tar.gz file into a working directory (/home/"your user name"/temp works fine)
14 - put the patch into the same temp directory and extract the et131x-1.2.2.tar.bz2 file that was inside the original tar.gz. Unpack this one too.
15 - rename the et131x-1.2.2 folder to et131x
16 - in a shell type [FONT="Courier New"] cd temp[/FONT] this is to get you in the folder where you unpacked the stuff... (temp or whatever you named that folder)
17 - lets patch: 

Apply the patches in order:
[FONT="Courier New"]
$patch < new_ver_x86_3-10-06.patch
$patch < fix-patch_et131x_x86_3-10-06.diff
$patch < fix-get_mac_address_from_EEPROM.diff
$patch < et131x_kernel_2.6.17.patch[/FONT]

each time you do it, it will ask for the file to patch; write et131x/"the file name shown before you are asked to write it" sometimes it already includes et131x/ in the file name.

DO NOT type et131x twice!!!!

18 - one of the patches (eeprom) will print out an error message; ignore it
19 - ok, your drivers are patched
20 - lets compile them:
21 - in the shell type [FONT="Courier New"]cd et131x[/FONT]
22 - type [FONT="Courier New"]make[/FONT] should any compile error come up like something to do with build or modpost, you probably do no have the correct linux-headers; make sure you do, by going into /usr/src and checking there is a linux-headers-"your kernel" folder there. hopefully it all went right, and you are ready to go
22 - in the shell type
[FONT="Courier New"]
$sudo make modules_install
$sudo insmod et131x.ko
$sudo depmod
$sudo modprobe et131x[/FONT]
23 - go to System>administration>network (or something like it)
24 - your card should be there...
25 - go to the DNS tab and add your router IP (usually 192.168.1.1)
26 - try the net; (if it's too slow type 
[FONT="Courier New"]
sudo gedit /etc/modprobe.d/blacklist[/FONT]
and add "blacklist ipv6" at the bottom; save and exit; reboot


check the urls below for many other thing to do on a LG laptop using ubuntu (including the hated synaptics)
[http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html]("http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html")

hope it helps
slira

---

### Post by Trixcan on 2008-01-18
Excellent help! Thanks guys for the hard work on this, i finally got mine working too! :D

---

### Post by slira on 2008-01-19
Hi there!
glad it worked!!! :):)
for the sake of curiosity: are you still on dapper?
Best
slira

---

