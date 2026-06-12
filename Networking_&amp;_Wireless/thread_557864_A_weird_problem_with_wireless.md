---
title: "A weird problem with wireless"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by johndoeee on 2007-09-23
Hello. I am new to Ubuntu and Linux environment but I have made a great headway , so far.
But one problem still doesnt go away.

I have tried all third party programs but there is always a problem with them too. I will list them.


My problem is i Cannot connect to wireless. I can see the list of wirelesses but i cannot connect any of them. I tried Kwifimanager (which i had already used before) but it says no access point and though i see my wireless i cannot click switch to wireless button.

other wireless connection programs give somewhat similar errors.

I wrote iwconfig to terminal and here is what i got in response.

lo no wireless extensions

eth0 no wireless extensions

eth1 unassociated ESSID:"y&#305;ld&#305;r&#305;m"
          mode: managed frequency:nan khz access point : not associated
          bit rate: o kb/s tx-power:16 dbm
          retry limit:15  rts thr:off fragmentthr:off
          power management:off
          link quality:0 signal level:0 noise level:0
          rx invalid nwid:0 Rx invalid crypt:0 rx invalid frag:0
          Tx excessive retries:0 Invalid misc:1063 missed beacon:0

sit0   no wireless extension






by the way, y&#305;ld&#305;r&#305;m is my wireless account i wrote it myself via networking on system administration menu. i also wrote the security key. the problem is again although i see all the possible wirelesses around i cannot connect any of them.
The problem shouldnt be with my wireless card . should it ? because otherwise i couldnt see any wireless around. maybe the problem is with access point i dont know i am absolutely noob 

so please can you help me ?
thnks in advance

---

### Post by uputer on 2007-09-23
I would help you if I could since you have zero replies.   If someone leaves their connection 'open' or unencrypted, they could have a router or wireless connection around and you could 'see' it.   Perhaps, that's what you're seeing?

It sounds like your drivers or wireless product is not being loaded or activated.   One or the other.   I am just making suggestions as I can't tell from what you wrote.

---

### Post by johndoeee on 2007-09-23
> **uputer said:**
> I would help you if I could since you have zero replies.   If someone leaves their connection 'open' or unencrypted, they could have a router or wireless connection around and you could 'see' it.   Perhaps, that's what you're seeing?
.

hmm. you mean i can see wireless connections even if my wireless driver doesnt work properly. I havent known it actually. Then i am supposed to try to check whether my wireless driver works.
I just wrote lspci to terminal and here is what i get.


0:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d8 (rev a1)[COLOR="Red"]
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)[/COLOR]
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


Does it mean my wireless card is installed correctly.
by the way, my laptop is hp dv6000.

---

### Post by uputer on 2007-09-23
I'm a complete newbie so I'm probably not the person to ask.   But, common sense suggests to me that is just a command to give you an output of your hardware components (and which chipsets and other hardware that make up your hardware devices).   If you cannot access the internet properly (i.e. no connection, connection dropping off or whatever), then it means your wireless is not working properly.   The command can output what your device is but it doesn't necessarily mean it's working properly.   I believe there are some commands that give you an output whether the device is working properly or 'activated.'    But, I am still learning and offhand, I'm not sure what the command is but I believe I read it somewhere here (in this forum).   

Hopefully, someone with more experience and knowledge will respond to your inquiries.   Sorry I couldn't be of more help.

---

### Post by johndoeee on 2007-09-24
isnt there anyone who can help ?

i think the problem has to do with access point.because it says n/a for access point. but i dont what the heck is access point and how can i fix it :(

no help ?

---

### Post by Lorenz on 2007-09-24
Is there an open wireless network near you that you could try to connect to?

Because as far as I can see there is nothing wrong with your wireless card, it is recognized and seems to work. Do you know the key for your wireless network? Or perhaps the settings only allow certain MAC adresses to connect to it, no matter if you know the passphrase...

Anyway, I would recommend  using Network Manager.
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

It always worked great for me and I had no problems with any wireless anymore.
Give it a try, perhaps you have more luck with it.

---

### Post by sanderella on 2007-09-24
One of the hardest things to sort out is wireless cards. There are so many different ones, and what's right for you may not be right for someone else. It took weeks for me to find the solution I needed, but finally someone at my local Linux User Group helped me.

However many problems have already been sorted out by Canonical. Look at the sticky threads at the top of this category. Then using your knowledge of your own hardware, follow the links and you will probably find the help you are looking for.

Start with the hardware compatability list. Then try [https://help.ubuntu.com/7.04/internet/C/index.html](https://help.ubuntu.com/7.04/internet/C/index.html)
especially the link to wireless cards.

The answer is there, but it may take some time to find it.

Best of luck!:popcorn:

---

### Post by uputer on 2007-09-24
Do this:
ifconfig to list lo adapter and eth0 or ethX options/devices

lspci lists whether the adapter exists 

grep -i 3945 will inform you whether or not the driver was installed.   (I think so anyway)

Are you using a laptop?   There's a thread about the Intel wireless chip, same one, in a laptop and the user had to flip some switch to turn wireless on.

---

### Post by Lorenz on 2007-09-24
I second the idea about the switch. 
I got the same chipset on a IBM T60 - there is a switch on the front of the laptop (bottom), left to the speaker. Could be that it's just this that you have to do. But - I don't think so, as you can see wireless networks around and that wouldn't work if it's switched off.

---

### Post by johndoeee on 2007-09-25
hey the problem is solved :)

actually i havent exerted any special effort but i noticed that i can only connect to wirelesses without keys. i mean encryption.

it sounds strange . doesnt it . now the problem is how can i access connect to wirelesses with key:(

---

