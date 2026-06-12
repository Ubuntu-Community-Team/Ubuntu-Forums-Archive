---
title: "No Wireless Connection"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by frolickingdp on 2011-07-10
I know this post has been made a million times, but none of the solutions have worked for me, and I know very little about Ubuntu, so I figured I'd get some specific advice on how to get the wireless connection on Ubuntu 11.04 to work. I installed it on a MacBook Pro, but none of the drivers I installed are making the connection work. Thank you for any advice you may have.

---

### Post by matt_symes on 2011-07-10
Hi

Open a terminal and type (case sensitive)

```
sudo lshw -C network
```Enter your password. It will not be echoed to the screen. Post the results back here.

Kind regards

---

### Post by Bucky Ball on 2011-07-10
Welcome. Have you plugged in an ethernet cable and gotten online, gotten updates, then checked System>Administration>Additional Drivers?

If you haven't gotten online with a cable do that, get updates and report back (including the output of Matt_Symes' code, please, if the cable doesn't fix things). ;)

---

### Post by frolickingdp on 2011-07-10
Here's what happened when I typed in the code. I plugged in a cord and it never connected to the internet, so I don't know what that means except that it's really aggravating for me.

*-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 10:9a:dd:6c:54:4c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=57765-v1.37 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:a0600000-a0603fff

---

### Post by josephmills on 2011-07-10
Hi there could we see a ```
lspci -vnn | grep 14e4 
``` also a ```
lsmod
``` and a ```
rfkill list all 
``` thanks

---

### Post by Bucky Ball on 2011-07-11
Okay, this card should work without an issue, but getting online to do it seems to be an issue. Why your ethernet is not working is an issue, too. 

Basically, all you need to do from here is go to System>Administration>Synaptic Package Manager, search for and install:

firmware-b43-installer
b43-fwcutter

... and that card should be up in a jiffy without any of this other screwing around. But, as mentioned, getting online with the ethernet cable seems to be the issue here. Are you running static IP addresses? Is your router set to give you an IP (set as DHCP server)? Could you try switching machine off and restarting with the cable plugged in and see if that gives you any joy?

One last thing, is there anything in System>Admin>Hardware Drivers (or Additional Drivers)? STA driver disabled?

---

### Post by mkamalkayani on 2011-07-11
I have the same problem.I recently installed Ubuntu 11.04 on vmware and was unable to find any wireless connection.I have a dell Inspiron 1564 laptop.My wireless works fine in windows 7
Fllowing are the responses to the commands I entered.Please do help me solve my problem.Thanks.

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:e5:80:d1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical tp 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=vmxnet driverversion=2.0.8.0 duplex=full firmware=N/A ip=192.168.126.132 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 ioport:2000(size=128) memory:dc400000-dc40ffff

kamal@ubuntu:~$ lspci -vnn | grep 14e4
kamal@ubuntu:~$ lsmod
Module                  Size  Used by
usbhid                 41704  0 
hid                    77084  1 usbhid
nls_utf8               12493  1 
isofs                  39571  1 
binfmt_misc            13213  1 
rfcomm                 38125  8 
vmblock                18170  0 
vesafb                 13449  1 
vmsync                 12872  0 
sco                    17779  2 
vmhgfs                 57262  0 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_ens1371            24722  2 
gameport               15027  1 snd_ens1371
snd_ac97_codec        105614  1 snd_ens1371
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13095  0 
snd                    55295  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
vmci                   71332  1 vmhgfs
ppdev                  12849  0 
soundcore              12600  1 snd
snd_page_alloc         14073  1 snd_pcm
parport_pc             32111  1 
shpchp                 32345  0 
vmw_balloon            12729  0 
psmouse                73312  0 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
pcnet32                36760  0 
mptspi                 22323  2 
mptscsih               39170  1 mptspi
vmxnet                 22220  0 
floppy                 60032  0 
mptbase                96634  2 mptspi,mptscsih
scsi_transport_spi     25480  1 mptspi
kamal@ubuntu:~$ rfkill list all
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by westie457 on 2011-07-11
Hi mkamalkayani
There is no output from ```
lspci -vnn | grep 14e4
``` It should look something like this.

graham@graham-Aspire-3690:~$ lspci -vnn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
if you have a Broadcom Wireless chip in your computer. You do not. Please start a new thread to sort out your situation.

---

