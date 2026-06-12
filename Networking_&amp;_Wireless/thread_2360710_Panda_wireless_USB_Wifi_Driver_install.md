---
title: "Panda wireless USB Wifi Driver install"
date: 2017-05-07
forum: Networking &amp; Wireless
---

### Post by hal20002 on 2017-05-07
Hello, im sort of noob and is using google to figure this stuff out, Im trying to install this usb wifi driver on ubuntu 16.04, the driver itself is a panda wireless pau06 that i bought from here  [http://pandawireless.com/](http://pandawireless.com/)  
on that website is where i installed the driver as well, but the filename of the driver says LinuxDriver4Fedora_v2.5.0.3.tar.bz2 and thats the only one they have for linux so im guessing it works for ubuntu too.
If you scroll down on that website at the bottom theres a .pdf instruction manual, here is what it says

You need to become the superuser of your machine before you perform the following  instructions:- 
1) Blacklist RT2800 wireless module in the Linux Kernel $>cd /etc/modprobe.d $>vi blacklist.conf Add "blacklist rt2800usb" at the end of the file. 
2) Copy RT2870STA to /etc (RT2870STA.dat is located in your driver install directory) $>mkdir -p Wireless/RT2870STA (under /etc directory)            $>cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
   *I had to use sudo nautilus to do this as it wouldnt let me cp the .dat file into the Wireless/RT2870STA directory i made, seemed to work just fine*
3) Create tftpboot directory under root directory 
$> mkdir /tftpboot 
4) Compile the driver for the Panda Wireless N adapter 
    $> tar jxvf LinuxDriver4Fedora_v2.5.0.3.tar.bz2 
    $> make 
          You will find rt3070sta.ko in /tftpboot directory 
   5) Load driver $>insmod rt3070sta.ko 
                       $>ifconfig ra0 inet up 
  $>ifconfig ra0 inet up
6) Unload driver $>ifconfig ra0 inet down 
 $>rmmod rt3070sta.ko

I did this except create the tftpboot directory it root as i dont know where that is, theres the standard directory where everything you see or the "My Files" i guess, and apperantly a hidden folder called /root itself, which i dont know how to get to or how its going to write its rt3080sta.ko file to it as its hidden

ive also blacklisted my own onboard wifi card which is a realtek rtl8188ce(Using a rtl8192ce driver i think) here is what the blacklist file looks like
(the driver the manual told me to blacklist plus the other 2 i found out to do aswell from some forum i forgot where)
  blacklist rt2x00usb
   blacklist rt2x00lib
   blacklist rt2800usb

 (My laptops own onboard wifi card)
    blacklist rtl8192ce
    blacklist rtl8188ce

after this i run ./configure and i get "bash: ./configure: No such file or directory
apperantly i need a configure file to do this but the only such file is a configure.mk file

i then run the "make" command in terminal and i get this recipe for target 'LINUX' failed error
cc1: some warnings being treated as errors


compilation terminated.


scripts/Makefile.build:289: recipe for target '/home/kareem/Downloads/LinuxDriver4Fedora_v2.5.0.3/os/linux/../../sta/sta_cfg.o' failed


make[2]: *** [/home/kareem/Downloads/LinuxDriver4Fedora_v2.5.0.3/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1491: recipe for target '_module_/home/kareem/Downloads/LinuxDriver4Fedora_v2.5.0.3/os/linux' failed


make[1]: *** [_module_/home/kareem/Downloads/LinuxDriver4Fedora_v2.5.0.3/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-36-generic'


Makefile:356: recipe for target 'LINUX' failed


make: *** [LINUX] Error 2


ps i need to copy terminal errors on flashdrive and paste them to this windows laptop im on now, then add the spaces to make it easier to read as it pastes in 1 giant line in windows notepad,also i can do a wired connection but it requires me to go downstairs and sit in an uncomfortable position so im on this pc instead.

also this isnt really time sensitive, im just trying to see if i can get my old laptop working and maybe give it to my mom or something. I had to replace the harddrive and fan so i put ubuntu on the new hard drive, the laptop is a HP Pavillion dv6-6c35dx
so i had to remove the whole motherboard via youtube instructions and inevitably broke a few things, like the white antenna connector on the integrated wifi card lol

---

### Post by chili555 on 2017-05-07
It is doubtful that you will get that oldy moldy Fedora file to ever work.

Let's try an experiment; please revert the blacklist changes you made and reboot with the device inserted and tell me what happens.

---

### Post by hal20002 on 2017-05-07
> **chili555 said:**
> It is doubtful that you will get that oldy moldy Fedora file to ever work.

Let's try an experiment; please revert the blacklist changes you made and reboot with the device inserted and tell me what happens.

i guess it seems to be working now, im guessing its using the rt2800usb driver for some reason the instructions told me to blacklist, i dont know how to check what the driver its using is though, thx!

---

### Post by chili555 on 2017-05-08
Let's find out! Please open a terminal and run the command to list all the loaded modules (drivers):```
lsmod
```Wow! That's quite a long list, isn't it?  Let's trim the list down to any drivers with the term 'rt2' in them, as rt2800usb is our suspect. Let's use the pipe symbol | to output the long list into another command, grep. grep means, approximately, look for a pattern.```
lsmod | grep rt2
```I am confident that the driver is rt2800usb and all its cousins, rt2800lib, rt2x00lib and more.

Next, I suggest that we blacklist the driver for the internal device. Let's find out what it is:```
lspci -nnk | grep 0280 -A2
```Once we know more, we'll proceed.

---

### Post by hal20002 on 2017-05-08
lsmod tells me indeed the usb is using the rt2800 and its cousins

lspci says:

Network controller [2800]:realtek semiconductor co. , Ltd. RTL8188CE 802.11b/g/n wifi adapter [10ec:8176] (rev 01)
             device name:
              subsystem: Hewlett-Packard company RTL8188CE 802.11b/g/n wifi adapter [103c:1629

---

### Post by chili555 on 2017-05-08
> lsmod tells me indeed the usb is using the rt2800 and its cousins
Excellent!> realtek semiconductor co. , Ltd. RTL8188CE 802.11b/g/n wifi adapter [10ec:8176]This device uses the driver rtl8192ce. You can check that as well:```
lsmod | grep rtl
```If so, we can avoid some possible (probable) conflicts by unloading and blacklisting it;```
sudo -i
modprobe -r rtl8192ce
echo "blacklist rtl8192ce"  >>  /etc/modprobe.d/blacklist.conf
exit
```You should be all set.

---

### Post by pbc11111 on 2017-09-01
Can you please break that down to commands I would have to enter in chronological order so even the layman can understand it.  
I just want to install the necessary driver to get the Panda PAU06 USB Wifi antenna to work with my version of Linux Ubuntu 16.04

Something like this would be helpfull:
1) enter this
2) ....
3)....


Thanks

---

### Post by chili555 on 2017-09-01
> **pbc11111 said:**
> Can you please break that down to commands I would have to enter in chronological order so even the layman can understand it.  
I just want to install the necessary driver to get the Panda PAU06 USB Wifi antenna to work with my version of Linux Ubuntu 16.04

Something like this would be helpfull:
1) enter this
2) ....
3)....


ThanksI will be most happy to help!

Rather than piggyback this old thread, please start your own new thread and I'll be there to help. Include in your original post the result of this terminal command:```
lsusb
```Thanks.

---

