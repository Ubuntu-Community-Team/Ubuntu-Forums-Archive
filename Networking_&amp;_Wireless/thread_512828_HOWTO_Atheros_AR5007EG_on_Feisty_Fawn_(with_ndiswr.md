---
title: "HOWTO: Atheros AR5007EG on Feisty Fawn (with ndiswrapper)"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by bmartin on 2007-07-29
[COLOR="Red"]**If you're running a 32-bit OS, this method is deprecated. I recommend [the native linux driver]("http://ubuntuforums.org/showthread.php?t=792158") instead.**

If you're running a 64-bit OS, use the method below.[/COLOR]

Make sure you use the appropriate version of the drivers for your version of Linux. If you're using a 64-bit version of Linux, you **must** use 64-bit drivers. You can check this using the following command:
```
getconf LONG_BIT
```

I personally recommend using the [wicd]("http://blakecmartin.googlepages.com/wicd.html") program for WiFi connectivity. It boasts built-in WPA support and has been successful where other network connection manager programs have failed.

This chipset showed up on my Acer Aspire 5050-3785. The lspci program spit out the following info:
```
Atheros Unknown device 001c (rev 01)
```
It also has been incorrectly labeled as an AR5006X device, in some cases.

Here is a step by step procedure to install the drivers manually (in case you don't want to use the script I wrote, or if it doesn't work properly). Open a terminal and copy/paste the following lines:

1a. Download the ndiswrapper source code and AR5007EG Windows drivers:
```
http://wifix.sourceforge.net/software.php?title=ndiswrapper
```
1b. Download the AR5007EG Windows XP drivers:
If you're using a 32-bit version of Linux, use this command:
```
wget http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz
```
For 64-bits of blazing WiFi glory, use this:
```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```
2. Extract the archives:
```
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
```
3. Ensure you have your kernel headers and the build essential package.
```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```
4. Blacklist the ath_pci kernel module (it doesn't support our chipset).
```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```
5. Compile ndiswrapper:
```
pushd ndiswrapper-*/
sudo make uninstall
make
sudo make install
popd
```
6. Install the Windows drivers (using ndiswrapper):
```
pushd */ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
```
7. Make sure ndiswrapper loads up every time we start Linux:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```
8. Restart your computer.
```
sudo init 6
```

=====
FAQ
=====
Q: Linux seems to see my device now, but it can't see any networks. What can I do now?
A: This frequently happens on built-in devices. There's usually either
[LIST]
[*]A switch on your computer somewhere that toggles whether the wireless radio is on or off (BEWARE! Some of these are very unintuitive. The setting that may seem like "on" may be "on" and vice-versa.)
[*]A keyboard combination that enables/disables the wireless connection (usually Fn+F2).
[*]A setting in the BIOS that needs to be changed. This can be frustrating to track down. The BIOS is the program that loads before your OS. When your computer first boots, there's a key you can press to go into the system setup; look for a wireless setting in there that you can enable.
[/LIST]

Q: I can see wireless networks. Why can't connect to any of them?
A: There are a couple options to try here. If you're using WICD to connect and WPA encryption, under preferences, make sure that for WPA Supplicant Driver, you're using WEXT (make sure you've installed WPA_Supplicant). If you're using WEP, try putting your key in "double quotes". If you can't connect to an encrypted network, try removing they key to see if that's the problem. If you're not using WICD, try it out; many people have been successful simply after switching the wireless connection manager program to WICD.

Q: None of this worked. I'm no closer to having my wireless working than I was when I first installed my OS. What's wrong?
A: Try running **sudo modprobe ndiswrapper**; the program should run silently. If you get any output, there's a problem. If the ndiswrapper,ko file can't be found, run **sudo depmod -ae**, then try **sudo modprobe ndiswrapper** again.

If you installed your OS a long time ago, some people have had better success with a fresh install. Try installing the drivers while running from the Live CD.
=====
EDIT: I removed the instructions for using the script. It seemed to not work for anyone other than me. I checked it over several times and couldn't figure out why. The instructions and the script seem to perform the same set of operations.

---

### Post by ryscar on 2007-07-30
Thanks for the howto, unfortunately, it did not work for me.  I copy/pasted everything and received no errors.  I would appreciate your help in getting this working.  The results of lshw -C network show that the adapter is still unclaimed.

Additional Info:
Fresh install of 7.04 w/updates
Acer Aspire 3680-2682
AR5007EG as reported by Vista

Please let me know if you can give me a hand on this.  If you need some logs, just let me know.  Also, I have no reservations about a fresh install at any time.

Thanks in advance!
Ryan

**UPDATE**
Well, I got it working.  Not too sure how I did it but, I will figure that part out in a week or so (family visiting). I know I am using the latest ndiswrapper and the drivers linked to from here: [http://ivangarcia.org/blog/?p=13](http://ivangarcia.org/blog/?p=13).

Thanks for getting me started in the right direction and when I get some time, I will update this to reflect what worked for me.

---

### Post by bmartin on 2007-07-31
Good to know the method worked. Please send me the steps you took to make it work (i.e. how it differs from my method).

---

### Post by skaz on 2007-08-01
I ran your script but I'm still having trouble.

dmesg shows that ndiswrapper 1.47 is loaded.

ndiswrapper -l displays

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


..but I get nothing else. This is an Acer Aspire 5570Z (5570-2690). Fresh install of Ubuntu, installed nothing else yet.

---

### Post by msingletary on 2007-08-01
> **skaz said:**
> I ran your script but I'm still having trouble.

dmesg shows that ndiswrapper 1.47 is loaded.

ndiswrapper -l displays

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


..but I get nothing else. This is an Acer Aspire 5570Z (5570-2690). Fresh install of Ubuntu, installed nothing else yet.

I get the same... followed the directions and everything looks to be running okay but still no wireless.

---

### Post by ryscar on 2007-08-01
I just did a fresh install and followed the directions from the link below and everything went smooth.  The only thing I did differently is on the last two steps I had to use sudo.  Anyhow, wireless is working!!

[http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)

Ryan

---

### Post by msingletary on 2007-08-01
> **ryscar said:**
> I just did a fresh install and followed the directions from the link below and everything went smooth.  The only thing I did differently is on the last two steps I had to use sudo.  Anyhow, wireless is working!!

[http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)

Ryan

Strange! I tried those as well and couldn't get it to work.

---

### Post by ryscar on 2007-08-01
Did the process fail at some point or did it complete successfully but still no wireless?  I know when I first tried to compile ndiswrapper, I had forgot to do an apt-get install g++ to get the things I needed.

---

### Post by msingletary on 2007-08-01
> **ryscar said:**
> Did the process fail at some point or did it complete successfully but still no wireless?  I know when I first tried to compile ndiswrapper, I had forgot to do and apt-get install g++ to get the things I needed.

Everything went through properly without any errors. Wireless just refuses to work.

---

### Post by fischer98 on 2007-08-01
This does not work for me. I have an AR5007EG on a Toshiba U305-5077. I followed the manual instructions you listed here. After the modprobe command on step 7, I looked at a dmesg output, and this is what I saw:

[ 1438.516000] ndiswrapper version 1.47 loaded (smp=yes)
[ 1438.532000] ndiswrapper: driver net5211 (,01/20/2006,4.2.2.7) loaded
[ 1438.532000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[ 1438.532000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[ 1438.532000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[ 1438.532000] ndiswrapper (NdisWriteErrorLogEntry:192): log: C0001389, count: 4, return_address: f90645d4
[ 1438.532000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xdf820200
[ 1438.532000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x28
[ 1438.532000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8db8000
[ 1438.532000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8db8000
[ 1438.532000] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[ 1438.532000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[ 1438.536000] ndiswrapper (mp_halt:258 ): device f6749400 is not initialized - not halting
[ 1438.536000] ndiswrapper: device eth%d removed
[ 1438.536000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[ 1438.536000] ndiswrapper: probe of 0000:06:00.0 failed with error -22
[ 1438.540000] usbcore: registered new interface driver ndiswrapper

Basically, it looks like the driver does not work for my card. Any thoughts?

---

### Post by ryscar on 2007-08-01
That was the same thing I was getting.  I think it has something to do with the driver included in the script but, I am not sure.  It does appear to be older than the one that worked for me in the above post.

---

### Post by fischer98 on 2007-08-01
I got this working in Backtrack. I haven't tried ubuntu. I was just looking at this thread as an alternate info source. But considering I was getting the same errors in both, it should work for you too. You are right about the driver being old. You can get the latest drivers from here:

[ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip)

You'll need both the ar5211.sys and the net5211.inf files. With these new files, the instructions above worked for me.

---

### Post by fischer98 on 2007-08-01
Misread your post a bit. Looks like you already got it working. Anyway, the info is hear now for those who come after.

FYI, i found the latest drivers by doing a search on ndiswrapper's website, under their known working cards list:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by Adntu on 2007-08-01
Hi 
I tried all the listed drivers, and I tried madwifi before, but all did not work, I tried the XP driver from Atheros.cz all with no success, I do not know what is the problem, any suggestions???
thanks

---

### Post by fischer98 on 2007-08-01
Mad wifi says specifically on their site that the AR5007EG will *not* work.

Did you download the drivers from the ftp site I provided? The instructions would not work for me until I got the latest drivers.

---

### Post by Adntu on 2007-08-01
I tried these and all the others, at last I tried the XP driver I got from :
[http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1)
and that worked, now I am posting using wlan.
thanks guys

---

### Post by balk on 2007-08-05
> **ryscar said:**
> I just did a fresh install and followed the directions from the link below and everything went smooth.  The only thing I did differently is on the last two steps I had to use sudo.  Anyhow, wireless is working!!

[http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)

Ryan
Thank you so much!! it is working now.

For the search:
wlan on Acer Aspire 3680 - 2682
Atheros AR5BXB63 wifi (as indicated on bottom of laptop)
chipset AR5007EG

happy :)

now wait for video enabled skype and I can throw away vista completely

---

### Post by bmartin on 2007-08-05
> **fischer98 said:**
> FYI, i found the latest drivers by doing a search on ndiswrapper's website, under their known working cards list:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)
Thank you. I uploaded the new drivers and modified the instructions accordingly.

---

### Post by overdrank on 2007-08-08
Thanks it works, the short cut did not work but the long way did. Thanks a lot you just don't know how much that help. GREAT WORK!!!!!!!!!! 

:guitar::guitar::guitar::guitar:

---

### Post by victorawesome on 2007-08-08
Thanks so much ... I was struggling with this all day until I found this thread.

I've got a Toshiba Satellite Intel Pentium Dual Core T2080 1.73GHz Laptop (P200-RT1) if that helps anyone.

---

### Post by bmartin on 2007-08-10
Sweet... so it looks like the script may work at this point, but the long way definitely does. I'm glad this has worked for a couple people, anyways.

I'm having a lot of trouble getting other things to work on my Acer Aspire 5050-3785. The ACPI is completely screwed up and the card reader is unsupported.

---

### Post by victorawesome on 2007-08-11
I can't seem to get the wireless going when I reboot the labtop ... but if I shut it down and turn it on again it works great ... though it's not a big deal b/c I will rarely need to restart ubuntu :)

Has anyone else experienced this?

---

### Post by spike316 on 2007-08-11
Ok, so I have this installed and everything and it says it's working but I'm not getting anything... I still just have ethernet and modem connection in my connection options thing, and now rather than using the atheros hardware access layer in the list of drivers not in use it says it's not using it. It's enabled, but it's not in use. Help? Sorry, i'm kind of a noob at this.

*edit* I'm running this on an Acer Aspire 5100-5840 if that makes any difference.

---

### Post by bmartin on 2007-08-11
So **ndiswrapper -l** indicates that ndiswrapper and the driver are OK and **iwconfig** indicates that you have a wireless device, but you can't connect? Try using the wifi-radar program. It's in the universe repo; the package name is wifi-radar.

---

### Post by spike316 on 2007-08-11
this is what i get with ndiswrapper -l:
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

so it looks like i installed things properly... but for some reason it's still not recognizing my card?

---

### Post by chadjohnson on 2007-08-11
This tutorial worked for me (I did it the manual way, not sure about the script). I have an Acer Aspire 5050.

---

### Post by bmartin on 2007-08-11
> **spike316 said:**
> this is what i get with ndiswrapper -l:
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

so it looks like i installed things properly... but for some reason it's still not recognizing my card?
Try **lsmod | grep ndiswrapper**.

---

### Post by spike316 on 2007-08-11
> **bmartin said:**
> Try **lsmod | grep ndiswrapper**.

ndiswrapper           239608  0 
usbcore               154416  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

---

### Post by bmartin on 2007-08-11
How about trying the following?
```
sudo ifconfig wlan0 up
sudo ifconfig eth1 up
```
It's wlan0 on my computer. Perhaps it's being detected, but the interface is down for some reason.

---

### Post by chadjohnson on 2007-08-11
Three things I noticed.

[LIST=1]
[*]This only started working when I used wifi-radar. After that, I could run dhclient and get an IP address, but not before.
[*]The newest drivers from Acer don't work, but the ones on this thread do. Why is that?
[*]My connection is very fast in the same room as my router, but when I go across the house, it hardly works at all. It worked perfectly throughout the house with my other laptop on the same router settings.
[/LIST]

---

### Post by bmartin on 2007-08-11
> **chadjohnson said:**
> This only started working when I used wifi-radar. After that, I could run dhclient and get an IP address, but not before.
For this reason, I recommend wifi-radar whenever someone has trouble. In fact, I'll modify the instructions to include this recommendation.

> **chadjohnson said:**
> The newest drivers from Acer don't work, but the ones on this thread do. Why is that?
I'd like to know the same thing. When I originally built this thread, I had a couple different Windows drivers on my computer, and I must've picked the wrong ones for the script because the first two people who tried this install had no success. They figured out the problem. I then downloaded the drivers they claimed worked, and ever since then, this has worked for everyone.

I think there's a difference between using the Vista and XP drivers, and I've heard people say that Windows drivers updates can affect your Linux WiFi. There are a lot of "unexplained" wireless phenomena. Personally, I haven't had any problem with either of my WiFi chipsets (I also have a [Broadcom 4318]("http://ubuntuforums.org/showthread.php?p=3174150#post3174150") chipset). The fact that I don't use Windows on either computer is probably why I've had more luck than many other people.

> **chadjohnson said:**
> My connection is very fast in the same room as my router, but when I go across the house, it hardly works at all. It worked perfectly throughout the house with my other laptop on the same router settings.
Some chipsets send/receive signals better than others. Have you compared it to the strength in Windows? If there's disparity between the OS's, my guess is it's ndiswrapper's fault (ndiswrapper is a work-in-progress, but it's pretty stable).

---

### Post by chadjohnson on 2007-08-11
Have not tried it in Windows -- I should have before I formatted it. Oh well. I have the recovery discs, so maybe someday.

---

### Post by spike316 on 2007-08-11
> **bmartin said:**
> How about trying the following?
```
sudo ifconfig wlan0 up
sudo ifconfig eth1 up
```
It's wlan0 on my computer. Perhaps it's being detected, but the interface is down for some reason.
 
that doesn't seem to work either:
wlan0: ERROR while getting interface flags: No such device

and chad: your internet card on your other laptop is probably just better than the one you have on this one.

---

### Post by ntlam on 2007-08-16
I got the same problems
everything seemed OK when being installed but no wireless
 iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

BTW, i have a satellite u305-5077
atheros ar5007eg

Any one here has the same laptop and already succeeded?

---

### Post by ntlam on 2007-08-16
Here's what i did:

Step 1: Disable ath_pci

sudo rmmod ath_pci
sudo gedit /etc/modprobe.d/blacklist-common

add the following line at the end of the file

blacklist ath_pci

Save and close

Restart computer

step 2. remove old ndiswrapper by using synaptics

Step 3: Build essentials
Use the synaptic package manager
Install the package called "build-essential" in the group called "Development"
But I already got it installed

Step 4: Install Ndiswrapper.

Go to [http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)
Download ndiswrapper-1.47.tar.gz to folder /home/username

Code:

cd /home/username/
sudo tar xvzf ndiswrapper-1.47.tar.gz
cd /home/username/ndiswrapper-1.47/
sudo make
sudo make install

Step 5: Load drivers with ndiswrapper.
sudo ndiswrapper -i net5211.inf

installing net5211 ...

forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
........ a lot of lines like above...

then:
sudo ndiswrapper -l
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)

Step 6: Load ndiswrapper and check if it worked
sudo modprobe ndiswrapper

Check it:
iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

Then I did:

sudo ndiswrapper -m


But no wireless after reboot

---

### Post by ntlam on 2007-08-16
got it work now
[http://ubuntuforums.org/showthread.php?p=3202754#post3202754](http://ubuntuforums.org/showthread.php?p=3202754#post3202754)

---

### Post by buzzmandt on 2007-08-18
spot on instructional and stuff.......
tried literally every other "how to" for my acer wireless and this one finally got it to work

thank you

---

### Post by scull on 2007-08-18
Thanks for the clear and precise instructions.  I had to follow the entire sequence but the wireless on my Toshiba A200 now works perfectly.

John:)

---

### Post by jgrantham on 2007-08-20
I have tried all the instructions and followed them to a tee. I can run iwlist wlan0 scan and it shows networks. I can run wifi-radar and it shows networks but I get no IP and can not  connecct to the internet. It also shows my MAC as being all 0's. 

I can not figure this out but it is about to make me pull all my hair out. I have a Acer Aspire 5100 with the Aetheros 5007eg card in it running Fiesty on x86 64 bit. Does anyone have any ideas?

---

### Post by buzzmandt on 2007-08-20
> **jgrantham said:**
> I have tried all the instructions and followed them to a tee. I can run iwlist wlan0 scan and it shows networks. I can run wifi-radar and it shows networks but I get no IP and can not  connecct to the internet. It also shows my MAC as being all 0's. 

I can not figure this out but it is about to make me pull all my hair out. I have a Acer Aspire 5100 with the Aetheros 5007eg card in it running Fiesty on x86 64 bit. Does anyone have any ideas?

when you run wifi-radar and select connect, does it show up an ip address in that screen?  If so, your network icon can still show no connection and it will just work, found this out the hard way

---

### Post by bmartin on 2007-08-20
I recently found an even better WiFi manager. It's called [wicd]("http://blakecmartin.googlepages.com/wicd.html"). It has succeeded for many people where other network connection managers have failed, and it boasts built-in WPA support. It comes highly recommended.

---

### Post by BenjaminCHILOE IS. on 2007-08-21
It worked in the end in Kubuntu Feisty , I had to remove Knetwork Manager and replaced it for KWlan and also added Kwifi Manager. I followed each step given in HOW TO Everything worked out in my new ACER  ASPIRE 5050 with this Atheros Ar5006x which never did work. AAAHh don't forget to activate manually the swith on (frontal switch next to the left speaker) you can check it with Kwifi MAnager when activated. I am happy with kubuntu running well in my machine.

The best for all from CHILE.

---

### Post by blahquaker on 2007-08-21
it's not working for me.

I went through the instructions and ndiswrapper seems to think the driver is installed correctly, but nothing else (iwconfig, iwlist, ifconfig, etc) seems to know my wireless card exists.

I tried adding wlan0 with the mac to /etc/iftab (something I found in another thread) but it's still not recognized anywhere.

any help would be appreciated.

toshiba a215-s4807, ubuntu 7.04, amd64, atheros ar5007eg.

---

### Post by jgrantham on 2007-08-21
It shows connected to the Ap with an IP of 127.0.0.1 . I have no idea why this won't work. I followed the istructions agin to the tee and still no go.


HELLLLLLLPPPPPPPPPP!!!!!:(

---

### Post by trjepp on 2007-08-21
Hi, I used the howto instructions (with the shortcut) and it worked like a dream on my aspire 5050 where nothing else would. all of the networks in the area show up now, through any of the wireless apps that came installed on ubuntu ultimate 1.4. anyways the problem i'm having is i can't get into my apartment complex's internet.... i have my username and password, but don't know how to get to a point where i have even been prompted for them. by now you can probably tell i'm new at this and don't know what i'm doing. if anybody could help my sign in and use the connection, i would really appreciate it

---

### Post by bmartin on 2007-08-21
If you're using Ubuntu (GNOME), try going to System > Administration > Network. That should allow you to enter the appropriate wireless settings.

You can also use [WICD]("http://blakecmartin.googlepages.com/wicd.html") or [wifi-radar]("http://blakecmartin.googlepages.com/wifi-radar.html") to connect.

---

### Post by gigabite on 2007-08-22
Thank you so much! I would have never gotten this working in a thousand years without your post.

---

### Post by blahquaker on 2007-08-22
I got it to "work" for me finally... I tried three different drivers, and finally got it to register the interface correctly with the xp 64-bit driver from atheros.cz. it now recognizes the interface and wifi-radar displayed eligible networks, but wouldn't give me the option of connecting to any of them. so I'll just have to figure that part out when I get home.

another somewhat major issue, though - if the wireless card is turned on, GRUB won't load and the system won't boot. I have to turn the wireless off (external switch), then boot, then turn the wireless card on. is this something anyone else has experienced?


toshiba a215-s4807, ubuntu 7.04/vista dual-boot, amd64, atheros ar5007eg

---

### Post by bmartin on 2007-08-22
> **blahquaker said:**
> another somewhat major issue, though - if the wireless card is turned on, GRUB won't load and the system won't boot. I have to turn the wireless off (external switch), then boot, then turn the wireless card on. is this something anyone else has experienced?
Yep. It might be that you have to blacklist the rt73usb module.
```
echo "blacklist rt73usb" | sudo tee -a /etc/modprobe.d/blacklist
```
I had that problem with my parents' wireless adapter. It might be a different module, but that sounds like it could be the case.

You might have to blacklist rt2570 and rt2500usb, too

---

### Post by blahquaker on 2007-08-22
> **bmartin said:**
> Yep. It might be that you have to blacklist the rt73usb module.
```
echo "blacklist rt73usb" | sudo tee -a /etc/modprobe.d/blacklist
```
I had that problem with my parents' wireless adapter. It might be a different module, but that sounds like it could be the case.

You might have to blacklist rt2570 and rt2500usb, too

ok, I didn't see any of those in lsmod, but I blacklisted all of them anyways... and no change. the only thing in the list that looked like that was r8169, but I need that for my wired ethernet adapter.

anyone have any other ideas?

---

### Post by bmartin on 2007-08-22
I wouldn't give up on the "modules" idea... it could still be a module (it sounds like it to me), but I don't have any idea which ones are loaded up on your computer. The r8187 and r818x modules are known to cause problems (they should already be blacklisted)... so should ath_pci. Make sure those are all blacklisted.

---

### Post by keypox on 2007-08-23
hey i installed the driver from acer and it didnt work. Someone had said something was wrong with it so i downloaded the one that is supposed to work but i cant install it because the old one is still installed how do i remove the old one? 

I think i use the -r command but it doesnt find it.  I guess i need to know where it is installed?

---

### Post by bmartin on 2007-08-23
To remove the driver, use **sudo ndiswrapper -e (driver)**, where (driver) is the name of the driver shown by *ndiswrapper -l*

---

### Post by keypox on 2007-08-23
> **bmartin said:**
> To remove the driver, use **sudo ndiswrapper -e (driver)**, where (driver) is the name of the driver shown by *ndiswrapper -l*

couldn't delete /etc/ndiswrapper/net5211.inf: No such file or directory

---

### Post by bmartin on 2007-08-23
What'd you type? sudo ndiswrapper -e net5211.inf?

Try **sudo ndiswrapper -e net5211**

---

### Post by keypox on 2007-08-23
> **bmartin said:**
> What'd you type? sudo ndiswrapper -e net5211.inf?

Try **sudo ndiswrapper -e net5211**

yep i did that it worked, i installed the new driver and still doesnt work

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sudo ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


any ideas?  Have people actually got this to work on the Acer 5570-2977?

---

### Post by keypox on 2007-08-23
hey finally got it to work from previous poster 

[http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)


i only had to do the blacklist stuff.  Make sure you save that file and it worked for me.

---

### Post by warpasylum on 2007-08-24
worked on my acer 5050 perfectly. wasn't able to use script, but worked manually cutting n' pasting.  thanks=)

---

### Post by bmartin on 2007-08-24
Heh, my bad with the script. I found the bug. I used "echo" to comment out a bunch of commands and didn't un-comment them. It should work now. Thanks for pointing that out.

---

### Post by mrfr0g on 2007-08-26
Acer Aspire 5570

While the script did not work for me, going through the motions step by step absolutely worked perfectly. I am now typing this on my wonderful wireless network. Thank you SOOOO much! You don't even know how many different walk throughs, tutorials, and FAQ pages I went through, all which failed. I'm so glad I stumbled across this page.

---

### Post by BudaAlien on 2007-08-28
I am new to Ubuntu and linux, so I don't really know many commands yet but I am learning! I'm trying to get my atheros 5007eg wireless to work on fiesty fawn. I tried to install the lastest ndiswrapper but I get error messages that start when the install gets to the utilities. When I check the ndiswrapper I get this:  

$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

Am I missing something like a compilier?? I have the driver needed for my wifi and ndiswrapper lists it as installed but I have no interface.

---

### Post by bmartin on 2007-08-28
[Here's a HOWTO]("http://ubuntuforums.org/showthread.php?t=104539") for compiling ndiswrapper.

---

### Post by marianoi on 2007-08-28
I am going to try this tomorrow in a Acer Aspire 5570 for my "in law". One simple question: what would happen once a kernel update appear? would they have to do it all over? :confused:

---

### Post by bmartin on 2007-08-28
Probably not, because the ndiswrapper.ko kernel module is included with Ubuntu.

The instructions compile the newest ndiswrapper utility program and kernel module. Your wireless device probably works with an older one.

If you need to recompile the kernel module every time for some reason, you could modify /boot/grub/menu.lst so that the same kernel loads up every time (the current one) even if a newer one is installed.

---

### Post by marianoi on 2007-08-28
Thanks bud. 

But one thing regarding the kernel update. Every new Kernel goes to the top of the GRUB list...how can I force it to always boot on the current kernel without editing the menu.lst fie?

Thanks!

Cheers

Mariano

---

### Post by bmartin on 2007-08-28
There isn't a way that I know of. However, take a look at menu.lst.

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

If you put something **here**, it will be the first selection in GRUB.

### BEGIN AUTOMAGIC KERNELS LIST
```
I had to do this for my girlfriend's computer. She has one of those awful Acer laptops with the messed up ACPI DSDT. Without a patched kernel (or special kernel image), her CPU, fans, and lid (the switch) don't work properly, and her battery isn't displayed.

What I'd try doing, since you seem pretty worried about a kernel upgrade, is to simulate one. Add another kernel in and see if it works fine. I upgraded my kernel on my laptop and there wasn't a problem; I'm currently using the Gutsy one on there.

---

### Post by axylone on 2007-08-29
Thanks!  Worked perfectly for me:
Kubuntu on an Acer Aspire AS5570Z-2997
I installed ndiswrapper through the package manager, but other than that followed the directions.

---

### Post by sbassett on 2007-08-29
Followed this little how-to for a friend's Acer, and I personally use WICD at home (because it rocks) however, this will not work correctly on the Acer. Did you set this up on the Acer? And did you run into any issues?

**CLARIFICATION** : This HOW-TO worked on the Acer, but the WICD install did not.

---

### Post by bmartin on 2007-08-29
I have to fix the script. The step-by-step instructions and the script were both tested on an Acer 5050-3785.

---

### Post by bearswatchin on 2007-08-30
Thanks so much! That was the last thing I needed to fix so I could get out of Windoze bondage. Works fine. Worked the first time out of the script (box). I am 100% Linux Mint on my Acer Aspire 5570Z.

bearswatchin

---

### Post by mberry on 2007-08-31
Well, it took a couple of hours, but wifi is now working for me on a Toshiba Equium L40-10Z thanks to this.
The acer driver didn't work, but the one included with [http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1b.tar.gz](http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1b.tar.gz) worked fine.
Many thanks.

---

### Post by Hypersonic on 2007-08-31
I've lurked on this thread and finally got the wireless going on my Toshiba Satellite A215.  The script did not work, the long version did install the driver but it still did not work.  Then I saw the post about blacklisting the Atheros restricted driver and that did it.  Thanks much for all the help!

---

### Post by atilla.the.hodge on 2007-09-01
Hi All,

I also wanted to say thank you for the hard work to everyone who contributed to this solution.  I was able to get my wireless network up and running in < 15min by following the instructions posted by bmartin.  I am using the wicd program as was also suggested.

The only 'problem' that I have encountered is that I cannot for the life of me talk to either my wireless gateway (Siemens Gigaset SE567) or my wireless router (DLink DI-624) using WPA security; I tried both the 'wext' and 'ndiswrapper' encryption settings.  WEP 128-bit seems to work fine if I use a hexidecimal key.

Thank you again!
Take care,
-- Adam

---

### Post by bmartin on 2007-09-02
Did you install the wpa-supplicant package? (sudo aptitude install wpasupplicant)

ASCII keys should work in WICD; I think you have to put "double quotes" around them, though.

---

### Post by atilla.the.hodge on 2007-09-02
Hi,

I double checked and I do definitely have the wpa_supplicant package installed.  Thank you though for the tip about using quotes to enclosed ASCII passwords!

I tried setting WPA again today using the newer version of wicd (1.3.3 [testing version: [http://wicd.sourceforge.net/phpbb/viewtopic.php?f=5&t=146]](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=5&t=146]) vs. 1.3.1 that's installed via package manager) and still no luck.  For whatever reason I can talk to the gateway/router, but no IP address is assigned - wicd says "Obtaining IP address..." for a minute or so and times out; this could be a gateway/router setting, although my wife's Macbook can connect without trouble.

Thanks again!
Take care,
-- Adam

---

### Post by paymoretaxes on 2007-09-06
Just want to say that the script you had before did work for me. The manual way works too. Thanks.

---

### Post by Rockman4140 on 2007-09-06
I can now detect wireless networks with my card with the Atheros.cz drivers, but I cannot connect to them. When I attempt to, it asks for a key, which is my WEP key, after giving it that, it either attempts to connect and fails, or connects at 0% connection. I find it pretty weird. Here is a transcript of what I've typed in the Terminal to give someone out there some kinda knowledge.
```

Network
Wireless Connection - Roaming Mode (Connects to AP with 0%, Manual Config doesn't work.)
Added Wireless Router IP as DNS server
===========================
Network Tools
wlan0:avahi IP4 - 169.254.0.1 255.255.0.0 169.254.255.255 (Interface doesn't exitst)
wlan0
===========================
daniel@daniel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:0F:DA:D4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:38:0F:DA:D4  
          inet addr:169.254.8.69  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158114 (154.4 KiB)  TX bytes:158114 (154.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:f8200000-f8210000 

wlan0:ava Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:169.254.0.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f8200000-f8210000 

daniel@daniel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@daniel-laptop:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```

The *:avai makes me wonder if I did something wrong.

Also, is there a tarball of the wifi-radar program?

---

### Post by ntlam on 2007-09-06
I have the same problem. Some one suggested me to check the available wireless by using: sudo iwlist scan

---

### Post by helwitch on 2007-09-06
> This chipset showed up on my Acer Aspire 5050-3785. The lscpi program spit out the following info:
Do you mean lspci? cos when I do lscpi, I get command not found, but lspci shows me, among other things, the wireless adapter.

---

### Post by Alfred_McGee on 2007-09-06
Pasted all commands into terminal. Still no wifi conection, and lspci still says "Unkown device" for my ar5007eg card. My Feisty install is new. Are any of the Ubuntu updates necessary? Sometimes certain repositories may disable other repositories, so I am nervous about installing anything I'm not sure is necessary, but some of the updates seem to be related to wifi function.

---

### Post by bmartin on 2007-09-06
> **Alfred_McGee said:**
> lspci still says "Unkown device" for my ar5007eg card.
That's normal. If you want it to say the real device name, run **sudo update-pciids**. That updates the database that provides information on PCI/PCMCIA/built-in devices.
> **Alfred_McGee said:**
> My Feisty install is new. Are any of the Ubuntu updates necessary? Sometimes certain repositories may disable other repositories, so I am nervous about installing anything I'm not sure is necessary, but some of the updates seem to be related to wifi function.
AFAIK, no updates are necessary. I've never heard of one repository disabling another.

If you want to determin whether your WiFi device is detected or not, use **iwconfg** and it should tell you what wireless devices it detects as installed. If you want to determine whether it's correctly detecting network, use **sudo iwlist scanning**. To determine the status of the hardware, use **sudo lshw -C network**

---

### Post by Alfred_McGee on 2007-09-06
Thanks. Updating list of pci devices told me that my ar5007eg card is actually ar5006eg, despite what Windoze had said. Does it matter?

**sudo iwlist scanning** gave me this:

wlan1     No scan results

And **sudo lshw -C network** gave me this:

 *-network
       description: Wireless interface
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan1
       version: 01
       serial: 00:00:00:00:00:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.47+,11/15/2006,5.1.1.9 latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:54100000-5410ffff irq:17

Do you know what the problem is? Sorry if my questions are dumb!

---

### Post by bmartin on 2007-09-06
You might want to use the AR5006EG driver supplied to you with Windows... unless it's a Vista driver. I think I remember hearing something about NDISwrapper working with XP drivers only. Someone please verify this or correct me.

---

### Post by marshak on 2007-09-08
seriously don't know how to thank you enough. I've been trying different distro's, messing with files for about a month now. you have my wifi working with linux. Tonight I sleep a little easier. for those wondering, I simply followed his instructions verbatim.

---

### Post by lioninthesky on 2007-09-09
> **chadjohnson said:**
> Three things I noticed.

[LIST=1]
[*]The newest drivers from Acer don't work, but the ones on this thread do. Why is that?
[/LIST]

I had the same issue with my wife's Acer 5050.  I was receiving an "Unknown device" response from lspci.  After updating the PCI information, it resolved as a AR5006EG.  Still, this did not resolve the issue.  Looking further into the log files I found the infamous "HAL status 13" error message.  After doing some research I found this MadWifi bug report:

[http://madwifi.org/ticket/859]("http://madwifi.org/ticket/859")

Less specific to that card, and more generalized to the statement of "HAL status 13" error message is this bug report:

[http://madwifi.org/ticket/370]("http://madwifi.org/ticket/370")

I tried for hours to get the MadWifi to work with no success.  After finding those bug reports, I tried the ndiswrapper method step for step in this tutorial, and it worked flawlessly.

On a side note, beware of the killswitch issue:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/121415]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/121415")

There are several bug reports for the killswitch issue, which looks to be resolved for some people.  Still though, if you find Ubuntu locking up out of nowhere on your laptop, it's worth looking into.   Strangely, I had the issue until I stopped using the ieee80211_crypt_tkip module.  

Well, I got a bit off track there.  Hopefully the initial information helped you with regards to your wifi question.

---

### Post by Rockman4140 on 2007-09-10
Wow, alright, make sure to update the PCI IDs, I just updated mine, and mine is reading as a 5006EG, that could be an issue. I will download the new drivers and re-test.

---

### Post by Alfred_McGee on 2007-09-10
Although the Device Manager in Windowz had told me my card was an AR5007EG, updating the PCI IDs in Ubuntu told me that it was actually an AR5006EG. But whatever it is, **it works**, now thanks to bmartin and the instructions he posted at the beginning of this thread. Being a hardcore newbie, I had to stumble across the Wicd Manager (Applications-> Internet -> Wicd Manager) before I realized that it was working, but MANY thanks to bmartin! My computer, BTW, is an Acer Aspire 5570z.

---

### Post by bmartin on 2007-09-10
It's amazing to me how bad Acer laptops are supported by Linux (it's really not Linux's fault). They suffer from chronic ACPI problems. My girlfriend's Acer has no battery detected, the lid switch doesn't work, power management doesn't work, it overheats, etc. The card reader isn't supported in Linux at all (ENE); the Atheros chipset isn't supported by Madwifi.

The laptop was a steal at $400, but it's a Windows XP machine now (we removed Vista). I can't see running a dysfunction laptop in Linux, even though she's been using primarily Linux for about a year now.

---

### Post by khunphil on 2007-09-12
Hi,

I finally got my Wifi card to be recognized, using drivers XP not from Acer page. I had a hard time trying to do it, more than 2 weeks ;-)
Now, I can see the wireless networks, but cannot connect to it. After trying to acquire an address, it times out with the message :

(/var/log/message)
$ dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
$ kernel: [  747.384000] ndiswrapper (iw_set_ap_address:629): setting AP mac address failed (00010003)
$ kernel: [  751.592000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

The link is working, my other computer is connected (windows).
I have no idea if I need to configure something else now. Any hints ?

Thanks,

Philippe.

---

### Post by Rockman4140 on 2007-09-12
bmartin, you have done quite a deed helping us out. You have no clue how appreciated you are. I scavenged for a Ethernet cord and finally installed wicd, which is currently the reason I am posting on my Ubuntu side of the laptop.

About PCIID reporting a different card version, it uses the same driver, so that is not the issue. For some reason, the wireless manager just couldn't connect, bit wicd pulled through no problem. I highly recommend it, and if you can get net access through an ethernet cord, I would highly suggest an "apt-get update", fixed my dumb sound card issue. Now onto getting my crap video card working...

---

### Post by GraFfiX420 on 2007-09-12
After two days and about 5 different drivers, I finally got this working on my Toshiba Satellite A215-S4757. After updating the pciids and running lspci it identifies my card as a 5006eg, but it&#347; a 5007. I used the latest drivers for xp64.thanks a lot everyone.

---

### Post by mfdc1969 on 2007-09-15
Worked perfectly with Acer 5610Z (configuration 5610-2013)!

Thank you very much!!

Mike

---

### Post by davidthewatson on 2007-09-16
Worked for me on Acer Aspire 5570-2067. Thanks!

:)

---

### Post by jigneshmpatel on 2007-09-18
I have Acer Aspire AS5050-3785 2.2GHz ,AMD Turion(TM) 64 Laptop.

It also has missing wirelss driver. Does the process BMartin mentioned works for that too.

I highly appreciate prompt reply.

---

### Post by choifyken on 2007-09-20
i trisd,

but my notebook(Acer AS4520G),the wifi's LED doesn't work,i press the WIFI button again and again,no worlds play.
how can i know if the wifi card work?

---

### Post by bmartin on 2007-09-20
> **choifyken said:**
> how can i know if the wifi card work?
Post the output of the following commands:
```
ndiswrapper -l
sudo lshw -C network
```

---

### Post by John Mandrake on 2007-09-20
I tried your step by step procedure on my laptop. The result was that now the system can see my wireless device, but it can't see any wireless networks. 
Can you please help me?
Thank you.

> **bmartin said:**
> *** I personally recommend using the [wicd]("http://blakecmartin.googlepages.com/wicd.html") program for WiFi connectivity. It boasts built-in WPA support and has been successful where other network connection manager programs have failed.

Attached is a script and the necessary Windows drivers to get this card working. You can view the contents of the file by using the **cat** command from a terminal.

This chipset showed up on my Acer Aspire 5050-3785. The lspci program spit out the following info:
```
Atheros Unknown device 001c (rev 01)
```

Here is a step by step procedure to install the drivers manually (in case you don't want to use the script I wrote, or if it doesn't work properly). Open a terminal and copy/paste the following lines:

1. Download the ndiswrapper (v1.47) source code and AR5007EG Windows drivers:
```
wget http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1b.tar.gz
```
2. Extract the archive:
```
tar xvf atheros-ar5007eg-installer-0.1b.tar.gz
```
3. Ensure you have your kernel headers and the build essential package. **Make sure you copy/paste this instruction, as those are backticks, not single quotes!**
```
sudo aptitude update && sudo aptitude install linux-headers-`uname -r` build-essential
```
4. Blacklist the ath_pci kernel module (it doesn't support our chipset).
```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```
5. Compile ndiswrapper:
```
pushd atheros-ar5007eg-installer-0.1b/ndiswrapper-1.47/
sudo make uninstall
make
sudo make install
popd
```
6. Install the Windows drivers (using ndiswrapper):
```
pushd atheros-ar5007eg-installer-0.1b/ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
```
7. Make sure ndiswrapper loads up every time we start Linux:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```
8. Restart your computer.
```
sudo init 6
```

EDIT: I removed the instructions for using the script. It seemed to not work for anyone other than me. I checked it over several times and couldn't figure out why. The instructions and the script seem to perform the same set of operations.

---

### Post by bmartin on 2007-09-20
> **John Mandrake said:**
> I tried your step by step procedure on my laptop. The result was that now the system can see my wireless device, but it can't see any wireless networks. 
Can you please help me?
Thank you.
Try using the links below to install WICD or wifi-radar. People tend to have better luck with them.

---

### Post by John Mandrake on 2007-09-21
> **bmartin said:**
> Try using the links below to install WICD or wifi-radar. People tend to have better luck with them.


It seems this doesn't work...
Not only that my wireless card does not see any wireless connections, it looks like it is turned off. It just refuses to work.

jhon@john-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Am I missing something?
Thank you!

---

### Post by dr_cerebro on 2007-09-22
> **John Mandrake said:**
> It seems this doesn't work...
Not only that my wireless card does not see any wireless connections, it looks like it is turned off. It just refuses to work.

jhon@john-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Am I missing something?
Thank you!


First, thank you very much Mr. bmartin, I'm new at Linux, and the last two weeks I've been googleing A LOT, trying to make wireless work, I followed the steps of this HowTo, and finally get my Wifi Card recognized, but I can't go wireless.  I have exactly the same problem than Mr. Mandrake.  And Wicd, or Wifi radar don't detect any Wireless network.  My laptop is a Acer Aspire 5050-4872, and running Ubuntu Feisty Fawn.

iwconfig displays some differences:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s
          Encryption key:off
          Power Management:off
          Link Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any sugestions?

---

### Post by bmartin on 2007-09-22
Usually, when your device is detected but doesn't detect **any** networks, the problem is that your wireless radio is disabled. Usually either a switch on your computer or a keyboard combination can activate this (such as Fn+F2)... look for a key with a little radio tower symbol on it.

If there's a switch to enable/disable your wireless radio, it might behave the opposite way you expect it to, i.e., people have reported that setting their switch toward the transmit symbol disables it.

---

### Post by dr_cerebro on 2007-09-22
> **bmartin said:**
> Usually, when your device is detected but doesn't detect **any** networks, the problem is that your wireless radio is disabled. Usually either a switch on your computer or a keyboard combination can activate this (such as Fn+F2)... look for a key with a little radio tower symbol on it.

If there's a switch to enable/disable your wireless radio, it might behave the opposite way you expect it to, i.e., people have reported that setting their switch toward the transmit symbol disables it.

Yes, it almost worked.  I had to move the switch when loading, and it detected the wireless net, but, then it freezes.  I read somewhere than this computers need the acer_acpi driver to work properly.  I will try that and let you informed.

If you have any idea, please, post it.

Thank you.

---

### Post by Robin.Muilwijk on 2007-09-23
Very helpful thread, I recently bought a Toshiba A200-1K8 and with the described method I was able to get wireless working in a few minutes. No glitches, just copy/paste the commands, reboor, and connect...

---

### Post by dr_cerebro on 2007-09-23
Well, I'm close.
I made a fresh new install.  Disable restricted drivers for Atheros Card (ATH_HAL).
Updated my system.
Installed acer_acpi.
Follow each one of your steps.
Now it detects wireless networks available.  But if I try to connect, then it freezes.

Any ideas?

---

### Post by bmartin on 2007-09-24
> **dr_cerebro said:**
> Any ideas?
[These results]("http://www.google.com/search?hl=en&q=atheros+ndiswrapper+freeze&btnG=Google+Search") look hopeful. Please post your findings.

---

### Post by timelord726 on 2007-09-26
Just wanted to take the time to say thanks for a simple and well-written howto that got wireless working on my Acer Aspire 5100 (with AR5007EG)!  Much appreciated!

---

### Post by dr_cerebro on 2007-09-26
Well, acer_acpi helped me a lot.  It just freezes a little, and I just have to wait a couple of minutes and then try to start wireless network.  I could't make it without this HowTo. 
I'm writing this post with my Acer laptop via wireless.
Thank you very much.

---

### Post by clmcdanne on 2007-09-26
so far so good!  I was just about to give up on Ubuntu (and therefore network printer) and go back to openSUSE which recognized/configured the wifi card out of the box (but was not able to share Samsung ML-2510 networked printer).  coupled with wicd I am pleased and almost ready to throw MS Windows out the window! :popcorn:

---

### Post by Alfred_McGee on 2007-10-01
When finishing up an installation of Kismet, there is a **source=** line that must be filled in. It's in my */usr/local/etc/kismet.conf* file and must specify the driver, device, and description of the "capture source" (wifi card). If I have used the wonderful fix posted on this thread to run my wifi card, what should I enter on this line, or is running Kismet not an option for those who are using Ndiswrapper and a Windows driver?

---

### Post by bmartin on 2007-10-01
> **Alfred_McGee said:**
> what should I enter on this line, or is running Kismet not an option for those who are using Ndiswrapper and a Windows driver?
This is just a guess... I'd put **ndiswrapper** for the driver, the PCI ID of the device (you can find it using **ndiswrapper -l**... it's the value of the form xxxx:xxxx), and whatever you'd like for the description.

---

### Post by Alfred_McGee on 2007-10-01
Actually, the Kismet readme file says "Anything using ndiswrapper is using WINDOWS drivers AND CANNOT BE USED WITH KISMET." Sorry, I should have checked that documentation before posting. I'll just use an external card that I have. Thanks again!

---

### Post by tdrusk on 2007-10-01
I have to reinstall my Ubuntu every so often. I got tired of copying and pasting all of that. I wrote this and it worked flawlessly.

```
wget http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1c.tar.gz && tar xvf atheros-ar5007eg-installer-0.1c.tar.gz && sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential && echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist && pushd atheros-ar5007eg-installer-0.1c/ndiswrapper-1.48/ && sudo make uninstall && make && sudo make install && popd && pushd atheros-ar5007eg-installer-0.1c/ar5007eg/ && sudo ndiswrapper -i net5211.inf && popd && sudo modprobe ndiswrapper && echo "ndiswrapper" | sudo tee -a /etc/modules && sudo init 6
```

It's your guide linked together by a bunch of && signs.

---

### Post by bmartin on 2007-10-01
There actually is a script, but a bunch of people said it didn't work, so I didn't mention it... it's in the archive at the beginning.

---

### Post by tdrusk on 2007-10-01
> **bmartin said:**
> There actually is a script, but a bunch of people said it didn't work, so I didn't mention it... it's in the archive at the beginning.
Ah okay then. 

How hard would it be for me to make that into a script? I would like to have that knowledge.

---

### Post by bmartin on 2007-10-01
> **fuzzyhair said:**
> Ah okay then. 

How hard would it be for me to make that into a script? I would like to have that knowledge.
You basically just put the commands in a file. Since the script is written in BASH, you'd put **#!/bin/bash** at the top (this simply tells Linux to use BASH to interpret the file's contents). Then you can add comments (lines starting with a #) to indicate what the commands do. Comments are optional, of course, but they help other people understand what your scripts do. You'll also have to put "execute permissions" on the file. If the file is in the current directory and it's named **myinstaller**, you'd run **chmod 755 myinstaller** to make it executable.
```
#!/bin/bash
# retrieve and extract the installer
wget http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1c.tar.gz
tar xvf atheros-ar5007eg-installer-0.1c.tar.gz && sudo aptitude update
# retrieve code needed for installation
sudo aptitude install linux-headers-$(uname -r) build-essential
# blacklist the ath_pci driver; it doesn't work with our chipset
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
# change into the installation directory (temporarily)
pushd atheros-ar5007eg-installer-0.1c/ndiswrapper-1.48/
# uninstall the old ndiswrapper
sudo make uninstall
# compile ndiswrapper
make
# install ndiswrapper
sudo make install
# go back to the directory we were in before pushd
popd
# tell ndiswrapper to use the Windows driver
pushd atheros-ar5007eg-installer-0.1c/ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
# insert the ndiswrapper driver into the kernel
sudo modprobe ndiswrapper
# make the driver load up every time
echo "ndiswrapper" | sudo tee -a /etc/modules
# restart the computer
sudo init 6
```

---

### Post by tdrusk on 2007-10-01
> **bmartin said:**
> You basically just put the commands in a file. Since the script is written in BASH, you'd put **#!/bin/bash** at the top (this simply tells Linux to use BASH to interpret the file's contents). Then you can add comments (lines starting with a #) to indicate what the commands do. Comments are optional, of course, but they help other people understand what your scripts do. You'll also have to put "execute permissions" on the file. If the file is in the current directory and it's named **myinstaller**, you'd run **chmod 755 myinstaller** to make it executable.
```
#!/bin/bash
# retrieve and extract the installer
wget http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1c.tar.gz
tar xvf atheros-ar5007eg-installer-0.1c.tar.gz && sudo aptitude update
# retrieve code needed for installation
sudo aptitude install linux-headers-$(uname -r) build-essential
# blacklist the ath_pci driver; it doesn't work with our chipset
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
# change into the installation directory (temporarily)
pushd atheros-ar5007eg-installer-0.1c/ndiswrapper-1.48/
# uninstall the old ndiswrapper
sudo make uninstall
# compile ndiswrapper
make
# install ndiswrapper
sudo make install
# go back to the directory we were in before pushd
popd
# tell ndiswrapper to use the Windows driver
pushd atheros-ar5007eg-installer-0.1c/ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
# insert the ndiswrapper driver into the kernel
sudo modprobe ndiswrapper
# make the driver load up every time
echo "ndiswrapper" | sudo tee -a /etc/modules
# restart the computer
sudo init 6
```
Awesome!

Thanks a lot.

---

### Post by fishdude21 on 2007-10-01
Ok...i  can see my wireless card and eveyrthing now...the problem is now that i for some reason cannot connect to the internet.  I definantly have internet connection and i have it set on DHCP too but its not wanting to connect anyone know how to fix this?

---

### Post by bmartin on 2007-10-01
> **fishdude21 said:**
> Ok...i  can see my wireless card and eveyrthing now...the problem is now that i for some reason cannot connect to the internet.  I definantly have internet connection and i have it set on DHCP too but its not wanting to connect anyone know how to fix this?
That's the million dollar question. Frustratingly enough, this is the most common problem with WiFi in Linux. Try using WICD (see the link at the bottom of my post, where quotes usually go).

---

### Post by fishdude21 on 2007-10-02
I tried to install the wicd and im getting this error when i try to reload the repository

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Any idea what that means?  I know my internet is working because im on it right now...

---

### Post by hacienda_irrevocably on 2007-10-04
really am greatful the work for BMartin. not I understand, but step for step and the acer travelmate 2480-2968 she am working after 5 hours no one else helsp

---

### Post by Hmarroqu on 2007-10-06
computer freezes when i try to connect to network, thats right , ubuntu crashes...why ? i dont knw , any one know? btw if you can answer me asap this is a installation for a friend who is leaving in a day and his computer needs to wrk flawlessly. ....ubuntu is making me look bad so far

"connecting to a wap2"

non secure like "linksys" works fine.

---

### Post by rickc on 2007-10-07
> **Hmarroqu said:**
> computer freezes when i try to connect to network, thats right , ubuntu crashes...why ? i dont knw , any one know? btw if you can answer me asap this is a installation for a friend who is leaving in a day and his computer needs to wrk flawlessly. ....ubuntu is making me look bad so far

"connecting to a wap2"

non secure like "linksys" works fine.

I got the same thing going on....

Not sure why though.

---

### Post by Grinder on 2007-10-08
Awesome howto. 

I also had my laptop freeze up connecting to a WPA secured network. I switched to WEP 128 bit and the problem went away.

Any ideas why WPA locks up Ubuntu?

-Phil

---

### Post by bmartin on 2007-10-08
I don't have access to the router I'm connected to in order to try this, but many drivers aren't WPA compatible. This might be one of them. Did you install wpa-supplicant, and are you connecting using the wext driver? Have you tried using WICD?

---

### Post by Grinder on 2007-10-09
I do have wpa-supplicant installed. Not sure exactly what driver I have, I followed your directions at the beginning of the thread.

I have not tried WICD yet.

---

### Post by eeeandrew on 2007-10-09
Hi, I'm new to linux (as in I've been using it now for about an hour) I just installed 7.04 in dual boot with windows vista and tried the instructions on page 1 to get my card working. unfortunately I have no experience with the linux terminal so I got lost somewhere on page 2. I followed the instructions on page 1 exactly. it came through without errors (as far as I can see) but the wireless card does not show up in the networking wizard for me to connect nor can I find any other way to connect. can anyone post an idiot proof method? or do I just need to get a seperate wifi configuration tool?

---

### Post by bmartin on 2007-10-09
> **eeeandrew said:**
> can anyone post an idiot proof method?
There's a method on page 1 that's pretty idiot proof. Are you using a 32- or 64-bit version of Ubuntu?

There are graphical programs capable of install NDIS drivers. You need to use a Windows XP driver with NDISwrapper. The one you tried to install before was 32-bit. If you have a 64-bit version of Ubuntu, you're bound to run into all sorts of issues... and you'll need to find a 64-bit driver to use with NDISwrapper.

To check whether the driver is installed properly, try running **ndiswrapper -l** in a terminal and post the output here.

---

### Post by eeeandrew on 2007-10-09
how do I check if its 32 or 64 bit?

---

### Post by bmartin on 2007-10-09
uname -m

If it returns i386 or i686 or something like that, it's 32-bit. x86_64 indicates a 64-bit build.

What does **ndiswrapper -l** say?

---

### Post by eeeandrew on 2007-10-09
ndiswrapper -l said:

invalid driver: 5211

am not an expert but I think that means I've got the wrong driver:)

and uname -m came out as

i686

Laptop info: Toshiba Equium L40-10X, Intel 1.73 dual core processor(if it helps)

---

### Post by bmartin on 2007-10-09
> **eeeandrew said:**
> ndiswrapper -l said:

invalid driver: 5211

am not an expert but I think that means I've got the wrong driver:)
Yep.

Run these 6 commands, in this exact order. It doesn't matter where you run them from:
```
wget http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1c.tar.gz
tar xvf atheros-ar5007eg-installer-0.1c.tar.gz
pushd atheros-ar5007eg-installer-0.1c/ar5007eg/
sudo ndiswrapper -e 5211
sudo ndiswrapper -i net5211.inf
popd
```

---

### Post by eeeandrew on 2007-10-10
I just finished running those commands. Came across an error with the ndiswrapper -e command turns out it should have been -e net5211 but no harm done. Thanks for all your help couldn't have got this wireless working otherwise

---

### Post by eeeandrew on 2007-10-10
erm don't know if I'll get thrown off for blasphemy asking this here but...I rebooted my computer and logged onto the Vista partition after updating and setting up linux as per your instructions. According to Vista the drivers for the card are now missing... I can always find the drivers from somewhere the problem is that I want both OS to work at least for now so if I reinstall the drivers on vista will it affect the linux install?

---

### Post by bmartin on 2007-10-10
> **eeeandrew said:**
> erm don't know if I'll get thrown off for blasphemy asking <snip>
Nope. We're not anti-Windows (at least, most of us aren't). I keep Windows around because Fate, an older game, doesn't run in Wine or Cedega.

> **eeeandrew said:**
> According to Vista the drivers for the card are now missing... I can always find the drivers from somewhere the problem is that I want both OS to work at least for now so if I reinstall the drivers on vista will it affect the linux install?
Maybe. If the drivers load firmware into the card every time, then potentially yes. Try booting back and forth a couple times.

---

### Post by eeeandrew on 2007-10-11
feel like a bit of an idiot now that I've found the problem...when I posted that the laptop had been plugged in for a while. turns out my motherboard had shut the card down to stop it overheating.

---

### Post by bmartin on 2007-10-11
> **eeeandrew said:**
> feel like a bit of an idiot now that I've found the problem...when I posted that the laptop had been plugged in for a while. turns out my motherboard had shut the card down to stop it overheating.
Wow... I've never heard of that before. It interests me because I'm currently writing a program to act as a universal WiFi installer.

I'm looking for the causes of WiFi devices being installed correctly but refusing to work. Common causes are hardware (i.e., levers), software switches (i.e., push-buttons  and certain HP computers that only work when certain software is installed), and BIOS settings.

What did you have to do to get the card to turn on? Did it turn on when your computer cooled down, or did you have to change a setting?

---

### Post by Rockman4140 on 2007-10-11
Again, BMartin's effors are gladly appreciated by everyone, but I have a few more questions that I hope may help people.

Because of NDISwrapper, will Wireshark or SWScanner work? It says I can't capture from it, and I wonder if that is because of NDISwrapper or because of human error. Kismet works like that, so would the others follow suit?

---

### Post by sheriffdaone on 2007-10-11
I tried every method that you showed in this topic but none of them let my wireless to work.

Here is the lspci output of my laptop:

> 00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


and here is the ndiswrapper -l output:

> 
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


and here is the ifconfig output:

> 
eth0      Link encap:Ethernet  HWaddr 00:1B:38:3D:21:E1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe3d:21e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2039868 (1.9 MiB)  TX bytes:367913 (359.2 KiB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42025 (41.0 KiB)  TX bytes:42025 (41.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:9E:3D:C7:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Memory:f8200000-f8210000 



so i can't solve my problem due to something but i also cannot find my problem, if you can help me i'll be very happy 

Thank you

---

### Post by bmartin on 2007-10-11
> **Rockman4140 said:**
> Because of NDISwrapper, will Wireshark or SWScanner work? It says I can't capture from it, and I wonder if that is because of NDISwrapper or because of human error. Kismet works like that, so would the others follow suit?
According to [the NDISwrapper FAQ]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,faq/"), master and promiscuous modes are not supported, so network traffic analysis would be impossible. Feel free to put in a request for promiscuous mode support at [NDISwrapper's tracker]("http://sourceforge.net/tracker/?group_id=93482&atid=604453").

In other words, NDISwrapper probably won't do what you want it to. I don't know if the MadWiFi driver supports promiscuous mode, either, and it may or may not support the AR5007EG chipset at this point. I'm sorry that I can't be more helpful.

---

### Post by bmartin on 2007-10-11
> **sheriffdaone said:**
> I tried every method that you showed in this topic but none of them let my wireless to work.
It appears your wireless device is detected (it shows up as wlan0). It might be managed by either driver at this point. **lsmod | grep ath_pci** should have no output. If it shows the ath_pci kernel module as loaded, then it needs to be removed from memory. NDISwrapper is set up correctly and your device is detected.

Are you using encryption on the router? Many problems revolve around proper entry of WEP or WPA keys. Are you using the built-in networking program, or wifi-radar, or WICD?

---

### Post by sheriffdaone on 2007-10-11
> **bmartin said:**
> It appears your wireless device is detected (it shows up as wlan0). It might be managed by either driver at this point. **lsmod | grep ath_pci** should have no output. If it shows the ath_pci kernel module as loaded, then it needs to be removed from memory. NDISwrapper is set up correctly and your device is detected.

Are you using encryption on the router? Many problems revolve around proper entry of WEP or WPA keys. Are you using the built-in networking program, or wifi-radar, or WICD?

No i am not using encryption on the router, and i am using the build-in networking program. Should i use wifi-radar because i also installed wifi-radar but it doesn't also see my wireless network.

---

### Post by bmartin on 2007-10-11
> **sheriffdaone said:**
> No i am not using encryption on the router, and i am using the build-in networking program. Should i use wifi-radar because i also installed wifi-radar but it doesn't also see my wireless network.
No; if you could see the network but not connect, then I might suggest wifi-radar.

However, it sounds to me like the wireless radio isn't working. Usually there's a way to enable/disable it on every laptop. On mine, you press a button to enable/disable the scanning feature. Perhaps there's a button or lever on yours, or it might be the Fn+F2 keyboard combination, or perhaps even a setting in the BIOS.

When your wireless radio is working, **sudo iwlist scanning** should show wireless networks around you.

---

### Post by sheriffdaone on 2007-10-11
> **bmartin said:**
> No; if you could see the network but not connect, then I might suggest wifi-radar.

However, it sounds to me like the wireless radio isn't working. Usually there's a way to enable/disable it on every laptop. On mine, you press a button to enable/disable the scanning feature. Perhaps there's a button or lever on yours, or it might be the Fn+F2 keyboard combination, or perhaps even a setting in the BIOS.

When your wireless radio is working, **sudo iwlist scanning** should show wireless networks around you.

Well it looks like Fn + F8 should work but it didn't work at all. Can i see if enable or disable it by some command? I tried "dmesg" but it wasn't a realtime logger well it was realtime when i was using gentoo.

---

### Post by bmartin on 2007-10-11
I don't know any command that'll work. My girlfriend's Aspire 5050 has the killswitch kind where you slide a lever over in the front to enable/disable wireless.

---

### Post by eeeandrew on 2007-10-12
hi, again. to make the card work again I just left the laptop to cool down. I can't believe you've not heard of that before. most modern computers monitor their own temperatures and can do various things depending on how hot it gets. my power desktop that I just gave to my brother for example, if it gets too hot it turns on a big noisy fan and if its still too hot then it shuts down...I've heard theres some windows tools used by overclockers that will let u see the temperature and choose what happens and at what temperatures. I'll try and find the article

---

### Post by eeeandrew on 2007-10-12
me again, couldn't find the article on it but I did find a tool on the same site that says it has the temperature monitering stuff. don't know exactly what it will let you change coz I haven't tried it myself but hopefully it helps.

[http://www.pcworld.com/downloads/file/fid,64350/description.html](http://www.pcworld.com/downloads/file/fid,64350/description.html)

---

### Post by bmartin on 2007-10-12
> **eeeandrew said:**
> hi, again. to make the card work again I just left the laptop to cool down. I can't believe you've not heard of that before.
I've heard of different actions being taken when the computer gets too hot. I've never heard of the wireless shutting off because of it. That would bother me.

---

### Post by k33bz on 2007-10-12
ok, this wendsday i will be changing my acer 3680-2419 from a vista OS to Ubuntu Fiesty.  Its when i will be able to use my a LAN. 

Question though. I would like to know if WICD will work with airsnort?

---

### Post by bmartin on 2007-10-12
> **k33bz said:**
> ok, this wendsday i will be changing my acer 3680-2419 from a vista OS to Ubuntu Fiesty.  Its when i will be able to use my a LAN. 

Question though. I would like to know if WICD will work with airsnort?
The limiting factor here is not WICD, but rather NDISwrapper. NDISwrapper doesn't support **promiscuous mode**, which is required for capturing packets. If your chipset is supported by [MadWiFi]("http://madwifi.org"), you can use that driver instead. Then again, I don't know if MadWiFi supports promiscuous mode or not.

Promiscuous mode is often implemented in a proprietary manner, mean it'd have to be reverse-engineered in most cases, unless the company offered a FOSS implementation or a thorough specification to FOSS developers. The MadWiFi was afforded a specification for many chipsets back in the day, so promiscuous mode support might be available on some chipsets, but not others.

I personally recommended WICD, and to the best of my knowledge, it will not affect your ability to use airsnort. NDISwrapper, however, is not compatible. Check the MadWiFi page to see if it has any details.

---

### Post by k33bz on 2007-10-12
[QUOTE=bmartin;3521356]The limiting factor here is not WICD, but rather NDISwrapper. NDISwrapper doesn't support **promiscuous mode**, which is required for capturing packets. If your chipset is supported by [MadWiFi]("http://madwifi.org"), you can use that driver instead. Then again, I don't know if MadWiFi supports promiscuous mode or not.QUOTE]

I checked the page, didnt bother looking to see if it supports promiscuous mode or not, I was stopped at compatability. MasWiFi does not support my chipset.......

Oh well, as saying was just curious to see if it would, doesn't stop me from installing Ubuntu onto my laptop. I love ubuntu, and deeply miss using it. My CPU fried out on my Desktop awhile back and havnt had the chance to replace it yet.

So Wendsday the deadline to have Ubuntu back in my life. Hope I dont run into any other problems.

Thanks again bmartin.

K33BZ

---

### Post by eeeandrew on 2007-10-12
well yeah it is annoying but I suppose its less annoying and I'm less likely to lose data than if it were to just shut my computer down...and after using Vista for a month that seems like a very minor annoyance in comparison. Good luck with the wifi program sounds like an absoloutely massive task but it would be really useful.

---

### Post by abhi.datt on 2007-10-13
In my case it worked without errors in terms of recognizing the card and ifconfig now shows the device wlan0.
What puzzled me is that when I do iwscan list
It is says no networks found.

I used another program called wifi-radar, it also shows no networks available.

My network is very much alive and it's unrestricted (no WEP key)

What is that I'm not doing right?

Please help

---

### Post by bmartin on 2007-10-13
> **abhi.datt said:**
> In my case it worked without errors in terms of recognizing the card and ifconfig now shows the device wlan0.
What puzzled me is that when I do iwscan list
It is says no networks found.

I used another program called wifi-radar, it also shows no networks available.

My network is very much alive and it's unrestricted (no WEP key)

What is that I'm not doing right?
Your WiFi radio is turned off. There's probably a switch on your computer or a keyboard combination (e.g., Fn+F2) that turns the radio on/off. Sometimes it's in the BIOS. At any rate, once that's turned on, run **sudo iwlist scan** and you should see networks.

If you can't find a network using that command, no program will work.

---

### Post by abhi.datt on 2007-10-13
Bingo!! got that working THANKS

---

### Post by k33bz on 2007-10-14
so question is, how to i go about installing everything i need to get my wireless up and going with out my laptop connecting to internet?

Just need to know the the commands to use, and where to find the actual files, programs, and drives on net to be downloaded and transported via Flash Drive.


Thanks

nvm, i got it all on now took a little bit more time than i expected, but once i got the necessary files it was no problem at all.

thanks again.

---

### Post by buzz123 on 2007-10-14
hi 

i cannot get my AR5007EG working in Monitor Mode
the driver is loaded and i can surf with my wlan0

but

i cant get it work with airmon-ng. So everytime i start "airmon-ng start wlan0 11"
i get the following MSG:

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

wlan0           Unknown         ndiswrapper (MONITOR MODE NOT SUPPORTED)

-------------------

can anyone please help me get it working in Monitor Mode ?

---

### Post by bmartin on 2007-10-14
> **buzz123 said:**
> hi 

i cannot get my AR5007EG working in Monitor Mode
the driver is loaded and i can surf with my wlan0

but

i cant get it work with airmon-ng. So everytime i start "airmon-ng start wlan0 11"
i get the following MSG:

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

wlan0           Unknown         ndiswrapper (MONITOR MODE NOT SUPPORTED)

-------------------

can anyone please help me get it working in Monitor Mode ?
No.

No one can, unless you don't have an AR5007EG, or MadWiFi starts supporting your chipset. NDISwrapper only supports ad-hoc and managed modes. You could beg and plead with the developers, I suppose.

Developers use cards to reverse-engineer the specs. Here are some ideas I had, but none of them are practical, except the last:
[LIST=1]
[*]Donate your laptop to the MadWiFi team, with the condition that they implement the code to support your chipset.
[*]Wait until someone in the MadWiFi development team buys a new laptop with the chipset in it.
[*]Develop the code for the MadWiFi driver yourself and submit a patch.
[*]Get the specs for the promiscuous/monitor mode implementation for the AR5007EG chipset and submit them to the MadWiFi team.
[*]Find an obscure piece of code out there that someone wrote to take care of the problem.
[*]Buy another card for sniffing packets (something w/ an Intel chipset would be ideal).
[/LIST]

---

### Post by buzz123 on 2007-10-15
thx bmartin.

i think best way is to buy another wlan interface ;-)

---

### Post by dward526 on 2007-10-16
Shot myself in the foot...again

I tried this method and it did not work at home, after 2 weeks I bought a supported adapter and am waiting for it to come in the mail.  I found that at my college (I am going back to school for Computer Service and Networking...go fig) I can access the open wireless....so it seems my problems now lie with the config of my home network.  

Ah well, I am sure I can find another use for the usb wireless...live and learn.

---

### Post by bmartin on 2007-10-16
> **dward526 said:**
> I tried this method and it did not work at home, after 2 weeks I bought a supported adapter and am waiting for it to come in the mail.  I found that at my college (I am going back to school for Computer Service and Networking...go fig) I can access the open wireless....so it seems my problems now lie with the config of my home network.
Which program are you using to connect? The built-in one?

Some people have had to put quotes around their password or key to get it to work. I had to do that once when using a WEP key.

---

### Post by bradjinks81 on 2007-10-16
Worked Great! Thanks alot

---

### Post by dward526 on 2007-10-17
> **bmartin said:**
> Which program are you using to connect? The built-in one?

Some people have had to put quotes around their password or key to get it to work. I had to do that once when using a WEP key.

I actually got it to work now be not using wicd, but reinstalling the native gnome network manager.  I also had to change my home encryption protocol to wep, but it works great now.  Thanks a lot...I also found a use for my network adapter some where else:) !  Now I can kill vista completely on my laptop

The only issue is sometimes it sees no wireless networks (about 1 in 20 times), but a cold reboot fixes this.

---

### Post by bmartin on 2007-10-17
I got it to work w/ WPA using TKIP, but not AES.

---

### Post by wiscados on 2007-10-17
I didn't get it to work, but I didn't actually follow the howto.

If there is one thing I, not hate, but really dislike, is when howtos and guides to get network cards working include "download this and apt-get this". Thank you very much, but if I could do that I wouldn't need this doc, would I?

It happened all too often when I was trying to get wifi working on my desktop, which took me a few months.

I do understand that some have wired network and want their wireless to work too, but at least have an optional way to do it for us who really, really, really need it. 



ANYWAYS, what did was: I download the file in step 1 on my desktop, and transfer it to my laptop along with precompiled ndiswrapper .debs that I had on my desktop hard-drive, from when I needed it to get the desktop online.

Then I installed ndiswrapper, installed the driver, modprobed it, blacklisted ath_pci, and added 'ndiswrapper' to /etc/module. 

When I run 'ndiswrapper -l'  is says that the driver is installed and the hardware is present. And 'iwconfig' says pretty much the same as on my desktop.

However I don't know how to use it, how to turn it on. 

This would be a great time to say that I have a ATI Mobility Radeon HD 2400, that crashes X. (Though I got a copy of SELD 10.1 with a magazine and with that X runs, only 800x600, but still...)

I'm all CLI here!! I'm lost without the NetworkManager utility!

How do I turn it on!?!

---

### Post by Xenaco on 2007-10-17
There is an Atheros Linux open-source driver available at:

[[COLOR="Blue"]https://sourceforge.net/projects/madwifi/[/COLOR]]("https://sourceforge.net/projects/madwifi/")

It works for pci, pcmcia and usb devices.

---

### Post by bmartin on 2007-10-17
> **Xenaco said:**
> There is an Atheros Linux open-source driver available at:

[[COLOR="Blue"]https://sourceforge.net/projects/madwifi/[/COLOR]]("https://sourceforge.net/projects/madwifi/")

It works for pci, pcmcia and usb devices.
Except for the AR5007EG, which still isn't supported. See [the MadWiFi page]("http://madwifi.org/wiki/Compatibility/Atheros").

---

### Post by Alfred_McGee on 2007-10-18
bmartin once said that RutilT is the greatest wifi interface. That appears to be true, so I was wondering if it's possible to use it in this fix for the AR5007EG wifi card instead of wicd. I installed RutilT, but it seems to have disabled my wicd interface, so I guess I will have to uninstall it...

---

### Post by bmartin on 2007-10-18
> **Alfred_McGee said:**
> bmartin once said that RutilT is the greatest wifi interface. That appears to be true, so I was wondering if it's possible to use it in this fix for the AR5007EG wifi card instead of wicd. I installed RutilT, but it seems to have disabled my wicd interface, so I guess I will have to uninstall it...
That was before I found WICD. I think RutilT, which is quite great, was designed for RT chipsets. I seem to have a hard time getting RT stuff to work with other wireless connection managers. My parents have an RT chipset and that's the only WCM I can get it to work with.

Strangely enough, I can't get the connection to work consistently with Windows, so despite the fact that it's set up for dual-boot, they requested that I set Ubuntu as the default. I had to shell into my brother's computer (the one that receives port 22 requests to their router), then shell into my parents' computer from there to change the grub settings.

---

### Post by dca on 2007-10-18
The guide worked great for Gutsy, Aspire 5610z, & network-manager...  The problem, the signal is dropped after an hour or so and there's no way to get it back.  Sometimes when starting the laptop once the DE starts there's no wireless causing you to shutdown, wait a few secs and try again.  Peculiar.  What Gutsy does on start-up is different than Feisty.  Right after GRUB it displays some PCI error message and then moves on to starting the OS...  I'll try and jot it down next time.  The freeze everyone was talking about only happened to me in Feisty and it's still too tough to say if it was something I did wrong.

---

### Post by LEDZEP974 on 2007-10-19
:lolflag:Good morning, i hope you will excuse my bad english (I'm french).....and since last week...my english is out (Rugby World Cup...).
A great thanks to **B Martin** !!! I post this comment with my wifi conection on my TOSHIBA P200-12W !
It works fine ! 
Enjoy Ubuntu !

---

### Post by hacienda_irrevocably on 2007-10-19
update to gust of gobbins and is again brokered. I procedure one more to make report

+++++++

later after an i follow all procedure. still not good an not work. i type lspci an ehternet controller listed as AR500**6**EG. now it has wrong one in list, not AR500**7** EG, why?  restricted-manager say an hal is not active it saying. ndiswrapper saying net5211 is current. 

moment! iwlist made discoveries! an no clue what made to work... switch to gust of goblins frustrating!

---

### Post by dr_cerebro on 2007-10-21
Hi, great howto... but I have this problem:

```

[   30.469622] ndiswrapper version 1.48 loaded (smp=yes, preempt=no)
[   30.557701] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   30.557756] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net5211'
[   30.558316] ndiswrapper (load_wrap_driver:118): couldn't load driver net5211; check system log for messages from 'loadndisdriver'

```

---

### Post by bmartin on 2007-10-21
> **dr_cerebro said:**
> Hi, great howto... but I have this problem:
```
[   30.557701] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 
```
Only the 32-bit driver was included when I downloaded the AR5007EG driver. If you track down the 64-bit driver, I'll tell you how to install it. If you're dual-booting, it should be on your Windows partition.

---

### Post by bmartin on 2007-10-21
Actually... I found it. Try the following:
```
mkdir ~/tmp
cd ~/tmp
wget http://www.atheros.cz/download/drivers/ar5xxx/xp64-5.3.0.56-whql.zip
unzip -a xp64-5.3.0.56-whql.zip
sudo ndiswrapper -i net5211.inf
```

---

### Post by dr_cerebro on 2007-10-21
Thank you, I installed the 64 bit driver and now Wifi works perfect.
Thank you very much !

I made some modifications, just another way to install it, following your steps but with a modification, and, installing acer_acpi first because, otherwise, just do not work in this machine...

I'll be honored if you check the steps: [http://ubuntuforums.org/showthread.php?t=580672](http://ubuntuforums.org/showthread.php?t=580672) in page 2 and 3.

Thank you again

---

### Post by missingno on 2007-10-21
Thankyouthankyouthankyou! I've been trying to get ndiswrapper to work for a while with my AR5006EG under Gutsy, and this worked perfectly! Now my ethernet cable is no longer a leash for my laptop.

---

### Post by bmartin on 2007-10-21
> **dr_cerebro said:**
> Thank you, I installed the 64 bit driver and now Wifi works perfect.
Thank you very much !

I made some modifications, just another way to install it, following your steps but with a modification, and, installing acer_acpi first because, otherwise, just do not work in this machine...
That's awesome. I'm glad it works. I'm having a problem with a Linksys WUSB54GP right now. I can only get it to work with the prism54usb driver, but it's flaky and doesn't support WPA; it's also not working well w/ WEP.

Two suggestions for your steps; I looked them over, but I'm not going to actually try them:

When you want to retrieve multiple packages at once, it makes sense to use one command to get them both. The two **sudo aptitude install** commands can be merged into one:
```
sudo aptitude install build-essential linux-headers-$(uname -r)
```
And you can simplify the /home/YOUR USER NAME directory a couple of way. Either of these lines will work:
```
 mkdir $HOME/download
mkdir ~/download
```
$HOME is a BASH constant; it will always be equivalent to ~. However, ~ is a POSIX standard for referring to your home directory. All that means is that it's generally considered a better practice to use ~ instead of $HOME. POSIX standards work cross-platform and in different shells (BASH, KSH, CSH, etc.)

---

### Post by dr_cerebro on 2007-10-21
You are right.
Its easy that way, and those steps work too.

I will correct those steps. And I will see if someone has found how to make that Lynksys card to work fine.

Thank you again.

---

### Post by bmartin on 2007-10-21
> **dr_cerebro said:**
> You are right.
Its easy that way, and those steps work too.

I will correct those steps. And I will see if someone has found how to make that Lynksys card to work fine.

Thank you again.
You're welcome.

It seems that many people have that card working OK; but a lot of people are having the same problem as me. I've had that card working using the same driver and the same version of NDISwrapper on different computers.

I ended up hooking that computer up to a wired connection; we ran a long Ethernet cable under a couple doors using a tape measure and a twist tie. I really like to solve problems that seem to be inconsistent like that wireless adapter... but it wasn't worth it; it's my girlfriend's PC and we both prefer wired connections.

---

### Post by tdrusk on 2007-10-21
ath5k reports to work with this card. It seems like a pain to install it.

---

### Post by bmartin on 2007-10-21
> **tdrusk said:**
> ath5k reports to work with this card. It seems like a pain to install it.
Despite the fact that GIT is, in fact, very fast for what it does, it is a **very slow** checkout process.

If I can get the source code to compile and install, I'll put up instructions. I'll test it on my girlfriend's AR5007EG and if it works, I'll create a snapshot of it (which I could update periodically) and post instructions as an alternative to using NDISwrapper.

Thanks for the heads-up.

---

### Post by Alfred_McGee on 2007-10-22
Yes,   ath5k.org seems to have finally delivered on the promise to support the ar5007eg. For people like us, that's big news. Does anybody know what kind of network manager this system would use? Wicd is good, but it has certain limitations, too. With RutilT, for example, you never have to hit the "Refresh" button to see what's new in terms of the signal strength of your network.

---

### Post by bmartin on 2007-10-22
> **Alfred_McGee said:**
> Yes,   ath5k.org seems to have finally delivered on the promise to support the ar5007eg.
A big setback is that you either need to get the upstream kernel and compile it or download the entire GIT tree (enormous) and compile that. I haven't found an easy way to simply grab the source for the driver and compile it in. You might have to wait until the next Gutsy kernel (or perhaps more than 1 kernel version) before you see the ath5k kernel module.
> **Alfred_McGee said:**
> For people like us, that's big news. Does anybody know what kind of network manager this system would use? Wicd is good, but it has certain limitations, too. With RutilT, for example, you never have to hit the "Refresh" button to see what's new.
It should work with pretty much whatever you desire. RutilT was made for RT chipsets, I think, but it might work with other chipsets.

---

### Post by Alfred_McGee on 2007-10-22
RutilT looks as though it could support other wifi cards besides the RT chipset that I used it with. It even recognizes the ar5007eg under ndiswrapper, but of course it won't run it. Being able to run all wifi cards under one network manager would be convenient, especially if monitor mode were supported. The Wicd install page that bmartin set up mentions that Wicd won't run if certain other network managers are installed, and in any case it's nice to manage all your wifi cards in one place...

EDIT: I have managed to run both RutilT and WICD at the same time, for two different wifi cards. No serious problems.

---

### Post by Computer Cat on 2007-10-23
This solution works when I use the 32-bit version of Ubuntu (gusty or feisty), but not for when I use the 64-bit version (again for gusty or feisty)

---

### Post by bmartin on 2007-10-23
> **Computer Cat said:**
> This solution works when I use the 32-bit version of Ubuntu (gusty or feisty), but not for when I use the 64-bit version (again for gusty or feisty)
This was recently discussed on this thread.

Only the 32-bit version is provided. I posted a link to the 64-bit version; it was tested and works fine. If you want to use the 64-bit version of Ubuntu, you need to use the 64-bit driver.

I'll amend the instructions later today so that 64-bit users can get up-and-running.

---

### Post by bmartin on 2007-10-23
The instructions have been updated. 

Also, NDISwrapper is now bundled separately from the drivers, so you should get the newest version every time. I used a PHP redirect on one of my sites so that I can keep the newest version available simply by changing the URL on the site; the one in the instructions won't have to change.

---

### Post by ohzopants on 2007-10-23
Thanks for the great info on setting up wireless.

Also, thanks for the wcid recommendation.  I've had it installed for about 5 minutes and I already prefer it to the gnome one.

---

### Post by mi_were on 2007-10-26
It finally worked after I calmed down and followed the instructions literally!

Thanks

---

### Post by mi_were on 2007-10-26
I did get a string of errors after using ndiswrapper but after rebooting the wireless appears to be working. I will give it a once over once I get home.

---

### Post by SexyGorilla on 2007-10-27
I wanna kiss bmartin right n the mouth!

[http://www.codebucket.org/node/10](http://www.codebucket.org/node/10)

Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You!

---

### Post by mrukus on 2007-10-28
everything worked like a charm, no problem when i was entering the codes, just upon restart, i had to revert back to my last version of kubuntu.  when restarting my updated version it pauses and freezes, it does this only after i ran the codes.  thanks a bunch

---

### Post by rughalt on 2007-10-28
Hi
I succesfully installed ndiswrapper driver using your guide. Device is discovered by system, but, unforunately, when I try to do the "iwlist scan" i get nothing... maybe not exactly nothing - I get some crap, and not the WIFI networks I should.

For example, I get two networks with ESSID "", no connection strength. Thats weird, because in the same room, while using vista, I'm able to connect to my home WiFi network with maximum signal strength.

I've tried using different driver vesions (all for x86_64 arch, since I'm using 64bit ubuntu), different tools (including WCID, Wifi-radar and some more).

I have no idea why it isn't working. 

Thanks in advance for any help

---

### Post by gnu87 on 2007-10-28
I'm using ubuntu feisty on an acer travelmate 5510. the card's name is atheros ar5bxb63, your solution didn't work for me until i installed acerhk:[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/) . My card was recognized and i could scan for networks, but when i tried to connect, all programms stopped when trying to get an ip. Now connectivity is equal or even better than on vista. I used it on ubuntu-i386. There were two other xp drivers which worked: the one posted here: [http://ubuntuforums.org/showthread.php?t=503537&highlight=ar5bxb63](http://ubuntuforums.org/showthread.php?t=503537&highlight=ar5bxb63) and one from [www.atheros.cz](www.atheros.cz), but it took longer to connect with them. 
I did the same procedure on gutsy amd64, and i'm using it wireless right now, but it didn't  went that smooth. Network-Manager frozes one time or just stopped, but after a few tries and two reboots, i wonder why it's working now, 

thank's a lot for the howto !!!:) it helped much.

---

### Post by JoshOvki on 2007-10-28
Im using an Acer Aspire 5050 laptop and ive been having some awful trouble with my wifi.

The first time i used the instructions it worked... sometimes... half the time i didn't want to connect the other it would until i restarted and it wouldn't connect again.

So i started a fresh, reinstall ubuntu 7.10 and started again... this is where things get really confusing:

The instructions worked fine no problems at all, i rebooted and it finds the wireless networks in my area, i select my home one, enter the WEP key and..... it crashes... stone dead. Restart after about a 5 - 10 minuet wait its back up. So i try to connect again... and it dies again. Ok another reinstall third time luck an all. So i reinstall ubuntu again... follow the same instructions... see the network, try to connect... stone dead again. At this point I'm thinking maybe its something to do with my WEP key, so i turn off the WEP key on my router (Through my wired pc) restart my laptop try to connect... this time it doesn't ask for the WEP key... it just dies again. 

So i register and post, currently as i type my laptop is stone cold dead, I've left it trying to connect to the network and it just doesn't seem to be doing anything.

So does anyone have any ideas on whats happening to my poor laptop?

Thanks

Josh

---

### Post by dr_cerebro on 2007-10-28
> **JoshOvki said:**
> Im using an Acer Aspire 5050 laptop and ive been having some awful trouble with my wifi.

The first time i used the instructions it worked... sometimes... half the time i didn't want to connect the other it would until i restarted and it wouldn't connect again.

So i started a fresh, reinstall ubuntu 7.10 and started again... this is where things get really confusing:

The instructions worked fine no problems at all, i rebooted and it finds the wireless networks in my area, i select my home one, enter the WEP key and..... it crashes... stone dead. Restart after about a 5 - 10 minuet wait its back up. So i try to connect again... and it dies again. Ok another reinstall third time luck an all. So i reinstall ubuntu again... follow the same instructions... see the network, try to connect... stone dead again. At this point I'm thinking maybe its something to do with my WEP key, so i turn off the WEP key on my router (Through my wired pc) restart my laptop try to connect... this time it doesn't ask for the WEP key... it just dies again. 

So i register and post, currently as i type my laptop is stone cold dead, I've left it trying to connect to the network and it just doesn't seem to be doing anything.

So does anyone have any ideas on whats happening to my poor laptop?

Thanks

Josh

Did you install acer_acpi first?

---

### Post by JoshOvki on 2007-10-28
> **dr_cerebro said:**
> Did you install acer_acpi first?

No i didnt, but the device is shown as on and working. After using WICD ive found out that it dies then it gets to  

> Generating WPA configuration file...

---

### Post by The Only Joey on 2007-10-28
Hello all.

I have the exact wireless card as specified (AR5007EG) and did everything in the tutorial.
The led of my "Packard Bell EasyNote MX52" of my wireless is burning, i can see a lot of connections but i can not connect to any of them.
Open or Closed, i can not connect to any of them.
I use 7.10 GG.

Tried a lot of stuff.. nothing yet.

---

### Post by JoshOvki on 2007-10-28
Just an update, after a 4th install and install kubuntu-desktop  before trying anything with wireless i have got it not freezeing! However.... i still cant connect, im in the same situation as The Only Joey

---

### Post by boyce on 2007-10-29
Hi, thanks everyone for all the great info in this thread,

I am at that really frustrating stage where I think everything is set up fine but can not see any wireless networks. 
I have read the whole thread and it seems as though most people at this stage are advised to check the wifi radio button.

On my laptop (fujitsu-siemens amilo li1718) the button for the wifi is above the keyboard.
I am currently dual-booting with Vista, where it toggles fine. It has no effect in Ubuntu so I went into the Bios settings and found an option to enable Wireless, Now, when I boot into Vista it connects automatically (before, the Bios option was disabled).

I fear that the same should be happening when I boot into Ubuntu, and since it isn't working, the problem lies somewhere elsewhere? 

Also, if everything was working ok, should I automatically see some networks from the start ( with "sudo iwlist scanning"  or do I have to create new one? (the only options I see when I unplug ethernet cable are Create New,,,Connect to Other...Manual Configuration)

Please can you advise me?

---

### Post by John Mandrake on 2007-10-30
> **bmartin said:**
> Usually, when your device is detected but doesn't detect **any** networks, the problem is that your wireless radio is disabled. Usually either a switch on your computer or a keyboard combination can activate this (such as Fn+F2)... look for a key with a little radio tower symbol on it.

If there's a switch to enable/disable your wireless radio, it might behave the opposite way you expect it to, i.e., people have reported that setting their switch toward the transmit symbol disables it.

I'm back... I gave up last time for it was not working and lost my patience.

I figured that the problem is indeed the wifi switch, but, on my Fujitsu notebook, the switch only works when it's driver is instaled. The problem is, I couldn't find a linux driver, and neither the .inf file, so I could use ndiswraper with that to.

In other words, my wireless card is working, but I see no way to turn it on. Any ideas?

---

### Post by mhyk on 2007-10-31
How come it doesn't work for me? I follwed the steps.
when i do 
dmsesg | grep ndiswrapper

[   41.000834] ndiswrapper version 1.49 loaded (smp=yes, preempt=no)
[   41.131295] ndiswrapper: driver net5211 (,01/20/2006,4.2.2.7) loaded
[   41.132466] ndiswrapper (NdisWriteErrorLogEntry:191): log: C0001389, count: 4, return_address: dcc585d4
[   41.132470] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xd3a68600
[   41.132472] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x28
[   41.132474] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xdcbb0000
[   41.132477] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xdcbb0000
[   41.132542] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[   41.132547] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   41.132558] ndiswrapper (mp_halt:259): device dbd1f500 is not initialized - not halting
[   41.132565] ndiswrapper: device eth%d removed
[   41.132585] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[   41.134359] usbcore: registered new interface driver ndiswrapper

can someone help me with this?

---

### Post by desiath on 2007-11-02
Hi, thanks for the tutorial. I followed your steps on my Acer 5103 for my Feisty and worked perfectly. Then I had a fresh install of Gutsy and followed the same steps (I used KnetworkManager this time) and it worked, though not perfectly this time. 

After the first installation I got wireless directly and started using it. After a reboot however I lost it. no wlan0 at all with iwconfig. After a reboot it came back and I used it without any problems. But it goes on like this, chaotic, after a boot I don't know if I am going to see it or not.

Any ideas?

---

### Post by ourmaninparis on 2007-11-03
Thanks very much for this guide. It worked perfectly and I'm a complete newby. I used it for Gutsy Gibbon.

---

### Post by Greg F on 2007-11-03
The guide worked perfectly on my MSI ER710X notebook. Thank you for the hard work you put into creating the guide. The step-by-step instructions really help a noob like me.

---

### Post by tdrusk on 2007-11-04
This guide works for Debian Etch with the minimal base system installed. Just replace being logged in with su and remove the sudos.

I figured I would just report this for some extra info.

---

### Post by cogumbreiro on 2007-11-04
Worked for me, thanks!

I've installed it in a LG R405. Here's my blog post about it:
[http://irrepupavel.blogspot.com/2007/11/installing-ubuntu-gutsy-gibbon-710-into.html](http://irrepupavel.blogspot.com/2007/11/installing-ubuntu-gutsy-gibbon-710-into.html)

---

### Post by hatebreeder on 2007-11-05
hi everyone,

i have an Acer Aspire 5100 with that atheros wireless internet problem

i have 32 bit ubuntu 7.10

my wireless internet sometimes works.... i think its only when i boot with my eithernet plugged in, maybe it activates or turns on my wireless hardware

it works fine when i boot into vista

i seriously don't know what to do, ive tried so many things including everything that was on the first page of this thread

when i type: ndiswrapper -l

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)



when i type: lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
04:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
04:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
04:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
04:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
04:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)



do i have a boot problem or a linux driver problem???

---

### Post by warped6 on 2007-11-05
So here is my experience. I got it up and running under Feisty (64 bit) and then updated to Gutsy(64 bit). I lost wireless and reran the setup howto. I got my wireless back, but...

I can't seem to connect to any secure wireless access points. I've tried both at home and at work. I tried changing almost every setting.

Anybody else have any luck with this type of situation?

---

### Post by The_Great_Beast on 2007-11-06
I've got an Acer Aspire 5315-2153 and this worked great thanks :)

---

### Post by neo-cortex on 2007-11-07
> **cogumbreiro said:**
> Worked for me, thanks!

I've installed it in a LG R405. Here's my blog post about it:
[http://irrepupavel.blogspot.com/2007/11/installing-ubuntu-gutsy-gibbon-710-into.html](http://irrepupavel.blogspot.com/2007/11/installing-ubuntu-gutsy-gibbon-710-into.html)

Oh gosh! I wish I got wireless working on my Ubuntu install on my LG R405. It didn't work so I had to come back to vista :(

---

### Post by Ryadovoy on 2007-11-08
I've a problem installing the windows driver. I'm using Ubuntu 7.10 Gutsy Gibbon on an Aspire 7520G with an Atheros AR5007EG card.
when i try to execute this command: "sudo ndiswrapper -i net5211.inf" it says that ndiswrapper doesnt exists.

Can anyone help me with this problem??

---

### Post by tdrusk on 2007-11-08
> **Ryadovoy said:**
> I've a problem installing the windows driver. I'm using Ubuntu 7.10 Gutsy Gibbon on an Aspire 7520G with an Atheros AR5007EG card.
when i try to execute this command: "sudo ndiswrapper -i net5211.inf" it says that ndiswrapper doesnt exists.

Can anyone help me with this problem??

reinstall ndiswrapper. It's not seeing it.

---

### Post by nudaz on 2007-11-08
LG laptop SA8X2A: This worked perfectly for me, thank you.I just followed the instructions in the first post.

I only have one question: will this survive the update/upgrade process or will I have to do it again after updates?

Thanks heaps ;)

---

### Post by ParaGuy on 2007-11-10
Laptop = Acer Aspire 5100-3357, Wireless card - Atheros AR5007EG. I have tried these help steps with both Kubuntu and Ubuntu latest versions and it does not work for me. I have the correct windows driver for my card. Is there anyone who can post directions for using a windows driver from scratch for us noobs?

Thanks
PG

---

### Post by Ryadovoy on 2007-11-11
I tried to reinstall, but now it says that it can't find ndiswrapper (or doesn't recognise).

---

### Post by Ryadovoy on 2007-11-11
Solved, I have now wireless internet connection.

---

### Post by laltomar on 2007-11-12
I have  Toshiba U305-S7448

These steps did NOT work for me until I removed the HAL restricted driver using the Synaptic Package Manager.  It worked fine once I did that.

---

### Post by brothermalcolm on 2007-11-15
> **bmartin said:**
> [COLOR="Red"]Make sure you use the appropriate version of the drivers for your version of Linux. If you're using a 64-bit version of Linux, you **must** use 64-bit drivers. You can check this using the following command:
```
getconf LONG_BIT
```

I personally recommend using the [wicd]("http://blakecmartin.googlepages.com/wicd.html") program for WiFi connectivity. It boasts built-in WPA support and has been successful where other network connection manager programs have failed.
[/COLOR]

This chipset showed up on my Acer Aspire 5050-3785. The lspci program spit out the following info:
```
Atheros Unknown device 001c (rev 01)
```
It also has been incorrectly labeled as an AR5006X device, in some cases.

Here is a step by step procedure to install the drivers manually (in case you don't want to use the script I wrote, or if it doesn't work properly). Open a terminal and copy/paste the following lines:

1a. Download the ndiswrapper (v1.48) source code and AR5007EG Windows drivers:
```
wget http://wifix.sourceforge.net/software.php?title=ndiswrapper
```
1b. Download the AR5007EG Windows XP drivers:
If you're using a 32-bit version of Linux, use this command:
```
wget http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz
```
For 64-bits of blazing WiFi glory, use this:
```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```
2. Extract the archives:
```
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
```
3. Ensure you have your kernel headers and the build essential package.
```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```
4. Blacklist the ath_pci kernel module (it doesn't support our chipset).
```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```
5. Compile ndiswrapper:
```
pushd ndiswrapper-*/
sudo make uninstall
make
sudo make install
popd
```
6. Install the Windows drivers (using ndiswrapper):
```
pushd */ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
```
7. Make sure ndiswrapper loads up every time we start Linux:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```
8. Restart your computer.
```
sudo init 6
```

=====
FAQ
=====
Q: Linux seems to see my device now, but it can't see any networks. What can I do now?
A: This frequently happens on built-in devices. There's usually either
[LIST]
[*]A switch on your computer somewhere that toggles whether the wireless radio is on or off (BEWARE! Some of these are very unintuitive. The setting that may seem like "on" may be "on" and vice-versa.)
[*]A keyboard combination that enables/disables the wireless connection (usually Fn+F2).
[*]A setting in the BIOS that needs to be changed. This can be frustrating to track down. The BIOS is the program that loads before your OS. When your computer first boots, there's a key you can press to go into the system setup; look for a wireless setting in there that you can enable.
[/LIST]

Q: I can see wireless networks. Why can't connect to any of them?
A: There are a couple options to try here. If you're using WICD to connect and WPA encryption, under preferences, make sure that for WPA Supplicant Driver, you're using WEXT (make sure you've installed WPA_Supplicant). If you're using WEP, try putting your key in "double quotes". If you can't connect to an encrypted network, try removing they key to see if that's the problem. If you're not using WICD, try it out; many people have been successful simply after switching the wireless connection manager program to WICD.

Q: None of this worked. I'm no closer to having my wireless working than I was when I first installed my OS. What's wrong?
A: Try running **sudo modprobe ndiswrapper**; the program should run silently. If you get any output, there's a problem. If the ndiswrapper,ko file can't be found, run **sudo depmod -ae**, then try **sudo modprobe ndiswrapper** again.

If you installed your OS a long time ago, some people have had better success with a fresh install. Try installing the drivers while running from the Live CD.
=====
EDIT: I removed the instructions for using the script. It seemed to not work for anyone other than me. I checked it over several times and couldn't figure out why. The instructions and the script seem to perform the same set of operations.


Hi thanks alot for the valuable instructions. Worked brilliantly after following through carefully and reboot.

I use an acer TravelMate 6231 laptop with dualboot Gutsy (upgraded from Feisty) and Vista. From device manager in Vista it tells me I have an AR5007EG. 

 I'd just like to post because some of the instructions had to be slightly modified when I used them, and secondly because there doesn't seem to be any posts on the forums for this particualr laptop model. Also, I did this a similar thing before I updated to Gutsy from Feisty, and it was the update that seemed to have messed the wlan up.

So here's a list of things I changed on the quoted instructions (alot of them are realy obvious but could prevent success for newbie users like myself):
- in step 2, dont forget to change the filenames of the tarballs to the ones you actually downloaded (my advice is to use tab completion)
- i skipped step 3 because it said it would remove alot of files from my computer 
- in step 5, when using the uninstall command, make sure you do as the output suggests and repeat until there are no more 'removing ...' lines appearing in the output
- in step 6 you might want to just pushd then use tab completion to get you to the destination directory (where the file net5211.inf is located)
- NOTE: if you were copying commands from the script that was posted on page 12 of this thread, you will notice the links dont work... instead use the links given by quoted instructions above

Basically, if you have no clue about commands in linux, you would probably get a bit stuck using the instructions word for word. This may be a reason why some ppl on this thread cant get it working if they only used the commands or the script like a black box. Hope this extra commentary can help ppl who are stuck. :)

---

### Post by dskid807 on 2007-11-16
I have followed the instructions but ubuntu says I have an AR5006EG when I know it is the 7EG. Does anyone have a fix?

---

### Post by inversis on 2007-11-17
Hi people. Thnks for the thread!

I also have an AR5007EG. I've reinstalled ubuntu several times, the problem is allways the same (i've read many guides..): it works in the first time (after first reboot). Then, on second reboot, it stop detecting any networks.


sudo ndiswrapper -v
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version:        1.49
vermagic:       2.6.22-14-generic SMP mod_unload 586 
```

ndiswrapper -l
```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```
   
sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ef:4f:cb
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:4f:07:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.49+,11/15/2006,5.1.1.9 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:19:DB:EF:4F:CB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

BTW, the computer is an LG E500-LP55P (chipset intel gl960)

with this, can someone help me please? :S

---

### Post by PogMoThoin on 2007-11-17
Hi all,

Been posting in [this]("http://ubuntuforums.org/showthread.php?t=615768") thread, decided i might get better response here.

My wifi card details ar as follows:
> 05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
Subsystem: AMBIT Microsystem Corp. Unknown device 0428
Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Interrupt: pin A routed to IRQ 19
Region 0: Memory at d0000000 (64-bit, non-prefetchable) [disabled] [size=64K]
Capabilities: [40] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
Address: 00000000 Data: 0000
Capabilities: [60] Express Legacy Endpoint IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
Device: Latency L0s <512ns, L1 <64us
Device: AtnBtn- AtnInd- PwrInd-
Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
Link: Latency L0s <512ns, L1 <64us
Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
Link: Speed 2.5Gb/s, Width x1
Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
Vector table: BAR=0 offset=00000000
PBA: BAR=0 offset=00000000

sudo lshw -C network
> *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:e4:3d:c5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.0.11 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s


Been trying to follow this guide, got ndiswapper & Xp drivers using the commands, i get as far as extracting the archives, this is the output i get when i try:
> colm@l33t-str33t-2:~$ tar xvf ar5007eg-*.tar.gz
ar5007eg-32-0.2/
ar5007eg-32-0.2/ar5007eg/
ar5007eg-32-0.2/ar5007eg/net5211.inf
ar5007eg-32-0.2/ar5007eg/ar5211.sys
ar5007eg-32-0.2/README
colm@l33t-str33t-2:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
What am i doing wrong? Can some1 lookover it & tell me whats wrong?

---

### Post by wilerk on 2007-11-18
Thank you very much for the original poster, it works like a charm for me with your steps!

I have a AR5006eg though, but Wifi-Radar picks up the networks around me!

---

### Post by laki42 on 2007-11-18
Really thanks for the thread, after a week of desperate tryings I've finally made my wifi work (actually I don't know how, because I did a lot of reinstalls but wifi-radar fixed the whole thing at the end).
BTW I'm new to Ubuntu but I've got a feeling that I'll say goodbye to my XP very soon :) The only thing that wasn't working in my Gutsy so far is now working, so the only reason to keep my WIN is playing games :D

---

### Post by awatts on 2007-11-21
So I'm running Gutsy on my new ASUS f3ka laptop.  The only issue I'm still having is with the ar5007eg.  I followed the instructions and tried to connect with network manager. Of course I could not connect.  so I installed WICD and gave it a go.  sure enough it connected, only thing was it disconnected (or rather went into limited or local connectivity)  I can only stay connected for like 20 seconds before this happens...sometimes my network will not show up at all in WICD after a period of time.  Also, the signal strength is also extremely low (3% in an area that had 5 bars under vista.)  Should i be trying other drivers, installing different versions of ndis, going back to feisty, or messing with wifi-radar?  Based on the results of this thread you would think i could get it to work. Any thoughts would be appreciated.

---

### Post by JonathanSteenbrugge on 2007-11-26
In my case the card works fine now. Thanks for the help. It is true that when I reboot the computer, the card stops working. I don't know what the problem is. Someone any Idea?

When I shut down and restart after that, everything is ok...

---

### Post by coltcannon on 2007-11-26
I picked up a Toshiba Satellite a135-s7403 on black friday. Ive gotten everything to work except the wireless (reliably). The chipset is the atheros ar5006eg. Like many others it works fine after the initial reboot. If I have to reset again it will no longer recognize any wifi networks. I can post info if there is any help on this problem.

---

### Post by dominik_ap on 2007-11-27
Hi, i have just installed kubuntu gutsy gibbon on my new laptop acer aspire and wifi doesnt work...

i tried this guide but it didnt help...

lspci:
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.

dmesg: this i found
[   17.892000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   17.892000] ndiswrapper (load_sys_files:216): couldn't prepare driver 'netathr'
[   17.956000] ndiswrapper (load_wrap_driver:118): couldn't load driver netathr; check system log for messages from 'loadndisdriver'


ndiswrapper -l
bcmwl5 : driver installed
bcmwl6 : driver installed
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
netathr : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


as you can see i tried to install more drivers, but i dont know which one is right...
i got some CD with drivers for my laptop, but drivers from it doesnt work

How should i repair it? Do you know how to start wifi on my laptop? Thanks

Dominik Franek

---

### Post by coltcannon on 2007-11-27
So Im surprised to come home to the wifi working. I left for work and started the software update this morning. Got home restarted and wifi was operational. Im afraid to move it back to its home. Thanks for the how to.

---

### Post by inversis on 2007-11-28
The guide worked for me by adding at the end:
$ sudo ndiswrapper -ma
$ sudo ndiswrapper -mi

But I still cant connect fine to [http://www.eduroam.org/](http://www.eduroam.org/) witch is an WIFI connection on my University. (WPA enterprise - PEAP - TKIP - CA certificate)
Sometimes it does, sometimes it doesn't. And after some seconds connected, connection name becomes "unkown". After 20min, I lost connection.
It doesn't work like that on Windows Vista/XP or MAC.

In my house it works just fine (normal home WPA)

---

### Post by YiZuSc on 2007-11-30
Thank you very much Bmartin, i really appreciate your How/To it worked great for my acer 5050-4872 running Ubuntu x86_64

For
> **PogMoThoin said:**
> Hi all,

Been posting in [this]("http://ubuntuforums.org/showthread.php?t=615768") thread, decided i might get better response here.

My wifi card details ar as follows:


sudo lshw -C network



Been trying to follow this guide, got ndiswapper & Xp drivers using the commands, i get as far as extracting the archives, this is the output i get when i try:

What am i doing wrong? Can some1 lookover it & tell me whats wrong?

I was having the same problems like you, i just realized that i was just a bit left from acomplish... i am new at this but i think what you have left to do is this.

3. Ensure you have your kernel headers and the build essential package.
Code:

sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential

then...
7. Make sure ndiswrapper loads up every time we start Linux:
Code:

sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules

Just restart and check if its working. If not, try Blacklisting the ath_pci or very that is already done, and plz dont Blacklist ath_hal as i did maybe...

Then again Thank you very much to Bmartin

---

### Post by jpblock82 on 2007-11-30
THIS STEP....

wget [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)


gives me the following results:

jeremy@jpblock-3100:~$ wget [http://blakecmartin.googlepages.com/arg5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/arg5007eg-32-0.2.tar.gz)
--13:01:06--  [http://blakecmartin.googlepages.com/arg5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/arg5007eg-32-0.2.tar.gz)
           => `arg5007eg-32-0.2.tar.gz'
Resolving blakecmartin.googlepages.com... 72.14.203.118
Connecting to blakecmartin.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:01:07 ERROR 404: Not Found.

Sup with that????

---

### Post by DemonBob on 2007-12-03
Madwifi Patch  for this card: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Madwifi Other Card Thread: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Patch was removed from Madwifi due to API Breakage on non I386/686 platforms. I was able to grab a new link to it from #eeepc channel

Download, source + patch [http://quaggaspace.org/eee/madwifi-eee.tar.bz2](http://quaggaspace.org/eee/madwifi-eee.tar.bz2).

It does work. 

Madwifi is talking to Athero's about getting this working across all platforms, and included in an offical release. Right now it only works on i386 and not x64. It does work on Acer 5315. 

> Last but not least: meanwhile it was approved that the patch was contributed by Atheros. We are currently talking to them about how to proceed in order to get AR5007 support into MadWifi properly (means: not just for i386, but for all platforms, to prevent ABI breakage). Please stay tuned, we will keep you updated.

Quote above was taken from ticket 1679

lsmod | grep ath output

```

ath_rate_sample        15232  1 
ath_pci               114600  0 
wlan                  211376  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280544  3 ath_rate_sample,ath_pci

```

dmesg output

```

[   15.652000] ath_hal: module license 'Proprietary' taints kernel.
[   15.652000] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[   15.728000] wlan: 0.8.4.2 (svn r2756)
[   15.760000] ath_pci: 0.9.4.5 (svn r2756)
[   15.760000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   15.760000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   16.248000] ath_pci: switching rfkill capability off
[   16.324000] ath_rate_sample: 1.2 (svn r2756)
[   16.324000] ath_pci: switching per-packet transmit power control off
[   16.324000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   16.324000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   16.324000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   16.324000] wifi0: mac 14.2 phy 7.0 radio 10.2
[   16.324000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   16.324000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   16.324000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   16.324000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   16.324000] wifi0: Use hw queue 8 for CAB traffic
[   16.324000] wifi0: Use hw queue 9 for beacons
[   16.344000] wifi0: Atheros 5424/2424: mem=0x54100000, irq=19

```

---

### Post by event on 2007-12-06
> **DemonBob said:**
> Madwifi Patch  for this card: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Madwifi Other Card Thread: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Patch was removed from Madwifi due to API Breakage on non I386/686 platforms. I was able to grab a new link to it from #eeepc channel

Download, source + patch [http://quaggaspace.org/eee/madwifi-eee.tar.bz2](http://quaggaspace.org/eee/madwifi-eee.tar.bz2).

It does work. 

Madwifi is talking to Athero's about getting this working across all platforms, and included in an offical release. Right now it only works on i386 and not x64. It does work on Acer 5315. 



Quote above was taken from ticket 1679

lsmod | grep ath output

```

ath_rate_sample        15232  1 
ath_pci               114600  0 
wlan                  211376  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280544  3 ath_rate_sample,ath_pci

```

dmesg output

```

[   15.652000] ath_hal: module license 'Proprietary' taints kernel.
[   15.652000] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[   15.728000] wlan: 0.8.4.2 (svn r2756)
[   15.760000] ath_pci: 0.9.4.5 (svn r2756)
[   15.760000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   15.760000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   16.248000] ath_pci: switching rfkill capability off
[   16.324000] ath_rate_sample: 1.2 (svn r2756)
[   16.324000] ath_pci: switching per-packet transmit power control off
[   16.324000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   16.324000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   16.324000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   16.324000] wifi0: mac 14.2 phy 7.0 radio 10.2
[   16.324000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   16.324000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   16.324000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   16.324000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   16.324000] wifi0: Use hw queue 8 for CAB traffic
[   16.324000] wifi0: Use hw queue 9 for beacons
[   16.344000] wifi0: Atheros 5424/2424: mem=0x54100000, irq=19

```

Worked for me when nothing else worked. ndiswrapper worked in kubuntu, but only this madwifi patch worked for me in ubuntu. Thanks!!

I have an Acer 5570Z. (5570-2977)

---

### Post by aletomsic on 2007-12-07
pleaseeeee help!!! running on ubuntu gutsy, 64 bits, atheros ar5007eg wireless. i did follow every step but errors came when i was trying to compile ndiswrapper:

alek@alek-laptop:~/ndiswrapper-1.5$ make

make -C driver
make[1]: Entering directory `/home/alek/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/alek/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/alek/ndiswrapper-1.5/driver/loader.o
/home/alek/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/alek/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/alek/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/alek/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/alek/ndiswrapper-1.5/driver'
make: *** [all] Error 2
alek@alek-laptop:~/ndiswrapper-1.5$ 


any ideas?? thank you

---

### Post by joewandy on 2007-12-07
I encountered the same problem when I tried to compile ndiswrapper version 1.50 (got it from wget in the steps).

Go here and get version 1.49. Compile it again, and it should be okay.

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

---

### Post by Jeztastic on 2007-12-09
> **DemonBob said:**
> Madwifi Patch  for this card: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Madwifi Other Card Thread: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Patch was removed from Madwifi due to API Breakage on non I386/686 platforms. I was able to grab a new link to it from #eeepc channel

Download, source + patch [http://quaggaspace.org/eee/madwifi-eee.tar.bz2](http://quaggaspace.org/eee/madwifi-eee.tar.bz2).

It does work. 

Madwifi is talking to Athero's about getting this working across all platforms, and included in an offical release. Right now it only works on i386 and not x64. It does work on Acer 5315. 

Please could I get a step-by-step on haw to install this? I'm sorry, but I'm a total n00b, and a lot of this stuff is beyond me. Not even sure if I have midwifi. I tried to download it, but you have to compile it and it looks pretty complex.

Thanks.

---

### Post by xodeus on 2007-12-09
Yes. it could be very nice with installation instructions for the madwifi patch. Could anyone please provide instructions?

---

### Post by residentsa on 2007-12-11
Thanks a lot for writing this.  I was not able to get Ndiswrapper 1.50 to compile correctly but the guide worked perfectly with Ndiswrapper 1.49.

---

### Post by Stuart Soloway on 2007-12-12
This worked for me, and I want to thank Blake for posting the directions.  I had been banging my head against a brick wall (metaphorically) for a week trying to get my wireless up.  But I ran into one problem that I hope others can avoid.  (I doubt I would have had a problem had I not been a relative beginner to Ubuntu and Linux.)  I couldn't build ndiswrapper.

The uninstall complained that it was trying to delete directories.  I think I manually deleted the directories it was complaining about, and then things were OK.  

But then the make failed with compiler errors!  I was about to throw my laptop out the window, when I decided to check if I had the most recent rev.  I don't remember the details, but I went to the sourceforge site for ndiswrapper and downloaded rev 1.50.  For some reason, Blake's command had retrieved rev 1.5, which must have been different.  I don't understand the difference, but the build worked with 1.50.

I then loaded wicd, and after making some guesses as to how to translate my router's security config I was up and running.

Stu

---

### Post by aletomsic on 2007-12-12
after running the following:
```

alek@alek-laptop:~/ndiswrapper-1.5$ sudo make uninstall 
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper
/bin/rm: no se puede borrar `/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper': Es un directorio
make: *** [uninstall] Error 1
alek@alek-laptop:~/ndiswrapper-1.5$ make
make -C driver
make[1]: se ingresa al directorio `/home/alek/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/alek/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/alek/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/alek/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/alek/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/alek/ndiswrapper-1.5/driver/loader.o
/home/alek/ndiswrapper-1.5/driver/loader.c: En la función ‘register_devices’:
/home/alek/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ no tiene un miembro llamado ‘owner’
make[3]: *** [/home/alek/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/alek/ndiswrapper-1.5/driver] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/home/alek/ndiswrapper-1.5/driver'
make: *** [all] Error 2

```

please help! this is killing!

---

### Post by Fritzwr on 2007-12-12
I am attempting to use this tutorial to install a wireless driver on my Toshiba Satelite Pro A210 in Gutsy amd64. However when type the command "make" in step 5 i get the following error:

fritz@Fritz2:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/fritz/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/fritz/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/fritz/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/fritz/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/fritz/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/fritz/ndiswrapper-1.5/driver/loader.o
/home/fritz/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/fritz/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/fritz/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/fritz/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/fritz/ndiswrapper-1.5/driver'
make: *** [all] Error 2"
 Any ideas?

---

### Post by danwood76 on 2007-12-13
There is a patch for the latest madwifi which allows the use of the AR5007EG so you dont have to use ndiswrapper.

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Follow the directions in post 11.

When I had ndiswrapper it used to regularly crash for no reason with no recovery but a restart.

regards,
Danny

---

### Post by sanctified-x on 2007-12-16
But it still won't connect no matter how many times I put in my PassPhrase.
I had it working once at an earlier time so I am trying to use the same settings? The HEX settings? And that won't work either. Neither will any of the others.

I know my Pass is right. I use it on Vista whenever I reinstall and I can type it with my eyes closed. ( sigh ) And to think I had so much hope as soon as I saw those blue bars pop up. Now I can't connect and they just look as if they are taunting me (lol ).

---

### Post by danwood76 on 2007-12-17
try the madwifi driver with the patch, I can confirm it working on the abit airpace card, and others have reported it working on laptops aswell!

---

### Post by sanctified-x on 2007-12-17
MadWifi is great and all, but the instructions on the site look liek complete gibberish to me. I agree with you, though. After I sucessfully had my wireless up and running, the damn thing kept crashing. Sigh. I will have to do another fresh install but the good thing is I have done it so many times I know all the comand line scripts by heart.

Not quite sure if that is a good thing... (lol)

---

### Post by hellkiller on 2007-12-18
Can somebody tell me the instructions to install madwifi patched driver. Thanks. When I try to patch it fails. Step-by-step:

1. Download madwifi-0.9.3.3.tar.gz
2. Download madwifi-ng-0933.ar2425.20071130.i386.patch
3. tar -xvzf madwifi-0.9.3.3.tar.gz
4. cd madwifi-0.9.3.3
5. copy madwifi-ng-0933.ar2425.20071130.i386.patch to madwifi-0.9.3.3 dir
5. patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch

> rahnev@Slack:~/Desktop/Atheros New/madwifi-0.9.3.3$ patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch
patching file hal/ah.h
Hunk #1 FAILED at 33.
Hunk #2 FAILED at 416.
Hunk #3 FAILED at 441.
Hunk #4 FAILED at 488.
Hunk #5 FAILED at 674.
Hunk #6 FAILED at 711.
6 out of 6 hunks FAILED -- saving rejects to file hal/ah.h.rej
patching file hal/public/i386-elf.hal.o.uu
Hunk #1 FAILED at 33.
Hunk #2 FAILED at 3284.
Hunk #3 FAILED at 3374.
Hunk #4 FAILED at 3382.
Hunk #5 FAILED at 3470.
Hunk #6 FAILED at 3479.
Hunk #7 FAILED at 3567.
Hunk #8 FAILED at 3607.
Hunk #9 FAILED at 3615.
Hunk #10 FAILED at 3623.
Hunk #11 FAILED at 4415.
Hunk #12 FAILED at 4425.
Hunk #13 FAILED at 5472.
Hunk #14 FAILED at 5532.
Hunk #15 FAILED at 5562.
Hunk #16 FAILED at 5576.
Hunk #17 FAILED at 5592.
Hunk #18 FAILED at 5606.
Hunk #19 FAILED at 5637.
Hunk #20 FAILED at 5651.
Hunk #21 FAILED at 5666.
21 out of 21 hunks FAILED -- saving rejects to file hal/public/i386-elf.hal.o.uu.rej
patching file hal/public/i386-elf.inc
patching file hal/public/i386-elf.opt_ah.h
Hunk #1 FAILED at 7.
1 out of 1 hunk FAILED -- saving rejects to file hal/public/i386-elf.opt_ah.h.rej
patching file hal/version.h
Hunk #1 FAILED at 33.
1 out of 1 hunk FAILED -- saving rejects to file hal/version.h.rej


---

### Post by danwood76 on 2007-12-18
Luckily for you there is already a patched version the madwifi team have released.

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

so you just have to untar that and follow the standard install instructions from the madwifi site. this only works on 32 bit x86 systems btw.

regards,
Danny

---

### Post by hellkiller on 2007-12-19
The patch was for a specific version of the driver. Problem solved. Patch's working :)

---

### Post by jmatbastos on 2007-12-21
Atheros AR5005G on Acer Aspire 5051AWXMi (AMD 64) on Ubuntu dapper drake 6.06 LTS 

with kernel
Linux 2.6.15-29-amd64-generic #1 SMP PREEMPT Mon Sep 24 17:19:55 UTC 2007 x86_64 GNU/Linux

managed to make wlan0 work with xp64-4.2.1.1-whql.zip
[http://www.atheros.cz/download.php?atheros=AR5005G&system=2](http://www.atheros.cz/download.php?atheros=AR5005G&system=2)



> **Adntu said:**
> I tried these and all the others, at last I tried the XP driver I got from :
[http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1)
and that worked, now I am posting using wlan.
thanks guys

---

### Post by BenHobbs on 2007-12-24
bmartin,

Thank you so very much for your guide. I followed your directions word by word and I'm now surfing on my lappy =) Thanks!!!

Acer Aspire 3680-2682

---

### Post by Raja Lakshminarayan on 2007-12-25
bmartin,

Thanks a ton for the directions. I'm posting this through my wireless connection to the net.

Thanks,
Raja, INDIA

---

### Post by go_beep_yourself on 2007-12-27
HELP!!!!!!!!! I HAVE NO INTERNET WITH UBUNTU

I tried using Vista x86 and x64 drivers with ndiswrapper. Neither
appeared to work.I thought I had to use ndiswrapper, but as I was
browsing around the web to find the windows driver, I found a linux
driver, so I began to follow the directions, but got stuck while
running a command didn't work. I have no experience with wireless in
Linux.

```
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ls
ifcfg-wlan0  release_note    wlan0dhcp  wpa_supplicant-0.4.9.tar.gz
makedrv      rtl8185.tar.gz  wlan0down
readme       stack.tar.gz    wlan0up
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ cat readme
RTL8185 Linux Driver v1027.0823.2007 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK/WPA2PSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
        rtl8185.tar.gz
        stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
        wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
        wpa_supplicant-0.4.9.tar.gz

    (6)Example of supplicant configuration file
        wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules
from source code and start the nic:

        (1)Build up the driver from the source code
                ./makedrv

        (2)Load the driver module to kernel and start up nic
                ./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
                ./wlan0rmv
                ./wlan0down
                ./wlan0up
            should be OK.
           )
        (3)Refer to < Set wireless lan MIBs > to set Wireless LAN
specific parameters.





< Set wireless lan MIBs >
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]
where

        parameter explaination          [parameters]
        -----------------------         -------------
        Show available chan and freq    freq / channel
        Show and Scan BSS and IBSS      scan[ning]
        Show supported bit-rate         rate / bit[rate]
        Show Power Management mode      power

For example:

        iwlist wlan0 channel
        iwlist wlan0 scan
        iwlist wlan0 rate
        iwlist wlan0 power


Driver also supports "iwconfig", manipulate driver private ioctls, to set MIBs.

        iwconfig wlan0 [parameters] [val]
where

        parameter explaination      [parameters]                [val]
constraints
        -----------------------     -------------
------------------
        Connect to AP by address    ap                          [essid]
        Set the essid, join (I)BSS  essid                       [mac_addr]
        Set operation mode          mode                        {Managed|Ad-hoc}
        Set keys and security mode  key / enc[ryption]
{N|open|restricted|off}


For example:

        iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
        iwconfig wlan0 essid "ap_name"
        iwconfig wlan0 mode Ad-hoc
        iwconfig wlan0 mode essid "name" mode Ad-hoc
        iwconfig wlan0 key 0123456789 [2] open
        iwconfig wlan0 key off
        iwconfig wlan0 key restricted [3] 0123456789

< Getting IP address >
After start up the nic, the network needs to obtain an IP address
before transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0
IP_ADDRESS" command, or using DHCP.

If using DHCP, setting steps is as below:

        (1)connect to an AP via "iwconfig" settings
                iwconfig wlan0 essid [name]     or
                iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

        (2)run the script which run the dhclient
                ./wlan0dhcp
           or
                dhcpcd wlan0
                (Some network admins require that you use the
                hostname and domainname provided by the DHCP server.
                In that case, use
                dhcpcd -HD wlan0)



< WPAPSK >
WPA_SUPPLICANT help the network to communicate under the protection of
WPAPSK mechanism

        (1)Unpack source code of WPA supplicant:
                tar -zxvf wpa_supplicant-0.4.9.tar.gz
                cd wpa_supplicant-0.4.9

        (2)Create .config file:
                cp defconfig .config

        (3)Edit .config file, uncomment the following line:
                #CONFIG_DRIVER_IPW=y.

        (4)Build WPA supplicant:
                make

        If make error for lack of <include/md5.h>, install the openssl lib:
         1. Install the openssl lib from corresponding installation disc:
            Fedora Core 2/3/4/5/6/7(openssl-0.9.71x-xx),
            Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
            Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl),
            Gentoo(dev-libs/openssl), etc.
         2. Download the openssl open source package from
www.openssl.org, build and install it.

        (5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
        For example, the following setting in "wpa1.conf" means SSID
to join is "BufAG54_Ch6"
        and its passphrase is "87654321".

                network={
                        ssid="BufAG54_Ch6"
                        proto=WPA
                        key_mgmt=WPA-PSK
                        pairwise=CCMP TKIP
                        group=CCMP TKIP WEP104 WEP40
                        psk="87654321"
                        priority=2
                }
        Note: 1. proto=WPA for WPA, proto=RSN for WPA2.
              2. If you want to connect an AP which works under WPA2
mixed mode, you'd better
                 use Realtek customed wpa_supplicant package.


        (6)Execute WPA supplicant (Assume 8185 and related modules had
been loaded):
                ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$   ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko
rm -rf /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/tmp
make -C /lib/modules/2.6.22.9chris1/build
M=/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211 CC=gcc
modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:
In function 'ieee80211_softmac_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241:
warning: assignment from incompatible pointer type
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_aes_encrypt':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:88:
warning: passing argument 1 of 'crypto_cipher_encrypt_one' from
incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:110:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:127:
warning: passing argument 1 of 'crypto_free_cipher' from incompatible
pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_deinit':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:144:
warning: passing argument 1 of 'crypto_free_cipher' from incompatible
pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_set_key':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:422:
warning: passing argument 1 of 'crypto_cipher_setkey' from
incompatible pointer type
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/tmp
make -C /lib/modules/2.6.22.9chris1/build
M=/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185 CC=gcc
modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'proc_get_stats_hw':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:375:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:376:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:379:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:380:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:383:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:384:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'check_tx_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:909:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:909:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:910:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:910:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'alloc_tx_desc_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1592:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1592:
warning: cast to pointer from integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'alloc_rx_desc_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1770:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1770:
warning: cast to pointer from integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'rtl8180_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3159:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522:
warning: 'deprecated_irq_flag' is deprecated (declared at
include/linux/interrupt.h:66)
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522:
warning: passing argument 2 of 'request_irq' from incompatible pointer
type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
At top level:
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:579:
warning: 'r8180_get_wireless_stats' defined but not used
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_sa2400.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_93cx6.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_max2820.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_gct.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8225.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8225z2.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8255.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_softmac_stop_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "free_ieee80211_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_wap_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wake_queue_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_rx_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_mode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_is_shortslot"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_freq_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_name_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_rate_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_rate_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_ps_tx_ack"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_freq_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_is_54g"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_stop_queue_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_scan_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_essid_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_scan_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_mode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_get_beacon"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_rawtx_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_encode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_stop_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_wap_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_power_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_encode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_softmac_start_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wlan_frequencies_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_power_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "alloc_ieee80211_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_reset_queue"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_essid_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_start_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation
not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation
not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8180.ko': -1 Operation not permitted
wlan0: ERROR while getting interface flags: No such device
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ sudo ./wlan0up
[sudo] password for chris:
wlan0: ERROR while getting interface flags: No such device
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$
```

Why does it say wlan0, no such device? I appended this to my
/etc/network/interfaces

```
iface wlan0 inet dhcp

auto wlan0


```
and I restarted the networking service.

---

### Post by prescottp on 2007-12-31
I keep getting this error when I try to go through step 5 of the process, as described on page 1 of this thread...

```
penguin@300below-laptop:~/ndiswrapper-1.5$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper': Is a directory
make: *** [uninstall] Error 1
penguin@300below-laptop:~/ndiswrapper-1.5$ 
```

Any ideas??

---

### Post by go_beep_yourself on 2007-12-31
> **prescottp said:**
> I keep getting this error when I try to go through step 5 of the process, as described on page 1 of this thread...

```
penguin@300below-laptop:~/ndiswrapper-1.5$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper': Is a directory
make: *** [uninstall] Error 1
penguin@300below-laptop:~/ndiswrapper-1.5$ 
```

Any ideas??

Notice this message.

> [COLOR="Red"]Run uninstall as many times as necessary until no "removing" messages appear below.[/COLOR]

What it is saying is to run this command several times until nothing is getting removed anymore.

sudo make uninstall

---

### Post by danwood76 on 2007-12-31
If you still get that error message after re running try to remove the module manually by doing:

```

sudo rm -R /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper

```

then re run the sudo make uninstall

regards,
Danny

---

### Post by prescottp on 2007-12-31
GoBeep-- I tried it like 20 times... Then I tried Danny's and that worked.  I'm not sure why it worked that way though-- perhaps I was leaving out the sudo before the rm command, as I tried to remove it manually with a recursive option, too.  Thanks for the help.  I'll let you know soon how the rest of the install goes.

---

### Post by prescottp on 2007-12-31
Now I'm having this problem:

```
penguin@300below-laptop:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/penguin/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/penguin/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/penguin/ndiswrapper-1.5/driver/hal.o
Assembler messages:
Fatal error: can't create /home/penguin/ndiswrapper-1.5/driver/.tmp_hal.o: Permission denied
make[3]: *** [/home/penguin/ndiswrapper-1.5/driver/hal.o] Error 2
make[2]: *** [_module_/home/penguin/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/penguin/ndiswrapper-1.5/driver'
make: *** [all] Error 2
penguin@300below-laptop:~/ndiswrapper-1.5$ 

```

---

### Post by go_beep_yourself on 2007-12-31
> **danwood76 said:**
> If you still get that error message after re running try to remove the module manually by doing:

```

sudo rm -R /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper

```

then re run the sudo make uninstall

regards,
Danny

Would you please help me uninstall a linux wireless driver (rtl8185_linux_26.1027.0823.2007) that did not work? I posted in the big code block above. I've tried removing several different ways. I tried "sudo make uninstall", "sudo ./makedrv uninstall". Neither worked :(

---

### Post by prescottp on 2007-12-31
So then I tried to continue on the #5 from the first post in the thread...

```
penguin@300below-laptop:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/penguin/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/penguin/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/penguin/ndiswrapper-1.5/driver/hal.o
Assembler messages:
Fatal error: can't create /home/penguin/ndiswrapper-1.5/driver/.tmp_hal.o: Permission denied
make[3]: *** [/home/penguin/ndiswrapper-1.5/driver/hal.o] Error 2
make[2]: *** [_module_/home/penguin/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/penguin/ndiswrapper-1.5/driver'
make: *** [all] Error 2
penguin@300below-laptop:~/ndiswrapper-1.5$ sudo make install
make -C driver install
make[1]: Entering directory `/home/penguin/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/penguin/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/penguin/ndiswrapper-1.5/driver/loader.o
/home/penguin/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/penguin/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/penguin/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/penguin/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/penguin/ndiswrapper-1.5/driver'
make: *** [install] Error 2
penguin@300below-laptop:~/ndiswrapper-1.5$ 

```

All to no avail.  Any ideas?

---

### Post by prescottp on 2007-12-31
So then I removed EVERYTHING and re-extracted.  Here's what I have now...

```
penguin@300below-laptop:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/penguin/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/penguin/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/penguin/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/penguin/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/penguin/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/penguin/ndiswrapper-1.5/driver/loader.o
/home/penguin/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/penguin/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/penguin/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/penguin/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/penguin/ndiswrapper-1.5/driver'
make: *** [all] Error 2
penguin@300below-laptop:~/ndiswrapper-1.5$ 

```

---

### Post by tdrusk on 2007-12-31
Anyone want to update the guide so it uses ndiswrapper 1.51

---

### Post by go_beep_yourself on 2007-12-31
> **tdrusk said:**
> Anyone want to update the guide so it uses ndiswrapper 1.51

Is the latest version of ndiswrapper in the ubuntu repositories?

---

### Post by prescottp on 2008-01-03
Alright I figured out how to get the wireless working.  Apparently it was downloading 1.5 and not 1.51.  However, now that the wireless is working, I still can't get it to finish the connection.  It can see all the wireless networks in the area, but it won't get an IP address.  I thought it was something to do with WPA and a TKIP key, but when I turned the security off it still wouldn't get an IP address...  It wouldn't work with a manual IP either, even with all the other settings plugged in.  Does anyone have any ideas as to why that's going on?  I'm using Wicd... Does it have something to do with that?

---

### Post by bwtranch on 2008-01-03
Re: #264 Actually I don't. I do know that a Belkin 7050 works right out of the box and it's $35 at walmart. Don't use roaming and use WPA. You might have to re-boot and make sure you have your ESSID right. Edit: Oh yeah, no wrapper required.

---

### Post by aprilie on 2008-01-10
helo I use ubuntu 7.10 and my wireless is not work I tray you advice which you post but it stil not work if do you know how to install driver for acer 5570z using ubuntu 7.10 please tell me how:confused:

---

### Post by xodeus on 2008-01-10
> **danwood76 said:**
> There is a patch for the latest madwifi which allows the use of the AR5007EG so you dont have to use ndiswrapper.

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Follow the directions in post 11.

When I had ndiswrapper it used to regularly crash for no reason with no recovery but a restart.

regards,
Danny
> **danwood76 said:**
> Luckily for you there is already a patched version the madwifi team have released.

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

so you just have to untar that and follow the standard install instructions from the madwifi site. this only works on 32 bit x86 systems btw.

regards,
Danny

Could anyone post a step by step to install this one?
maybe pack it to a deb or make a script that will do the work?
Cause I'm returning to linux, but can't use my neighbours LAN cable for more than 5 minutes

---

### Post by Jeztastic on 2008-01-11
> **xodeus said:**
> Could anyone post a step by step to install this one?
maybe pack it to a deb or make a script that will do the work?
Cause I'm returning to linux, but can't use my neighbours LAN cable for more than 5 minutes

+1

The instructions on the site are incomprehensible to a n00b like myself.

---

### Post by fmzw on 2008-01-12
Nice try! It works for me!
My notepad is ThinkPad R61.
I have posted my installation process here:
[http://techbuffalo.blogspot.com/2008/01/try-ubuntu-wireless.html](http://techbuffalo.blogspot.com/2008/01/try-ubuntu-wireless.html)

---

### Post by xodeus on 2008-01-12
> **Jeztastic said:**
> +1

The instructions on the site are incomprehensible to a n00b like myself.
that's great. I can follow the instructions but I almost always get errors. So when compiling the madwifi driver I got this message. can anyone help?
```
mariusz@mariusz-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/mariusz/Desktop/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath/if_ath.o
  CC [M]  /home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath/if_ath_pci.o
  LD [M]  /home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath/ath_pci.o
  CC [M]  /home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/ah_os.o
  HOSTCC  /home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: At top level:
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'main':
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/mariusz/Desktop/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/mariusz/Desktop/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
mariusz@mariusz-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ 

```

I found out that I had to install build-essential package...
Now I can follow this polish howto: [http://forum.ubuntu.pl/showthread.php?t=61317&highlight=5007eg](http://forum.ubuntu.pl/showthread.php?t=61317&highlight=5007eg)

---

### Post by fissionmailed on 2008-01-13
I have a problem. I have a Satellite 215 S5818, with an Atheros AR5007EG.   I've tried ndiswrapper a million times and something goes wrong.  I can get linux to see it just fine. It shows it has wlan0 and all.  But it won't show up in Network Manager and I've tried WICD.  I ONCE got it to work off and on but I had to reinstall the OS due to me screwing something up and now for the life of me I can't get it to work,  When it did work, it was very iffy and some times Network Manager would just freeze, BUT it worked some times. Any ideas guys?

---

### Post by tad1073 on 2008-01-14
Is there any support for an AR5416 D-link Extreme G 64 bit on 32bit ubuntu, or do I need to change to 64 bit ubuntu?

```

00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:01.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:03.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 4f)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
01:04.0 SCSI storage controller: LSI Logic / Symbios Logic 53c895a (rev 01)
01:05.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 08)
01:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
01:07.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
05:01.0 RAID bus controller: Digital Equipment Corporation DECchip 21554 (rev 01)

```

---

### Post by xodeus on 2008-01-14
> **fissionmailed said:**
> I have a problem. I have a Satellite 215 S5818, with an Atheros AR5007EG.   I've tried ndiswrapper a million times and something goes wrong.  I can get linux to see it just fine. It shows it has wlan0 and all.  But it won't show up in Network Manager and I've tried WICD.  I ONCE got it to work off and on but I had to reinstall the OS due to me screwing something up and now for the life of me I can't get it to work,  When it did work, it was very iffy and some times Network Manager would just freeze, BUT it worked some times. Any ideas guys?
If you're running on a i386 pltform then you could maybe try compiling madwifi from source with the Atheros 5007EG patch?
Because I got it running without any problems on my Mint.
Instructions, translated from polish to english:
> 
1. get this version of madwifi madwifi:
[http://snapshots.madwifi.org/madwifi…0071018.tar.gz](http://snapshots.madwifi.org/madwifi…0071018.tar.gz)

2. get this patch:
[http://madwifi.org/attachment/ticket…tch?format=raw](http://madwifi.org/attachment/ticket…tch?format=raw)

3. extract madwifi

4. Browse to the extracted folder

5. Copy/Move the patch to the extracted folder and lauch terminal and cd into the folder

6. Patch madwifi:
patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch

7. make

8. sudo make install

10. Now remove ath_pci in your restricted drivers manager and restart. If your wireless does not work at this point continue here:

11. sudo modprobe ath_pci

12. sudo modprobe wlan_scan_sta

13. Now you can look for aviable networks in your Network Manager.


---

### Post by tad1073 on 2008-01-14
What am I doing wrong I had a look at this and the drivers are the same.
```
Card: D-Link Rangebooster N Desktop Adapter DWA-542 
Chipset: Atheros unknown device 0023 (rev 01) PCI
pciid: 168c:0023
Driver: net5416; Driver available on accompanying CD
Other: Installed on Xandros Home Desktop 4 Premium, with WPA.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)
```
but why can't i get mine to work?

---

### Post by fissionmailed on 2008-01-15
> **xodeus said:**
> If you're running on a i386 pltform then you could maybe try compiling madwifi from source with the Atheros 5007EG patch?
Because I got it running without any problems on my Mint.
Instructions, translated from polish to english:

Nope, running a 64 bit version.  I'd just wondering, even with ndiswrapper and a windows driver it won't work.  But I got it to one time. :confused:

---

### Post by xodeus on 2008-01-15
This can be really tricky to get it working. I tried and tried and tried with ndiswrapper and never got it working. 
But madwifi and atheros are working on a solution to implent the drivers for all platform to next release of madwifi.

---

### Post by fissionmailed on 2008-01-15
> **xodeus said:**
> This can be really tricky to get it working. I tried and tried and tried with ndiswrapper and never got it working. 
But madwifi and atheros are working on a solution to implent the drivers for all platform to next release of madwifi.

:\

Maybe I should just buy a cheap USB wireless card.   I swear though, it's so irritating when I got it to work one time even if it was shaky and now I can't to save my life. I just hope they come out with it soon.

---

### Post by istredd on 2008-01-15
Thanks alot!

Worked for me at Acer Extensa 5220 and Linux Mint Daryna (Based on Feisty), but using ndiswrapper 1.51

---

### Post by phidia on 2008-01-18
I have a new HP dv6705us that has the ar5007eg chipset. I can install the driver but no network is seen. I'm using 7.10 64bit -- tried heron too but nothing there either.
It's discouraging i wanted to use this with ubuntu. I'm continuing to search and read here including connecting using cli. If anyone has suggestions i'll listen.

The more i think about it i think my best option is to return the laptop to hp ( i got a 3 week trial with it ) i just don't have the time to troubleshoot this to such extent.

---

### Post by xodeus on 2008-01-20
> **phidia said:**
> I have a new HP dv6705us that has the ar5007eg chipset. I can install the driver but no network is seen. I'm using 7.10 64bit -- tried heron too but nothing there either.
It's discouraging i wanted to use this with ubuntu. I'm continuing to search and read here including connecting using cli. If anyone has suggestions i'll listen.

The more i think about it i think my best option is to return the laptop to hp ( i got a 3 week trial with it ) i just don't have the time to troubleshoot this to such extent.
DO not return it yet. There are several versions of the x64 driver in this post. try with all of them with ndiswrapper. You can also wait for madwifi and atheros to complete the driver; someone is talking about unleashing it in the next madwifi release. :D

---

### Post by robpower on 2008-01-20
Not working on Ubuntu Gutsy **64 Bit**, neither with madwifi nor ndiswrapper.
Any hope for 64bit users?:confused:

---

### Post by siukii on 2008-01-21
I almost got it to work i did [this]("http://ubuntuforums.org/showthread.php?p=3202754#post3202754") (but i use ndiswrapper 1.51 the last one), i used i dont remember what drivers but i think they are the most common ones for 64 bits winxp,  i can see the networks around but i cannot connect to any of them does anyone have something on this??

---

### Post by phidia on 2008-01-21
> **robpower said:**
> Not working on Ubuntu Gutsy **64 Bit**, neither with madwifi nor ndiswrapper.
Any hope for 64bit users?:confused:

I don't know-it is a good question though. Having really good hardware recognition for 64 bit hardware would IMO be a bragging point for linux distros since M$ doesn't-there are 64bit versions of windows out there but the laptop I have came with 32bit vista. 

People in the 64 bit forum [here]("http://ubuntuforums.org/forumdisplay.php?f=134") have been saying this for awhile now-support 64 bit since all new hardware is 64 bit. Apple has been completely 64 bit for years now.

It seems the only way to get this atheros chipset to function is to install 32 bit linux.

---

### Post by siukii on 2008-01-21
I got it to work on my ubuntu 64 bits on a acer aspire 5520 thanks to all of you
here it is what i did on a fresh installation:
1st- sudo aptitude install linux-headers-$(uname -r) build-essential (i actually didnt have internet on my ubuntu so i downloaded [this]("http://packages.ubuntu.com/gutsy/devel/linux-headers-2.6.22-14-generic") in amd 64, and i used the installation cd to get build-essential.
2nd- i downloaded ndiswrapper from the [official page]("http://ndiswrapper.sourceforge.net/joomla/")
3rd-sudo rmmod ath_pci
sudo gedit /etc/modprobe.d/blacklist-common

add the following line at the end of the file

blacklist ath_pci

Save and close

Restart computer

4th- i build ndiswrapper
make
sudo make install
4th- i downloaded this drivers that i found [here ]("http://www.atheros.cz/download/drivers/ar5xxx/xp64-5.3.0.56-whql.zip")
5th- sudo ndiswrapper net5211.inf
6th- sudo ndiswrapper -m
7th- sudo modprobe ndiswrapper
8th - i rebooted and it didnt actually work at first but  then i saw the networks around and i tried to connect to one and i got it, the wifi light doesnt turn on i dunno why, and since i got it to work i havent rebooted so i dunno if it going to work after i reboot
cya thanks to all of you
all of this i found it in this thread thanks to all of you

--
Valdivia es la ciudad mas linda del mundo!!!

---

### Post by siukii on 2008-01-21
it didnt work when i rebooted i had to do
sudo modprobe ndiswrapper
and it did it does anyone know what do i have to do to make it automatic??

---

### Post by quinto0827 on 2008-01-21
after about an hour I got it working!!! I just followed the instructions on the first post, I used the ndiswrapper 1.51 version.

---

### Post by Sergio Moura on 2008-01-22
THANKS A LOT!
It's working fine now... But the wireless led won't turn on (works on windows).
I downloaded the driver from the 1st thread link. no other drivers (not even the one in the cd that came with my notebook) worked.

I'm using an Acer Aspire 3050-1458.

Atheros (according to lspci):

```

$ sudo lspci -nn -d 168c: -v
02:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device [1468:0428]
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at b0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

```

Thanks again everyone.

- Sergio

---

### Post by Rotarychainsaw on 2008-01-24
> **phidia said:**
> I don't know-it is a good question though. Having really good hardware recognition for 64 bit hardware would IMO be a bragging point for linux distros since M$ doesn't-there are 64bit versions of windows out there but the laptop I have came with 32bit vista. 

People in the 64 bit forum [here]("http://ubuntuforums.org/forumdisplay.php?f=134") have been saying this for awhile now-support 64 bit since all new hardware is 64 bit. Apple has been completely 64 bit for years now.

It seems the only way to get this atheros chipset to function is to install 32 bit linux.

Is this true? I just installed hardy 64bit, the 64bit driver, and ndiswrapper 1.51. I can see all my networks but can't connect. It's not a huge deal if I have to install 32 bit hardy, but I'd rather try to go true 64bit...

---

### Post by phidia on 2008-01-25
> **Rotarychainsaw said:**
> Is this true? I just installed hardy 64bit, the 64bit driver, and ndiswrapper 1.51. I can see all my networks but can't connect. It's not a huge deal if I have to install 32 bit hardy, but I'd rather try to go true 64bit...

I haven't been able to get 64bit ubuntu. working with my laptop. 
It would be helpful if the 64bit users, if any, who got this working would state that they are using 64bit and which method worked. I'm definately done trying to make 64 bit work specifically with the atheros chip. I do use 64 bit for my desktop which has a physical connection (not wireless) to the network-but for a notebook I can't justify the hand installing which could cause apt to complain during future updates.

---

### Post by TheDilettante on 2008-01-29
[Removed, because I just needed to recompile my kernel.  Never mind, and sorry for the extended log]

---

### Post by afterstep13 on 2008-01-29
Hi, I use an acer 4520 which has a ar5007eg card. I'm using 64 ubuntu.
right now I'm using ndiswrappper1.44 + windows drivers.

I tried using ndis-1.5* but the problem is that I kept getting compile errors.
A 2nd problem is that,  sometimes the card is on and detects the network
but can't connect to it. That happens because the wifi adapter gets assigned a 
incorrect MAC 00:00:00:...

I posted the fix in this thread at page 12:
[http://ubuntuforums.org/showthread.php?p=4221408](http://ubuntuforums.org/showthread.php?p=4221408)

hope it works for you too :)

---

### Post by phidia on 2008-01-29
> **afterstep13 said:**
> Hi, I use an acer 4520 which has a ar5007eg card. I'm using 64 ubuntu.
right now I'm using ndiswrappper1.44 + windows drivers.

I tried using ndis-1.5* but the problem is that I kept getting compile errors.
A 2nd problem is that,  sometimes the card is on and detects the network
but can't connect to it. That happens because the wifi adapter gets assigned a 
incorrect MAC 00:00:00:...

I posted the fix in this thread at page 12:
[http://ubuntuforums.org/showthread.php?p=4221408](http://ubuntuforums.org/showthread.php?p=4221408)

hope it works for you too :)

I followed your method + used the guide for manually establishing a connection posted [here]("http://ubuntuforums.org/showthread.php?t=571188&highlight=atheros")
but I have not got wireless working.I did use the 1.44 ndiswrapper and you're right the later versions do seem to mess up the MAC address, but I'm still no closer to getting this working.

I can see my network but the connection isn't useable?

output from last commands:

loki:~$ sudo iwconfig wlan0 mode Managed
loki:~$ sudo ifconfig wlan0 up
loki:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by afterstep13 on 2008-01-30
note the lines
> Listening on LPF/wlan0/00:00:00:00:00:00
Sending on LPF/wlan0/00:00:00:00:00:00

wlan0 has a mac address of 00:00:....!

to change that do 
sudo ifconfig wlan0 hw ether XX:XX:XX:XX:XX:XX

where XX:XX:XX... is the actual mac address of the wifi card

then try to connect.

---

### Post by phidia on 2008-01-30
> **afterstep13 said:**
> note the lines


wlan0 has a mac address of 00:00:....!

to change that do 
sudo ifconfig wlan0 hw ether XX:XX:XX:XX:XX:XX

where XX:XX:XX... is the actual mac address of the wifi card

then try to connect.

I got the MAC address in win commandline using ipconfig /all
at first I thought it didn't work because I still got those lines
> No DHCPOFFERS received.
No working leases in persistent database - sleeping.

from sudo dhclient wlan0
But when I tried the connection i was suprised to find it working-I'm using it now!!
Thank you!!

Note: I'm using 64 bit Gutsy (7.10) and the atheros 5007eg network chip _IS_ working!!:)

---

### Post by phidia on 2008-01-30
This didn't work so well after all. On reboot I have to change the MAC address and bring up the interface all over again from CLI.
I don't think it's very usable in laptop terms. 
I tried editing /etc/network/interfaces and including hwaddress ether (the correct MAC address) but the system seems to remove the edit on boot??

---

### Post by afterstep13 on 2008-01-30
> I tried editing /etc/network/interfaces and including hwaddress ether (the correct MAC address) but the system seems to remove the edit on boot??


that's strange. How can the system remove the edit ?
Did you do  :
sudo <your fav editor> /etc/network/interfaces

then add
pre-up /sbin/ifconfig wlan0 hw ether <The MAC address>

that should have worked. 

Another option would be to include the command

/sbin/ifconfig wlan0 hw ether <MAC>

in a startup script. (Try searching the forums or on google)

---

### Post by phidia on 2008-01-30
> **afterstep13 said:**
> that's strange. How can the system remove the edit ?
Did you do  :
sudo <your fav editor> /etc/network/interfaces

then add
pre-up /sbin/ifconfig wlan0 hw ether <The MAC address>

that should have worked. 

Another option would be to include the command

/sbin/ifconfig wlan0 hw ether <MAC>

in a startup script. (Try searching the forums or on google)

I agree-it is strange! I hardly believe it myself, but I have added lines to the interfaces file twice now, using vim (I've been using linux for years) saved the changes, but when I reboot they're gone. The comment line I included stays but the auto wlan0 & hwaddress ether <MAC address> are removed.  I just added those lines though so maybe I'll try the string you provided that calls /sbin/ifconfig and see how that works.

It's odd that the correct MAC address is in /etc/udev/rules.d/70-persistent-net.rules.
Also I can also get the connection now by doing just those two commands.
sudo ifconfig wlan0 hw ether 00:1E:4C:4D:DC:F2
sudo ifconfig wlan0 up

OK-The pre-up string you provided seemed to work on reboot!! I'll have to see how this goes over the next few days and thanks very much for your help!

Follow -up: After several reboots & trying different WAP's-it looks like it's going to work fine now-yeeeeeaaaah! 
Thanks again for that string aterstep13 and you've been "thanked" too!

---

### Post by afterstep13 on 2008-02-01
I upgraded to Hardy Heron and almost everything is working fine :)
(some minor glitches occur but surely updates will fix 'em soon :)

I'll keep updating...

---

### Post by MJ Britt on 2008-02-01
:guitar:
All I can say is THANK YOU! 
I have been trying to get this stupid wireless card to work with Kubuntu since I got this laptop and I thought I was stuck with Vista.... Thank you, it works beautifully!


MJ

---

### Post by n0sferatu on 2008-02-01
I was in the same situation.  I have Ubuntu 7.10 64-bit on my Compaq F750US Laptop with the AR5007EG  wifi chipset and I couldn't get Madwifi working, which I found out later was because it doesn't yet support 64-bit.  So I used the Ndiswrapper instructions at the beginning of this thread and was able to finally view wireless networks.  I wasn't able to connect to them however.  I finally got it working, I had to enter the 128-bit WEP key as Hex instead of a plaintext passphrase.  As soon as I did that, it connected and started working great.  The wifi light on my laptop is still orange instead of blue, but wifi is working so no big deal.

---

### Post by davydanko on 2008-02-02
hey, i have a AR5006EG, followed instructions and it worked perfectly. after trying madwifi and other stuff for hours and hours, i would just like to THANK YOU for a great post:D

---

### Post by rbarra on 2008-02-04
Hello bmartin,

Today it is my first time with Ubuntu. I bought an Acer Aspire 4720, then installed Windows XP, and after that I installed Ubuntu. I have an Atheros AR5600X wireless card working fine in Win XP, but I can't go wireless in Ubuntu.

It says [there is no free alternatives for this Atheros card]("http://rbarra.vtrbandaancha.net/atheros.jpg")... so I can't get connected.

Should I follow the same procedures described by you in the first post? I know nothing about Linux, but want to learn, so I'd appreciate detailed help.

Thank you guys. From Chile,

Ricardo
btw: I'm using Gutsy Gibbon (7.10)

---

### Post by Makcum on 2008-02-06
[COLOR="Red"]Driver net5211 is not good at all!!![/COLOR]

1. Download the latest ndiswrapper
2. Download windows driver version xp32-6.0.3.85.zip

From here lets' say. [http://www.atheros.cz/download.php?atheros=AR5008&system=1](http://www.atheros.cz/download.php?atheros=AR5008&system=1)

It is 5416 driver

Then it will work perfectly even with the working LED. With normal MAC address and etc.
I don't know the latest version for the 64bit systems. I think it is useless to use 64bit systems if you have 4gb and less of RAM.

PS:[COLOR="Red"]TO EVERYBODY: DO NOT USE net5211 DRIVER ON AR5007EG CARDS, IT DOESN'T WORK AS IT SHOULD!!! [/COLOR]

[COLOR="Silver"]pss: I've posted a copy of this text on ndiswrapper official forum too.[/COLOR]

---

### Post by rbarra on 2008-02-06
Hi Makcum,

But after downloading, should I follow the steps described in this tutorial or is there an easier way? I'm sorry, but I'm a total newbie.

I'm getting ready to re-install Ububtu because I think I have done too many things so far. I'll start all over again. 

Feedback appreciated. 

Ricardo

---

### Post by gnicko on 2008-02-06
Works great on Acer Extensa 5420-5687 having AR5007EG. 

Just finished up about 5 minutes ago and have wireless! I love it! Haven't checked any of the "internal" stuff to see about how everything is set up...or tried to reconnect after reboot, but I'm confident that if its working once, it should work again.

I followed each step as written. Had some trouble with installing wicd/wicd-tray. The install  process "wacked" my network connection (!) but after reboot all was well. I don't remember if the instructions mentioned that or not,

All in all, it was a pretty rough process. Many interruptions. Miscellaneous errors, etc. I think I did several steps more than once....almost gave up, but in the end...seems OK

Thanks to all!!

---

### Post by dj kraemer on 2008-02-07
This procedure **_WILL NOT_** work with the latest version of Ndiswrapper 1.50-rc3.  

If you have installed this version and are not able to operate your wireless, you will need to remove ndiswrapper 1.50-rc3 and compile version 1.49-rc4.  Additionally, apt-get ndisgtk and remove the wireless driver from the list.  

After all is said and done, follow the steps on page one omitting the installation of ndiswrapper.

Cheers.

---

### Post by link141 on 2008-02-08
Theres no 64-bit version of the latest driver :/ ?  I got my wifi working perfectly after setting the mac address (using ndiswrapper 1.44).  The only thing that doesn't work it the light but I don't notice any bugs, quirks or flaws with the net5211 driver.

Makcum, why do you think it is useless to use 64-bit systems on machines with less than 4GB of ram.  I'm using it on a Turion64x2 with only 2GB of RAM and it blows 32-bit Vista out of the water (the difference is on Vista 6 hours to transcode a video and on 64-bit Kubuntu it only to 1 to transcode a similar video).

To Afterstep13: THANK YOU!!  I took me a month before I got this working.  Interesting enough, setting the mac address only works if I add the setting to /etc/networking/interfaces; it wont work with the command.  No big deal though, as my wifi is working great.

---

### Post by robpower on 2008-02-09
> **link141 said:**
> Theres no 64-bit version of the latest driver :/ ?  I got my wifi working perfectly after setting the mac address (using ndiswrapper 1.44).  The only thing that doesn't work it the light but I don't notice any bugs, quirks or flaws with the net5211 driver.

Makcum, why do you think it is useless to use 64-bit systems on machines with less than 4GB of ram.  I'm using it on a Turion64x2 with only 2GB of RAM and it blows 32-bit Vista out of the water (the difference is on Vista 6 hours to transcode a video and on 64-bit Kubuntu it only to 1 to transcode a similar video).

To Afterstep13: THANK YOU!!  I took me a month before I got this working.  Interesting enough, setting the mac address only works if I add the setting to /etc/networking/interfaces; it wont work with the command.  No big deal though, as my wifi is working great.

So to get it work on 64 bit Ubuntu version you have installed ndiswrapper and this ( [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz) ) driver, and then manually set up the MAC address?

The version you used for ndiswrapper is the one provided by ubuntu repositories?
Without the MAC setting does it see networks but couldn't connect, right?
Please if you could answer, you'll be helpful to any 64 bit Ubuntu user, me included.
Thanks

---

### Post by agm1101 on 2008-02-09
> **gnicko said:**
> Works great on Acer Extensa 5420-5687 having AR5007EG. 

Just finished up about 5 minutes ago and have wireless! I love it! Haven't checked any of the "internal" stuff to see about how everything is set up...or tried to reconnect after reboot, but I'm confident that if its working once, it should work again.

I followed each step as written. Had some trouble with installing wicd/wicd-tray. The install  process "wacked" my network connection (!) but after reboot all was well. I don't remember if the instructions mentioned that or not,

All in all, it was a pretty rough process. Many interruptions. Miscellaneous errors, etc. I think I did several steps more than once....almost gave up, but in the end...seems OK

Thanks to all!!

I have the same laptop... I followed the instructions as written without any problems. However, I can see the networks, but not associate with them. I tried unsecured as well as with secured settings. Any idea what might be the problem? 

The only thing I can think of is I used ndiswrapper 1.51. Did you use the same or 1.44? If it works with 1.44, I will try that out too. Thanks.

---

### Post by afterstep13 on 2008-02-10
do an ifconfig and see the MAC address of the wireless device.

an invalid or zero mac-address is probably the reason you can't connect to networks though you can see them.

(checkout older posts to fix this issue)

---

### Post by MissShona on 2008-02-10
> **Makcum said:**
> [COLOR="Red"]Driver net5211 is not good at all!!![/COLOR]

1. Download the latest ndiswrapper
2. Download windows driver version xp32-6.0.3.85.zip

From here lets' say. [http://www.atheros.cz/download.php?atheros=AR5008&system=1](http://www.atheros.cz/download.php?atheros=AR5008&system=1)

It is 5416 driver

Then it will work perfectly even with the working LED. With normal MAC address and etc.
I don't know the latest version for the 64bit systems. I think it is useless to use 64bit systems if you have 4gb and less of RAM.

PS:[COLOR="Red"]TO EVERYBODY: DO NOT USE net5211 DRIVER ON AR5007EG CARDS, IT DOESN'T WORK AS IT SHOULD!!! [/COLOR]

[COLOR="Silver"]pss: I've posted a copy of this text on ndiswrapper official forum too.[/COLOR]

OH YEAH BABY THIS WORKED!  I LOVE YOU!  :KS:KS:KS

Ok here's my specs:

Acer 3680-2762 with the Atheros chip AR5BXB63.  Fiesty Fawn Kubuntu installed.  I got ndiswrapper installed and working last night ~ via the instructions posted here (thank you, thank you).  I knew there was improvement because the built in network manager at least saw my wireless card.  With two reboots (and I may have toggled the switch), it would find my network.  But on the initial connection it would hang up at 57% and fail to connect.

Then I decided to read a bit more this morning.  I found your post and downloaded the 5416 driver.  Uninstalled and re-installed ndiswrapper.  Rebooted...and it worked!  Now the LED light works and everything!  

Now I just need to fix my screen resolution....

:guitar:

---

### Post by agm1101 on 2008-02-10
Doing an ifconfig gives me the following output

--------------------
wlan0     Link encap:Ethernet  HWaddr 00:1E:4C:27:9A:3D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:7328 (7.1 KB)
          Interrupt:17 Memory:f0200000-f0210000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1E:4C:27:9A:3D  
          inet addr:169.254.4.197  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:f0200000-f0210000 
--------------------------------------

How do I know if the MAC address is invalid? I tried with the net529 driver (64 bit) as well as the net5416 (32 bit) driver - same problem. I have 64 bit ubuntu installed. I cannot connect to any networks although I can see many more in Ubuntu, than in Vista.

Thanks for your help.

-agm

---

### Post by link141 on 2008-02-11
[quote=robpower]So to get it work on 64 bit Ubuntu version you have installed ndiswrapper and this ( [http://blakecmartin.googlepages.com/...-64-0.2.tar.gz](http://blakecmartin.googlepages.com/...-64-0.2.tar.gz) ) driver, and then manually set up the MAC address?[/quote]
 Yeah, that's basically all I did.

 [quote=robpower]The version you used for ndiswrapper is the one provided by ubuntu repositories?[/quote]
No, I uninstalled the version of NDiswrapper that came with Kubuntu and recompiled NDiswrapper 1.44 from source.  There's been reports that NDiswrapper 1.49 will work, but I haven't tried it.

 [quote=robpower]Without the MAC setting does it see networks but couldn't connect, right?[/quote]
Correct.  Using the sourceforge 1.44 version of NDiswrapper, and the Net5211 driver, it sets the Mac address to all 0s.  They specifically mention this happening with our chipset on this page ( [http://ndiswrapper.sourceforge.net/joomla/index.php?/content/view/19/2/](http://ndiswrapper.sourceforge.net/joomla/index.php?/content/view/19/2/) ).  [noparse]I can't tell what they meant by "set OID_802_3_PERMANENT_ADDRESS" (probably some config file) but I took Afterstep13's advice of adding that setting to /etc/network/interfaces, and it worked![/noparse]

[noparse]Here's a synopsis of what I did:

1. Follow the HOWTO, using version 1.44 of NDiswrapper.

2. Open up /etc/network/interfaces as root (with "kdesudo kate /etc/network/interfaces" replacing "kdesudo" with "gksudo" if your using gnome, and "kate" with the text editor of your choice)
A. Comment out "auto wlan0", if you don't, two wireless interfaces will get listed.
B. Add the line "pre-up /sbin/ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx" where "xx:xx:xx:xx:xx:xx" is the Mac address of your card.  Be sure to use ":" instead of "-" to separate the numbers/letters
C. Save the file

**To determine the correct mac address of your card, either use windows or look on the back of the actual chip.  In Windows go to startmenu->run...->cmd, the type "ipconfig /all".  Under where it says "Wireless Lan ..." record the Mac address listed to the right of "Physical address".  This is your mac address.

3. Restart networking with "sudo /etc/init.d/networking restart"

Thanks to afterstep13 for pointing out the Mac address issue.

Try this, and tell us if it works.

Hope this helps
link141[/noparse]

---

### Post by afterstep13 on 2008-02-12
@agm
note ava:wlan0
and the ip address 169.254.*.*

basically this means you were not able to bind with any network due to many possible reasons including :

(0) the essid is not set
     (do an iwconfig --help and everything will become clear :)
     ( iwlist wlan0 scanning will giv all networks in ur area)

(1) the network uses WEP key etc
      try to get the key, 

(2) the network accepts only registered / specific MAC addresses.
     in that case talk to the network admin.

hope this helps

---

### Post by agm1101 on 2008-02-12
> **afterstep13 said:**
> @agm
note ava:wlan0
and the ip address 169.254.*.*

basically this means you were not able to bind with any network due to many possible reasons including :

(0) the essid is not set
     (do an iwconfig --help and everything will become clear :)
     ( iwlist wlan0 scanning will giv all networks in ur area)

(1) the network uses WEP key etc
      try to get the key, 

(2) the network accepts only registered / specific MAC addresses.
     in that case talk to the network admin.

hope this helps


Well, I did all that yesterday. I knew that I was not able to associate with any network even though I could see all of them. Using wicd, I just got errors where it said something to the effect that DHCP did not receive any IP address. I tried Wifi radar as well, which did not help. I also tried the built in Network tool to see what I can change. I saw 2 wlan0 devices in there. One was for the 169.... IP address which basically was invalid, and which did not let me configure it. I then configured the other wlan0 device and set my essid, key etc. That changed the /etc/network/interfaces file. But that did not work either. All of this work was done using ndiswrapper 1.43, 1.51 and 1.52. I got valid MAC addresses using all of these.

But since none of these worked, I then followed link141's method. I tried using ndiswrapper 1.44. I got the invalid MAC address (00:00:....) and thanks to link141, changed the /etc/network/interfaces file to add the line "pre-up /sbin/ifconfig wlan0 hw ether xx:...." where "xx:..." is the MAC address of my card. I put it on the 3rd line after the auto and iface line. However, nothing happened even after resetting the network - the MAC address of the card did not change. So i manually ran that command, found using iwconfig that the MAC address had indeed been changed, and restarted the networking. 

SUCCESS! DHCP worked now with my WEP network. I was associated with the network specified in the interfaces file along with the essid and key settings I put in there. I tried to use wifi radar to change the network to an unsecured one, but that did not work. I uninstalled wifi radar and installed wicd, but that did not work either. I can see all networks using these tools, but cannot change networks with them. However, I am able to browse the internet using the network settings I put in the interfaces file.

Another thing to note was that when I tried to put the "pre-up /sbin/ifconfig wlan0 hw ether xx:......"  line in the beginning of the interfaces file, or the 2nd line, it gave me an error while restarting the network. However, if I put it in the 3rd line, it did not give an error and restarted the network, but was unable to assign a MAC address to the wireless card. Maybe some of you Linux gurus can help me understand whats going on. 

Right now, I have not restarted my computer after testing it, I may find out that it just works when I turn it on. I will let you guys know. I still need to get a good program to change wireless networks. Also, I would love to have eth0 connect directly as soon as the network cable is connected to the computer - right now, I have to use wicd to do that.

Here are some details of my configuration - Ubuntu Gutsy on Acer Extensa 5420-5687 with Atheros 5007EG wireless card. This got recognized as 5006 when I did lspci. However, after i did update-pciids, it changed the identification of the card again to something different - I don't remember it right now, and the laptop is not with me. Finally, I am using 64 bit Ubuntu, and the 64 bit 5219 driver worked for me along with ndiswrapper 1.44 with the method described by link141.

Hope that helps someone.

-agm1101

---

### Post by smithheart360 on 2008-02-13
Worked on my VGN-NR120E with 7.10
 Thanks a million i had been pulling my hair out trying to get my wifi card to work.

---

### Post by ftnewton on 2008-02-14
This worked fine for me except for the line tar xvf ndiswrapper-newest.tar.gz had to be changed to tar xvf ndiswrapper.1.57.tar.gz. All of the other artheros setups i have tried we either intermittent or would fail after an upgrade or update, I would also have to play with the system to get it to respond. So far this setup seems to work flawlessly. One thing I noticed with the acer i am using (aspire 3680 series) was that with the other setups the switch on the front of the computer would not work and the light was always on, with this setup the switch now works. For anybody out there that still does not get any wireless connections after this install with the acer, Please check and see if the light is out next to the switch and if it is turn on your wireless.  It is located next to the earphone jack on front of the computer for the aspire 3680 series.:)

---

### Post by jpeirce on 2008-02-14
Wow, thank you so much. 

This was the easiest setup of wireless I have ever experienced in linux(or even M$ for that matter). On my last laptop it took a few hours at the terminal fooling around with options to get the wireless up.

Thanks!

---

### Post by lucadigioia on 2008-02-14
thanks a lot!!!
It worked on my wife`s acer 4315-2490...
it`s a lot quicker than vista basic internet explorer as expected. :)

---

### Post by iggypop on 2008-02-15
after few days of searching and trying different installations for atheros ar5007eg i finally installed it on acer 5520g running 64-bit kubuntu.only thing that didn't work is ndiswrapper-newest but i got it to work without it...

---

### Post by littletinman on 2008-02-17
ok, the great news is i got it to work. that bad news is it only stayed connected for about 3 hours. Then it disconnected me and it won't connect anymore. Help please. i have an acer aspire 5520 and i'm running the 64 7.10. Any help is very aprec.

  Phil

---

### Post by kikke on 2008-02-22
It works for me, but avoid from modprobe ndiswrapper. Simply reboot instead.

---

### Post by ivanmladek on 2008-02-25
I got it to work on  2.6.22-14-generic #1 SMP Thu Jan 31 23:33:13 UTC 2008 x86_64 with the driver [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz) with ndiswrapper 1.50-rc3 compile from source.

---

### Post by rmayer32 on 2008-02-28
It took a bit but I got mine working..  Hopefully it stays that way.

---

### Post by mrfraser89 on 2008-03-05
Just a quick message from Australia, posting from my Asus Pro50RL laptop, finally got wireless working (on the AR5007EG card).

WICD seemed to fix the problem, Wifi-Radar wouldn't connect neither would the default gnome network manager.

Huge thanks to Bmartin, as I can now use internet at uni which is a big help :)

---

### Post by kiisu on 2008-03-05
Little strange - this worked for me before, but i had my computer in for repairs (screen damage so shouldn't have touched the wireless) when I got it back I did a fresh install.

Now running through these steps didn't get my wireless working. Shows as network unclaimed:

*-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:fd:be:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.104 latency=0 module=r8169 multicast=yes


so .... What can I do to claim it?

---

### Post by kiisu on 2008-03-06
Think I got it ....

I tried a mix of instructions from this thread and also this one:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
Hard to tell what exactly made it work but I think the version of ndiswrapper upon install was 1.45 so had to remove that and install version 1.48 as detailed in the other thread.

Anyways, happy for now!

---

### Post by gasparov on 2008-03-15
anyone got it working on hardy 64?

I see all the networks but i cannot coonect,i get  connected to XXXX at 0 then connected to none at 0

---

### Post by makkan77 on 2008-04-02
Worked for me on Hardy amd64. 
I'm using an Acer Aspire 5715Z and I have tried atleast 2-3 other drivers that didn't work atleast not with the amd64 install. 
I might add that I skipped the part of compiling the latest ndiswrapper, I just used the one in the repositories. 

Thanks alot for this guide.

---

### Post by jijitus on 2008-04-05
Hi Ubuntu fellas, my first post here. Just to say thanks to afterstep13 for pointing how to fix the problem with ndiswrapper and the net5211 driver on my Debian "lenny" installation.

My Compaq Presario F754LA has an Atheros AR5006EG (a misidentified AR5007 ???) and it was giving me a really hard time. I could connect from XP to the router at work and to my access point at home (a dissatisfying C-NET CWA-854). I could also connect to the router at work (128-bit WEP) using Mandriva 2008.0 and Debian with kwifimanager. But at home (128-bit WEP again), it was impossible to get a connection to the access point, I can't understand why this wifi module behaves different with a router and with my access point.

I was getting LOTS of Tx excessive retries: and high numbers in Invalid misc: too, that's the output of iwconfig.

When I activated syslog from the access point to my desktop PC I began to see:
```

Apr  5 01:40:30 192.168.1.253 klogd: wlan0: A wireless client is associated - 00:00:00:00:00:00
Apr  5 01:40:45 192.168.1.253 klogd: wlan0: A wireless client is deauthenticated - 00:00:00:00:00:00
Apr  5 01:40:46 192.168.1.253 klogd: wlan0: A wireless client is associated - 00:00:00:00:00:00
Apr  5 01:40:48 192.168.1.253 klogd: wlan0: A wireless client is deauthenticated - 00:00:00:00:00:00

```
Google brought me to afterstep13's post: for some reason the card was NOT using its real MAC address but one full of zeros.
Adding a line with:
```

   pre-up /sbin/ifconfig wlan0 hw ether 11:22:33:44:55:66

```
did the trick. I tried hwaddress ether 11:22:33:44:55:66 but that executes AFTER setting the essid so it was losing association right after getting it.
In fact my full "stanza" in /etc/network/interfaces is a bit paranoid:
```

iface wlan0 inet dhcp
  wireless-mode managed
  wireless-key _removedforobviousreasons_
  wireless-essid MyNetwork
  pre-up /sbin/iwpriv wlan0 reload_defaults
  pre-up /sbin/ifconfig wlan0 hw ether 11:22:33:44:55:66
  pre-up /sbin/iwconfig wlan0 key off
  pre-up /sbin/iwconfig wlan0 essid off
  post-down /sbin/iwpriv wlan0 deauthenticate
  post-down /sbin/iwconfig wlan0 essid off
  post-down /sbin/iwpriv wlan0 reload_defaults
  post-down /sbin/iwconfig wlan0 key off

```
but it works :) - and I don't have to use kwifimanager to be the connection starter, an ifup wlan0 does the job.

I don't know why but I keep on having Tx excessive retries and Invalid misc in the output from iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MyNetwork"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:11:A1:22:1F:FB
          Bit Rate=54 Mb/s
          Encryption key:1234-4567-789a-abcd-def0-0123-34   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-21 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:664  Invalid misc:1696   Missed beacon:0

```
The access point's name and MAC address where changed to protect it's identity ;)

---

### Post by MuddBuddha on 2008-04-05
Flawless.  Thanks for the great walk through!

---

### Post by makkan77 on 2008-04-05
> **makkan77 said:**
> Worked for me on Hardy amd64. 
I'm using an Acer Aspire 5715Z and I have tried atleast 2-3 other drivers that didn't work atleast not with the amd64 install. 
I might add that I skipped the part of compiling the latest ndiswrapper, I just used the one in the repositories. 

Thanks alot for this guide.

I guess I spoke to soon. As soon as I got the wifi working I did a system update and since then I can't connect to any network allthough I can see them.

---

### Post by Eraser on 2008-04-06
This worked for me on Gutsy 64 bit, I'm on an HP Pavilion dv6810us.

I made a couple of mistakes along the way, but I finally figured them out. I figured that since the HOWTO was written for Feisty, and I'm on Gutsy, that I wouldn't have to compile NDISwrapper from source and the version of NDISwrapper included with Gutsy would work, I was wrong.

Using the version of NDISwrapper included with Gutsy, I was in a situation similar to one a few others described, my laptop could detect nearby wireless networks, but no matter what I did it didn't connect. After I downloaded the latest version of NDISwrapper (1.52 as of today), compiled it and used it, I was able to connect without a problem. 

For some reason I can only use wifi-radar to connect, the Network Manager applet does not work, not a big deal, but something to be aware of. 

By the way, while trying to get things to work I installed wicd as suggested, unfortunately it did a number on my laptop. After installing it the laptop wouldn't even detect the wired network. That was a predicament since because of a conflict it uninstalled Network Manager, now I had no way to connect to the internet, luckily I was able to reinstall Network manager from the Ubuntu CD. 

Thanks bmartin for this excellent guide, if I hadn't been so hardheaded and followed your instructions exactly, I would have been up and running in a few minutes.

---

### Post by Eraser on 2008-04-06
Turns out I , like others, spoke too soon. After rebooting the wireless stopped working again.

I'm back to being able to see wireless networks, but not being able to connect.

I have tried installing different versions of ndiswrapper (so far 1.48. 1.50rc3, and 1.52), no luck. With 1.48 I was able to get it working, but after a reboot it stopped working again.

I'm back to 1.52, but still unable to connect. I'm using the 64 bit driver listed on the first message of this post. I tried others, based on the PCI ID of the card to no avail.

If anyone has any ideas I'm all ears.

> **Eraser said:**
> This worked for me on Gutsy 64 bit, I'm on an HP Pavilion dv6810us.

I made a couple of mistakes along the way, but I finally figured them out. I figured that since the HOWTO was written for Feisty, and I'm on Gutsy, that I wouldn't have to compile NDISwrapper from source and the version of NDISwrapper included with Gutsy would work, I was wrong.

Using the version of NDISwrapper included with Gutsy, I was in a situation similar to one a few others described, my laptop could detect nearby wireless networks, but no matter what I did it didn't connect. After I downloaded the latest version of NDISwrapper (1.52 as of today), compiled it and used it, I was able to connect without a problem. 

For some reason I can only use wifi-radar to connect, the Network Manager applet does not work, not a big deal, but something to be aware of. 

By the way, while trying to get things to work I installed wicd as suggested, unfortunately it did a number on my laptop. After installing it the laptop wouldn't even detect the wired network. That was a predicament since because of a conflict it uninstalled Network Manager, now I had no way to connect to the internet, luckily I was able to reinstall Network manager from the Ubuntu CD. 

Thanks bmartin for this excellent guide, if I hadn't been so hardheaded and followed your instructions exactly, I would have been up and running in a few minutes.

---

### Post by Eraser on 2008-04-06
Ok, got it to work and this time it has survived a few reboots, looks like it will "stick".

Essentially I followed afterstep13's instructions: [http://ubuntuforums.org/showthread.php?p=4221408]("http://ubuntuforums.org/showthread.php?p=4221408")

I installed ndiswrapper 1.44 from source, used the 64 bit driver listed in the first post of this thread, then modified /etc/network/interfaces so that the correct MAC address is assigned to the card, as explained by afterstep13.

One more caveat is that wireless doesn't work if I specify roaming mode in Network Settings. I need to specify the essid, the password type (128bit hex in my case) and the password.

I also had the problem of the incrementing eth# interface (first it was eth0, then eth1, then eth3, so on and so forth, with every reboot the number increased by one), afterstep13's instructions solved that as well.

Thanks both afterstep13 and bmartin for their help in setting this up.

> **Eraser said:**
> Turns out I , like others, spoke too soon. After rebooting the wireless stopped working again.

I'm back to being able to see wireless networks, but not being able to connect.

I have tried installing different versions of ndiswrapper (so far 1.48. 1.50rc3, and 1.52), no luck. With 1.48 I was able to get it working, but after a reboot it stopped working again.

I'm back to 1.52, but still unable to connect. I'm using the 64 bit driver listed on the first message of this post. I tried others, based on the PCI ID of the card to no avail.

If anyone has any ideas I'm all ears.

---

### Post by keypox on 2008-04-08
yeah and then we dont even know why... this is one of the problems that keeps me away from ubuntu.

---

### Post by brentpas on 2008-04-10
I'm getting so frustrated with this.

Like a lot of other people, mine works until I reboot.

Does anyone have a fix for this? :confused:

---

### Post by Growlor on 2008-04-12
One thing I have been seeing with my laptop (an Acer 5420-5687) is that the WPA settings don't seem to "stick" after a reboot (I use WPA with AES at home with a pretty long SSID and encryption string) So, I end-up going into manual network config and unchecking the box next to the wireless conneciton, then close and reopen manual config, paste-back in the WPA key and check the box again which seems to force a reconnect. 
Not ideal, but it gets it working.

---

### Post by hacienda_irrevocably on 2008-04-25
new ubuntu version has evicerated ability for access apt-get and synaptic. recently my wreless stops and needs ndiswrapper reinstall. how i can has other access ndiswrapper?

---

### Post by andreip on 2008-04-26
This worked for me on Hardy (8.04) on a Toshiba Sattelite U305

---

### Post by kiisu on 2008-04-26
Anyone who has problems with this working and then being lost on reboot might try uninstalling network manager. I know that caused me a lot of headaches after following this tutorial.

I use WICD now - [http://www.wicd.net/](http://www.wicd.net/) - and havent had any problems after the initial install. Actually the install itself deleted both network-manager and wifi-radar from my system, saving me the time.

My only advice would be to make sure you have a backup plan - say, another working internet connection - just in case something goes wrong, because once you remove network-manager you may not be able to connect to the internet.

---

### Post by dwrs on 2008-04-28
thank youuuu at alll i m very appriciated about that i solved the thread with your helps.thank you very much ;) 
And finally all the users that have same problem 
im writing to you with my 64 bit AMD turion X2 Acer AS5520G-604G25MI laptop installed kubuntu hardy 64 bit version
i m using linux for 2 days :D and like to learn every steps ;) it's an advanture i think 

Best Regards from Turkiye

---

### Post by Lord Juan on 2008-04-28
> **gasparov said:**
> anyone got it working on hardy 64?

I see all the networks but i cannot coonect,i get  connected to XXXX at 0 then connected to none at 0

I have the same problem in hardy, which i had in Gutsy until i installed the version 1.44 of ndiswrapper, my problem now it's, i can't compile ndiswrapper 1.44 on hardy, am i the only one with this problem (so i keep trying to find what's wrong) or someone else got this wireless problem with hardy?

I swear i won't ever buy anything labeled Atheros again, ever >.<

Edit: And btw i did test installing a different version of ndiswrapper (1.52), installed fine, but i got back to the "Connected to None" problem. I guess i will try with other ndiswrapper versions to see if any of them make it work.

---

### Post by nray on 2008-04-28
> **prescottp said:**
> However, now that the wireless is working, I still can't get it to finish the connection.  It can see all the wireless networks in the area, but it won't get an IP address.  I thought it was something to do with WPA and a TKIP key, but when I turned the security off it still wouldn't get an IP address...  It wouldn't work with a manual IP either, even with all the other settings plugged in.  Does anyone have any ideas as to why that's going on?

Describes my situation almost exactly.

I was using ndiswrapper with my AR5007EG (Abit Airpace) in 32-bit Ubuntu 7.10 without any trouble whatsoever.

Then I switched first to 64-bit Ubuntu 7.10, and what you describe is what I experienced, even with ndiswrapper 1.52 (and even experienced some *wired* networking problems while I was changing the *wireless* settings!)  Then I recently installed 64-bit Ubuntu 8.04, and while my wired network connection hasn't gone down, ndiswrapper in 64-bit (the 1.50 package version shipped with 8.04) still doesn't work, same symptoms: sees wireless networks, no errors, but will not connect to my non-encrypted wireless network (RX bytes and TX bytes stay at 0 no matter what, will not pick up a dhcp address, no errors anywhere that I can find).  Can't express my frustration enough.

---

### Post by nray on 2008-04-29
> **nray said:**
> Describes my situation almost exactly.

And here's the solution -

In at least 64-bit Ubuntu 8.04, with the ndiswrapper package (version 1.50 at the time of this writing), using the XP x64 5.3.0.56 driver, it is absolutely necessary to put this line into /etc/network/interfaces under iface wlan0 with your AR5007EG's hardware ethernet address where 00:00:00:00:00:00 is:

pre-up /sbin/ifconfig wlan0 hw ether 00:00:00:00:00:00

With that line in place, things will work they way they should in 64-bit.  I didn't need that line in 32-bit Ubuntu 7.10 with ndiswrapper, but I needed it in 64-bit.

---

### Post by phidia on 2008-04-29
I had wifi working very well in 64 bit Gutsy-I went back over my steps and this thread for Heron, but no way can I get a working wireless connection in my 64 bit Heron install(with an HP laptop & the atheros ar5007eg card).
I tried putting the line, from the previous poster, in my /etc/network/interfaces file too but nothing.
The connection is seen by network manager and wifi radar too but I can not use it.
I'll mess around with it a little more but I may be re-installing Gutsy.

---

### Post by justo_yo on 2008-04-30
Hello, I have a similar issue with an ACER 5520 5290... this atheros driver worked fine in Kubuntu 7.10 but once I moved to Kubuntu 8.04 it doesn't. I applied the solution above about adding a line and at least I started to see the networks around me but I cannot connect to them. Activating Wireless network (Network Manager) get stuck at 57% or at 28%. Later it ask again for WEP password or declare connection failure. Any help will be very appreciated.

---

### Post by phidia on 2008-05-01
This is really discouraging I followed the excellant guide on the ar5007eg card [here]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html") and also readthrough and tried several troubleshooting methods from [here]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html") but although the network is seen I cannot connect. I'm using 64 bit 8.10 The driver is loaded see this snippet of dmesg: > [   33.419596] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   33.421285] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[   33.422435] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   33.422450] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   33.422512] ndiswrapper (ZwClose:2227): closing handle 0x0 not implemented
[   33.422651] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   33.835792] ndiswrapper: using IRQ 19
[   34.040712] wlan0: ethernet device 00:1e:4c:4d:dc:f2 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   34.045010] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


At this point I'm pretty sure I will return to Gutsy-I can't spend weeks looking for the solution :(
Really excellant guides though and I reccomend them.

---

### Post by nray on 2008-05-01
> **phidia said:**
> I had wifi working very well in 64 bit Gutsy-I went back over my steps and this thread for Heron, but no way can I get a working wireless connection in my 64 bit Heron install(with an HP laptop & the atheros ar5007eg card).
I tried putting the line, from the previous poster, in my /etc/network/interfaces file too but nothing.
The connection is seen by network manager and wifi radar too but I can not use it.
I'll mess around with it a little more but I may be re-installing Gutsy.

That's odd that you had ndiswrapper working with the AR5007EG in Ubuntu 7.10, because I never got it to work there (at least without adding the pre-up line, which I've only tried in Ubuntu 8.04, having given up on 7.10).

Besides the pre-up line in my /etc/network/interfaces I also have several other lines specifying the wireless network I want wlan0 to connect to and it's channel etc., so I'm not sure if those make a difference.

Also, my AR5007EG is not in a notebook, this is a desktop system and the wireless card with that Atheros chipset is an Abit Airpace, which I also don't know if it makes a difference.

Anyone else had success adding the pre-up line?  It definitely fixed things for me.

---

### Post by phidia on 2008-05-01
> **nray said:**
> That's odd that you had ndiswrapper working with the AR5007EG in Ubuntu 7.10, because I never got it to work there (at least without adding the pre-up line, which I've only tried in Ubuntu 8.04, having given up on 7.10).

Besides the pre-up line in my /etc/network/interfaces I also have several other lines specifying the wireless network I want wlan0 to connect to and it's channel etc., so I'm not sure if those make a difference.

Also, my AR5007EG is not in a notebook, this is a desktop system and the wireless card with that Atheros chipset is an Abit Airpace, which I also don't know if it makes a difference.

Anyone else had success adding the pre-up line?  It definitely fixed things for me.

I Saw your post in another thread on this card and yes it works, for me, in Gutsy but not Heron. I am using the pre-up line that requires the wlan0 actual hardware address ( I don't think that is clear enough ).

I notice that with either of the two releases the light that shows the card is on does not work. The light works, of course, in windows.

I don't want to be cranky but this specific atheros card is too difficult to get working (in 64 bit anyway) I have gutsy installed to an external drive and while I know I could copy the install over to the internal I tried instead to just do a fresh install-I can't get that install to use the connection :confused: I did so many little things to get it to work before and obviously didn't take profuse notes and can't (?) duplicate the previous steps ](*,)

I do think the pre-up line is important and I remember I had to try that several ways on the install that works. I'll provide my interfaces file:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The wlan0 interface added 1-30-08
pre-up /sbin/ifconfig wlan0 hw ether 00:1e:4c:4d:dc:f2







iface eth63 inet dhcp

auto eth63


In hopes that illustrates what to do. You need to use ifconfig in terminal to determine the hardware address for your card and insert that in /etc/network/interfaces.
Why I can't get the internal drive install working is maddening.

---

### Post by Rotarychainsaw on 2008-05-01
> **nray said:**
> And here's the solution -

In at least 64-bit Ubuntu 8.04, with the ndiswrapper package (version 1.50 at the time of this writing), using the XP x64 5.3.0.56 driver, it is absolutely necessary to put this line into /etc/network/interfaces under iface wlan0 with your AR5007EG's hardware ethernet address where 00:00:00:00:00:00 is:

pre-up /sbin/ifconfig wlan0 hw ether 00:00:00:00:00:00

With that line in place, things will work they way they should in 64-bit.  I didn't need that line in 32-bit Ubuntu 7.10 with ndiswrapper, but I needed it in 64-bit.

HOLY CRAP I LOVE YOU! This seems to have fixed my problem where I would have to rmmod and modprobe ndiswrapper every time I rebooted. This is such a PITA.

Edit - Realtime kernel seems to make ndiswrapper constantly reset the card, so beware.

---

### Post by vnieto on 2008-05-04
> **Rotarychainsaw said:**
> HOLY CRAP I LOVE YOU! This seems to have fixed my problem where I would have to rmmod and modprobe ndiswrapper every time I rebooted. This is such a PITA.

Edit - Realtime kernel seems to make ndiswrapper constantly reset the card, so beware.

I Use the same procedure but in some times is necesary rmmod and modprobe ndiswrapper only work in few times.

Some news?
I use amd64 over Ubuntu hardy

---

### Post by hacienda_irrevocably on 2008-05-07
everyone knows? patched madwifi does now work for 5007eg the wiif card. no more problems!
link to patch in link
[patch link]("http://forums.gentoo.org/viewtopic-t-596777-highlight-atheros+5007eg.html")

---

### Post by vnieto on 2008-05-07
> **hacienda_irrevocably said:**
> everyone knows? patched madwifi does now work for 5007eg the wiif card. no more problems!
link to patch in link
[patch link]("http://forums.gentoo.org/viewtopic-t-596777-highlight-atheros+5007eg.html")

Work over amd64??

---

### Post by phidia on 2008-05-08
> **vnieto said:**
> Work over amd64??

As far as I know and from what I've read about madwifi drivers that patch is only for 32bit-so if you're running 64bit you need to use the ndiswrapper work-around and add a line to your /ect/network/interfaces file too.

---

### Post by zipposcott on 2008-05-09
Thank you so much for this how to I have been working at this for hours and finally found something that actually helped me i am now on my wireless and completely away from vista for good.

---

### Post by Bryantos on 2008-05-09
YES! The driver worked for my laptop (Sony VGN-NR110E). It detected that I have wireless now, but I havn't really tried it out. I will be trying it out soon. It keeps asking me for the password for my network right now, but I'm not sure if I'm putting in the right password.

I will update soon.

---

### Post by thebrokenbox on 2008-05-10
This doesn't work for me :( I've tried so many different ways to do it but it just won't work.

---

### Post by Tigin on 2008-05-11
I tried the how-to at the 1st post , i have to say that was the best working one for me , at least i can connect to my wireless at the moment , i still canNOT see any mozilla pages loading though ( /cry ).

I stick to how-to , mostly copy - pasted except ndiswrapper ( i had it already with distro ).

My system is ; Ubuntu-studio , running on Acer Aspire 5520 laptop , AMD64 CPU , atheros ARBXB63 wireless card .

I am using Wicd and can connect to my wireless network , but no chance to view any page thorough mozilla .

Any idea about solution ? help will be greatly appreciated .

---

### Post by Promaster91 on 2008-05-13
It works! Thanks.

---

### Post by josedb on 2008-05-13
Swith led is not changing when switching to on/off. Any idea?

---

### Post by gdelta9 on 2008-05-20
first of all thnx  a lot for this great how to.Great job!!!!!
After following your how to i got so close to make it work,but still have connection issues.I can see wireless networks but cannot connect to any of them(well manged to connect only once and never again).I assume that what is wrong is that my atheros card is indicated as AR242x and not as ar5007eg.Here is what i get:


Description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:66:24:32
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.5


Any ideas how to fix this?


SOLVED:Just added that line and everything works just perfect now!!!!!

---

### Post by Adridar on 2008-05-28
Hey, I followed the How-To, and it got me to where I could see the wireless networks, but I couldn't connect to them...so I went and tried to install WICD...but during the installation process, it removes the Network Manager...leaving my laptop dead in the water, without wired networking, on top of no wireless....is there any way to reinstall the Network Manager without access to the internet on my laptop? and if so, once I do that, do you know what is causing my Atheros card to not connect to the networks?
Thanks!

Adridar

---

### Post by inportb on 2008-05-28
btw, the AR5007EG wireless device has the AR242x chipset.

---

### Post by xaitax on 2008-06-04
Hi,

now AR5007 works with a HAL patch from SAM and the latest SVN trunk.

Like [here]("http://madwifi.org/ticket/1679#comment:212") I wrote:

> Hi, I just created a file which simplifies the installation of the driver. So you don't need any subversion packet (huh, anyways, why don't u have?). It ist the latest madwifi svn version (from now on) and the patch from Sam is already included (GREAT WORK SAM!). Just enter "./install.sh" and watch for the output. If something goes wrong, don't hesitate to contact me. [http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2](http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2)

So, have phun with it!

Regards,
xaitax

---

### Post by Tigin on 2008-06-08
OMG! , OMG !!.... after almost one moth you gave me the solution :D , heh i can see the light now man , ty ty :)



(My system  :  AMD64 AthlonX2 Acer Aspire 5520 ubuntu 8.04 64 bit )

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by dave87 on 2008-06-10
This just worked perfectly for me with Ubuntu 8.04 on a Toshiba Satellite Pro A200 where lspci says I have an Atheros AR242x but is actually an AR5007EG. Thankyou!

---

### Post by Tigin on 2008-07-07
i ve set wireless on same laptop more then 3 times every time successfully , here is my simple how-to :

"" sudo apt-get install build-essential ""

get this file :[http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2](http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2)

run ""install sh"" ( double click on it and hit "**run in terminal**" again or drag it to terminal then hit "enter" )

then uncheck "atheros Hardware Access Layer (HAL)" and "support for atheros 802.11 wireless lan cards" in "SYSTEM>ADMINISTRATION>HARDWARE DRIVERS" menu , then restart.

cheers



(My system : AMD64 AthlonX2 Acer Aspire 5520 ubuntu 8.04 64 bit )

---

### Post by ruggrat on 2008-07-09
Thanks for at least getting me off the ground! I was getting the same network UNCLAIMED and no logical name as a few other people around here, but now it looks like I actually got the card to play with the drivers by your method.  

Still can't connect, but now I can see them. One step closer to surfing in bed!

---

### Post by slobapet on 2008-07-12
Uh, I finally made it on MSI VR601. On Kubuntu x64... it works. I can't thank you enough... :KS

---

### Post by Jim2029 on 2008-07-20
I need some help.... I followed everything and still no wifi. I went to the network and only see my nic and my modem device. no wifi. I'm using a HP DV6810us.

---

### Post by Tigin on 2008-07-20
Jim is your card atheros AR5007eg ? and your system please 32 bit or 64 bit?

 these infos will make easier to help you for others

---

### Post by ctijacob on 2008-07-21
OK, having some troubles here.. fresh install..Ubuntu 8.04 64-bit, Acer Aspire 5050 w/ Atheros 5007EG Chipset. I did the walkthrough and it worked, rebooted, still worked.. rebooted again and it sees the network but cannot connect, rebooted multiple times, same issue. I'm using wicd as the network connection manager.. I tried to ifconfig wlan0 up.. scan, it still sees them, but doesn't connect.. help.. please..??

---

### Post by Tigin on 2008-07-21
Try this hope it helps . It worked for me ,it may work for you as well , you will have madwifi drivers .



"" sudo apt-get install build-essential ""



get this file :  



[http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2](http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2)


run ""install sh"" ( double click on it and hit "run in terminal" again or drag it to terminal then hit "enter" )


then uncheck "atheros Hardware Access Layer (HAL)" and "support for atheros 802.11 wireless lan cards" in "SYSTEM>ADMINISTRATION>HARDWARE DRIVERS" menu , then restart.


try with the default network manager
cheers

---

