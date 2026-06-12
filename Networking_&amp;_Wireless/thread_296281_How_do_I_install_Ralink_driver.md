---
title: "How do I install Ralink driver"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by Tweedicus on 2006-11-09
I run Edgy. I have a Belkin card 7010. My local Linux shop kindly gave me the correct drivers for them on a CD. These are native Linux drivers, not Windows drivers. So please no-one tell me to use Ndiswrapper. 

I've taken the drivers off the CD, they're a tar.gz file, and extracted them onto my desktop. The file name is RT73_Linux_STA_Drv1.0.3.0

How do I install this driver so that my card recognises it, and runs off it.

Thanks.

---

### Post by FrodoB on 2006-11-09
Note: I have now made a improved document on the installation of the F5D7050 ver 3000 using the rt73 driver. The new document is cleaned up and easier to follow.

This new document can be found on the Ubuntu Documentation site here:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)


Here is the original post for those who wish to follow this thread:

Installation of the RT73 driver is somewhat long, but not difficult. I have been using it on a Belkin F5D7050 ver 3000 that uses the same driver for some time. If you want to use the driver off of your CD you will have to change the name slightly. 

My instructions refer to the F5D7050 ver 3000 you just insert your device's name when you encounter it. You will also have to use a different USB device ID and you might find that yours is already in the rtmp_def.h file. Just run lsusb to see what ID your device has.

Here is how I installed the F5D7050 ver 3000 that uses the same RT73 driver:

1. You need to blacklist the existing driver module, which does not work, so that it does not interfere with this new module:

user@ubuntu:~$ sudo gedit /etc/modprobe.d/blacklist


add the following to the end of the file:

# Added when rt73 module was installed
blacklist rt73usb

Save the file. The blacklisted module will not be loaded from now on.


2. You will need to install the kernel sources to compile the driver so if you do not have them already then:

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build


3. Download the latest version of the Ralink RT2571W/RT2671 USB drivers from:

