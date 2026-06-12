---
title: "unable to install the wlan driver"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by difuiv250385 on 2011-01-24
Hi ,
I am trying to install the wlan driver in my laptop so that I can start using wifi.
if I use "lspci " or "lshw" I am not able to see my wlan card.
the response to "lshw" is as follows,

sudo lshw | grep -i network
           *-network
                product: PRO/100 VE Network Connection

and for "lspci"

sudo lspci | grep -i network

08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

I donno whether this ethernet controller and wlan controller are same!!!!

I installed ndsiwrapper also, and tried finding the windows driver in hp(my laptop is hpdv2000) website and downloaded the .exe which I am not able to unzip to get the .inf file.

can anybody tell me how I can solve this issue. I spent almost 4 days on it :(.
And I am sorry i din mention dat m a newbee..

---

### Post by Frogs Hair on 2011-01-24
You could try installing 7zip to extract the file . I read on another forum that this worked for someone but I have not tried it . After installing right click the .exe and select 7zip to extract the file.

I know there are users here that have installed drivers using the wrapper , so be patient and welcome to the forums.

---

### Post by davidmohammed on 2011-01-24
if you run 

sudo lshw -class network

please post the results in a reply - in the trace should be a wlan0 logical device that is claimed.  If it is then the kernel has recognised you wireless card correctly.

If it is unclaimed, please post the results of 

lsusb

and

lspci

thanks.

---

### Post by difuiv250385 on 2011-01-25
[B]Re: unable to install the wlan driver

Thanks for the reply,
[/B]
>sudo lshw -class network

  *-network               
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:10:fb:7e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:d4000000-d4000fff ioport:3000(size=64)

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0bc2:2120 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Bucky Ball on 2011-01-25
Have you plugged in an ethernet cable? Is it working? If so, get your updates then:

System>Administration>Additional Drivers.

AVOID ndiswrapper unless it's the ABSOLUTE *last* resort or your card is known to only work with it (in other words, only works with the Windows driver, there is no Linux driver, pretty rare nowadays). It can be a maze and is superseded for most wireless cards now. Intel wireless generally works out of the box, BUT, you need to be connected with an ethernet cable to get it happening. ;)

Just looking at your outputs, I don't see a wireless card there. You are looking for a 'Network Controller', something like this:

```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
```

---

### Post by difuiv250385 on 2011-01-27
I can only c system->administration and there is no option like additional driver.

m sorry m vey new bee to linux.. also if i click on system->asminidtrator->hardware drivers, it shows a message saying there is no propriatery drivers installed.

---

### Post by Bucky Ball on 2011-01-27
You are using 8.04 LTS? Support runs out in April. If you have just installed I would recommend reinstalling 10.04 LTS. Supported until April 2013. LTS = long term support.

'Hardware Drivers' is the one you should be looking at, yes. Again, have you plugged in a cable and gotten all updates?

System>Administration>Update Manager.

---

### Post by difuiv250385 on 2011-01-31
Hi,
 
I have installed the ubuntu 10.4 just before couple of days. 
 
>> System>Administration>Update Manager
 
I will try doing this and update you with the result.

---

### Post by Bucky Ball on 2011-01-31
In 10.04 LTS 'Hardware Drivers' becomes 'Additional Drivers', found in the same place.

Have a look there after you have plugged in with a cable and gotten updates. Remember, you need to be online to download the firmware. Good luck. ;)

---

### Post by A-rap on 2011-02-01
Obviously u havent installed the drivers correctly. U must extract driver folder. 1st please donwload the most up to date drivers from realtek website. Then in that driver package is a pdf with correct instructions to install the driver. It worked for me, until SIOCSIFFLAGS came kickin in....

---

### Post by Bucky Ball on 2011-02-01
> **A-rap said:**
> Obviously u havent installed the drivers correctly. U must extract driver folder. 1st please donwload the most up to date drivers from realtek website. Then in that driver package is a pdf with correct instructions to install the driver. It worked for me, until SIOCSIFFLAGS came kickin in....

Try:

```
sudo su
make
make install
```

NOT:

