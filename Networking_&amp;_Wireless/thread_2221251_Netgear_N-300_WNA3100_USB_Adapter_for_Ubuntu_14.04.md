---
title: "Netgear N-300/ WNA3100 USB Adapter for Ubuntu 14.04"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by tomash66 on 2014-05-01
I Have a dell optiplex 755 and it has XP im trying to upgrade to Ubuntu  14.04 32 bit. I have been using a distro and have not completely  installed because I can not get the Wifi to work what so ever and this  is a deal breaker even though I like everything else. I am using a  netgear router/modem and a netgear usb adapter to pick up wifi. I am  very new to linux all together and I am very slow with it currently but I  have spent hours on this issue and nothing has helped, please help me.                 the dongle is a wireless N-300 and model number is WNA3100 and I dont not know where I would find the chipset info?

---

### Post by praseodym on 2014-05-01
Please check
```

lsusb
```

---

### Post by tomash66 on 2014-05-01
I am new an I assume you mean press Ctrl+Alt+T and then enter lusb and press enter if so this is what I got:

ubuntu@ubuntu:~$ lsusb
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 002: ID 03f0:5307 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$

---

### Post by praseodym on 2014-05-01
Right, well done:

```
 Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```
Thats the one. Broadcom-USB-sticks only work with ndiswrapper and the corresponding windows driver:

Install it via:
```

sudo apt-get install ndisgtk ndiswrapper-dkms dkms linux-headers-generic build-essential
```
The driver can be found here:
[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)
Unpack it and install the respective *.INF file via the "Windows-WLAN-tool"

---

### Post by tomash66 on 2014-05-01
I used your code and downloaded the link but what is the windows-wlan-tool?

---

### Post by praseodym on 2014-05-01
Search for WLAN in the "dash".

---

### Post by tomash66 on 2014-05-01
I know being such a newbie I am a pain but I assume the place your suggesting I search is the top left hand corner button and when I click it and search for WLAN nothing pops up for that do I need to download this tool in the software center?

---

### Post by praseodym on 2014-05-01
You can also install the driver via terminal. Unpack the driver to "Downloads" and run

For 32bit:

```
sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
```

For 64bit:

```
sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
```

Load the driver:
```

sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
dmesg | grep ndis
lsmod
iwconfig
ndiswrapper -l # thats a small L

```

---

### Post by tomash66 on 2014-05-05
Thank you you are a UBUNTU Genius and your help was much appreciated

---

### Post by Shawn_Pitman on 2014-05-24
Just joined to say thanks for this, also. Same problem, same solution.

Long time amateur Ubuntu user.

---

### Post by jalen3 on 2014-05-24
Hey, I was just posting because I have the same exact problem, but when I followed the steps and nothing has worked. I have been researching the problem for about five hours now with no success.

---

### Post by melissadick17 on 2014-06-11
OMG...Thank you so much, I have been working on this for two days and you totally solved it. :P

---

### Post by Robert_Kupfner on 2014-07-19
> **jalen3 said:**
> Hey, I was just posting because I have the same exact problem, but when I followed the steps and nothing has worked. I have been researching the problem for about five hours now with no success. Check Praiseodym's post as his will get you set up all you have to make sure you do is download the file and extract it to your downloads and copy and paste what he put down. make sure on the last part to not copy and paste the later half saying it's a captal L though.

---

### Post by Hexxus on 2014-09-22
> **praseodym said:**
> You can also install the driver via terminal. Unpack the driver to "Downloads" and run

For 32bit:

```
sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
```

For 64bit:

```
sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
```

Load the driver:
```

sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
dmesg | grep ndis
lsmod
iwconfig
ndiswrapper -l # thats a small L

```


THANK YOU SO MUCH!!!

I was struggling with this for over a day trying to get ndiswrapper to work for me.

---

### Post by Enate60 on 2014-10-27
Hello! Like others above, I've joined just to thank Praseodym for this solution, and Tomash66 for asking the right question, so that I've got myself up and running with Ubuntu in two evenings. What a helpful and knowledgeable community - many thanks again

---

### Post by the_nuts on 2014-10-28
> **praseodym said:**
> 
Install it via:
```

sudo apt-get install ndisgtk ndiswrapper-dkms dkms linux-headers-generic build-essential
```


How am I supposed to do it if I don't have the drivers to connect to the internet? 

lol they told me "leave Windows and switch to Linux, it's simple and easy..."

---

