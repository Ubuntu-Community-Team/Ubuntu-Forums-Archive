---
title: "HOW TO: DWA-552 , DWA 556 and other Atheros cards with madwifi"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by zeesson on 2008-03-07
This is simply how i got my DWA-552 and DWA-556 (Atheros chipset 5416/5418 to work for me in Linux MInt 4.0 and Ubuntu Gutsy. consistently using [color=#0040FF]madwifi [/color](a native linux driver specifically developed for atheros chipsets) which is arguably a better choice than the alternative [color=#0000FF]ndiswrapper[/color](basically a workaround that allows you to use SOME windows drivers in Linux. First please be patient with me as I am far from a Guru as far as Linux is concerned, but I will help you the best way I can and if I cannot then hopefully someone else can.


YOU WILL TEMPORARILY NEED A HARD WIRED INTERNET CONNECTION FOR THIS GUIDE


Note:  Press ENTER after each line command
first open up a terminal and in it type the following:

You dont have to install module-assistant, but i believe it helps
```
sudo apt-get install module-assistant
sudo m-a prepare
```

if you prefer or if this is not working for you you can open up Synaptic package manager in the System tools menu and install module assistant that way same goes for libc6-dev

```
sudo apt-get install libc6-dev 
```
you may be asked for a password. (sudo) allows you to execute commands as root without having to be constantly logged in as root (which would be a little dangerous) Enter the same password that you logged into the computer with.

libc6-dev will allow you to compile madwifi.

next install subversion which will allow you to retrieve the nightly snapshot of madwifi.

```
sudo apt-get install subversion
```

next we are going to create a directory where madwifi will be downloaded to and then we will change to that directory.
 ```
mkdir madwifi
cd madwifi
```
if  you did this correctly your terminal should look like this

**(username)@(computername):~/madwifi$**

next we will download the madwifi snapshot

```
svn co http://svn.madwifi.org/madwifi/trunk
```

when it is done you should see:

[b]checked out version number ####

(username)@(computername):~/madwifi$[/b]


Next we will enter the directory that was created when we downloaded the snapshot and start to compile

```
cd trunk
```

your terminal should look like this

**(username)@(computername):~/madwifi/trunk$**

and then compile

```
sudo make
```

NOTE this will take a 10-30 seconds 
 
NOTE: before we move on know that you should not have gotten **ANY** errors while compiling if you did. Then stop and try again, if that doesnt work then explain you error here.  Now for those who did not recieve any errors the next step is to install madwifi

```
sudo make install
```

NOTE:you may get a message that says that madwifi drivers are already installed from an older installation  and gives you the option to either remove them, ignore them or exit. type the letter r and then press ENTER to remove the old drivers and install the new ones.

if you dont get this message fine move on to the next step


Next you will have to add an entry to your /etc/network/interfaces file in order to be able to bring up the device. To make use of wpa_supplicant in roaming mode. 

```
gksudo gedit /etc/network/interfaces
```

this will open up a text document all you need to do is copy and paste the following into this text file after the text that is already there:

[b]#Wireless
noauto ath0
allow-hotplug ath0

iface ath0 inet manual
    wpa-driver madwifi
    wpa-roam   /etc/network/wpa_supplicant.conf

iface default inet dhcp[/b]


Now save and close that text file.

Now all that is left to do is probe the module

```
sudo modprobe ath_pci
/sbin/ifconfig
```

you should now see your network connections it should look something like this

[b]ath0      Link encap:Ethernet  HWaddr 00:19:7E:41:09:C1  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54115716 (51.6 MiB)  TX bytes:823180275 (785.0 MiB)



eth0      Link encap:Ethernet  HWaddr 00:15:58:86:70:EE  
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000 Memory:ee000000-ee020000 



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182621 (178.3 KiB)  TX bytes:182621 (178.3 KiB)



wifi0     Link encap:UNSPEC  HWaddr 00-19-7E-41-09-C1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:462907 errors:753 dropped:0 overruns:0 frame:182
          TX packets:563036 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:91695661 (87.4 MiB)  TX bytes:846831037 (807.6 MiB)
          Interrupt:21 [/b]

It's the ath0 interface that you're after for actually configuring whatever network manager you choose to use. Personally I use Wicd (which you can get form here [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)) use the instructions for Ubuntu 

NOTE you will have to uninstall network-manager from Synaptic (mentioned above) in order to use Wicd as your network manager  

Ignore the wifi0 it is just the binary hal interface. Enjoy 

I tried my best to put this together "in a simple new user style" with info i got from a bunch of different places mainly the ubuntu forums, thinkwiki, and madwifi.org.  any extra input would be appreciated

Remember **"Each One Teach One"**





**Troubleshooting**
If you're having trouble getting the ath0 interface to show up on a regular ifconfig, but can see it if you do an ifconfig -a and nothing seems to be happening with wpa_supplicant, the solution (for some unknown reason) is to rename ath0 to wlan0. This is easily done by modifying the udev rule. 

```
gksudo gedit /etc/udev/rules.d/70-persistent-net.rules 
```

this will open up a text document you should see a line that looks similar to this

[b]# PCI device 0x168c:0x0024 (ath_pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="<your mac address>", ATTR{type}=="1", NAME="[color=#FF4040]ath0[/color]"[/b]
All you need to do is change the "[color=#FF4040]ath0[/color]" to "wlan0"

save and close the document and  then remove the module with

```
sudo rmmod ath_pci
sudo pkill wpa

```

and then reprobe the module

```
sudo modprobe ath_pci
```

---

### Post by zeesson on 2008-03-15
Let me know if this is works for you please

---

### Post by dinub1 on 2008-03-22
Hey, cool.:) 

My card is a DWA 642 for laptop...(PCMCIA)  it uses the Atheros for 802.11N. I assumed it did not work with mad fi driver, though on the madfi website it is stated that it works with.

This is why I used ndiswrapper.

I had to study how to install the (under Mint 4 as well). It comes with ndiswrapper pre-installed, but does not work at all with this card. So I had to reinstall ndiswrapper by re compiling with "make" and then "install". 
Upon installing the Windows drivers from CD and typing,

$ sudo modprobe nediswrapper. My card miraculously started to work like a king... :) Before the recompiled ndiswrapper, upon issuing the modprobe command, laptop would simply freeze.

