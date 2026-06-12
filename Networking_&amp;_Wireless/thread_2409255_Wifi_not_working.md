---
title: "Wifi not working"
date: 2018-12-30
forum: Networking &amp; Wireless
---

### Post by edrisnpv on 2018-12-30
okay so im new new to ubuntu and installed it on my dell inspiron 6400 [mm061] 
Everyting was fine untill i wanted to connect to wifi
there was no wifi on networks
//my wlan card is broadcom 4311 (rev-01)


```
 
##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Limited BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44

0b:00.0 Network controller [0280]: Broadcom Limited BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

```

attached my wifi info
[ATTACH]282048[/ATTACH]

---

### Post by wildmanne39 on 2018-12-30
Please do:
```
sudo apt purge bcmwl-kernel-source 
```
Then:
```
sudo apt install firmware-b43-installer
```
Reboot

---

### Post by edrisnpv on 2018-12-30
Sorry man still no wifi ](*,)
                                       ](*,)

---

### Post by wildmanne39 on 2018-12-30
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by edrisnpv on 2018-12-30
im stuck like 2 days:mad:

link is not working for me

---

### Post by wildmanne39 on 2018-12-30
What link is not working? the one in my signature that says wireless script works for me, it is the same one you posted earlier just run it again and post the new results so we can see the changes since you removed the wrong driver and installed the correct one.

---

### Post by edrisnpv on 2018-12-30
[http://paste.ubuntu.com/p/sbvBKQDmnb/](http://paste.ubuntu.com/p/sbvBKQDmnb/)

---

### Post by wildmanne39 on 2018-12-30
Did you reboot the computer? if so please run those commands again and post the output because the changes have not taken effect.

Thanks

---

### Post by edrisnpv on 2018-12-30
[http://paste.ubuntu.com/p/jp7P58b7PR/](http://paste.ubuntu.com/p/jp7P58b7PR/)

---

### Post by jeremy31 on 2018-12-30
Post results for ```
dkms status; dpkg -l | grep -i broadcom
```

---

### Post by wildmanne39 on 2018-12-30
Did you reboot the computer? if so please run those commands again and post the output from the commands you ran, we need to see output from the commands to see if the commands failed.

---

### Post by edrisnpv on 2018-12-30
yea man i did

bcmwl, 6.30.223.271+bdcom, 4.15.0-43-generic, i686: installed
ndiswrapper, 1.60, 4.15.0-43-generic, i686: installed
ii  b43-fwcutter                          1:019-3                             i386         utility for extracting Broadcom 43xx firmware
ii  bcmwl-kernel-source                   6.30.223.271+bdcom-0ubuntu4         i386         Broadcom 802.11 Linux STA wireless driver source

---

### Post by jeremy31 on 2018-12-30
```
sudo apt purge bcmwl-kernel-source && shutdown -r now
```

Then see if it works

---

### Post by wildmanne39 on 2018-12-30
I am going to back out and let jeremy31 help you because I have to leave for a little while.

---

### Post by edrisnpv on 2018-12-30
ok, tnx alot

---

### Post by edrisnpv on 2018-12-30
Nothing, no wifi 
want to send another Wireless-lnfo?

---

### Post by jeremy31 on 2018-12-30
yes ```
./wireless-info && cat wireless-info.txt | pastebin; dkms status
```

---

### Post by edrisnpv on 2018-12-30
[http://paste.ubuntu.com/p/6fCGXGvM6p/](http://paste.ubuntu.com/p/6fCGXGvM6p/)

---

### Post by edrisnpv on 2018-12-30
pastebin: command not found
ndiswrapper, 1.60, 4.15.0-43-generic, i686: installed
edris_npv@EdrisNPV-Laptop:~$ 
this showed up after the link

---

### Post by jeremy31 on 2018-12-30
```
sudo apt install firmware-b43-installer
```
Reboot

---

### Post by edrisnpv on 2018-12-30
it was already installed
rebootin anyway now

---

### Post by edrisnpv on 2018-12-30
it was already installed
rebootin anyway now

---

### Post by praseodym on 2018-12-30
Check the "dmesg" output. The missing firmware is not part of that package anymore (afaik). Use this one instead

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by jeremy31 on 2018-12-30
It is still part of firmware-b43-installer, it was removed 4 years ago from linux-firmware-nonfree

---

### Post by edrisnpv on 2018-12-30
again nothing

---

### Post by edrisnpv on 2018-12-30
im so confused,
there has to be a way

---

### Post by jeremy31 on 2018-12-30
It should work ```
locate ucode5.fw; dpkg -l | grep -i broadcom
```

---

### Post by edrisnpv on 2018-12-30
reboot? nuthing happened

---

### Post by jeremy31 on 2018-12-30
Post results for that command

---

### Post by edrisnpv on 2018-12-30
[http://paste.ubuntu.com/p/dMW67gr6JJ/](http://paste.ubuntu.com/p/dMW67gr6JJ/)

---

### Post by jeremy31 on 2018-12-30
Try a shutdown and then boot

---

### Post by wildmanne39 on 2018-12-30
Jeremy31, I am just here for a minute but I am wondering is the compat module causing an issue, it has not been used in a long time, I believe it is now in the backports so why is it listed?

---

### Post by jeremy31 on 2018-12-30
compat is actually part of backports, wildmanne39,  I know where it is from now, thanks
edrisnpv
```
cd backport-iwlwifi
sudo make uninstall
```
Reboot

---

### Post by edrisnpv on 2018-12-30
okay? done! still no wifi
 		 			 				:frown:

---

### Post by jeremy31 on 2018-12-30
New script results, please

---

### Post by edrisnpv on 2018-12-31
[http://paste.ubuntu.com/p/pDKRDSxPrR/](http://paste.ubuntu.com/p/pDKRDSxPrR/)

---

### Post by edrisnpv on 2018-12-31
jeremy31, tnx alot man just saw it now after a  shutdown, my wifi works fine

---

### Post by edrisnpv on 2018-12-31
but my screen brightness is still low even after setting it to high,
if i couldnt fix it i will post it on another thread

---

### Post by balalrumy on 2019-01-07
I also faced the same issue with braodcom card but finally i changed my card to ASUS USB AC68 dual Band AC1900 which is [best wifi card](https://technicalustad.com/best-wifi-card-for-pc/) and it's perfectly working fine on ubuntu and windows also.

---

