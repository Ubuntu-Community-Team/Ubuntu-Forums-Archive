---
title: "Imposible to install mt7610u driver for usb wifi dongle"
date: 2017-10-01
forum: Networking &amp; Wireless
---

### Post by Lancro on 2017-10-01
I followed this guide [https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u](https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u)

It doesnt work, the computer doesnt have internet wired access, so i downloaded everything (packages and dependencies) in other computer, copied everything and tried, the error begins with IEEE80211 NUM_BANDS, in make stage, it says that if I meant "NUM_TIDS" because it cant find that num_bands thing, in make install the error is related to a file called mt7610u_sta.ko, it cant find.

Is there any other method for ubuntu 17.10 beta 2?, I havent found a fix for the previous tutorial, in all places its the same, and its supposed to work, or was supposed... I will look to take out the output correctly, like I said, the computer cant connect to internet without the device working.

I googled like hell, can anyone help me? (the device is the one of the tutorial, Ive done lsusb, its detected with same id, but doesnt work.

Thanks.

---

### Post by jeremy31 on 2017-10-01
*Thread moved to **Networking & Wireless**.*
You might need to file an issue at the github site with your errors but I think the code works with Ubuntu 16.04 or 16.04.1

---

### Post by Lancro on 2017-10-01
Dont know, all day working with that, Im nearly dead, Ill put the Output of make and sudo make install, there are a lot of errors there not fixed, lets see if anyone knows a solution, if not i wont be able to return to Ubuntu...

Make
> make -C tools
make[1]: se entra en el directorio '/home/lancrus/src/tools'
gcc -g bin2h.c -o bin2h
make[1]: se sale del directorio '/home/lancrus/src/tools'
/home/lancrus/src/tools/bin2h
chipset = mt7610u
cp -f os/linux/Makefile.6 /home/lancrus/src/os/linux/Makefile
make -C /lib/modules/4.13.0-12-generic/build SUBDIRS=/home/lancrus/src/os/linux modules
make[1]: se entra en el directorio '/usr/src/linux-headers-4.13.0-12-generic'
  CC [M]  /home/lancrus/src/os/linux/../../os/linux/rt_profile.o
scripts/Makefile.build:302: fallo en las instrucciones para el objetivo '/home/lancrus/src/os/linux/../../os/linux/rt_profile.o'
Makefile:1546: fallo en las instrucciones para el objetivo '_module_/home/lancrus/src/os/linux'
make[1]: se sale del directorio '/usr/src/linux-headers-4.13.0-12-generic'
Makefile:403: fallo en las instrucciones para el objetivo 'LINUX'


So make install...

> make -C /home/lancrus/src/os/linux -f Makefile.6 install
make[1]: se entra en el directorio '/home/lancrus/src/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/lancrus/src/conf/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/4.13.0-12-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7610u_sta.ko /lib/modules/4.13.0-12-generic/kernel/drivers/net/wireless/
Makefile.6:454: fallo en las instrucciones para el objetivo 'install'
make[1]: se sale del directorio '/home/lancrus/src/os/linux'
Makefile:499: fallo en las instrucciones para el objetivo 'install'


sale = exiting
fallo = fail
instrucciones = instructions
para = for
objetivo = objective
entra = entering

I think with that you will understand that spanish output, if anyone can help...

---

### Post by jeremy31 on 2017-10-01
I just tried it in Ubuntu 16.04 with the 4.4 kernel and it does build a module but with a lot of warnings and I don't have the wireless card to test with.  I can imagine trying to build it using a 4.13 kernel would be impossible.  The code from github is 2 years old. Maybe try [https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916](https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916) as it is a bit newer code but still 9 months old, so I have some doubts about it working with 4.13

---

### Post by Lancro on 2017-10-02
Thanks for trying, Ill look for some adaptors

---

### Post by chili555 on 2017-10-02
For the benefit of the searchers out there, please see post #18: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u)> Original Poster: Help me make this work.
Driver guru: It can't work.
Original Poster: But, but, isn't there another solution?
Driver guru: Sure. Put this under the wheel of your car as you drive down to the store to get a different device.


---

### Post by vitaly-v-ch on 2018-07-14
Two more drivers for this stuff:


[LIST]
[*][https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes](https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes)
[*][https://github.com/ulli-kroll/mt7610u](https://github.com/ulli-kroll/mt7610u)
[*][https://github.com/Hygens/mt7610u_ubuntu_1610](https://github.com/Hygens/mt7610u_ubuntu_1610)
[/LIST]

---

### Post by chili555 on 2018-07-14
> **vitaly-v-ch said:**
> Two more drivers for this ****

[LIST]
[*][https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes](https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes)
[*][https://github.com/ulli-kroll/mt7610u](https://github.com/ulli-kroll/mt7610u)
[/LIST]
Do they compile and drive the device correctly with a current kernel version, say 4.4 and newer?

---

### Post by vitaly-v-ch on 2018-07-14
They all are primarily targeted for current kernels. I'm testing them just now.

---

