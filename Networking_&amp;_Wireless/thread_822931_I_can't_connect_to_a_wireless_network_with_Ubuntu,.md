---
title: "I can't connect to a wireless network with Ubuntu, but I can with Windows."
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by DocHolliday2006 on 2008-06-08
Hi. There is a free wireless network, which does not require a password, etc, that I'd like to connect to.

Using my work computer, a Dell Latitude D520 loaded with windows, I have no problem connecting to the network. I just select it and it connects.

However, using my personal computer and personal laptop, which are loaded with Ubuntu, I can't get it to connect. I select it off the list of available wireless networks, and it does the swirly "connecting" animation, and then it just doesn't connect. No explanation is given.

If it matters, my work computer (Dell), uses a built in network card. It's listed as a Intel Pro/wireless 3945 ABG network connection in device manager. 


My personal laptop (an older dell) uses a proxim Orinoco a/b/g combo card that is not built in.

My personal computer (self built) has a proxim too, though I don't have the model number.

On my personal computer, the restricted driver for the wireless card is listed as: "Support for Atheros 802.11 wirelss Lan Cards"

That is obviously not proxim. I don't know what Atheros is.

Any ideas? How can I connect?

Thanks.

---

### Post by pytheas22 on 2008-06-08
Please post the output of the commands:
```

iwlist eth1 scan
iwlist wlan0 scan
iwconfig
ifconfig
lspci
```

for both of your Ubuntu machines.  Also please say what the name of the free wireless network is so that I can give you some commands to try connecting to it using the command line, which will hopefully provide more information about what's going wrong.

---

### Post by DocHolliday2006 on 2008-06-08
"Hotspot_Meriden" is the name of the network.

iwlist eht1 scan: Interface doesn't support scanning

Iwlist wlan0 scan: Interface doesn't support scanning

iwconfig:
lo no wireless extensions
eth0 no wireless extensions
wifi0 no wireless extensions
ath0:
"IEEE 802.11G Essid:"" Nickname: ""
Mode: Managed Channel: 0 Access Point: Not -Associated
Bit Rate: 0kb/s tx-power:14 dbBm sensitivity=1/1
retry: off RTS thr:off Fragment thr: off
power Management: off
Link Quality= 0/70 Signal level= -97 dBm Noise level=-97 dbm
rx invalid nwid 4639 Rx invalid crypt: 0 rx invalid frag: 0
tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

IF config:

ath0
link encap: ethernet Hwaddr 00:20:a6:4C eb:d5
Up Broadcast multicast MTU 1500 Metric:1
RX packets 23 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 32 errors: 0 dropped: 0 overruns: 0 carrier: 0
colisions: 0 txqueuelens: 0
RX bytes: 1120 (1.0 kb) tx bytes: 6301 (6.1 kb)

eth0 
Link encap: ethernet Hwaddr 00:14:2A:a7:68:29
up broadcast multicast mtu:1500 Metric: 1
RX packets: 0 errors: 0 dropped: 0 overruns:0 frame: 0
(everything else 0)
interupt: 18 base address : 0x2000

Lo
link encap: local Loopback
inet addr 127.0.0.1 Mask: 255:0.0.0
iet6 addr: ::1/128 Scope: Host
Up Loopback Running MTU: 16436
Metric: 162 errors: 0 dropped: 0 overruns: 0 frame: 11944

