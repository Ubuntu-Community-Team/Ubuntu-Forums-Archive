---
title: "Ubuntu 11.04 on ASUS U41SV"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by chakhedik on 2011-05-09
I've searched entire forums and find none related to ubuntu 11.04 on asus u41sv. So I take the liberty to make this post to share my experience and ask for helps on things I've not yet settled.

First thing I notice after ubuntu installed was the heat under my left palm. Too hot. And when on battery, it only can last 1 hour + where it should last 8 hours for this model.

Here's what I did :

1. Install lm-sensors to monitor the temperatures.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

```
sudo apt-get install lm-sensors
``````
sudo sensors-detect
```Answer YES to all questions.

```
sudo service module-init-tools start
```Then install sensors-applet

```
sudo apt-get install sensors-applet
```When hddtemp configuration popup, choose yes to start hddtemp daemon on boot.

Right click on top panel and choose Add to Panel then select Hardware Sensors Monitor. After added, right click on it and choose Preferences. Go to Sensors tab, click on hddtemp dropdown, scroll to the right, tick to enable it.

At that time my cpu temps was around 56ºC-68ºC while my hdd around 39ºC-41ºC.

2. Install acpi_call to switch off nvidia graphic card (this will reduce the heat).

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

Remove nvidia driver from System->Administration->Additional Drivers first. You already can use unity after driver removed but still not reduce the heat.

```
git clone http://github.com/mkottman/acpi_call.git
``````
cd acpi_call
``````
make
``````
sudo insmod acpi_call.ko
``````
./test_off.sh
```Then find out which method works and delete other methods in test_off.sh. In my case method \_SB.PCI0.PEG0.GFX0.DOFF works.

Now make it run on boot.

```
sudo nano /etc/rc.local
```Add these lines before "exit 0" and change it to your username :

```
insmod /home/yourusername/acpi_call/acpi_call.ko
./home/yourusername/acpi_call/test_off.sh
```On 32-bit, it work great. But when on 64-bit, sometimes the login screen hangs. So what I do is only put insmod line in /etc/rc.local then put **sh /home/yourusername/acpi_call/test_off.sh** command in System->Preferences->Startup Apllications.

Also on 64-bit, sometimes shutdown/restart also hangs. You can try switch it back on before shutdown/restart.

```
cp test_off.sh test_on.sh
```Change \_SB.PCI0.PEG0.GFX0.DOFF to \_SB.PCI0.PEG0.GFX0.DON

Then run ./test_on.sh

