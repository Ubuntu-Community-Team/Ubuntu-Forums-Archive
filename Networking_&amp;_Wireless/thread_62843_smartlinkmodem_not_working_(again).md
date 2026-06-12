---
title: "smartlinkmodem not working (again)"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by nonamefortoday on 2005-09-06
Hi,
ok, i am kinda new to linux and it works pretty well (UBUNTU 5.04   i386) but im still having 1 big problem i can't get the modem to work. im trying for about a week but nothing has changed. 
[B]
modem : smartlink smartPCI561 56k Modem "NetoDragon", ALi Corporation[/B]

I've downloaded the driver from [www.smlink.com](www.smlink.com) (slmodem-2.9.10), read the readme (of course...),
changed the makefile (->KERNEL_DIR:=/usr/src/linux which i think is the correct path to the local kernel source tree (i dont exactly know what this means but anyways the installation doesnt seem to be the problem, i had to run module-assistant once to create all the things) 

root-terminal: *make*
       
->

[I]make -C modem all
make[1]: Entering directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/modem'
rebuild profile...
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_cmdline.o -c modem_cmdline.cgcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_datafile.o -c modem_datafile.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_at.o -c modem_at.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_timer.o -c modem_timer.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_pack.o -c modem_pack.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_ec.o -c modem_ec.c
modem_ec.c:689: warning: `t403_timeout' defined but not used
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_comp.o -c modem_comp.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_param.o -c modem_param.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_debug.o -c modem_debug.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o homolog_data.o -c homolog_data.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_sinus.o -c dp_sinus.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_dummy.o -c dp_dummy.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o sysdep_common.o -c sysdep_common.cgcc -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_test.o -c modem_test.c
gcc -o modem_test modem_test.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
make[1]: Leaving directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/modem'[/I]



no mean error messages...



root-terminal : [I]make install

make -C modem all
make[1]: Entering directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/modem'
make[1]: Leaving directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/modem'
make -C drivers KERNEL_DIR=/usr/src/linux
make[1]: Entering directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
cc -I/usr/src/linux/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.10-5-386
make[2]: Entering directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
make modules -C /usr/src/linux SUBDIRS=/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers
make[3]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers/.amrlibs.o.cmd for /home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers/amrlibs.o
*** Warning: "usb_endpoint_halted" [/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers/slusb.ko] undefined!
make[3]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[2]: Leaving directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
make[1]: Leaving directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
make install -C drivers KERNEL_DIR=/usr/src/linux
make[1]: Entering directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
cc -I/usr/src/linux/include -o kernel-ver kernel-ver.c
mkdir -p /dev
mknod -m 600 /dev/slamr0 c 212 0 ;   mknod -m 600 /dev/slamr1 c 212 1 ;   mknod -m 600 /dev/slamr2 c 212 2 ;   mknod -m 600 /dev/slamr3 c 212 3 ;  echo -n
mknod -m 600 /dev/slusb0 c 213 0 ;   mknod -m 600 /dev/slusb1 c 213 1 ;   mknod -m 600 /dev/slusb2 c 213 2 ;   mknod -m 600 /dev/slusb3 c 213 3 ;  echo -n
make install KERNEL_VER=2.6.10-5-386
make[2]: Entering directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
install -D -m 644 slamr.ko /lib/modules/2.6.10-5-386/extra/slamr.ko
install -D -m 644 slusb.ko /lib/modules/2.6.10-5-386/extra/slusb.ko
/sbin/depmod -a
make[2]: Leaving directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
make[1]: Leaving directory `/home/flo/Desktop/inst/slmodem-2.9.10.tar_FILES/slmodem-2.9.10/drivers'
install -D -m 755 modem/slmodemd /usr/sbin/slmodemd
rm -f -rf /var/lib/slmodem
install -d -D -m 755 /var/lib/slmodem[/I]

mmmh...looked pretty good.

that's what i did next:
*root terminal: slmodemd --country=42 *   (for germany)

but then:

[I]error: mdm setup: cannot open dev `/dev/slamr0': No such device or address
error: cannot setup device `/dev/slamr0'[/I]

this happens everytime i start slmodemd. gnome-ppp still can't find any modem.if i type:

slmodemd /dev/ttyS0 --country=42   (dont ask me why i did that, it seemed right to me at this moment...) it said:

[I]SmartLink Soft Modem: version 2.9.10 Sep  6 2005 17:09:15
bad country name `42', using default by code!
symbolic link `/dev/ttySL64' -> `/dev/pts/1' created.
modem `ttyS0' created. TTY is `/dev/pts/1'
Use `/dev/ttySL64' as modem device, Ctrl+C for termination[/I]

i'Ve tried some things with the following pakages:

sl-modem-daemon_2.9.9-1_i386.deb
sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb
sl-modem-source_2.9.9-1_i386.deb

No result.
I've read lots of comments, questions, faqs, wikis, boards and tried a lot of things 
no result

I need help, seriously! Thank you very much. 
And please, try to explain things as easy as possible.

flo

---

### Post by elfgoh on 2005-10-19
Hi, u can go to networking, under administration >> Click properties of your interent conncetion, enable the ppp connection >> Do not autodetect the deivce, instead set it as "/dev/ttySL64".

Key in all your other dial up settings and c if it works.

---