### Post by westie457 on 2011-07-11
[QUOTEHere's what happened when I typed in the code. I plugged in a cord and it never connected to the internet, so I don't know what that means except that it's really aggravating for me.][/QUOTE]

Go to System > Preferences > Network Connections.
In there select the Wired tab and then select the connection in the list. Click on edit and in this window select the IPv6 Settings tab. In here next to the word method is a box, Click here and change to IGNORE. Also make sure there is a tick in the small box at the top so the connection is available to all users. Click apply. Close the editor. You should now have a wired connection running so josephmills can help ypu properly.

Apologies to all if I have stepped on some toes.

Good luck

---

### Post by Bucky Ball on 2011-07-11
Westie: If OP was online it would be as easy as installing the B43 stuff and this card would be up (if it doesn't automagically come up with an update). Broadcom were the worst headache once, now they're pretty much 'out-of-the-box', thanks to B43, but you need to get online. There should be no need to use a terminal or faff about.

[mkamalkayani]("http://ubuntuforums.org/member.php?u=1337892"), Welcome. Please start a separate thread for your problem rather than asking for help on this one. Already helping the OP here, your issue is NOT exactly the same and it gets confusing working on two separate issues in the one thread. You will get more help in your own thread if you use a descriptive title and give as much info as possible about your problem, machine, and software. ;)

---

### Post by westie457 on 2011-07-11
@ Bucky Ball

> Westie: If OP was online it would be as easy as installing the B43 stuff and this card would be up (if it doesn't automagically come up with an update). Broadcom were the worst headache once, now they're pretty much 'out-of-the-box', thanks to B43, but you need to get online. There should be no need to use a terminal or faff about.

I realise what you are saying is right and was suggesting a way that might have got the OP's wired connection working without causing any hindrance. If my suggestion has helped the OP all well and good. If it did not there was no harm done and we have to come up with something that will work. Thank you for your comments.

Now you may correct me if I am wrong.

The b43-fwcutter package can be installed from a LiveCD as can  bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb.

This will at least get the wired connection working and soon after the wireless as well. Unfortunately I am unsure of the right procedure to do this. Hopefully you or someone else knows the routine and can explain to the OP how to do this.

---

### Post by Bucky Ball on 2011-07-12
Insert CD, add it to software sources (there is an option in there to do that, a tickbox) and try again.

---

### Post by wep940 on 2011-07-12
Yep - on the installation CD.  If I might suggest, just open the CD under "Places" rather than add to the package manager - it will eliminate a bunch of warnings every time you run the package manager in the future but don't have the CD in the drive (unless I've been doing something wrong! ;) )
 
Navigate to the /pool/main/b folder and you should find what you need.
 
There is also a downloadable firmware file (something with "all" in the name - I'll have to look for it) that you can download on another PC then bring to your Ubuntu box.  When using the firmware cutter, I have found this firmware file to be a great help as sometimes even with everything else installed it will still say the firmware is missing.  That firmware file gets rid of that problem.
 
Maybe BuckyBall knows the file I'm referring to and get you a link.  I'll go looking for it myself and post back when I find it.
 
Keep in mind that it will need to be downloaded, which means you'll need to use a computer with internet access then move it to your Ubuntu machine with a USB flash drive or perhaps a CD.

---

### Post by westie457 on 2011-07-12
Hi the link is here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

And here is the bit with the install from CD instructions
> b43 - No Internet access
If you do not have any other means of Internet access on your computer, you will have to install b43-fwcutter and patch packages from the install media. After that you will need to setup firmware manually (without the firmware automatically downloading and being set up).

Setp 1.

b43-fwcutter is located on the Ubuntu install media under ../pool/main/b/b43-fwcutter/ and patch is located under ../pool/main/p/patch/ or both in the official repositories online.

Double click on the package to install or in a terminal (under the desktop menu Applications > Accessories > Terminal) navigate to the folder containing the package and issue the following command:


:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
Step 2.

On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Step 3.

Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware:


~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
Step 4.

Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use.

Note: A computer restart may be required before using the wifi card.

LiveCD/LiveUSB
Note: The install media contents are mounted under /cdrom of the filesystem.

Step 5.

For temporary use with the LiveCD and LiveUSB environments, instead of a computer restart, in a terminal issue the following commands:


~$ sudo modprobe -r b43 ssb
~$ sudo modprobe b43
Note: Allow several seconds for the network manager to scan for available networks before attempting a connection.



---

### Post by wep940 on 2011-07-12
Good job!  I will add to it by mentioning again that for me, even after doing everything explained above, I still got the "firmware missing" message.  After some research I found I needed the "all" firmware found in the following link:
 
[http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 
It may not be needed with your adapter.  Mine is a Broadcom 4306 for my laptop.

---