[http://www.ralink.com.tw/supp-1.htm](http://www.ralink.com.tw/supp-1.htm)

The latest at the time I am writing this is:

[http://www.ralink.com.tw/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralink.com.tw/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

You can get them into your current directory with the following wget command:

user@ubuntu:~$ wget [http://www.ralink.com.tw/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralink.com.tw/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz)


4. Extract the archive into you home directory and then change into that directory:

user@ubuntu:~$ tar xvzf RT73_Linux_STA_Drv1.0.3.6.tar.gz 

user@ubuntu:~$ cd RT73_Linux_STA_Drv1.0.3.6/Module

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6$ 

  
5. Fix the permissions are not correct on the files using chmod and convert them to UNIX text.

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ chmod -R 755 *

install todos and fromdos

user@ubuntu:~$ sudo apt-get install tofrodos

Fix all of the file in the directory:

user@ubuntu:~$ fromdos *

6. Edit the file rtmp_def.h and near the end of the file is a section that deals with the USB IDs of the devices that this driver works with. You will have to change your USB ID to match the F5D7010 devices' ID.

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ gedit rtmp_def.h

You need to add this devices USB ID to the file immediately after the #define RT73_USB_DEVICES comment. Just make a copy of the first entry and change it to:

#define RT73_USB_DEVICES { \
 {USB_DEVICE(0x050d,0x705a)}, /* Belkin F5D7050 ver 3000 */      \

Save the file.


7. Copy the Makefile.6 file into the Makefile:

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ cp Makefile.6 Makefile


8. Make the driver with make:

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make

This will take several minutes.


9. Install the driver:

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo make install


10. Confirm that /lib/modules/2.6.17-10-generic/extra contains the rt73.ko file.

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ ls /lib/modules/2.6.17-10-generic/extra


11. Copy the device's firmware into the assigned areas, by creating the firmware directory and copying the rt73.bin and rt73sta.dat files into it:

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo mkdir /etc/Wireless
user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo mkdir /etc/Wireless/RT73STA
user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo cp rt73.bin /etc/Wireless/RT73STA
user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo cp rt73sta.dat /etc/Wireless/RT73STA

12. Now we need to create the entries for the new device in /etc/network/interfaces:

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo gedit /etc/network/interfaces

This is the data to add at the end of the file: (Choose either to use a hex or ASCII key, but not both, uncomment one.)

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid MY_ESSID
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto rausb0

The only thing different between this record and the one that would be created by the Networking applet is the "pre-up ifconfig rausb0 up" line.


13. Without having the F5D7050 ver 3000 inserted in the system do a system restart. This seems to be required to get the modules loaded happily for some reason.


14. After the system has restarted and you have logged in, insert your F5D7050 version 3000 device into a usb connector on your machine and verify that you can see it by opening a terminal window and running lsusb. You should see the device as:

Bus 00X Device 00X: ID 050d:705a Belkin Components 


15. In the same terminal window run iwconfig and you should see the device as rausb0.


16. It should have come up and recognized your access point if all of your data was entered correctly.


17. In the same terminal window enter a iwconfig command you should see something like this: 

Note: Initialization of the device may take up to 15 seconds, so wait if your device is not fully configured yet.

rausb0    RT73 WLAN  ESSID:"MY_ESSID"  
          Mode:Managed  Frequency=1 MHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-28 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Note that the Frequency is listed as 1 MHz, but this is really the channel number, this seems to be a feature of the present driver implementation. Also, my access point is a 802.11b device so I do not know how well the device may work at higher speeds.


18. If you run a "netstat -rn" command you should see that the routing paths are setup:

Note: Initialization of the device may take up to 15 seconds, so wait if your device is not fully configured yet.

user@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 rausb0
0.0.0.0         192.168.1.2     0.0.0.0         UG        0 0          0 rausb0

19. You can now control the device with ifup and ifdown like so:

user@ubuntu:~$ sudo ifdown rausb0
user@ubuntu:~$ sudo ifup rausb0


 
I hope that this helps you. The Ralink chipset devices seem stable once they finally get installed correctly.

Good Luck,

FrodoB

---

### Post by ckellner on 2006-11-10
I tried some days ago to install the RALINK driver for my ASUS  wl 167g (RT73 Version) ebfore seeing this post. I did not really get that to work (although I already forgot what was the problem) so I switched to the serialmonkey RT73 legacy driver. That worked -almost.

Since these drivers are similar I post this here in this thread. 
I get the driver working with

sudo ifconfig rausb0 up
sudo iwconfig rausb0 essid ID
sudo iwconfig rausb0 key open PWD
sudo dhclient rausb0 

however, it does not work automaticcaly at bootup, even after I changed

My etc/network/interfaces to

iface rausb0 inet dhcp
ifconfig up
wireless-key s:PHW
wireless-essid ID
wireless-keymode open
auto rausb0

and my /etc/network/if-pre-up.d/wireless-tools

starts with 
   

#!/bin/sh

IFCONFIG=/sbin/ifconfig

if [ ! -x $IFCONFIG ]; then
exit 0
fi

if [ -n "$IF_IFCONFIG" ]; then
eval $IFCONFIG "$IFACE" $IF_IFCONFIG
fi

IWCONFIG=/sbin/iwconfig

...

Any ideas, where is the problem or how i could check whats going wrong?

---

### Post by FrodoB on 2006-11-11
The SerialMonkey rt73 driver may not be ready for public consumption yet. One some days it has not even compiled for me. That is why I suggest the Ralink driver, it is stable and does seem to work well. I can't wait for the SerialMonkey to be more stable and have releases.

---

### Post by ckellner on 2006-11-11
OK, reinstalled original Ralink driver. 
Following strictly to above how-to it finally worked - Seems indeed a little more stable. Thanks for this HOW-to. i would never come up how to modify the one .h file 

However, my problem was not related to the driver, it was simply a typo in the password (although i though I checked 3 times)

---

### Post by liljoe76 on 2006-11-12
frodob, i'm stuck on # 8.
joe@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/joe/RT73_Linux_STA_Drv1.0.3.6/Module modules
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
just wondering if any anyone has any insight. i'm much too new at this to get any further. thanks for any help.
sorry for not providing more info, not sure whats needed though. i'm on edgy 386.
-joe

---

### Post by FrodoB on 2006-11-12
Joe;

Can you look in /usr/src and see if you see something like this:

user@ubuntu:/usr/src$ ls
linux                            linux-source-2.6.17
linux-headers-2.6.17-10          linux-source-2.6.17.tar.bz2
linux-headers-2.6.17-10-generic

Publish what you have please.

---

### Post by FrodoB on 2006-11-12
Joe;

Give me the output of ls at /lib/modules

$ ls /lib/modules

mine shows:

user@ubuntu:/lib/modules$ ls
2.6.17-10-generic

Also an ls of /usr/src:

S ls /usr/src

mine shows:

user@ubuntu:/usr/src$ ls
linux                            linux-source-2.6.17
linux-headers-2.6.17-10          linux-source-2.6.17.tar.bz2
linux-headers-2.6.17-10-generic

---

### Post by liljoe76 on 2006-11-12
usr/src/
linux-headers-2.6.17-10          linux-source-2.6.17.tar.bz2
linux-headers-2.6.17-10-generic
/lib/modules/
2.6.17-10-386  2.6.17-10-generic

i actually just got the headers cause after installing the beta nvidia drivers i'm running on the 386 kernel. so i'm trying to get back on the generic as i type this....

---

### Post by FrodoB on 2006-11-12
The problem is that with your current kernel:

/lib/modules/2.6.17-10-i386/build 

should be a symbolic link to

/usr/src/linux-headers-2.6.17-10-i386


Under the generic kernel they should be linked this way:
/lib/modules/2.6.17-10-generic/build 

should be a symbolic link to

/usr/src/linux-headers-2.6.17-10-generic


So you either need to change kernels back to the generic or repair the link.

To stay with the one you have in a terminal change to:

$ cd /lib/modules/2.6.17-10-i386

and then

$ sudo rm build

$ sudo ln -s /usr/src/linux-headers-2.6.17-10-i386 /lib/modules/2.6.17-10-i386/build

At least that is what it looks like from here.

Then change back to your Modules directory and do a make again.

I take no responsibility for any damage that may occur as a result of my advise. Good luck my friend.

---

### Post by liljoe76 on 2006-11-12
i thank you for your help. all your commands went, but no change with the error message, the link wasn't created. unfortunately i dont know enough to do this, and dont really want to, seeing as i have a amd turion running on a single core (stupid) and a broadcom 4311 i cant get going for the past 3 weeks (yea!!). so i'm gonna do ANOTHER reinstall/clean slate to try getting something working right... 
i really wish i could recommmend this OS to my clients..... pissa
thank you again, i love this forum. 
-joe

---

### Post by FrodoB on 2006-11-12
Yes, it looks like having had multiple kernels is somehow a part of   your issues. This will work on a clean install for sure.

Good luck and let me know how it finally goes.

---

### Post by liljoe76 on 2006-11-12
thanks again. i love learning this, i just need to temper frustration.... :)

---

### Post by FrodoB on 2006-11-12
The problem with my previous instruction is that the:

/usr/src/linux-headers-2.6.17-10-i386

did not exist. So you would have to do a 

$ sudo apt-get install linux-headers-2.6.17-10-i386 

and that would likely have worked.

A fresh install is fine as well.

---

### Post by liljoe76 on 2006-11-13
so yea, i dont know exactly how i made it work but i'm back on the generic kernel. so i'll give this all a shot again when i get home...
hopefully i can get the dlink running since having a laptop is virtually pointless without wireless.... least thats what it feels like.

---

### Post by FrodoB on 2006-11-13
OK, I have installed a clean Ubuntu 6.10 and gone through the procedure and make some improvements. Let me know how it goes.

---

### Post by liljoe76 on 2006-11-13
ok, so.. to continue the saga, i started over. every command except fromdos* (joe@ubuntu:~$ fromdos *
fromdos: File read/write error while converting worked without errors RT73_Linux_STA_Drv1.0.3.6.). unfortunately the link light on my dlink dwl-g122 now fails to light up, it did previously. so i'm gonna list out what relevant info i can. 

joe@ubuntu:~$ uname -r
2.6.17-10-generic

joe@ubuntu:~$ lsusb
Bus 002 Device 004: ID 2001:3703 D-Link Corp. [hex] DWL-122 802.11b
Bus 002 Device 003: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05bc:0110 3G Green Green Globe Co., Ltd 
Bus 001 Device 001: ID 0000:0000 

rtmp_def.h
#define RT73_USB_DEVICES { \
 {USB_DEVICE(0x2001,0x3703)}, /* D-Link */      \
should the other entries be deleted?

network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

#iface eth1 inet dhcp
#wireless-essid joe

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid joe
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX # This line for ASCII (string) keys
i commented out the built-in wifi. no reason, just seemed right.... and i'm running a dlink di-524, broadcast ssid: joe, no wireless security. just trying to get'er on. 
i could sometimes get bcm4311 to see the config page login, but thats another stories and _many_ installs ago..... UGH

joe@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

rausb0    RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
i did reboot twice without usb stick. ummm, i've unplugged the cat5 rebooted... uhhh i disabled the wired connection, rebooted.. i have neither network manager or wifi radar installed. 
and i honestly cant imagine a normal person doing this.... lol
thanks for reading any of this. if you "got nothing", thats cool. i'm ok with that, i'm getting good at reinstalls... 
-joe

ps. the usb stick isnt burning hot like normal.... not initialized?

---

### Post by FrodoB on 2006-11-13
You do not need to worry about the entries for other devices, just add your own.

Note that there is a space between fromdos and *

Otherwise it should work, I did it cut and paste on a new install this afternoon.

You might want to try from the beginning. No reinstall of Ubuntu required.

Maybe I fixed something between when you got you copy of the procedure and when I rebuilt my system?

---

### Post by liljoe76 on 2006-11-13
alrightly then... :) no go here. i did fix the fromdos by running it from the correct directory, not home. but i simply dont know enough to help you help me... 
i think i'm done trying, i was doing this just to get some wireless going. i haven't had a good run w/edgy since rc, considering it more sketchy than edgy. so i'm dl'in dapper and see whats up. give edgy some time to mature... i truely appreciate your help, and i may be calling on you again. if nothing we put info into the forum to help others..... i know i've read enough of these threads in the past month to make anyone's head spin :)
take care, 
joe

