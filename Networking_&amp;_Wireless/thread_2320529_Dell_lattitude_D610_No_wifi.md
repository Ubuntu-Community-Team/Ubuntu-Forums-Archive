---
title: "Dell lattitude D610 No wifi"
date: 2016-04-14
forum: Networking &amp; Wireless
---

### Post by Ben_E on 2016-04-14
So i was given the task to convert 10 D610s to Ubuntu . But the WiFi doesn't work at all . 

ubuntu-15.10

Here are the things I already did.

 
pressed fn-f2 (wifi button)
downloaded b43 software
checked if the wifi card was defective
reinstalled Ubuntu 
tried other distributions

Can some one help me fix this?

---

### Post by Geoffrey_Arndt on 2016-04-14
Did you try the standard process to install the wireless driver?   (which is not downloading b43 software from the web) (or do any of the other things you've tried).

System Settings>Software & Updates>Additional Drivers Tab

---

### Post by Ben_E on 2016-04-15
No i have not . I am a complete noob to Ubuntu . I went to the additional drivers tab and the only thing that shows up is processor firmware for intel cpus.

---

### Post by mörgæs on 2016-04-15
A D610 works great with X/Lubuntu. I have one myself.

Just install and apply all updates using a wired connection. Reboot. After that this will do the trick: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by howefield on 2016-04-15
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by Hadaka on 2016-04-15
Hi Ben_E The Ubuntu version you have 15.10 is no longer supported
[TABLE]
[TR]
[TD="bgcolor: #f1f1dd"][Wily Werewolf]("https://wiki.ubuntu.com/WilyWerewolf") 
[/TD]
   [TD="bgcolor: #f1f1dd"] [Rel]("https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes") 
[/TD]
   [TD="bgcolor: #f1f1dd"] [October 22, 2015]("https://lists.ubuntu.com/archives/ubuntu-announce/2015-October/000202.html") 
[/TD]
   [TD="bgcolor: #f1f1dd"] [July 2016]("https://lists.ubuntu.com/archives/ubuntu-announce/2015-October/000202.html")  
[/TD]
[/TR]
[/TABLE]

I suggest you load 14.04 LTS as it is supported until 2019

also, please read the "sticky's" on the top of the Network and wirless
trouble reporting page.
thanks.

---

### Post by mörgæs on 2016-04-15
It's supported until July 2016, as can be seen in your text above :-)

I recommend 15.10 as I have only good experience with this release on a D610 but I think many releases will perform fine.

---

### Post by Hadaka on 2016-04-15
Hi, please forgive my error, morgaes is correct, Ubuntu 15.10 is still supported.

Please open a terminal ctrl/alt/t then Copy and paste the following command
and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is ***wireless-info.txt***
Next.
From your directory please copy,paste and post the ***wireless-info.txt***
thanks.
*Note
 You may want to retain,these instructions as they will apply to whatever Ubuntu version
you decide to load in 2 months when Ubuntu 15.10 is no longer supported.

---

### Post by Ben_E on 2016-04-15
The file does not get placed in the home folder. And have no internet on any of these machines

---

### Post by Hadaka on 2016-04-15
ok, Let's start with one machine..just one.
open a terminal. ctrl/alt/t then enter one command at a time.
```
uname -r
lsb_release -a
lspci -n | awk '/0200|0280/{print$3}'
lsmod | awk '/wl|b43|iwl|ath/{print}'
```
post the output.
thanks.

---

### Post by Ben_E on 2016-04-15
test@test-Latitude-D610:~$ uname -r
4.2.0-16-generic
test@test-Latitude-D610:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily
test@test-Latitude-D610:~$ lsp -n | awk '/0200|0280/{print$3}'
No command 'lsp' found, did you mean:
 Command 'ls' from package 'coreutils' (main)
 Command 'lgp' from package 'simh' (universe)
 Command 'l2p' from package 'alliance' (universe)
 Command 'lscp' from package 'nilfs-tools' (universe)
 Command 'tsp' from package 'task-spooler' (universe)
 Command 'lsx' from package 'suckless-tools' (universe)
 Command 'lsw' from package 'suckless-tools' (universe)
 Command 'xsp' from package 'mono-xsp' (universe)
 Command 'fsp' from package 'alliance' (universe)
 Command 'lp' from package 'cups-client' (main)
 Command 'lp' from package 'gnuspool' (universe)
 Command 'lp' from package 'lprng' (universe)
 Command 'asp' from package 'asp' (universe)
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lcp' from package 'lsh-client' (universe)
lsp: command not found
test@test-Latitude-D610:~$ lsmod | awk 'wl|b43|iwl|ath/{print}'
awk: line 1: syntax error at or near b43
test@test-Latitude-D610:~$ lsmod | awk '/wl|b43|iwl|ath/{print}'
b43                   401408  0
bcma                   49152  1 b43
mac80211              659456  1 b43
cfg80211              483328  2 b43,mac80211
ssb                    57344  1 b43
test@test-Latitude-D610:~$

---

### Post by Hadaka on 2016-04-15
Hi you have a typo the command is...
```
lspci -n | awk '/0200|0280/{print$3}'
```
please try again.
thanks.

---

### Post by Ben_E on 2016-04-15
Sorry here it is

test@test-Latitude-D610:~$ uname -r
4.2.0-16-generic
test@test-Latitude-D610:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily
test@test-Latitude-D610:~$ lspci -n | awk '/0200|0280/{print$3}'
14e4:1677
14e4:4318
test@test-Latitude-D610:~$ lsmod | awk '/wl|b43|iwl|ath/{print}'
b43                   401408  0
bcma                   49152  1 b43
mac80211              659456  1 b43
cfg80211              483328  2 b43,mac80211
ssb                    57344  1 b43
test@test-Latitude-D610:~$

---

### Post by Hadaka on 2016-04-15
Hi, thanks for the updated information. we now know what network cards you have.
```
Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] 
Broadcom Corporation BCM4318  Wireless LAN Controller [14e4:4318]
```
Your ethernet uses the "tg3" driver..
your wirless uses the "b43"
Am I correct that you have no wired access to a router?  only wireless??
You have the correct driver loaded,b43 so let's look at a few things to see why it is not connecting.,
*Some of the following commands will probably result in error or file not found...ignore and do each command.
please post the output of..
```
rfkill list all
 sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf b43
sudo modprobe -vv b43
iwconfig
ifconfig
iwlist wlan0 scan
dmesg | grep b43
```
thanks.

---

### Post by Ben_E on 2016-04-16
So i bought one of the d610s home to fix for next week . And i have access to a router . It would be best to get the WiFi working asap. anyway here is the code



test@test-Latitude-D610:~$ rfkill list all
test@test-Latitude-D610:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
[sudo] password for test: 
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
test@test-Latitude-D610:~$ sudo modprobe -rf b43
test@test-Latitude-D610:~$ sudo modprobe -vv b43
modprobe: INFO: ../libkmod/libkmod.c:356 kmod_set_log_fn() custom logging function 0x800191f0 registered
insmod /lib/modules/4.2.0-16-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/4.2.0-16-generic/kernel/net/wireless/cfg80211.ko 
modprobe: INFO: ../libkmod/libkmod-module.c:884 kmod_module_insert_module() Failed to insert module '/lib/modules/4.2.0-16-generic/kernel/net/wireless/cfg80211.ko': File exists
insmod /lib/modules/4.2.0-16-generic/kernel/net/mac80211/mac80211.ko 
modprobe: INFO: ../libkmod/libkmod-module.c:884 kmod_module_insert_module() Failed to insert module '/lib/modules/4.2.0-16-generic/kernel/net/mac80211/mac80211.ko': File exists
insmod /lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/b43/b43.ko 
modprobe: INFO: ../libkmod/libkmod-module.c:884 kmod_module_insert_module() Failed to insert module '/lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/b43/b43.ko': File exists
modprobe: INFO: ../libkmod/libkmod.c:323 kmod_unref() context 0x81352100 released
test@test-Latitude-D610:~$ iwconfig
lo        no wireless extensions.


enp2s0    no wireless extensions.


test@test-Latitude-D610:~$ ifconfig
enp2s0    Link encap:Ethernet  HWaddr 00:15:c5:14:96:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:374843 (374.8 KB)  TX bytes:374843 (374.8 KB)


test@test-Latitude-D610:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


test@test-Latitude-D610:~$ dmesg | grep b43
[    2.169177] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x35aed59b437, max_idle_ns: 881590733090 ns
[   16.380733] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   16.412076] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   16.412099] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 8, Version 0
[   16.982599] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   16.982630] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   17.100524] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   17.100554] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   17.100560] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   17.100563] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   17.100567] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  905.330166] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[  905.360535] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[  905.360563] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 8, Version 0
[  905.374145] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[  905.374187] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[  905.374228] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[  905.374262] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[  905.374271] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  905.374277] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  905.374283] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
test@test-Latitude-D610:~$