RX packets: 1366 errors 0 '' '' '' ''
tx packets 1336 errors:0 '' '' '' ''
collisions:0 tx queuelen: 0
rx bytes: 68300 (66.6 kb) txbryes 68300 (66.6

wifi 0
Link encap :unspec Hwaddr 00-20-A6-4C-EB-D5-00-00-00-00-00-00-00-00-00-00
Up broadcast running multicast mtu: 1500 Metric: 1
rx packets 6262 errors: 0 '' '' '' frame 11944
tx packets: 413 errors: 18 dropped: 0 overruns: 0 carriers: 0
collisions: 0 txqueuelen: 199
rx bytes 543049 (530.3 kb) tx bytes: 24532 (23.9 kb)
interrupt: 20

lspci:
0:00.0 memory controller: nvidia corp
00:01.0 ISA bridge

This goes on....getting tired of typing...

let me know if there is something specific you need off this list...


Thanks for you help,


> **pytheas22 said:**
> Please post the output of the commands:
```

iwlist eth1 scan
iwlist wlan0 scan
iwconfig
ifconfig
lspci
```

for both of your Ubuntu machines.  Also please say what the name of the free wireless network is so that I can give you some commands to try connecting to it using the command line, which will hopefully provide more information about what's going wrong.

---

### Post by pytheas22 on 2008-06-08
> lspci:
0:00.0 memory controller: nvidia corp
00:01.0 ISA bridge

This goes on....getting tired of typing...

I need the line that refers to your wireless card.  It probably says something like "Network controller (or possibly 'Ethernet controller'): Atheros...."  Keep in mind that you can always copy and paste from the terminal by highlighting text, right-clicking and selecting copy.  If you don't have any Internet access on your Ubuntu computer, you could paste into a text file and transfer it (via a USB drive for instance) to the machine you're using to make the post.

Also, please post the output of:
```

iwlist ath0 scan
```

(I was guessing earlier about what your interface's name is; it's ath0, not eth1 or wlan0; this is why I have to ask for this information again).

---

### Post by DocHolliday2006 on 2008-06-09
Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

iwlist ath0 scan

Cell 01- Address: 00:20:A6:5A:f6:82
ESSID: "Hotspot_Meriden"
Mode: Master
Frequency: 2.412 GHz (channel 1)
Quality= 10/70 Signal level= -85 dBm Noise level=-95 dBm
encryption key: off
Bit Rates: 1mb/s; 2mb/s; 5.5 mb/s; 11 mb/s; 6mb/s 12 mb/s; 24mb/s; 36 mb/s; 9 mb/s; 18 mb/s 48 mb/s 54 mb/s
extra: bcn_int 100

Cell 02
address: 00:14:95:DA:62:09
ESSSID: "2wire187:
Mode: master
Frequency 2.437 ghz (channel 6)
quality 6/7- Signal level=-89 dBm Noise level -95 dBm
Encryption key: on
Bit Rates: see above
extra: bcn_int=100

cell 03
extra: bcn_int=100
address: 00:20:A6:5A:63:51
ESSID: "Htspot_Meriden"
Mode: master
Frequency 2.417 Ghz (Channel 2)
Quality 7/70 Signal level=-88 dbm Noise level= -95 dBm
encryption key: off
bit rates: see above
Extra: bcn_int=100

The smiley face above should read: :9 5 : D A : 6 2
There you go. Let me know if there's anything else.

Thanks.

> **pytheas22 said:**
> I need the line that refers to your wireless card.  It probably says something like "Network controller (or possibly 'Ethernet controller'): Atheros...."  Keep in mind that you can always copy and paste from the terminal by highlighting text, right-clicking and selecting copy.  If you don't have any Internet access on your Ubuntu computer, you could paste into a text file and transfer it (via a USB drive for instance) to the machine you're using to make the post.

Also, please post the output of:
```

iwlist ath0 scan
```

(I was guessing earlier about what your interface's name is; it's ath0, not eth1 or wlan0; this is why I have to ask for this information again).

---

### Post by pytheas22 on 2008-06-09
Thanks for all the information.  Please try running these commands and post any output that you get:
```

sudo -s
iwconfig ath0 channel 1
iwconfig ath0 essid "Hotspot_Meriden"
dhclient ath0
dhclient ath0
```

These commands should get you connected to the Internet if the card is working correctly.  If not, hopefully they'll point out what's going wrong.

---

### Post by DocHolliday2006 on 2008-06-09
Ok. So it accepted all commands up to: iwconfig ath0 essid "Hotspot_Meriden"

on dhclient ath0, it gave me:

Internet systems consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet systems consortium
all rights reserved
for more info.....

wifi0: unknown hardware address type 801
wifi0: unknown hardware daddress type 801
listening on LPF/ath0/00:20:a6:4C:eb:d5
sending on ''
sending on socket/fallback
DHCPDISCOVER on ath0 to 255.255.255 port 67 interval 3
'' interval 6
'' interval 6
'' interval 7
'' interval 9
No DHcpoffers received.
No working leases in persistent database- sleeping

on dhclinent ath0:

There is already a pid file/ var/run/dhclient.pid with pid 6238
killed old client process, removed pid file
internet systems consortium dhcp client v3.0.6
.........
....
...

similar stuff.

still can't connect.




> **pytheas22 said:**
> Thanks for all the information.  Please try running these commands and post any output that you get:
```

sudo -s
iwconfig ath0 channel 1
iwconfig ath0 essid "Hotspot_Meriden"
dhclient ath0
dhclient ath0
```

These commands should get you connected to the Internet if the card is working correctly.  If not, hopefully they'll point out what's going wrong.

---

### Post by pytheas22 on 2008-06-09
Everything looks like it's working alright.  The card just isn't getting an IP address, which could have to do with the way that the wireless network works, not your card.  When you connect in Windows to Hotspot_Meriden, does it just connect, or do you have to go to a browser page first or something to register?  Also, have you ever connected to Hotspot_Meriden on the same computer that's now running Ubuntu (because the wireless network could be configured to only give out IP addresses to certain computers, which it keeps track of by looking at the hardware addresses of their wireless cards).

Another possible problem is the signal strength--it's reported as very weak.  The Linux Atheros drivers have issues with signal strength.  You could possibly get a stronger signal if you used ndiswrapper instead of the Linux driver.  But first let us know about how the network Hotspot_Meriden works; then we can decide whether ndiswrapper would be helpful or not.

---

### Post by DocHolliday2006 on 2008-06-09
In windows, you choose the network off of a list of wireless networks, and then when you open the browser, it bring you to a page where its lists the terms of use and you have to click a button saying that you agree.

The signal strength where my desktop is is a bit on the weak side. Even the windows laptop gets one bar only there. However, in an area that has  full bars for my windows laptop, my ubuntu laptop cannot connect, so I think this is an issue beyond signal strength. If I can get the connect to work, I'm going to buy something to relay the signal from near the window where I get a  lot of bars.


I have never connected to hot spot Meriden with the computer that is installed with Ubuntu. 


> **pytheas22 said:**
> Everything looks like it's working alright.  The card just isn't getting an IP address, which could have to do with the way that the wireless network works, not your card.  When you connect in Windows to Hotspot_Meriden, does it just connect, or do you have to go to a browser page first or something to register?  Also, have you ever connected to Hotspot_Meriden on the same computer that's now running Ubuntu (because the wireless network could be configured to only give out IP addresses to certain computers, which it keeps track of by looking at the hardware addresses of their wireless cards).

Another possible problem is the signal strength--it's reported as very weak.  The Linux Atheros drivers have issues with signal strength.  You could possibly get a stronger signal if you used ndiswrapper instead of the Linux driver.  But first let us know about how the network Hotspot_Meriden works; then we can decide whether ndiswrapper would be helpful or not.

---

### Post by pytheas22 on 2008-06-09
If you're sure that the signal where you're trying to connect with the Ubuntu laptop is good, then the only other thing I know to try is to use ndiswrapper, which lets you drive wireless cards using their Windows drivers instead of native Linux ones.  You would need to follow these steps:

Make sure your Ubuntu install CD is in the drive.

1. blacklist the native Linux drivers for your wireless card:
```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
echo 'blacklist ath_hal' >> /etc/modprobe.d/blacklist
```

2. install ndiswrapper:
```

sudo apt-get install ndiswrapper ndisgtk
```

3. find the Windows driver for your wireless card.  If you have the CD that came with the card, that would be the easiest place to look.  Otherwise you can download them from the Internet.  If you can't find them I can help, but I'll need to know the exact name and model of your card.

Copy the files for the Windows wireless driver to your Ubuntu computer.  You don't need all of the files associated with the driver, but you will need to have the three files whose names end in .cat, .sys and .inf; those are what ndiswrapper needs in order to work.

4. in a terminal type:
```

sudo ndisgtk
```

and use that program to install the Windows driver.  You'll have to navigate to the place where you copied the Windows driver files, and select the file whose name ends in .inf.

5. If all has gone well, you'll get a message at this point to the effect of "device present, driver loaded."  Now you can reboot, and hopefully you'll be able to connect.  If you can't, post the output of:
```

iwconfig
```

---

### Post by DocHolliday2006 on 2008-06-10
so when I type this in, it says:

Reading package lists...done
building dependency tree
reading state information...done
E: couldn't find package ndiswrapper

The Ubuntu CD is installed.

Any ideas?

> **pytheas22 said:**
> 
2. install ndiswrapper:
```

sudo apt-get install ndiswrapper ndisgtk
```



---

### Post by pytheas22 on 2008-06-11
You probably got this error because apt (the program to install software) doesn't know to look at the CD for packages (sorry; I forgot to anticipate this possibility).  You can correct it by going to System>Administration>Software Sources and under the Ubuntu Software tab, make sure that the box to install software from the CD (under the "Installable from CD-ROM/DVD" section) is checked.  Then press Close, and when you're asked if you want to reload the software list, say yes.  Then try following the instructions of my last post again; apt should find ndiswrapper on the CD and install it.

If for some reason it still doesn't work, you can find the packages manually by exploring your Ubuntu CD (you can open it by selecting it from the Places menu) and navigating to the location '/media/cdrom0/pool/main/n'  Then open the folder for ndiswrapper and install the two packages there by double clicking on them.  Then go back up a directory and open the ndisgtk folder to install ndisgtk in the same way.

---

### Post by steelmachine on 2008-06-11
[http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/)

Maybe something useful in the link above?

---

### Post by DocHolliday2006 on 2008-06-11
> **steelmachine said:**
> [http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/)

Maybe something useful in the link above?

It looks like it might have been, but it requires an active internet connection to use, so it's useless to me.

---

### Post by DocHolliday2006 on 2008-06-11
I've got my Ubuntu 8.04 Cd in the drive. I can access it, etc, so I know it's working.

But when I got into software sources, under the installable from CD-Rom/DVD, there is no box to click.

But when I 

> **pytheas22 said:**
> You probably got this error because apt (the program to install software) doesn't know to look at the CD for packages (sorry; I forgot to anticipate this possibility).  You can correct it by going to System>Administration>Software Sources and under the Ubuntu Software tab, make sure that the box to install software from the CD (under the "Installable from CD-ROM/DVD" section) is checked.  Then press Close, and when you're asked if you want to reload the software list, say yes.  Then try following the instructions of my last post again; apt should find ndiswrapper on the CD and install it.

If for some reason it still doesn't work, you can find the packages manually by exploring your Ubuntu CD (you can open it by selecting it from the Places menu) and navigating to the location '/media/cdrom0/pool/main/n'  Then open the folder for ndiswrapper and install the two packages there by double clicking on them.  Then go back up a directory and open the ndisgtk folder to install ndisgtk in the same way.

---

### Post by pytheas22 on 2008-06-11
> But when I got into software sources, under the installable from CD-Rom/DVD, there is no box to click.

I don't know why it would do that.  But try this:

sudo dkpg --install /media/cdrom/pool/main/n/ndiswrapper/ndiswrapper*
sudo dkpg --install /media/cdrom/pool/main/n/ndisgtk/ndisgtk*

This should do the same thing as apt.

---

### Post by DocHolliday2006 on 2008-06-11
I got it to install, and then I installed the windows driver and restarted, but it's still not letting me connect.

Do you see the post that the other guy made? Do you think that's anything? I can't try it because I can't connect to the internet. 

Any other ideas welcome.

> **pytheas22 said:**
> I don't know why it would do that.  But try this:

sudo dkpg --install /media/cdrom/pool/main/n/ndiswrapper/ndiswrapper*
sudo dkpg --install /media/cdrom/pool/main/n/ndisgtk/ndisgtk*

This should do the same thing as apt.

---

### Post by pytheas22 on 2008-06-11
Did you run the commands to blacklist the native drivers?  i.e.:
```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
echo 'blacklist ath_hal' >> /etc/modprobe.d/blacklist
```

If not, do this and restart.

When you installed the Windows driver in ndiswrapper, did you get a message to the effect of "driver installed, hardware present?"

Is there a wireless connection listed by Network Manager and can you see networks with it?  If yes, what happens when you try to connect?  What is the output of iwconfig (you don't have to type it all, but at least tell me please which interface names it lists, e.g. lo, eth0, wlan0...).

---

