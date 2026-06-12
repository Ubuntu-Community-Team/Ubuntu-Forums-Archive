---
title: "Mad WiFi Help"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Real Newbie on 2007-02-04
I could really use some help.I feel that I am just a short putt from solving my problem.
I have an old P100 laptop with 160MB ram, 40GB HD. I have installed Xbuntu 6.06. I have a Proxim Gold ORiNOCO a/b/g ComboCard Model 8480-WD. It is an Atheros Chipset card.

```
kelly@xbuntu:/$ lspci
0000:00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
0000:00:01.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2093 [MagicGraph 128ZV] (rev 02)
0000:00:0a.0 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)
0000:00:0a.1 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)
0000:01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
``` 

I downloaded and installed MAD WiFi via Synapatic. I am following the instructions from the Mad WiFi page and I am geting nowhere.

The instructions are 

First, set all your MadWifi devices down:

ifconfig ath0 down
ifconfig wifi0 down

```
kelly@xbuntu:/$ sudo ifconfig ath0 down
Password:
kelly@xbuntu:/$ sudo ifconfig wifi0 down
wifi0: ERROR while getting interface flags: No such device
```

then-
Assuming that you're inside the MadWifi directory, execute the following scripts to remove the current modules from your system and its memory:
cd scripts
./madwifi-unload.bash
./find-madwifi-modules.sh /lib/modules/
cd ..
```

kelly@xbuntu:~$ cd /lib/modules/2.6.15-25-386/madwifi
kelly@xbuntu:/lib/modules/2.6.15-25-386/madwifi$ cd scripts
bash: cd: scripts: No such file or directory
kelly@xbuntu:/lib/modules/2.6.15-25-386/madwifi$ ./madwifi-unload.bash
bash: ./madwifi-unload.bash: No such file or directory
```
I thought I went to the madwifi directory. Did I? Why did the commands not work? I have been fighting this for 2 months, Can anyone shed some light on what is happening here? 

