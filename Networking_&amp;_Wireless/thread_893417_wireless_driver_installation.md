---
title: "wireless driver installation"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by heeman453 on 2008-08-18
Hi every one..this is my first time with ubuntu and never knew this existed,.So i need help..I managed to view device manager after running some google search etc..I can see it has a wireless card but no driver installed.So I need some help to install and get the wireless card running.
Vendor is Intel corporation and device is PRO/Wireless 2200BG network connection...How do I get this running?? Thanks for all in advance.

---

### Post by itix on 2008-08-19
I'm going to ask you to enter some code in what we call the terminal. Provided that there is a fix, plese continue to enter my instructed codes there. It can be found under *Applications -> Acessories -> Terminal*.

The first one would be *lshw -C network*
Please note the capital C. It lists your network devices and specific information about them that I will need to find a fix and help you through the process (given that there is a fix, which in most cases there is).

Since you say that the vendor is intel, I'd give you a good chance of finding drivers for your network device since intel have a very kind mode towards open operating systems (they have officially supported ubuntu before, but are now supporting fedora).

---

### Post by heeman453 on 2008-08-23
prishma@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wlan0
       version: 05
       serial: 00:16:6f:cc:e0:51
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,12/19/2007,9.0.4.39 latency=64 maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth4
       version: 10
       serial: 00:e0:4e:77:07:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
prishma@ubuntu:~$ 


// Thanks for helping me..I am new to this but trying to learn so far..Can you tell me how to get my ethernet and wireless working.Hope to hear from you.

---

### Post by itix on 2008-08-24
Your wired ethernet is broken too?
Well, lets take things one step at a time...

You can find a driver for your wireless here: [http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.2.2.tgz?download](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.2.2.tgz?download)

It's a source package which will require some "non-conventional" ways of installing for someone not used to linux. 
First of all, extract the archive to wherever (it's easiest if you extract it in your home folder... don't worry, you can delete that folder afterwards). Go to the terminal again. If you have extracted the archive in any other folder than home, you'll need to navigate to that folder. This is done with *[COLOR="Green"]cd foldername[/COLOR]*(you can find *foldername* with *[COLOR="Green"]ls[/COLOR]*) or *[COLOR="Green"]cd ..[/COLOR]* (cd period-period) which navigates to directory above.

Navigate into the folder you extracted with *[COLOR="Green"]cd ipw2200-1.2.2[/COLOR]*. Type *[COLOR="Green"]sudo make install[/COLOR]* and it should install correctly. If that doesn't work, type *./configure* first and then sudo make install.

The site where I found the drivers also said something about some firmware that was needed. It can be found here: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php) (you'll want 3.0).

The [Documentation]("http://ipw2200.sourceforge.net/INSTALL") says that the folder should be extracted to /usr/lib/hotplug/firmware/ or /lib/hotplug/firmware/, however I don't have any of them on my xubuntu distribution.

If you don't have any of them, create the /usr/lib...blah blah one with *[COLOR="Green"]sudo nautilus[/COLOR]* and create hotplug under /usr/lib/ and then create a firmware in the hotplug folder as usual. Now try to extract the firmware to that folder in the nautilus window you opened with sudo nautilus.

Now there is only loading the network module left. That is done with *[COLOR="Green"]sudo modprobe ipw2200[/COLOR]* in the terminal.

Excuse the two mile long post. Hope it solves your wireless...

If this succeeds, let's do the wired one :p

---

### Post by heeman453 on 2008-08-24
prishma@ubuntu:~$ cd Desktop
prishma@ubuntu:~/Desktop$ sudo make install ipw2200-1.2.2
[sudo] password for prishma: 
make: *** No rule to make target `install'. Stop.


// This is the message I am getting..Can't proceed further.Any idea why? Thanks a lot for your help.

---

### Post by heeman453 on 2008-08-25
prishma@ubuntu:~$ cd Desktop
prishma@ubuntu:~/Desktop$ ls
bluez-4.1        Geek Squad.desktop  ipw2200-1.2.2.tgz  wader-gtk.desktop
firefox.desktop  ipw2200-1.2.2       ipw2200-fw-3.0
prishma@ubuntu:~/Desktop$ cd ipw2200-1.2.2
prishma@ubuntu:~/Desktop/ipw2200-1.2.2$ sudo make install
mkdir -p /home/prishma/Desktop/ipw2200-1.2.2/tmp/.tmp_versions
make -C /lib/modules/2.6.24-19-generic/build M=/home/prishma/Desktop/ipw2200-1.2.2 MODVERDIR=/home/prishma/Desktop/ipw2200-1.2.2/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/prishma/Desktop/ipw2200-1.2.2/ipw2200.o
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_send_adapter_address’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:2374: error: implicit declaration of function ‘MAC_ARG’
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:2374: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_add_station’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:3951: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_send_disassociate’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:3990: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_rx_notification’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:4515: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:4597: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 7 has type ‘const char *’
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:4597: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:4622: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:4651: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:4691: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:4709: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_best_network’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5769: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5779: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5792: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5810: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘const char *’
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5810: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5826: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘const char *’
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5826: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5839: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5852: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5863: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5874: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘char * const’
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5874: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 7 has type ‘char * const’
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5874: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5887: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5896: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5906: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5916: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5925: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:5940: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_debug_config’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:6202: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_associate_network’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:7588: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_rx’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:8543: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_wx_set_wap’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:9117: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_wx_get_wap’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:9146: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_tx_skb’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:10370: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_net_set_mac_address’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:10698: warning: too few arguments for format
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_pci_probe’:
/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.c:11937: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/prishma/Desktop/ipw2200-1.2.2/ipw2200.o] Error 1
make[1]: *** [_module_/home/prishma/Desktop/ipw2200-1.2.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
prishma@ubuntu:~/Desktop/ipw2200-1.2.2$ 


// These are the messages I am getting when trying to install...

prishma@ubuntu:~$ sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6294): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by itix on 2008-08-29
wow!
That was many errors.

Sorry for the delay. I've moved and I don't have any internet connection at my new appartment. I am now at the library and stealing their wireless =D

I have no idea what might cause all those. What does it say if you do just *[COLOR="Green"]sudo make[/COLOR]*??

---

### Post by heeman453 on 2008-08-30
Hi again..I have changed my laptop to a new one thinking that there is something faulty...but it seems I am getting the same problem..I typed sudo make and this is what I got:

prishma@ubuntu:~$ sudo make
[sudo] password for prishma: 
make: *** No targets specified and no makefile found. Stop.
prishma@ubuntu:~$

---

### Post by itix on 2008-08-30
That's not the same problem at all. That means that it (the GNU c compiler) can't find the make-file which is essential to building drivers and stuff. It contains evironment variables and similar. Are you sure that you are in the correct folder at the terminal? (you know, [COLOR="Green"]*cd* path[/COLOR], where *path* was /home/prishma/Desktop/ipw2200-1.2.2 on your prevoius laptop)

EDIT: ...or shall I put it more bluntly; you ARE in the wrong folder unless you've moved the files from ipw2200-1.2.2 to your home folder :p

---

### Post by heeman453 on 2008-09-08
I got it up and running now..If you press Fn+ F1 then it starts the wireless network...and to run youtube on it I had to enable flash non free in the synaptic package..Thanks a lot for your help..Everything is ok now..

---

### Post by itix on 2008-09-10
Great!
Don't forget tp mark the thread as solved.

It is true that you require flash-nonfree. The free version don't run too well unfortunately. I have the non-free as well.

---

