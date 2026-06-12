---
title: "Help finding and installing"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by Shpend R on 2007-05-16
Ok, I have found out the driver if I have to download for my laptopn to work. 

It is called ' RealTek RTL8180 802.11B WLAN Adapter drivers'. It is for Packard Bell because my laptop is a packard bell. 

I use Ubuntu 6.06 (will update when  get my wireless drive working). The main problem is that I cannot find a the driver for the Linux OS, only for Windows (.exe files). I have tried google and I did not find anything.

Thanks, *Shpend*

(If you are wondering on how I am posting this, I am on my other laptop which uses Windows)

---

### Post by chili555 on 2007-05-16
The problem is that the r818x module that your card needs is blacklisted in Feisty because it is often buggy. Here is an excerpt from the file */etc/modprobe.d/blacklist*:```
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
```You can do one of two things; first, you can try un-blacklisting the module. *sudo gedit etc/modprobe.d/blacklist* to change to this:```
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
#blacklist r818x
blacklist r8187
```Putting that little hashmark in front tells us to 'ignore what follows.' Reboot. If your card fires up and runs acceptably, you are all set.

The other option is this: [http://ubuntuforums.org/showthread.php?t=440116&highlight=rtl8180](http://ubuntuforums.org/showthread.php?t=440116&highlight=rtl8180) It's a bit complex, but works well.

Obviously, I suggest you try the quick and easy first, but don't be disappointed if it doesn't work perfectly.

---

### Post by Shpend R on 2007-05-16
I tried that, it did not work (the first one). I am not sure about the second one. I have been searching all over google and I cannot find anything. I would really appriciate any help :)

Thanks

---

