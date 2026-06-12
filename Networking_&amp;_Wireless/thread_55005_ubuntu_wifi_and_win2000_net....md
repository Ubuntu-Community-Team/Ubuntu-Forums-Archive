---
title: "ubuntu wifi and win2000 net..."
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by lucaflea on 2005-08-07
hi i bought a pirelli gate router and adsl modem. i installed it in win2000 and it works but now i want to configure it on my notebook in wich ubuntu is installed. i bought also a usb wireless adapter (iee802.11g). in the win cd there is a folder "linux" with a tar.gz file. what do i have to do with it?

in any case, is it possible to create a net between win2000 and ubuntu?
is it possible to share the adsl connection?

help... please....
luca

---

### Post by PeP on 2005-08-07
[QUOTE=lucaflea]hi i bought a pirelli gate router and adsl modem. i installed it in win2000 and it works but now i want to configure it on my notebook in wich ubuntu is installed. i bought also a usb wireless adapter (iee802.11g). in the win cd there is a folder "linux" with a tar.gz file. what do i have to do with it?

in any case, is it possible to create a net between win2000 and ubuntu?
is it possible to share the adsl connection?

help... please....
luca[/QUOTE]

usually when you have a tar.gz file you take this steps:
1. unzip:
tar -xvzf yourthing.tar.gz
2. go to the created folder
cd yourthing_versionnumber
3. configure
./configure
4. compile
make
5. install
sudo make install

but sometimes you just have to do
./thing.sh
instead of steps 3,4,5

once it unzipped, you shold read the README first.

You should also first check that the device is not supported natively by the linux kernel (a little bit of google), maybe you just need to activate a module.

And yes you can make a network with a linux machine and almost everything including win2k machines

---

### Post by lucaflea on 2005-08-07
if i can i'll post the guide i found in the cd...i don't understand anything....

---

### Post by lucaflea on 2005-08-07
this is the content of the read me file of the usb wireless adapter:

"
ZD1211 - linux driver for ZyDAS ZD1211 based usb 2.0 wlan adapters
------------------------------------------------------------------

Reqirements:
------------

- Kernel 2.4.x. I am developing the driver on 2.4.24, but it
  reportedly also works on 2.4.x. If your kernels version is less than
  2.4.22 (for example Red Hat 9.0 is 2.4.20-8), suggest to upgrade kernel 
  for better support on USB 2.0. 
  
- Kernel 2.6.x. This driver has been verify on 2.6.6 and 2.6.7.

- To build zd1211 you will need: Configured kernel source code for the 
  kernel you are running. Ideally, Configured means that you have at 
  least run 'make config', 'make menuconfig', or 'make xconfig'. If your
  platform is not SMP system, please don't config SMP supported, because
  when module loaded, this will make unresolved symbol..
     
- Make sure your kernel usb 2.0 support is running
  - Use lsmod to check "ehci-hcd" module is loaded.
  - If host is not support usb 2.0, zd1211 will run under pure-b mode.


Building zd1211:
------------

1)  untar the package using the command:
    tar zxvf zd1211-XXXX.tar.gz

2)  edit the Makefile to make sure the path of KERNEL_SOURCE is your
    are running, and the kernel version is correctly configure.
	
3)  Under zd1211-XXXX/zdsta directory, use "make clean", "make", "make install"
    to make and install driver.	


Running:
--------

- If you have hotplug installed, the drivers should now be loaded. If not,
  load them by hand: modprobe -v zd1211 
  (or Under zd1211-XXXX/zdsta directory use "insmod zd1211.o" for kernel 2.4.x, 
  "insmod zd1211.ko" for kernel 2.6.x)

- Check if the modules are loaded with lsmod. It should look like this:
  ...
  zd1211          183576   0  (unused)
  ...

- Run 'ifconfig <iface> <your IP address>'