---

### Post by Hadaka on 2016-04-16
Hi, you are missing the firmware for the b43 driver            **This method does not require internet access ***
First thing to do is drag and drop the attached b43.zip file
to a usb dirve, then transfer 
to the desktop of the dell610. Then right click and choose "Extract Here"
next..
open a terminal and do...
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -rf b43
sudo modprobe -rf ssb
sudo modprobe b43
```
test wireless

[URL="http://ubuntuforums.org/attachment.php?attachmentid=229272&d=1356748832"]b43.zip


[/URL]

---

### Post by Ben_E on 2016-04-16
Thank You SO MUCH it works now.... :D

Could you guys fix this in the next update? So no has this problem.

---

### Post by mörgæs on 2016-04-16
The problem is closed - source software that can't be distributed in a Buntu package. Broadcom is not very friendly supporting open source. It will be same process in next release.

Still it's a good idea if you try 16.04, as you will have to go there eventually when 14.04 and 15.10 is out of support. 

Please mark the thread solved.

---

### Post by Ben_E on 2016-04-16
were do i get it because on the Ubuntu site it only gives me 15.10

---

### Post by Hadaka on 2016-04-16
you are welcome, be advised that just because the other machines
are dell d610's doesnt mean they will all have the same network cards.
I would like you to mark this thread solved and apply the method to 
the other machines, then open a new thread for any that fail to load.
to mark solved,,go to the first post on this thread and click Thread Tools
then choose Solved.
thanks.

*I am going to pm you and give you a script that will help with the
remaining machines if you like,.
thanks,.

---

