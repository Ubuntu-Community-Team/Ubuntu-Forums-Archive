---
title: "ar5007 wireless problems - have tried ndiswrapper and madwifi"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by esthete23 on 2008-01-11
I've tried ndiswrapper. got the wireless networks to show up after much hassle, but would never connect to one of the networks... even unsecured. i tried madwifi briefly, but couldn't get it to install properly. any help is appreciated if you've dealt with this card before. i've tried many of the suggestions in the forum with no avail. thanks

---

### Post by Rockman4140 on 2008-01-12
I'm in the same boat as you, friend. After dropping security on my router and attempting to connect with WICD I had no luck.

I use WEP so my DS can get online, but since I disabled it and tried with no luck, I figure it wouldn't matter.

It scans for awhile on the network with no luck. After using a battery of Keys with no luck, I went to the default manager. No luck with the keys there, so I switched back to WICD.

Ndiswrapper 1.47
Magic 2.6.22-14-generic SMP mod_unload
WICD 1.3.1

It seems I can't run WICD from the Terminal. If you'd like info dumped, I'd be more than glad to.

---

### Post by styyle14 on 2008-04-01
use network manager and nm-applet, i got mine working, yet wicd still wont work

if you really want to use wicd that badly, if i remember correctly, you need to uninstall networkmanager first, yet it I never got wicd working

it sounds like you need to install madwifi (a patched version is required because ubuntu incorrectly identifies this type of wireless card)