Your HOWTO worths a try and I will try it when time allows. My other/former  PCMICIA card also a D-Link with Atheros chipset, this was a Turbo G (I'm kissing the model number right now) worked with madfi out of the box. No extra tuning or modifications in the network conf file needed. Just open the knetworkmanager, configure the connection and here you go. 
Now my new card works with knetworkmanager but, with the Windows drivers using ndiswrapper.

---

### Post by TeslaTony on 2008-03-25
I just got the DWA 556 and installed it using your guide. Overall, it works quite well, except that it cuts out from time to time, and the only method I've found to work so far has been to restart my computer (which I rather dislike). I assume there's a set of commands I could use to restart the driver without restarting the whole machine, but is there a way to make sure it doesn't stop working in the first place?

---

### Post by uncommontalent on 2008-03-25
This works great. Thank you very much. I had some problems installing it manually.
I got a whole lot of errors.

I try your method first. Then I started here:

 I went to System -> Administration -> Synaptic Package Manager
entered password then searched for " module-assistant " and " libc6-dev " 

Under the module-assistant search select: module-assistant (currently version 0.10.11)

Under the libc6-dev select: libc6-dev and libc6-dev-i386 (both versions 2.6.1-1ubuntu10)

I am using Ubuntu 7.10 Desktop-amd64 version and have the DWA-556 PCI Express (PCIe) Card

Install the selected items. You will need the Ubuntu CD.

Then I continued from the step:

next install subversion which will allow you to retrieve the nightly snapshot of madwifi.

After everything is installed  click on the two computer in the upper right hand corner
(Manual network configuration) and select manual configuration.

you may have to enter password

select wireless connect

uncheck Enable roaming mode

find your network and enter the password if you have one

then enter connection setting
(try automatic)

I am using the default network manager

Thanks again

I hope this helps someone. I was turned off of Ubuntu for a while because of a lack of Wi-Fi support. Now if only I could get my graphics card and my wireless network card to work on my Acer Ferrari.

---

### Post by dredwerker on 2008-03-28
This worked really well with my linksys wmp300n. After hours (days) of using ndiswrapper and crashing and screaming.

I would thank the OP formally for this if I could figure out how :)

O well thanks for sorting this one out and thanks to the madwifi people :)

---

### Post by muckblit on 2008-04-14
I compiled latest svn madwifi.
       