```
sudo make
sudo make install
```

For some reason the latter just doesn't work.

---

### Post by difuiv250385 on 2011-02-15
I downloaded the windows driver for the wireless lan card (i searched in google for "wifi driver hp pavillion dv2046tu windows" and downloaded it from hp site). and tried installing the driver using the wine application. I got the following error during installation.

chethu@chethu-laptop:~/Downloads$ wine HP_Broadcom_wirelessLANdriver.exe 
wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
wine: cannot find L"C:\\windows\\system32\\HP_Broadcom_wirelessLANdriver.exe"
chethu@chethu-laptop:~/Downloads$ wine WIFI_IntelPRO_Driver.exe
wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
wine: cannot find L"C:\\windows\\system32\\WIFI_IntelPRO_Driver.exe"
chethu@chethu-laptop:~/Downloads$ wine WIFI_IntelPRO_Driver.exe
wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination

C:\SWSetup\SP34489A>start /wait sinstall.exe
fixme:exec:SHELL_execute flags ignored: 0x00000100

C:\SWSetup\SP34489A>if errorlevel 1 goto end



Please tell me if i have to do some thing extra than this.

---

### Post by gandaran on 2011-02-15
> **difuiv250385 said:**
> I downloaded the windows driver for the wireless lan card (i searched in google for "wifi driver hp pavillion dv2046tu windows" and downloaded it from hp site). and tried installing the driver using the wine application. I got the following error during installation.

chethu@chethu-laptop:~/Downloads$ wine HP_Broadcom_wirelessLANdriver.exe 
wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
wine: cannot find L"C:\\windows\\system32\\HP_Broadcom_wirelessLANdriver.exe"
chethu@chethu-laptop:~/Downloads$ wine WIFI_IntelPRO_Driver.exe
wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
wine: cannot find L"C:\\windows\\system32\\WIFI_IntelPRO_Driver.exe"
chethu@chethu-laptop:~/Downloads$ wine WIFI_IntelPRO_Driver.exe
wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination

C:\SWSetup\SP34489A>start /wait sinstall.exe
fixme:exec:SHELL_execute flags ignored: 0x00000100

C:\SWSetup\SP34489A>if errorlevel 1 goto end



Please tell me if i have to do some thing extra than this.
wine uses a virtual drive C, you cant install system drivers using wine!
and why are you trying to install broadcom drivers? does you laptop have broadcom wireless card or ins't it intel?
look it would be better if you ask for help in the networking and wireless section of ubuntu forums, I'm sure you would get better support there.

---

### Post by difuiv250385 on 2011-02-16
I will switch this thread to "networking and wireless" section of ubuntu forums. But before that please tel me how I can check which wireless n/w card does my laptop has.. I bought my laptop before 4.5 years and its is HP dv2046TU .. where I can get the information about the wireless card my laptop has.

---

### Post by gandaran on 2011-02-16
> **difuiv250385 said:**
> I will switch this thread to "networking and wireless" section of ubuntu forums. But before that please tel me how I can check which wireless n/w card does my laptop has.. I bought my laptop before 4.5 years and its is HP dv2046TU .. where I can get the information about the wireless card my laptop has.
do you have windows installed? you could check there.
the reason the 'lspci' command doesn't turn out what card the laptop has could be either to an unsupported wireless card in linux, if this is the case then you will have a hard time fixing it or also can be something is wrong with the card, I would check if it's properly installed first.

---

### Post by difuiv250385 on 2011-02-22
>  I would check if it's properly installed first. 	

But how to check whether the wlan card is working fine or not.. also I dont have any other operating system.. but I had windows along with suse linux few months bk but now i have only ubuntu linux in my pc.. if the windows system drivers cant be installed using wine and linux device driver for my wlan card is not there what do you suggest me to do to make my wlan working..

---

### Post by G4Oblivion on 2011-02-22
I found the windows drivers for your computer.
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=228&lc=en&cc=us&dlc=en&sw_lang=&product=3252195#N298]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=228&lc=en&cc=us&dlc=en&sw_lang=&product=3252195#N298") (XP drivers. Vista do not work with ndiswrapper)

