---
title: "Install driver for Asus usb-n10 (usb wireless adaptor)"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by baguahsing on 2010-07-07
[SIZE=2]I purchased an Asus usb-n10 wireless adaptor for my old laptop. I don't have a clue how to install the drivers from the cd.[/SIZE]
Here is part of the readme text:
 
===============================================================================
Component 
===============================================================================
The driver is composed of several parts:
1. Firmare to make nic work
1.1 firmare/RTL8192SU
2. Module source code
2.1 ieee80211 
2.2 HAL/rtl8192u
2.3 wpa_supplicant-0.5.10 (User can download the latest version from 
internet also, but it is suggested to use default package contained
in the distribution because there should less compilation issue.)
 
3. Script to build the modules
3.1 Makefile 
4. Script to load/unload modules
4.1 wlan0up 
4.2 wlan0down 
5. Script and configuration for DHCP
5.1 wlan0dhcp
5.2 ifcfg-wlan0
6. Example of supplicant configuration file:
6.1 wpa1.conf
7. Script to run wpa_supplicant
7.1 runwpa
===============================================================================
Installation 
===============================================================================
<<Method 1>>
Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
1. Build up the drivers from the source code
make
2. Install the driver to the kernel
make install
reboot
3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
ifconfig wlan0 up 
Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name, 
since it may change wlan0 to wlan1,etc.
<<Method 2>>
Or only load the driver module to kernel and start up nic.
1. Build up the drivers from the source code
make
2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/
cp -rf firmware/RTL8192SU /lib/firmware
or
cp -rf firmware/RTL8192SU /lib/firmware/(KERNEL_VERSION)
Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware
3. Load driver module to kernel and start up nic.
./wlan0up
Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
after run ./wlan0up, please run ./wlan0down first, then it should 
be ok..
Note: If you see the message of "unkown symbol" during ./wlan0up, it
is suggested to build driver by <<Method 1>>.
 
I am a total newb so please break it to me easy and simply. I've only been using Ubuntu / linux for a week.

---

### Post by nothingspecial on 2010-07-07
Have you tried just plugging it in?

---

### Post by baguahsing on 2010-07-07
Yes, and nothing happens. I recall looking for the rtl8192su driver and it does not exist in lib/firmware, so I have to install it.

---

### Post by nothingspecial on 2010-07-07
Follow these instructions

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by baguahsing on 2010-07-07
The cd has drivers for linux, so I was hoping to use those instead of ndiswrapper.  I won't be able to have access to my laptop until I get home.

---

### Post by nothingspecial on 2010-07-07
Copy the linux drivers to your Desktop

Open a terminal

type ```
 cd ~/Desktop/folder

```Replace folder with the exact name of the folder on your desktop
```

make
sudo make install
```reboot

That should be it according to the instructions.

---

### Post by nothingspecial on 2010-07-07
Appologies for suggesting ndiswrapper but I couldn`t read the instructions at first

---

### Post by baguahsing on 2010-07-07
The linux folder on the cd has one file which ends with .tar.gz. Does 10.04 have the ability to unzip this file or do I have to open synaptic and install some sort of unzip program. Thanks for being patient.  The file has the following (I'm on my work computer - don't tell my boss!)
 
folders - firmware, HAL, and ieee80211
files - makefile
         radiopower.sh
         runwpa
         wireless-rtl-ac-dc-power.sh
         wlan0up
         wlan0down
         wlan0dhcp
         wpa1.conf
         ifcfg-wlan0
         wpa-supplicant-0.6.9.tar.gz
         release_note
         readme.txt (a portion of which I posted earlier)
So which one(s) is/are the drivers?

---

### Post by nothingspecial on 2010-07-07
> **baguahsing said:**
> The linux folder on the cd has one file which ends with .tar.gz. Does 10.04 have the ability to unzip this file or do I have to open synaptic and install some sort of unzip program. Thanks for being patient.  The file has the following (I'm on my work computer - don't tell my boss!)
 
folders - firmware, HAL, and ieee80211
files - makefile
         radiopower.sh
         runwpa
         wireless-rtl-ac-dc-power.sh
         wlan0up
         wlan0down
         wlan0dhcp
         wpa1.conf
         ifcfg-wlan0
         wpa-supplicant-0.6.9.tar.gz
         release_note
         readme.txt (a portion of which I posted earlier)
So which one(s) is/are the drivers?

None of them as such, they will become the driver after you have compiled it.

Copy the file to your desktop Double click on it and choose to extract it to your desktop

Open a terminal (Accessories > Terminal) in your menu.

Type ```
sudo apt-get install build-essential
```


You will have to type your password, you won`t see it, just type it then  press enter

That will install tools necessary for compiling source code, you will need a wired connection to do this. If you can`t get one try everything else anyway or it might be on the live cd you installed from (we`ll cross that bridge if we come to it.)

Drag the extracted file on your desktop into the terminal.

Then type ```
make
```

followed by ```
sudo make install
```

Then reboot.

---

### Post by baguahsing on 2010-07-07
Thanks, I'll try it out when I get home and will post the results.

---

### Post by baguahsing on 2010-07-07
ok, I was able to make but when I tried to sudo make install I recieved the following error
 
Makefile:11: /config: No such file or directory
make: *** No rule to make target '/config'.  Stop.
 
I did the sudo make install from the same directory as I was in when I executed the make.   Whats wrong?

---

### Post by nothingspecial on 2010-07-08
Well lets try method 2 in the instructions
```

sudo cp -rf firmware/RTL8192SU /lib/firmware
```

```
./wlan0up
```

You might need a sudo before ./wlan0up