That ath_pci and other ath mods created wifi0 and ath0, which the ubuntu madwifi had not been able to do.

I installed wicd. It says there is no wireless network. No new info there!

I set up /etc/network/interfaces the way you said, and another way by a poster who put all the wpa_supplicant details into /etc/network/interfaces the ath0 section. Same diff, I see wifi0 and ath0k, wifi0 has TX bits, ath0 has none, no scan results. No sign in router of any access attempt. Doesn't matter if I use no security or wpa2. There's a gap somewhere.

Doesn't matter what I do, ath0 never gets an IP or shows any TX or RCV bits. wifi0 does show TX bits. I have a D-Link pcmcia card DWA-642 with AR5416 chip, and router is D-Link DIR-625 also with atheros inside.

______________
grep ath /var/log/messages

Apr 10 23:49:42 vdodds-laptop dhcpcd[6169]: ath0: dhcpcd 3.0.17 starting
Apr 12 15:31:45 vdodds-laptop dhcpcd[8891]: ath0: dhcpcd 3.0.17 starting
Apr 12 16:51:08 vdodds-laptop kernel: [ 6419.524000] ath_hal: module license 'Proprietary' taints kernel.
Apr 12 16:51:08 vdodds-laptop kernel: [ 6419.524000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Apr 12 16:52:31 vdodds-laptop kernel: [ 6502.352000] ath_pci: 0.9.4.5 (0.9.3.2)
Apr 12 16:53:40 vdodds-laptop dhcpcd[9040]: ath0: dhcpcd 3.0.17 starting
Apr 12 17:11:22 vdodds-laptop kernel: [  122.911231] ath_hal: module license 'Proprietary' taints kernel.
Apr 12 17:11:22 vdodds-laptop kernel: [  122.914589] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Apr 12 17:11:22 vdodds-laptop kernel: [  123.071340] ath_pci: 0.9.4.5 (0.9.3.2)
Apr 13 01:25:16 vdodds-laptop kernel: [29766.996000] ath_pci: driver unloaded
Apr 13 01:25:22 vdodds-laptop kernel: [29772.468000] ath_pci: 0.9.4.5 (0.9.3.2)
Apr 13 01:34:55 vdodds-laptop kernel: [30346.044000] ath_pci: driver unloaded
Apr 13 01:35:05 vdodds-laptop kernel: [30355.712000] ath_pci: 0.9.4.5 (0.9.3.2)
Apr 13 01:36:39 vdodds-laptop kernel: [30450.000000] ath_pci: driver unloaded
Apr 13 01:36:45 vdodds-laptop kernel: [30455.772000] ath_pci: 0.9.4.5 (0.9.3.2)
Apr 13 03:42:13 vdodds-laptop kernel: [  123.347615] ath_hal: module license 'Proprietary' taints kernel.
Apr 13 03:42:13 vdodds-laptop kernel: [  123.349117] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
Apr 13 03:42:13 vdodds-laptop kernel: [  123.589551] ath_pci: svn r3538
Apr 13 03:42:13 vdodds-laptop kernel: [  124.024696] MadWifi: ath_attach: HAL managed transmit power control (TPC) disabled.
Apr 13 03:42:13 vdodds-laptop kernel: [  124.024733] MadWifi: ath_attach: Interference mitigation is supported.  Currently disabled.
Apr 13 03:42:13 vdodds-laptop
_____________________
ifconfig

ath0      Link encap:Ethernet  HWaddr 00:1B:11:6D:B8:FD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:264 (264.0 b)  TX bytes:264 (264.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-11-6D-B8-FD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 b)  TX bytes:37352 (36.4 KB)
          Interrupt:11 

__________________

iwlist ath0 scan
ath0      No scan results

_____________________

/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto ath0
#iface ath0 inet dhcp
#wpa-driver madwifi
#wpa-essid dlink
#wpa-ap-scan 2
#wpa-proto RSN
#wpa-pairwise CCMP
#wpa-group CCMP
#wpa-key-mgmt WPA-PSK
#wpa-psk [deleted]

#Wireless
noauto ath0
allow-hotplug ath0

iface ath0 inet manual
wpa-driver madwifi
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

iface default inet dhcp
_________________________________
/etc/wpa_supplicant/wpa_supplicant.conf
update_config=1
# global configuration (shared by all network blocks)
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=netdev
eapol_version=2
ap_scan=1
fast_reauth=1
pkcs11_engine_path=/usr/lib/engines/engine_pkcs11.so

network={
scan_ssid=0
ssid="dlink"
proto=RSN
key_mgmt=WPA-PSK
auth_alg=OPEN
pairwise=CCMP
group=CCMP
psk=[deleted]
proactive_key_caching=1
}


# Wildcard match for SSID (plaintext APs only). This example select any
# open AP regardless of its SSID.
network={
	key_mgmt=NONE
}

---

### Post by muckblit on 2008-04-14
DHCPDISCOVER is transmitted, nothing comes back, dhcpcd times out. TX bits on wifi0, none on ath0

---

### Post by unleadedblues on 2008-04-14
My card is the DWA-552 on 64 bit Ubuntu (Gutsy 2.6.24-12-generic).  I followed your steps and the driver seemed to install without any errors at all.  When I then tried to 'modprobe' the card it returned very quickly and the interface would not show up in ifconfig (with or without the '-a' flag).  Does anyone have any ideas how I can look into this problem further ?

Thanks,
Curt

---

### Post by muckblit on 2008-04-15
unleadedblues, look at your dmesg right after you modprobe ath_pci. See if you have Unrecognized symbols or some complaint. I can load svn madwifi's ath_pci with 2.6.24-16-generic, but with 2.6.24-18 in ubuntu hardy modprobe finds unrecognized symbols but ath_hal loads.

Back to my problem.

ath_hal says it works with chip AR5416. That's what I have in dlink DWA-642 pcmcia card.

Dlink router DIR-625 and pc with card are set up for no security. I also tried wpa2. Router reports a few hundred bits transmitted, no receive. PC reports many bits transmitted on wifi0, none on ath0, and none received. I am sitting with the laptop a few inches from router. Signal -96db, whatever that means.

Here is some dmesg:

[   44.389852] ath_hal: module license 'Proprietary' taints kernel.
[   44.398491] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[   44.594293] wlan: svn r3538
[   44.678215] ath_pci: svn r3538
[   44.678298] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[   44.678314] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   45.109500] MadWifi: ath_attach: HAL managed transmit power control (TPC) disabled.
[   45.109537] MadWifi: ath_attach: Interference mitigation is supported.  Currently disabled.
[   45.170106] cs: IO port probe 0x100-0x3af: clean.
[   45.171343] cs: IO port probe 0x3e0-0x4ff: clean.
[   45.171893] cs: IO port probe 0x820-0x8ff: clean.
[   45.171964] cs: IO port probe 0xc00-0xcf7: clean.
[   45.172621] cs: IO port probe 0xa00-0xaff: clean.
[   45.212877] cs: IO port probe 0x100-0x3af: clean.
[   45.214154] cs: IO port probe 0x3e0-0x4ff: clean.
[   45.214704] cs: IO port probe 0x820-0x8ff: clean.
[   45.214776] cs: IO port probe 0xc00-0xcf7: clean.
[   45.215433] cs: IO port probe 0xa00-0xaff: clean.
[   45.393472] MadWifi: ath_attach: Switching rfkill capability off.
[   45.449404] ath_rate_sample: 1.2 (svn r3538)
[   45.450172] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   45.450180] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   45.450193] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   45.450203] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   45.450214] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
[   45.450216] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
[   45.450219] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
[   45.450222] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
[   45.450225] wifi0: ath_announce: Use hw queue 8 for CAB traffic
[   45.450228] wifi0: ath_announce: Use hw queue 9 for beacons
[   45.501990] ath_pci: wifi0: Atheros 5416: mem=0x3c000000, irq=11
[  187.863083] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  190.069616] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  193.857256] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  196.721576] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  200.301975] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  203.213186] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  205.566019] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  208.438003] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  127.320207] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  129.789049] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  219.800352] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.

