---
title: "Help pls"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by angelonico on 2011-03-12
Hello, I am a programing student and I need to use a linux based os for our class. I got an Acer Aspire 4745G with an ATI 5650 video card (switchable). I tried installing ubuntu before using wubi but I couldnt get the wifi/lan working therefore I removed it. I think the drivers for that are not supported. I searched the internet and it has provided me solutions that didnt work. But recently, I am really considering to move to ubuntu as a primary OS. I used a software from Acer to detect the specific hardware installed on my laptop. Here is the result:

BLUETOOTH       Broadcom
CAMERA          Suyin
LAN             Atheros
VGA             ATI/AMD
VGA_2           Intel
Wireless LAN    Broadcom

I still got the drivers cd that came with my laptop. I want to start fresh so reformating wouldnt be a problem. And I want Windows 7 as a secondary OS. Can anyone please help me with the installing of both OS as a dual boot and get all the drivers to work in ubuntu? Thanks and more power to Linux!

---

### Post by lykeion on 2011-03-12
[LIST]
[*]Start by installing Windows first (this is necessary if you want to have a dual boot setup).
[*]Then download and burn a CD with Ubuntu.
[*]Boot with CD and run Ubuntu without installing it (as Live CD).
[*]Check that everything works as it should with your hardware. Broadcom drivers have been a problem before but there have been lots of developing to get them to work.
[*]Finally install Ubuntu on your hard disk.
[/LIST]

I'll check the links to the documentation pages of dual-booting, installing Ubuntu, and Broadcom drivers, etc, and post them here in a while...

EDIT
* [Broadcom BCM43XX WiFi Driver]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
Will guide you how to install the driver (not sure if this is the chipset you have though). I recommend that you identify your card/driver while running Ubuntu from LiveCD

* [Dual Boot Ubuntu and Windows]("https://help.ubuntu.com/community/WindowsDualBoot")
Will guide you how to setup a dual boot of Windows/Ubuntu. There are also links with guides: How to Resize Windows Partitions and BurningIsoHowto.

