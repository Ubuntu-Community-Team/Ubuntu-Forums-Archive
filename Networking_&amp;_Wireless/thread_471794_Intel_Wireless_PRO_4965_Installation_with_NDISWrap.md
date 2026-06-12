---
title: "Intel Wireless PRO 4965 Installation with NDISWrapper"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by kitpierce on 2007-06-12
I was having some problems installing the Intel PRO/Wireless 4965 card in my Dell Inspiron 6400/1505 with Kubuntu 7.04 Feisty Fawn.  After much searching and tons of help from the forums, I pieced together a solution using NDISWrapper that finally got me up and running.  I decided to write a short how-to that might help.

First, make sure you're actually using a 4965 card.  Many of my problems to start with were due to trying to install the wrong card.  From a teminal type:
> **sudo update-pciids**
then:
> **lspci**

Toward the end of the list will be an indication of your Wireless Card.  Mine reads:
*0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)*

Install Ndiswrapper by whatever method you prefer.  I personally used [Automatix2]("http://www.getautomatix.com/wiki/index.php?title=Installation").

Download the WindowsXP drivers directly from Intel by [clicking here]("http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=All&OSFullName=All+Operating+Systems&lang=eng").  Filename will be V11.1.1.0_XP_DRIVERS.ZIP.

Extract the files wherever you'd like.

Open terminal and navigate to where you extracted the files.  Run the following command to install the 4965 driver:
> **sudo ndiswrapper -i netw4x32.inf**

load the module using this command
> **sudo ndiswrapper -m**

check the installation using this command
> **ndiswrapper -l**

my readout says:
> *netw4x32 : driver installed*