---

### Post by unleadedblues on 2008-04-15
muckblit : here is the complete output from dmesg after modprobe ath_pci ,

[ 1722.513296] ath_hal: module license 'Proprietary' taints kernel.
[ 1722.514052] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1722.563626] wlan: 0.9.4
[ 1722.576902] ath_pci: 0.9.4

Is this normal ?  I'm wondering how I can look into this further or is this the end of the line ?

From what I can tell the card is there
lspci | grep Ath
0c:02.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)

---

### Post by muckblit on 2008-04-16
The "taint" warning is normal. ath_hal is a closed or proprietary binary. It will go away with ath5k. madwifi is categorized as legacy now. I don't use git so I'm sticking with madwifi because svn is so easy.

---

### Post by muckblit on 2008-04-16
In my case, bits are transmitted by dlink router and card, but none are received by either. I wonder if my wpa_supplicant and wpa_* are not doing anything. No bits move on ath0, only wifi0, according to ifconfig.

---

### Post by zeesson on 2008-04-18
> **unleadedblues said:**
> My card is the DWA-552 on 64 bit Ubuntu (Gutsy 2.6.24-12-generic).  I followed your steps and the driver seemed to install without any errors at all.  When I then tried to 'modprobe' the card it returned very quickly and the interface would not show up in ifconfig (with or without the '-a' flag).  Does anyone have any ideas how I can look into this problem further ?