Additional info
```
kelly@xbuntu:/$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:5.58 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Thanks for any help.

---

### Post by TheMono on 2007-02-04
So, you have linux-restricted-modules installed?

---

### Post by Real Newbie on 2007-02-04
I think that I installed it via Synaptic. How do I tell?

Next question-If I upgrade to 6.10, will it install he card automatically?

Thanks for any help,
Noob

---

### Post by pmshirey on 2007-02-04
You also need ndiswrapper installed. Here are the steps for that.
[LIST=1]
[*]Insert any Ubuntu live CD
[*]go to synaptic package manager
[*]type in ndiswrapper in the search box
[*]mark both ndiswrapper-custom and ndiswrapper-utils 1.8 for installation
[*]click apply
[/LIST]
If you did it right you will now have ndiswrapper installed on your computer:) .

---

### Post by tturrisi on 2007-02-04
> **pmshirey said:**
> You also need ndiswrapper installed. Here are the steps for that.
[LIST=1]
[*]Insert any Ubuntu live CD
[*]go to synaptic package manager
[*]type in ndiswrapper in the search box
[*]mark both ndiswrapper-custom and ndiswrapper-utils 1.8 for installation
[*]click apply
[/LIST]
If you did it right you will now have ndiswrapper installed on your computer:) .
Ignore the above, you do NOT need ndiswrapper for atheros chipset pcmcia cards.  Ndiswrapper is a "wrapper" application that uses the windows drivers for a device.  Madwifi is the linux driver that works with atheros chipset cards.

If you installed the restricted modules for your kernel, then just run the networking applets,

---

### Post by Real Newbie on 2007-02-05
How do I run the networking applets? I can't find them in any of the menu's?

Thanks,
Noob

---

### Post by tturrisi on 2007-02-05
Applications menu, select Systems -> Networking to bring up the network-admin tool.

---

### Post by Real Newbie on 2007-02-05
I have been trying to configure from the Network Admin tool. How do I configure using MadWiFi?
That seems to be the only thing that will configure a Atheros chipset.

Noob

---

### Post by spd106 on 2007-02-05
It depends on what you are trying to achieve.

If you simply want to connect to a managed network then you just need to install the linux-restricted-modules packages. These contain the madwifi drivers (specifically the ath_hal and ath_pci kernel modules). Then you can use the network-admin capplet that you have been directed to above.

You should know that the 6.06 releases have madwifi-old. The 6.10 release has madwifi-ng.

If you want to do more advanced things such as monitor mode, then you will have to download the madwifi source code and build it yourself. If you want to do this I suggest you study the madwifi.org website first.

---

### Post by tturrisi on 2007-02-05
fyi
madwidi old and madwifi_ng both have monitor mode support, as do all other versions.

Real Newbie
net-admin works with madwifi.
Are you using any encryption?  net-admin ONLY works with WEP, not WPA.

---

### Post by Real Newbie on 2007-02-07
I am not using any encryption. 

I found some posts that suggested that 6.10 had better support for the Atheros chipset. I used the upgrade utility in Xbuntu and now the whole system has crashed. I found out after the fact that it was problematic.

Oh well...

I am downloading a Xbuntu 6.10 install CD and will try it in the morning. I also ordered a Chiefmax wireless card ([http://3btech.net/ch5480wipcne.html)](http://3btech.net/ch5480wipcne.html)). It uses the RT2500 chipset, which is supposed to have excellent support under Linux.

Does anybody have any expierence with this card?

Thanks for all of the help,
Noob

---

### Post by tturrisi on 2007-02-08
do a forum search here, rt2500 has issues as well.

---

### Post by drumkitcat on 2007-02-08
> **pmshirey said:**
> You also need ndiswrapper installed. Here are the steps for that.
[LIST=1]
[*]Insert any Ubuntu live CD
[*]go to synaptic package manager
[*]type in ndiswrapper in the search box
[*]mark both ndiswrapper-custom and ndiswrapper-utils 1.8 for installation
[*]click apply
[/LIST]
If you did it right you will now have ndiswrapper installed on your computer:) .

do you boot up using the live cd or do you boot up normally and put the live cd in after?
where do you click to get the synaptic package manager?

---

### Post by Real Newbie on 2007-02-17
I have finally solved my wireless problem.

Quick recap...
I have an old Gateway Solo 150 MMX Pentium w 160MB RAM that my 13 YO found. He asked if he could have it. It was my 1st step into Linux. I have struggled to get wireless to work for the last 3 months with an old Proxim a/b/g gold card. I have tried DSL Linux, MEPIS (very slow on the old machine), Ubuntu, and settled on Xbuntu (still a little slow, but not unacceptably slow for a 13YO). I started out with 6.06 moved to 6.10. Every installed had to be done at least a couple of times to get it right (because I didn't know what I was doing). All of this was to get the wireless card to work.

In searching the forumns, I found a post that had a link ([http://3btech.net/ch5480wipcne.html](http://3btech.net/ch5480wipcne.html)) to a card that was said to just work-w/o any problems. I got it this morning, put it in the old laptop and 2 minutes later I was surfing. The card is less than $20 w/ free shipping and performs as advertised. As my wife pointed out to me earlier, she was ready to kill me over all of the time I have spend on this issue. I should have bought the card 3 months ago.

FULL DISLOSURE-I have no financial stake, or any stake in the company that sells these. As a mater of fact, I had never heard of them. Just because it worked for m does not mean that it will work for you.

For those of you still fighting the wireless battle, I might give it a try. For $20 it was more than worth it.

Thanks again to all of those that have tried to help me with this and all of the other problems that I have had.

Noob

---

### Post by jgcamp99 on 2007-02-24
> **Real Newbie said:**
> I have finally solved my wireless problem.

Quick recap...
I have an old Gateway Solo 150 MMX Pentium w 160MB RAM that my 13 YO found. He asked if he could have it. It was my 1st step into Linux. I have struggled to get wireless to work for the last 3 months with an old Proxim a/b/g gold card. I have tried DSL Linux, MEPIS (very slow on the old machine), Ubuntu, and settled on Xbuntu (still a little slow, but not unacceptably slow for a 13YO). I started out with 6.06 moved to 6.10. Every installed had to be done at least a couple of times to get it right (because I didn't know what I was doing). All of this was to get the wireless card to work.

In searching the forumns, I found a post that had a link ([http://3btech.net/ch5480wipcne.html](http://3btech.net/ch5480wipcne.html)) to a card that was said to just work-w/o any problems. I got it this morning, put it in the old laptop and 2 minutes later I was surfing. The card is less than $20 w/ free shipping and performs as advertised. As my wife pointed out to me earlier, she was ready to kill me over all of the time I have spend on this issue. I should have bought the card 3 months ago.

FULL DISLOSURE-I have no financial stake, or any stake in the company that sells these. As a mater of fact, I had never heard of them. Just because it worked for m does not mean that it will work for you.

For those of you still fighting the wireless battle, I might give it a try. For $20 it was more than worth it.

Thanks again to all of those that have tried to help me with this and all of the other problems that I have had.

Noob

I did that a few years back with a Netgear MA401RA Rev D and Linux. But alas, everything I read Ubuntu and this card leaves me hopeless. I have a D-Link DWL-650+ Rev 1 ATX100 chipset that I read is fully supported and works out of the box, but it doesn't and is only slightly better than the Netgear, as it's recognized. Anyway, just bought the Proxim 8480-WD, your experience with it is not encouraging news, I guess I'll find out soon enough though, it arrives next monday ?

---

