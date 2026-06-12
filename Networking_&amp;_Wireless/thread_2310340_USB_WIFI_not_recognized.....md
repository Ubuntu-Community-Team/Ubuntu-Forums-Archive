---
title: "USB WIFI not recognized...."
date: 2016-01-18
forum: Networking &amp; Wireless
---

### Post by rich37 on 2016-01-18
Attempting to install a generic usb wifi addapter.     Using the newest Ubuntu, just downloaded and installed.    The usb adapter isn't recognized, I have the linux driver on cd, but no idea to make it work.   I have typed sudo lsusb, and wifi is not listed.   Can someone help walk me thru the install???   TIA

---

### Post by chili555 on 2016-01-18
Please tell us what it reports:```
lsusb
```Thanks.

---

### Post by rich37 on 2016-01-18
Update.  If I open the home group, I see the linux file.  I have opened and extracted the file.  When in terminal I type sudo./rtl8192cus.run, it says no such file or directory.   Still can't figure out what I'm missing.    Any help is appreciated......

---

### Post by chili555 on 2016-01-18
Is the driver file old or new? Will it compile correctly for your kernel version and gcc version? What is your kernel version? Do you have the necessary build tools, linux headers, et al installed?

If you are unsure about these issues, then let's start at the beginning:> Please tell us what it reports:

```
lsusb
```

---

### Post by rich37 on 2016-01-18
> **chili555 said:**
> Please tell us what it reports:```
lsusb
```Thanks.

Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia card reader
Bus 001 Device 002: ID 0bda:818b Realtek Semiconductor Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 2635:0601
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2016-01-18
> 0bda:818b Realtek Semiconductor Corp.That device is *NOT* supported by the driver rtl8192cu. It is supported by the rare and elusive driver 8192eu.

I suggest you obtain a working internet connection by ethernet, tethered or whatever means possible. Open a terminal and do:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/jpostma/rtl8192eu.git
cd rtl8192eu
make
sudo make install
sudo modprobe 8192eu
```Is your wireless now working? If not, post:```
dmesg | grep 8192
```

---

### Post by rich37 on 2016-01-18
> **chili555 said:**
> That device is *NOT* supported by the driver rtl8192cu. It is supported by the rare and elusive driver 8192eu.

I suggest you obtain a working internet connection by ethernet, tethered or whatever means possible. Open a terminal and do:



OK, thanks for the reply.    I will obtain the correct driver, but I will have to transfer it to the needing computer via a usb drive.   Does drag and drop work in Ubuntu, or do I have to do it within the terminal window?

> **chili555 said:**
> That device is *NOT* supported by the driver rtl8192cu. It is supported by the rare and elusive driver 8192eu.

I suggest you obtain a working internet connection by ethernet, tethered or whatever means possible. Open a terminal and do:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/jpostma/rtl8192eu.git
cd rtl8192eu
make
sudo make install
sudo modprobe 8192eu
```Is your wireless now working? If not, post:```
dmesg | grep 8192
```

OK so far, In the terminal window, I get to cd rtl8192eu.  So it apparently sees that file.    When I type make and enter it says - make: *** No target specified and no makefile found.  Stop.
What am I doing wrong???

---

### Post by chili555 on 2016-01-18
> **rich37 said:**
> OK so far, In the terminal window, I get to cd rtl8192eu.  So it apparently sees that file.    When I type make and enter it says - make: *** No target specified and no makefile found.  Stop.
What am I doing wrong???Let's see what we see:```
cd rtl8192eu
```Press Enter. Now let's list the contents of the directory:```
ls
```Press Enter. You should see:```
clean  dkms.conf  ifcfg-wlan0  Kconfig  [COLOR="#FF0000"]Makefile[/COLOR]  platform   runwpa
core   hal        include      LICENSE  os_dep    README.md  wlan0dhcp

```If you see the Makefile, then proceed:```
make
```And so on to the end.

---

### Post by rich37 on 2016-01-18
Not sure what I'm missing but, I closed the terminal to start fresh.   At first I type in sudo lsusb.    That lists all the devices.   Then I type in cd rtl8192eu it returns- bash: cd: rtl8192eu: No such file or directory.    So from there it tried just ls.   It returns 

Desktop    Downloads   Music   Public   Templates
Documents   examples.desktop   Pictures   RTL8192EU   Videos

So the file is in the home folder, what am I missing?

---

### Post by chili555 on 2016-01-18
I haven't the faintest idea how or where you got a directory named RTL8192EU instead of the expected rtl8192eu unless you renamed it. Here is what happens when I repeat the sequence as a test:```
git clone https://github.com/jpostma/rtl8192eu.git
[COLOR="#FF0000"]Cloning into 'rtl8192eu'[/COLOR]...
remote: Counting objects: 403, done.
remote: Total 403 (delta 0), reused 0 (delta 0), pack-reused 403
Receiving objects: 100% (403/403), 1.65 MiB | 665.00 KiB/s, done.
Resolving deltas: 100% (141/141), done.
Checking connectivity... done.

