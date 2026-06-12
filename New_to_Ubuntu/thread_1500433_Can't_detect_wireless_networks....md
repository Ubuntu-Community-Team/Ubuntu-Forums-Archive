---
title: "Can't detect wireless networks..."
date: 2010-06-03
forum: New to Ubuntu
---

### Post by wombatvvv on 2010-06-03
Can anyone help out here?

I'm pretty sure the wifi does work, because I think I've seen it detect wifi-networks in other places (but I'm not 100% sure).

Now I can't detect any networks at all. If I restart in Windows (which is what I've done now), I can detect about 7 different wifi networks. So it looks like something is wrong.

My laptop specs can be seen here: [http://gulf.computers.toshiba-europe.com/innovation/en/product/Qosmio-F60-10V/1081301/toshibaShop/false/](http://gulf.computers.toshiba-europe.com/innovation/en/product/Qosmio-F60-10V/1081301/toshibaShop/false/)

If anyone has any idea, I'd be much appreciative.

---

### Post by angelsguitar on 2010-06-03
Did it work previously on Ubuntu, and then suddenly stop working?  Or it never worked in Ubuntu (only in Windows)?

Anyway, lets start with the obvious and simple. Do you see the network manager icon on your panel's tray area? Is you see it, right click on it and make sure that both "Enable Networking" and "Enable Wireless" have a check mark on them.

If that doesn't solve the problem, post the output of the following commands to get a little more info of your setup:

```
lspci
```
```
iwconfig
```

---

### Post by wombatvvv on 2010-06-03
thanks for helping.

Yes, the icon is there and networking is enabled. The networks works when plugged in.

I'll do what you've asked, but it's going to take a bit because I'll have to restart in Linux, copy the output into a text file and paste it into my windows drive, restart in windows, etc.

Give me 10 minutes.

---

### Post by wombatvvv on 2010-06-03
Okay, this is what I got. Although I'm keen to learn, it's all gibberish to me, I hope you know what it means!

```

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a2b (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
02:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

vboxnet0  no wireless exte




```

---

### Post by angelsguitar on 2010-06-03
Ok, lspci tells us you have a Realtek 8172 Wireless card. Then iwconfig tells us that your card (the one that appears as wlan0) is apparently configured.  However, it is not detecting nearby networks (I guess you already knew that ](*,)) I googled up some info about it, and found out that you are not the only one with the problem.

Let's try to update the driver of your card with a pre-packaged one. You'll need to do this from the Ubuntu partition, and you'll need to be connected to the Internet. Try to connect using an ethernet cable if possible. If there's no way you can connect by cable, I'll explain an alternate way later (but the connected way is better, though)

Run the following commands on the terminal. First, let's add a new repository location, so that we can install it from there later (it will ask for your password):

```
sudo add-apt-repository ppa:matt-price/mattprice
```

Now, let's refresh package info on our system:

```
sudo apt-get update
```

Now, install the driver from the recently added repo:

```
sudo apt-get install rtl8192se-dkms
```

After that, reboot your machine, and see if it works. If still doesn't work, try the following on the terminal (this is to bring up, or activate, the network card, in case it is not activated):

```
ifconfig wlan0 up
```


In case you don't have any way to connect to the Internet in Ubuntu, from Windows download the following file (this is the network driver):

[https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb]("https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb")

Copy it to your Ubuntu partition (or a USB drive) and double-click it from Ubuntu to install it. However, the other method is preferred because that way you'll get notifications of any update to the driver.

Well, I hope this solves the wireless card problem.

(By the way, nice machine you have there!)

---

### Post by wombatvvv on 2010-06-03
That worked like a charm!

Thankyou so much for helping me out.

---