Thanks,
Curt

Double check that you edited and saved you interfaces file correctly

---

### Post by zeesson on 2008-04-18
> **muckblit said:**
> In my case, bits are transmitted by dlink router and card, but none are received by either. I wonder if my wpa_supplicant and wpa_* are not doing anything. No bits move on ath0, only wifi0, according to ifconfig.


Follow the steps in the troubleshooting part of the HOWTO for renaming ath0 to wlan0 (trust me this works more ofthen than you would believe, even though I dont know why).  

The line that says **gksudo gedit /etc/udev/rules.d/70-persistent-net.rules**  the 70 might be different on your system so its best to open the etc folder then the udev then the rules.d folder and see what actually precedes  persistent-net.rules in the filename. and then substitute in the command.

---

### Post by muckblit on 2008-04-18
Quote:
Originally Posted by muckblit View Post
In my case, bits are transmitted by dlink router and card, but none are received by either. I wonder if my wpa_supplicant and wpa_* are not doing anything. No bits move on ath0, only wifi0, according to ifconfig.

zeeson replying: Follow the steps in the troubleshooting part of the HOWTO for renaming ath0 to wlan0 (trust me this works more ofthen than you would believe, even though I dont know why).

The line that says gksudo gedit /etc/udev/rules.d/70-persistent-net.rules the 70 might be different on your system so its best to open the etc folder then the udev then the rules.d folder and see what actually precedes persistent-net.rules in the filename. and then substitute in the command.

--

I'll try that as soon as I get to the other pc. Meanwhile, does the following mean that madwifi and/or wpa_supplicant received bits:

Apr 14 16:23:37 vdodds-laptop kernel: [63591.844000] wifi0: FAILEDverification of AR5K_PHY_AGCSIZE_DESIRED default value [found=0xff (-1)expected=0xde (-34)].
Apr 14 16:23:37 vdodds-laptop kernel:[63591.844000]              (unknown):0x9850:0xffffffff:1111111111111111 11111111 11111111:unknown
Apr 14 16:23:37 vdodds-laptopkernel: [63591.844000] wifi0: FAILED verification ofAR5K_PHY_AGCCOARSE_LO default value [found=0xff (-1) expected=0xcc(-52)].
Apr 14 16:23:37 vdodds-laptop kernel:  [63591.844000]            (unknown):0x985c:0xffffffff:11111111 11111111 1111111111111111:unknown
Apr 14 16:23:37 vdodds-laptop kernel:[63591.844000] wifi0: FAILED verification of AR5K_PHY_AGCCOARSE_HIdefault value [found=0x7f (-1) expected=0x6e (-18)].
Apr 14 16:23:37vdodds-laptop kernel: [63591.844000]            (unknown):0x985c:0xffffffff:11111111 11111111 11111111 11111111:unknown
Apr14 16:23:37 vdodds-laptop kernel: [63591.844000] wifi0: FAILEDverification of AR5K_PHY_SIG_FIRPWR default value [found=0xff (-1)expected=0xba (-70)].
Apr 14 16:23:37 vdodds-laptop kernel:[63591.844000]              (unknown):0x9858:0xffffffff:1111111111111111 11111111 11111111:unknown
Apr 14 16:23:37 vdodds-laptopkernel:  [63591.844000] wifi0: FAILED verification ofAR5K_PHY_WEAK_OFDM_LOW_M1 default value [found=0x7f (127) expected=0x32(50)].

