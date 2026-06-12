---
title: "DWL-650 + ubuntu 7.04 + IBM P3 laptop"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by xct9-3 on 2007-08-12
I looked through a few other threads before posting this but couldn't really find anyone with the same situation.  I tried following the steps listed here,
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#driver](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#driver) and through this realized ubuntu did recognize that the device exists, but I cannot seem to install a driver.  I looked around online and found it's Realtek based but has a TI ACX100 chipset.  I tried a few drivers that I couldn't figure out how to install then resorted to ndiswrapper.

After extracting ndiswrapper I tried the command "make uninstall" after changing directory to the newly extracted folder and it returned permission denied and instructed to run uninstall as many times as necessary until no "removing" messages appear below.  Currently one appears below saying I do not have permission.  I tried to run this command as super, while trying to install super I received the message "E: Couldn't find package super".

---

### Post by xct9-3 on 2007-08-12
bumping, I think if I could get authority to move further in the install I would have a chance.  Odd that I can't install the super command.

---

### Post by tturrisi on 2007-08-13
What version DWL-650 do you have?
You can tell the version # by looking at the back of the card where it says:
H/W: xx  F/W: xx
H/W = hard ware
F/W = firm ware

---

### Post by xct9-3 on 2007-08-13
I can't seem to find that on the card, here's everything displayed.

---

### Post by tturrisi on 2007-08-14
Your card is a DWL-650M.  It cannot be Realtek basede AND have an ACX chipset!

DWL-650 Revision M

# The DWL-650 revM has a completely rectangular shape, similar to the DWL-650K1 and L1.
# On the back of the body is a label with two sets of bar codes. The hardware version is written under the second set of bar codes and will be listed as V.M1.

Ther card has a Realtek chipset & in linux needs the RTL8180 driver.  This driver "may" be blacklisted in Ubuntu, I'm not sure cause I don't use Ubuntu, I use straight Debian.
[http://sourceforge.net/projects/rtl8180-sa2400](http://sourceforge.net/projects/rtl8180-sa2400)

I have a card that uses that driver, I got it installed like this:
Open a root terminal and do
```
apt-get install build-essential
apt-get install linux-headers-`uname -r`
cd /usr/src
wget http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz
tar -xvzf rtl8180-0.21.tar.gz
make && make install
depmod -a
modprobe r8180
```

You can also use a patched driver so thye card works with aircrack-ng:
```
wget http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz
wget http://patches.aircrack-ng.org/rtl8180-0.21v2.patch
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180
```

Windows driver here:
[http://support.dlink.com/products/view.asp?productid=DWL%2D650M](http://support.dlink.com/products/view.asp?productid=DWL%2D650M)

---

### Post by xct9-3 on 2007-08-14
Thank you for the reply, hopefully it will work out well.

When I try the first command, it states "E:  Couldn't find package build-essential".  This is the same thing that happened when I tried to install the super command, am I missing needed files on my HD?  If so how can I get them?

Thanks

---

### Post by tturrisi on 2007-08-15
Uninstall ndiswrapper using Synaptic.

Open a Root terminal:  Accessories > Terminal (as root) + password
or
use sudo:
sudo apt-get install build-essential

---

### Post by xct9-3 on 2007-08-15
I used sudo and typed in "sudo apt-get install build essential", after I input my password it returned,

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build essential

This is similar to what happened when I tried to install the super command, which makes me believe I'm missing necessary files on my HD.

---

### Post by xct9-3 on 2007-08-16
I got past my previous problem and realized it was because I was not fully upgraded and was not connected to the internet at any point on that machine.  I downloaded the install files and ran attempted to run the 2nd code posted with the patch.  Everything worked well after a few tries and I got to "make && make install".  It stated I did not have the permissions necessary so I ran the code with sudo in front yet still did not have permission, here's the entire response if that helps,

> bill@Garage:~/rtl8180-0.21$ sudo make && make install
Password:
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/bill/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 4 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/bill/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 4 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
mkdir -p /lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless
mkdir -p /lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/alg
mkdir: cannot create directory `/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/alg': Permission denied
make: *** [install] Error 1
bill@Garage:~/rtl8180-0.21$ 





Thanks for everyones help so far, this has been frustrating at times but I am enjoying the learning experience.  I think I'll add ubuntu in a dual boot setup to my main pc as well.

---

### Post by xct9-3 on 2007-08-17
So this has turned into a classic can't find the router problem.  I installed ndiswrapper through the GUI and the device is now recognized as having a driver and enabled/ the active light is blinking on the card.  However no matter where I place my computer it cannot find my unencrypted, open network.  This computer is using the wireless connection to edit this post so I know the router is not the problem.  The only thing I can think of is that because I was halfway through the install of the linux driver, that is some how hurting me.  But anyways if anyone has any ideas please post.  I know it's annoying to deal with newbs (I was active on overclocking forums for awhile) but I've tried all the self help/ guides I can find.

Thanks!

---

