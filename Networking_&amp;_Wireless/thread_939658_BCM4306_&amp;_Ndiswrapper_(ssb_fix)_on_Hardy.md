---
title: "BCM4306 &amp; Ndiswrapper (ssb fix) on Hardy"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2008-10-06
[B][COLOR="Red"]UPDATE 11/2/09


Great news!!!

As of 9.10 Karmic Koala, 

BCM4306 (rev02) appears 100% supported out-of-the-box, & connection to WPA networks is as easy as using WICD, with it's default settings. Just enter your encryption method & pass key & your online. 

The following tutorial should no longer be necessary.[/COLOR][/B]


The following is a list to get your BCM4306 (rev02) working (with WPA) in Hardy.It includes a fix for the "dreaded" ssb issue. Working perfect for me. 

***********************************************************************

Prerequisites in router settings...
(This is personal preference...if different, adjust the /network/interfaces to reflect it below)

WPA1 (TKIP)
Hidden ssid


*************************************************************************

Many thanks to ubunturules, fireant & weiman01, as this tutorial includes valuable information from their tutorials, in order to get my connection active. I've just combined their processes, with mine, into a simple numerical order, but which leaves out much of the thorough explanation. Credit goes to the above authors, for their contributions. See their tutorials at...

[http://ubuntuforums.org/showthread.p...06+wpa&page=75](http://ubuntuforums.org/showthread.p...06+wpa&page=75)
[http://ubuntuforums.org/showthread.p...06+wpa&page=75](http://ubuntuforums.org/showthread.p...06+wpa&page=75)

**Don't forget to use terminal to UNZIP the Windows driver to a new folder in your home folder! **


Be sure to have network-manager or Wicd installed. You'll use this only as a monitor of your wireless, not to enter any keys, etc. This will be done manually in the /network/interfaces file. 


1) Download the 32 or 64 bit Windows drivers

2) *lspci | grep Broadcom\ Corporation*

3) *sudo rmmod bcm43xx*

4) [I]echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[/I]
5) Place Ubuntu Hardy 8.04 disk in your DVD/CD tray

6) *sudo aptitude install build-essential*

7) *uname -r*    

(This will give you your kernel info...be sure to substitute it below!) 

8 ) *sudo ln -s /usr/src/linux-2.6.22-14-generic /lib/modules/2.6.22-14-generic/build*

9) [I]sudo apt-get install ndiswrapper-utils-1.9
[/I]
10) *sudo ndiswrapper -i /folder where driver is/bcmwl5.inf* ....for 32-bit drivers
*sudo ndiswrapper -i /folder where driver is/bcmwl564.inf* ....for 64-bit drivers

11) *ndiswrapper -l*

12) [I]sudo ndiswrapper -m
[/I]
13) *sudo modprobe ndiswrapper*

14) *echo 'ndiswrapper' | sudo tee -a /etc/modules*

15) [I]sudo gedit /etc/udev/rules.d/70-persistent-net.rules
[/I]
(Replace the "eth1" entry for (bcm43xx) with "wlan0" as the following example shows. If it's already listed as "wlan0", just skip this step)

# PCI device 0x14e4:0x4306 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:04:c2:65:3b:b4", NAME="wlan0")

16) *echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant*

17) [I]sudo /etc/init.d/dbus restart
[/I]
18 ) *wpa_passphrase "your_essid" "your_ascii_key"*
(....replace your_essid & your_ascii_key with your respective info & copy the outcome scrambled line after "psk=")

19) *sudo gedit /etc/network/interfaces*
(....keep any auto lo lines & replace all wlan0 lines with the following & replace <your_essid> with your ssid name & replace <your_hex_key> with the scrambled code you previously copied...)

auto wlan0
iface wlan0 inet dhcp
pre-up sleep 10
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>

20) [I]sudo /etc/init.d/networking restart
[/I]

This "should" get you to an active internet connection with 54MB/s, WPA1 encryption & Hidden SSID.

After a reboot, your connection will likely be gone...because of the Hardy "ssb" issue. 

************************************************************************

**To fix the Hardy "ssb"/ndiswrapper module/lost-wireless-at-reboot issue, we'll have to create this small script to run at startup...**