### Post by chili555 on 2007-05-16
Let's see the output of these two commands:```
sudo modprobe r818x
ifconfig
```Thanks.

---

### Post by Shpend R on 2007-05-17
Currently I am at school, but when I go back home, I will enter that command

*Shpend*

---

### Post by tturrisi on 2007-05-17
I don't understand why the Ubuntu r818x has to be blaclisted to beging with because in Debian it works flawlwssly.  I run Etch and use that driver all the time w/ never any isues.

On Ubuntu, what I would do is uninstall the existing r818x drivers, download the source, build it using module-asistant and install it.  I even patched mine using aircrack-ng patch so the driver supports packet injection.

[http://www.aircrack-ng.org/doku.php?id=install_drivers](http://www.aircrack-ng.org/doku.php?id=install_drivers)
ifconfig wlan0 down
rmmod r8180
wget [http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz)
wget [http://patches.aircrack-ng.org/rtl8180-0.21v2.patch](http://patches.aircrack-ng.org/rtl8180-0.21v2.patch)
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180

---

### Post by Shpend R on 2007-05-17
> **chili555 said:**
> Let's see the output of these two commands:```
sudo modprobe r818x
ifconfig
```Thanks.

Whati i get is below:

Nothing. It breaks line and nothing appears.

But,  when it is the ifconfig part, i though it was 'ip'config. That came up with this message:

'FATAL: Error inserting r181x (/lib/modules/2.6.15-26-386/kernel/drivers/net/wire
less/rtl818x/r818x.ko): Unknown symbol in module, or unknown parameter (see dmes
g)

Any good?

---

### Post by chili555 on 2007-05-17
> I don't understand why the Ubuntu r818x has to be blaclistedI'm just telling you what I read! [https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/88430](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/88430)> Any good?Nope. I think this rules out the quick and easy method. 

I suggest you try tturrisi's method above. You will probably need to install the packages *build-essential* and *linux-headers-`uname -r`* and *module-assistant*.

Post back if you get stuck.

---

### Post by tturrisi on 2007-05-17
the above method I posted will also prompt you to remove the existing drivers.

---

### Post by Shpend R on 2007-05-18
> **tturrisi said:**
> I don't understand why the Ubuntu r818x has to be blaclisted to beging with because in Debian it works flawlwssly.  I run Etch and use that driver all the time w/ never any isues.

On Ubuntu, what I would do is uninstall the existing r818x drivers, download the source, build it using module-asistant and install it.  I even patched mine using aircrack-ng patch so the driver supports packet injection.

[http://www.aircrack-ng.org/doku.php?id=install_drivers](http://www.aircrack-ng.org/doku.php?id=install_drivers)
ifconfig wlan0 down
rmmod r8180
wget [http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz)
wget [http://patches.aircrack-ng.org/rtl8180-0.21v2.patch](http://patches.aircrack-ng.org/rtl8180-0.21v2.patch)
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180

Hold on, I saw the source but what on earth am I suppose to do with it? 

Thanks

---

### Post by Shpend R on 2007-05-19
Do I have to write those commands in the terminal?

---

### Post by tturrisi on 2007-05-19
do this in a terminal:

apt-get install build-essential linux-headers-`uname -r` module-assistant

next, in a terminal do:

ifconfig wlan0 down
rmmod r8180
wget [http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz)
wget [http://patches.aircrack-ng.org/rtl8180-0.21v2.patch](http://patches.aircrack-ng.org/rtl8180-0.21v2.patch)
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180

---

### Post by Shpend R on 2007-05-19
After I done that, will it mean that I will be able to use wireless?

(I will post results of that :))

---

### Post by Shpend R on 2007-05-19
Everytime, everything failed. Nothing happened after.

---

### Post by chili555 on 2007-05-19
> Everytime, everything failed. Nothing happened after.Can you be a bit more specific?

Note that these commands assume you can walk the laptop over to the router or access point and connect an ethernet cable and get internet access. Is this not the case?

---

### Post by Shpend R on 2007-05-19
Sorry, but I do not quite understand you. 

For the commands, I really dont get it on how it suppose to help to get wireless?

---

### Post by chili555 on 2007-05-19
Your initial post was that you couldn't find a Linux driver for your Realtek 8180 card. These commands will get the driver downloaded, installed and running. Was that not your request?

---

### Post by Shpend R on 2007-05-19
EDIT: I have wrote all the commands, and this time it was a success. Nothing happened after, so how do I test it out to see if I was wrong somewhere in the code?

Sorry, I am going to run the commands now in the Terminal now. Hopefully it should workk again.

Shpend

---

### Post by Shpend R on 2007-05-19
I wrote all the commands and nothing happened. After the 'apt-get install build-essential linux-headers-`uname -r` module-assistant' the lines started with '>'. I typed all the commands and no things came up, nothing new appeared in the system tray.

I restarted the computer and nothing came up.

What do I do?

Shpend

---

### Post by chili555 on 2007-05-19
> the lines started with '>'I don't understand how this can happen!

Please let me see:```
lsmod | grep 818
```If the module did not load, we'll retrace our steps.

---

### Post by Shpend R on 2007-05-20
When I type this in 'apt-get install build-essential linux-headers-`uname -r` module-assistant', it comes up with the following message:

```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

[IMG]http://img521.imageshack.us/img521/2392/screenshot1yp9.png[/IMG]

That is what came up. Does that help narrow the soloution?

---

### Post by Rui Pais on 2007-05-20
you are doing several mistakes. 

you are trying to run commands that need administrative powers as a normal user. You need to add sudo to the beginning of those commands.
Example:
```
sudo apt-get install build-essential linux-headers-`uname -r` module-assistant
```

You are trying to apt-get stuff from the net, but you don't have a network working. OF course it will faill.

