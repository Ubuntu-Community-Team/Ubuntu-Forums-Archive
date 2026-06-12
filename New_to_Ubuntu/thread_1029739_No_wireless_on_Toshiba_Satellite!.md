---
title: "No wireless on Toshiba Satellite!"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by mystearica007 on 2009-01-03
Hi.
I'm a noob at computers. xD
Sorry if this is already posted, but I checked and nothing came up.

Okay, so here's the problem.
I run a Toshiba Satellite A200 (I believe).
I installed Ubuntu onto it, and I opened up Mozilla Firefox.

NOTHING.

I don't know what I'm doing wrong.
I don't get it. xD
So... 
Any ideas? :)

---

### Post by Tom--d on 2009-01-03
Erm..
Not to be rude.. but you've just said I installed Ubuntu and opened up Firefox.

Did you even think that you might of needed to configure your wireless? You know. Connect to it?


Anyways: Post your outcome of "lsusb" and "lspci" from the Terminal (Applications > Accessories > Terminal)

Thanks,
Tom

---

### Post by -kg- on 2009-01-03
Absolutely!  I am using a Toshiba Satellite (A135-S4487).

On your top Launch bar toward the right side, you should see an icon right next to your "Speaker" icon that looks like signal strength bars.  Left clicking on that will bring up the available networks to connect to via wireless.

You will want to click on your network.  If you have WEP or WPA security set up on your wireless network (you *DO* have that set up, right?) you will need to configure the network connection and enter your Encryption key to access the network.

Once this is done, you should be up and running.

---

### Post by melojo on 2009-01-03
Click on Applications>Accessories>Terminal  and type these commands below and post the output.

```
lspci
sudo -C network
ifconfig

```

This will give us more info.

---

### Post by mystearica007 on 2009-01-03
Sorry. xD
I meant, like, I opened up my Network connections and nothing showed up for my wireless.
Nothing.

So anyway, here's the lsusb
Bus 005 Device 001: ID ld6b: 0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID ld6b: 0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID ld6b: 0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID ld6b: 0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID ld6b: 0001 Linux Foundation 1.1 root hub

And for the lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/Gms, 943/940GML Express integrated Graphics Controller (rev 03)
00:02.1Display controller: Intel Corporation Mobile 945GM/GMS/GME. 943/940GML Express Integrated Graphics Controller (rev 03)
00:lb.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:lc.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:lc.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:lc.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:ld.0 USB Controler: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:ld.0 USB Controler: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:ld.0 USB Controler: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:ld.0 USB Controler: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:ld.0 USB Controler: Intel Corporation 82801G (ICH7 Family) USB3 EHCI Controller (rev 02)
00:le.0 PCI bridge: Intel Corporation 82801 Mobile Bridge (rev e2)
00:lf.o ISA bridge: Intel Corporation 82801GBM (IXH7-M) LPC Interface Bridge (rev 02)
oo:lf.2 IDE iterface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11 abg Wireless PCI Express Adaptor (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

There you go. :]

---

### Post by mystearica007 on 2009-01-03
stanxkyle@MeaganMayChristyne:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
stanxkyle@MeaganMayChristyne:~$ sudo -C network
sudo: illegal option `-C'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
stanxkyle@MeaganMayChristyne:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:a8:83:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

There's my lspci/sudo -C network/ifconfig
(This is all like Latin to me. I don't understand any of it. xD)

---

### Post by thomas228 on 2009-01-03
> **mystearica007 said:**
> Hi.
I'm a noob at computers. xD
Sorry if this is already posted, but I checked and nothing came up.

Okay, so here's the problem.
I run a Toshiba Satellite A200 (I believe).
I installed Ubuntu onto it, and I opened up Mozilla Firefox.

NOTHING.

I don't know what I'm doing wrong.
I don't get it. xD 
So... 
Any ideas? :)

Hi

What version of ubunrtu 8.04 Hardy or 8.10 Intrepid ?

It can make a big diference in what kind of help you get

Good luck

Tom

---

### Post by nothingspecial on 2009-01-03
In your menus system > administration > hardware drivers
Disable the atheros driver in there. Then accessories > terminal and copy and paste

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Then

```
sudo modprobe ath5k
```

to load the driver.

Then to make the driver load every time you boot

```
gksudo gedit /etc/modules
```

add this to the bottom of the file


```
ath5k
```

save
close
reboot

---

### Post by mystearica007 on 2009-01-04
@Nothingspecial-
Thanks you!
It worked! :)

I really appreciate all of your help, guys~ ^_^

---

