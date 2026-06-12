---
title: "bcm43xx Wireless Work!!!!!!"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by mr_lechuck on 2006-09-28
1 #install fwcutter with command:
  sudo apt-get install bcm43xx-fwcutter

2 #download firmware of here [http://www.ulaopstudio.it/firmware/wl_apsta.o](http://www.ulaopstudio.it/firmware/wl_apsta.o)
  
3 bcm43xx-fwcutter -w /lib/firmware /insert path of wl_apsta.o

4 #insert word bcm43xx on modules with command
  vim /etc/modules //insert bcm43xx

5 reboot

6 yooooo

---

### Post by Emge on 2006-09-28
Is your card a Broadcomm 4318 ?

---

### Post by garfunk on 2006-10-03
I have an Acer Aspire 5022 WLMI with a broadcom 4318. I can get it work, dmesg says me "eth1 : link is not ready".
A friend has an Acer Aspire 5024, it's the same driver with the same wlan card, but it don't work, i don't know why.
I'm really bored with it, someone had the same problem ?

---

### Post by firetux on 2006-10-03
for an acer5024(works with 5022 too):
1)follow this [howto]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")
2) install [acer-acpi]("http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html")

3)when starting the wireless connection you (additionally to the howto):
```
modprobe acer-acpi
modprobe-acer-acpi
 echo "enabled:1">/proc/acpi/acer/wireless
ifup wlan0(or whatever name your wireless has, see iwlist)
```

---

### Post by garfunk on 2006-10-04
Hello
thanks for your help.
i forgot to say that my friend succeded to bring up his interface at the first time without using acer-acpi. I used acer-acpi in Breezy but not in Dapper, are you sure i must install it ?
By the way i can't compile it, i've got a LOT of warnings, saying that /lib/modules/2.6.17-10-generic/build/include/linux/version.h does'nt exist...
Maybe a problem with the version of gcc ? how must i do to force the version of gcc ? with a prefix ?


(excuse for my english...)

---

### Post by firetux on 2006-10-04
I could bring up the interface too without acer-acpi, but to be able to scan for networks I needed acer-acpi. It enables the radio.

Please post the output of your attempt to install it.
The first I can think of is that you need kernel-devel, or something like that, I don't remember the exact name.

---

### Post by garfunk on 2006-10-04
Hello,
thx :)
I give you my outputs :
```
garfunk@garfunk-laptop:/media/GARFUNK/80211g.zip_FILES/80211g$ sudo bcm43xx-fwcutter -w /lib/firmware/ bcmwl5.sys
bcm43xx-fwcutter can cut the firmware out of bcmwl5.sys

  filename :  bcmwl5.sys
  version  :  3.100.46.0
  MD5      :  38ca1443660d0f5f06887c6a2e692aeb

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
*****: Sorry, it's not possible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
*****: Sorry, it's not possible to extract "bcm43xx_microcode13.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
```
As you can see, i have an error when extracting the firmware. My friend says that he has the same error, but by configuring the card in the terminal (iwconfig essid bla key 04AB... )he can connect to his AP.
My lspci :
```
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
My card revision is 02, maybe the problem comes from there...
When i try to bring up my interface, i see :
```
garfunk@garfunk-laptop:/media/GARFUNK/80211g.zip_FILES/80211g$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:9b:b9:80:81
Sending on   LPF/eth1/00:0e:9b:b9:80:81
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
And of course i have no scan results :
```
garfunk@garfunk-laptop:/media/GARFUNK/80211g.zip_FILES/80211g$ iwlist eth1 scan
eth1      No scan results
```
Trying with dhclient eth1 doesn't work anymore ](*,) , and in the dmesg i can see : ```
eth1 : link is not ready
```
And of course since this morning, my ethernet card doesn't work anymore, i dont know why...so i cant install new packages...i must reinstall edgy :'(
Thx :)

---

### Post by firetux on 2006-10-04
1) I don't think the errors while fwcutting are fatal, just ignore them.

2)Did you blacklist ndiswrapper?

3)My lspci is excactly the same. Also 4318 rev 02.

4) About "DHCPDISCOVER","No scan results" and "link not ready" errors: I had the same errors untill I installed acer-acpi.

5)To get your wired network working again: Try removing all your network devices in system-admistration-networking(or something like that) and adding them again.

---

### Post by garfunk on 2006-10-04
Hi,

thanks for your tip about my connection, it works :D
I made a lot of updates, about 150 Mo, i think it is bigger than when i was in beta-test for dapper...
unfortunately, i doesn't work for kernel-devel, i cant compile anymore acer_acpi...i don't understand, i have installed build-essential, ernel-devel, i have my kernel-headers...but "make" makes a lot of errors.
thx for your help, i can go ahead !!

---

### Post by firetux on 2006-10-04
> "make" makes a lot of errorsLOL

Maybe I can help, can you post the errors you get?

---

### Post by garfunk on 2006-10-05
Arf i'm so a noob...you were right i didn't have all the dependencies needed to compile...i compiled acer_acpi, loaded it at boot, but i dodn't remember where i must put the command line which activate the wifi at boot...
But IT WORKS :)
thanks a lot dude, really !
but by the way, i have a little problem : when i activate it, ma card works well, but it's really slooooowwwww. and it gets slower and slower until i can't surf or connect to Gaim or IRC.
Have you got the same problems or not ?
But really, thanks thanks thanks !!!!

---

### Post by firetux on 2006-10-05
I'm really happy it worked, that way I can give something back to the community that got me started with linux.

About the other problem: can you post the output of iwconfig?

I'm not really an expert on networking(I can't solve problems I've never had myself) so you might want to start a new thread on your problem if I can't solve it.

---

### Post by garfunk on 2006-10-05
Arf...after rebooting the pc, i doesn't work anymore. I can activate my card, i see the led blinking, the gnome applet show the green reception meter, but i can't have an IP from my AP.
I tried all that i can : restarting the networking daemon, ifdown/ifup, dhclient, changing the parameters by iwconfig eth1 essid... or with the gnome app (Network in Parameters), but NOTHING...i can't bring it up again.
where can i put the command line to activate my wifi at boot (echo "enable :1"...) ?
Thx in advance

---

### Post by firetux on 2006-10-05
Try:
```
modprobe bcm43xx
modprobe acer-acpi
echo "enabled:1">/proc/acpi/acer/wireless
ifup nameofwirelessdevice
```
What errors do you get when trying the things you mentioned?

---

### Post by garfunk on 2006-10-05
```
garfunk@garfunk-laptop:~$ sudo -s
Password:
root@garfunk-laptop:~# echo "enabled:1">/proc/acpi/acer/wireless
root@garfunk-laptop:~# ifup eth1
Ignoring unknown interface eth1=eth1.
```
It's the first time i got this error o_O
It's boring me !! I can't get it work like yesterday, i don't understand. I think i'll be back to ndiswrapper :(
```
root@garfunk-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:616E-746F-696E-6572-6F62-696C-6C   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by firetux on 2006-10-05
I see two problems: 
> ESSID:""
Go to the networking gui and put ESSID on "auto".

