---
title: "Lubuntu (14.04) Internet Connection Always Dies And I Can't Get It Back"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by Andrew_Jay on 2014-04-23
Hey,

I'm just having a weird problem with Lubuntu 14.04 and I'm wondering if any of you can help me with it.

Basically the problem is this:

Whenever I do a fresh install and I'm running the operating system off the USB or DVD, I will be able to connect to the internet just fine. The problem is, the connection always dies after a while and I can't seem to get it back. The only way I've been able to figure out to start connecting to the internet on Lubuntu again after the connection dies, is to do a fresh install... But again, give it a day or so and the connection will just die again and not be fixable (at least not by someone with my level of experience).

Few things...

1. When I click on the little battery button it says "adapter is online." Is this referring to the network adapter?

2. Nevertheless, the internet connection seems genuinely dead... Not only can I not use Firefox, I also can't download apps from the Lubuntu software center.

3. I've followed all the tutorials I can find that involve editing the network connection... None of these fix the problem.

4. I've tried pinging various IP addresses... nada.

Does anybody know what might be the case here?

Sorry if this seems like I'm asking a question that's been asked a billion times but I've googled this and walked through the solutions that worked for many other people and I can tell you with 100% certainty they're not working for me. 

I'd also stress that my problem is a little different: I'm **initially** able to connect to the internet... It's just that the connection, uh, "goes away," and I know it's not something with the router because my Windows 7 Desktop works fine.

---

### Post by praseodym on 2014-04-23
Hi,

did you deactivate IPv6 in the network-manager applet? Please show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by Andrew_Jay on 2014-04-23
OK...

I just ran those in terminal. I can't copy and paste the full thing because my Lubuntu box is not online, but here's basically what came up...

1. [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net showed...
[/FONT][/COLOR]
Reltek Semiconductor Co., ltd. RTL8101E/RTL Wireless Network Adapter [10ec:8179]

2.  [COLOR=#000000][FONT=Ubuntu Mono]lsusb showed...

[/FONT][/COLOR]Bus 002 Device 003: ID 10fl:1a52 Importek


Bus 002 Device 002: ID 0bda:0129 Rektek Semiconductor corp RTS5129

3. lsmod showed a whole bunch of stuff... I can't really pick out which information among what was posted here is most relevant and I can't type it out by hand it would take me all day.

4. iwconfig showed...

eth0 no wireless extensions

lo no wireless extensions

wlan0 IEEE 802.11bgn ESSID: "(insert my network ID here)"

4. Sudo iwlist scan showed a ton of stuff... Again there's too much here for me to type out by hand. The most important seems to be Bit rates, which seem to suggest that I'm connected or able to download something but again, still can't use firefox or download center.

I will try deactivating IPv6

---

### Post by praseodym on 2014-04-23
Please try his driver:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
echo "options rtl8188ee ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8188ee.conf
sudo cp -r firmware/* /lib/firmware
```
Change the encryption mode to pure WPA2-AES (CCMP), nothing with "TKIP". Check the router manual. After that, reboot.

---

### Post by Andrew_Jay on 2014-04-23
I'd need to hook it up to an eternet cable to do that right?

---

### Post by Andrew_Jay on 2014-04-23
OK so, I managed to make a LITTLE bit of progress on this, though maybe not much.

Using the advice at the link below...

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

... I was always to get a network manager applet showing in the lower right corner of my screen.

However in some ways, this only compounds the mystery... Why do firefox and download center STILL not work, when I'm allegedly connected to the internet (it's saying the connection is at 70%)?

I am in an apartment on wifi and do not have access to an ethernet cable.

Are you sure this problem requires a new driver as a solution?

Like I said, firefox was working fine **for a short time* *... It's just that it stopped working randomly after a few hours.

Due to the lack of ethernet I may end up having to try a more wifi-friendly distro... Can anyone recommend one that's known for having no wifi issues?

---

### Post by Andrew_Jay on 2014-04-23
Here's a comment somebody said on another forum...

"You understand how the packet management **** works and where you have to go to download the correct broadcom package(99% chance you need a Broadcom wireless package that doesnt come with Ubuntu by default)?"

Anybody understand what he means by this? From some of my efforts I have indeed determined that my driver is called "realtek" and not "broadcom," so maybe that's part of the problem?

---

### Post by praseodym on 2014-04-24
You hav a Realtek chipset, so no need for Broadcom drivers ;)

---

### Post by Patrick_McCabe on 2014-04-27
> **praseodym said:**
> Please try his driver:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
echo "options rtl8188ee ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8188ee.conf
sudo cp -r firmware/* /lib/firmware
```
Change the encryption mode to pure WPA2-AES (CCMP), nothing with "TKIP". Check the router manual. After that, reboot.

I spent 3 days trying everything I could think of and everything I could find to get my wifi to work. Your solution solved my problem. Thank you so much.

Realtek RTL8188EE wireless adaptor, Toshiba satellite S55.

---