- Run 'iwconfig <iface> ' to configure the wireless setting, here are 
  some examples, more detail information please check with 'man iwconfig'.
  Example:
  iwconfig <iface> essid "My Network"   //Set essid
  iwconfig <iface> channel 1            //Set channel
  iwconfig <iface> mode Managed (Station mode)	//Set operation mode
  iwconfig <iface> mode Ad-Hoc (Ah-Hoc mode)
  iwconfig <iface> rts 512             //Set rts threshold
  iwconfig <iface> frag 512            //Set fragment threshold
  iwconfig <iface> key s:password [2]  //Set encryption key
  iwconfig <iface> power on/off        //Set power-save mode
  ......


Private Parameters:
------------------

In addition to the parameters of iwconfig, some can be set by iwpriv:
- open system authentication: iwpriv <iface> set_auth 0
- shared key authentication:  iwpriv <iface> set_auth 1
Be aware that shared key authentication requires a WEP key.

- long preamble: iwpriv <iface> set_preamble 0
- short preamble: iwpriv <iface> set_preamble 1
- iwpriv <iface> get_preamble	//will display the current preamble type

- List current BSS information:iwpriv <iface> list_bss
  You can use "dmesg" to check the result.



Note:
----

- You can modify the script file "sta" to enable Station function.
  "sta en" Enable STA function
  "sta dis" Disable STA function
- I have tested the driver under Red-Hat 9.0, It's unstable than kernel 2.4.24.
  So please update the kernel.



Version:
--------
-4715
 -Support kernel 2.6.x
 -Fixed bug: DHCP will hard to get IP problem.
 -Support iwpriv command
 	iwpriv <iface> set_mac_mode	 mac_mode	//1: Mixed Mode 
 											//2: Pure G Mode
 											//3: Pure B Mode 
		 
 	iwpriv <iface> get_mac_mode				//display current Mac Mode
 
-4630
 -Fixed Ad-Hoc mode can't work problem.
 -Support Roamming.
 -Support iwlist <iface> scan(ning) command.
 -Support iwpriv command
 	iwpriv <iface> connect cell_number	//the cell_number can be get 
 										//from the result of 
 										//iwlist <iface> scan(ning) command
 										 
 	iwpriv <iface> dbg_flag				//set debug level, default is 0

 -Fiexd Chairot multicast can't work problem.	
 -Fixed Ack timeout problem. 
 
 
-4621
 -First release version.
 -WPA, 802.1X with dynamic key exchange are not supported.
 -Watchdog function was not fully implementated.
 -Apdbg.c provides basic debug command for driver development.
 -Airoha RF chip is not verified.
 -Support basic wireless extension setting.
 -Fixed	iwconfig will show wrong essid information.
 -Roaming is not fully verified.
 	


Known Bugs:
-----------


someone help me please writing the steps i have to follow

---

### Post by varunus on 2005-08-07
First, it looks like you'll need ethernet to install these drivers.  If you don't have a working net connection in linux, post back here; there are alternatives, but they're not as pretty.

-Kernel 2.6.x support
  Score!  That's what Ubuntu uses, so you'll be able to use this driver.  Here are step by step instruction.  I've posted terminal commands here since its easier for me to just tell you what to type; most of the stuff below can be done in GUI, but it'll be easier if you can just copy and paste.

Here's a step by step guide:

**Step 1 - Kernel Sources** 
Open up a terminal/konsole (if you're on KDE) and type the following:
```
sudo apt-get install linux-headers-2.6.10-5-386
cd /usr/src/
ln -s linux-headers-2.6.10-5-386 linux
```

These commands do something the driver needs you to do; it installs the configuredsource code for the linux kernel.

**Step 2 - Extracting the Driver** 
In the same terminal, use the "cd" command to change to the directory where you copied the driver (preferably somewhere in your home folder).  Then, execute the following:
```
tar zxvf zd1211-XXXX.tar.gz
```
If this command fails, use
```
sudo tar zxvf zd1211-XXXX.tar.gz
```
instead.
The XXXX will vary, its going to be a number, you'll know when you copy over the driver. (don't actually type xxxx)

This should have made a new directory called zd1211-XXXX.  "cd" inside of it.