It looks like you either have a Broadcom or Intel card.
My guess would be Intel.
I don't believe Intel has the best of support for linux drivers.

If you have windows on the computer too, open up CMD and type ipconfig /all
Post what it printed.

This site may have one of your dirvers
[http://www.intel.com/support/wireless/sb/cs-006408.htm]("http://www.intel.com/support/wireless/sb/cs-006408.htm")

I suggest finding a way to confirm what card you have before trying out different drivers.

Just to make sure, you have your wireless card enabled in your BIOS, right?
May want to try updating your BIOS.

EDIT:
Looks like if its an Intel card it would be one of these: 3945, 2915 or 2200.
All of those are supposed to be in the kernel already.

3945 can be found here:
[http://ipw3945.sourceforge.net/]("http://ipw3945.sourceforge.net/")

2915 & 2200:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by gandaran on 2011-02-22
> **difuiv250385 said:**
> But how to check whether the wlan card is working fine or not.. also I dont have any other operating system.. but I had windows along with suse linux few months bk but now i have only ubuntu linux in my pc.. if the windows system drivers cant be installed using wine and linux device driver for my wlan card is not there what do you suggest me to do to make my wlan working..
maybe removing the back cover and checking if it's properly inserted unless it is built in onboard, I have seen this problem before here on the forum, the card most times was not detected with 'lspci' command because it was slightly detached.

---

### Post by Bucky Ball on 2011-02-22
If it's Broadcom or Intel, as suggested, plug in an ethernet cable, get online, get updates, then check:

System>Administration>Additional Drivers.

Broadcom and most Intel cards are fully supported in Linux, esp Ubuntu.

---

### Post by wep940 on 2011-02-22
+1 on what Bucky Ball is saying - you need to plug an ethernet cable into the ethernet port on your laptop and connect the other end to a port on your router. This should get you at least on the internet. Once there, do the updates, then check in Additional Drivers again.
 
EDIT: ADDED THE FOLLOWING:
 
I just noticed that when you were trying to install the drivers with wine (as someone else pointed out, this will not work), you tried installing 2 completely different drivers - 1 for Broadcom and 1 for Intel. As far as I have ever seen, it's either 1 or the other, but never both. Installing 2 different drivers can result in conflicts that cause the device to fail (not break, just fail to be used).
 
END OF EDIT
 
 
If you absolutely can't see your wireless adapter (the last output you posted does not show a wireless adapter) I would suspect a physical problem with the adapter. So, I'm going to back up a step: when you had Windows and Suse installed could they both see the adapter? If so, boot using the OpenSuse LiveCD, then:
 
-open a terminal window
 
- try lspci and lsusb again - your wireless should show. Keep in mind that while most built-in wireless adapters are pci devices, there is also a lot of laptops that have the internal wireless connected to an internal USB bus. That's why we are asking for both the lspci (lists all PCI devices Linux knows about - doesn't mean they have a driver and can work, simply that Linux recognizes it as a PCI device) and also the lsusb (list all known USB devices, same conditions as lspci output).
 
If they show a wireless device, post that back here so we can help try to find you a driver if the hard wired connection and the update make no difference.
 
A couple of comments on ndiswrapper:
 
- it used to be needed for a lot of wireless adapters, but so much progress has been made by very dedicated individuals to create native drivers for most of these devices. Ndiswrapper should only be considered AFTER everything else has failed.
 
- ndiswrapper, with it's front-end ndisgtk, is fairly simple to use now. BUT, if you have tried it already without realizing what happens, it can mess some things up such that ndiswrapper will need to be removed and then installed again to clear things out. The drivers can ONLY be Windows XP and must match the architecture of your Ubuntu install - 32 bit or 64 bit. With that said, *PLEASE* be sure so exhaust all other options. It may take a while to get through things, but it's best to go without ndiswrapper if at all possible.
 
So, follow Bucky Ball's advice and hardwire a connection and do the update. Also post back if you could use the wireless in Windows and in OpenSuse - particulary OpenSuse so we can what the adapter actually is. We haven't determined that yet. As dumb as it sounds, considering it's not showing at all, I'm curious in the above output because I wonder if you're wireless adapter has been removed by someone.
 
Bucky Ball:  no one has determined the actual device and chipset yet have they?  I saw a post in this thread about using the realtek drivers, but I think that poster just saw your example and made assumptions?

---

### Post by Bucky Ball on 2011-02-22
Perhaps. ;)