21) *sudo gedit *

22) Copy all of the following, to the blank file you just opened...

[COLOR="Blue"]#!/bin/bash

rmmod b43 
rmmod b44 
rmmod b43legacy
rmmod ssb 
rmmod ndiswrapper 
modprobe ndiswrapper
modprobe ssb 
modprobe b44 
/etc/init.d/networking restart[/COLOR]   

23) Save the above as filename "wireless.sh", and place it in the "/etc/init.d" folder. (You'll have to be root for this)   

24) Execute permissions for the script...
[I]sudo chmod +x /etc/init.d/wireless.sh 
[/I]
25) This command will run the script at boot...
*sudo ln -s /etc/init.d/wireless.sh /etc/rcS.d/S40wireless*

Reboot

:popcorn:

---

### Post by ZeroWithEverything on 2008-10-06
The links to reference threads are bad.

32 & 64bit drivers can be found in this thread:
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I'm going to try this tutorial now, and report

$ lspci
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by DapperMe17 on 2008-10-07
Best of luck, it works perfect with my BCM4306 v02. Don't be turned off by the length of the tread...that's what it took! :)

"THEE" key for me was script toward the end & especially the "network restart" line & the final terminal command to "run-the-script-at-boot." 

All the other threads that I researched failed to mention those two, which I've found essential to make it work.

The only other thing I suggest, is to manually set your network interface file. Neither network-manager, Wicd or wifi-radar would do the trick. However, they will act as a nice monitor of your internet connection.

---

### Post by ZeroWithEverything on 2008-10-07
w00t! Got it going. Thanks a ton. :) I did not get /etc/network/interfaces right, but the wifi showed up happily in network settings and i set it to roaming

---

### Post by DapperMe17 on 2008-10-07
Great to hear! 

If you're using WPA with network-manager (without manaully setting your network interfaces file, of course), could you kindly let me know? 

Thanks

---

### Post by DapperMe17 on 2009-10-30
This tutorial still works thru 9.10 Karmic Koala.

---

### Post by djaquay on 2009-10-31
Yes, another vote for "still works", although I didn't get the init script working in /etc/rcS.d, but rather in /etc/rc2.d.

Dave

---

### Post by DapperMe17 on 2009-11-02
Great Dave.

I don't know the difference, but I'll stick that change into terminal. 

I have noticed that on intermittent boots, my network is down. A re-start or two takes care of it. 

Maybe your change will take care of that.

I haven't tried the built-in driver yet out-ot-the-box.

If anyone has luck with the built-in driver, with either network manager or wicd, please let us know. We'll update the thread if there are any "easier" successes!

---

### Post by DapperMe17 on 2009-11-02
As of 9.10 Karmic Koala, the manual method is NO LONGER NECESSARY!

Just download & install WICD. It will handle the connection with perfection! 

See my update above, in the original tutorial.

:popcorn:

---

### Post by djaquay on 2009-11-03
I replaced network-manager with wicd, and got it to work at boot-up, but I did still need to have the rc2.d script in place, or the wireless nic wouldn't turn on (using the Fn-F2 key, on my laptop).  Also, I added a line I saw in another thread, making my /etc/init.d/wireless script look like:

> 
#!/bin/bash

rmmod b43
rmmod b44
rmmod ssb
rmmod ndiswrapper
sleep 5
modprobe ndiswrapper
modprobe ssb
modprobe b44


Otherwire, wicd does appear to work better than network-manager.

Thanks, DapperMe17!

Dave

---

### Post by kevdog on 2009-11-03
Why you would ever want to use ndiswrapper for the 4306 rev 02 card is beyond me!!! b43 and openfwwf make drivers that work -- and you can run these drivers in monitor mode.

---

### Post by DapperMe17 on 2009-11-05
Come on kevdog!

That was the only way to get it done in 1964...we're in a better place now

:lolflag:

PS...I enjoyed reading your weblog

---

### Post by brookie on 2009-11-21
not meaning to hijack this thread, i can start another one, but kevdog, 
any ideas on how to get the bcm4318 working? 

