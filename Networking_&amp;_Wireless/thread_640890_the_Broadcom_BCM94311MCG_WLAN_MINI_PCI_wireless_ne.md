---
title: "the Broadcom BCM94311MCG WLAN MINI PCI wireless network"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by mmichalik on 2007-12-14
Hi everyone,

Just wanted to let you know that I received my new Compaq Presario C700 laptop today.  7.10 went on with only one hitch.

The laptop has the Broadcom BCM94311MCG WLAN MINI PCI wireless network card in it.  I found a great website that explains step-by-step instructions on how to install the ndiswrapper for it.

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

It worked the first time for me, with one variant.  Instead of using the wget command to get the ndiswrapper file, I had to use the URL via the browser and just download the file to the appropriate location.  Then, I picked up with the next step on the command line.

Good luck!

---

### Post by Coward on 2007-12-14
I have this wireless card and have installed it so that ndiswrapper detects the hardware. wlan0, however, is not setup for me. Since I think this is controlled by the file /etc/network/interfaces, could you post the contents of the file as it is on your computer? I would like to copy at least part of it. Thanks.

---

### Post by mmichalik on 2007-12-14
Here you go but, there's not much to it.

My other Ubuntu boxes have interface files that are a lot more complex then this.

auto lo
iface lo inet loopback
iface eth0 inet dhcp
iface eth1 inet dhcp
wireless-key xxxxxxxxxxxxxxxxx
wireless-essid xxxxxxxxxxxxxxx
auto eth1
iface wlan0 inet dhcp
wireless-key xxxxxxxxxxxxxxxxx
wireless-essid xxxxxxxxxxxxxxx
auto wlan0


My suggestion would be to follow that HowTO, even removing the existing ndis stuff as he suggests.  It worked perfect for me. (granted, I just pulled my laptop out of the box and put the Ubuntu disk in it but....)

Good Luck!

---

### Post by gfd_2 on 2007-12-18
i'll be home in a couple of hours and will give the how-to a shot.  Thanks for the suggestions.

---

### Post by mmichalik on 2007-12-18
Good luck!

---

### Post by gfd_2 on 2007-12-18
alrighty then!!! the blue light is back... here's what I did: 

First step, you must uninstall ndiswrapper & bcm43xx-fwcutter
 1.sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9sudo apt-get remove bcm43xx-fwcutter Add bcm43xx to the /etc/modprobe.d/blacklist file 
2.sudo gedit /etc/modprobe.d/blacklistadd this line blacklist bcm43xx and save the file.
3.Reboot 
4.Download driver for BCM94311MCG wlan mini-PCI here ( if this link expire I can't help you... this came from another site)
5.tar -xzvf WLANBroadcom.tar.gz
6.) move the folder WLANBroadcom to your home directory using the next step.
7.mv WLANBroadcom/ /home/yourname/ 
8.Install ndiswrapper from source : 
a.)sudo apt-get update
b.) sudo apt-get install build-essential 
c.) sudo apt-get install linux-headers-`uname -r`
d.) sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/buildmkdir -p ~/bcm43xx/ndiswrapper
9.) cd ~/bcm43xx/ndiswrappersudo 
10.) wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz)
11.) tar xvzf ndiswrapper-1.49.tar.gz
12.) cd ndiswrapper*make distcleanmakesudo make install
13).Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper.
14.) cd /home/yourname/WLANBroadcom/
15.) sudo ndiswrapper -i bcmwl5.infndiswrapper -l 
16.) sudo gedit /etc/modulesadd this line ndiswrapper
17.) sudo modprobe ndiswrapper
18.) sudo ndiswrapper -m 
19.) reboot

After rebooting  the wifi light is blue and I see my network being advertized.  however... I can't connect.  If I make any modifications to the /etc/network/interfaces file I loose <my network name> and have Manual Configuration in Network Manager.  When I loose the essid by checking "enable roaming" in N-M I can see < my network name>  

lspci = 02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02).

iwconfig =
lo no wireless extension
eth0 no wireless extention
wlan0 IEEE 802.11g ESSID: off/ any
mode managed Frequency: 2.462 Ghz Access Point: Not-Associated Bit Rate: 54Mb/s TX-Power: 32dBm RtS thr: 2347 B Fragment thr 2346 B Power Management: off Link Quality: 0 Signal Level:0 Noise Level:0 RX invalide nwid:0 RX invalid crypt:0 Rx invalid frag:0 TX excessive retries: 0 Invalid misc: 0 Missed becon: 0

dmesg:
wlan0: ethernet device 00:1a:73:d7:d6:fe using NDIS driver: bcmwl5, version ox4640f05, NDIS version 0×501, vendor” ‘NDIS Network Adaptor” 14E4:4311.5.conf
wlan0: encryption modes support WEP, TKIP with WPA, WPA2, WPA2 PSK; AES/CCMP with WPA, WPA2, WAP2PSK.
registered new interface driver ndispwrapper
blah
blah
blah
eth0: link up
eth0: link up
Faliure registering capabilites wtih primary seciruty module.
blah
blah
blah
eth0: no IPv6 routers present
ADDRCONF(NETDEV_UP): wlan0: link is not ready
r8169: etho: link up
eth0: no IPv6 routers present

Any advice would be GREATLY appreciated… thanks…

---