That would be the only evidence that either card or router received anything.

---

### Post by muckblit on 2008-04-18
I renamed ath0 to wlan0 in /etc/udev/rules.d/70-persistent-net.rules

I checked /etc/modprobe.d/ for any file with alias ath0 ath_pci

Reboot. dmesg--

[  685.623870] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[ 1146.206863] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  688.942846] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[ 1150.457334] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[ 1152.657349] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[ 1154.937192] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  694.263405] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[  695.613411] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[ 1161.369670] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.
[ 1163.603978] wifi0: ath_rxorn_tasklet: Receive FIFO overrun; resetting.

DHCPDISCOVER bombs and dhclient goes to sleep. I had to manually dhclient wlan0 up, where is the config file to make it run on wlan0?

wicd scan and iwlist wlan0 scan have the usual null results.

---

### Post by muckblit on 2008-04-19
dir-625 dlink router says:

[INFO]	Fri Apr 18 20:09:32 2008	Wireless system with MAC address 001B116DB8FD disconnected for reason: Received Deauthentication.
[INFO]	Fri Apr 18 20:09:32 2008	Wireless system with MAC address 001B116DB8FD associated

---

### Post by dredwerker on 2008-04-23
argggh - this worked swimmingly until I upgraded to hardy.

I get this on the modprobe:

