---
title: "Realtek RTL8187 driver help"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by cawill on 2006-12-07
Hi, i have an RealTek RTL8187 usb wireless adaptor with linux drivers.
I am using ubuntu and I am trying to get the device to work.

I follow the instructions:


tar -zxvf stack.tar.gz

tar -zxvf drv.tar.gz




cd ieee80211/

make clean;make

insmod ieee80211_crypt.ko

insmod ieee80211_crypt_wep.ko

insmod ieee80211_crypt_tkip.ko

insmod ieee80211_crypt_ccmp.ko

insmod ieee80211-r8180.ko

cd -

cd beta-8187/

make clean;make

insmod r8187.ko

This is probably fairly simple but i get stuck at the 'make clean;make' command.

I get the following output when i type that:
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/chris/Desktop/driver/ieee80211/tmp
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/chris/Desktop/driver/ieee80211 MODVERDIR=/home/chris/Desktop/driver/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
scripts/Makefile.build:17: /home/chris/Desktop/driver/ieee80211/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/chris/Desktop/driver/ieee80211/Makefile'.  Stop.
make[1]: *** [_module_/home/chris/Desktop/driver/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [modules] Error 2


Can someone please help me getting this driver installed?

Thanks

---

### Post by FrodoB on 2006-12-07
If you run Ubuntu 6.10 Edgy Eft the driver is included and just works when you put the device into the system.

---

### Post by cawill on 2006-12-11
It doesn't seem to work though when i enter the wireless settings nothing comes up. Sorry for the late reply. How would i get the driver installed anyway? And when i type in 'iwlist wlan0 scan' it comes up straight away with no results?

Thanks so far.

---

### Post by cawill on 2006-12-11
Ndiswrapper reconises my hardware, but i am still unable to connect to my BT Voyager 2000 base station, i have no security on the network for now. Any ideas on how to get it to work?

Thanks again

---

### Post by bns on 2006-12-11
Sounds remarkably like my problem.  Same device (mine is a netgear, but it has the rtl8187 chipset).  I got it to work with ndiswrapper, but it doesn't see my router.  However, I did get it to connect to a different router.  Have you checked to see if you can connect to any other networks or other routers?

---

### Post by FrodoB on 2006-12-11
At this point it is usually that the WEP keys are not identical on both ends. 

Try making new ones and installing them.  HEX keys are most compatible between  device manufacturers:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

If all else fails borrow  a different  wireless router or  if this  is a laptop go test it at a coffee shop.

---

### Post by cawill on 2006-12-12
As my network is unencrypted, WEP keys would not matter right?

I will try using another network in a few days time, bns wot router were you using and what settings did it have?

Thanks.

---

### Post by FrodoB on 2006-12-12
I am using a Linksys WRT54G and a ViewSonic WAPBR-100 that I am using for testing using 128bit WEP.

---

### Post by cawill on 2006-12-17
Hi, ive managed to test the Realtek wireless adaptor on an different pc using ubuntu 6.10 on a different network using a different router etc and i am still unable to get it to work.
Am i doing anything wrong?
How can i get it to scan for wireless networks?

---

### Post by Progressive on 2006-12-23
same problem here... I can't get wireless to work. I tried tons of different settings in /etc/network/interfaces

I have a WEP network... and I entered my key and selected "Shared Key" instead of open system... i tried selecting ASCII and Hexadecimal... neither work.

edgy recognized my card originally but wouldnt connect to any networks... so i tried installing the driver from the website just like the OP.... no luck. Now I dont even know if it recognizes my card anymore. It doesnt show up in Knetworkmanager anymore.

I somehow got it to work a few months ago in ubuntu, but I dont know how and it might have been while using Dapper. I had to wipe my hard drive recently.

---

### Post by Zer0Nin3r on 2007-01-14
> **Progressive said:**
> same problem here... I can't get wireless to work. I tried tons of different settings in /etc/network/interfaces

I have a WEP network... and I entered my key and selected "Shared Key" instead of open system... i tried selecting ASCII and Hexadecimal... neither work.

edgy recognized my card originally but wouldnt connect to any networks... so i tried installing the driver from the website just like the OP.... no luck. Now I dont even know if it recognizes my card anymore. It doesnt show up in Knetworkmanager anymore.

I somehow got it to work a few months ago in ubuntu, but I dont know how and it might have been while using Dapper. I had to wipe my hard drive recently.

Sweet!  I've been having the same problem as all of you I believe.  

Setup:

Ubuntu 6.10 64bit (Athalon)
Asus Motherboard M2N32 SLI-Deluxe w/ Wi-Fi already implemented.

WiFi Device recognized as a usb device (0bda:8187 Realtek Semiconductor Corp.)

(need more info?)

Problem:

Originally in the beginning I was able to see the device and manipulate it's settings using the driver that came with Ubuntu.  At first I wasn't able to see the router (WEP off; open network), but unable to connect.  I was showing that I'll receive packets, but none would be transmitted when doing a dhcpclient command.

So this leaves me to believe there is a problem along the line of communications from the driver interfacing with the hardware itself.  

I tried to download the Linux drivers from Realtek and had no luck with that either.  I was able to get some progress in  (make)ing the driver, but would run into errors in trying to install and initialize the driver.

Next, I removed the drivers for the RTL8187 and tried using ndiswrapper (v1.18?) with no luck.  Tried the Win98 version of the driver (that's on the motherboard install CD), because I've been reading that has been the most successful one to be used (with some bugs.)

I had no luck with the Win98 drivers because they were 32-bit and in looking at my kern.log I noticed that I was getting an error because of so.  So I installed the 64-bit drivers I had on the Asus CD with success, but no device success.

Ndiswrapper is being initialized and utilizing the 64-bit drivers, but still running into initialization problems of the device.  Ndiswrapper module is being registered under the 'lsmod' under "usbcore".

I also performed a complete removal of the restricted-generic modules under the synaptic package manager in hopes that it may fix a conflict.  Now I want to reinstall the package along with the original RTL8187 drivers that are installed with Ubuntu, but I am stuck as far as that.  I can't get the removed packages to appear in the package manager.  So, that's where I'm stuck.

In closing:

I'm about only inches away from wiping the drive and re-installing with a 32-bit version of Ubuntu.

---

### Post by jck on 2007-01-19
I've been trying for months to get it to work, Zer0nin3r.

I have a M2N32-SLI Deluxe board as well.

I've tried all the solutions but 1, so far.  That is to get an add-in PCI wireless card.

I just bought 2 Encore cards with Atheros 5211 chipsets (thank God they are different).

I read somewhere else that the reason Asus has not come to the rescue of Linux enthusiasts is that M$ keeps them at bay somehow...urban legend or truth?  You have to decide.

And after seeing that the Vista Ultimate (what we are calling in the office "Redmond KDE", and will assumably be basically Windows XP Pro x64 w/3D windows and slower operation) will be $399 MSRP...I am now dedicated to moving to a totally non-Windows platformed household.  I can not substantiate paying $400 to Microsoft...then paying $250 per support call after the first 2...it's become more about money than real technological innovation and end-user satisfaction in Redmond, I think.

A time has come to move to Linux...and support those in the Linux development community who care about putting out a product more than they care about getting wealthy from end-user dependence.

(*rant over*)

I will let you know as soon as I get the Encore card into the machine if Ubuntu/Kubuntu (I'm about to upgrade the OS once I have the new card in) recognised the card and auto configured it.  If so, I will let you know where I got the card and the price.

Good luck with your troubleshooting...I wish you all the luck and success I didn't have.

---

### Post by Zer0Nin3r on 2007-01-23
JCK, Thank you for your interesting views.  I would be more than happy to discuss the ways of Microsoft sometime.  You are not alone in thinking of such.  Just the other day I caught myself asking a co-worker if Microsoft Vista was out yet.  (How good can the latest and greatest OS be if I have to ask about it?)

Anyway.  I come to you all with updates on my venture.

Success!  After many hours and various tinkering around I have been able to get the built in wifi to work.  What I had to do:

1) Scrap the install of Ubuntu 6.10 64bit (AMD)

2) Install Ubuntu 6.10 32bit x86

3) Blacklisted the drivers of the RTL8187 chipset