You are typing instruction you don't understand on the terminal. Thats wrong. You **must** copy+past them from here to terminal or mistake will arise. 
As an example you miss the symbol ` with something like ' other. That take you the the line ended with '>'

You have a running dpkg or apt-process. Until it finnish you will not be able to apt-get (or dpkg) anything.

---

### Post by Shpend R on 2007-05-20
Thank you very much!!!

I am going to try it now and i am going to see if it works!! (im sure it will!!!)

---

### Post by Shpend R on 2007-05-20
No success, here are a few screenshots:

[IMG]http://img512.imageshack.us/img512/9290/termial1kt6.png[/IMG]


[IMG]http://img87.imageshack.us/img87/9128/37436262dw1.png[/IMG]

I do not know what to say?

---

### Post by Rui Pais on 2007-05-20
ok, it's impossible to give an advice that is an absolute truth (in that case what failed was the copy+paste :() ...forum shortened the long net address (cause it was written as text instead of code tags)
we will correct this...

First an extra advice. Those command depend sequentially on each other if one fails the other couldn't complete correctly. It's useless and sometimes dangerous to run it in a row when an error occurs, ok?

you need to do first:
```
wget -c http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz
```

and then, if it downloads ok, skip to the step:
```
tar -xvzf rtl8180-0.21.tar.gz
```

post any doubts or errors outputs.


Anyway i suggest you first try the method give by chili555 on [4th post.]("http://ubuntuforums.org/showpost.php?p=2668263&postcount=4") Till you have sure it fails it was the easiest way.

---

### Post by tturrisi on 2007-05-20
and instead of using sudo, open a root terminal to do this.  Go to Accessories > Terminal (as root) or Root Terminal, whatever it's called now in that accessories menu.

just so you know what is happening:

apt-get install build-essential linux-headers-`uname -r` - downloads & installs the files required to build packages from the source code.
ifconfig wlan0 down - shuts off current realtek adapter IF it is on & working.
rmmod r8180 - unloads the realtek driver IF it is loaded.
wget [http://ovh.dl.sourceforge.net/source...80-0.21.tar.gz](http://ovh.dl.sourceforge.net/source...80-0.21.tar.gz) - downloads the current realtek driver source code
wget [http://patches.aircrack-ng.org/rtl8180-0.21v2.patch](http://patches.aircrack-ng.org/rtl8180-0.21v2.patch) - downloads a patch for the driver
tar -xvzf rtl8180-0.21.tar.gz - unpacks the compressed tar archive of files
cd rtl8180-0.21 - changes to the directory with the unpacked files
patch -Np1 -i ../rtl8180-0.21v2.patch - adds the patch to the files used to build the driver
make && make install - builds & installs the driver
depmod -a - creates the needed file so the driver can load at boot, along w/ any other needed dependencies to make it work with your kernel.
modprobe r8180 - loads the needed driver (instead of having to reboot)

---

### Post by luigibanzato on 2008-05-31
Hello,

Im having some problems with my wireless card as well. I tried the above, here are my results:
- installing linux headers: went fine.
- ifconfig wlan0 down: wlan0: ERROR while getting interface flags: No such device
- I didn't have the r8180 module loaded: ERROR: Module r8180 does not exist in /proc/modules
- Downloading the tar.gz archive, uncompressing and patching went fine.

BUT, when I try to "make":

```
luigi@luigi-desktop:~/rtl8180-0.21$ make
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/luigi/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/luigi/rtl8180-0.21/ieee80211_rx.o
In file included from /home/luigi/rtl8180-0.21/ieee80211_rx.c:43:
/home/luigi/rtl8180-0.21/ieee80211.h:43:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/skbuff.h:17,
                 from include/linux/if_ether.h:113,
                 from include/linux/netdevice.h:29,
                 from include/linux/if_arp.h:26,
                 from /home/luigi/rtl8180-0.21/ieee80211_rx.c:25:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/luigi/rtl8180-0.21/ieee80211_rx.c: In function ‘ieee80211_monitor_rx’:
/home/luigi/rtl8180-0.21/ieee80211_rx.c:296: error: ‘struct sk_buff’ has no member named ‘mac’
/home/luigi/rtl8180-0.21/ieee80211_rx.c: In function ‘ieee80211_r8180_rx’:
/home/luigi/rtl8180-0.21/ieee80211_rx.c:1131: error: ‘struct sk_buff’ has no member named ‘mac’
/home/luigi/rtl8180-0.21/ieee80211_rx.c:1131: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/luigi/rtl8180-0.21/ieee80211_rx.o] Error 1
make[1]: *** [_module_/home/luigi/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [2.6] Error 2

```

I know the card is there. Here are lspci result about it:
```
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

Using lshw -C network I get:
```
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32

```

I wonder why lshw shows the network adapter, but it have no logical name associated... I tryed removing the driver that was loaded automaticaly (r8169) and using ndiswrapper to load windows XP driver. Here are the result:
```
luigi@luigi-desktop:~/rtl8180-0.21$ ndiswrapper -l
net8185 : driver installed
	device (10EC:8185) present

```

It seems fine, but the device haven't a logical name. Anyone got some idea of what should I do?

Thanks in advance.

---

### Post by luigibanzato on 2008-05-31
Tried out this one, works fine for me: [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

---

