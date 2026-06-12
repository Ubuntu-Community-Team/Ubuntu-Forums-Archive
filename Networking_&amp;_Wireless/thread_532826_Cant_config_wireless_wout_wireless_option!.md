---
title: "Cant config wireless w/out wireless option!"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Lord Dirk on 2007-08-23
I have been attempting to make the internet work on my laptop with freshly-installed linux.  I have followed many forum posts- I downloaded ndiswapper, ndisgtk, and both are up and running.  BUT now when i open the network options, i only have the option of a wired connection or a modem connection.  The wireless one disappeared!  because of this, in ndisgtk when i install the built in wireless card driver, it 'installs' it but doesnt show up on the list.  How may i go about getting the wireless option back into the networking screen?  the laptop has a BCM4306 wireless connection card, and I DID have the option for wireless connections earlier, but now i dont!

---

### Post by will71110 on 2007-08-23
Do a iwconfig in terminal.  Does it show up there?

---

### Post by jesselfout@gmail.com on 2007-08-23
I have the exact same problem with my card which is also a 4306

here is the output for the suggested command.
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"something"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:09:5B:6C:0A:18   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=61/100  Signal level=-65 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




Also, mine will not work on boot up but will work after i do 
sudo modprobe bcm43xx
in terminal

---

### Post by floppy-headed-drunk on 2007-09-05
Same problem.
Same symptoms.
Bummer.
Anyone have any help?

---

### Post by kevdog on 2007-09-05
Seems like you guys are using a combination of ndiswrapper and the bcm43xx driver -- in reality you can only use one or the other.  I dont really care (and you probably dont either) which one you use, only that you have an internet connecttion. Lets just see what you have right now.  Can you post the following:

lshw -C network
lspci -nn
/etc/network/interfaces
modinfo ndiswrapper
ndiswrapper -l
modinfo bcm43xx
/etc/modprobe.d/blacklist

---

### Post by yangtj207 on 2007-09-06
It seems that I do have both bcm43xx and ndiswrapper. Could you instruct me how to remove one? Thanks.

---

### Post by kevdog on 2007-09-06
To remove one or the other you need to edit the blacklist file:

gksudo gedit /etc/modprobe.d/blacklist

And add a line to the bottom of the file.

If you do not want bcm43xx:

blacklist bcm43xx

If you do not want ndiswrapper:

blacklist ndiswrapper

This will prevent the module from loading at boot time.
Reboot.

To see if either module is loaded after a reboot:
lsmod | egrep {'ndiswrapper|bcm43xx'}
Only one or the other should be listed

---