```
blacklist rtl
blacklist rtl8187
blacklist r8187
```

4) Using the cd containing the drivers from Asus, I used ndiswrapper to install the _Win98_ drivers.  (I had no luck with the XP (32bit or 64bit; I'm not alone on this one), or WinMe drivers; Win98 seems to be the only one that works.)

5) Wrote out to the modprobe.d within ndiswrapper and that's pretty much it.

I know some people were talking about problems with the Win98 drivers, but I really hadn't experienced such.  Only once did the card go down (stopped communicating) and I had to reboot to fix.  The only problems I'm having now is with the wireless usb keyboard and mouse (loss of use with a period of inactiveness)

---

### Post by phossal on 2007-01-23
What wireless dongles are you guys using?

---

### Post by Zer0Nin3r on 2007-01-23
> **phossal said:**
> What wireless dongles are you guys using?

I'm using the WiFi device that's implemented within my motherboard.  It comes with an external antenna.  

(see above) 

 Does that help?

---

### Post by jck on 2007-01-26
> **Zer0Nin3r said:**
> JCK, Thank you for your interesting views.  I would be more than happy to discuss the ways of Microsoft sometime.  You are not alone in thinking of such.  Just the other day I caught myself asking a co-worker if Microsoft Vista was out yet.  (How good can the latest and greatest OS be if I have to ask about it?)

Anyway.  I come to you all with updates on my venture.

Success!  After many hours and various tinkering around I have been able to get the built in wifi to work.  What I had to do:

1) Scrap the install of Ubuntu 6.10 64bit (AMD)