---

### Post by baguahsing on 2010-07-09
I tried the second option.  ./wlan0up gave me a permission denied.  So I tried sudo ./wlan0up and I got a command not found.  If I do a ls the file wlan0up is listed.  What next?

---

### Post by baguahsing on 2010-07-14
I used the updated driver from the Realtek website.  I extracted the file in terminal.  Then did a make followed by a insmod 8712u.ko.  Great, wlan0 now shows up in iwconfig.  I am able to connect using network manager.  When I reboot or shutdown and restart wlan0 does not exist and I have to make and insmod again for it to show up.  How do I make this the default on startup?  The internal wireless is listed as eth1, but I have been unable to make it work.  Do I need to blacklist it in order for my usb wireless adaptor to boot up by default?

---

### Post by Windy Peaks on 2010-09-05
Hey Folks:

I have been following along with Your thread as I too am at the same point You are.
wifi on when new realtek driver used, make and insmod 8712u.ko.
However I think that I am now having a problem connecting to my wifi network due toi the fact I followed the command line instruction fully but still first connected to My network through the GUI network manager. If You read to the very end of the realtek driver instructions it says that the command line and GUI network manager will create a conflict if You use both together.

It recommends that You disable the GUI network manager before using the command line option " ifconfig wlan0 up "
Anybody know how to do that ????


Your assistance is much welcomed.

Windy

---

### Post by ed3054 on 2010-11-02
hey guys, 

i solved this for my own system. however, i know nothing about linux, & it was my first time doing anything like this, so i'm just gonna write out what i did & hope you understand. i know *why* it worked, but could probably not tell you how. basically, the asus package is faulty, & you need to fix it during the installation. here goes... 

you'll need a wired connection (or a different wireless connection) on the same computer. you'll also need to login as root at one point, so make sure you know your password. *if you don't*, & you don't think you've ever set one, then from the taskbar click SYSTEM>ADMINISTRATION>USERS AND GROUPS. click UNLOCK, enter your own password, select the user called 'root', click PROPERTIES, and choose a password under the 'set password by hand' section. click OK, & you're done. 

next, you need basic installer & checkinstall, so if you don't already have them, open terminal & put this in: 

```
sudo apt-get install build-essential
sudo apt-get install checkinstall
```it will run a separate install for each, after each line of code, so give it time. you might also need to enter your password. then, copy the .bz2 file that asus supply on the cd (& on their website if you need it) to your hard drive. you can just do this in ubuntu, or terminal if you want to. it's simpler not to put it on the desktop (you'll see in a second) - i put mine in 

/home/user

replace 'user' with whatever your username/user folder is called

unpack the .bz2. you can do this in terminal, or in ubuntu just right-click it, select 'open in archive manager', then 'extract', & extract it to the same directory that the .bz2 file is in (/home/user). Then right-click the extracted folder, & re-name it 

asus

the next part of the process involves something that you may not have permission to do on your system - you'll need to log out & log in as root. if your system won't let you do this from the login screen, then restart, pressing ESCAPE during startup to get all of the startup options, & select 'safe mode' which will let you login as root, in terminal proper. 

once you're logged in as root, input

```
cd /home/user/asus
```replacing 'user' with your own username once again (not 'root'). then

```
make
```your system will now build an installation according to asus' instructions, which are faulty. let it do this, & when it's done, type 

```
sudo checkinstall
```checkinstall will run, alert you that part of the installation is missing, & offer to replace it with generic code to rectify the problem. take it up on this kind offer by entering

Y

when prompted. you now have a proper install, so input

```
sudo make install
```your system will install everything. once it's done, input

```
reboot
```the system will restart, & you can log in the normal way. you should have a working wireless card. 

sorry if the above seems overly-simplified or long - i tried to write the sort of thing that i would need in order to be able to follow, which is probably more basic than for you! 

if there are errors - it's because it was the first time i did anything like this, so either ask someone or use common sense. and good luck!

---

### Post by drillvoice on 2010-11-09
I followed these instructions,  but the checkinstall stage was unsuccesful.

========================= Installation results ===========================
make[1]: Entering directory `/home/joel/asus/HAL/rtl8192u'
make -C /lib/modules/2.6.35-22-generic/build M=/home/joel/asus CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
install -p -m 644 r8192s_usb.ko  /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install: cannot stat `r8192s_usb.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/joel/asus/HAL/rtl8192u'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

any thoughts?

---

### Post by zerothorder on 2010-12-03
[SIZE=4] I have solve this with [/SIZE][SIZE=4]windows wireless driver after try to install it through terminal for a few week.

before start don't forget to plug your device in usb port

1.go to [/SIZE][SIZE=4]ubuntu software center and install software name
    "windows wireless drivers"
[/SIZE][SIZE=4]3.insert driver disc (or download windows xp driver)[/SIZE]
[SIZE=4]2.after that go to system -> administration -> 
   windows wireless drivers
4."click install new driver" button
5.go to windows xp driver folder find file that have *.inf   
   extension and double click it

finish 

now your can click on internet connection button on bar that i don't know it's name (taskbar i guess) (near sound and mail botton) and access internet like windows does 




  





[/SIZE]

---

### Post by zerothorder on 2010-12-03
sorry for my bad english

---

### Post by sabraham22 on 2011-03-12
Thanks for the instructions ed3054.
I was able to install the drivers, but something weird is happening upon reboot. My screen goes blank. So I shut down the PC and removed the usb dongle and restarted and all was fine. But as soon as I plug in the USB-N10, my screen goes blank again and I have to reboot.

Please help.

Thanks!

---

