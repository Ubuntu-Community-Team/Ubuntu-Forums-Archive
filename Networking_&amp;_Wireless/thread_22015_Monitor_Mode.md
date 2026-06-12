---
title: "Monitor Mode"
date: 2005-03-25
forum: Networking &amp; Wireless
---

### Post by somuchfortheafter on 2005-03-25
I have kernel 2.6.10-5-386 and a smc wireless card(SMC2532W-B) anyway I added the orinoco patch to allow monitor mode on the card so I can use kismet, however I seem to be having a bit of trouble. I enter in the following:
```
thanatosys@darkstar:~$ sudo ifconfig eth2 down
thanatosys@darkstar:~$ sudo iwconfig eth2 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Invalid argument.
``` 
And yes I have checked that the card is set to eth2 and I have tried it being disabled and enabled in the gnome network monitor but the problem still persists. Any ideas?

---

### Post by wernst on 2005-03-25
Hi.

I wrote the Orinoco Patch Howto over in the Warty Forums.

I quickly tried it myself in hoary and I get the same thing as you (of course, I have a genuine Orinoco card. I don't know about the SMC card...)

I might look into it this weekend, but in all likelihood, I'm going to wait until after Hoary is final before diving in.

Of course, I've certianly not an expert; just a good troulshooter. If someone else has an idea or wants to make it work, that would be grand...

-Warr

---

### Post by somuchfortheafter on 2005-03-25
i was thinking it was a driver issue but if you have the real card idk....

---

### Post by sMell on 2005-03-29
Try iwpriv instead of iwconfig for setting monitor mode...

---

### Post by somuchfortheafter on 2005-03-29
that still doesnt work :(

---

### Post by somuchfortheafter on 2005-03-29
also now during the process of running make i get this
```

root@darkstar:~/extras/orinoco-0.15rc2# make
make -C /usr/src/linux-headers-2.6.10-5-386 M=/home/thanatosys/extras/orinoco-0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.o
In file included from /home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c:117:/home/thanatosys/extras/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/home/thanatosys/extras/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_cor_reset':
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c:158: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c:164: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c:171: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c:174: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_suspend':
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/home/thanatosys/extras/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/home/thanatosys/extras/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [modules] Error 2

```
any ideas??

---

### Post by sMell on 2005-03-30
[QUOTE=somuchfortheafter]also now during the process of running make i get this
...
any ideas??[/QUOTE]

I believe they changed various interfaces in 2.6.9

Try the 26 driver for 2.6.9+ here: [http://www.kismetwireless.net/code/orinoco-0.13-26-r1.tar.gz](http://www.kismetwireless.net/code/orinoco-0.13-26-r1.tar.gz)

---

### Post by somuchfortheafter on 2005-03-30
well still a compilation problem.. could it be that there is no 2.6.10 file yet? anyway here is the error
```

thanatosys@darkstar:~/extras/orinoco-0.13-26$ sudo make install
make -C /usr/src/linux-headers-2.6.10-5-386 M=/home/thanatosys/extras/orinoco-0.13-26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
mkdir -p /etc/pcmcia
install -m 644 -o 0 -g 0 hermes.conf /etc/pcmcia/hermes.conf
install: cannot stat `hermes.conf': No such file or directory
make: *** [installconf] Error 1

```
obviously there is no hermes.conf file but im still lost on where it could have been?

---

### Post by sMell on 2005-03-30
[QUOTE=somuchfortheafter]
obviously there is no hermes.conf file but im still lost on where it could have been?[/QUOTE]

Sounds like a bug in the package.  Try this in the driver directory, which will back up all the orinoco drivers in hte kernel and install the ko files in place

```

for x in *.ko; do 
  mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/$x{,~} && mv $x /lib/modules/`uname -r`/kernel/drivers/net/wireless/$x
done
depmod -a

```

---

### Post by somuchfortheafter on 2005-03-30
ok this is becomming a bother in itself? wonder if it would be worth it to create a seporate directory with a warty install and just chroot into it.... that would be a bit of work, anyway new error is:
```
 
thanatosys@darkstar:~/extras/orinoco-0.13-26$ for x in *.ko; do
> sudo  mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/$x{,~} && mv $x /lib/modules/`uname -r`/kernel/drivers/net/wireless/$x
> done
mv: cannot move `hermes.ko' to `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/hermes.ko': Permission denied
mv: cannot move `orinoco_cs.ko' to `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/orinoco_cs.ko': Permission denied
mv: cannot move `orinoco.ko' to `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/orinoco.ko': Permission denied
mv: cannot move `orinoco_pci.ko' to `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/orinoco_pci.ko': Permission denied
mv: cannot move `orinoco_plx.ko' to `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/orinoco_plx.ko': Permission denied
mv: cannot move `orinoco_tmd.ko' to `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/orinoco_tmd.ko': Permission denied

```

---

### Post by sMell on 2005-03-30
[QUOTE=somuchfortheafter]ok this is becomming a bother in itself? wonder if it would be worth it to create a seporate directory with a warty install and just chroot into it.... that would be a bit of work, anyway new error is:
[/QUOTE]

Sorry, should have put the sudo in myself.  You need two, one for each mv.  && ties the two commands together so that if the first one fails, the second one doesn't run...so if those backups were already made... you ge tthe drift.

---

### Post by somuchfortheafter on 2005-03-30
i removed the previous error by manually moving the .ko files into the specfied directory, all  is well now with that however whenever i run make install i get this
```

thanatosys@darkstar:~/extras/orinoco-0.13-26$ sudo make install
make -C /usr/src/linux-headers-2.6.10-5-386 M=/home/thanatosys/extras/orinoco-0.13-26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
mkdir -p /etc/pcmcia
install -m 644 -o 0 -g 0 hermes.conf /etc/pcmcia/hermes.conf
install: cannot stat `hermes.conf': No such file or directory
make: *** [installconf] Error 1

```
obviously i lack the hermes.conf file
i did a scan of my filesystem for it and well i cannot find it. sMell would it be possible for you to post yours and its location and then i shall add it to mine and see if it works?

---

### Post by sMell on 2005-03-31
[QUOTE=somuchfortheafter]obviously i lack the hermes.conf file
i did a scan of my filesystem for it and well i cannot find it. sMell would it be possible for you to post yours and its location and then i shall add it to mine and see if it works?[/QUOTE]

I don't have one myself.  Not sure what it's for actually---haven't heard of a kernel module with a configuration file.  If you have those .ko files that it made installed, you should have monitor mode.

---

### Post by somuchfortheafter on 2005-03-31
well here is the latest in my saga for monitor mode
```

thanatosys@darkstar:~$ iwpriv
lo        no private ioctls.

eth0      Available private ioctl :
          set_power        (8BE0) : set   1 int   & get   0
          get_power        (8BE1) : set   0       & get  80 char
          set_mode         (8BE2) : set   1 int   & get   0
          get_mode         (8BE3) : set   0       & get  80 char

eth1      no private ioctls.

sit0      no private ioctls.

eth2      Available private ioctl :
          force_reset      (8BE0) : set   0       & get   0
          card_reset       (8BE1) : set   0       & get   0
          set_port3        (8BE2) : set   1 int   & get   0
          get_port3        (8BE3) : set   0       & get   1 int
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get   1 int
          set_ibssport     (8BE6) : set   1 int   & get   0
          get_ibssport     (8BE7) : set   0       & get   1 int
          dump_recs        (8BFF) : set   0       & get   0

thanatosys@darkstar:~$ man iwpriv
Reformatting iwpriv(8), please wait...

[1]+  Stopped                 man iwpriv
thanatosys@darkstar:~$ sudo iwconfig eth2 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Invalid argument.
thanatosys@darkstar:~$ sudo iwpriv eth2 8BO6
Invalid command : 8BO6
thanatosys@darkstar:~$

```
well im guessing i would need to see monitor mode and it would have 8B06 near it, however as you can see i do not. would those .diff files have anything to do with the reason this is failing.

---

### Post by jshein on 2005-04-02
I have it working perfectly as of today.

I am running with universe sources enabled in /etc/apt/sources.list

All commands need to be done as root

Install kismet
# wget http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.01.R1-2_i386.deb
# apt-get install ethereal-common
# dpkg -i kismet_2005.01.R1-2_i386.deb

Install the kernel sources
# apt-get install linux-source-2.6.10

go to the /usr/src directory
# cd /usr/src

extract the kernel-source
# bunzip2 linux-source-2.6.10.tar.bz2
# tar -xvf linux-source-2.6.10.tar

make a link to the kernel source
# ln -s /usr/src/linux-source-2.6.10 /usr/src/linux

cd to the source dir
# cd /usr/src/linux

get the monitor mode patch
# wget http://www.kismetwireless.net/code/orinoco-2.6.9-rfmon-dragorn-1.diff

patch the kernel-source
# patch -p1 --dry-run < ./orinoco-2.6.9-rfmon-dragorn-1.diff

and if no errors appear
# patch -p1 < ./orinoco-2.6.9-rfmon-dragorn-1.diff

Make a directory to backup the existing drivers.
# mkdir /orinoco

Move orinoco drivers to backup location
# mv /lib/modules/2.6.10/kernel/drivers/net/wireless/orinoco* /orinoco
# mv /lib/modules/2.6.10/kernel/drivers/net/wireless/hermes.ko /orinoco

copy the config file to the source directory
# cp /boot/config-2.6.10-5-386 /usr/src/linux/.config

compile the modules
# make modules
# make modules_install

copy the new modules to the proper directory
# cp /usr/src/linux/drivers/net/wireless/orinoco*ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/

# cp /usr/src/linux/drivers/net/wireless/hermes.ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/

edit /etc/kismet/kismet.conf for your card
use orinoco,eth1,orinocosource

enjoy

---

### Post by somuchfortheafter on 2005-04-23
dude im gonna try this.. and if it works, you are officially the worlds most awesome person ever

---