2) Install Ubuntu 6.10 32bit x86

3) Blacklisted the drivers of the RTL8187 chipset

```
blacklist rtl
blacklist rtl8187
blacklist r8187
```

4) Using the cd containing the drivers from Asus, I used ndiswrapper to install the _Win98_ drivers.  (I had no luck with the XP (32bit or 64bit; I'm not alone on this one), or WinMe drivers; Win98 seems to be the only one that works.)

5) Wrote out to the modprobe.d within ndiswrapper and that's pretty much it.

I know some people were talking about problems with the Win98 drivers, but I really hadn't experienced such.  Only once did the card go down (stopped communicating) and I had to reboot to fix.  The only problems I'm having now is with the wireless usb keyboard and mouse (loss of use with a period of inactiveness)

Are you using any encryption, Zer0Nin3r?  I use WPA-PSK.  I'll try this tonight.  Sorry I've been busy and haven't replied earlier.  Thanks for the info.

---

### Post by Zer0Nin3r on 2007-01-27
No I am not using encryption.  I hope it works out for you.  Let us know how it goes.

---

### Post by amanita on 2007-01-29
Hi Guys,

I had the same problem with my wifi on Asus M2N32 but followed Zer0Nin3r recommendation and wiki [(here)]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") and it just works! I was not able to get it work on AMD64 version so I had to wipe it out and install back i386 version as was suggested, thanks!

---

### Post by Zer0Nin3r on 2007-01-29
Glad you were able to get it to work and that you were able to find the information you were looking for/needed.  I have high hopes for Linux & Open Source.

---

### Post by goofeyfoot on 2007-03-10
Gents:

I have the same wireless problem.

Have 6.10 x386. No drivers work.  Have already tried the windows 98 drivers.  Will not connect.

I am about to trash the whole linux idea. Without wireless, I can't do anything I want, so what is the point.

Any suggestions would be appreciated.

All my other posts have pretty much dead ended.

Michael

---

### Post by jck on 2007-03-23
A bit of an update:

At 4:30am when I couldn't sleep, I decided to take Ubuntu 6.10 Desktop i386 and install it over my Kubuntu 6.10 x64 Desktop install.

Ubuntu installed great onto my system.

However when I went into the ndiswrapper directory (both 1.38 and 1.28) and did a "sudo make distclean" and then a "sudo make install", I got a **HUGE** amount of "loadndisdrivers.c" errors and warnings.

I am not sure why, but this did not happen with Kubuntu.

Any ideas?

If I don't see a response by tonight, I will just re-load Kubuntu 6.10 Desktop but use the 32-bit version instead...and see if it's filesystem/build related...or an bit-compatibility issue.

I really want to get Linux running.  Once I have my big gaming box running...the old machines should all be a piece of cake.

Thanks all.

jck

---

### Post by goofeyfoot on 2007-03-23
I know what you mean about wanting to get the thing running.  The wireless farce alone has brought my whole project to a standstill.  Can't do anything much without access.

After that I have to do something to get the Soundblaster card working under Ubunto.  As thing stands I have to use the onboard card.

Jeez I was hoping the people at Realtek would get the wireless driver fixed.  Wonder how hard it can be to fix.  I guess they do have drivers which supposedly work with other distributions of Linux.  So one would think it's not much of a leap to get Ubuntu going too.  Who knows?

Keeping the fingers crossed.

Michael

---

### Post by jck on 2007-03-24
OK...there is good news...

I downloaded last night and burned the Kubuntu (I'm assuming Ubuntu will be identical/similar) 7.04 Beta 32-bit desktop distro.

I now have my system fully working, with WPA-PSK (WPA Personal) on a 54Mb/s encrypted connection and I'm using the latest Firefox for Linux.

My system uses:

Asus M2N32-SLi Deluxe Wireless Edition Motherboard with the Realtek 8187 chipset

Things you need to know/have before starting this process:
     - Your router's ESSID
     - Your router's MAC Address on your local network
     - The channel your router is using
     - Your original Asus motherboard CD

I will try and step you through this.  Due to differences in hardware for network cards, wireless routers, etc., in different parts of the world, I can't guarantee that this will work for everyone.  I am not a Linux guru, so I probably can't answer all the questions folks might pose.  I hope this helps some/all of you with the same motherboard that I have.

Steps:

1) Download and burn a CD for the 7.04 Beta Desktop distro released 23 March 2007

2) Download and burn a CD for the 7.04 Beta Alternate distro released 23 March 2007

