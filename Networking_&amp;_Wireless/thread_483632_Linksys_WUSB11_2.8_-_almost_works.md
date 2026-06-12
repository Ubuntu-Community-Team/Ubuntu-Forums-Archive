---
title: "Linksys WUSB11 2.8 - almost works"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by brian.johnson on 2007-06-24
OS = Feisty Fawn using 2.6.20-16 kernel
Wireless Card = Linksys WUSB11 version 2.8 with an Atmel AT76C505 chipset - this I know for sure, I opened up the adapter and looked.
PC = Fujitsu C4230 Lifbook, AMD k6-2 450, 192 MB RAM, no working CD-ROM, ethernet over PCMCIA that DOES work (out of the box, BTW)

With no CD-ROM I had to do a network install of Ubuntu. I chose to install install Feisty, regretfully in hindsight, and so had to download a copy of GRUB for DOS (the notebook was running Windows 98) and hook it into the config.sys file and copy over a couple of install files. Reboot, I kick into the GRUB bootloader, install pops up and works flawlessly. Feeling pretty happy, I decide to give the wireless a go, after all the idea is to edit docs and surf the internet without having to be tethered to my basement router. I've used the WUSB11 before to great success in Linspire 4.5 using ndiswrapper. I figured I might have to resort to the same in Ubuntu, but was pleasantly surprised to discover that the card was detected as a wireless lan adapter, wlan0, and the handy little network manager utility  allowed me to enter my ssid and attempt to connect. Even better, it picked up an IP and connected- for about 20 seconds. I could not coax the adapter into reconnecting without unplugging it and trying again. Same result. I figure it might be the driver so I lurked some threads and found a few people had luck with the berlios.de driver.

I attempted to compile the driver but received error config.h not found errors after running "sudo make". Tried compiling the driver at atmelwlandriver.sourceforge.net, exact same error. Fine. Time for the ndiswrapper. I installed the packages using synaptic, copied the windows drivers to the laptop with a floppy, and ran sudo ndiswrapper -i neusb.inf

Plug in the USB, run sudo ndiswrapper -l , the device is listed with an alternate driver at76 listed. I assume at76 is the default drive that half asses worked. I attempt to connect- no dice, can't even pick up an IP now.
Even by running sudo dhclient wlan0.

Getting kinda pissed now. Break out my other USB wireless card, some generic piece of crap that happens to use the exact same atmel chipset (yes I opened it too and checked) and try that. Same diff. It's detected and comes up as wlan0, but I can't get and IP. Fine.

Give up on ndiswrapper, the graphical interface won't properly install the .inf file and when I run ndiswrapper -a xxxx:xxxx [driver name] (where xxxx:xxxx is the device id from lsusb and driver name ts the name of the windows driver from the linksys cd and the generic device cd) and I get "file already exists, driver may not be installed properly" errors. I remove the windows drivers using sudo ndiswrapper -r [name of driver]