I also had to add the ndiswrapper module by hand using this:
> **sudo cp /etc/modules /etc/modules.ndiswrapperbackup**    (creates backup file)
> **sudo kwrite /etc/modules**    (opens modules file using kwrite - use gedit if you're using Ubuntu instead of Kubuntu)
then add the following line:
> **ndiswrapper**
then save and close.

Next you'll want to reboot.  Note - my computer stalled the first time I tried to reboot but turning it off and then back on worked like a charm.  Don't know why...
[B][I]
Kubuntu specific[/I][/B]: Once the computer starts, click on the KNetworkManager icon, click Options, then Enable Wireless.  That worked for me, hope it helps somebody else too!

Note: I haven't used this to try to connect to any secured networks; evidently people are having some problems with that - please search the forums for whatever encryption you're using for additional help.  This is my first how-to and I wrote it from memory, so if there's anything wrong please let me know and I will correct it.

---

### Post by fflarex on 2007-06-13
Well, I had networking configured perfectly on my system just 2 days ago, with no glitches or anything whatsoever. Then a huge screw up of mine forced me to reinstall everything, and I went through the exact same procedure that I did the first time through, in order to install ndiswrapper and 1.46, except now I had trouble booting with wireless on (a problem I never had before, though other people certainly did). As far as I can tell, I did *absolutely nothing* different, yet now I had troubles with it. Frustrating, but I guess I don't really know what my point is.

I do have a question on this though. This seems like a longer procedure than what I did either time; what is the effect of editing the modules file and where are you inserting ndiswrapper?

---

### Post by Mrkluky on 2007-06-13
Hy KitPierce 
I have a laptop with intel pro wireless 2200 bg
I succesfully installed ndiswrapper,infact

$ ndiswrapper -l
Installed ndis drivers:
w29n51          driver present, hardware present
 
...and also ...

$ lsmod | grep ndis
ndiswrapper           177364  0
usbcore               130820  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

But I have the doubt that I'm still using the old driver:

$ lsmod | grep ipw
ipw2200               107308  0
ieee80211              37064  1 ipw2200

If i make "rmmod ipw2200" can I restore it later if ndiswrapper doesn't make the trick ?
I want to try ndiswrapper because my internet connection drop (maybe when my isp change my external ip) to restore it I have to do: 
  $ sudo poff       
  $ sudo ifdown eth1
  $ sudo ifup eth1
  $ sudo pon dsl-provider
Even each time I reboot my machine I must type the above commands to connect wireless
...Sorry for this huge reply ! I hope that if you help me you'll help lot's of people ! Bye

---

### Post by kitpierce on 2007-06-14
To fflarex:
The writeup is a bit longer than absolutely necessary, but it's what I did that worked.  If you know what hardware you're using you can eliminate the *sudo update-pciids* step because that just helped me figure out exactly what model my wireless card was.  Also, I am not sure what you mean by "inserting ndiswrapper" but I think that may be what I accomplished by editing */etc/modules*.  That file is a list of all the modules that start at boot time - I couldn't figure out how to get ndiswrapper to load other than that, so if you have any suggestions I'd be more than willing to add them.

To Mrkluky:
Sadly I have no idea - you're way over my head from a technical standpoint on those questions.  Anyone else want to pitch in an idea or two to help out?

---

### Post by S15_88 on 2007-06-14
I have that same card, and i was planning on using ndiswrapper as the card is not supported by ubuntu but a quick question for you, on the ndiswrapper website it says that the 4965 is not supported by ndiswrapper either?  although now since two ppl here have said that they used ndiswrapper with a 4965 it must work.

---

### Post by fflarex on 2007-06-14
> **kitpierce said:**
> To fflarex:
The writeup is a bit longer than absolutely necessary, but it's what I did that worked.  If you know what hardware you're using you can eliminate the *sudo update-pciids* step because that just helped me figure out exactly what model my wireless card was.  Also, I am not sure what you mean by "inserting ndiswrapper" but I think that may be what I accomplished by editing */etc/modules*.  That file is a list of all the modules that start at boot time - I couldn't figure out how to get ndiswrapper to load other than that, so if you have any suggestions I'd be more than willing to add them.

No, actually that's exactly what I was asking. Before I did this step, my system wouldn't boot. I believe the first time I successfully installed ndiswrapper with the driver, I accomplished this with the command' modprobe, so it didn't look like a familiar step to me. I must have forgotten that command the second time.

[QUOTE=S15_88]I have that same card, and i was planning on using ndiswrapper as the card is not supported by ubuntu but a quick question for you, on the ndiswrapper website it says that the 4965 is not supported by ndiswrapper either? although now since two ppl here have said that they used ndiswrapper with a 4965 it must work.[/QUOTE]

If you check the version history, it says that issues with the 4965AGN were addressed in version 1.45 IIRC. The current version is 1.47.

---

### Post by S15_88 on 2007-06-15
Trouble! so i go to install the driver and it says it's already installed, ok i'll take that haha
then i get some crazy stuff, instead of saying driver installed i get invalid driver! this is my output of the steps i've done:

alain@S15:~$ sudo ndiswrapper -i netw4v32.inf
Password:
driver netw4v32 is already installed
alain@S15:~$ sudo ndiswrapper -m
module configuration already contains alias directive

alain@S15:~$ ndiswrapper -l
netw2 : invalid driver!
netw4v32 : invalid driver!
netw4v64 : invalid driver!
netw4x32.sys : invalid driver!
alain@S15:~$ 

Any suggestions on further steps?????


Thanks, Alain

---

### Post by fflarex on 2007-06-16
Remove the invalid drivers with:
sudo ndiswrapper -e XXXX
Where XXXX is the name of the driver. Try installing it again with the instructions from [here]("http://ubuntuforums.org/showpost.php?p=2514602&postcount=8").

If that doesn't work, make sure you have the latest version of ndiswrapper (not from the repository). If you need help installing it from source there are instructions in this [thread]("http://ubuntuforums.org/showthread.php?t=464720&highlight=4965agn").

---

### Post by S15_88 on 2007-06-16
OK so this is what happened i unistalled that driver i uninstalled ndiswrapper and decided i'd start fresh.  I did it all again and it still says: invalid driver!   So this is what I did, bear with me it's a bunch of terminal stuff thought i'd post it so everyone could follow along with what and how i installed things.  Did i do something wrong?  why does it keep saying they are invalid drivers?!?!

> 

alain@S15:~$ cd /home/alain/Desktop
alain@S15:~/Desktop$ tar zxvf ndiswrapper-1.47.tar.gz
ndiswrapper-1.47/
ndiswrapper-1.47/AUTHORS
ndiswrapper-1.47/ChangeLog
ndiswrapper-1.47/INSTALL
ndiswrapper-1.47/Makefile
ndiswrapper-1.47/README
ndiswrapper-1.47/ndiswrapper.spec
ndiswrapper-1.47/ndiswrapper.8
ndiswrapper-1.47/loadndisdriver.8
ndiswrapper-1.47/utils/
ndiswrapper-1.47/utils/Makefile
ndiswrapper-1.47/utils/ndiswrapper
ndiswrapper-1.47/utils/loadndisdriver.c
ndiswrapper-1.47/utils/ndiswrapper-buginfo
ndiswrapper-1.47/driver/
ndiswrapper-1.47/driver/divdi3.c
ndiswrapper-1.47/driver/hal.c
ndiswrapper-1.47/driver/iw_ndis.c
ndiswrapper-1.47/driver/iw_ndis.h
ndiswrapper-1.47/driver/loader.c
ndiswrapper-1.47/driver/loader.h
ndiswrapper-1.47/driver/longlong.h
ndiswrapper-1.47/driver/Makefile
ndiswrapper-1.47/driver/crt.c
ndiswrapper-1.47/driver/ndis.c
ndiswrapper-1.47/driver/ndis.h
ndiswrapper-1.47/driver/ndiswrapper.h
ndiswrapper-1.47/driver/ntoskernel.c
ndiswrapper-1.47/driver/ntoskernel.h
ndiswrapper-1.47/driver/ntoskernel_io.c
ndiswrapper-1.47/driver/pe_linker.c
ndiswrapper-1.47/driver/pe_linker.h
ndiswrapper-1.47/driver/pnp.c
ndiswrapper-1.47/driver/pnp.h
ndiswrapper-1.47/driver/proc.c
ndiswrapper-1.47/driver/rtl.c
ndiswrapper-1.47/driver/usb.c
ndiswrapper-1.47/driver/usb.h
ndiswrapper-1.47/driver/winnt_types.h
ndiswrapper-1.47/driver/workqueue.c
ndiswrapper-1.47/driver/wrapmem.h
ndiswrapper-1.47/driver/wrapmem.c
ndiswrapper-1.47/driver/wrapper.c
ndiswrapper-1.47/driver/wrapndis.h
ndiswrapper-1.47/driver/wrapndis.c
ndiswrapper-1.47/driver/lin2win.h
ndiswrapper-1.47/driver/win2lin_stubs.S
alain@S15:~/Desktop/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/alain/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/alain/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /home/alain/Desktop/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/alain/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/alain/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/alain/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/alain/Desktop/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/alain/Desktop/ndiswrapper-1.47/utils'
alain@S15:~/Desktop/ndiswrapper-1.47$ make install
make -C driver install
make[1]: Entering directory `/home/alain/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/alain/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
mkdir: cannot create directory `/lib/modules/2.6.20-16-generic/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/alain/Desktop/ndiswrapper-1.47/driver'
make: *** [install] Error 2
alain@S15:~/Desktop/ndiswrapper-1.47$ sudo make install
make -C driver install
make[1]: Entering directory `/home/alain/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/alain/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/alain/Desktop/ndiswrapper-1.47/driver'
make -C utils install
make[1]: Entering directory `/home/alain/Desktop/ndiswrapper-1.47/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/alain/Desktop/ndiswrapper-1.47/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8

alain@S15:~/Desktop/ndiswrapper-1.47$ sudo ndiswrapper -i NETw4v32.INF
driver netw4v32 is already installed
alain@S15:~/Desktop/ndiswrapper-1.47$ sudo ndiswrapper -m
module configuration already contains alias directive

alain@S15:~/Desktop/ndiswrapper-1.47$ sudo ndiswrapper -l
netw2 : invalid driver!
netw4v32 : invalid driver!
netw4v64 : invalid driver!
netw4x32.sys : invalid driver!
alain@S15:~/Desktop/ndiswrapper-1.47$ 




Any help would be greatly appreciated!  

Thanks, Alain

---

### Post by S15_88 on 2007-06-16
any suggestions?? maybe?? no?? haha i'm stumped!

---

### Post by fflarex on 2007-06-16
Well, you have 4 drivers installed and none of them work, obviously. Remove them all and try again, simply uninstalling ndiswrapper doesn't get rid of the drivers. I'm going to just walk you through the process to make sure you didn't miss anything. So after you've uninstalled the invalid drivers with the command I gave above, make sure you download the XP drivers from [here]("http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=45&OSFullName=Windows*%20XP%20Home%20Edition&lang=eng"). Extract it, and change directory to the extracted folder with:

cd /home/alain/*whereveryouputit*/V11.1.1.0_XP_DRIVERS.ZIP_FILES

Then run:

ndiswrapper -i NETw4x32.INF
ndiswrapper -m
ndiswrapper -l

The last one will check to make sure it's working correctly. Now:

sudo gedit /etc/modules

This will open a text file. Insert a line somewhere that says nothing but:

ndiswrapper

Save and close. Restart, and if wireless isn't working after that then I have no idea what's going wrong.

---

### Post by S15_88 on 2007-06-17
Didn't work again but now new output that i never got before?!?!?! this is what i did this time around.

again, i uninstalled all previous drivers and deleted all files associated with them.  
Then i changed directories to the folder all the new/proper drivers were in:

> alain@S15:~$ cd /home/alain/V11.1.1.0_VT_DRIVERS.ZIP_FILES

 Now i tried to install the driver but i got this new ERROR:

> alain@S15:~/V11.1.1.0_VT_DRIVERS.ZIP_FILES$ sudo ndiswrapper -i netw4v32.INF
installing netw4v32 ...
couldn't open netw4v32.INF: No such file or directory at /usr/sbin/ndiswrapper line 217.

Ignored the error and continued with:

> alain@S15:~/V11.1.1.0_VT_DRIVERS.ZIP_FILES$ sudo ndiswrapper -m
module configuration already contains alias directive
[email]alain@S15:~/V11.1.1.0_VT_DRIVERS.ZIP[/email]_FILES$ sudo ndiswrapper -l
netw4v32 : invalid driver!


Alrighty Not too sure if this new error is significant to the fact that it just doesn't want to work!  other things i'd like to point out to anyone reading this, my full computer specs are as follows:

[QUOTE]
C:\Users\Alain>systeminfo

OS Name:                   Microsoft® Windows VistaT Home Premium
OS Version:                6.0.6000 N/A Build 6000
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Workstation
OS Build Type:             Multiprocessor Free
System Manufacturer:       Dell Inc.
System Model:              MXC061
System Type:               X86-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: x64 Family 6 Model 15 Stepping 6 GenuineIntel ~2000 Mhz
Total Physical Memory:     2,038 MB
Available Physical Memory: 1,250 MB
Network Card(s):           3 NIC(s) Installed.
                           [01]: Broadcom 440x 10/100 Integrated Controller
                                 Connection Name: Local Area Connection
                                 Status:          Media disconnected
                           [02]: Intel(R) Wireless WiFi Link 4965AGN
                                 Connection Name: Wireless Network Connection
                           [03]: Bluetooth Device (Personal Area Network)
                                 Connection Name: Bluetooth Network Connection
                                 Status:          Media disconnected


If anyone could shed some light on possibly why i am having these troubles when i'm doing exactly what everyone else is doing and there's is working! that would be great!!  Thanks for all the help so far!  i'm very interested in knowing wat everyone thinks about this so others can learn from my miserable fight with wireless haha

---

### Post by fflarex on 2007-06-18
I'm no expert, and I have no idea why it isn't working for you. All I can really do is tell you that when I did it, it worked, then check to see if you did the same thing. If you get other errors, like the one above, someone else will need to step in and troubleshoot for you.

I noticed the system info you gave is from Vista, so maybe it is a dual boot problem? I really have no idea, sorry.

---

### Post by S15_88 on 2007-06-18
hey jus thought u might wanna know i`ve got it running.  these pieces of machinery they like to call computers do some messed up stuff every so often, i jus uninstalled the drivers and tried for probably the 5th time to reinstall them and i worked!  so now it says the driver is installed but it still fails to recognize the hardware? no wifi light and when i go to network there's online wired and modem no wireless?  did u have to do any tinkering to get the harware recognized after u installed the driver?

thanks, Alain

---

### Post by S15_88 on 2007-06-20
here is the output of my commands to try and get it working....any thoughts? 
> 
alain@S15:~$ ndiswrapper -l
netw4v32 : driver installed
        device (8086:4229) present
alain@S15:~$ modprobe ndiswrapper
alain@S15:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:7A:3C:13  
          inet6 addr: fe80::215:c5ff:fe7a:3c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2091469 (1.9 MiB)  TX bytes:629690 (614.9 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:65.94.130.221  P-t-P:64.230.197.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2019843 (1.9 MiB)  TX bytes:571094 (557.7 KiB)

alain@S15:~$ 


---

### Post by klyver on 2007-07-05
hey S15_88, did you get the wireless network working?
I'm having the same problem. Finally gone through the ndiswrapper thing, but for some reason it still can't find the wireless. Any idea??

---

### Post by fredj on 2007-07-05
What version of ndiswrapper are you using. The version in the Feisty repositories does not work. It is the
wrong version. Open a terminal and type ndiswrapper -v and post the result here. If there is any suggestion 
of an error in the message you get then you probably have the faulty version. 

The only way to get a good version is to download the latest source files from the ndiswrapper site and
compile them. I know because I have been through all this. The wrong version was put in the Feisty 
repositories and now it can't be corrected. The whole thing is very frustrating and needs to be given wider
publicity so people don't waste their time with a program that just doesn't work.

---

### Post by kevdog on 2007-07-06
Hey Ive read your posts, and I think you guys really never completed the installation properly.

First lets just check a few things (please post):
ndiswrapper -v
ndiswrapper -l

This will verify no problems with ndiswrapper

Next
sudo modprobe -l | grep ndiswrapper

This will check to see if the module has been inserted in the kernel

Next
lshw -C network

This will see if the ndiswrapper driver is associated with your card

Next
dmesg | grep ndiswrapper

Just see if any error comes up if ndiswrapper is listed.  If no error, then no problem.

Next
installation of ndiswrapper automatically makes a wireless associated with wlan0
So please list the following to see if your wlan0 interface is setup
/etc/network/interface
/etc/iftab

Thanks, I know I asked for a lot, however these points were never clarified.

---

### Post by makaroni on 2007-07-09
I have complete the installation of 4965agn and can see wireless networks and you can connect to the card from other computers. But in the ubuntu installation you cannot see that you are connected or connect to a ad hoc network either.

Don't have access to a router for the moment but can someone say if this are a problem with using ad hoc networks or just a problem that everyone have.

---

### Post by klyver on 2007-07-15
okey, here it is.

klyver@klyver:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 
klyver@klyver:~$ ndiswrapper -l
netw4x64 : driver installed
        device (8086:4229) present
klyver@klyver:~$ sudo modprobe -l | grep ndiswrapper
/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
klyver@klyver:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:db:8e:fa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.72 ip=192.168.15.100 latency=0 multicast=yes
       resources: iomemory:f0000000-f000ffff irq:17
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:f8200000-f8201fff irq:17
klyver@klyver:~$ dmesg | grep ndiswrapper
[   42.140109] ndiswrapper version 1.47 loaded (smp=yes)
[   42.364151] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   42.372505] ndiswrapper: driver netw4x64 (Intel,04/30/2007,11.1.1.11) loaded
[   42.373020] ndiswrapper (NdisWriteErrorLogEntry:192): log: 40001B7C, count: 2, return_address: ffffffff8831b80e
[   42.373024] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x56524457
[   42.373027] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xdd
[   42.373050] Modules linked in: ndiswrapper sbp2 parport_pc lp parport snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device sdhci mmc_core af_packet psmouse snd soundcore snd_page_alloc serio_raw shpchp pci_hotplug intel_agp tsdev evdev ext3 jbd mbcache sg sd_mod usbhid hid generic ahci ata_generic libata scsi_mod tg3 ohci1394 ieee1394 uhci_hcd ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap
[   42.373247]  [<ffffffff8831b70b>] :ndiswrapper:win2lin3+0x11/0x14
[   42.373271]  [<ffffffff88311575>] :ndiswrapper:IofCompleteRequest+0xa5/0x160
[   42.373295]  [<ffffffff88311518>] :ndiswrapper:IofCompleteRequest+0x48/0x160
[   42.373321]  [<ffffffff88313093>] :ndiswrapper:pdoDispatchPnp+0x433/0x450
[   42.373346]  [<ffffffff8831b6f7>] :ndiswrapper:win2lin2+0xe/0x11
[   42.373370]  [<ffffffff88310cdb>] :ndiswrapper:IofCallDriver+0x8b/0xc0
[   42.373396]  [<ffffffff8831700a>] :ndiswrapper:mp_init+0xaa/0x1b0
[   42.373423]  [<ffffffff883171bb>] :ndiswrapper:NdisDispatchPnp+0xab/0xe30
[   42.373458]  [<ffffffff8831174b>] :ndiswrapper:IoInitializeIrp+0x3b/0x70
[   42.373484]  [<ffffffff8831b6f7>] :ndiswrapper:win2lin2+0xe/0x11
[   42.373508]  [<ffffffff88310cdb>] :ndiswrapper:IofCallDriver+0x8b/0xc0
[   42.373531]  [<ffffffff88310cb0>] :ndiswrapper:IofCallDriver+0x60/0xc0
[   42.373555]  [<ffffffff88311c2f>] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
[   42.373579]  [<ffffffff8831319c>] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
[   42.373606]  [<ffffffff8831348f>] :ndiswrapper:pnp_start_device+0x4f/0xb0
[   42.373634]  [<ffffffff883136fb>] :ndiswrapper:wrap_pnp_start_device+0x20b/0x250
[   42.373662]  [<ffffffff88313790>] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
[   42.373728]  [<ffffffff8830776c>] :ndiswrapper:loader_init+0x15c/0x250
[   42.373744]  [<ffffffff8807107e>] :ndiswrapper:wrapper_init+0x7e/0xb6



/etc/network/interfaces contains:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp



/etc/iftab contains:
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d4:db:8e:fa arp 1


any suggestions??

---

### Post by dracomordag on 2007-07-28
alright, i tried to install this with the feisty version of ndiswrapper, then i read that that didnt work, so i uninstalled that and installed the new one, and now i get this: ```
 sudo ndiswrapper -r netw4x32.inf
couldn't delete /etc/ndiswrapper/netw4x32.inf: No such file or directory
david@bluenote:~/Desktop/wifi_card_driver$ sudo ndiswrapper -i netw4x32.inf
driver netw4x32 is already installed
david@bluenote:~/Desktop/wifi_card_driver$ sudo ndiswrapper -m
module configuration already contains alias directive

david@bluenote:~/Desktop/wifi_card_driver$ ndiswrapper -l
netw4x32 : invalid driver!

```

what the hell can i do?

---

### Post by nelo on 2007-07-30
Remove the driver:
```
sudo ndiswrapper -l
netw4x32 : invalid driver!
sudo ndiswrapper -r netw4x32

```
**[COLOR="Red"]netw4x32[/COLOR]** is the driver in UBUNTU and NETw4x32.INF in windows

> **dracomordag said:**
> alright, i tried to install this with the feisty version of ndiswrapper, then i read that that didnt work, so i uninstalled that and installed the new one, and now i get this: ```
 sudo ndiswrapper -r netw4x32.inf
couldn't delete /etc/ndiswrapper/netw4x32.inf: No such file or directory
david@bluenote:~/Desktop/wifi_card_driver$ sudo ndiswrapper -i netw4x32.inf
driver netw4x32 is already installed
david@bluenote:~/Desktop/wifi_card_driver$ sudo ndiswrapper -m
module configuration already contains alias directive

david@bluenote:~/Desktop/wifi_card_driver$ ndiswrapper -l
netw4x32 : invalid driver!

```

what the hell can i do?

---

### Post by Rapid_Fire222 on 2007-08-31
im having the same problem please help it keeps saying invalid driver

---

### Post by fjodork on 2007-09-10
hi
i have succesfully installed the driver in ndiswrapper, BUT it does not find any networks.

The module is loaded and is in the kernel as well, but in the network manager there are no networks at all. on another laptop using speedtouch 121g with ndiswrapper the networks are there and things work perfectly... suggestions?

---

### Post by fjodork on 2007-09-10
[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty)

this howto worked perfectly :P i only used the 1,47 ndiswrapper version instead off the 1.43..

Great stuff.


now an offtopic question - possible to disable the mousetouchpad from  time to time? I use a usbmouse most off the time, and when i type i often touch the pad - pretty irritating-- is it possible to enable or disable it like in windows?

br fjodork

---

### Post by Marty4344 on 2007-09-11
hey i just wanted to give anyone a heads up...maybe most of you know this already and are still having problems but when i was getting the invalid driver issue with ndiswrapper for the file netw4x32.inf i tried the netw4x64.inf file because im running feisty 64 bit edition..and continued following the same steps and everything worked...if that don't work try the other inf files in that directory..see if they work..if not then  
just remove them and try a different one.

---

### Post by fjodork on 2007-09-12
Hi.

I have installed the driver and it works ok. but sometimes, even though im connected to the AP or the router, and have an IP assigned by DHCP, i cant get online. I have to either to disable/enable the WLAN or i have to restart the computer and login again to the network in order for the webpage to load...

Anyone else with same problem?

---

### Post by chacal69_ on 2007-09-16
Hi i got it working in a Asus g1s laptop with ndiswrapper, it works just fine for 5 minutes but after then it stops receiving packages so altought i'm conected to the wifi network it doesn't work. Any idea why this happens?

---

### Post by brad103 on 2007-11-21
Just a note for thise trying this howto. I kept getting the invalid driver issue, and I could see it installed when looking at the ndiswrapper gui. Turns out the driver download from the link provided gives files that look like
NETw4x32.INF
which is different case to that in howto, which is all lowercase. Try renaming the .INF file to be all lowercase and try adding that instead.

---

### Post by monkeyking on 2007-12-22
don't use ndiswrapper,
use the native linux driver [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24)

---

### Post by skeff on 2007-12-26
I've noticed this thread hasn't been replied to for a while, since I guess most people don't have much trouble with iwl4965 anymore.

I've been running ubuntu 7.10 for a while with a vista dual-boot and I've noticed recently that the network speed tends to be 1/10 in Ubuntu compared to in Vista.

Now I'm running LinuxMint 4.0, which is basically ubuntu 7.10, and the same problem was there. So I decided to switch to the windows drivers by force of ndiswrapper, and it seems the network speed has picked up very very markedly.

Not sure where to report this though. Feel free, anyone.
-simon

---

### Post by kitpierce on 2008-01-17
To Skeff:
I haven't had any problems with Kubuntu 7.10 - driver works great out of the box.  Also works great with Mint 3.1 & 4.0, as well as Suse 10.3, and Fedora 8.

Hope that helps.

---

### Post by colonel32 on 2008-04-18
Thanks so much for the post. It only took me 7 days, 1 purchased wireless card that didnt work, and a lot of stress and annoyance before I found your post. Now I have wireless for my Dell Inspirion 1505 and can work anywhere again. 

Thanks Again!!!

---

### Post by mattmolitor on 2008-04-27
Thank you!  It took me a while to find your post after trying other methods of getting my wireless to work.  This worked great and I am pleased to move my computer back out of the basement (only wired connection).

Thanks again.

---

