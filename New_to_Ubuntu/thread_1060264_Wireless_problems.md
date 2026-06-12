---
title: "Wireless problems"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Witan on 2009-02-04
I have the Broadcom Corporation BCM4322 802.11a/b/g/n Wireless chip in my computer.  I installed the Broadcom STA wireless driver, but the light on my computer for my wireless chip shows that the chip is turned off, even though the chip shows up when I run lspci in the terminal.

While searching for a solution to the problem, I came across this:

[http://linuxwireless.org/en/users/Drivers/b43#FAQ-Frequentlyaskedquestions]("http://linuxwireless.org/en/users/Drivers/b43#FAQ-Frequentlyaskedquestions")

It apparently says that there is no support yet for this chip.

Does this mean that I just have to wait until this version of the chip is supported?  Is there something I can do?

---

### Post by avtolle on 2009-02-04
My take on what was reported in the link is that there is no support for the N draft, but I think the card should do OK for a/b/g. Others may well have different thoughts, and as I'm no expert, I'll cede to them.

---

### Post by mpl34 on 2009-02-04
Im new to this but i suggest using the broadcom driver found [here]("http://www.broadcom.com/support/802.11/linux_sta.php"),

Make a directory hybrid in your home folder and copy the download Driver given in the above link

Bring up the knsole and go to the directory u placed the download driver file
ie.  cd ~/hybrid

Uncompress the file:
tar -xzf hybrid*.tar.gz 

Then compile the file cleaning the install directury first (just incase there is something previously there
make  -C /lib/modules/`uname -r`/build M=`pwd` clean
make -C /lib/modules/`uname -r`/build M=`pwd`

Remove any current wireless modules:
sudo modprobe -r b43 b44 ssb ndiswrapper wl

Load the nessecary modules: (make sure you are still within the directory the driver has been extracted ie. ~/hybrid)
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko

Restart your network:

sudo /etc/init.d/networking restart

This worked for the BCM4328 your may have to check that this driver is suitable for the BCM4322 but i would assume so.

---

### Post by mpl34 on 2009-02-04
Just checked and yes this driver can be used for the BCM4322 model

---

### Post by Witan on 2009-02-04
> **mpl34 said:**
> Im new to this but i suggest using the broadcom driver found [here]("http://www.broadcom.com/support/802.11/linux_sta.php"),

Make a directory hybrid in your home folder and copy the download Driver given in the above link

Bring up the knsole and go to the directory u placed the download driver file
ie.  cd ~/hybrid

Uncompress the file:
tar -xzf hybrid*.tar.gz 

Then compile the file cleaning the install directury first (just incase there is something previously there
make  -C /lib/modules/`uname -r`/build M=`pwd` clean
make -C /lib/modules/`uname -r`/build M=`pwd`

Remove any current wireless modules:
sudo modprobe -r b43 b44 ssb ndiswrapper wl

Load the nessecary modules: (make sure you are still within the directory the driver has been extracted ie. ~/hybrid)
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko

Restart your network:

sudo /etc/init.d/networking restart

This worked for the BCM4328 your may have to check that this driver is suitable for the BCM4322 but i would assume so.

I'm brand new to Linux, could anybody explain that a little more clearly?

---

### Post by avtolle on 2009-02-04
I'll try to give some assistance.

First, go to the site linked and download the driver for your architecture. It will no doubt d/l to your desktop.

Second, open a terminal (Applications>Accessories>Terminal)

Third, do in terminal ```
mkdir hybrid
cd Desktop
cp (name of driver file) /hybrid #copies the driver from your desktop to the /hybrid directory
cd ~/hybrid #change to the hybrid directory
tar -xzf hybrid*.tar.gz #extracts tarball
make  -C /lib/modules/`uname -r`/build M=`pwd` clean #loads needed kernel modules, and cleans out the installation directory.
make -C /lib/modules/`uname -r`/build M=`pwd`
sudo modprobe -r b43 b44 ssb ndiswrapper wl #removes any existing driver modules
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko #loads the necessary modules into the kernel
sudo /etc/init.d/networking restart #restarts your network
```Before doing this, once you open the terminal before doing the mkdir command, be sure to install build-essential ```
sudo apt-get install build-essential
```Then, exit the terminal. Confused? Ask questions.

---

### Post by Witan on 2009-02-04
How can I figure out whether the 32 bit or 64 bit one is appropriate?  I had the 64 bit version of Vista, but I don't know which of those two versions of Ubuntu I have.

If it helps any, sudo lshw shows this for the network:

 *-network
                description: Wireless interface
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth1
                version: 01
                serial: 00:21:00:79:4e:18
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless


But looking through the list, I see a mix of 32 bits and 64 bits for different things.

---

### Post by Witan on 2009-02-04
uname -a yields this

revenant@revenant-laptop:~$ uname -a
Linux revenant-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

and from what I'm reading, i686 means 32 bit

I'm confused :-P

---

### Post by mpl34 on 2009-02-04
Basically from my understanding the per-installed b44 driver is not compatiable with a large variety of the broadcom drivers, however broadcom has recently released a drivers for BCM4322 based chipsets for a linux environment.

What i have suggested is to download the tar file into a directory in your home folder (i have user /home/michael/Driver/hybrid).

When you open the terminal (command based prompt screen) the default directory u will be positioned in is /home/user, my first command "cd ~/hybrid" moves you into the directory /home/user/hybrid that you should have set up to download the tar.gz file into. (you can use a different directory, up to you)

> tar -xzf hybrid*.tar.gz
is obviously used to untar(unzip) the file into the current directory (/home/user/hybrid)

> make -C /lib/modules/`uname -r`/build M=`pwd` clean
 will clean the directory into which the driver is complied, this is just incase you have tried to compile driver previously.

> make -C /lib/modules/`uname -r`/build M=`pwd` 
is used to compile the driver into the appropriate directory in the root folder.

> sudo modprobe -r b43 b44 ssb ndiswrapper wl 
this is used to remove any wireless drivers that are currently running so that the broadcom can boot. this is because the broadcom driver will have problems while ssb b44 and b43 is in use. ndiswrapper is included from those ppl who have tried to install the driver using the windows driver provided by broadcom, this shouldnt be a problem for you as for wl not to sure because that is what you a trying to kick start, again im very new to this and do not fully understand and may be slightly incorrect.

These following commands are to start the wl module which is used to recognise the broadcom driver, again new and probably incorrect in my explanation.
> sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko sudo insmod wl.ko <------ note* this code still assumes you are in the home/user/hybrid directory, if you are not a good way to run it would be sudo insmod /home/user/hybrid/wl.ko should do the same thing.

You can then run the command > sudo modprobe b44 to start the enthernet driver but maynot be needed if your using wireless.

Finally, > sudo /etc/init.d/networking restart will restart your network with the current driver inplace ie. wl (the broadcom driver for linux) and b44 the preinstalled ehternet driver.

Hope this helps i've only been using linux for a week and i'm currently sitting at work as bored as hell so thought i'd giv ashot at explaining the process even tho i'm slightly unsure myself.

---

### Post by mpl34 on 2009-02-04
One more thing that may be useful (i'm probably jumping the gun here) but modifying your rc.local file. 

This is because when you reboot your system the linux drivers will start up, the b43, b44 and ssb driver and therefore the broadcom driver will not be able to load into the kernel. therefore by modifying the rc.local file it will automatically run the nessecary commands to load the broadcom driver that you would otherwise have to do manually after every boot.

Here's how:

> sudo nano /etc/rc.local

then it will say something along the lines of this does nothing by default, from memory

then add the following anywhere in the script

> modprobe -r b43 b44 ssb ndiswrapper wl
modprobe ieee80211_crypt_tkip
insmod /home/user/hybrid/wl.ko
modprobe b44
/etc/init.d/networking restart

exit by ctrl+z (from memory) press y to save and enter to save it to /etc/rc.local.

Now your wireless should be running automatically after rebooting

---

### Post by avtolle on 2009-02-04
If using nano, Ctrl-o to write, return to accept the name of the file, and ctrl-x to exit.

---

### Post by Witan on 2009-02-04
insmod wl.ko didn't work.  Here's what I got.

> revenant@revenant-laptop:~$ sudo insmod /home/user/hybrid/wl.ko
insmod: can't read '/home/user/hybrid/wl.ko': No such file or directory
revenant@revenant-laptop:~$ 

---

### Post by avtolle on 2009-02-04
> **Witan said:**
> insmod wl.ko didn't work.  Here's what I got.
Command should be, I believe, ```
sudo insmod /home/revenant/hybrid/wl.ko
```if revenant is your user name, user being a placeholder for your user name.

---

### Post by Witan on 2009-02-04
Ah, didn't catch that....but it still doesn't work :-(

> revenant@revenant-laptop:~$ sudo insmod /home/revenant/hybrid/wl.ko
insmod: can't read '/home/revenant/hybrid/wl.ko': No such file or directory
revenant@revenant-laptop:~$ 

---

### Post by mpl34 on 2009-02-04
Try this
> sudo rmmod wl
sudo insmod wl.ko
in the hybrid directory

to get to the hybird directory typ cd /hybrid (cd means change directory)

---

### Post by Witan on 2009-02-04
It didn't work (and I remembered to put the tilde before the slash ;-) )

> revenant@revenant-laptop:~$ cd ~/hybrid
revenant@revenant-laptop:~/hybrid$ sudo rmmod wl
[sudo] password for revenant: 
ERROR: Module wl does not exist in /proc/modules
revenant@revenant-laptop:~/hybrid$ 

---

### Post by mpl34 on 2009-02-04
Hey sorry i've just been out for lunch i suggest trying again from start as 
> make -C /lib/modules/`uname -r`/build M=`pwd` clean  will clean the directory the driver is installed into. And then follow through the process again

Make sure you start by changing your directory to hybrid and run each command please post the outcome and i may be able to help.

---

### Post by Witan on 2009-02-04
Another question: I'm not sure whether I need the 32 bit or 64 bit driver.  My computer is 64 bit capable, I had 64 bit Vista, my network card (lshw) shows up as being 64, but my system is i686, which, from what I've read, means a 32 bit system.

---

### Post by mpl34 on 2009-02-04
One thing to make sure of is that 
```
sudo modprobe ieee80211_crypt_tkip
```
Is run before ```
sudo insmod wl.ko
```
as i believe the insmod command is dependent on the modprobe ieee80211_crypt_tkip

---

### Post by mpl34 on 2009-02-04
Ok im not too sure about the i686 thing im a newb too, but if you have installed 32-bit ubuntu then u'll need the 32-bit driver

---

### Post by Witan on 2009-02-04
Think I can use 32 bit even if I have 64?  How can I find out?

---

### Post by mpl34 on 2009-02-04
I dnt think you can but possibly ive never owned a 64-bit system so never ran into the problem,

---

### Post by mpl34 on 2009-02-04
From [this]("http://support.microsoft.com/kb/946765") i would say no 32-bit drivers are not compatible with a 64-bit OS

---

### Post by mpl34 on 2009-02-04
This link [here]("http://www.linuxquestions.org/questions/linux-software-2/stupid-q-how-to-determine-version-64-bit-or-32-bit-164741/"), suggests that yes i686 is a 32-bit OS

---

### Post by Witan on 2009-02-04
Hmm...I tried several times to copy the file to the "hybrid" folder with the Terminal, but it didn't work, I had to use the GUI to do it.

I wonder why that happened, and I wonder if it has anything to do with this process not working.

---

### Post by Witan on 2009-02-04
The last step isn't working.

Here's what I get:

> revenant@revenant-laptop:~$ cd ~/hybrid
revenant@revenant-laptop:~/hybrid$ tar -xzf hybrid*.tar.gz
revenant@revenant-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
revenant@revenant-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd`make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  LD      /home/revenant/hybrid/built-in.o
  CC [M]  /home/revenant/hybrid/src/wl/sys/wl_linux.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/revenant/hybrid/src/include/linuxver.h:38,
                 from /home/revenant/hybrid/src/wl/sys/wl_linux.c:34:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/revenant/hybrid/src/include/linuxver.h:38,
                 from /home/revenant/hybrid/src/wl/sys/wl_linux.c:34:
include/linux/mmzone.h:218: error: &#8216;MAX_NR_ZONES&#8217; undeclared here (not in a function)
In file included from /home/revenant/hybrid/src/include/linuxver.h:63,
                 from /home/revenant/hybrid/src/wl/sys/wl_linux.c:34:
include/linux/mm.h:438:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:486:62: warning: "NR_PAGEFLAGS" is not defined
make[1]: *** [/home/revenant/hybrid/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/revenant/hybrid] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
revenant@revenant-laptop:~/hybrid$ sudo modprobe -r b43 b44 ssb ndiswrapper wl
revenant@revenant-laptop:~/hybrid$ sudo modprobe ieee80211_crypt_tkip
revenant@revenant-laptop:~/hybrid$ sudo insmod wl.ko
insmod: can't read 'wl.ko': No such file or directory
revenant@revenant-laptop:~/hybrid$ 

---

### Post by mpl34 on 2009-02-04
Hey sorry i've been away in a meeting.

I did not get this error however i have found some information regarding to this and i would suggest trying to run the commands as follows

```
make -C /lib/modules/`uname -r`/build M=`pwd` clean
make prepare
make -C /lib/modules/`uname -r`/build M=`pwd`
modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo /etc/rc.d/network restart
```
Again insure you are in the hybird directory for the insmod command. I hope this works good luck

---

### Post by mpl34 on 2009-02-04
Heres a copy of my output from these 2 commands.

```
michael@michael-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd` clean

make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

michael@michael-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd`

make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
LD /home/michael/hybrid/built-in.o
CC [M] /home/michael/hybrid/src/wl/sys/wl_linux.o
CC [M] /home/michael/hybrid/src/wl/sys/wl_iw.o
CC [M] /home/michael/hybrid/src/shared/linux_osl.o
/home/michael/hybrid/src/shared/linux_osl.c: In function ‘osl_printf’:
/home/michael/hybrid/src/shared/linux_osl.c:456: warning: format not a string literal and no format arguments
LD [M] /home/michael/hybrid/wl.o
Building modules, stage 2.
MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/michael/hybrid/wl.o
see include/linux/module.h for more information
CC /home/michael/hybrid/wl.mod.o
LD [M] /home/michael/hybrid/wl.ko
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
```

---

### Post by Witan on 2009-02-04
It says that there is no rule to make the target "build"

Here's what I get:

> revenant@revenant-laptop:~$ cd ~/hybrid
revenant@revenant-laptop:~/hybrid$ make -C /lib/modules/`uname -r` /build M=`pwd` clean
make: Entering directory `/lib/modules/2.6.27-11-generic'
make: *** No rule to make target `/build'.  Stop.
make: Leaving directory `/lib/modules/2.6.27-11-generic'
revenant@revenant-laptop:~/hybrid$ make prepare
make: *** No rule to make target `prepare'.  Stop.
revenant@revenant-laptop:~/hybrid$ 

---

### Post by Witan on 2009-02-04
I tried again from the beginning, with the same result.

> revenant@revenant-laptop:~$ cd ~/hybrid
revenant@revenant-laptop:~/hybrid$ tar -xzf hybrid*.tar.gz
revenant@revenant-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
revenant@revenant-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  LD      /home/revenant/hybrid/built-in.o
  CC [M]  /home/revenant/hybrid/src/wl/sys/wl_linux.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/revenant/hybrid/src/include/linuxver.h:38,
                 from /home/revenant/hybrid/src/wl/sys/wl_linux.c:34:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/revenant/hybrid/src/include/linuxver.h:38,
                 from /home/revenant/hybrid/src/wl/sys/wl_linux.c:34:
include/linux/mmzone.h:218: error: &#8216;MAX_NR_ZONES&#8217; undeclared here (not in a function)
In file included from /home/revenant/hybrid/src/include/linuxver.h:63,
                 from /home/revenant/hybrid/src/wl/sys/wl_linux.c:34:
include/linux/mm.h:438:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:486:62: warning: "NR_PAGEFLAGS" is not defined
make[1]: *** [/home/revenant/hybrid/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/revenant/hybrid] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
revenant@revenant-laptop:~/hybrid$ sudo modprobe -r b43 b44 ssb ndiswrapper wl
[sudo] password for revenant: 
revenant@revenant-laptop:~/hybrid$ sudo modprobe ieee80211_crypt_tkip
revenant@revenant-laptop:~/hybrid$ sudo insmod wl.ko
insmod: can't read 'wl.ko': No such file or directory
revenant@revenant-laptop:~/hybrid$ 
revenant@revenant-laptop:~/hybrid$

---

### Post by Mattie03 on 2009-02-04
A wireless spy camera is embedded within a decorative mirror has been providing high quality security cameras & spy equipment.
____________________________________
The used of [outdoor security system]("http://www.video-surveillance-guide.com/wireless-outdoor-surveillance-systems.htm").

---

### Post by mpl34 on 2009-02-04
Did u include that make prepare command?

EDIT: Just checked your last post and yer i didn't notice the "make prepare" command do this after you run the clean and apparently it should fix it.

---

### Post by Witan on 2009-02-05
It says there's no rule to make "prepare"

> revenant@revenant-laptop:~$ cd ~/hybrid
revenant@revenant-laptop:~/hybrid$ tar -xzf hybrid*.tar.gz
revenant@revenant-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
revenant@revenant-laptop:~/hybrid$ make prepare
make: *** No rule to make target `prepare'.  Stop.
revenant@revenant-laptop:~/hybrid$ 

---

### Post by mpl34 on 2009-02-05
have you run sudo apt-get update? you could try running the following commands although i'm not sure if they would be of much help 
```
aptitude install module-assistant 
m-a prepare
```

---