the b43 driver does not work on it for hidden networks with wpa/wpa2 encryption. b43 works on unsecure networks though. np.

i tried lots of these tutorials and failed, but the ethernet connection is faster anyway. 

just thought i'd ask in case my son wants to take his laptop out someday. cheers, brook

---

### Post by billfinch on 2009-12-09
back to the original 4306 issue. I posted about my problems with rev 03 earlier before I saw this. I tried something almost like this before and it failed, but given the step by step, I'll give it another shot.

Question about the Win drivers. I have the bcmwl5.inf and the bcmwl5.sys files. another thread said some binaries were required as well. If True, where do I get these?

---

### Post by billfinch on 2009-12-09
Ok so I drank the kool aid and installed a brandy new 9.1 immediately after seeing this thread. Guess what? No wireless. At least it tries to connect now, but still nothing. I put in my network name, etc. I even tried with and without WPA. No luck. 

Before I start trying all the variants suggested on other threads I wanted to ask on this one for what else? One thing is that even though it automatically downloaded the b43 driver which also loaded the firmware into the /lib/firmware/b43 folder (This did not exist prior to the DL. I checked), it is not clear whether it downloaded and/or ran b43-fwcutter. There is a note that says this needs to happen, but I didn't see any notification that it was doing anything. Being a newbie, I'm not sure exactly how to get it if I need it. Synaptic didn't show it under packages. Is this one of those apt-get things?

BTW, I have a rev 03 card, not an 02.

Any help is appreciated. I really want to get this to work.

---

### Post by DapperMe17 on 2009-12-12
I see you have the BCM4306, Rev 3. 

The tutorial was for Rev 2. 

I believe that the difference is probably two different architectures. But, I'm not entirely sure.

If WICD "sees" your wireless network, half the work is already done! Don't give up, this card is a bugger.

Another member of this thread indicated that he/she had to go through the steps at the end of the thread, I believe 21-25, in addition to using WICD.

Try that, before you go the entire tutorial. If that fails, do the whole tutorial as a routine & worry not about using WICD.

It is a long, trying process with the BCM4306. I know, I went through what you are. 

You do not need any other binaries.   

Keep the faith, you'll get there & will learn alot through any frustrations.

---

### Post by billfinch on 2009-12-14
Thanks for the encouragement. I finally got it! Basically, after a zillion other issues, I found I had the wrong Win driver. Apparently, BCM made a config du jour for the PC manf. I found that there is still a Compaq support site which is different from the HP site where I got the first one.

Anyway, I used a combination of your ideas and the GTK gui version of NDIS and got it going at boot. At least, for 1 day and 10 boots. I will post the whole solution on my original post so it can show as solved.:D

---

### Post by DapperMe17 on 2009-12-14
Glad to hear to did it!

I won't lie, it's alot of work with Broadcom cards. 

I recently found Vector Linux, which supports the CM4306 w/encryption...out-of-the-box.:D

I'm very partial to Debian tho.

I suggest you upload your solution, if anything, just to keep it online should you need it again.

:popcorn:

---

### Post by chuckles on 2009-12-15
> **DapperMe17 said:**
> Glad to hear to did it!

I won't lie, it's alot of work with Broadcom cards. 

I recently found Vector Linux, which supports the CM4306 w/encryption...out-of-the-box.:D

I'm very partial to Debian tho.

I suggest you upload your solution, if anything, just to keep it online should you need it again.

:popcorn:

So does anyone know if the B43-Fwcutter solution will work for the BCM4306 Cards?   I have a Dell inspiron 8600 with Broadcom internal wireless card, and I'm running 9.10 Kubuntu. 

my syslog file indicates that I need a version 3 driver.

b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

But when i run lspci i get this:

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


And if I load the fwcutter tool with the hardwire drivers section, it installs the B43Legacy driver, which from what I understand, is indicated for version 2 of the BCM4306 Card, but the standard B43 Driver is what is indicated for version 3 of this chip.  I'm I wrong here?  

Is there a way to get this to work with using windows driver with ndiswrapper?  If so, will get full (54mbps) speed?   Please advise.

Thanks,

Chuckles

---