### Post by mmichalik on 2007-12-19
under step 8 - C and D, did you replace 'uname -r' with the appropriate information?  (i'm assuming you did. i'm just trying to figure out where you are)

---

### Post by jadjay on 2007-12-20
gfd_2 i have the exact same problem than you...

I saw the others wlan network next to me, but even if one is not protected i can't connect, i don't know why... And thus i can't connect to my...

But this solution has the same result as using ubuntu's ndiswrapper, i thought it was a "special" bcmwl5.inf but it's just one matching the device.

So up! If anyone has got a damned tip to help us thanks a lot.

---

### Post by Presto123 on 2007-12-20
Wow...all I got to say is that I never expected so many to have problems with the Compaq on 7.10. All I did was get it from Restricted Drivers Manager and let it download the driver from the net.

---

### Post by gfd_2 on 2007-12-20
> **mmichalik said:**
> under step 8 - C and D, did you replace 'uname -r' with the appropriate information?  (i'm assuming you did. i'm just trying to figure out where you are)


mmichalik... no I used the ` mark (next to the letter one) .... I thought this would pull in the appropriate info.... am I wrong in thinking that?    should I be manually entering the entire version number?

Thanks

---

### Post by igknighted on 2007-12-20
> **gfd_2 said:**
> mmichalik... no I used the ` mark (next to the letter one) .... I thought this would pull in the appropriate info.... am I wrong in thinking that?    should I be manually entering the entire version number?

Thanks

No, you are correct.  the `marks run the embedded command.

---

### Post by gfd_2 on 2007-12-20
> **igknighted said:**
> No, you are correct.  the `marks run the embedded command.

whew!    Glad to hear it... otherwise I'd have wasted 4 days for nothing....

---

### Post by mmichalik on 2007-12-20
yes, at the command line (before you do anything) just type in the command uname -r.  Put that information in it's proper place, without the ' marks on either side, when the HowTo calls for 'uname -r'.

ex:

from my command line, when I type uname -r I get:

 2.6.22-14-generic.

on your list, 8 c it reads c.) sudo apt-get install linux-headers-`uname -r`

but when you execute it, it should read:

sudo apt-get install linux-headers-2.6.22-14-generic  (or what ever your uname -r information is)

Also, make sure that everything is executed in sequence.  Your list has a couple of lines that look like you ran them at the same time.

ex:

Line 1 reads:

1.sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9sudo apt-get remove bcm43xx-fwcutter Add bcm43xx to the /etc/modprobe.d/blacklist file

and it should read like:

1     sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
1.a  sudo apt-get remove bcm43xx-fwcutter
1.b  sudo vim bcm43xx to the /etc/modprobe.d/blacklist
      (1.b opens a text editor, you need to add the following:
            blacklist bcm43xx
       to the bottom of the file and save it.  Then move on to the next step)

It may look confusing on the webpage HowTo but, just take your time and execute each step and it will work out.

igknighted is correct but, the example above should help eliminate any confusion.

---

### Post by gfd_2 on 2007-12-20
> **mmichalik said:**
> yes, at the command line (before you do anything) just type in the command uname -r.  Put that information in it's proper place, without the ' marks on either side, when the HowTo calls for 'uname -r'.

ex:

from my command line, when I type uname -r I get:

 2.6.22-14-generic.

on your list, 8 c it reads c.) sudo apt-get install linux-headers-`uname -r`

but when you execute it, it should read:

sudo apt-get install linux-headers-2.6.22-14-generic  (or what ever your uname -r information is)

Also, make sure that everything is executed in sequence.  Your list has a couple of lines that look like you ran them at the same time.

ex:

Line 1 reads:

1.sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9sudo apt-get remove bcm43xx-fwcutter Add bcm43xx to the /etc/modprobe.d/blacklist file

and it should read like:

1     sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
1.a  sudo apt-get remove bcm43xx-fwcutter
1.b  sudo vim bcm43xx to the /etc/modprobe.d/blacklist
      (1.b opens a text editor, you need to add the following:
            blacklist bcm43xx
       to the bottom of the file and save it.  Then move on to the next step)

It may look confusing on the webpage HowTo but, just take your time and execute each step and it will work out.

igknighted is correct but, the example above should help eliminate any confusion.

OK... I'm going to give it another try with a clean reinstall.  One question.... after running through the steps I see wlan0 as being recognized while other folks seem to display ath0 as their wireless card... what might cause that? 

Thanks again...

---

### Post by mmichalik on 2007-12-20
mine is wlan0 as well. 

Not sure why it comes up differently.

---

### Post by |{urse on 2008-04-14
what causes ath0 is an atheros chipset.

---

### Post by mmichalik on 2008-05-11
In Hardy, this all works but, before the final reboot, you also need to run the following:

echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local



Thanks to JLANDAW for that little bit

---

### Post by afkun on 2008-05-13
This [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) posted by mmichalik and adding this:

echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local

worked perfectly for me. I'm on a HP dv2410us with the bcm94311, and this guide is what it took. I restarted before reading that last bit of code and nothing worked, but when I added that and then restarted, perfect. Wireless works just fine now.

---

### Post by Bob Stine on 2008-07-20
The links to the driver downloads are at [http://invaleed.wordpress.com/2007/1...ci-ubuntu-710/](http://invaleed.wordpress.com/2007/1...ci-ubuntu-710/)

---