If you want to make it run on shutdown or restart, please refer here : [http://ubuntuforums.org/showpost.php?p=1073150&postcount=3](http://ubuntuforums.org/showpost.php?p=1073150&postcount=3)

Now my cpu temps is around 41ºC-50ºC and hdd temp still around 39ºC-41ºC.

What I have not settled yet is Bluetooth and Fn keys.

For bluetooth, I already tried restart bluetooth service and install latest kernel from pre-released repo, none works.

Everytime I want to use bluetooth, I need to boot into windows first then restart into ubuntu, only then the bluetooth can be used. If not, it grayed all the time.

If any of you found a workaround for bluetooth and fn keys on this model please post it here.

Thanks.

---

### Post by user1397 on 2011-05-09
Is this the first ubuntu release you've installed on this laptop?

Seems to be quite problematic with 11.04, although it might get better and better after the giant bug-squashing phase is over (usually a few weeks after a release).

---

### Post by chakhedik on 2011-05-09
Yep, this is the first release installed on this laptop. Just bought a day before ubuntu 11.04 launched.

---

### Post by user1397 on 2011-05-13
I would try dualbooting it with 10.10 or maybe even 10.04 and see if you still have those problems, maybe 11.04 is not for your laptop (happens sometimes, one release works perfectly and the next doesnt)

---

### Post by wildmanne39 on 2011-05-13
> **chakhedik said:**
> I've searched entire forums and find none related to ubuntu 11.04 on asus u41sv. So I take the liberty to make this post to share my experience and ask for helps on things I've not yet settled.

First thing I notice after ubuntu installed was the heat under my left palm. Too hot. And when on battery, it only can last 1 hour + where it should last 8 hours for this model.

Here's what I did :

1. Install lm-sensors to monitor the temperatures.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

```
sudo apt-get install lm-sensors
``````
sudo sensors-detect
```Answer YES to all questions.

```
sudo service module-init-tools start
```Then install sensors-applet

```
sudo apt-get install sensors-applet
```When hddtemp configuration popup, choose yes to start hddtemp daemon on boot.

Right click on top panel and choose Add to Panel then select Hardware Sensors Monitor. After added, right click on it and choose Preferences. Go to Sensors tab, click on hddtemp dropdown, scroll to the right, tick to enable it.

At that time my cpu temps was around 56ºC-68ºC while my hdd around 39ºC-41ºC.

2. Install acpi_call to switch off nvidia graphic card (this will reduce the heat).

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

Remove nvidia driver from System->Administration->Additional Drivers first. You already can use unity after driver removed but still not reduce the heat.

```
git clone http://github.com/mkottman/acpi_call.git
``````
cd acpi_call
``````
make
``````
sudo insmod acpi_call.ko
``````
./test_off.sh
```Then find out which method works and delete other methods in test_off.sh. In my case method \_SB.PCI0.PEG0.GFX0.DOFF works.

Now make it run on boot.

```
sudo nano /etc/rc.local
```Add these lines before "exit 0" and change it to your username :

```
insmod /home/yourusername/acpi_call/acpi_call.ko
./home/yourusername/acpi_call/test_off.sh
```On 32-bit, it work great. But when on 64-bit, sometimes the login screen hangs. So what I do is only put insmod line in /etc/rc.local then put **sh /home/yourusername/acpi_call/test_off.sh** command in System->Preferences->Startup Apllications.

Also on 64-bit, sometimes shutdown/restart also hangs. You can try switch it back on before shutdown/restart.

```
cp test_off.sh test_on.sh
```Change \_SB.PCI0.PEG0.GFX0.DOFF to \_SB.PCI0.PEG0.GFX0.DON

Then run ./test_on.sh

If you want to make it run on shutdown or restart, please refer here : [http://ubuntuforums.org/showpost.php?p=1073150&postcount=3](http://ubuntuforums.org/showpost.php?p=1073150&postcount=3)

Now my cpu temps is around 41ºC-50ºC and hdd temp still around 39ºC-41ºC.

What I have not settled yet is Bluetooth and Fn keys.

For bluetooth, I already tried restart bluetooth service and install latest kernel from pre-released repo, none works.

Everytime I want to use bluetooth, I need to boot into windows first then restart into ubuntu, only then the bluetooth can be used. If not, it grayed all the time.

If any of you found a workaround for bluetooth and fn keys on this model please post it here.

Thanks.
Hi, yes there is a bug report on the overheating of laptops,and it is being worked on according to what I read. Also you can make sure your cpu is on power saver mode and the monitor is set to dim that will help with the heat and battery life. I had over heating on my laptop a couple of years ago and I bought one of those pad with fans to set it on and it helped alot.:D

---

### Post by chakhedik on 2011-05-13
> I would try dualbooting it with 10.10 or maybe even 10.04 and see if you still have those problems, maybe 11.04 is not for your laptop (happens sometimes, one release works perfectly and the next doesnt)I tried with 10.04 & 10.10, fn keys and bluetooth not detected also.

> 
Hi, yes there is a bug report on the overheating of laptops,and it is  being worked on according to what I read. Also you can make sure your  cpu is on power saver mode and the monitor is set to dim that will help  with the heat and battery life. I had over heating on my laptop a couple  of years ago and I bought one of those pad with fans to set it on and  it helped alot.:grin:How to set cpu to power saver mode?

For those who want to enable optimus and use nvidia gc on this laptop. Try this -> [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

It works and tested with Speed Dreams 2.0 and Saurbraten. Use asus N61JV settings.

--------------------------------------------------

Nevermind, I found it, just use **CPU Frequency Scaling Applet** to set cpu to power saver mode.

---

### Post by Zogg on 2011-05-20
I can second the above mentioned problems: bluetooth and fn keys does not work on Asus U41SV.

Because the OP did really help (by turning off the nvidia card), i shall seek to fix at least the fn keys issue. I will post the progress here, if any.

---

### Post by serious7 on 2011-05-29
Sorry for going out of topic, Where can I buy this laptop? I've been looking everywhere but I cannot seem to find a way to order it.

---

### Post by Zogg on 2011-07-24
Status update: still no working fn media keys. With the newest kernel at least the bluetooth does not hand the ubuntu anymore.

If anybody know any kind  of probable ways to get the media keys working, please, give me the dericetions.

---

### Post by Zogg on 2011-07-25
Get your nvidia optimus working with bumblebee!

> bumblebee is Optimus support for Linux, with real offloading, and not
switchable graphics.. More important.. it works on Optimus Laptops without a
graphical multiplexer..


Installation and docs at it's official repository:
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

---

### Post by jaen-ni-rin on 2011-09-02
I'm in a bit different situation, since I'm generally using Arch Linux , but I can chime in a bit.

First off, the system does hang on shutdown when
a) nVidia card has been turned off
b) the netbook is on battery power
Reenabling the nVidia card in shutdown script does not do the trick.
To rectify this you need to remove ehci_hcd module in the shutdown script. Clean shutdown every time ; D

I decided to not install the bumblebee, since it won't automatically turn the card on/off, though I may think about writing some wrapper scripts for that.

As for the ACPI - upon install lm-sensors recognizes only the CPU sensor, I don't even have /proc/acpi/fan and asus_laptop kernel module doesn't recognize the netbook as a proper Asus. Hddtemp works as should, but the HDD seems to be kind of hot, dunno if that's how it should be; gonna compare it to Windows if I can manage to force it to install.

The only function keys I have working are F5 - F7, but that's probably they are processed on the hardware side.

CPU frequency scaling through cpufreq works well, the processor idles most of the time at mere 800 MHz giving excellent uptimes.

I didn't try to do anything with the bluetooth yet.

Right now I'm upgrading the kernel to 3.0.4-1, will tell if it changes anything.

---

### Post by Zogg on 2011-10-01
> **jaen-ni-rin said:**
> 
I decided to not install the bumblebee, since it won't automatically turn the card on/off, though I may think about writing some wrapper scripts for that.


Now it may do that (power_saving mode), but comes with warning concerning acpi calls. More @ [https://github.com/Bumblebee-Project/Bumblebee/wiki/ACPI-Removed](https://github.com/Bumblebee-Project/Bumblebee/wiki/ACPI-Removed)

> **jaen-ni-rin said:**
> 
The only function keys I have working are F5 - F7, but that's probably they are processed on the hardware side.


Even tho 11.10 will soon hit the ground, media keys are NOT functional under 11.04. That means no sound controlls on keyboard. 

The worst part is the broken power-management. If the screen is dimmed (after a period of inactivity), upon moving a mouse the screen will hit 100% brightness, and not the previous intensity. It gets even worse when on battery power (do not use backlight dimming option). And there is no automatic CPU power saving when on battery power.

See you next time!

---