**Step 3 - Configure the Driver** 
There should now be a file called "Makefile" in the directory you're in.  Open it:
```
sudo gedit Makefile
``` 
Or, if you're on KDE, use sudo kwrite.
Enter your password when asked.
(MAKE SURE WORD WRAP IS OFF)

Use the search/find function to find the text "KERNEL_SOURCE"
There should be a path listed there; change it to /usr/src/linux

Use the search/find function to find VERSION (or kernel_version, not sure)
Change the version parameter to say something like KERNEL_VERSION=2.6.10-5-386

Save and exit gedit or kwrite.

**Step 4 - Install the Driver** 
Now, type "cd zdsta" into the terminal.
Type the following:
```
make clean
make
sudo make install
#enter your password when asked
``` 
Now type "sudo modprobe -v zd1211"
And you're done!  You can configure it through the GNOME networking panel or the KDE networking control center module now (graphically).

---

### Post by lucaflea on 2005-08-07
i don't have a working net connection but i'll try to do what you wrote. thanx.

but, if i can do all the things you said will i be able to navigate the web?or will i need something more?

---

### Post by varunus on 2005-08-07
Crap, I forgot also; above, you'll need the "build-essential" package before you do this.  This will allow you to compile the module.  To install it, type "sudo apt-get install build-essential" at a terminal (when you have ethernet).