i wrote a guide a little while back that has one solution in it:
[http://ubuntuforums.org/showthread.php?t=699149](http://ubuntuforums.org/showthread.php?t=699149)
yet it appears that a pre-patched version is already available, so i would recommend going to:
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
and reading what they have to say on the matter, or searching the ubuntu forums for the lastest info and guides

---

### Post by kevdog on 2008-04-01
Yes you need the patched wifi driver as explained above for this particular chipset.  Without this special version of the driver things will not work.

---

### Post by formol on 2008-04-01
this may help you :

from [http://ubuntuforums.org/showthread.php?t=527619&page=4](http://ubuntuforums.org/showthread.php?t=527619&page=4)

 Originally Posted by bmartin  View Post
Make sure you use the appropriate version of the drivers for your version of Linux. If you're using a 64-bit version of Linux, you must use 64-bit drivers. You can check this using the following command:
Code:

getconf LONG_BIT

I personally recommend using the wicd program for WiFi connectivity. It boasts built-in WPA support and has been successful where other network connection manager programs have failed.


This chipset showed up on my Acer Aspire 5050-3785. The lspci program spit out the following info:
Code:

Atheros Unknown device 001c (rev 01)

It also has been incorrectly labeled as an AR5006X device, in some cases.

Here is a step by step procedure to install the drivers manually (in case you don't want to use the script I wrote, or if it doesn't work properly). Open a terminal and copy/paste the following lines:

1a. Download the ndiswrapper (v1.4 source code and AR5007EG Windows drivers:
Code:

wget [http://wifix.sourceforge.net/software.php?title=ndiswrapper](http://wifix.sourceforge.net/software.php?title=ndiswrapper)

1b. Download the AR5007EG Windows XP drivers:
If you're using a 32-bit version of Linux, use this command:
Code:

wget [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

For 64-bits of blazing WiFi glory, use this:
Code:

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

2. Extract the archives:
Code:

tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz

3. Ensure you have your kernel headers and the build essential package.
Code:

sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential

4. Blacklist the ath_pci kernel module (it doesn't support our chipset).
Code:

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

5. Compile ndiswrapper:
Code:

pushd ndiswrapper-*/
sudo make uninstall
make
sudo make install
popd

6. Install the Windows drivers (using ndiswrapper):
Code:

pushd */ar5007eg/
sudo ndiswrapper -i net5211.inf
popd

7. Make sure ndiswrapper loads up every time we start Linux:
Code:

sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules

8. Restart your computer.
Code:

sudo init 6

=====
FAQ
=====
Q: Linux seems to see my device now, but it can't see any networks. What can I do now?
A: This frequently happens on built-in devices. There's usually either

    * A switch on your computer somewhere that toggles whether the wireless radio is on or off (BEWARE! Some of these are very unintuitive. The setting that may seem like "on" may be "on" and vice-versa.)
    * A keyboard combination that enables/disables the wireless connection (usually Fn+F2).
    * A setting in the BIOS that needs to be changed. This can be frustrating to track down. The BIOS is the program that loads before your OS. When your computer first boots, there's a key you can press to go into the system setup; look for a wireless setting in there that you can enable.


Q: I can see wireless networks. Why can't connect to any of them?
A: There are a couple options to try here. If you're using WICD to connect and WPA encryption, under preferences, make sure that for WPA Supplicant Driver, you're using WEXT (make sure you've installed WPA_Supplicant). If you're using WEP, try putting your key in "double quotes". If you can't connect to an encrypted network, try removing they key to see if that's the problem. If you're not using WICD, try it out; many people have been successful simply after switching the wireless connection manager program to WICD.

Q: None of this worked. I'm no closer to having my wireless working than I was when I first installed my OS. What's wrong?
A: Try running sudo modprobe ndiswrapper; the program should run silently. If you get any output, there's a problem. If the ndiswrapper,ko file can't be found, run sudo depmod -ae, then try sudo modprobe ndiswrapper again.

If you installed your OS a long time ago, some people have had better success with a fresh install. Try installing the drivers while running from the Live CD.
=====
EDIT: I removed the instructions for using the script. It seemed to not work for anyone other than me. I checked it over several times and couldn't figure out why. The instructions and the script seem to perform the same set of operations.

---

### Post by fissionmailed on 2008-04-01
> **kevdog said:**
> Yes you need the patched wifi driver as explained above for this particular chipset.  Without this special version of the driver things will not work.

Doesn't work with 64 bit comps, I've tried.





I have a question, when you type iwconfig, does a wlan0 show up?

Edit: Is it a AR5007EG?

---

### Post by formol on 2008-04-02
if  i remember well, yes.  my laptop is on repair now, motherboard is dead... at least it was under garanty....

---

### Post by fissionmailed on 2008-04-02
> **formol said:**
> if  i remember well, yes.  my laptop is on repair now, motherboard is dead... at least it was under garanty....

I know to get mine(AR5007EG) to work I had to use Ndiswrapper 1.44 or 1.45rc1 and add my MAC address in /etc/network/interfaces and then I could connect to the internet, but I didn't use a GUI to connect.

---

### Post by formol on 2008-04-02
really, it was working with madwifi? great!  i had the impress that ndiswrapper was sometime unstable, and many people told me to use madwifi and not ndiswrapper...

i will probably have to re-install all my OS when i will have my laptop back.  those guys will probably re-install vista...

do you know if the hardware support (for wifi in particular) will be better in Ubuntu 8.04?

---

### Post by kevdog on 2008-04-02
Yes you are correct -- the patched madwifi driver is for the 32bit OS, and not 64 bit.  Sorry to mislead anyone.

---

### Post by fissionmailed on 2008-04-02
> **formol said:**
> really, it was working with madwifi? great!  i had the impress that ndiswrapper was sometime unstable, and many people told me to use madwifi and not ndiswrapper...

i will probably have to re-install all my OS when i will have my laptop back.  those guys will probably re-install vista...

do you know if the hardware support (for wifi in particular) will be better in Ubuntu 8.04?

oohh no no no, I use ndiswrapper.  It's run perfectly for me.  I've personally have had good luck with it.



Kevdog:  I even installed a 32-bit OS on my laptop and with the patched madwifi and I couldn't get it to work. Of course I could be comptarded, but it didn't work for me.

---