3) Go through the installer for 7.04 Desktop distro

4) Reboot into 7.04 Desktop from disk drive

5) Blacklist the built-in driver by editing **/etc/modprobe.d/blacklist** and add the following line to the bottom:

           **blacklist rtl8187**

           then save the modification and exit your editor

6) Insert the 7.04 Alternate CD into your CD drive

7) Cancel any default actions the operating system wants to assign to the CD

8) Start Adept (Menu->System->Adept Manager in Kubuntu) and do **Manage Repositories** option under the **View** menu

9) In the **Software Sources** window, choose the 2nd tab labelled **Third-Party Software** and click the **Add CD-Rom...** button at the bottom.

10) Adept should load the repositories that are on the Alternate Distro CD, then ask you to Update your repositories list.

11) When your list refreshes, scroll down and find **ndiswrapper-utils-1.9**, choose to **Request Install**, then click the **Apply Changes** button to install ndiswrapper.

12) Once you have ndiswrapper on your system, exit Adept.

13) Eject your 7.04 Alternate CD, and insert your Asus motherboard CD.  Cancel any defaults that the Operating System wants to assign.

14) When it mounts and displays on your desktop, right click and Open the CD.

15) Navigate to the Drivers/Wifi/WIN98 directory, and copy the **Netrtuw.inf** and **RTL8187.sys** files.

16) Navigate to your home directory and paste the files there.

17) Open a terminal window.

18) At the terminal window, do the following:

     **ndiswrapper -l**

              You should have no drivers loaded

     **sudo ndiswrapper -i Netrtuw.inf**

              This should load the driver into ndiswrapper

     **sudo ndiswrapper -m**

              You might see some kind of message...but...it didn't affect me.

     **sudo depmod -a**

              This should work fine too.

19) Now, restart your install.

20) Once you have 7.04 up, login.

21) Open a terminal window.

22) Type **ifconfig** and confirm that "wlan0" is there.  It should be.

23) Type iwconfig and confirm "wlan0" is there too.  Mine was there, but it had no ESSID, no AP Association, and the channel/frequency was wrong.

24) Type the following commands to setup your wlan0:

     **sudo iwconfig wlan0 essid <your router's ESSID>**
     **sudo iwconfig wlan0 ap <your router's MAC Address>**
     **sudo iwconfig wlan0 channel <your router's channel>**

25)  Type iwconfig again and look at wlan0.  You should now be getting signal strength and what not.  At least, I did.

25) If the previous step worked, then do this: On your taskbar, go to the KNetworkManager icon, right click it, and choose your local wireless network.  This should have the same name as your ESSID.

26) At this point, it should recognize your network and the proper encryption.  You should have a place to enter your WPA password.  Enter the ASCII password and Apply.


Wait and watch...my network came up...and...I am typing this article from my Firefox 2.0.0.2 browser in Kubuntu 7.04 Beta using WPA-PSK. :)

I will try to answer questions as I can.

This is a **32 bit distro** that I am using.  I will try to install 64-bit 7.04 beta to see if it works any better.  If it does, I will post something this weekend.