---

### Post by liljoe76 on 2006-11-13
.

---

### Post by dean20007 on 2006-11-14
Hi Folks

I followed the how to step by step and hey it works a treat. After 3 days of other how tos and ndiswrappper nightmares I got it working woohoo. 

My problem now is that it never brings up the connection automatically after booting.

Can anyone help?

---

### Post by FrodoB on 2006-11-14
Maybe you can explain how you do get the connection going.

---

### Post by FrodoB on 2006-11-14
I just rebooted to check my Belkin F5D7050 ver 3000 and its network does start on boot. 

It also starts automatically if I just plug it in. If I unplug the device everything is stable and if I plug it in again its network connection just starts automatically.

This is what I was hoping would happen for others, are you using the exact same device as mine or just another device that uses the rt73 drivers?

---

### Post by dean20007 on 2006-11-14
not sure but the supplied windows drivers were rt73 so i went the ones you recommended. 

when i boot up, if i try and ping my router it tells me that the network is unreachable. 

I played about and set my essid (even though it is set in /etc/network/interfaces/

with sudo iwconfig rausb0 essid (myessid)
sudo ifconfig rausb0 up

and this seems to work

but obviously it would be nice if it did it on startup 

any ideas?
 

cheers

---

### Post by FrodoB on 2006-11-14
Go back and look at your interfaces file. 

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid MY_ESSID
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX # This line for ASCII (string) keys
auto rausb0


"pre-up ifconfig rausb0 up" does the ifconfig automatically.

$ sudo ifup rausb0

$ sudo ifdown rausb0 

should work if you have it correct.

---

### Post by dean20007 on 2006-11-14
my bad... i omitted the up from the end of the first line hopefully that will solve all problems 

your help is much appreciated

---

### Post by FrodoB on 2006-11-14
Good, should do it. I have installed on three different machine with equally good results so far.

---

### Post by doug10k on 2006-11-14
FrodoB - thank you for the concise help on installing the RT73 driver.  I was just about ready to give up on Edgy and install another distro when I saw your post and decided to give it a try.  Now I'm on Edgy with my Linksys WUSB54GC wireless for the first time since I upgraded from Dapper Drake!

FYI, one minor difference I saw was that my rt73.ko ended up in /lib/modules/2.6.17-10-386/extra rather than in /lib/modules/2.6.17-10-386-generic/extra.

For anyone else with the Linksys WUSB54GC, the driver information that needs to be added to rtmp_def.h is this:

{USB_DEVICE(0x13b1,0x0020)}, /* Linksys WUSB54GC */ \

Again, thanks for the help.

---

### Post by FrodoB on 2006-11-14
OK thanks for the feedback please verify the fixes that I made. I put your devices USB ID in the instructions and I fixed the ls for checking for the module to:

user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ ls /lib/modules/`uname -r`/extra 

If you cut and paste that instruction into a terminal it should show you the module in the correct directory.

Thanks again for the assistance.

---

### Post by doug10k on 2006-11-15
Your updates look correct.  I'm glad this is all written down for others to follow.

---

### Post by Shack on 2006-12-26
... solved

---

### Post by Shack on 2006-12-26
omg, my wlan is actually working. Thanks to you guys!!

Thanks alot, I mean alot. I've been working with this for 3-4 days and now this feels like heaven :)

---

### Post by lfullard on 2007-02-25
Hi, I am trying to follow the guide but when i get to #8 i get



--------------------------------------------------------------

lfullard@lfullard-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/lfullard/RT73_Linux_STA_Drv1.0.3.6/Module modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
lfullard@lfullard-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ 

--------------------------------------------------------------

My  output of ls at /lib/modules is
--------------------------------------------------------------

lfullard@lfullard-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ ls /lib/modules/
2.6.15-26-386  2.6.15-27-386
lfullard@lfullard-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$

----------------------------------------------------------------

and     Also an ls of /usr/src:
----------------------------------------------------------------

  lfullard@lfullard-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ ls /usr/src/
linux-wlan-ng-source.tar.gz  ndiswrapper-source.tar.bz2  rt2400.tar.gz
modules                      ov511.tar.gz                rt2500.tar.gz

----------------------------------------------------------------


I am reasonably new to linux, am using Kubuntu

Thanks

Luke
lfullard@lfullard-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$

---

### Post by watson540 on 2007-02-28
Obviously, you're reasonably new to reading as well. Install your kernel headers.

P.S. Why must threads always be hijacked by people that need their hand held. Is mass migration to linux really a good thing?!

P.S.S. Umm...Im so dissapointed, Heh, the spell checker on this website is telling me that linux is mis-spelled ! Such a travesty! :)

---

### Post by Rxke on 2007-04-18
Thanks! Works wonders

---

