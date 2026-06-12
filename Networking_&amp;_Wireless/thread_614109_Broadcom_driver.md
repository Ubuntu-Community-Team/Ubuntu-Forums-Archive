---
title: "Broadcom driver"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by Angelbeast on 2007-11-15
I have a broadcom card that i had to use the ndiswrapper with. But now i see in 7.10 some "firmware" is included in the restricted driver manager. Does that take the place of ndis? And if so does it work well?if i canuse that without ndis i would like to try it because i believe that i am having issues with ndis.

---

### Post by NullHead on 2007-11-15
You can still use ndiswrapper if you install he firmware. I never use the firmware because it's allot slower then ndiswrapper. You might want to see if your device is supported first. Check hear [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

---

### Post by kevdog on 2007-11-15
The built in bcm43xx driver in terms of performance is not better than ndiswrapper, at it does not support all broadcom cards.  Just a suggestion which you can take it or leave it --- stay with ndiswrapper.  Its kind of a pain to setup but its very reliable.

---

### Post by Angelbeast on 2007-11-15
have either of you herd of ndiswrapper causing lockups, or causing internet traffic to 'freeze'?

---

### Post by Angelbeast on 2007-11-15
> **NullHead said:**
> You can still use ndiswrapper if you install he firmware. I never use the firmware because it's allot slower then ndiswrapper. You might want to see if your device is supported first. Check hear [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

Now ho do i tell which device i have or which chip set? i don't remember *LOL*

---

### Post by NullHead on 2007-11-15
I agree use ndiswrapper. You can check you're card model number by using the following.```
lspci | grep Broadcom
``` Mine looks like this.> 01:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Angelbeast on 2007-11-15
> **NullHead said:**
> I agree use ndiswrapper. You can check you're card model number by using the following.```
lspci | grep Broadcom
``` Mine looks like this.

I have the same thing...I don't mind ndiswrapper but i think i may be having issues with it since upgrading to gutsy...have you heard of anyone having their internet traffic just 'freeze' until they reboot? I've also been having hard lockups since feisty and sometimes when i look at the syslog right after a crash it says something about incorrect buffer size for ndis right at the time of the lockup...

---

### Post by kevdog on 2007-11-15
Rather than blaming ndiswrapper, I would check that there isnt a different Windows XP 64 bit driver available for your card.

---

### Post by Angelbeast on 2007-11-15
> **kevdog said:**
> Rather than blaming ndiswrapper, I would check that there isnt a different Windows XP 64 bit driver available for your card.

Hi...Well i did find this:

[http://fedoramobile.org/fc-wireless/hpsp33008.tar.gz/view](http://fedoramobile.org/fc-wireless/hpsp33008.tar.gz/view)

That is version 4 though and the current one on the HP site is version 6. I wouldn't have any idea where else to look...

---

### Post by Angelbeast on 2007-11-16
does anyone know if there IS anywhere i could find a 64 bit version if the river?

---

### Post by Angelbeast on 2007-11-16
driver even *LOL*

---

### Post by NullHead on 2007-11-16
OK hear is a 64bit ndiswrapper driver. 

[http://ubuntuforums.org/attachment.php?attachmentid=44622&d=1190994539](http://ubuntuforums.org/attachment.php?attachmentid=44622&d=1190994539)

Do you know how to install the driver?

---

### Post by Angelbeast on 2007-11-16
> **NullHead said:**
> OK hear is a 64bit ndiswrapper driver. 

[http://ubuntuforums.org/attachment.php?attachmentid=44622&d=1190994539](http://ubuntuforums.org/attachment.php?attachmentid=44622&d=1190994539)

Do you know how to install the driver?

can i just replace the inf file or do i hve to remove everything and start over from scratch?

thjanks for the link too by the way  :-)

---

### Post by NullHead on 2007-11-16
Well what I would do is just look at whats installed and remove whats in the list. ```
ndiswrapper -l
sudo ndiswrapper -e 'driver name'
```
Then I would install the drivers I linked to.
```
sudo ndiswrapper -i 'pathname to new driver'
``` 
And the register the driver```
sudo ndiswrapper -m
```
Then modprobe the ndiswrapper and stop bcm43xx from loading
```
sudo modprobe ndiswrapper
sudo rmmod bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
then you should be all set.

---

