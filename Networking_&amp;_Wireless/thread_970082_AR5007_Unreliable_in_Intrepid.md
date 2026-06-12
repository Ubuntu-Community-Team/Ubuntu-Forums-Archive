---
title: "AR5007 Unreliable in Intrepid"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Quartz25 on 2008-11-03
Hello again, everyone.  I am one of the unlucky folks who's stuck with an AR5007 chipset.  I had mine working perfectly with Gutsy and Hardy using the Mad-Wifi unofficial patch (good ol' [Ticket 1679]("http://madwifi-project.org/ticket/1679")), then once I got to Intrepid, the patch stopped compiling for the kernel.

After this compiler fiasco, I checked back on the ticket to see that it had been superseded by [Ticket 1192]("http://madwifi-project.org/ticket/1192"), the one that recommends you use the forked subversion branch, so I did just that.  It compiled and installed correctly, but after connecting to my home network, the connection slowed to a crawl.  I went directly to ethernet to check, and even tested the Wi-Fi with my iPod Touch, but it was definitely the AR5007 driver that was the problem.

I went back to the forums to find the [linux-backports-modules-intrepid]("http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid") package.  I blacklisted ath_hal and ath_pci and enabled ath5k.  The same problem persists: the connection is too darn slow (on the order of 2 KiB/s, according to System Monitor).

Any recommendations?

---

### Post by highenergy on 2008-11-04
I have same chipset but I am one of those lucky ones. I made it work under kubuntu 8.04. In order to that I first activated restricted drivers of atheros but not restricted hal. Then downloaded the latest hal as mentioned at the ticket 1192 ([http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)). Compiled it and installed it. Then a restart of the system needed. That's all.

One last thing. If there are ubuntu packagers around here reading this thread, please update ubuntu restricted drivers of atheros. Because there is a new ath_hal module.

---

### Post by JairunCaloth on 2008-11-04
I have this same chipset, compiling ath_hal worked perfectly. Just untar the archive, cd in, make then make install. After that's all done modprobe ath_pci and you should be good to go.

---

### Post by AklBlue on 2008-11-04
After battling with the same problem for 2 days I FINALLY got it working, and its going great..

Firstly, what didn't work is the default ath5k driver, or the ath_pci from the backports workaround. The latest stable HAL from madwifi also didn't work. I was seeing the wlans but it either would connect and then go painfully slow, or it wouldn't connect.

What did work for me was.
1. Fresh install. No post-install updates whatsoever.
2. Disable the default driver from "Hardware Drivers".
3. Download and install build-essential package.
4. Download and install compat-wireless package, reboot. (didn't work at this point)
5. Disable the 5xxx driver created from the package above.
6. Download and install madwifi HAL TESTING driver. 
[http://snapshots.madwifi-project.org/madwifi-hal-testing/madwifi-hal-testing-r3872-20081104.tar.gz]("http://snapshots.madwifi-project.org/madwifi-hal-testing/madwifi-hal-testing-r3872-20081104.tar.gz")
7. Reboot
8. Success at last !!!!! 

I find that the signal strength is quite weak, but it connects and I get good speeds.  Problem is after so much hassle I'm afraid to install the latest kernel update..

EDIT: I notice now that if I go back into Hardware Drivers, the "Support for Atheros 802.11..." driver is enabled and in use... all very strange.. I can only assume that the madwifi package added something that wasn't working with the default driver.

---

### Post by eks on 2008-11-04
For me, on a HP Pavilion dv6000, the backports modules [are working fine]("http://ubuntuforums.org/showthread.php?t=967855"). :-s

---

### Post by Quartz25 on 2008-11-05
Okay, I tried uninstalling my download of Mad-Wifi 0.10.5.6 from Issue 1192 and using the testing version (as suggested by AklBlue), but I'm still getting speeds of about 2 KiB/s.  Backports does not work for me, either.  If it helps anyone, I'm using a Sony VAIO Notebook VGN-NR220E with the AR5007EG.

---

### Post by rfsquared on 2008-11-06
Hey, I need some help too.

I'm running the AR x242 chipset (that's the same as the 5007, no?  I have the 5x drivers so yeah...).  The wireless is fast when it works, but it tends to have problems when I switch areas.  For example, when I'm at my university it will work periodically and then stop, and then when I come back home it won't recognize my wifi router at all (or I'll be sitting like 5 feet away from my router and it tells me I have a 9% signal).  I usually end up having to restart the whole machine for it to work again, and that doesn't always help either.  Anyway, any help would be great!

---

### Post by Quartz25 on 2008-11-12
Bump

---

### Post by rynyeager on 2008-11-13
I have acer aspire 7520 AMD64. Have tried every step by step i could find. NOTHING IS WORKING!!! please help!!!!!:confused:


now running 8.10

---

### Post by enigmageek on 2008-11-13
Hello all. I find using the latest madwifi-hal works good but needs a little tweaking. First I disabled both the support for atheros wireless cards and hal support in restricted drivers. In /etc/modprobe.d/blacklist add ath5k and ath9k to the end, each in it's own line. Compile the madwifi-hal driver, version 0.10.5.6 worked the best for me. For wireless speed type gksu gedit /etc/init.d/networking and just below the word "start" add line 
iwconfig ath0 rate 54M

save the file. All file editing must be done as root so if you're using Gnome the command in Terminal is "gksu gedit /location/folder/filename" without parentheses.For KDE kdesu kwrite.

I compiled the 2.6.27 kernel in Hardy so in order for my modules, wireless, virtualbox, etc, to rebuild automatically I installed DKMS.I have the madwifi-hal dkms.conf if anyone needs it. This way when you upgrade the kernel you won't keep losing wireless. Also I use scripts to restart the network, set the speed, and reconnect upon resume from suspend. Hope this helps.
Regards, Ray
Ubuntu Hardy 8.0.4.1-2.6.27.5
Windows Vista and XP via VirtualBox

---

### Post by skaboss on 2008-11-15
Hello guys, i own an Acer 7520G. Wifi worked as a charm with Hardy and the patched version of Madwifi.
However, i got stuck several days trying to make work the so called "out of the box" Intrepid's atheros driver.
I tried everything i found in this forum (linux-backports-modules-intrepid-generic after a fresh install, and so on).
Nothing worked and i even thought about moving to another distro !
After all, i simply downloaded the windows driver for my card, installed ndiswrapper, and i can tell my wifi connection nerver worked as good as today !
So if you are like me, and madwifi's patched patches drive you nuts, have a look at ndiswrapper  :wink:

---

### Post by acreech on 2008-12-03
[http://ubuntuforums.org/showthread.php?p=6201697#post6201697]("http://ubuntuforums.org/showthread.php?p=6201697#post6201697")

If you have not got this figured out yet. This post is how I get my wireless card to work. Hope it helps.

---

