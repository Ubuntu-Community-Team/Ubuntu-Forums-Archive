---
title: "[SOLVED] Internet works with Windows but not Ubuntu"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by Damien Kane on 2008-03-26
Hi all -

I thought I'd post under a different heading in case other people might have an idea.

What's happened, is that I recently upgraded my desktop machine and installed Ubuntu v7.10 but it doesn't connect to the internet. I've gone through forums and help files and it's clear there's a problem with the network card, a Realtek RTL8168C/8111C Family PCI-E Gigabit Ethernet NIC.

I really like Ubuntu, but I'm no expert but I can't use it because of no internet connection. When trying to recompile stuff as per some instructions elsewhere in these forums, I completely destroyed Ubuntu and it doesn't boot up.

So, I'm back to re-installing which isn't a problem, but I know I'll still have the same issue with getting on the internet.  I dual boot with Vista and understand there's some sort of LAN conflict. I tried a few things - to be honest, I'm lost in the forest.

I'd appreciate any help. I hope it gets fixed with the new Ubuntu version.

Thanks in advance,
Damien.

---

### Post by superprash2003 on 2008-03-26
try this [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html)

---

### Post by dstew on 2008-03-26
There might be an issue with the wake-on-lan feature of Vista. See [this thread]("http://ubuntuforums.org/showthread.php?p=4586020"). Different card, and XP, but maybe the same problem.

EDIT: To see if it is the wake-on-lan issue, [this thread]("http://ubuntuforums.org/showthread.php?t=538448") gives details of a unplug/shutdown test that will confirm (or deny) that this is the problem.

---

### Post by Damien Kane on 2008-03-26
Here's what I did:

In Vista:
1. Made sure that the power saver on the device is off
2. Made sure that the LAN wakeup is disabled
3. I repeated the above steps and turned off the LAN in the bios, and back on again.

In Ubuntu:
1. Re-installed everything
2. Tried the boot up method after disconnecting everything for 20 seconds
3. Tried the boot up method with everything connected
4. Tried to manually configure DCHP, but the options for ip address etc were greyed out
5. Tried to install wicd and received the following error message: "Error: conflicts with the installed package 'network manager'"

There is something on the Realtek site to install the driver, but I couldn't follow it and completely stuffed up the previous install which is why I had to reinstall everything. It'd be much simpler if it was one of those deb files so I just double-click it and it works.

I was wondering if it could be fixed - if not, is there another version of Linux that perhaps does support the network adapter (and will the new version of Ubuntu support it?)

Many thanks for your assistance.

---

### Post by dstew on 2008-03-26
First, what is the result of the unplug/shutdown test?

---