My kudos to Ubuntu/Kubuntu/Edubuntu/Xubuntu.  You are the first OS I have gotten to work with this (relatively) new hardware I have.  I am very appreciative and will be trying to get as much of a donation together to send to show my appreciation.

Cheers

jck

***Edit:*** I went ahead and did a **/etc/networking/interfaces** file from Wieman's examples at the article [here]("http://www.ubuntuforums.org/showthread.php?t=318539")

Don't know if it helps, but it might stabilize your connection

---

### Post by goofeyfoot on 2007-03-28
JCK:

Congratulations on getting yours running.

I was not as fortunate but thought I would post something in case someone knows what is going on.

First, I have the same setup as you except that I am using Ubunto 6.03 instead of the version you are using.

I followed your instructions.  The glitch came when I was trying to enter the card parameters which you cited.  When I entered the channel, I did get the interface to switch frequencies.  But, when I entered the mac address of the router nothing happened.  Also, when I entered the "essid" name, nothing happened.  I verified that nothing changed by looking at wfconfig.  The only thing that moved was the frequency change.  The interface still showed "not associated" for an access point.  No essid appeared.  And there was no signal strength showing.  Everything as far as "strength" and "noise" still showed zero.  When I entered the parameters I never got any error messages - I just got ignored.

I also ran the "dhcpclient" thing and scanned for access points.  Nothing showed.

I also ran the native Ubuntu wireless interface screen and got nowhere with that.  It scanned and came up dry.

So, the short of it is that the driver is there.  I just can't seem to get the parameters to budge with the exception of the channel change.

If anyone has any more insights into this issue, would appreciate an update.

Thanks for your post.

Michael

---

### Post by jck on 2007-03-28
> **goofeyfoot said:**
> JCK:

Congratulations on getting yours running.

Thank you.
> 
I was not as fortunate but thought I would post something in case someone knows what is going on.

First, I have the same setup as you except that I am using Ubunto 6.03 instead of the version you are using.

I would suggest upgrading if the 6.03 is your version.  I believe I read somewhere previous that they had improved the wireless interface in later versions.

> 
I followed your instructions.  The glitch came when I was trying to enter the card parameters which you cited.  When I entered the channel, I did get the interface to switch frequencies.  But, when I entered the mac address of the router nothing happened.  Also, when I entered the "essid" name, nothing happened.  I verified that nothing changed by looking at wfconfig.  The only thing that moved was the frequency change.  The interface still showed "not associated" for an access point.  No essid appeared.  And there was no signal strength showing.  Everything as far as "strength" and "noise" still showed zero.  When I entered the parameters I never got any error messages - I just got ignored.

I also ran the "dhcpclient" thing and scanned for access points.  Nothing showed.

I also ran the native Ubuntu wireless interface screen and got nowhere with that.  It scanned and came up dry.

So, the short of it is that the driver is there.  I just can't seem to get the parameters to budge with the exception of the channel change.

If anyone has any more insights into this issue, would appreciate an update.

Thanks for your post.

Michael

I have seen mine lockup as well like that, where the **iwconfig** commands changed no settings.

here is what I have in /etc/modprobe.d/blacklist in my 7.04 Beta install:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist rtl8187

```

And here is what my /etc/network/interfaces file looks like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid "linksys"
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

```

Note:  I am using ndiswrapper 1.28 with the Asus M2N32-SLi CD driver for Windows 98/ME using WPA which Kubuntu 7.04 Beta automatically configured after I did the commands to configure my ESSID, Channel, and my AP settings in iwconfig.

Do you have the Asus M2N32-SLi Deluxe Wireless edition motherboard, or are you using another device that has the Realtek 8187 Wireless chipset?

Let me know and I will do anything I Can to try to help you resolve your issue.  I am quite new at this, but I'm always willing to try to help.

---

### Post by goofeyfoot on 2007-03-29
Hello JCK:

Thanks for the information.

First, an update.  After my last post I took your advice and went to the link you had in your "edit" towards the end of your last post.  I'm referring to the etc/network file that needs to be edited.

Since I have WEP (I have a couple things unlrelated that require I use WEP) I had to mess with the etc/networks file.  Because most of the lines contained in that file are nothing more than magical incantations to me, I had to do some guessing as to what WEP should look like.  I just did the best I could from what little I know about any of this.

