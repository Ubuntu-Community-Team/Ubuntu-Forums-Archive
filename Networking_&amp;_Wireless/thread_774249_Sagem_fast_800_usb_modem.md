---
title: "Sagem fast 800 usb modem"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by oapjonboy on 2008-04-29
I have just installed ubuntu 8 on my old PC.  Installation went as sweet as a nut, no problems.
I would now like to install my Sagem Fast800 usb modem so as I can go on the Internet.  I have visited the Sagem site and downloaded the Linux driver, but have no idea what to do next.
It doesn't seem so easy to install hardware on Linux as it does in XP.

I thought I would try Linux just to give my old brain something to do.  Thanks in anticipation.

---

### Post by chili555 on 2008-04-29
How about giving us a link to the driver and we'll see if we can help.

---

### Post by oapjonboy on 2008-04-29
[http://www.sagem.com/support/site/modele_fax.php?page=driver](http://www.sagem.com/support/site/modele_fax.php?page=driver)

I hope this helps.
Thanks for your help.

---

### Post by chili555 on 2008-04-29
Ah! eagle! Have a look here: [https://help.ubuntu.com/community/UsbAdslModem/EagleUsb](https://help.ubuntu.com/community/UsbAdslModem/EagleUsb)  especially this:> It is highly recommended that you use the ueagle-atm driver instead if you are running Edgy or newerVersion 8.08, which you installed, is newer by three than Edgy. I would plug that Sagem in and then open a terminal and do:```
sudo modprobe ueagle-atm
```Did your modem spring to life?

---

### Post by vnevoa on 2008-04-30
You are unfortunate enough to have one of the shittiest modems in existence. I know, because I have it too. ;)

The first thing you must find out is your ISP details (VPI,VCI, and mode: PPPoATM or PPPoEth). Go here:
[http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL](http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL)

It is not easy to get it working, but it is not extremely difficult either.
There are many pages and threads that teach you how to do this, but the one I think is the best so far is this:
[http://ubuntuforums.org/showpost.php?p=2548455&postcount=3](http://ubuntuforums.org/showpost.php?p=2548455&postcount=3)
It configures the access in PPPoATM mode.

In a nutshell, it goes like this: you don't need any new driver, Ubuntu already has the one you need (in principle). What you need is:
1 - to prepare the firmware;
2 - to prepare the ppp scripts for automatic dialing;
3 - to change your networking to call the automatic dialing of the modem.
All of which are described in the above post.

If it doesn't work for you, try the other post:
[http://ubuntuforums.org/showpost.php?p=4402171&postcount=32](http://ubuntuforums.org/showpost.php?p=4402171&postcount=32)
It presents 2 scripts that automatically setup the modem - one for PPPoEth and another for PPPoATM. I haven't tried them, but I will.

Good luck!

---

### Post by chili555 on 2008-04-30
Isn't this supposed to be a family friendly forum?

---

### Post by zenza on 2008-05-30
I have a fresh Hardy Heron (2.6.24.16) installation.
I use a sagem fast 800 E3 usb modem. 

I use graphic installation which is discrib here : [http://doc.ubuntu-fr.org:81/modem_sagem_fast_800](http://doc.ubuntu-fr.org:81/modem_sagem_fast_800). The installation is complete but there is no connexion with firefox or ifconfig.

In starting of ubuntu :
```
firmware_helper[3971]main error loading /lib/firmware/ueagle-atm/CMVep.bin.V2 for device /pci0000:00/0000:00:07.2 /usb1/1-2/firmware/1-2 with the driver (unknown)
```

Then, it stay with no limit in :
```
 * configuring network interfaces...
```
I must unplug the modem to continue...  
```
[] usb 1-2 [UEGLE-ATM] uea_int()failed with -84
[] usb 1-2 [UEGLE-ATM] ush control-msg error
```
and the login scream appear.

In gnome there are no connexion posssible.

Can you help me ?



In extra, maybe util

$ cat /etc/network/interfaces :
> auto lo
iface lo inet loopback

auto ppp0
iface ppp0 inet ppp
pre-up /etc/usbatm-iface/usbatm-updown $IFACE
provider adslusb
$ sudo ifup ppp0
> ppp0: ERROR while getting interface flags: No such device
Plugin pppoatm.so loaded.
Using interface ppp0
Connect: ppp0 <--> 8.35
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
and some element of**$ dmesg**
> [  482.555580] usb 1-2: [ueagle-atm] ATU-R firmware version : 44e2ea17
[  482.562087] usb 1-2: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
[  482.634004] usb 1-2: [Ueagle-atm] use deprecated cmvs version, please update your firmware
[  482.668349] usb 1-2: [ueagle-atm] modem started, waiting synchronization...


[ 1271.629182] usb 1-2: [ueagle-atm] modem operational

---

### Post by chili555 on 2008-05-30
It seems, at a minimum, that it cannot find les firmwares. Did you get down to this step in the page you referenced?> Les Firmwares

L'installation des Firmwares se fait de la façon suivante :

    *
      Décompression de l'archive ueagle-data-1.1.tar.gz :

      cp /làoùsetrouvelefichier/ueagle-data-1.1.tar.gz /tmp && cd /tmp
      tar -zxvf ueagle-data-1.1.tar.gz

    *
      Création du répertoire /lib/firmware/ueagle-atm et copie des modules :

      sudo mkdir /lib/firmware/ueagle-atm
      cd ueagle-data-1.1
      sudo cp -a * /lib/firmware/ueagle-atm

Pour la plupart des FAI (fournisseurs d'accès internet), l'installation des firmwares ne pose pas de problèmes, cependant, si vous rencontrez des difficultés à ce niveau, jetez un œil ici : [http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc](http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc) Exemple : pour Wanadoo/Orange en France, 8.35 

---

### Post by zenza on 2008-05-31
The firmware allready installed :

> utilisateur@ordi:/lib/firmware/ueagle-atm$ ls
930-fpga.bin  CMVeiWO.bin    CMVepFR10.bin  DSP9p.bin   eagleIII.fw
adi930.fw     CMVep.bin      CMVepFR.bin    DSPei.bin
CMV9i.bin     CMVepES03.bin  CMVepIT.bin    DSPep.bin
CMV9p.bin     CMVepES.bin    CMVepWO.bin    eagleI.fw
CMVei.bin     CMVepFR04.bin  DSP9i.bin      eagleII.fw

But there isn't CMVep.bin.V2 in /lib/firmware/ueagle-atm and it's not in ueagle-data-1.1.tar.gz

I search about CMVep.bin.V2, I found some incomprensible explain. 
Maybe it just need to add this file. 
Some body have this file ??? 

**$ dmesg | grep ueagle**
> [ 2713.829925] [ueagle-atm] driver ueagle 1.4 loaded
[ 2713.830035] usb 1-2: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9031) Rev (0X200B): Eagle III
[ 2714.150300] usb 1-2: [ueagle-atm] using iso mode
[ 2714.160200] usb 1-2: [ueagle-atm] (re)booting started
[ 2714.163147] usbcore: registered new interface driver ueagle-atm
[ 2717.765218] usb 1-2: [ueagle-atm] ATU-R firmware version : 44e2ea17
[ 2717.769496] usb 1-2: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
[ 2717.831058] usb 1-2: [ueagle-atm] modem started, waiting synchronization...
[ 2728.835335] usb 1-2: [ueagle-atm] modem operational
[ 8277.940743] usb 1-2: [ueagle-atm] ADSL device removed

---

