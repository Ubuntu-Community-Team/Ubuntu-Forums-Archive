---
title: "Belkin F5D7000 (Realtek 8185 chipset)"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by Povilas on 2008-03-02
Hello,

I've recently upgraded to a new rig and I'm having some problems with Belkin PCI wireless card.

It's Belkin F5D7000, but looks like there are multiple revisions of this card, each with different chipset. Mine has RTL8185 chipset.

I've managed to get it running with ndiswrapper and net8185.inf (realtech driver, had to associate it with hardware using 'ndiswrapper -a 1799:700f net8185'). However I am experiencing random disconnects. It might work for couple minutes, it might work for couple hours. Then network becomes unreachable. I was unable to find any pattern between disconnects, they seem to be completely random.

On some occassions machine becomes semi-unusable, with ndiswrapper constantly attempting to restart wlan0 and computer freezing for short periods of time every couple seconds. I have to reboot the machine to get it to normal state again. It doesn't happen every time, but it does happen. Again, no pattern found.

lspci reports card as 'Ethernet controller: Belkin Unknown device 700f (rev 20)', pciid is '1799:700f'.

Tried with ndiswrapper 1.45 and 1.52.

---

### Post by ebierly on 2008-03-02
how do you identify the chipset?

---

### Post by Povilas on 2008-03-02
> how does you identify the chipset?
> 
lspci reports card as 'Ethernet controller: Belkin Unknown device 700f (rev 20)', pciid is '1799:700f'.

I've done some adjustments to Linux drivers provided for RTL8185 chipset by realtek (simply added pciid to rtl8185/r8180_core.c) and managed to get network running without ndiswrapper. No disconnects so far, instead I get random network slowdowns (issuing /etc/init.d/networking restart seem to fix that). I am not sure if it's just my crappy (/unsupported) card or is the problem with the OS itself.

---

### Post by ebierly on 2008-03-02
lspci
04:01.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

how do you get the pciid and furthermore resolve that to the chipset?

thanks

---

### Post by Povilas on 2008-03-02
$ lspci
> 
...
05:00.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
...


$ lspci -n (see matching line, comparing by left part, in my case '05:00.0')
> 
05:00.0 0200: **1799:700f** (rev 20)


I've found out that mine uses realtech chipset by trial and error. Try net8185.inf driver with ndiswrapper.

Let me know if you are able to connect using ndiswrapper and if you experience disconnects.

---

### Post by ebierly on 2008-03-02
i removed the card and have confirmed it is a realtek 8185 chipset.

 i followed these instructions earlier and got nowhere 

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/belkin-f5d7000-wireless-card-in-linux-complete-guide-386847/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/belkin-f5d7000-wireless-card-in-linux-complete-guide-386847/)

it installed the driver but did not recognize the hardware.

im inclined to try the linux drivers if i can find them

---

### Post by Povilas on 2008-03-02
First off, remove any other ndiswrapper drivers you have installed, e.g. sudo ndiswrapper -r bcmwl5a

Then download realtek windows xp drivers (don't download unix drivers) from here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

After extracting files from archive, you should have net8185.inf, rtl8185.sys and some other files.

Install realtek driver:
sudo ndiswrapper -i net8185.inf

Make it work with your card:
sudo ndiswrapper -a 1799:700f net8185

Reload ndiswrapper module:
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

See if you have a wireless interface:
iwconfig (should report wlan0 as wireless)

If needed, restart networking:
sudo /etc/init.d/networking restart

If this works and you are able to connect, let me know if you get any random disconnects, like I do.

---

### Post by ebierly on 2008-03-02
iwconfig gets me 

wlan0 IEEE 802.11g EESID:off/any

Mode:Auto Frequency:2.1412 Ghz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:-2147483648 Sensitivity=0/3
RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

but
 sudo /etc/init.d/networking restart
 failed so i changed /etc/network/interfaces to add

auto wlan0
iface wlan0 inet dhcp

but get
No DHCPOFFERS recieved
on restart

very grateful that i got further along

---

### Post by Povilas on 2008-03-02
Since you have interface up, graphical user interface tools should be able to set-up SSID and encryption options.

You're at the point where your hardware was identified and (hopefully) working, all you have to do is to connect to an AP.

---

### Post by ebierly on 2008-03-03
this may be relevant from another thread since i have a wlan0:ava entry from ifconfig

Apparently one of the daemons in the avahi package that comes with Gutsy doesn't like ndiswrapper. For a while after every reboot, my wireless works just fine. However, eventually it stops working. When this happens, everything is reported as normal by ndiswrapper, lspci, iwconfig, etc., except ifconfig reports that a new interface, wlan0:avahi, has been created, that wlan0 (my usual wireless interface) no longer supports IPv4 communication, and the new interface is the only one that supports it.

---

### Post by ebierly on 2008-03-03
btw have you seen this
[http://ubuntuforums.org/showthread.php?t=210958](http://ubuntuforums.org/showthread.php?t=210958)

---

### Post by Povilas on 2008-03-04
> **ebierly said:**
> this may be relevant from another thread since i have a wlan0:ava entry from ifconfig

Apparently one of the daemons in the avahi package that comes with Gutsy doesn't like ndiswrapper. For a while after every reboot, my wireless works just fine. However, eventually it stops working. When this happens, everything is reported as normal by ndiswrapper, lspci, iwconfig, etc., except ifconfig reports that a new interface, wlan0:avahi, has been created, that wlan0 (my usual wireless interface) no longer supports IPv4 communication, and the new interface is the only one that supports it.
That's interesting, I don't think I checked ifconfig after network went down.

Anyway I was using modified RTL official linux drivers and they do work, apart from random slowdowns.

Here's a quick guide:

1. Download UNIX driver from realtek website. ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true))

2. Extract the package, cd into the directory.

3. ./makedrv

4. Open rtl8185/r8180_core.c with text editor

5. Add this near other pciids:
```


        {       /* Belkin F5D7000 */
	        .vendor = PCI_VENDOR_ID_BELKIN,
                .device = 0x700f,
                .subvendor = PCI_ANY_ID,
                .subdevice = PCI_ANY_ID,
                .driver_data = 2,
        },

```

6. cd rtl8185 && make

7. cd ../ && sudo rmmod ndiswrapper

8. You might want to blacklist ndiswrapper module (/etc/modprobe.d/blacklist) or remove it altogether, just to be safe.

9. sudo ./wlan0up

10. (if that didn't connect you) sudo ./wlan0dhcp

---

### Post by ebierly on 2008-03-05
thank you for the step by step

i got a lot of incompatible pointer type and ieee80211 undefined warnings on the make

the ./wlan0up made the card light go on

the ./wlan0dhcp resulted in 

No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
get ip:

assuming the warnings were meaningless i will need to hunt down a dhcp tutorial

---

### Post by Povilas on 2008-03-05
Try 'sudo /etc/init.d/networking restart' a couple of times if ./wlan0dhcp doesn't help.

It's safe to ignore warnings if 'make' output doesn't end with error.

Cheers.

---

### Post by zenosdog on 2008-03-09
One thing that really helped me from the ndiswrapper faq was blacklisting the bcm43xx driver.  I was also getting that additional wlan0:avahi.

From the [FAQ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"):

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

Just remember to restart after blacklisting it.

---

### Post by Povilas on 2008-03-09
Looks like my slowdowns were caused by the router. I've bought myself a Linksys WRT54GL and installed DD-WRT firmware on it ([guide here](http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php)). It's all working beautifully now.

---