### Post by praseodym on 2014-10-28
Download the respective DEB files from [http://packages.ubuntu.com](http://packages.ubuntu.com) (except "build-essential"), save them in "Downloads" and install them via:
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by kurt18947 on 2014-10-28
> **the_nuts said:**
> How am I supposed to do it if I don't have the drivers to connect to the internet? 

lol they told me "leave Windows and switch to Linux, it's simple and easy..."

Catch 22, isn't it?  I use two options in addition to praseodym's good solutions.  If you have a laptop, can you get a one-time ethernet cable connection to install wireless drivers?  If not and wireless is the only option, I have a couple USB dongles that have been plug 'n' play for a couple years at least. One is Trendnet's TEW-649UB using RealTek's RTL8192**SU **chipset. Use caution here, RTL8192**CU** seems much more common but needs a tweaked proprietary RealTekdriver to work reliably. The second good choice IME is Netgear's WNA1100 using an Atheros AR9271 chipset. There is a third choice but it's pretty slow(G speed) and ugly, Trendnet TEW-424UB (ver.2 or better)  but plug it in and it works -- every time since 9.04 in my experience.  I keep that old Realtek for situations such as yours, I need a one time connection to download driver software/firmware.

---

### Post by Ben_Shaver on 2015-04-02
Like the others who have posted above this comment, I'm here to thank praseodym for his very detailed and in-depth guide that helped me get internet access on many a computer. (Thanks!)

---

### Post by Stormdancer on 2015-06-12
[COLOR=#000000][FONT=verdana]Unfortunately, I'm having a very similar problem. I've spent quite a lot of time trying to work it out, but to no avail. 

[/FONT][/COLOR][FONT=verdana][COLOR=#000000][FONT=verdana]While I've used linux a fair amount, I still count myself a nub, especially when it comes to drivers & such.
[/FONT][/COLOR][/FONT]
[FONT=verdana][COLOR=#000000][FONT=verdana]I've done some googling on this product, and got the NDIS wrapper installed, downloaded the appropriate driver from this thread, installed said driver, and it appears to be basically in place.[/FONT][/COLOR][/FONT]
[FONT=verdana][COLOR=#000000][FONT=verdana]
However... I can't find any way to actually USE it. It doesn't light up when plugged in, and I see no way in the 'System Settings/Network' to add/configure it.
[/FONT][/COLOR][/FONT]
[FONT=verdana][COLOR=#000000][FONT=verdana]**ndiswrapper -l** replies[/FONT][/COLOR][/FONT]
[COLOR=#000000][FONT=courier new]  bcmn43xx64 : driver installed

[/FONT][/COLOR][FONT=verdana][COLOR=#000000][FONT=verdana]However, **lsusb** shows only (other stuff filtered out)[/FONT][/COLOR][/FONT]
[COLOR=#000000][FONT=courier new] Bus 001 Device 007: ID 0846:9014 NetGear, Inc. 

[/FONT][/COLOR][FONT=verdana][COLOR=#000000][FONT=verdana]and **iwconfig** shows[/FONT][/COLOR][/FONT]
[COLOR=#000000][FONT=courier new]eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

[FONT=verdana]And **dmesg | grep ndis** gives me this output[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=courier new][  577.080168] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new][  577.082639] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new][  577.165071] usbcore: registered new interface driver ndiswrapper[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]
[/FONT][/COLOR]
[FONT=verdana][COLOR=#000000][FONT=verdana]Any ideas? What am I missing? I did reboot after installing the drivers.[/FONT][/COLOR][/FONT]

---

### Post by chili555 on 2015-06-12
> **Stormdancer said:**
> [COLOR=#000000][FONT=verdana]Unfortunately, I'm having a very similar problem. I've spent quite a lot of time trying to work it out, but to no avail. 

[/FONT][/COLOR][FONT=verdana][COLOR=#000000][FONT=verdana]While I've used linux a fair amount, I still count myself a nub, especially when it comes to drivers & such.
[/FONT][/COLOR][/FONT]
[FONT=verdana][COLOR=#000000][FONT=verdana]I've done some googling on this product, and got the NDIS wrapper installed, downloaded the appropriate driver from this thread, installed said driver, and it appears to be basically in place.[/FONT][/COLOR][/FONT]
[FONT=verdana][COLOR=#000000][FONT=verdana]
However... I can't find any way to actually USE it. It doesn't light up when plugged in, and I see no way in the 'System Settings/Network' to add/configure it.
[/FONT][/COLOR][/FONT]
[FONT=verdana][COLOR=#000000][FONT=verdana]**ndiswrapper -l** replies[/FONT][/COLOR][/FONT]
[COLOR=#000000][FONT=courier new]  bcmn43xx64 : driver installed

[/FONT][/COLOR][FONT=verdana][COLOR=#000000][FONT=verdana]However, **lsusb** shows only (other stuff filtered out)[/FONT][/COLOR][/FONT]
[COLOR=#000000][FONT=courier new] Bus 001 Device 007: ID [COLOR="#FF0000"]**0846:9014**[/COLOR] NetGear, Inc. 

[/FONT][/COLOR][FONT=verdana][COLOR=#000000][FONT=verdana]and **iwconfig** shows[/FONT][/COLOR][/FONT]
[COLOR=#000000][FONT=courier new]eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

[FONT=verdana]And **dmesg | grep ndis** gives me this output[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=courier new][  577.080168] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new][  577.082639] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new][  577.165071] usbcore: registered new interface driver ndiswrapper[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]
[/FONT][/COLOR]
[FONT=verdana][COLOR=#000000][FONT=verdana]Any ideas? What am I missing? I did reboot after installing the drivers.[/FONT][/COLOR][/FONT]The driver in this thread is for v2 of the device; you have v3. v2 is a Broadcom chipset; yours is a Mediatek. This page suggests it's an MT7632U: [https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)

At this time, I know of no way to get the device working. If you can find Windows XP 64-bit driver files, that is .inf and .sys, we can try ndiswrapper again.

---

### Post by praseodym on 2015-06-13
Try changing the router settings to b/g mode

---

### Post by leonardo22 on 2015-06-18
[B]> **tomash66 said:**
> I am new an I assume you mean press Ctrl+Alt+T and then enter lusb and press enter if so this is what I got:

ubuntu@ubuntu:~$ lsusb
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 002: ID 03f0:5307 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$[/B]
________________________________________________________________________________________________________________________________________


What does it mean if I type 
lsusb 
and I get this

Bus 001 Device 004: ID 0846:9020 NetGear, Inc.  
instead of

Bus 001 Device 004: ID 0846:9020 NetGear, Inc. [COLOR=#ff8c00]WNA3100(v1) Wireless-N 300 [Broadcom BCM43231][/COLOR]

---

### Post by chili555 on 2015-06-18
> **leonardo22 said:**
> ****
________________________________________________________________________________________________________________________________________


What does it mean if I type 
lsusb 
and I get this

Bus 001 Device 004: ID 0846:9020 NetGear, Inc.  
instead of

Bus 001 Device 004: ID 0846:9020 NetGear, Inc. [COLOR=#ff8c00]WNA3100(v1) Wireless-N 300 [Broadcom BCM43231][/COLOR]It means nothing; it is the same 0846:9020 device. I suggest you check here: [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

---

### Post by kylesmail80 on 2015-06-30
How do I install the driver via a flashdrive? I put the driver on a flashdrive and put it in my dektop (the one without internet) extracted the tar and did your code but it doesn't recognize the "ndiswrapper" command. Is this because I didn't install it directly to the desktop? because I can't really do that without internet.

---

### Post by jeremy31 on 2015-06-30
> **leonardo22 said:**
> 
________________________________________________________________________________________________________________________________________


What does it mean if I type 
lsusb 
and I get this

Bus 001 Device 004: ID 0846:9020 NetGear, Inc.  
instead of

Bus 001 Device 004: ID 0846:9020 NetGear, Inc. [COLOR=#ff8c00]WNA3100(v1) Wireless-N 300 [Broadcom BCM43231][/COLOR]

That description should change after ```
sudo update-usbids
```  It won't make the wifi work any better

---

### Post by chili555 on 2015-06-30
> **kylesmail80 said:**
> How do I install the driver via a flashdrive? I put the driver on a flashdrive and put it in my dektop (the one without internet) extracted the tar and did your code but it doesn't recognize the "ndiswrapper" command. Is this because I didn't install it directly to the desktop? because I can't really do that without internet.Please start a new thread and include:```
lsusb
lsb_release -a
```Also, please tell us what, exactly, you downloaded and extracted.

Thanks.

---

### Post by amax6416 on 2015-07-01
Okay, so I've been messing around with this for about the past 3-4 hours now and I just want to get it fixed. 
I think what my problem is, is that I've installed over the driver a few too many times. Now I have all these random ones that aren't working and I can't figure out how to uninstall them 


lsusb 

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1532:011a Razer USA, Ltd 
Bus 004 Device 002: ID 1532:0040 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 008 Device 004: ID 18d1:4ee4 Google Inc. Nexus 4 (debug + tether)
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

(Yes I am currently tethering with my phone so I can access the internet is that causing issues? I couldn't imagine it is.)


lsb_release -a 

No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 17.2 Rafaela
Release:    17.2
Codename:    rafaela


when I run the 'ndiswrapper -l' I get this
bcmn43xx32 : driver installed
    device (0846:9020) present
bcmn43xx64 : invalid driver!
bcmwlhigh5 : invalid driver!
bcmwlhigh6 : invalid driver!


as I said I know I've installed ones that are incorrect. I thought it was supposed to be something like this to uninstall: 
sudo ndiswrapper -r bcmwlhigh6  etc,etc with all the other ones but it returns this

couldn't delete /etc/ndiswrapper/bcmwlhigh6.inf: No such file or directory

iwconfig returns

eth0      no wireless extensions.


usb0      no wireless extensions.


lo        no wireless extensions.

---

### Post by chili555 on 2015-07-01
> I thought it was supposed to be something like this to uninstall: 
sudo ndiswrapper -r bcmwlhigh6 etc,etcPlease try:```
sudo ndiswrapper -e bcmwlhigh6
```e for erase.

Then load ndiswrapper:```
sudo modprobe ndiswrapper
```And check the log:```
dmesg | grep ndis
```

---

### Post by darthCore on 2015-07-15
Hello All. I am very new to linux/ubuntu. I am having trouble getting my netgear wna3100 to work. I believe i have already installed ndiswrapper. But I still get the following error when i try to run the inf file from terminal.

What I put in: 

   sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf

error:

```
darthcore@WerkPC:~$ sudo modprobe ndiswrapper
darthcore@WerkPC:~$ sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
couldn't open /home/darthcore/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 162.


```

---

### Post by chili555 on 2015-07-15
> **darthCore said:**
> Hello All. I am very new to linux/ubuntu. I am having trouble getting my netgear wna3100 to work. I believe i have already installed ndiswrapper. But I still get the following error when i try to run the inf file from terminal.

What I put in: 

   sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf

error:

```
darthcore@WerkPC:~$ sudo modprobe ndiswrapper
darthcore@WerkPC:~$ sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
couldn't open /home/darthcore/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 162.


```Is the file actually there?```
cd ~/Downloads && ls
```One of the folders you should find is Broadcom_bcm43xx_USB_32_64bit_v2. Is it there? If so, navigate to that folder:```
cd Broadcom_bcm43xx_USB_32_64bit_v2
```List the contents:```
ls
```Now do you see the needed .inf files? If so, install it:```
sudo ndiswrapper -i bcmn43xx64.inf
sudo modprobe ndiswrapper
```Any errors, problems, complaints, etc.?

---

### Post by darthCore on 2015-07-16
Gotcha, thank you. I am now getting the message "driver bcmn43xx64 is already installed" . and When i type in "sudo modprobe ndiswrapper", nothing happens.. I am not able to open ndiswrapper. I am running Ubuntu 15.04 . On the top right corner I am able to see wifi networks. but after I enter my password, it just asks for my password again.. doesnt provide any error message.

I was able to open the GUI using the command "   sudo ndisgtk

But when I enter my network password, the same box comes back up saying to enter the network pw again. I am positive that I am entering the correct network key.

---

### Post by chili555 on 2015-07-16
Let's check some diagnostics:```
ndiswrapper -l
dmesg | grep ndis
```That's a lower-case L for 'list;' not a numeral one.

---

### Post by darthCore on 2015-07-16
this is what i get

```
darthcore@WerkPC:~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9020) present
darthcore@WerkPC:~$ dmesg | grep ndis
darthcore@WerkPC:~$ 


```

looks like it outputs nothing when i enter "dmesg | grep ndis"

---

### Post by chili555 on 2015-07-16
Weird! Let's try to provoke some meaningful messages:```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by darthCore on 2015-07-16
```
darthcore@WerkPC:~$ sudo modprobe -r ndiswrapper
[sudo] password for darthcore: 
darthcore@WerkPC:~$ sudo modprobe ndiswrapper
darthcore@WerkPC:~$ dmesg | grep ndis
[  131.128622] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  131.130451] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  132.589208] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  132.839451] usbcore: registered new interface driver ndiswrapper
darthcore@WerkPC:~$ 


```

---

### Post by chili555 on 2015-07-17
That looks perfect. I gather that it creates a wireless interface, ideally wlan0 and offers to connect but doesn't. May I see:```
sudo iwlist wlan0 scan
```Please omit all the access points but yours and then obscure the MAC address like this:> Cell 01 - Address:[COLOR="#FF0000"] XX:D7:19:41:54:XX[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bcf610e66
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A2C1917FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500000000000040
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057200010000
Some wireless drivers don't like TKIP and there may be a few other changes we can make to help.

---

### Post by darthCore on 2015-07-17
Everytime I boot up i need to enter this in order to see wireless networks

```
sudo modprobe -v ndiswrappersudo ndiswrapper -ma
dmesg | grep ndis
lsmod
iwconfig
ndiswrapper -l
```

I tried another Troubleshooting step. I turned off security for my network. I was able to connect wirelessly, but could not browse to any webpages. Im thinking about just investing in a ubuntu compatable wireless network adapter.

@chili555 im at work now, but ill do what you said on my lunch break.

---

### Post by zander2 on 2015-07-20
I tried this solution as well, and found that it did not work for me. While the drivers installed correctly, iwconfig returned

```
eth0      no wireless extensions.

lo        no wireless extensions.
```

dmes | grep ndis returned

```
[14323.727637] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[14323.795385] usbcore: registered new interface driver ndiswrapper

```

I followed all the instructions in this thread, and many others in an attempt to get this up and running. I have Ubuntu desktop 15.04, which may be why the solution for 14.04 isn't cutting it for me. :P Any ideas? Thanks in advance.

Extra info:

lsusb returns

```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03eb:2104 Atmel Corp. AVR ISP mkII
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 002: ID 14cd:6500 Super Top 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1532:010b Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and 

ndiswrapper -l says that the driver is installed.

```
bcmn43xx64 : driver installed
```

---

### Post by chili555 on 2015-07-20
> ndiswrapper -l says that the driver is installed.

Code:
bcmn43xx64 : driver installedHowever, it doesn't say the all important, 'device present.' That means either that the device wasn't inserted in the USB slot while you are trying to get the wireless working (!!) or, more likely, that the driver file you installed, bcmn43xx64.inf, doesn't cover your device:> [COLOR="#FF0000"]0846:9011[/COLOR] NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]The copy I have on my system clearly does cover it:```
[Manufacturer]
%Broadcom% = Broadcom

[Broadcom]
%BCM4xx01_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_825C
%BCM4xx02_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_6050
%BCM4xx04_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_615A
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_[COLOR="#FF0000"]0846[/COLOR]&PID_[COLOR="#FF0000"]9011[/COLOR]
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_0846&PID_9020

```Where did you get the files you installed? Link and post number, please.

---

### Post by zander2 on 2015-07-20
The device is certainly in one of my ports. Just to make sure the port wasn't faulty, I ran lsusb, which returned


```
Bus 001 Device 007: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]


```

so alas it isn't that simple of a fix. :P


I got the drivers from post #6 on [http://ubuntuforums.org/showthread.php?t=1964173&highlight=netgear+wnda](http://ubuntuforums.org/showthread.php?t=1964173&highlight=netgear+wnda) 

One of your posts actually. :D You have helped a lot of people my friend. :P

---

### Post by chili555 on 2015-07-20
> One of your posts actually.Oh, that old thing??

It certainly ought to work. May we see:```
arch
ls /etc/ndiswrapper
cat /var/log/syslog | grep ndis | tail -n20
```Thanks.

---

### Post by zander2 on 2015-07-20
arch returns

```
x86_64
```

ls /etc/ndiswrapper returns

```
bcmn43xx64
```

cat /var/log/syslog | grep ndis | tail -n20 returns

```
Jul 20 11:43:57 CORA kernel: [14323.727637] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
Jul 20 11:43:57 CORA kernel: [14323.795385] usbcore: registered new interface driver ndiswrapper

```

How does that last command work? I am familiar with grep ndis, but I don't know what it does, and I have not come across the other two bits of that command.

edit: Still no connection. Was that last command supposed to fix the issue?

---

### Post by zander2 on 2015-07-23
Sorry to bump, but I haven't figured out how to resolve the issue. :/

---

### Post by lukes2 on 2015-08-02
Can I please be linked to this post he made (if he did so)? I'm having this same problem. The desktop I got doesn't have internet access (I'm posting from my laptop). I plug a flashdrive in, but I'm getting the same "ndiswrapper: command not found" thingy. Thanks!

---

### Post by brian-mccumber on 2015-08-27
Oh wow, I have been struggling with this for a couple days too now. I finally got it to work with these steps after bricking a router trying to bridge it.

1. I shared my ethernet connection from my laptop which had wireless working out of the box with Ubuntu. 
2. I connected the ethernet ports from my desktop to my laptop, and verified that I was getting connection to my desktop after selecting the shared connection from my laptop.
3. I opened the terminal on my desktop and sudo apt-get install ndiswrapper-common, ndiswrapper-dkms, apparently utils are bundled with dkms now.
4. Then I installed ndisgtk from the software center where it is labeled as Windows Wireless Drivers. I then could NOT find it in installed programs.
5. Opened terminal and started ndisgtk by typing sudo ndisgtk, then navigated to my desktop with Windows Wireless Drivers gui where I had the appropriate broadcom windows drivers unpacked and selected the .inf for my systems architecture and then the netgear usb adapter started working. 

This is only after I have tried alot of various things that did not work from the large number of posts about this subject. I don't know if this will help but if it does then great! I actually had it so buggered up once from trying things that I had to reinstall Ubuntu. And this is for the netgear 3100 usb adapter..

---

### Post by Jim_Ormsby on 2015-12-13
Hi
I just found this thread and am trying to use it.  I'm not heavily experienced with Ubuntu.  Yet....
I have just loaded ubuntu 15.10, and have added nothing to it except having tried to load and use an Edimax ew7811un, which works nicely for about 5 minutes.  I was unable to get it to function properly so I am trying to install an N300 which I have on hand.  An N300 is running on a separate Window 8.1 computer (which I am using to access this website). 


What should I be looking for in the results of the lsmod command?
I'm not sure the ndiswrapper -ma command worked properly.
The dmesg | grep ndis command yielded possible errors:
 
   ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
   nsidwrapper version 1.59 loaded (smp=yes, preempt=no)
   usbcore: registered new interface driver ndiswrapper

iwconfig yields:
   enp4s0   no wireless extensions
   lo          no wireless extensions

ndiswrapper -l   yields nothing

Thanks for any help.

---

### Post by chili555 on 2015-12-14
> What should I be looking for in the results of the lsmod command?You should see the module ndiswrapper loaded. If not, load it:```
sudo modprobe ndiswrapper
```> The dmesg | grep ndis command yielded possible errors:

ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
nsidwrapper version 1.59 loaded (smp=yes, preempt=no)
usbcore: registered new interface driver ndiswrapper
Those are not errors that prevent the driver and hardware from working. > ndiswrapper -l yields nothingEven after you modprobed the ndiswrapper module? If so, we'll start at the beginning and find out why.

---

### Post by kurt18947 on 2015-12-14
> **Jim_Ormsby said:**
> Hi
I just found this thread and am trying to use it.  I'm not heavily experienced with Ubuntu.  Yet....
I have just loaded ubuntu 15.10, and have added nothing to it e**xcept having tried to load and use an Edimax ew7811un, which works nicely for about 5 minutes.**  I was unable to get it to function properly so I am trying to install an N300 which I have on hand.  An N300 is running on a separate Window 8.1 computer (which I am using to access this website). 


What should I be looking for in the results of the lsmod command?
I'm not sure the ndiswrapper -ma command worked properly.
The dmesg | grep ndis command yielded possible errors:
 
   ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
   nsidwrapper version 1.59 loaded (smp=yes, preempt=no)
   usbcore: registered new interface driver ndiswrapper

iwconfig yields:
   enp4s0   no wireless extensions
   lo          no wireless extensions

ndiswrapper -l   yields nothing

Thanks for any help.

That's pretty typical of the Edimax adapter. The default driver is faulty. There is a pretty simple and effective fix here:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

From an account with sudo privileges, open a terminal and copy/paste each line one at a time under the **installation** header and press 'enter'. It uses dkms so there's no need to manually rebuild after image updates.

I'm of no help with the Netgear/NDISwrapper stuff. Chili555 is an expert there.

---

### Post by Jim_Ormsby on 2015-12-14
ndiswrapper -l still yields nothing.

With some embarrasment, I realized that I only saw the first page of this thread, and missed all the stuff about versions before I started.  My N300 device shows up as version 1, and I am attempting to use version 2 downloads.  While this may be a problem, it seems that ndiswrapper -l should still show something.
An added thing: I downloaded the software into "Downloads", but then put it in a subdirectory to keep things simple (?) before untarring and unzipping it.  That wouldn't be a problem, would it?  Can that long download file name be changed to something short so I don't keep fatfingering it when I type it in?

Chili, weren't you one of those trying to help me in the last few days with getting and Edimax 7811 to work?  If so, thanks again.  I just happen to have the spare N300 on hand.

---

### Post by chili555 on 2015-12-14
> My N300 device shows up as version 1, and I am attempting to use version 2 downloads.
 ....
That wouldn't be a problem, would it? Using the wrong driver for the wrong device? Absolutely.

Let's start at the beginning.```
lsusb
```

---

### Post by Jim_Ormsby on 2015-12-15
Sorry for the slow response.  Western WY; had to deal with snow and get the firewood.

lsusb lists this as the item of interest:
Bus 009 Device 003: ID 0846:9020 NetyBear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

Now that I know there are versions, even a low experience person like me can see this is a version 1 device, and that I have to load that version of the software instead of version 2, which is what I did.
Is it as simple as using the ndiswrapper command  "...32_64bit_v1.." instead of "v2"

---

### Post by chili555 on 2015-12-15
> Is it as simple as using the ndiswrapper command "...32_64bit_v1.." instead of "v2"Not exactly. The v1 vs. v2 came about a few years back when ole Chili was busy messing (editing!) with the Windows .inf files. The first version I tried crashed and the second version seems to work.

I suggest you try the v2 files and install the .inf appropriate to your architecture; either 32- or 64-bit. Find out:```
arch
```Do you need more explicit details?

[http://ubuntuforums.org/showthread.php?t=2221251&p=13010118#post13010118](http://ubuntuforums.org/showthread.php?t=2221251&p=13010118#post13010118)

---

### Post by Jim_Ormsby on 2015-12-15
arch give me "x86_64"  which confirms a 64 bit system

I had gone through the process already, and all seemed OK until I got this:
ndiswrapper -l    gave me nothing on the output. 
So I assume something went wrong.
One place I deviated was when I downloaded the package into the Download directory.  I made a subdirectory and put the package in there, and THEN executed the unzip, etc.  Is there some part of the process that assumes no subdirectory.

---

### Post by chili555 on 2015-12-15
> ndiswrapper -l gave me nothing on the output. 
So I assume something went wrong.So it seems.> One place I deviated was when I downloaded the package into the Download directory. I made a subdirectory and put the package in there, and THEN executed the unzip, etc. Is there some part of the process that assumes no subdirectory.You need to direct the process to the exact location of the inf and sys files; something like:```
sudo ndiswrapper -i ~/Downloads/[COLOR="#FF0000"]subdirectory[/COLOR]/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
```Of course, substitute the actual name you chose for the subdirectory. Then check:```
ndiswrapper -l
```It ought to report the driver bcmn43xx64 installed and the device 0846:9020 present.

---

### Post by Jim_Ormsby on 2015-12-16
OK, I seem to have buggered things up, so I started from scratch.  I reloaded the OS and followed the instructions withOUT any funny directories, etc.

modprobe -v ndiswrapper   returned   insmod /lib/modules/4.2.0-16-generic/updates/dkms/ndiswrapper.ko
lsmod                            returned  among other things:  ndiswrapper   286720  0
iwconfig  returned  

enxe 0469aa349eb  IEEE 802.11g  ESSID:  off/any
Mode: Managed  Frequency:2.412 GHz  Access POint: Not-Associated
Bit Rate:300Mb/s  Tx-Power: 32dBm
RTS thr:2347 B  Fragment thr:2346 B
Power Management: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx inflaic frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0


ndiswrapper -l   returned   bcmn43xx64  driver installed    device (0846:9020_ present)

So it seems to me everything is installed, but I get no blue light on the device, and it doesn't show up in the wireless tool in the upper right corner of the workspace.

I used the wireless tool to "Add" the wireless network, using the name that my other computer (this one) uses.  I entered router name, but there isn't a place for the password.
I think I'm close.....
Reboot????

Thanks,
Jim

---

### Post by chili555 on 2015-12-16
> ndiswrapper -l returned bcmn43xx64 driver installed device (0846:9020_ present)
  Perfect.> [COLOR="#FF0000"]enxe 0469aa349eb[/COLOR] IEEE 802.11g ESSID: off/any
Mode: Managed Frequency:2.412 GHz Access POint: Not-Associated
Bit Rate:300Mb/s Tx-Power: 32dBm
RTS thr:2347 B Fragment thr:2346 B
Power Management: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx inflaic frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0  Please check this. I don't believe there is a space in the interface name. 

In any event, Let's check the log:```
dmesg | grep -e ndis -e enxe
```Does it scan?```
sudo iwlist scan
```It actually looks pretty hopeful so far.

---

### Post by Jim_Ormsby on 2015-12-16
You are correct--there is no space.  I hand typed it in from the linux computer to this one.

The dmesg command returned:
[number]  ndiswrapper: module verification failed: signature and/or required key missing - tainted kernel
[number]  ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[number]  ndiswrapper: driver bcmn43xx64 (,08,26,2009, 5.10.79.30) loaded
[number]  usbcore: registered new interface driver ndiswrapper
[number]  ndiswrapper 9-4:1.0 enxe0469aa349eb: renamed from wlan0
[number]  ndiswrapper: interface renamed to 'enxe0469aa349eb'

The iwlist scan command returned lots of data about the device.  There were two others, "enp4s0' and 'lo' that don't support scanning.
The device of interest (enxe0469aa349eb) does have a MAC address and an ESSID that I put in using the wireless tool.
If I'm lucky you don't need me to type in all that stuff!  (But I will if it helps...)
Thanks,
Jim

---

### Post by chili555 on 2015-12-16
> The iwlist scan command returned lots of data about the device. The names of networks it sees?> Cell 04 - Address: xx:1F:A1:39:4C:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"MY_Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b97fb93154
...and so forth?

If it scans, Network Manager should see it and connect.

Your *dmesg* readings appear entirely normal.

---

### Post by Jim_Ormsby on 2015-12-16
Device (enxe0469aa349eb) which is the N300, sees ESSID: "Silverstar.23331"  I believe that is what you are asking.

As for the rest:
Cell 01 - Address: A0:E4:CB:75:F9:36
I don't see a channel
Frequency: 2.412GHz (Channel 1)
Quality:84/100  signal level:-42 dBm Noise level:-96 dBm
Encryption key: on
Bit rates match yours for one line; but I dont't have the second bit rate line
Mode:Master
Extra: bcn_int=100
Extra atim=0
There are 15 lines of "IE:" with gobs of digital characters after them.

I take it that by "Network Manager" you mean an installable GUI package, yes?
Shouldn't I just be able to use the wireless tool?  But I don't see a place to put in a router password.

Thanks,
Jim

---

### Post by chili555 on 2015-12-16
> I take it that by "Network Manager" you mean an installable GUI package, yes?
Shouldn't I just be able to use the wireless tool? Aren't they one and the same? Please see here: 

[ATTACH=CONFIG]266199[/ATTACH]

---

### Post by Jim_Ormsby on 2015-12-16
Yup, OK, I don't see the password connection unless  you select the WPA mode.  I told you I was pretty new...

I did find a network manager package, which is what prompted the question.

After rebooting, I used the tool available, and "connect to a hidden network".  But it doesn't connect.  No blue light on the device.
I'm getting close.  I can feel it!
Jim

---

### Post by chili555 on 2015-12-16
I suggest you remove all the settings you added and then restart NM:```
sudo service network-manager restart
```Then click the icon and see if it sees your network: [http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu%284%29.png](http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu%284%29.png)

Click it. You should be challenged for your WPA2 password. Type it in and connect.

---

### Post by Jim_Ormsby on 2015-12-16
YAAAAAYYYYYY!!!!!
It's been working for an hour and a half.  Looks like a winner!!!!
Thanks for all your time, effort, patience and knowledge.  I even managed to learn a thing or two more about the stuff.

---

### Post by F0rZ3r0 on 2015-12-20
Alright. I'm glad it worked for Jim, although I'm using the same adapter as him and yet I still have an issue. So, at one point, the open network hotspot that my ISP has down the street worked for 5 minutes. I left to use the bathroom, came back, to see my computer decided to lock the computer automatically. I log back in and the internet no longer works. I'm really confused. I've sat for another hour to try to get it to work, but nothing has solved my issue. I read all the pages of the thread, and yet to no avail.

So, now, I'm kind of just sitting here. The adapter blinks and can find internet, but can't connect to my secure internet, and only the hotspots down the street. Despite this, I can't do anything with the internet even if I wanted to connect to them.

So...What should I do? I don't want to have to force myself to use a 20ft long ethernet cable or something, because I can't even confirm from there if it'll reach. My room is, of course, not close to my router.

I have a different idea though. If all else fails, maybe try a different adapter, yeah? If that's required, what adapter would you suggest?

---

### Post by chili555 on 2015-12-21
> **F0rZ3r0 said:**
> <snip>
I have a different idea though. If all else fails, maybe try a different adapter, yeah? If that's required, what adapter would you suggest?I suggest the TP Link TL-WN722N. I have one and when I insert it in the USB slot, it blinks twice and connects. No driver, firmware, etc. needed to be installed.

[http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG](http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG)

There are several threads here and at askubuntu.com about fully supported devices. My suggestion is not the only choice.

SLIGHTLY OFF-TOPIC EDITORIAL

Linux will, indeed, always have driver issues, but for several reasons that may not be apparent to all of us. First, new devices are developed and released every day. The manufacturers are in a constant arms race to have a better device with more features and, often, cheaper. In almost every case, they have no concern for the 1-2% of Linux users and therefor don't provide a working driver.

Second, most new Linux users come to the party with what they have now that they bought with working Windows drivers. That device may work well or not at all in Linux. Experienced Linux users always check the forums and are sure the device works in Linux. Mrs. Chili hates it when we walk through the store and I make remarks about items in the computer department; "Those Netgears are tricky even in ndiswrapper." Now I can tell her they are frequently impossible.

---

### Post by jtamedrano on 2015-12-28
Im getting what looks like to be an error when running:

> dmesg | grep ndis

The output im getting is:

> 
[   70.956829] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   70.957552] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   72.088898] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   72.343563] usbcore: registered new interface driver ndiswrapper
[   72.345067] ndiswrapper 2-1:1.0 enxe4f4c63ef19e: renamed from wlan0
[   72.356125] ndiswrapper: interface renamed to 'enxe4f4c63ef19e'
[  231.336397] ndiswrapper: device enxe4f4c63ef19e removed
[  251.116880] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  253.161681] ndiswrapper 1-2:1.0 enxe4f4c63ef19e: renamed from wlan0
[  253.168185] ndiswrapper: interface renamed to 'enxe4f4c63ef19e'
[ 4607.455154] usbcore: deregistering interface driver ndiswrapper
[ 4607.472610] ndiswrapper: device enxe4f4c63ef19e removed
[ 4607.545621] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 4607.549252] usbcore: registered new interface driver ndiswrapper


I can't seem to get my device to work after following every direction.

also 

> Iwconfig

gives me an output of:

> 
enp0s25   no wireless extensions.

lo        no wireless extensions


Im using the same device as everyone else. Thank you in advance for all your help

---

### Post by chili555 on 2015-12-29
> **jtamedrano said:**
> Im getting what looks like to be an error when running:



The output im getting is:



I can't seem to get my device to work after following every direction.

also 



gives me an output of:



Im using the same device as everyone else. Thank you in advance for all your helpI don't see any error here aside from the harmless 'module verification failed: signature and/or required key missing - tainting kernel.' It may safely be ignored.

At time-stamp 72.356125, you had a wireless interface enxe4f4c63ef19e but at 231.336397, it appears that the device was removed. Is the device actually inserted at all times? Is the USB jack solid? Have you tried another USB port?

---

### Post by bob165 on 2016-01-03
Thank-you very much for your help in solving this matter. I tried several others solutions and none worked. You are a guru.:grin:

---

### Post by leka0024 on 2016-01-13
Hi, just wanted to reply about how great this thread is! Thanks to the people who have contributed their time and expertise.

For myself: I used the instructions from earlier pages to install the WNA3100. It seemed to work well. However, it started crashing my PC after a couple days of using it.

I decided to switch to a more friendly adapter. I followed the instructions on this thread to erase the driver and unload the ndiswrapper module.

Then I purchased the TP-LINK TL-WN723N N150 (note: this is slightly different part number than suggested in post #66). It has worked directly out of the box, plug n play.
Note: my 'lsusb' shows --->  Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp.

---

### Post by catherine3 on 2016-02-16
[QUOTE=
The driver can be found here:
[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)
Unpack it and install the respective *.INF file via the "Windows-WLAN-tool"[/QUOTE]

That link does not work.

---

### Post by chili555 on 2016-02-16
> **catherine3 said:**
> That link does not work.You can find the needed file at post #6 here: [http://ubuntuforums.org/showthread.php?t=2052594](http://ubuntuforums.org/showthread.php?t=2052594)

---

### Post by Aidas on 2016-03-03
After running: 
sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf

I got:

couldn't open /home/mediab3/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf: No such file or directory at /usr/sbin/ndiswrapper line 162.

Any suggestions?

---

### Post by chili555 on 2016-03-03
> **Aidas said:**
> After running: 
sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf

I got:

couldn't open /home/mediab3/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf: No such file or directory at /usr/sbin/ndiswrapper line 162.

Any suggestions?That simply means the file you downloaded isn't where you instructed the terminal to find it. Look in your Downloads folder. Do you see a folder called Broadcom_bcm43xx_USB_32_64bit_v2? If not, where did you put it? Did you download the zip and forget to extract it? Or...??

---

### Post by brian129 on 2016-05-15
I'm trying to figure out where to find the correct driver for the WNA3100 wireless adapter (the link on the first page is broken). 
Does anyone one know where I can download the correct driver for Ubuntu 16.04

---

### Post by jeremy31 on 2016-05-15
It should be an attachment in this post [http://ubuntuforums.org/showthread.php?t=2052594&p=12228106#post12228106](http://ubuntuforums.org/showthread.php?t=2052594&p=12228106#post12228106)

---

### Post by brian129 on 2016-05-17
I tried using that driver and it appeared to work, but I can't connect to wireless. It keeps asking for the password, even when I enter the correct password. Maybe not a driver problem though?

---

### Post by jeremy31 on 2016-05-17
The network might be using TKIP encryption and that is a struggle to make work with Linux kernel modules.  I would imagine ndiswrapper might make it impossible to connect.  I had one of those a year or so and gave up on it even without TKIP being enabled on the router

---

### Post by hhh81 on 2016-05-22
That file (driver) is no more there.
You can find the same in [https://media-cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)   from this site 
[https://forum.ubuntuusers.de/topic/belkin-play-wireless-adapter-f7d4101-nicht-er/#post-2612284](https://forum.ubuntuusers.de/topic/belkin-play-wireless-adapter-f7d4101-nicht-er/#post-2612284)

i found it after a quick search in google :)

---

### Post by hhh81 on 2016-05-24
Doesn't work, it disconnects frequently, it stops often, we need the new drivers from broadcom, what a shame.

---

### Post by jeremy31 on 2016-05-24
> **hhh81 said:**
> Doesn't work, it disconnects frequently, it stops often, we need the new drivers from broadcom, what a shame.


That is the same result chili555 and I both had with that device and ndiswrapper.  Here is chili555's [report](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

There are USB wifi dongles that work much better in Linux, like the TP-Link WN722N, 150 Mbps model

---

### Post by hhh81 on 2016-05-24
why  here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link)   it is reported giving matters and not compatible ??

---

### Post by jeremy31 on 2016-05-24
Reports from 6 years ago?  I have used mine in Ubuntu 14.04, 15.10, and 16.04 and it is supported by kernel module ath9k_htc

---

### Post by hhh81 on 2016-05-24
Now i'm using an old ,cheap **sitecom wl-608 v.1 001** (ralink) ,  wifi g.  Works "out of the box"

---

### Post by kurt18947 on 2016-05-25
> **hhh81 said:**
> why  here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link)   it is reported giving matters and not compatible ??

Part  of the difficulty with WiFi adapters is that manufacturers change  chipsets without changing model designations except to append a version  such as Ver.2 or VerB. Linux WiFi cares about chipsets, not manufacturer  model so what works with adapter abc v.1 may not work with abc v.2.   And the chipset used in abc v.2 may not have a native linux driver.  I  also am not sure about the level of support accorded NDISwrapper these  days. The last I knew there wasn't much effort to keep it updated. For  instance, the last I knew NDISwrapper only worked properly with Windows  XP drivers, not Win7, Win8 or Win10 drivers. Newer devices may well not  have Windows XP drivers. And 'bitness' matters with NDISwrapper e.g. if you're using 64 bit *buntu, you need to use 64 bit Windows drivers.  64 bit Windows XP drivers may not be available for some hardware

Short version, life is easier when using hardware with native support.

---

### Post by Owen Thomas on 2016-06-02
> **praseodym said:**
> 
The driver can be found here:
[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)
Unpack it and install the respective *.INF file via the "Windows-WLAN-tool"

I got to the above quoted instruction and couldn't find the driver. The link is broken. Please help.

Naahh,,, forget it.

---

### Post by adv0cat3 on 2016-10-22
> **Owen Thomas said:**
> I got to the above quoted instruction and couldn't find the driver. The link is broken. Please help.

Naahh,,, forget it.

I got the file here:

[https://ubuntuforums.org/showthread.php?t=1695036&p=11838453#post11838453](https://ubuntuforums.org/showthread.php?t=1695036&p=11838453#post11838453)

And used these directions to install:

[https://ubuntuforums.org/showthread.php?t=2221251&p=13010118#post13010118](https://ubuntuforums.org/showthread.php?t=2221251&p=13010118#post13010118)

Worked perfect for me in Ubuntu 16.04 x64.

Performance leaves a little to be desired but that's far from Ubuntu's fault. I have wireless access and that's all I could really ask for.

---

### Post by flameteen on 2017-02-08
When i completed installing the driver with ndiswrapper, internet appear on 10 seconds, later connecting is present, but no internet. iwconfig writing "Invalid misc:34768". But the internet on Windows is normal. Please, help :( (I am Russian, I Don't know English really good.)

---

### Post by chili555 on 2017-02-08
> **flameteen said:**
> When i completed installing the driver with ndiswrapper, internet appear on 10 seconds, later connecting is present, but no internet. iwconfig writing "Invalid misc:34768". But the internet on Windows is normal. Please, help :( (I am Russian, I Don't know English really good.)Please see post #81 above. It will probably never work.

---

### Post by flameteen on 2017-02-09
It will absolutely not working?

---

### Post by chili555 on 2017-02-09
> **flameteen said:**
> It will absolutely not working?Please see: [https://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](https://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)> After a couple of tries, I connected and even at N speeds! After about an hour, it slowed and stopped. Even though it appeared to be connected, pings to my router or to the DNS nameserver 8.8.8.8 went unanswered.And then:> After a reboot, in about an hour, it stalled again.And finally:> As of now, unless someone has another driver or process to try, I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.
Jeremy31 sent me this device, I assume to torture me, after he tried many things and failed. I tried many things and failed. If we can't get it to work, I assure you, it won't work for you either.

RANT:

Is this *really* what you want from your wireless device? Do you want trouble getting it installed, trouble getting connected, freeze-ups and many angry forum posts asking for help?

Why not spend a very few dollars or quid or rupees or whatever you have and get a device that just works smoothly? There are two posts above that suggest replacements. Here is one: [https://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG](https://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG)

END RANT.

---

### Post by mohsensoua on 2017-04-13
I've read through the whole thread and yet I am not sure of the answer to my questions. If I understood well, the proposed solution(s) suggested and tried here were for version 1 and version 2 of this wireless adapter.  Those versions seem to have different hardware architecture and therefore require different drivers. I have just bought a WNDA3100 v3 adapter with the hope to resolve the problems that I've been experiencing with TL-WN723N. From what I read here, it's clear that I made the wrong choice. I have a dual boot Windows 7 23 bits/Ubuntu 14.04. The adapter works great with windows, but not with Ubuntu. My question is: which solution/driver should I use to try and have it work?Thanks.

---

### Post by chili555 on 2017-04-13
> **mohsensoua said:**
> I've read through the whole thread and yet I am not sure of the answer to my questions. If I understood well, the proposed solution(s) suggested and tried here were for version 1 and version 2 of this wireless adapter.  Those versions seem to have different hardware architecture and therefore require different drivers. I have just bought a WNDA3100 v3 adapter with the hope to resolve the problems that I've been experiencing with TL-WN723N. From what I read here, it's clear that I made the wrong choice. I have a dual boot Windows 7 23 bits/Ubuntu 14.04. The adapter works great with windows, but not with Ubuntu. My question is: which solution/driver should I use to try and have it work?Thanks.Please follow this thread: [https://askubuntu.com/questions/903770/cannot-get-netgear-wnda-3100v3-wifi-dongle-to-work/](https://askubuntu.com/questions/903770/cannot-get-netgear-wnda-3100v3-wifi-dongle-to-work/)

Please notice that the latest post is: > when I plug the dongle back in and restart the manager, I get an internal error. Do you want the Journal?Please refer to my post above where I said: > RANT:

Is this really what you want from your wireless device? Do you want trouble getting it installed, trouble getting connected, freeze-ups and many angry forum posts asking for help?

Why not spend a very few dollars or quid or rupees or whatever you have and get a device that just works smoothly? 

---

### Post by mohsensoua on 2017-04-13
> **chili555 said:**
> 
Please refer to my post above where I said:  	 		 			 			 				RANT:

Is this really what you want from your wireless device? Do you want  trouble getting it installed, trouble getting connected, freeze-ups and  many angry forum posts asking for help?

Why not spend a very few dollars or quid or rupees or whatever you have and get a device that just works smoothly? 			 		
 	
 


Thank you very much for the quick reply. I hear very well and I wouldn't lose my time and temper struggling to end up with a poor/uncertain result. The problem is that at this  juncture, I don't know which adapter is now good for ubuntu and will remain good. I've been using TL-WN723N for a good while without significant problems (except that it disconnected from time to time from the wireless network and asked for the password(. But it has stopped working for the last week or so. After several attempts including a clean reinstall of linux, I thought the adapter might be out of order after all. But, then I I replaced it by a apare new one of the same model and the maximum download speed I could get was no more than 2-4 Mb against 30-35 Mb with the same adapter under Windows with the Netgear adapter and  70 Mbwith the Netgear one that doesn't work at all with Linux!...

---

### Post by jeremy31 on 2017-04-13
The TL-WN722N 150 Mbps is a better choice as it uses a better kernel module and has an external antenna, the WN723N is nice as it is small but the wifi signal suffers because of the size

---

### Post by mohsensoua on 2017-04-14
> **jeremy31 said:**
> The TL-WN722N 150 Mbps is a better choice as it uses a better kernel module and has an external antenna, the WN723N is nice as it is small but the wifi signal suffers because of the size
I resolved my linux network problem  by simply buying a wireless range extender that I connected to my pc with ethernet cable and now I am fine. The wifi adapters may serve some day elsewhere.

---

### Post by jeremy31 on 2017-04-14
I have a Linksys RE1000 but haven't tried using it much with linux distros and it isn't exactly portable as it needs it's own power supply

---