### Post by Damien Kane on 2008-03-26
Yeah, the unplugging and shutting down test didn't have any effect. I don't know if it's the card version, but most of the posts I've looked at are the 'B' series, but I have a 'C' series card. I tried to re-install the driver from the Realtek site (the instructions weren't exactly accurate but I got there in the end - last time, I destroyed the system!), but it still didn't work (although I didn't destroy the system this time). There was a terminal command to see if it was installed so I thought I'd post the output here because I don't understand it. By the way, the computer has a wireless card but I don't have a wireless modem.

I think it should be called plug n pray instead of plug n play!!!

h0      Link encap:Ethernet  HWaddr 00:1E:8C:40:32:76   
          inet6 addr: fe80::21e:8cff:fe40:3276/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:4294967258 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:18 Base address:0x4000  
 
eth0:avah Link encap:Ethernet  HWaddr 00:1E:8C:40:32:76   
          inet addr:169.254.5.13  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0x4000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:2984 (2.9 KB)  TX bytes:2984 (2.9 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:16:44:73:DA:5B   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-73-DA-5B-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Damien Kane on 2008-03-26
How'd that smiley face get in there?!

---

### Post by dstew on 2008-03-27
> How'd that smiley face get in there?!Avoid smileys by pasting between quote tags (on the toolbar of the text entry box).

It looks like the card is working, and you do not have the wake-on-lan problem if it passed the unplug/shutdown test. Most likely, you have a configuration problem. I think it is due to IPv6. If you don't need it, disable it. See [this]("http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/"). You can google for other info on the IPv6 problems.

---

### Post by Damien Kane on 2008-03-27
It works now!

There are two threads on the subject:

[http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998](http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998)
[http://ubuntuforums.org/showthread.php?t=699658&highlight=8168&page=2](http://ubuntuforums.org/showthread.php?t=699658&highlight=8168&page=2)

The second one worked mostly but I had to add a couple of things (copied and pasted here for convenience for other people):

1 - Download the latest driver from Realtek from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)
2 - Copy the file to the Desktop and extract it then open a terminal. cd Desktop
3 - $ sudo mv r8168-8.004.00 /usr/src

4 - $ cd /usr/src/r8168-8.004.00

5 - $ sudo make clean modules

6 - $ sudo make install

7 - $ sudo depmod -a

8 - $ sudo insmod ./src/r8168.ko

10 - $ cd /etc/modprobe.d

11 - $ sudo touch blacklist-network

12 - $ sudo gedit blacklist-network
13 - add text "blacklist r8169" to the file (without quotes) and save

14 - $ sudo update-initramfs -u #to make the change permanent

15 - reboot

16 - test the internet (ie, open Terminal and type ping [www.google.com](www.google.com)

I'm no expert, but I'll probably have to redo the above after each kernel update.

Thanks to all again!

---

### Post by dstew on 2008-03-27
Congratulations. Glad it is working. What you did was to compile a vendor-supported driver from source, and install it. My guess is that the open-source Ubuntu-supported r8169 driver is "supposed" to work with your card in gutsy, but different systems have different problems. Looking around it is clear that the r8169 driver in Gutsy is buggy. It seems the problem is fixed in Hardy. I don't know if the developers are going to bother to fix the r8169 driver. You might want to contribute your story to [lauchpad's bug reporting system]("https://bugs.launchpad.net/ubuntu/"). Search for bugs using r8169 as a search term. If you find one that is the same, or very similar, please report it. The specific information about your system is key to help the developers figure out what they did wrong, since this driver works fine on most systems.

---

### Post by Damien Kane on 2008-03-27
Thanks for that - I'll look at contributing the information.

I've been using Ubuntu for a bit - very impressed with Linux and its community, but I'm no expert. I'm all for trying to help people switch from Windows - but when they run into problems, the first thing they do is uninstall the system (and have problems in doing so), and unfortunately, they receive a bad opinion of Linux in general. I usually fix all their computer woes and end up with dozens of computers around the place. If I could get used to Ubuntu and hep them through, there'd be a good base to build upon for Linux, and drive people away from Windows.

I'll mark this thread as solved and bookmark it for later use! Now it's time to play.:guitar:

---

### Post by Damien Kane on 2008-03-27
Bug reported [https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012) including system specs. Thanks for that!

---

### Post by dbcambridge on 2008-03-27
Glad you managed to solve the problem. Any issue that causes disappointment to new users can clearly put them off using Linux - bad news!

I thought that I would share a recent problem that had me confused:

A few months ago I had to change my ADSL modem; my previous D-Link had stopped handling DNS so I replaced it with a Linksys. I set it up for DHCP on my home network and it worked when I was booted into Windows so I thought all was OK. Some time later I booted into Linux (with several different machines). Not one of them would log on.

After several frustrating attempts to log onto the network I realised that I had forgotten to set the Domain Name in the DHCP server settings of the modem. It appears that Windows machines can handle a domain name which is an empty string but Linux can't.

Having set a valid Domain Name my Linux boxes all accessed the network and the internet with no problem. Alright, I admit it was a bit of a schoolboy mistake on my part, but I don't mind looking silly if this reply stops just one newby from throwing his computer out of the window or abandoning Linux!

Happy computing

---

### Post by AgDon92 on 2008-05-16
Hello,
I am brand new to Ubuntu. In fact, I just installed it yesterday. I have a Realtek 8168 card in an Acer laptop. I've tried all of the tricks posted (started with network cable plugged in, reset all power, etc).  I think it's a driver problem. I downloaded the r8168-8.006.00.tar.bz2 file from Realtek and followed the instructions in the readme. They are the same as posted above. Here are my results:


sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/tmp/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/tmp/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/tmp/r8168-8.006.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/tmp/r8168-8.006.00/src'
make: *** [modules] Error 2
 
============================================================
uname -r
2.6.24-16-generic


Any help or suggestions are appreciated.

Cheers!

Don

---