```So it creates the folder and puts all the files in it.

Next I change directories:```
cd rtl8192eu
```And list the contents:```
ls
```And I clearly see:```
clean  dkms.conf  ifcfg-wlan0  Kconfig  [COLOR="#FF0000"]Makefile[/COLOR]  platform   runwpa
core   hal        include      LICENSE  os_dep    README.md  wlan0dhcp

```

---

### Post by rich37 on 2016-01-18
> **chili555 said:**
> I haven't the faintest idea how or where you got a directory named RTL8192EU instead of the expected rtl8192eu unless you renamed it. Here is what happens when I repeat the sequence as a test:```
git clone https://github.com/jpostma/rtl8192eu.git
[COLOR=#FF0000]Cloning into 'rtl8192eu'[/COLOR]...
remote: Counting objects: 403, done.
remote: Total 403 (delta 0), reused 0 (delta 0), pack-reused 403
Receiving objects: 100% (403/403), 1.65 MiB | 665.00 KiB/s, done.
Resolving deltas: 100% (141/141), done.
Checking connectivity... done.

```So it creates the folder and puts all the files in it.

Next I change directories:```
cd rtl8192eu
```And list the contents:```
ls
```And I clearly see:```
clean  dkms.conf  ifcfg-wlan0  Kconfig  [COLOR=#FF0000]Makefile[/COLOR]  platform   runwpa
core   hal        include      LICENSE  os_dep    README.md  wlan0dhcp

```

I copied the file from the cd that came with the adapter, didn't realize that all caps would make a difference.   When I enter cd RTL8192EU the directory changed to that file.  To be exact, it reads lisa@lisa-GT5465E:~/RTL8192EU$  When l type ls, it shows rtl8192_linux_v4.2.4   rtl8192_windows   then a string of Chinese characters,doc.   from that point I tried cd rtl8192 and it says bash: cd: rtl8192: No such file or directory   Sorry to take so much of your time.   I really do appreciate the help.....

---

### Post by chili555 on 2016-01-18
You can't mix and match the processes. You can't refuse to use the github file but then use the commands I suggested instead on your CD driver. 

Is there some reason you can't or won't use the method I proposed?

I have tried to help you the best I can but you continue to reject it. I am not sure I can do any more.

---

### Post by rich37 on 2016-01-18
I am in the process of going back to square one.    I didn't mean to reject your advice, when I saw the file you mentioned on the cd, I didn't think it would make a difference.    Apparently it does.
I appreciate your help and will try to follow your directions from the start.

Thanks,

After connecting to wired internet and following all previous instructions, continuing problems....  
 From the directory 
rtl8192eu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.19.0-25-generic/build M=/home/lisa/rtl8192eu modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-25-generic'
   CC [M]  /home/lisa/rtl8192eu/core/rtw_cmd.o
cc1: error: -Werror=date-time: no option -Wdate-time
make[2]: ***[/home/lisa/rel8192eu/core/rtw_cmd.o] Error 1
make[1]: ***[_module_/home/lisa/rtl8192eu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.-25-generic'
make: *** [modules] Error 2
lisa@lisa-GT5465E:~/rtl8192eu$ sudo make install
[sudo] password for lisa:
install -p -m 644 8192eu.ko'  /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/
install: cannot stat '8192eu.ko': No such file or directory
make: *** [install] Error 1
lisa@lisa-GT5465E:~/rtl8192eu$ 

Any suggestions are appreciated.

---

### Post by chili555 on 2016-01-19
First of all, when you get an error at 'make', stop and fix it as all further steps will also be errors.

I suggest you do this:```
cd ~/rtl8192eu
gedit Makefile
```Use nano or kate or leafpad if you don't have the text editor gedit. Find the lines:```
EXTRA_CFLAGS += -Wno-unused-variable
EXTRA_CFLAGS += -Wno-unused-value
EXTRA_CFLAGS += -Wno-unused-label
EXTRA_CFLAGS += -Wno-unused-parameter
EXTRA_CFLAGS += -Wno-unused-function
EXTRA_CFLAGS += -Wno-unused
[COLOR="#FF0000"]EXTRA_CFLAGS += -Wno-error=date-time[/COLOR]
#EXTRA_CFLAGS += -Wno-uninitialized

```Is the line I highlighted the same? If not, change it. 

If it is the same, let's comment it out, like this:```
EXTRA_CFLAGS += -Wno-unused-variable
EXTRA_CFLAGS += -Wno-unused-value
EXTRA_CFLAGS += -Wno-unused-label
EXTRA_CFLAGS += -Wno-unused-parameter
EXTRA_CFLAGS += -Wno-unused-function
EXTRA_CFLAGS += -Wno-unused
[COLOR="#FF0000"]#[/COLOR]EXTRA_CFLAGS += -Wno-error=date-time
#EXTRA_CFLAGS += -Wno-uninitialized

```Obviously, you can't put in the hashmark in red; I simply highlighted it to illustrate the change.

Proofread carefully, save and close the text editor. Now do:```
make clean
make
```If there is no error, proceed.```
sudo make install 
sudo modprobe 8192eu
```

---

### Post by rich37 on 2016-01-19
Thanks for all your help Chilli, here is the first part of the file.

  	 	 	 	   EXTRA_CFLAGS += $(USER_EXTRA_CFLAGS)  
 EXTRA_CFLAGS += -O1  
 [COLOR=#008080]#EXTRA_CFLAGS += -O3 
[/COLOR]
[COLOR=#008080] [/COLOR][COLOR=#008080]#EXTRA_CFLAGS += -Wall  [/COLOR]
[COLOR=#008080] [/COLOR][COLOR=#008080]#EXTRA_CFLAGS += -Wextra  [/COLOR]
[COLOR=#008080] [/COLOR][COLOR=#008080]#EXTRA_CFLAGS += -Werror  [/COLOR]
[COLOR=#008080] [/COLOR][COLOR=#008080]#EXTRA_CFLAGS += -pedantic  [/COLOR]

[COLOR=#008080] [/COLOR][COLOR=#008080]#EXTRA_CFLAGS += -Wshadow -Wpointer-arith -Wcast-qual -Wstrict-prototypes -Wmissing-prototypes  [/COLOR]
 

 EXTRA_CFLAGS += -Wno-unused-variable  
 EXTRA_CFLAGS += -Wno-unused-value  
 EXTRA_CFLAGS += -Wno-unused-label  
 EXTRA_CFLAGS += -Wno-unused-parameter  
 EXTRA_CFLAGS += -Wno-unused-function  
 EXTRA_CFLAGS += -Wno-unused  
 [COLOR=#008080]#EXTRA_CFLAGS += -Wno-error=date-time  
[/COLOR]
[COLOR=#008080] [/COLOR][COLOR=#008080]#EXTRA_CFLAGS += -Wno-uninitialized  [/COLOR]
 

 EXTRA_CFLAGS += -I$(src)/include  
 

 EXTRA_LDFLAGS += --strip-debug  [COLOR=#000000]

The line you highlighted was correct, I just added the #.

When  I enter make clean, it says   - make: Nothing to be done for 'clean'.
Then I enter make, it says,   make: *** No targets.  Stop.
[/COLOR]

---

### Post by chili555 on 2016-01-19
> When I enter make clean, it says - make: Nothing to be done for 'clean'.
Then I enter make, it says, make: *** No targets. Stop.Then you are not in the correct directory. Please try again:```
cd ~/rtl8192eu
ls
```Do you see 'Makefile'? If so:```
make clean
make
sudo make install
sudo modprobe 8192eu
```

---

### Post by rich37 on 2016-01-19
Following as instructed, there seem to be three makefiles, don't really know if that is correct, but this is what returns.

lisa@lisa-GT5465E:~$ cd ~/rtl8192eu
lisa@lisa-GT5465E:~/rtl8192eu$ ls
clean      hal          Kconfig   Makefile   platform   wlan0dhcp
core       ifcfg-wlan0  LICENSE   Makefile~  README.md
dkms.conf  include      makefile  os_dep     runwpa
lisa@lisa-GT5465E:~/rtl8192eu$ make clean
make: Nothing to be done for `clean'.
lisa@lisa-GT5465E:~/rtl8192eu$

---

### Post by chili555 on 2016-01-19
The file Makefile~ is entirely expected; when you modify a file, a sort of backup is automatically created.

The file makefile, with a lower case m, is unexpected. I haven't any idea where it came from. I certainly didn't ask that you write it. Let's rename it in case it interferes.```
cd ~/rtl8192eu
ls
```Before you proceed, make sure you are in the right directory.```
sudo mv makefile xxmakefilexx
```Now try to compile again:```
make clean
make
sudo make install
sudo modprobe 8192eu
```

[ATTACH=CONFIG]266838[/ATTACH]

---

### Post by rich37 on 2016-01-19
Success at last!    Thanks so much for all the help.   The wife will be very happy to have her computer back.

Thanks,

---

### Post by chili555 on 2016-01-19
Not so fast! When Update Manager installs a later kernel version, also known as linux-image, after the requested reboot, recompile:```
cd ~/rtl8192eu
make clean
make
sudo make install
sudo modprobe 8192eu
```Finally, please use thread tools to mark the thread Solved. The searchers will appreciate it.

Glad it's working.

---

### Post by rich37 on 2016-01-19
OK, when does that happen with Update Manager?   Is it a one time deal or do I have to do it after every update?    Either way, I do appreciate your patience....

---

### Post by chili555 on 2016-01-19
> **rich37 said:**
> OK, when does that happen with Update Manager?   Is it a one time deal or do I have to do it after every update?    Either way, I do appreciate your patience....There is no set time. A later kernel version could be installed tomorrow or a week from now or a month. The clues are that you are notified to reboot to complete the update and, after you reboot, the wireless isn't working. That's when you remember Chili told you to recompile.

---

### Post by nrsotnas on 2016-07-27
> **chili555 said:**
> That device is *NOT* supported by the driver rtl8192cu. It is supported by the rare and elusive driver 8192eu.



Chilli555, you sir are AWESOME!
I have been trying to get my card to work for days now, until i found this thread. Followed it step by step (even the errors i got were the same) and voilá i got to work!!!
THANK YOUUUUU :D

---