If you don't have a working net connection, this will be trickier.  You'll need to manually download all of these packages in Windows and install them onto your ubuntu.  I'm busy now, but I can compile a large list of URL's for you to download in Windows; you can then burn them to CD or copy them over to your Ubuntu from your Windows partition (here's a guide on how to mount a windows partition: [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

If you give me till tomorrow morning, I can have a large list of files for you to download.  Sorry about this hassle...

Once you do everything, you'll be able to get on the net; its all you need!

---

### Post by lucaflea on 2005-08-08
i'm waiting  ;-) 

did you mean that i need to configure a net between ubuntu and win?

and is it possible to download all the things i need (lookin' in synaptic) and manually install them?

---

### Post by PeP on 2005-08-08
[QUOTE=lucaflea]i don't have a working net connection but i'll try to do what you wrote. thanx.

but, if i can do all the things you said will i be able to navigate the web?or will i need something more?[/QUOTE]
you'll have to configure the network  interface
the basic setting (no wep key, no static address) is in
/etc/network/interfaces 
```

 iface <ifname> inet dhcp

```
where <ifname> is something like wlan0, ath0, eth1, zd0 ... 
to know which one it is just type
/sbin/ifconfig -a

If you're lost there must be a  good networking howto for debian systems.

Then your network is on, but you will still need applications to browse the web (eg firefox comes with ubuntu) and to  make a commmunication between the two boxes (file servers, samba, printer sharing, network games ... it' s up to you)

---

### Post by varunus on 2005-08-08
Actually, the above poster is just trying to do things the hard way; both Ubuntu and Kubuntu have graphical tools that can do almost everything you need to get on the net if you just use ethernet or wireless. ADSL, you may need to do some funky stuff if you have to login to your DSL, but otherwise, graphical tools!  Whoo!

Packages in Ubuntu can be downloaded in Windows and then installed manually. Unfortunately, you can't do this in Synaptic; you have to use the console.  I've outlined everything step by step below.

Here is what you should do before you install the driver as I described above.  Consider this step 0.

Here's the list of packages for you.  Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and use the search, make sure you're searching in hoary.  This assumes you have a working internet connection in Windows and either your win partition mounted in Ubuntu, a USB drive, or CD-R you can use.  You can manually download packages; but make sure to get all of their dependencies too, so you can install them properly.  I've compiled what I think is a full list of everything you need below.

Search for and download all of the following packages (this will be a large download):

libc6-dev
linux-kernel-headers
gcc
gcc-3.3
gcc-3.3-base
cpp
cpp-3.3
g++
g++-3.3
libstdc++5
libstdc++5-3.3-dev
libgcc1
make
linux-headers-2.6.10-5
linux-headers-2.6.10-5-386

Download all of the debian packages (.deb extension) for the above, and copy them to a folder you can remember, a USB drive, or a CD.  Then, reboot to Ubuntu.  Insert the USB drive or CD once GNOME comes up.  Then, open up a terminal and "cd" to the correct directory (should be /media/cdrom0 for a CD, will be /media/something for a USB drive, will vary for win partiton).

Execute the following:
```
cp *.deb ~/
cd ~
sudo dpkg -i *
``` 

Hopefully that's all the dependencies above; I think it should be.

Once this is done, you can follow the howto as above, but skip any "apt-get" commands you see.

Good luck.

---

### Post by lucaflea on 2005-08-09
hi i could install linux headers thorugh boot cd...
but now i can't "see" my usb wireless pen....
i think i installed all the drivers but.... in the net panel there is no "lo".....

i write "iwconfig lo" it says "no wireless extension....

---

### Post by PeP on 2005-08-09
[QUOTE=lucaflea]hi i could install linux headers thorugh boot cd...
but now i can't "see" my usb wireless pen....
i think i installed all the drivers but.... in the net panel there is no "lo".....

i write "iwconfig lo" it says "no wireless extension....[/QUOTE]
iwconfig has a w fir wireless
lo is the loopack network interface, It allows you to connect to your computer, and it's not wireless -> use ifconfig

---

### Post by varunus on 2005-08-09
If you followed my instructions, the drivers should have installed.  Can you post the output of lsmod in a terminal?

---

### Post by PeP on 2005-08-09
> Actually, the above poster is just trying to do things the hard way; both Ubuntu and Kubuntu have graphical tools that can do almost everything you need to get on the net if you just use ethernet or wireless. ADSL, you may need to do some funky stuff if you have to login to your DSL, but otherwise, graphical tools! Whoo! 

yeah whooo   ](*,) !


whoo only for desktops , as far as I can see, a good knowledge of how it works the debian way is necessary to make smart things (using whereami/ or ifplugd), configuring wifi is often used for laptops, so I assume this one is for a laptop.


I consider that static configuration is not suitable for a laptop, so a good beginning is to learns how it works, then how to make it usefull.

If you have a good gui for ubuntu  that configures your network correctly for a mobile platform (one that you use at work, at home, at your parent's, in the train ...) so I mean configure it dynamically (interface and encryption when you plug a cable or step near an ap, then location detection for extra things (mount samba shares @ your job, nfs @ home, configure proxies, mail gateways for smpt and pop if possible ...). If you have such a nice GUI please do me a real favor: let me know, send me a pm or even a mail. You will make my life easier.

---

### Post by lucaflea on 2005-08-09
i can't post it.... my floppy doesn't want to help me...
is there something i have to read and post here??


but....let's suppose i want to do a simple ethernet net with my router. what do i have to do???

---

### Post by PeP on 2005-08-09
for an eth net:

I suppose your router provides dhcp (automatic network configuration), 
plug a cable 
use a beautiful GUI to connect via dhcp
or
sudo ifconfig eth0 up
sudo dhclient eth0

if you have any problem check that you have eth0 
ifconfig -a
and that your router has dhcp enabled.

---

### Post by jr_G-man on 2005-08-27
[QUOTE=lucaflea]this is the content of the read me file of the usb wireless adapter:

"
ZD1211 - linux driver for ZyDAS ZD1211 based usb 2.0 wlan adapters
------------------------------------------------------------------

Reqirements:
------------

- Kernel 2.4.x. I am developing the driver on 2.4.24, but it
  reportedly also works on 2.4.x. If your kernels version is less than
  2.4.22 (for example Red Hat 9.0 is 2.4.20-8), suggest to upgrade kernel 
  for better support on USB 2.0. 
  
- Kernel 2.6.x. This driver has been verify on 2.6.6 and 2.6.7.

- To build zd1211 you will need: Configured kernel source code for the 
  kernel you are running. Ideally, Configured means that you have at 
  least run 'make config', 'make menuconfig', or 'make xconfig'. If your
  platform is not SMP system, please don't config SMP supported, because
  when module loaded, this will make unresolved symbol..
     
- Make sure your kernel usb 2.0 support is running
  - Use lsmod to check "ehci-hcd" module is loaded.
  - If host is not support usb 2.0, zd1211 will run under pure-b mode.


Building zd1211:
------------

1)  untar the package using the command:
    tar zxvf zd1211-XXXX.tar.gz

2)  edit the Makefile to make sure the path of KERNEL_SOURCE is your
    are running, and the kernel version is correctly configure.
	
3)  Under zd1211-XXXX/zdsta directory, use "make clean", "make", "make install"
    to make and install driver.	


