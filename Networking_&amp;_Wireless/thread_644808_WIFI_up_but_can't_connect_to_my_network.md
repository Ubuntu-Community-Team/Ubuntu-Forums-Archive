---
title: "WIFI up but can't connect to my network"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by gfd_2 on 2007-12-19
My wifi card now is seen (see below for specifics) but for some reason I can't connect to my network which is seen in both Network Manager (since un-installed) and in WICD (presently installed).   I click on Connect and after about 1 minute it times out.  I have a wide open network with no WEP or WAP... I have two XP laptops I use for work  which connect no problems without logging a password for the network.  

... here's what I did to get the card recognized: 

1.sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9sudo apt-get remove bcm43xx-fwcutter Add bcm43xx to the /etc/modprobe.d/blacklist file 
2.sudo gedit /etc/modprobe.d/blacklistadd this line blacklist bcm43xx and save the file.
3.Reboot 
4.Download driver for BCM94311MCG wlan mini-PCI here ( if this link expire I can't help you... this came from another site)
5.tar -xzvf WLANBroadcom.tar.gz
6.) move the folder WLANBroadcom to your home directory using the next step.
7.mv WLANBroadcom/ /home/yourname/ 
8.Install ndiswrapper from source : 
a.)sudo apt-get update
b.) sudo apt-get install build-essential 
c.) sudo apt-get install linux-headers-`uname -r`
d.) sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/buildmkdir -p ~/bcm43xx/ndiswrapper
9.) cd ~/bcm43xx/ndiswrappersudo 
10.) wget [http://downloads.sourceforge.net/ndi...er-1.49.tar.gz](http://downloads.sourceforge.net/ndi...er-1.49.tar.gz)
11.) tar xvzf ndiswrapper-1.49.tar.gz
12.) cd ndiswrapper*make distcleanmakesudo make install
13).Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper.
14.) cd /home/yourname/WLANBroadcom/
15.) sudo ndiswrapper -i bcmwl5.infndiswrapper -l 
16.) sudo gedit /etc/modulesadd this line ndiswrapper
17.) sudo modprobe ndiswrapper
18.) sudo ndiswrapper -m 
19.) reboot

After rebooting the wifi light is blue and I see my network being advertized. however... I can't connect. If I make any modifications to the /etc/network/interfaces file I loose <my network name> and have Manual Configuration in Network Manager. When I loose the essid by checking "enable roaming" in N-M I can see < my network name> 

lspci = 02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02).

iwconfig =
lo no wireless extension
eth0 no wireless extention
wlan0 IEEE 802.11g ESSID: off/ any
mode managed Frequency: 2.462 Ghz Access Point: Not-Associated Bit Rate: 54Mb/s TX-Power: 32dBm RtS thr: 2347 B Fragment thr 2346 B Power Management: off Link Quality: 0 Signal Level:0 Noise Level:0 RX invalide nwid:0 RX invalid crypt:0 Rx invalid frag:0 TX excessive retries: 0 Invalid misc: 0 Missed becon: 0

dmesg:
wlan0: ethernet device 00:1a:73:d7:d6:fe using NDIS driver: bcmwl5, version ox4640f05, NDIS version 0×501, vendor” ‘NDIS Network Adaptor” 14E4:4311.5.conf
wlan0: encryption modes support WEP, TKIP with WPA, WPA2, WPA2 PSK; AES/CCMP with WPA, WPA2, WAP2PSK.
registered new interface driver ndispwrapper
blah
blah
blah
eth0: link up
eth0: link up
Faliure registering capabilites wtih primary seciruty module.
blah
blah
blah
eth0: no IPv6 routers present
ADDRCONF(NETDEV_UP): wlan0: link is not ready
r8169: etho: link up
eth0: no IPv6 routers present


Any suggestions would be GREATLY appreciated.

---

### Post by petteriIII on 2007-12-19
I had same problem when trying to use Wireless in 7.10; 7.06 was OK. It turned out that before trying to go to Wireless you must first go to terminal and give the command: sudo /etc/init.d/networking restart  . Hope this works for you too.

---

### Post by gfd_2 on 2007-12-19
finally got home and got a chance to restart the network... here's what I got:
dcb@dcb-laptop:~$ /etc/init.d/networking restart
open: Permission denied
 * Reconfiguring network interfaces...                                          ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