FATAL: Error inserting ath_pci (/lib/modules/2.6.24-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by muckblit on 2008-04-24
"Unrecognized symbol" on modprobe should have been recognized by the package maintainer of madwifi tools, because it shows at compile time.

I saw that last week with last week's svn trunk version of madwifi (ath_*). It's gone now in a later svn version.

-Bob

---

### Post by muckblit on 2008-04-24
Two errors seem like madwifi list topics, but if you know how to fix these or otherwise tweak my /etc/network/interfaces or /etc/wpa_supplicant/wpa_supplicant.conf, help!

Logs show "FIFO overrun" and maybe a register conflict with ath_pci or wlan.ko. They load, they "work", but it seems like not much if any receive is happening with dwa-641 card or dir-625 router, a matched same-gen set from DLink.

---

### Post by muckblit on 2008-04-24
"dwa-641", correction, dwa-642 with chip AR5416, a dlink pcmcia card

---

### Post by dredwerker on 2008-04-24
> **dredwerker said:**
> argggh - this worked swimmingly until I upgraded to hardy.

I get this on the modprobe:

FATAL: Error inserting ath_pci (/lib/modules/2.6.24-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

It appears to be something to do with the latest kernel upgrade. If I choose an older kernel then I can at least see wifi but now I have compiled the latest madwifi trunk, I fear that I may have broken it.

and thanks for this Bob - I will look at the madwifi lists:
> Re: HOW TO: DWA-552 , DWA 556 and other Atheros cards with madwifi 

--------------------------------------------------------------------------------

"Unrecognized symbol" on modprobe should have been recognized by the package maintainer of madwifi tools, because it shows at compile time.

I saw that last week with last week's svn trunk version of madwifi (ath_*). It's gone now in a later svn version.

-Bob

---

### Post by muckblit on 2008-04-24
I have two hardy kernels, and the same one, 2.6.24-16-generic, gave me the trouble with "unresolved symbols". Actually the trouble is in madwifi-tools.

If you dpkg --purge madwifi-tools and the compile the svn madwifi, that will go away. Actually last week svn trunk madwifi did the same thing, but a later svn version works now.

All ubuntu has to do is compile current svn trunk (stable) madwifi.

---

### Post by muckblit on 2008-04-24
...but then I would still have my problem getting svn trunk madwifi to work with dlink dwa-642 pcmcia card!

---

### Post by muckblit on 2008-04-24
dredworker, look for something like "svn r3559" in your log for the wlan module. r3559 or later should be OK on resolving symbols.

ubuntu deb package of madwifi tools might change that naming. That's the naming in the svn source code and it will turn up in logs if you don't change the source.

---

### Post by muckblit on 2008-04-25
wpa_supplicant does not run unless I run it from a term. wlan_ccmp does not load unless I modprobe it. Even then, router does not receive any bits. laptop does id the mac of the router. What else can I do manually beyond loading wpa_succlipunt and wlan_ccmp? wpa2.

---

### Post by johnmac1952 on 2008-04-26
After following the instructions on the first page I got it all to install all the software. Took a little bit of messing around to actually get my Dlink DWA-652 work but work it does !!!!!!! Had to turn off the previously inbedded wireless on this Compaq V2000. Also had to configure the DWA-652 to run as "Roaming" instead of assigning the routers configuration. So far so good !!!!

---

### Post by GuruMadMat on 2008-05-02
I have a question:

does this card run in N mode?
because i'm looking for a pci N network card for ubuntu 8.04.

I also found a Edimax card that could work but not as easy as this!

---

### Post by Beebs on 2008-05-04
I've been following this guide to try and get my D-Link DWA 547 up and running on Hardy. Everything works fine and dandy right up to the point where I do ifup wlan0. I then get the following errors:

```
$ sudo ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:5b:08:d7:89
Sending on   LPF/wlan0/00:19:5b:08:d7:89
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Starting portmap daemon...
 * Already running.
   ...done.
 * Starting NFS common utilities
   ...done.
mount.nfs: internal error
mount.nfs: internal error
mount.nfs: internal error
mount.nfs: internal error
 * Stopping NTP server ntpd
   ...done.

```

Anyone got any ideas on this? I'd really appreciate the help.

---

### Post by cevans on 2008-05-06
> **muckblit said:**
> Two errors seem like madwifi list topics, but if you know how to fix these or otherwise tweak my /etc/network/interfaces or /etc/wpa_supplicant/wpa_supplicant.conf, help!

Logs show "FIFO overrun" and maybe a register conflict with ath_pci or wlan.ko. They load, they "work", but it seems like not much if any receive is happening with dwa-641 card or dir-625 router, a matched same-gen set from DLink.

This madwifi bug discusses the FIFO overrun problem: [http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017).

---

### Post by jotin on 2008-05-10
After restarting, widc no longer detects my dwa-556. I go back through the steps and I receive 

FATAL: Error inserting ath_pci (/lib/modules/2.6.24-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

when I try sudo modprobe ath_pci.

My /sbin/ifconfig does not contain the first entry

ath0 Link encap:Ethernet HWaddr 00:19:7E:41:09:C1
inet addr:192.168.0.102 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:316176 errors:0 dropped:0 overruns:0 frame:0
TX packets:562494 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:54115716 (51.6 MiB) TX bytes:823180275 (785.0 MiB)

---

### Post by mark2741 on 2008-05-28
After 2 separate installs of ubuntu (with a go at Windows XP in-between) in trying to get wireless to work using a D-Link DWA-652 pc card in a Dell D610 I'm happy to say that your instructions worked!

I previously tried everything - numerous madwifi installs/tutorials, ndiswrapper, etc and not a thing. 

I'm still having some problems though - when I reboot I have to go back into the System - Network and then change my password (I'm using WPA Personal) - I just reenter the same password and then click OK and it then reconnects. But without doing that it won't connect automatically after a reboot. I'm going to next try using Wicd as you suggest but hopefully I won't botch up the great progress I've made thanks to you!!!! THANK YOU!

---

### Post by mark2741 on 2008-05-28
Just to follow up to my last remaining problem regarding getting the DLink DWA-652 working flawlessly - problem appears to be solved (I'll report back if I'm prematurely reporting success!). To fix it so that I didn't need to go into Network Manager and reenter my wpa password to reconnect, I did the following:

sudo gedit /etc/network/interfaces

Edited the file so that:

1. commented out the noauto ath0 line
2. Placed auto ath0 just before the iface ath0 inet dhcp line
3. Added this line right after the iface line mentioned above:

pre-up sleep 10

On the surface these lines/edits look redundant to me, but as it stands now, it all works perfectly so I'm not changing a thing : )

Thanks again to the author!

---

### Post by mark2741 on 2008-05-28
I wanted to leave an update to my previous posts regarding the DLink DWA-652. Unfortunately, not good news. I gave up on it and purchased a Netgear WG511T (which works It kept dropping the connection unexpectedly. Sometimes it would be a minute of good connection and then lost, other times it would be 30 minutes straight before dropping. If it were just a dropped connection I would have kept trying to work at getting it working but since the laptop was for my wife and I needed it to 'just work' or else she would have ditched ubuntu without even trying, so I did some searching for a wifi card that would work out of the box. Fortunately, the Netgear WG511T worked without having to do any configuration/setup other than enable the hardware driver per Ubuntu's instructions. I'm using 8.04.

So, a summary of where I got with the DLink DWA-652:

a. Following the directions in this thread's first post, it was able to establish a connection and was *very* fast (in fact, I did a speed test and it clocked in as slightly faster than my wired desktop going through the same router).
b. The lights on it would just flash whether it was working/connected or not. Same for the Netgear card which works flawlessly so far after a day of use.
c. Without warning, the wireless connection would be lost, the lights on the card would go out, and it was as if the card weren't even in the pcmcia slot anymore (even though of course it was). A check of the Network manager would not even show that the card existed. Only way to reestablish the connection/get it to work was to reboot the laptop.
d. None of features of the network icon, when left-clicked, were functioning ever with the dlink card, even when it did have a connection.
e. When it did establish a connection, the DLink card was slightly faster than the Netgear card is. This is expected as the DLink card was wireless N, and also my router is a DLInk PRE-N router, and the Netgear card is just wireless G.

So, thanks, but in the end I had to quit tinkering and I'm happy my local Circuit City had the WG511T on clearance (still for $49 though, which is pricey for a wireless G card). But it works great out of the box in Ubuntu 8.04.

---

### Post by supergenius23 on 2008-05-31
THANKS DUDE! WORKED PERFECTLY! Now im loooking for a good network manager... 

:guitar: rock on

QUESTION: can anyone tell me whats "noauto ath0" mean?

---

### Post by Dragonlaw on 2008-06-02
I got this error when doing "sudo make install"

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-17-generic/build SUBDIRS=/home/justin/madwifi/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  HOSTCC  /home/justin/madwifi/trunk/ath_hal/uudecode
/home/justin/madwifi/trunk/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/justin/madwifi/trunk/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/justin/madwifi/trunk/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/justin/madwifi/trunk/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/justin/madwifi/trunk/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/justin/madwifi/trunk/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/justin/madwifi/trunk/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/justin/madwifi/trunk/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/justin/madwifi/trunk/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/justin/madwifi/trunk/ath_hal/uudecode.c: At top level:
/home/justin/madwifi/trunk/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/justin/madwifi/trunk/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/justin/madwifi/trunk/ath_hal/uudecode.c: In function 'main':
/home/justin/madwifi/trunk/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/justin/madwifi/trunk/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/justin/madwifi/trunk/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/justin/madwifi/trunk/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/justin/madwifi/trunk/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/justin/madwifi/trunk/ath_hal/uudecode] Error 1
make[2]: *** [/home/justin/madwifi/trunk/ath_hal] Error 2
make[1]: *** [_module_/home/justin/madwifi/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [modules] Error 2


What do I do?

---

### Post by Nick Mitin on 2008-06-21
dmesg | grep ath

```
[  400.959414] ath_hal: module license 'Proprietary' taints kernel.
[  400.962394] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  401.014725] wlan: 0.9.4
[  401.040379] ath_pci: 0.9.4

```

OK

lspci | grep Ath
```
02:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
```

OK

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:f9:fd:2a
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fef9:fd2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27706 (27.0 KB)  TX bytes:58155 (56.7 KB)
          Interrupt:23 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)
```

As yo see there is neither ath0 nor wlan0 interface shows up in ifconfig. Anybody knows why?

---

### Post by awwong on 2008-06-21
Thank you for spending time to post this information.  It is very clear and concise.  I used the instructions in the first post with my new D-Link DWA-552 wireless card and it works fine with Linux Mint 4 so far.  I believe it is working in G mode and not N.  The madwifi site seems to be down often as of late, but this morning I was able to successfully connect and complete the setup.

For (newbies like) me, ath0/wlan0 (I changed it to wlan0) does not display/register an inet address until you actually connect to a server/router using the network configuration in the administration application tools.  I spent some time fumbling around wondering why /sbin/ifconfig was not giving me an IP address for my wireless card.  I used the network manager that came with Mint.

---

### Post by awwong on 2008-07-23
Unfortunately I upgraded to Mint 5 R1 and my DWA-552 no longer works, despite a post at the [madwifi compatibility page]("http://madwifi.org/wiki/Compatibility/D-Link").  Perhaps because the reporter's OS was Gentoo; Hardy Heron seems to have broken compatibility.

---

