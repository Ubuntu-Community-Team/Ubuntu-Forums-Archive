---
title: "Realtek RTL8723BE very weak signal"
date: 2018-02-13
forum: Networking &amp; Wireless
---

### Post by rogin on 2018-02-13
Hello. Greetings from Estonia! I just deleted my Windows and decided to use Ubuntu. Downloaded version 17.10
Unfortunately I got a bad wifi card for Linux operation system. 
I already found out what I need to download, and did that.
iwconfig shows me "wlo1"
after I cd to the the unzipped folder and use command "make" it gives me an error...

> risto@Risto-HP:~/Töölaud/rtlwifi_new-rock.new_btcoex$ make
make -C /lib/modules/4.13.0-32-generic/build M=/home/risto/Töölaud/rtlwifi_new-rock.new_btcoex modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-32-generic'
arch/x86/Makefile:153: CONFIG_X86_X32 enabled but no binutils support
./scripts/gcc-version.sh: line 25: gcc: command not found
./scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: gcc: Command not found
make[1]: gcc: Command not found
make[1]: gcc: Command not found
make[1]: gcc: Command not found
make[1]: gcc: Command not found
  CC [M]  /home/risto/Töölaud/rtlwifi_new-rock.new_btcoex/base.o
/bin/sh: 1: gcc: not found
scripts/Makefile.build:308: recipe for target '/home/risto/Töölaud/rtlwifi_new-rock.new_btcoex/base.o' failed
make[2]: *** [/home/risto/Töölaud/rtlwifi_new-rock.new_btcoex/base.o] Error 127
Makefile:1550: recipe for target '_module_/home/risto/Töölaud/rtlwifi_new-rock.new_btcoex' failed
make[1]: *** [_module_/home/risto/Töölaud/rtlwifi_new-rock.new_btcoex] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-32-generic'
Makefile:57: recipe for target 'all' failed
make: *** [all] Error 2

Hope someone is willing to help me becouse I've read this community is really awsome!

---

### Post by jeremy31 on 2018-02-13
*Thread moved to **Networking & Wireless**.*

You have read very old information, since Ubuntu 16.04 you do not need to download anything, we can test a module parameter and see what works best
First we unload the module
```
sudo modprobe -r rtl8723be
```
Then we load it using the antenna selection parameter set to 1
```
sudo modprobe rtl8723be ant_sel=1
```

See what wifi's are found and signal strength
```
iwlist scan | egrep -i 'ssid|quality'
```

Then we unload the module and load it using antenna #2
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=2
```
See what wifi are found
```
iwlist scan | egrep -i 'ssid|quality'
```

Which results were better?
If ant_sel=1 was best
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtlant.conf
```
If ant_sel=2 was best
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtlant.conf
```
You shouldn't have to worry about it after a reboot

---

### Post by rogin on 2018-02-14
Thank you very much! It worked very well!! 
> risto@risto-HP-Notebook:~$ sudo modprobe -r rlt8723be
[sudo] password for risto: 
modprobe: FATAL: Module rlt8723be not found.
risto@risto-HP-Notebook:~$ sudo modprobe -r rtl8723be
risto@risto-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=1
risto@risto-HP-Notebook:~$ iwlist scan | egrep -i 'ssid|quality'
enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:"ASUSe_2,4Ghz"
risto@risto-HP-Notebook:~$ sudo modprobe rtl8723be
risto@risto-HP-Notebook:~$ sudo modprobe -r rtl8723be
risto@risto-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=2
risto@risto-HP-Notebook:~$ iwlist scan | egrep -i 'ssid|quality'
enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

                    Quality=36/70  Signal level=-74 dBm  
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:""
                    Quality=44/70  Signal level=-66 dBm  
                    ESSID:"TP-LINK"
                    Quality=70/70  Signal level=-14 dBm  
                    ESSID:"ASUSe_2,4Ghz"
                    Quality=30/70  Signal level=-80 dBm  
                    ESSID:"TP-LINK_2.4GHz_438831"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:""
risto@risto-HP-Notebook:~$ echo "option rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtlant.conf
option rtl8723be ant_sel=2



Now I can move to the other hand of my house and the wifi signal is fine! <3

---

### Post by praseodym on 2018-02-14
So, if "ant_sel=2" is fine, make it permanent, as this solution is temporary:
```

echo "options rtl8732be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

---

### Post by jeremy31 on 2018-02-14
> **praseodym said:**
> So, if "ant_sel=2" is fine, make it permanent, as this solution is temporary:
```

echo "options rtl8732be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
It seems rogin has already run a similar command but there was a typo
> risto@risto-HP-Notebook:~$ echo "option rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtlant.conf
It needs to be ```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtlant.conf
```
I has to be options not option

---

### Post by rogin on 2018-02-16
I'm sorry but I missed the part where I had to make it permanent and today after I rebooted my pc to disable secure boot I booted Ubuntu up again and strange things started to happen.. First it was trying to connect to wifi but could not and now I dont even have a wifi option anymore :confused: 
Tried to do same things as u mentioned earlier but now I got a error right away saying
> risto@risto-HP-Notebook:~$ sudo modprobe -r rtl8723be
[sudo] password for risto: 
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/rtlant.conf line 1: ignoring bad line starting with 'option'


E: Ethernet Network (Realtek RTL 8101 / 2 / 6PCI Express Fast / Gigabit Ethernet controller) dissconnected
E2: Did a restart and magic happend. Connected to wifi again and very good signal!

---

### Post by jeremy31 on 2018-02-16
If you ran the ```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtlant.conf
```
command again it would have fixed your typo and wifi would work properly again after rebooting, you can check
```
cat /etc/modprobe.d/rtlant.conf
```
To see if it shows options rtl8723be ant_sel=2 now and not option rtl8723be ant_sel=2

---