> Bit Rate=1 Mb/s
That's slow. It should be 11Mb/s. Somewhere in the howto you executed a command that put the bitrate on 1 istead of 11. Redo that command and your internet should be fast again, if you get it working.

---

### Post by garfunk on 2006-10-05
Oh my god, it's working !!!!
I installed Network-manager, and it worked out! 
I thank you !
Thx dude it's the most beautiful day in my life

---

### Post by finite9 on 2006-10-19
I have Acer Aspire 5021WLMi broadcom 4318 and have been using Dapper for several months with bcm43xx driver, acer_acpi and WPA.

to make acer_acpi you need

build-essential
kernel-headers
linux-kernel-headers-2.6.15-2x-<arch>

The reason you get so many errors when compiling acer_acpi is becasue you dont have linux-kernel-headers-2.6.15-2x-<arch>.

acer_acpi is needed to enable (via hardware) the wireless adapter.  This is done in Windows with the button on the front of the laptop and/or the Acer startup utility.  As Linux has no mapping for the button it cannot be turned on unless you use acer_acpi.  If you boot windows, then reboot to Linux then the adapter will be 'on' until next power cycle.

By the way, the best method is to apt-get install bcm43xx-fwcutter bcm43xx-firmware, after enabling cafuegos repository (in the wiki) as that will enable you to update the system easily at a later date.  Obviously, you still need to enable acer_acpi, but at least you can stick a new line in /etc/modules to start it instead of messing around with scripts.

---

### Post by garfunk on 2006-10-19
Thanks dude but i finally succedeed. My only little problem was the new arch system in Edgy : only one "generic" kernel. I have no more problems, but thanks for your intervention (don't know if this word exists :/).

---

### Post by WoodyMahan on 2006-10-25
> **mr_lechuck said:**
> 1 #install fwcutter with command:
  sudo apt-get install bcm43xx-fwcutter

2 #download firmware of here [http://www.ulaopstudio.it/firmware/wl_apsta.o](http://www.ulaopstudio.it/firmware/wl_apsta.o)
  
3 bcm43xx-fwcutter -w /lib/firmware /insert path of wl_apsta.o

4 #insert word bcm43xx on modules with command
  vim /etc/modules //insert bcm43xx

5 reboot

6 yooooo

YEEEAAAAAHHHHH!!!!!!!

All I can say is THANK YOU THANK YOU THANK YOU!!!!

Ever since I upgraded to Dapper I have had an awful time with my BCOM NIC.

I even reinstalled from scratch to get a clean copy of Dapper.  I found this how to and I now have a SOLID and stable Wireless connection WITHOUT ndiswrapper.  This is awesome and it only took 5 minutes.

SOMEONE PLEASE STICKY THIS!!!!!!

---