Anyway, when I got done I did actaully make one improvement.  I was now able to see not only my router but also a couple of others in the neighborhood.  Previously, I couldn't even see a network.  Now I was able, for the first time, to see the packets, signal strength etc which had always showed flatline before. So that was quite a nice surprise.

But, I still couldn't connect to my wireless.  I even shut down (temporarily) all of the security features and still no go.  So I suspect that I probably mis-guessed on the "etc" file and will have to play around a little there.

I will have to find a good configuration file applicable to WEP on a Linksys router.  That could take some time because the samples that were online were pretty hard to interpret for my specific setup.

I will also take a look at your text but obviously you are using a different type of security so I can't  use yours verbatim.

By the way my blacklist file looks pretty similar to yours, from what I recall.

To answer your other question, I do have the same MLI motherboard which you have, so following in your footsteps is probably a pretty good way to go.

Anyway, it looks like I will get there eventually.  Any other information which you might find helpful would be appreciated.

Best wishes and good luck.

Michael

---

### Post by jck on 2007-03-29
Michael,

If you need information on how to configure your **/etc/network/interfaces** file for WEP, the authoratative post (and the one I used to help me configure my settings) is the one on this forum in a thread done by wieman01 and others.

Check this thread:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

That is where I got almost all my config info from...and it is REALLY helpful.  Many examples of how to set different configurations depending on your encryption, protocol, etc.

Good luck with it.  It sounds like you are 1 step away from being Ubuntu-fied!

jck

P.S.-  One other note:

If you have rebooted and entered your password into KNetworkManager and it is trying to scan and timing out...

Open a console window and do a **sudo iwconfig** and enter your sudo password.  See if the ESSID and ap and frequency correct.

**If not:**

1) wait for KNetworkManager to fail setting your wireless
2) in the console, enter each of those ** sudo iwconfig...** commands in my original post, followed by checking to see if they work by just entering **iwconfig**
3) If they are setting, do all of them...confirming your ESSID, channel, and ap get set.
4) Once set, try re-starting the KNetworkManager trying to configure your wireless by selecting the wireless again in your KNetworkManager
5) If KNetworkManager succeeds, in your console window type **sudo iwconfig wlan0 commit** and press enter

Like I said as well...use wieman01's thread.  It is the best information resource I've found on the web for configuring a wireless device  for use with *buntu distros.

Good luck.  Please let me know how things go.

jck

---

### Post by goofeyfoot on 2007-03-30
JCK:

Thanks once again.

Yes, I will try your suggestions.  However, I believe mine is called "Network Manager" or something similar, not KnetworkManager.  Is that just a different distribution of the same basic application?

Also, I agree Wieman's posts are really good.  But I was wondering whether there was some way to figure out exactly which one of Wieman's samples are exactly right for a particular setup.  I noted that all of the "WEP" versions posted by Wieman contained other parameters for features I'm not all that familiar with.  Not knowing what to do, I took wild guesses and made changes wherever I thought my setup was different.  Is there some way to determine exactly what is needed for my particular setup so as to avoid unintentional conflicts or ommisions? 

Again, many thanks for your reliable feedback on this most frustrating problem.  Ah well, I do believe I am getting close to a solution.

Best regards.

Michael

---

### Post by jck on 2007-03-30
Michael,

First of all, yes...if you are using Ubuntu, I believe it is NetworkManager.  I use Kubuntu because it had the KDE interface by default, which I preferred.  They should be very very similar, if not identical.

If I remember right, wieman01 goes over what each of the entries in the .conf are for.  However, it doesn't cover a lot of WEP.  So, I'll go over what I do know.

But first, I need to ask a couple of things:

1) Are you using your own router, a school/university router, or sharing/using someone else's router?

2) What WEP are you using?  40?  64?  104?  128?


If you see my example...

> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid "linksys"
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

...it's a lot more intricate.

If you are running WEP, I'd say your **base** interfaces file for wlan0 would look something like this if you're doing dhcp from your router with broadcasting enabled on WEP-64:

[i]auto wlan0
iface wlan0 inet dhcp
wireless_keymode open
wireless_key <your key>
wireless_mode managed
wireless_essid <your ESSID>
[/i]

Let me know if that works for you.  If not, your router may use WEP-128 or shared key mode or something.  We can try to get you working.  Never hurts to try. :)