* [BinaryDriverHowTo/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
You might want to check this guide on how to install the proprietary fglrx driver for your ATI video card as well.

Finally a tip: Try to name your thread better. This is a quote from the Ubuntu Forums Code of Conduct:
> Make the title of your thread meaningful and concise. For example, if you are having difficulty using your BroadCom card to connect to your wireless internet, the title "Cannot connect to wireless with BroadCom card" will attract people with experience with wireless internet and BroadCom cards. Titles like "Help me please!!!" or "I have a problem" may be overlooked by people who could otherwise help you.

---

### Post by DougieFresh4U on 2011-03-12
You don't mention how much hard drive you have. I would say install Win7 first then install Ubuntu. When partition part comes up, you could go with install side-by-side option and all should be good. 
Actually quite easy if you don't require any thing special :D

---

### Post by angelonico on 2011-03-12
Actually I tried what you said before but I cant get the Wifi/LAN working so I asked for help. Anyhow I have 500gb worth of space and I want to have a swap space but I dont know how to

---

### Post by grahammechanical on 2011-03-12
Can you connect the laptop to the modem/router using a ethernet cable? If you can, then do it and then run the Ubuntu live CD. You should get a connection to the Internet. Then go to system>Administration>Additional Drivers to see if you are being offered any drivers to activate. If you are, then this is good. Because this is what you will need to do after the installation is complete.

When you choose the side by side option the installer will do all the work for you. It will create two Ubuntu partitions. One partition will be for Swap.

Do not choose to use the entire disc. You will lose your Windows operating system.

Study this link for Wireless Trouble Shooting:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Note what you have to do if you need to use the Windows Drivers. You may not need to but it is good to prepare beforehand.

And do not forget that the wireless adapter may need to be switched on through the keyboard. Or that Windows may switch it off as it shuts down.

There is also community documentation that explains the installation process. They are web documents so you can study them using Windows.

Regards.

---

### Post by angelonico on 2011-03-12
@graham

As I said LAN and WIFI is not working so I dont really have a way to connect to the Internet

@lykeion

Ill try to do that and will update this as soon as I can. Thanks for the help

---

### Post by angelonico on 2011-03-12
I installed the Ubuntu 10.10 already and the same problems still exists. According to the lswh, BCM43325 is the chipset

---

### Post by lykeion on 2011-03-13
I think it's BCM4325 you mean, and the link I gave you earlier ([Broadcom BCM43XX WiFi Driver]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")) will give you directions how to install the driver (see section Installing STA drivers).

---

### Post by angelonico on 2011-03-16
I got the internet connection running and I got updates from the internet. I also got the proprietary driver for the graphics card. Now, when I choose Ubuntu in GRUB, it does not load the GUI interface but a terminal like version. Its like DOS or something. I didnt know what caused that to happen.

---

### Post by matt_symes on 2011-03-16
Hi

Post the output of 

```
cat /proc/cmdline
```

Kind regards

---

### Post by angelonico on 2011-03-16
BOOT_IMAGE=/boot/vmlinuz-2.6 53-27 - generic root = klev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash


I am not sure exactly because I only copied the ouput by hand and typed it again here but more or less that is the output.

---

### Post by matt_symes on 2011-03-16
Hi

You command line looks fine. Is this a WUBI install ?

What happens if you type

```
sudo service gdm start
```

Does it start X ?

Kind regards

---

### Post by angelonico on 2011-03-16
Uhhh I tried the startx command but it doesnt do anything. And yes this is a WUBI installation. It worked fine the first week and it suddenly changed into the command line interface.

---

### Post by matt_symes on 2011-03-16
Hi

Did you try 

```
sudo service gdm start
```

Are there any error displayed with startx ?

Kind regards

---

### Post by angelonico on 2011-03-16
I think I got the problem. When I installed the ATI driver, and restarted my system, it goes back to the command line interface. If I disable the ATI driver, when I opened Ubuntu, it was on its GUI version. Any thoughts on how can I solve this problem?

---

### Post by matt_symes on 2011-03-16
Hi

What is your ati card. Open a terminal and type

```
lspci -k | grep -i vga -A3
```

Post back results. This will identify your card model.

Kind regards

---

### Post by angelonico on 2011-03-25
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
	Subsystem: Acer Incorporated [ALI] Device 0357
	Kernel driver in use: i915
	Kernel modules: i915
--
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
	Subsystem: Acer Incorporated [ALI] Device 0357
	Kernel driver in use: radeon
	Kernel modules: radeon

its a ati mobility radeon 5650

if I enabled the driver using Additional Drivers, after restarting I get the command line interface

---

### Post by matt_symes on 2011-03-25
Hi

> **angelonico said:**
> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
	Subsystem: Acer Incorporated [ALI] Device 0357
	Kernel driver in use: i915
	Kernel modules: i915
--
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
	Subsystem: Acer Incorporated [ALI] Device 0357
	Kernel driver in use: radeon
	Kernel modules: radeon

its a ati mobility radeon 5650

if I enabled the driver using Additional Drivers, after restarting I get the command line interface

This PC has 2 graphics cards ? The first thing i would do is disable the Intel integrated graphics card in the BIOS. 

I will do some research on your ATI card and the fglrx driver but i think it should work.

Kind regards

---

### Post by angelonico on 2011-03-26
its a laptop. it has two cards because its graphics can be switched between the intel and the dedicated ati.

---

### Post by matt_symes on 2011-03-27
Hi

Did you try disabling one of the graphics cards ? I think it might be a conflict.

I have guests around this weekend so it's very hard for me to look into this at the moment. (My friends birthday)

In the meantime could you please post the output of

```
cat /etc/X11/xorg.conf
```

when the flgrx driver is installed(ATI driver).

Kind regards

---

### Post by angelonico on 2011-03-29
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


i noticed when i installed and restarted, the loading screen has changed and there was a split second of random colors in a dirty white background but aside from that its ok i think

---

### Post by alphacrucis2 on 2011-03-29
> **angelonico said:**
> Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


i noticed when i installed and restarted, the loading screen has changed and there was a split second of random colors in a dirty white background but aside from that its ok i think

So is it working now?

---

### Post by angelonico on 2011-03-29
i guess its okay. i have not tested playing games on ubuntu. mostly im using just the terminal(gcc) and chromium(internet) and i havent really completely moved my stuff to ubuntu. thanks for the help. i just wish ubuntu would support real time discreet and integrated graphics card switching provided by Nvidia(optimus) and ATI(Switchable).

---