open: Permission denied
                                                                         [fail]


I've also triede using a single IP... my wire connects no problems... my wireless messed the bed. 

Any suggestions?

---

### Post by petteriIII on 2007-12-20
Was sudo also in your command (sudo /etc/init.d/networking restart ? Because it gives me those same errors if I omit it.

---

### Post by gfd_2 on 2007-12-20
Mother of God this is frustrating (sorry to anyone who has replied :>) ) anyway.... yes thanks... I did rerun the command: 
dcb@dcb-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for dcb:
 * Reconfiguring network interfaces...                                   [ OK ] 


When I run iwlist here's what I get:

dcb@dcb-laptop:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:D2:91:0E
                    ESSID:"04Z411305563"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-27 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

and when I fire up Wicd I see the network... I click on the connect icon and after flushing the routing tables, resetting IP, the app goes through obtaining IP address for about a minute then times out.  If I add a static IP address in the advanced tab of the app it will go through the same process and in about 5 seconds connect to the network at 0%.  Then when I click on the wire connection I'm in after about 2 seconds.  

I'm going to try a fresh install and see what happens by using the results of `uname -r` rather then using that syntax.

---

### Post by gfd_2 on 2007-12-20
mmkkkayyy...... here are the steps I followed... 
1.)   uname –r to determine the kernel version. (record this for later use).
2.)   sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
3.)   sudo apt-get remove bcm43  -fwcutter 
4.)   Add bcm43   to the /etc/modprobe.d/blacklist file 
5.)   sudo gedit /etc/modprobe.d/blacklist add “blacklist bcm43 “ (sans the qotes)  and save the file.
6.)   Reboot 
7.)   Download driver for BCM94311MCG wlan mini-PCI here ([http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html](http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html))
8.) .  tar - zvf WLANBroadcom.tar.gz
9.)    mv WLANBroadcom/ /home/dcb/
10.)   sudo apt-get update
11.)   sudo apt-get install build-essential 
12.)   sudo apt-get install linu -headers-`uname -r`
13.)   sudo ln -s /usr/src/linu -`uname -r` /lib/modules/`uname -r`/build
14.)   sudo mkdir -p ~/bcm43  /ndiswrapper
15)   cd ~/bcm43  /ndiswrapper 
16.)   sudo wget [http://downloads.sourceforge.net/ndi...er-1.49.tar.gz](http://downloads.sourceforge.net/ndi...er-1.49.tar.gz)
17.)    sudo tar  vzf ndiswrapper-1.49.tar.gz
18.)   cd ndiswrapper*
19.)   make distclean make
20.)   sudo make install
21.)   Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper.
22.)   cd /home/yourname/WLANBroadcom/
23.)   sudo ndiswrapper -i bcmwl5.inf
24.)   ndiswrapper -l 
25.)   sudo gedit /etc/modules
26.)   add this line ndiswrapper
27.)   sudo modprobe ndiswrapper
24.)   sudo ndiswrapper -m 
25.)  reboot
26.)    sudo /etc/init.d/networking restart

Note that after I ran the network restart I got: 
listening on LPF/wlan0/00:1a:73:d7:d6:fe
sending on LPF/wlan0/00:1a:73:d7:d6:fe
sending on Socket/ fallback
DCHPDISCOVER  on wlan0 255.255.255.255 prot 67 interval 5
DCHPDISCOVER  on wlan0 255.255.255.255 prot 67 interval 7
DCHPDISCOVER  on wlan0 255.255.255.255 prot 67 interval 13
DCHPDISCOVER  on wlan0 255.255.255.255 prot 67 interval 6
No DHCP offers
No working leases in persistent database - sleeping.



Wireless light is blue... network connection is GREAT for the wire.... nothing for wireless.  When I go into Network Manager (N-M) without making any changes I can see my network but when I try to connect the app times out after ~ 1 minute.  If I make ANY changes to the /etc/network/interfaces file ... say to add anything about wlan0... after I save and reboot I have excellent wired connection but the network isn't being seen for wireless... in N-M I only see wired and manual config.  When I remove the wlan0 info from the interfaces file i can again see the untouchable wireless network.

Any suggestions?  Thanks in advance!.

---

### Post by gfd_2 on 2007-12-21
bump...

---