I go back to compiling some alternate drivers. I figured I'd start by unistalling the at76 driver. So I so a search for at76 in synaptic... it comes up with the 0.14 beta version of the berlios.de driver as an installable package. I give that a shot. Same result. Device is detected as wlan0, but I can't keep a connection to the network for over 15 seconds. I fall back to compiling a driver. I go with the driver on [http://atmelwlandriver.sourceforge.net/news.html](http://atmelwlandriver.sourceforge.net/news.html). Figure the config.h does not exist error might be a clue. I do some research- turns out that config.h was replaced by autoconf.h. a fer kernel versions ago. I do a find and replace in all the .c files in the package. The next error is for linux_fs.h - turns out that file no longer exists so I remove the offending line of code. Next, I get an error WORK_INIT is being sent three arguments instead of 2. sudo make, sudo make install - no errors off we go. At this point I figure I might be getting some driver confilcts. With the card connected I run lsmod and get the names of the drivers associated with the device. I edit the blacklist file under /etc/modprobe.h and blacklist the original at76 driver and the beta driver from berlios.de. Reboot, plug in the device, now I can;t even get an IP at all. When I disconnect the device I am no longer able to input text from the keyboard. Fun. Reboot, blacklist all three drivers and try ndiswrapper again.

I can install the windows drivers, but when I connect the device it no longer detected at all. Crap.

How does one go about installing an older distro? Dapper might be a good choice based on what I've read, but I'm not sure how to downgrade if that is even possible. There are a few threads on the topic but they are fraught with apparent disinformation. So I guess I could install from scratch, but no CD-ROM drive... or I could buy a new card... if there was a card consistently known to work in feisty... or buy I CD_ROM drive... meh...

Thoughts? Suggestions? Why would the connection drop after 15 seconds? i forgot to mention this- I did try uninstalling the network manager app, I found a thread suggesting that it might be causing the problem. Not in my case, the connection consistently drops after 15-20 seconds.

Here's a question that might be easier to answer- how do I uninstall the drivers I compiled and installed?

---

### Post by kevdog on 2007-06-24
Sounds like you really know what you are doing.  I know you tried ndiswrapper, but first are you sure you installed it properly (ie not from synaptic but from compiling it from source)?  ndiswrapper -v should give you a clue.  Second, when you tried to install the driver into ndiswrapper, did you blacklist the alternate driver??
Did you check /etc/iftab to make sure your interface name (wlan0) was associated with your MAC address?

Just a few ideas

---

### Post by brian.johnson on 2007-06-25
To the first-

I may have to try a manual install. The packages thru synaptic don;t seem to be working quite right. When I "add" the driver, nothing appears in the window listing the installed drivers. When I add the same driver again it tells me "Driver: driver is already installed", and since it does not list the driver I can;t remove the driver from the ndisgtk screen. Lovely

ndiswrapper -v yields "utils Error: no version specified! driver modifno: could not open ndiswrapper: No such device"

That's not right.

To the second-

Yes, eventually. It took a duh moment yesterday, but I did blacklist the three drivers in order to test ndswrapper.


To the third -
Not yet. Forgot about iftab. I've been away from Linux too long, my brain has been soothed into a drone-like laziness that only WindowsXP can provide.

Unblacklisted the default at76_usb driver, plugged in the adapter, ran ifconig and noted the mac of wlan0. 

sudo gedit etc/iftab yields:
"eth0 mac (mac address of my PCMCIA network card, not the wifi adapter) arp 1"

That's it. Seems kind of skimpy compared to the iftab(5) man page I foundhttp://www.die.net/doc/linux/man/man5/iftab.5.html

Also, [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/102336](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/102336)  "For feisty+1 we plan to switch to using the static device name rules file, rather than iftab." hmmm...


=====



Found this [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

walked thru section 4 - no errors, pretty easy. Compiled the ndiswrapper 1.47 source without a hitch. Checked my blacklist, made sure all the at76* drivers were blacklisted. Rebooted. Install the windows drivers from the linksys CD sudo ndiswrapper -i netusb.inf, looks good, plug in the adapter- it's not detected. Can't find it in lsusb. Run ndiswrapper -l, "netusb: driver installed" but no device listed as being connected. Event tried the latest Windows drivers from the linksys site. Crap.

---

### Post by kevdog on 2007-06-25
Dont worry about the iftab file.  Its only a problem if the MAC address of your card is listed there with another interface name such as eth0,eth1.

When you reinstalled driver in section 4 - did you reload the kernel driver (Im not sure if this will help but something to try)
sudo modprobe -r ndiswrapper
sudo modprobe -i ndiswrapper

After the above did you check dmesg to see if there was an error?
Did you set the module to load at boot?? -- sudo modprobe -m

What is your /etc/network/interfaces file?? There should be an entry for wlan0
auto wlan0
... ..... wlan0 dhcp (sorry cant remember the exact syntax, its just like all the others except for the wlan0 part.

Id reboot at this step, however just things to help you troubleshoot:
iwlist wlan0 scanning (can you see your router?? Make sure no encryption,MAC filtering on initially)
ifconfig (is wlan0 even listed)
ifconfig down wlan0
ifconfig up wlan0
sudo /etc/init.d/networking restart  (I think this basically does what the other two commands do above)
sudo /etc/init.d/dbus restart (do this after making changes and dont want to reboot, and above command doesnt work)
check dmesg after reboot to see if you find any errors.

Crap out of ideas at this point!

---

### Post by kevdog on 2007-06-25
Is this your card?

   1.
      Card: Linksys WUSB11v2.5, 802.11b, USB 1.1

    *
      usbid: 066b:2212
    *
      Chipset: prism2 (Atmel?)
    *
      Driver: Linksys Windows XP driver from [ftp://ftp.linksys.com/pub/network/wusb11v25.zip](ftp://ftp.linksys.com/pub/network/wusb11v25.zip). Install with lswlusb.inf
    *
      Other: Works without any problems on SUSE 10.1 - Linux 2.6.16.13.
    *
      Note: FTP link above always failed with 426 Failure writing network stream. Alternate download location is [http://members.driverguide.com/driver/detail.php?driverid=97867&action=summary](http://members.driverguide.com/driver/detail.php?driverid=97867&action=summary). (I haven’t installed it yet, but I’ll update once I do.)

If it is did you blacklist the prism drivers????

---

### Post by brian.johnson on 2007-06-25
It is...

1.
Card: Linksys WUSB11v2.8, 802.11b, USB 1.1

*
usbid: 1915:2233
*
Chipset: Atmel at76c505 ( I looked )

[IMG]http://jamboree.ultrasciencelabs.com/cropped.jpg[/IMG]

*
Driver: Linksys Windows XP driver from linksys website WUSB11-v2.8_dr.zip. Install with netusb.inf
*
Other: Get your hands off me, you damn dirty ape!
*

If it is did you blacklist the prism drivers????

=======

[http://osdir.com/ml/linux.drivers.at76c503a.user/2003-11/msg00067.html](http://osdir.com/ml/linux.drivers.at76c503a.user/2003-11/msg00067.html)

Intersting... more hacking shall ensue

---

### Post by brian.johnson on 2007-09-29
Got tired of beating my head against the stupid thing.

So, months later did this. Fed up with Feisty, I decided to start from scratch. I went to CompUSA, bought a 44pin to 40pin IDE adapter so I could mount my laptop HDD in my desktop (no CD rom on the laptop, recall hence the net install of feisty). I also bought a TRENDnet TEW-441PC wireless PC Card (802.11g with Super G). I zero-filled the drive using erase software from the fujitsu website (drive manufacturer, check your manufacturer for similar apps). I downloaded the Dapper ISO, made a CD, booted my desktop with laptop drive installed and installed Dapper. Easy Peasy.

I mounted my laptop drive back in to the laptop, X failed to start, but otherwise the system booted. from the command prompt I ran sudo dpkg-reconfigure xserver-xorg and walked thru reconfiguring x for my laptop, rebooted, presto! I have a functional install with X running proper;y. I popped out my Linksys ethernet pc card and popped in the TRENDnet wireless PC card- poof! surfing online. No fuss, no muss.

CompUSA had the TRENDnet cards on sale - $35 w/o mail in, $25 after mail in rebate.

Anyone interested in a Linksys v2.8 USB wireless adapter?

---

### Post by elektropod on 2007-10-28
One thing that was never explored here was whether there was a fundamental problem between the Atmel-based devices and the wireless router the person was using. This is just one of those things that happens sometimes.

I bring this up because I just helped my sweetie get this exact USB adapter, a Linksys WUSB11 V2.8 working on her Feisty Fawn installation. What did we do?

1. booted Ubuntu
2. plugged in working wireless adapter (Netgear MA101 Rev.B, which Ubuntu recognizes OOB)
3. used Synaptic to install the current Atmel drivers
4. unplugged the MA101, plugged in the WUSB11
5. checked ifconfig, saw MAC address for WUSB11, but it wouldn't pick up an IP via DHCP
6. checked syslog, saw some mysterious burping
7. rebooted at sweetie's suggestion, WUSB11 picks up IP without incident - and she's ONLINE!

Our combo in this case is the Linksys WUSB11 V2.8 used in tandem with a Netgear WGR614 V6 Wireless Router. The machine is a Dell Dimension 4700 and the install of Feisty is the default from the CD ISO.

Anyways, I'm half-tempted to start a new thread saying 'Linksys WUSB11 V2.8 success' because this one user's experience could well scare away a lot of newbies from trying out a perfectly reasonable USB wireless option. As the adage goes, YMMV.

---

### Post by kvmapr on 2008-06-29
Elektropod,

Just re-found this thread and I've done what you suggest, i.e. started a thread about success with the Linksys WUSB11 (version 2.8 in my case). Check it out and add to it if you care to:
[http://ubuntuforums.org/showthread.php?p=5285445&mode=linear&highlight=linksys+usb+wireless#post5285445](http://ubuntuforums.org/showthread.php?p=5285445&mode=linear&highlight=linksys+usb+wireless#post5285445)

kvmapr

---

