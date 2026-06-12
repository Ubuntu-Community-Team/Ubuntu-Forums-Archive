---
title: "usb modem aam 6000ug"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by kbentekik on 2007-03-09
I'm a new mint (bianca) user,

yeah yeah, i know i'm here on the ubuntu forums but i guess you guy's can help me too.

the problem:i installed linux mint bianca, everyting did work very good, but i can't get connection with the internet.

I dead read a little and found the problem:
usb modems seem to be no good.
but, i have one so i would like to try to get it run:

nex problem:
i'm a linux noob, so i dead search for some howto's, and yeah i did found somme (made for debian)  there did let me instal the drivers and so on. <but when installing drivers i did get somme errors and didn't found some filles i should find and so on..

the modem:
asus aam6000ug (alcatel chipset i guess)

here are somme links i tried to use to help me already: (note: most are in dutch, but maybe somme of you are dutch too ;) )

[http://www.student.montefiore.ulg.ac.be](http://www.student.montefiore.ulg.ac.be) … stall.html
[http://forum.linux.be/index.phtml?nc=&a](http://forum.linux.be/index.phtml?nc=&a) … p;dt=31180
[http://old.netwerk.be/forum/list/messag](http://old.netwerk.be/forum/list/messag) … goto_90756

NOTE: though, i have a working internet connection, i am able to connect trough my lan whit a windows comp and so i have internet connection.

so, if sommeone could help me invery simple noob linux language :):popcorn:

---

### Post by kbentekik on 2007-03-14
Ok, seems no one has been able to help me, 
so here somme mor information

here you see how i tried to make the driver amedyn who was made to work with my modem.

Can anyone help me to say what's wrong?

(i installed a lot of packages which they suggested me.


root@kbentekik-laptop:~# cd /usr/amedyn
root@kbentekik-laptop:/usr/amedyn# make
cd init && make clean
make[1]: Entering directory `/usr/amedyn/init'
rm -f amload amioctl amloaddbg amloaddbgt 
make[1]: Leaving directory `/usr/amedyn/init'
cd module && make clean
make[1]: Entering directory `/usr/amedyn/module'
rm -f *.o .*.flags *.ko *.mod.* .*.o.cmd .*.ko.cmd
make[1]: Leaving directory `/usr/amedyn/module'
cd bridged && make clean
make[1]: Entering directory `/usr/amedyn/bridged'
rm -f br2684ctl 
make[1]: Leaving directory `/usr/amedyn/bridged'
cd amcontrol && make clean
make[1]: Entering directory `/usr/amedyn/amcontrol'
rm -f amcontrol amcontroldbg amcontroldbgt 
make[1]: Leaving directory `/usr/amedyn/amcontrol'
cd init && make && make install
make[1]: Entering directory `/usr/amedyn/init'
gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -Wsign-compare -I../include -lusb  amload.c -o amload
amload.c: In function ‘jump_to_address’:
amload.c:400: warning: pointer targets in passing argument 3 of ‘send_bulk’ differ in signedness
amload.c:405: warning: pointer targets in passing argument 3 of ‘send_bulk’ differ in signedness
amload.c: In function ‘send_cmds_sync’:
amload.c:420: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c:425: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c:430: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c:435: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c:443: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c: In function ‘load_firmware’:
amload.c:513: warning: pointer targets in assignment differ in signedness
amload.c:519: warning: pointer targets in passing argument 3 of ‘send_block’ differ in signedness
amload.c:525: warning: pointer targets in passing argument 3 of ‘send_bulk’ differ in signedness
amload.c:532: warning: pointer targets in passing argument 3 of ‘read_bulk’ differ in signedness
amload.c:547: warning: pointer targets in passing argument 3 of ‘send_block’ differ in signedness
amload.c:551: warning: pointer targets in passing argument 3 of ‘send_bulk’ differ in signedness
amload.c:572: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c:586: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c:603: warning: pointer targets in passing argument 6 of ‘transfer_ctrl_msg’ differ in signedness
amload.c:628: warning: pointer targets in passing argument 3 of ‘usb_bulk_read’ differ in signedness
gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -Wsign-compare -I../include -lusb  amioctl.c -o amioctl
make[1]: Leaving directory `/usr/amedyn/init'
make[1]: Entering directory `/usr/amedyn/init'
install -c -m 755 -p amload amioctl /usr/sbin
make[1]: Leaving directory `/usr/amedyn/init'
cd firmware && make
make[1]: Entering directory `/usr/amedyn/firmware'
install -c -m 644 -p fw-usb.bin Fw-usb_A.bin /usr/sbin
make[1]: Leaving directory `/usr/amedyn/firmware'
cd module && make && make install
make[1]: Entering directory `/usr/amedyn/module'
rm -f xdslusb_2.6.o
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/usr/amedyn/module XDSLUSB-MODULE=amedyn modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /usr/amedyn/module/xdslusb_2.6.o
/usr/amedyn/module/xdslusb_2.6.c:306: error: unknown field ‘owner’ specified in initializer
/usr/amedyn/module/xdslusb_2.6.c:306: warning: initialization from incompatible pointer type
/usr/amedyn/module/xdslusb_2.6.c: In function ‘udsl_usb_disconnect’:
/usr/amedyn/module/xdslusb_2.6.c:1343: warning: implicit declaration of function ‘shutdown_atm_dev’
make[3]: *** [/usr/amedyn/module/xdslusb_2.6.o] Error 1
make[2]: *** [_module_/usr/amedyn/module] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** [normal] Error 2
make[1]: Leaving directory `/usr/amedyn/module'
make: *** [AME_MODULE] Error 2
root@kbentekik-laptop:/usr/amedyn# 
root@kbentekik-laptop:/usr/amedyn# 


Hope someone can help me :confused: :KS

---

### Post by Stetzen on 2007-12-18
You should delete or (it will be detter) comment (put // in the beginning) two lines with "owner" in file /usr/amedyn/modules/xdslusb_2.6.c before compilation

---