### Post by Angelbeast on 2007-11-16
> **NullHead said:**
> Well what I would do is just look at whats installed and remove whats in the list. ```
ndiswrapper -l
sudo ndiswrapper -e 'driver name'
```
Then I would install the drivers I linked to.
```
sudo ndiswrapper -i 'pathname to new driver'
``` 
And the register the driver```
sudo ndiswrapper -m
```
Then modprobe the ndiswrapper and stop bcm43xx from loading
```
sudo modprobe ndiswrapper
sudo rmmod bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
then you should be all set.

okay do i need to extract the driver files before i do any of this?

---

### Post by Angelbeast on 2007-11-16
actully how do i see if i don't actually already have the 64 bitdriver installed?

---

### Post by NullHead on 2007-11-16
Yes you need to extract it first and the driver I gave you is the correct one and it won't hurt if you uninstall the one in question. It's painless and won't hurt a thing. But if you look at ndiswrapper -l it should tell you if it's working correctly.

---

### Post by Angelbeast on 2007-11-16
> **NullHead said:**
> Yes you need to extract it first and the driver I gave you is the correct one and it won't hurt if you uninstall the one in question. It's painless and won't hurt a thing. But if you look at ndiswrapper -l it should tell you if it's working correctly.

i started to give it a try and i got his...

ron@ron-laptop:~$ sudo ndiswrapper -e bcm43xx
couldn't delete /etc/ndiswrapper/bcm43xx: No such file or directory

---

### Post by NullHead on 2007-11-16
OK well please show me you output from ndiswrapper -l ... and we'll go from there.

---

### Post by Angelbeast on 2007-11-16
> **NullHead said:**
> OK well please show me you output from ndiswrapper -l ... and we'll go from there.

Okay here you go...

bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

i think maybe i put in the wrong thing for the driver?

---

### Post by NullHead on 2007-11-16
OK well it looks like you have *A* driver installed, but I'm not sure if it's the correct one. so you will remove it then install the new ones. ```
sudo ndiswrapper -e bcmwl5
``` and install the new ones```
sudo ndiswrapper -i 'path to new driver'
``` Then we need to configure it. ```
sudo modprobe ndiswrapper
sudo rmmod bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 
```

---

### Post by scrooge_74 on 2007-11-16
There is also a new linux native driver for broadcom it is working on this laptop 

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by Angelbeast on 2007-11-16
> **NullHead said:**
> OK well it looks like you have *A* driver installed, but I'm not sure if it's the correct one. so you will remove it then install the new ones. ```
sudo ndiswrapper -e bcmwl5
``` and install the new ones```
sudo ndiswrapper -i 'path to new driver'
``` Then we need to configure it. ```
sudo modprobe ndiswrapper
sudo rmmod bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 
```

kaygotcha...now one more stupid question before i give it another go...for path to driver i would put the path right to the if file in the new unpacked driver folder?

---

### Post by Angelbeast on 2007-11-16
> **scrooge_74 said:**
> There is also a new linux native driver for broadcom it is working on this laptop 

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

es but at the moment it's unstable for the 4318 chipset...i saw it in the restricted driver manager...i can't wait till it finally works *LOL*

---

### Post by Angelbeast on 2007-11-17
> **NullHead said:**
> OK well it looks like you have *A* driver installed, but I'm not sure if it's the correct one. so you will remove it then install the new ones. ```
sudo ndiswrapper -e bcmwl5
``` and install the new ones```
sudo ndiswrapper -i 'path to new driver'
``` Then we need to configure it. ```
sudo modprobe ndiswrapper
sudo rmmod bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 
```

Okay i got it all sorted out and it's all installed now...so yeah i was thinking the driver i had originally installed was from my windows dosk which was 32 bit...could something like that possibly be the culprit in causing lockups and internet traffic freezing?

---

### Post by Angelbeast on 2007-11-17
alright well i just got my answer about the hard lockups *LOL* ... i can't believe that NO NE has found a solution for that yet...

---

### Post by Angelbeast on 2007-11-17
well it seems that i have my answer on the internet traffic freezing as well...i did check the logs out and found this for around the time it occured...

messages

Nov 17 04:47:16 ron-laptop kernel: [10242.990680]  [sys_ioctl+149/176] sys_ioctl+0x95/0xb0
Nov 17 04:47:16 ron-laptop kernel: [10242.990688]  [system_call+126/131] system_call+0x7e/0x83
Nov 17 04:47:16 ron-laptop kernel: [10242.990699] 
Nov 17 04:47:38 ron-laptop kernel: [10264.584607] Inbound IN=eth1 OUT= MAC=01:00:5e:7f:ff:fa:00:1c:10:9d:76:2e:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=312 TOS=0x00 PREC=0x00 TTL=1 ID=46888 PROTO=UDP SPT=4439 DPT=1900 LEN=292 
Nov 17 04:47:38 ron-laptop kernel: [10264.587690] Inbound IN=eth1 OUT= MAC=01:00:5e:7f:ff:fa:00:1c:10:9d:76:2e:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=321 TOS=0x00 PREC=0x00 TTL=1 ID=46890 PROTO=UDP SPT=4440 DPT=1900 LEN=301 




syslog

Nov 17 05:03:16 ron-laptop kernel: [11161.336021] APIC error on CPU0: 40(40)
Nov 17 05:03:31 ron-laptop init: tty4 main process (4307) killed by TERM signal
Nov 17 05:03:31 ron-laptop init: tty5 main process (4308) killed by TERM signal
Nov 17 05:03:31 ron-laptop init: tty2 main process (4312) killed by TERM signal
Nov 17 05:03:31 ron-laptop init: tty3 main process (4313) killed by TERM signal
Nov 17 05:03:31 ron-laptop init: tty1 main process (4314) killed by TERM signal
Nov 17 05:03:31 ron-laptop init: tty6 main process (4315) killed by TERM signal
Nov 17 05:03:33 ron-laptop avahi-daemon[5212]: Got SIGTERM, quitting.
Nov 17 05:03:34 ron-laptop avahi-daemon[5212]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.105.




kern.log

Nov 17 04:47:16 ron-laptop kernel: [10242.990267] note: NetworkManager[4835] exited with preempt_count 1
Nov 17 04:47:16 ron-laptop kernel: [10242.990272] BUG: scheduling while atomic: NetworkManager/0x10000001/4835
Nov 17 04:47:16 ron-laptop kernel: [10242.990274] 
Nov 17 04:47:16 ron-laptop kernel: [10242.990275] Call Trace:

Does anyone at all ave any ideas about this? it JUST started when i upgraded to Gutsy...

Well if you will excuse me now i a going to go vent my frustration and kick something...grrrr...

---

