---
title: "Patched hostap driver in Dapper Drake, this is one way"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by waraey on 2006-07-22
I was kinda bummed to find out that there was no patch for the integrated kernel hostap driver that is included. I tried to create one but it got way to messy. I also didnt want to upgrade to kernel 2.6.16 yet, for which there is a patch. After trying many things, I found the following to work and be able to run a patched driver. I'm sure there are some of you out there that know a better method, feel free to show me up!

By the way, this is for cracking wep and use of aircrack-ng with packet injection! Without a patched driver you can't inject packages and crack wep properly.

Step one, get the latest hostap driver and patch.

wget [http://hostap.epitest.fi/releases/hostap-driver-0.4.9.tar.gz](http://hostap.epitest.fi/releases/hostap-driver-0.4.9.tar.gz)
tar -xvzf hostap-driver-0.4.9.tar.gz
cd hostap-driver-0.4.9
wget [http://patches.aircrack-ng.org/hostap-driver-0.4.7.patch](http://patches.aircrack-ng.org/hostap-driver-0.4.7.patch)
patch -Np1 -i hostap-driver-0.4.7.patch

This will patch the lasest driver for packet injection.
Next we will want to use this driver so we need to "fix" the source a little

Remove the following lines of code from these files:
/driver/modules/hostap.c
/driver/modules/hostap_cs.c
/driver/modules/hostap_plx.c
/driver/modules/hostap_pci.c

#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,14))
#error Host AP driver was added into Linux 2.6.14.
#error The version used in the kernel tree should be used instead of this
#error external release which is only maintained for old kernel versions.
#endif

After that has been done, you should be able to sucsessfully compile so run:

make

I would suggest not to run "make install" because we will install it manually.
The first step is to make a folder for our backups
and copy all the modules from /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/hostap for our backup.
If the card is ejected you can then delete all of the modules from: /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/hostap. 

Now that the folder is empty we need to fill it. We will copy all of the *.ko files from hostap-driver-0.4.9/driver/modules and place them in /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/hostap.

As the next step we need the configuration file so copy hostap-driver-0.4.9/driver/etc/hostap_cs.conf to /etc/pcmcia/hostap_cs.conf

At this point I ususally reboot then insert the card.

It will probably work at this point, but when I ran:

dmesg | grep hostap

I recieved an error about WEP and hostap_crypt_wep.o, if you do then run:

depmod -a
ifconfig wlan0 down
ifconfig wlan0 up

Now it should all work and you should be able to connect to the internet and enjoy the benefits of a patched hostap driver.
I have also got a working patched madwifi-old driver if anyone is interested.

---

### Post by k0shi on 2006-08-22
Thanks for that, I was actually able to patch my hostap driver for injection...few problems still remain though that did not before.

When I use Airodump or Kismet, or just about any other such tool, it dosnt see beacons, or collect data, only occasionally will it collect a little bit of data on APs of mine that I know have a lot of traffic. I was able to compile it fine, and install it manually, fine...restarting PCMCIA devices, disconnecting, reconnecting, reloading drivers ( patched ), still, no data. Any ideas? Thanks.

box:~$ uname -r
2.6.15-26-386

---

### Post by markus on 2006-09-01
I was struggling with hostap. My errors doesn't seem to come from problems with kernel version, but with the sources. I got lots of errors about 'dereferencing pointer to incomplete type', syntax errors, undeclared variables, and something more.

I was thinking it must come from a bad version of gcc, could be this? Any clue?

---

### Post by markus on 2006-09-01
Solved! There were problems with the kernel headers. I was using the ubuntu kernel tree 2.6.15 and that didn't work.

Then I installed linux-headers-2.6.15-26-386 which are the ones for de running kernel and compiled cleanly.

---

### Post by yeehawjared on 2006-09-28
hey markus, I'm still having problems installing my hostap drivers.  I have a senao 2511 CD ext2 card which works flawlessly in auditor/BackTrack (pen testing distrobutions)

My goal is to get hostap drivers working so I can packet inject like in BackTrack.

Can you provide details as to how you got the hostap drivers to successfully compile?  Thanks :)

---

### Post by Benadijus on 2006-10-04
I still have problems with hostap and senao 2511 ext2...:(
When I load the hostap driver and run ifconfig...
There is no Wlan0, just Eth2 and Wifi0 (with the same MAC address)...:( 
What I'm doing wrong?

Best Regards,

---

### Post by magnav0x on 2006-10-04
Are Eth2 and Wifi0 showing the mac address of your wireless card?  Sounds normal to me.  How did you switch to hostap drivers on  your Senao 2511 card?  Currently when I run airmon it shows mine as having a HermesI chipset and using the Orinoco drivers.  I would like to switch it to use the hostap drivers, what should I do?

---

### Post by Benadijus on 2006-10-05
Yes. the MAC is senao card...

---

### Post by k0shi on 2006-10-06
To get the Senao card to NOT use Orinoco Drivers, simply black list them.

nano /etc/modprobe.d/blacklist

Code:
blacklist <module name>

I have tryed updating the kernel of my computer, and patching the HostAP drivers, as well as patching the HostAP drivers on the old kernel...they will go into monitor mode and detect ESSIDs and all that, but they will not pick up any incoming data, nor can they inject data....I had better luck trying to collect what I need over the period of a week or two then I did trying to get the HostAP drivers to work on my Prism2.5.........if ANYONE can PLEASE tell us how to get a Prism2.5 on ubuntu with HostAP drivers to actually support Packet Injection....we'd love ya' to death. Thanks

---

### Post by DarkAngel88 on 2006-11-16
Hi, 

Sorry to bring back this thread but I'm wondering if there is any way I can get this method working under Edgy ??  I have a weird error when I try the "make" command.

Any help would be very appreciated !!

Thanks

---

### Post by aluche2003 on 2006-11-19
Hi.

Same for me. In Edgy, when type make it appears as follows:

root@xxxxxxx:~/hostap-driver-0.4.9# make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/root/hostap-driver-0.4.9/driver/modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /root/hostap-driver-0.4.9/driver/modules/hostap.o
In file included from /root/hostap-driver-0.4.9/driver/modules/hostap.c:110:
/root/hostap-driver-0.4.9/driver/modules/hostap_ap.c:20: error: expected ‘)’ before string constant
/root/hostap-driver-0.4.9/driver/modules/hostap_ap.c:25: error: expected ‘)’ before string constant
/root/hostap-driver-0.4.9/driver/modules/hostap_ap.c:30: error: expected ‘)’ before string constant
/root/hostap-driver-0.4.9/driver/modules/hostap_ap.c:35: error: expected ‘)’ before string constant
make[2]: *** [/root/hostap-driver-0.4.9/driver/modules/hostap.o] Error 1
make[1]: *** [_module_/root/hostap-driver-0.4.9/driver/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [2.6] Error 2

Hope that somebody can help me.

Thanks.

---

### Post by DarkAngel88 on 2006-11-27
Hmmm.. I can't believe that nobody tried to patch their hostap drivers under edgy !!   Please help us, Edgy users !

---

### Post by yeehawjared on 2006-12-02
yup, i'm in edgy and having problems too.  Have any edgy users successfully installed the newest hostap drivers?  here's my error:

root@jaredtop:/home/jared/hostap/hostap-driver-0.4.9# make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/jared/hostap/hostap-driver-0.4.9/driver/modules \
                MODVERDIR=/home/jared/hostap/hostap-driver-0.4.9/driver/modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
scripts/Makefile.build:17: /home/jared/hostap/hostap-driver-0.4.9/driver/modules/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/jared/hostap/hostap-driver-0.4.9/driver/modules/Makefile'.  Stop.
make[1]: *** [_module_/home/jared/hostap/hostap-driver-0.4.9/driver/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [2.6] Error 2
root@jaredtop:/home/jared/hostap/hostap-driver-0.4.9#

---

### Post by hansworst on 2006-12-16
and I have got the same errors:

make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/wouter/hostap-driver-0.4.9/driver/modules \
                MODVERDIR=/home/wouter/hostap-driver-0.4.9/driver/modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
scripts/Makefile.build:17: /home/wouter/hostap-driver-0.4.9/driver/modules/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/wouter/hostap-driver-0.4.9/driver/modules/Makefile'.  Stop.
make[1]: *** [_module_/home/wouter/hostap-driver-0.4.9/driver/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [2.6] Error 2

PLEASE HELP!!

---

### Post by yeehawjared on 2006-12-17
do this to get hostap working:

[http://ubuntuforums.org/showthread.php?p=1881943](http://ubuntuforums.org/showthread.php?p=1881943)


compile a newer kernel... hostap packet injection works great on my senao card.,

---