Cheers

Jck

---

### Post by goofeyfoot on 2007-03-31
Hi again:

The encryption is something I don't know much about except what the router interface says.

It says 64 bit WEP encryption.  Hopefully, that tells you what you want to know.  I don't use the phrase generation thing.  I just have my own key.

The router is just a Linksys wireless access point.

When you talk about the base file, is that stuff I am supposed to enter in the etc/network file thing or is that something you have to add through the terminal commands?

By the way, you show the ESSID in quotes.  Is that how it is supposed to read in the network file?  Or do you leave the quotes off?

Finally, I usually use broadcasting off.

Thanks again for getting back to me.

Michael

---

### Post by jck on 2007-04-01
> **goofeyfoot said:**
> Hi again:

The encryption is something I don't know much about except what the router interface says.

Hi.

No problem...everyone begins learning somewhere.

WEP = Wired Equivalent Privacy. has bunches of versions...40, 64, 104, 128, 152, etc.  The bigger number just basically means...it has a bigger key...more bits.

> 
It says 64 bit WEP encryption.  Hopefully, that tells you what you want to know.  I don't use the phrase generation thing.  I just have my own key.

The router is just a Linksys wireless access point.

When you talk about the base file, is that stuff I am supposed to enter in the etc/network file thing or is that something you have to add through the terminal commands?


OK...yes...64 bit WEP is the standard, basic encryption for Linksys routers.

And you're right not to worry about the phrase generation thing.  WEP keys are set values...basic encryption really.  WPA is more involved...its key renewes on occassion and mutates...so that it is more secure.  Don't worry about wpa_passphrase.  For WEP, just set the password in the router...then in your /etc/network/interfaces file in the **wireless_key** statement...and it should be fine.

When I said "base file", I meant a basic /etc/network/interfaces.  Sorry for not being explicit.  Essentially, just remark out all the lines for your wlan0 by putting a **#** at the beginning of each one.  Then, put this in the file after the lines you just remarked out which makes this your wlan0 entry:

[b]auto wlan0
iface wlan0 inet dhcp
wireless_keymode open
wireless_key <your key>
wireless_mode managed
wireless_essid <your ESSID>[/b]

> 
By the way, you show the ESSID in quotes.  Is that how it is supposed to read in the network file?  Or do you leave the quotes off?


I put quotes around it.

> 
Finally, I usually use broadcasting off.


You might have to put one more line into the file.  I don't know if this will work or not...it is purely a guess as to how the command might work for the WEP:

**wireless_ap_scan 2**

Try putting that in with the lines above...you probably want to put it in after the **wireless_keymode** line.

If that does not work...you might want to just try setting your AP to not hidden to see if it lets you acquire your lease.

> 
Thanks again for getting back to me.

Michael

No problem...hope this gets it fixed for you.  Glad I can help.

jck

---

### Post by ivantad on 2007-06-12
Hi,

I quiet new to Linux, and I had also the same problem with activating the integrated wifi of my P5w DH Asus motherboard.
Then I went for the upgrade to Ubuntu 7.04 Feisty Fawn and everything is working great now ! :p
I use NetworkManager to choose amongst the Internet connections proposed.

Cheers,

Ivantad

---

### Post by goofeyfoot on 2007-06-12
You're kidding aren't you.  I mean I gave up on this months ago.  What is this Fawn thing?  A newer version?

Thanks.

Michael

---

### Post by Daan on 2007-06-18
goofeyfoot, have you tried ndiswrapper?

---

### Post by goofeyfoot on 2007-06-18
Oh yeah.  Believe me I tried ndiswrapper about ten times and no go.  That's why I gave up.  I just need a different fix.

Michael

---

### Post by panurge77 on 2007-06-27
I had problems using the native 8187 driver, poor performance and random disconnection when using p2p. So I went back to ndiswrapper, as I was used to when I had a 8180. But then ndiswrapper would not work.... Dont know why, but the problem with it seems to lie in networkmanager. I disabled it and set the old /etc/network/interfaces and ndiswrapper is running perfectly now. Dont remember which guide I followed to disable networkmanager, but it should be around. Also... you need to make sure ndiswrapper is in /etc/modules or it will slow your boot.

---

### Post by Tlingit on 2008-07-19
take a look at the mac80211 module it is the new one it is conflicting with the ieee80211

---

