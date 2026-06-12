---
title: "Linksys WMP54G/rt61 - Dapper install probs"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by bigdave146 on 2006-10-28
Hello

I am trying to get my WMP54G card working with Dapper.  I have followed the link at [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980) and i still have problems !!!!

This is what I have done...

Clean install of Dapper LTS and installed updates (kernel 2.6.15-27-386)

$ iwconfig ra0
ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Frequency:1 MHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ dmesg | grep ra0
[17179601.496000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179671.816000] ra0: no IPv6 routers present
[17179700.892000] ra0: no IPv6 routers present
[17179785.248000] ra0: no IPv6 routers present

$ lshw
...stuff deleted...
 *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:18:39:17:f7:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT61 Wireless

$ lspci
...stuff deleted...
0000:03:07.0 Network controller: RaLink: Unknown device 0301

So downloaded rt61 drivers -  ([http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)) and extracted.
Installed gcc, make, kernel headers and source from Synaptic.
Followed instructions in readme...
	sudo cp Makefile.6 Makefile
	sudo make all – saw an error, is it important ?

/home/blah/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/druddle/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_info.o
In file included from /home/druddle/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/druddle/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/druddle/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/druddle/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_info.c:40:
	
	sudo mkdir -p /etc/Wireless/RT61STA/
	sudo cp *.bin /etc/Wireless/RT61STA/.
	sudo cp rt61sta.dat /etc/Wireless/RT61STA/.
	cd /etc/Wireless/RT61STA
	sudo vi -b rt61sta.dat

Only changes I made are...

SSID=Ruddle
NetworkType=Infra
Channel=0
AuthMode=SHARED
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=0819708609

	sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.
	sudo depmod
	sudo modprobe rt61
	sudo iwconfig ra0
	
ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So it doesnt look like the driver has loaded.

After a reboot...

$ iwconfig ra0
ra0       no wireless extensions.

Please help me as I am on the verge of installing XP instead as i have spent hours on this!!

Dave

---

### Post by bigdave146 on 2006-10-28
Got it working by writing a script to do all the iwset/iwpriv commands.  Dont know why its not reading the .dat file.

Dave

---

### Post by foxxx on 2006-12-11
could you post your self-written config for me? i´m going nuts here... :(
thx

---

### Post by dgold on 2006-12-15
> **bigdave146 said:**
> Got it working by writing a script to do all the iwset/iwpriv commands.  Dont know why its not reading the .dat file.


Would it be too much to ask that you would at least post how you solved the problem?

there is far too much of this type of activity on these forums - I have a problem - oh, wait I fixed it. This contributes nothing to the community and is downright selfish.

2c

Daniel

---

### Post by MeeMaw on 2006-12-15
I agree!  It would help others of us having the same problems!!!
](*,)    

Thanks,     MeeMaw

---

### Post by bigdave146 on 2007-01-23
File was

sudo ifconfig ra0 up
sudo iwlist ra0 scan
sleep 5
sudo iwconfig ra0 essid <My SSID>
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<key>
sudo dhclient ra0

Called this /etc/init.d/rt61 and added link to /etc/rc3.d

Dave

---

### Post by Jim Rogers on 2007-01-25
I have used Synaptic and found I have installed:
     gcc
     make
     kernel headers

I can find no reference to "source"

When I run the makefile, the process errors out with the following:
     ***No rule to make target 'driver/modules'
Do you have any clue as to where I should look to remedy this?

Any help would be greatly appreciated - third day trying to get wireless going....

---

### Post by Jim Rogers on 2007-02-01
ONE MORE LOOK AT THIS PROCESS

Actually, following bigdave146's first post, I found that the driver was indeed loaded. I searched the /etc/Wireless/RT61STA directory and the /lib/modules/2.6.17-10-generic/kernel/drivers/net/ and found everything was where it should be.

Usng the terminal:
   1)   entered iwconfig rao and and received "ra0 no wireless extensions".
   2)  I entered ifconfig ra0 up.
   3) again entered iwconfig ra0 and the .dat file was then loaded. So apparently the driver needed to be started ( makes sense ) before the .dat file is loaded. Once started everything is as it should be.

So the easy solution was:
   1) using nano -w /etc/network/interfaces
   2) added the following to automate the startup process on boot up.
                auto ra0
                iface ra0 inet dhcp

note: all the other ethernet interfaces on my computer had similar items posted in the /etc/network/interfaces file.

Been fun, just did not understand the necessity of the scripting. This seems "cleaner" to me.
the setup of the /etc/network/interfaces file was generously contributed by "incursorated".
Net result was the "special file" was not necessary nor the symbolic linking. Obviously either solution works, but this was easiest for me.

---

### Post by raydekok on 2007-02-08
ok i did this and it worked fine en great

[http://ubuntu.lupine.me.uk/dists/dapper/main/](http://ubuntu.lupine.me.uk/dists/dapper/main/)

---

### Post by pushingbuttons on 2007-03-11
> **bigdave146 said:**
> File was

sudo ifconfig ra0 up
sudo iwlist ra0 scan
sleep 5
sudo iwconfig ra0 essid <My SSID>
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<key>
sudo dhclient ra0

Called this /etc/init.d/rt61 and added link to /etc/rc3.d

Dave


Just wanted to thank you for this.   I spent most of the day with the latest release trying to get it to work.  Saw your note, installed the 6.06.1 LTS, logged in, ran the commands above as given, and it just worked.

Don't know what happened to the 6.10 release, but back rev-ing worked for me.

---