Running:
--------

- If you have hotplug installed, the drivers should now be loaded. If not,
  load them by hand: modprobe -v zd1211 
  (or Under zd1211-XXXX/zdsta directory use "insmod zd1211.o" for kernel 2.4.x, 
  "insmod zd1211.ko" for kernel 2.6.x)

- Check if the modules are loaded with lsmod. It should look like this:
  ...
  zd1211          183576   0  (unused)
  ...

- Run 'ifconfig <iface> <your IP address>'

- Run 'iwconfig <iface> ' to configure the wireless setting, here are 
  some examples, more detail information please check with 'man iwconfig'.
  Example:
  iwconfig <iface> essid "My Network"   //Set essid
  iwconfig <iface> channel 1            //Set channel
  iwconfig <iface> mode Managed (Station mode)	//Set operation mode
  iwconfig <iface> mode Ad-Hoc (Ah-Hoc mode)
  iwconfig <iface> rts 512             //Set rts threshold
  iwconfig <iface> frag 512            //Set fragment threshold
  iwconfig <iface> key s:password [2]  //Set encryption key
  iwconfig <iface> power on/off        //Set power-save mode
  ......


Private Parameters:
------------------

In addition to the parameters of iwconfig, some can be set by iwpriv:
- open system authentication: iwpriv <iface> set_auth 0
- shared key authentication:  iwpriv <iface> set_auth 1
Be aware that shared key authentication requires a WEP key.

- long preamble: iwpriv <iface> set_preamble 0
- short preamble: iwpriv <iface> set_preamble 1
- iwpriv <iface> get_preamble	//will display the current preamble type

- List current BSS information:iwpriv <iface> list_bss
  You can use "dmesg" to check the result.



Note:
----

- You can modify the script file "sta" to enable Station function.
  "sta en" Enable STA function
  "sta dis" Disable STA function
- I have tested the driver under Red-Hat 9.0, It's unstable than kernel 2.4.24.
  So please update the kernel.



Version:
--------
-4715
 -Support kernel 2.6.x
 -Fixed bug: DHCP will hard to get IP problem.
 -Support iwpriv command
 	iwpriv <iface> set_mac_mode	 mac_mode	//1: Mixed Mode 
 											//2: Pure G Mode
 											//3: Pure B Mode 
		 
 	iwpriv <iface> get_mac_mode				//display current Mac Mode
 
-4630
 -Fixed Ad-Hoc mode can't work problem.
 -Support Roamming.
 -Support iwlist <iface> scan(ning) command.
 -Support iwpriv command
 	iwpriv <iface> connect cell_number	//the cell_number can be get 
 										//from the result of 
 										//iwlist <iface> scan(ning) command
 										 
 	iwpriv <iface> dbg_flag				//set debug level, default is 0

 -Fiexd Chairot multicast can't work problem.	
 -Fixed Ack timeout problem. 
 
 
-4621
 -First release version.
 -WPA, 802.1X with dynamic key exchange are not supported.
 -Watchdog function was not fully implementated.
 -Apdbg.c provides basic debug command for driver development.
 -Airoha RF chip is not verified.
 -Support basic wireless extension setting.
 -Fixed	iwconfig will show wrong essid information.
 -Roaming is not fully verified.
 	


Known Bugs:
-----------


someone help me please writing the steps i have to follow[/QUOTE]

I have also run into some problems with this.  I have posted my experiences so far here:  [http://www.bloglines.com/blog/jrgman?id=5](http://www.bloglines.com/blog/jrgman?id=5)

I have some updates.  When I get them typed up, I can notify you if you like.

---

