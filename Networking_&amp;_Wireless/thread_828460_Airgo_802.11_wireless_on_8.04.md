---
title: "Airgo 802.11 wireless on 8.04"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by sgt_ferret on 2008-06-13
Hello,
     I just install Ubuntu 8.04, and I'm having LOTS of trouble getting my wireless card to work.  The card is an Airgo 802.11 mini pci with MIMO wireless card, and I've tried ndiswrapper, and it's still being really ridiculous.  The site I'm using to help guide me through is [http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

Thanks for all your help in advance!

---

### Post by lister171254 on 2008-08-24
If its any consolation, I have the same problem. The card is recognised and correctly identified but nothing I do will load a driver for this card.

---

### Post by EviLLeMonKey on 2008-09-26
I am also having the same problem. I have tried using ndiswrapper and the windows driver. That does not work, the .inf file is AUTORUN.INF ndiswrapper will not install this. I have also tried using the linux driver here [http://sourceforge.net/projects/agnx80211driver](http://sourceforge.net/projects/agnx80211driver) but when I get to the point after when I use the Make command (after being untarred) I get an Error 2 message. I read the Readme file for this driver and it says "The KDIR is defined to /pub/wd in Makefile, you need to change to your kernel 
DIR in order to compile success."

I open up the Makefile and it reads as followes:

[I]-include .config

      

KVER    := $(shell uname -r)
      
#KDIR    ?= /lib/modules/$(KVER)/build
    
KDIR    ?= /home/yanbo/kernel/wireless-testing_fujitsu
   
PWD     := $(shell pwd)



obj-m := agnx.o



agnx-objs := rf.o \
          
             pci.o \
          
             xmit.o \
           
             table.o \
	     
             sta.o \
            
             phy.o



default: modules



modules:
	
	$(MAKE) -C $(KDIR) M=$(PWD) modules


clean:
	
	rm -rf *.o *.ko cscope* .*.cmd .tmp_versions agnx.mod.c Module.symvers
[/I]

am I suppose to change something in the Makefile?? I am assuming it would be something to the right of KDIR, and would i need to uncomment (#) the first KDIR. If anyone has any insight into this any helps, hints, or links would be much appreciated.

---

### Post by wesmo on 2008-10-13
You don't need to uncomment the first kdir, rather the second kdir should be change to suit your local kernel source directory (found at /usr/src/linux_kernel_version). The command "uname -r" will show you which kernel version you are running. This requires a wireless-testing kernel to compile. This driver was added to the linux-staging kernel recently too.

I've used the blogspot link many times to get airgo drivers working with wpa2 & a linksys airgo pci card - make sure you download the svn version of ndiswrapper ([http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)) as it incorporates a couple of fixes (not found in intrepid or hardy). Upon reaching step 13 (part 2) you should lsmod and confirm the ndiswrapper is loaded. Additionally, 32bit drivers + ndiswrapper will not work on an amd64 install. There are no known airgo 64 bit windows drivers. The most recent Airgo windows drivers available v1.5.5.6 (for use with ndiswrapper) can be found here [http://www.laptopvideo2go.com/forum/index.php?showtopic=10239&view=findpost&p=35033](http://www.laptopvideo2go.com/forum/index.php?showtopic=10239&view=findpost&p=35033)

After that follow [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) to setup a static wireless link. Make sure you use wpa-driver wext & do NOT delete the loopback entry (else you'll experience excruciating loading times/package config times as the gnome daemon looks for loopback and fails - took me months to work out :D ):

so your etc/network/interfaces should look like:

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet static
address your_staticip_here
gateway your_gateway_here
dns-nameservers your_nameserver_here
netmask 255.255.255.0
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"]

Note that with kernel 2.6.25 onwards ndiswrapper support has disappeared - chiefly due to its access to GPL symbols removed [http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL](http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL). Hence with 8.10 onwards, your best off trying the yanbo's driver (although it looks like intrepid's kernel does not integrate the removal of GPL symbol access patch)

hope it helps

---