---

### Post by wep940 on 2011-02-22
Hopefully you understand, but no dig or anything was intended - I was just trying to make sure I had followed things up to now.;)

---

### Post by Bucky Ball on 2011-02-22
This machine has:

Integrated 802.11a/b/g,  Intel Pro/Wireless 3945ABG

According to this:

[http://www.bechna.com/shop~online-laptops-notebooks~prices-hp-pavilion-dv2046tu-laptop-with-core-duo-processor-14-1inch-screen~p-160339.html]("http://www.bechna.com/shop%7Eonline-laptops-notebooks%7Eprices-hp-pavilion-dv2046tu-laptop-with-core-duo-processor-14-1inch-screen%7Ep-160339.html")

Should work 'out of the box' but need to get online with a cable to do it. Not understanding what the problem is. I would suggest taking the back off and having a look to see if the card is in securely and wired to the machine.

If you boot from the LiveCD, does it see the card and offer drivers (presuming you are online with a cable at that time)?

You might find some other clues here:

[http://au.altavista.com/web/results?fr=altavista&itag=ody&q=Intel+Pro%2FWireless+3945ABG+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?fr=altavista&itag=ody&q=Intel+Pro%2FWireless+3945ABG+ubuntu&kgs=0&kls=0)

Let your fingers do the walking ...

* wep940: I can dig it! All cool here. ;)

---

### Post by wep940 on 2011-02-22
Great job Bucky Ball! ;)

---

### Post by wep940 on 2011-02-25
> **Bucky Ball said:**
> Perhaps. ;)
 
Jeez do I feel stupid - I usually am teased for having a different sense of humor, but how I missed your obvious humor here (assumption - perhaps) is beyond me. I love it!! ;)

---

### Post by difuiv250385 on 2011-03-07
I am very sorry for the delayed response I was out of reach to the network till today.

> maybe removing the back cover and checking if it's properly inserted
I think if its a detachable card it should appear in lsusb or lspci. Also as one of my friends suggested for the laptops the wlan cards shall be integrated within the mother board due to space constraint.So i didn dare to open the laptop as I don have the necessary tools to operate it :roll:.. I shall consider this option if nothing can be done from the driver's side.

> Integrated 802.11a/b/g, Intel Pro/Wireless 3945ABG
Yes, Its quite convincing , so I started searching for the Intel Pro/Wireless 3945ABG driver, and I found this

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)
>>[B]Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly.
[/B]
and My system has the kernel 2.6.32.
but there is no source code in **drivers/net/wireless/iwlwifi **folder
except a Makefile and Kconfig files. I will try to download the source code and build from [http://intellinuxwireless.org/](http://intellinuxwireless.org/) and try to install the driver.

Please let me know if there is any mistakes in my understanding.

---

### Post by difuiv250385 on 2011-03-16
I downloaded the source code and built it and laoded the module.. still the network card not geting detected.. as a last hope m planning to get it checked by an hp service centre to see whether the wlan card is fine from hardware point of view..

---

### Post by walt.smith1960 on 2011-03-16
I have that card in a ThinkPad--it's detected by a liveCD and default install, no internet connection required.  Do you have some sort of switch or key combination to enable/disable? That adapter is WELL supported.  It could be unplugged or died a premature death.  I wonder if there's one or more covers on the bottom of the machine.  My Thinkpad has 2; one is for memory and one is for the wireless card.  A friend just bought an HP notebook-don't know the model-and it had a keystroke on/off switch.  His key has an LED built into the keycap. Amber=off, white=on

---

### Post by difuiv250385 on 2011-04-10
I found the card exists but as u said it has dies a premature death.. The card not seems to be functional.. :(

---

