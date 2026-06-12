---
title: "Wifi stopped working after kernel update"
date: 2019-09-10
forum: Networking &amp; Wireless
---

### Post by fraizor on 2019-09-10
there was one kernel update wifi stopped working so i did the steps again and it worked 

```
user@user-pc:~$ cd rtl8723buuser@user-pc:~/rtl8723bu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-62-generic/build M=/home/user/rtl8723bu  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-62-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-62-generic'
user@user-pc:~/rtl8723bu$ sudo make install
[sudo] password for user:    
install -p -m 644 -D 8723bu.ko /lib/modules/4.15.0-62-generic/kernel/drivers/net/wireless/8723bu.ko
/sbin/depmod  -a 4.15.0-62-generic
install rtl8723b_fw.bin -D /lib/firmware/rtl_bt/rtl8723b_fw.bin
user@user-pc:~/rtl8723bu$ sudo -i
root@user-pc:~# modprobe -r rtl8xxxu
root@user-pc:~# echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
root@user-pc:~# exit
logout
user@user-pc:~/rtl8723bu$ 





```

today i updated to 4.15 using update manager 
wifi stopped working so i did the steps again and again but no luck

the system cant detect the internal wifi adapter
i am writing this message using external wifi adapter


any ideas ?

> :~$ dmesg | grep -e 8723 -e rtl[    7.672730] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    7.672735] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[    7.695377] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    7.695385] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    7.937979] 8723bu: version magic '4.15.0-60-generic SMP mod_unload ' should be '4.15.0-62-generic SMP mod_unload '








---

### Post by chili555 on 2019-09-10
Please try:

```
cd rtl8723bu
[B]make clean
git pull[/B]
make
sudo make install
```Check dmesg and we hope this is now corrected:> 8723bu: version magic '4.15.0-60-generic SMP mod_unload ' should be '4.15.0-62-generic SMP mod_unload '

---

### Post by fraizor on 2019-09-10
thank you again now it is working 

please explain what happned ?

---

### Post by chili555 on 2019-09-10
> **fraizor said:**
> thank you again now it is working 

please explain what happned ?When you ran 'make' originally, it was against kernel version 4.15.0-60 and I suspect it left some remnants behind. That seems to account for this message:> 
8723bu: version magic '4.15.0-60-generic SMP mod_unload ' ***should be '4.15.0-62***-generic SMP mod_unload '

The way to clear away all old remnants of a prior build is with 'make clean.' The 'git pull' step goes back to the original git repository and updates your driver file with any changes. Now that you have a cleaned workbench and the latest driver, then a correct driver is built and, most imprtantly, works!

---

### Post by fraizor on 2019-09-10
thank you a lot , you are a friend and a teacher !

appreciate your help bro

---

### Post by chili555 on 2019-09-10
> **fraizor said:**
> thank you a lot , you are a friend and a teacher !

appreciate your help broMay I please have a Solved? You can never overdose on positive vibes!

---

