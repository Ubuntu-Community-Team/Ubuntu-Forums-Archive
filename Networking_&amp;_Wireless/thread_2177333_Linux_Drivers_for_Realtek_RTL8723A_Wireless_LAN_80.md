---
title: "Linux Drivers for Realtek RTL8723A Wireless LAN 802.11n USB 2.0 Network Adapter?"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by Chris of Arabia on 2013-09-28
Does anyone know anywhere I could source these from at all? I've tried Realtek, but their site doesn't even have a reference to the RTL8723A - a re-badged model perhaps?

At the moment. Ubuntu can't see the wireless NIC at all on my Lenovo IdeaPad Yoga-13. The only interface I can see with "ifconfig -a" and "iwconfig" is the loopback, so my guess is it's a lack of drivers that's causing Ubuntu not to see it. It's working fine on the Win8 partition.

---

### Post by praseodym on 2013-09-28
You mean this one:

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by Chris of Arabia on 2013-09-28
The model number is very close, so it should give me something. I just need to rework the installation steps a little, as I've had to bring the files in on a memory stick rather than download them directly.

i also need to find a source for the 'build-essential' package, as I can't do any downloads on this device.

---

### Post by Jakob_Boman on 2014-05-13
Just wondering, did you find any working drivers for this? I'm stuck in the same situation ...

---

### Post by drobnac on 2014-06-11
[SIZE=2][FONT=arial]I have to same problem with 'build-essential' package - Im not able to download the package, since I dont have access to Internet within Linux and I cant install [/FONT][/SIZE][FONT=arial]Realtek RTL8723A drivers because I do not have the package. Is it possible to install 'build-essential' package offline? Can I download the package within Windows 8, upload it onto flash disk and install it in Kali Linux?

Please help[/FONT]

---

### Post by chili555 on 2014-06-11
> **drobnac said:**
> [SIZE=2][FONT=arial]I have to same problem with 'build-essential' package - Im not able to download the package, since I dont have access to Internet within Linux and I cant install [/FONT][/SIZE][FONT=arial]Realtek RTL8723A drivers because I do not have the package. Is it possible to install 'build-essential' package offline? Can I download the package within Windows 8, upload it onto flash disk and install it in Kali Linux?

Please help[/FONT]Yes, you can. However, before we try the long, hard way, do you mind if we get a few details?```
lsusb
```What file are you trying to compile?

---

### Post by drobnac on 2014-06-12
> **chili555 said:**
> Yes, you can. However, before we try the long, hard way, do you mind if we get a few details?```
lsusb
```What file are you trying to compile?

I have made Live USB with Kali Linux 1.0.7 and I booted it in persistence mode. I have Lenovo Yoga 13 with above mentioned Realtek network adapter, Windows 8.1 installed. When I boot Kali in persistence mode I dont have access to internet. 

> [COLOR=#000000][FONT=Times New Roman]root@kali:/# ifconfig[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]          RX packets:20 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]          RX bytes:1200 (1.1 KiB)  TX bytes:1200 (1.1 KiB)[/FONT][/COLOR]

> [COLOR=#000000][FONT=Times New Roman]root@kali:/# iwconfig[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]lo        no wireless extensions.[/FONT][/COLOR]


I think that it is because I dont have drivers for the Realtek network adapter. Therefore I look at the internet and found driver - it is in rtl8723au-master file. I tried to install the driver but I the error appeared.

[COLOR=#000000][FONT=Times New Roman]root@kali:~/Desktop# cd rtl8723au-master/[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]root@kali:~/Desktop/rtl8723au-master# make[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]make ARCH= CROSS_COMPILE= -C  M=/root/Desktop/rtl8723au-master  modules[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]make: *** M=/root/Desktop/rtl8723au-master: No such file or directory.  Stop.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]make: *** [modules] Error 2[/FONT][/COLOR]

Afterwards, I read that I have to install other packages to install the driver, but an error occurs when I tried to install the packages. Can you please help me? Thank you.

[COLOR=#000000][FONT=Times New Roman]root@kali:/# sudo apt-get install build-essential linux-headers-generic linux-headers-'uname -r'[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Package linux-headers-generic is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]is only available from another source[/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]E: Package 'linux-headers-generic' has no installation candidate[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]E: Unable to locate package linux-headers-uname -r[/FONT][/COLOR]

---

### Post by chili555 on 2014-06-12
I will be very happy to help you; very, very happy. However, as I said, before we proceed, I'd like to confirm that the package you are trying to compile is correct for your device. That's why I asked for:```
lsusb
```Feel free to omit everything that you are sure is not your Realtek.

It would be a huge waste of your time and mine to go through the tortuous process to compile the *wrong* driver.

---

### Post by drobnac on 2014-06-12
Oh, Im really sorry for misunderstanding - here it is: 

> [COLOR=#000000][FONT=Times New Roman]root@kali:~# lsusb[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 004 Device 004: ID 5986:029c Acer, Inc [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 004 Device 003: ID 2047:0855 Texas Instruments [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 003 Device 006: ID 04f3:000a Elan Microelectronics Corp. [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 003 Device 005: ID 0bda:1724 Realtek Semiconductor Corp. [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 003 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 002 Device 002: ID 125f:312b A-DATA Technology Co., Ltd. Superior S102 Pro[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]

---

### Post by chili555 on 2014-06-12
You device:> ID [COLOR="#FF0000"]0bda:1724[/COLOR] Realtek Semiconductor Corp. ...is indeed covered by the driver 8723au:```
chili@T410:~/rtl8723au$ modinfo 8723au.ko | grep 1724
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]1724[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*
```What you are missing is the meta packages build-essential and linux-headers-generic. If you could get, even temporarily, ethernet access, you could solve this in about five minutes; if not, maybe five long, difficult days.

You said:> When I boot Kali in persistence mode I dont have access to internet. What is the problem? Do we need to troubleshoot the ethernet device?

---

### Post by drobnac on 2014-06-13
Ouch - the thing is that I dont have Internet access in Kali, because I **dont have ethernet port **on my Lenovo Yoga 13. I can access internet in Windows through wireless if it could help.

---

### Post by chili555 on 2014-06-13
Here is how to do it in Ubuntu in about five days...maybe. I haven't a clue about Kali; sorry.

Go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Select Trusty in the drop-down box. Search for linux-headers-generic and build-essential. Be sure to locate their dependencies *and the dependencies of the dependencies.* Be sure to download the correct version, either 32- or 64-bit. Once you've download about fifteen or so packages on another computer, transfer them with a USB stick or similar to the desktop of your Ubuntu computer. Open a terminal and install them:

```
cd ~/Desktop
sudo dpkg -i *.deb
```
It may complain that a package is missing a dependency. If so, download that and add it to the desktop and try again. 

Write many posts on the forum to tell old Chili how you're stuck. Rinse and repeat.

---

### Post by brad33 on 2014-11-04
Were you ever able to get this to work?
And were did you find the drivers?

I'm thinking of installing Ubuntu on my Yoga13 and wanted to make sure it would be possible to get it to work.

---

