---
title: "Driver for Belkin F5D8001 PCI wifi adapter"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Chonnawonga on 2008-09-18
Hi!

I just picked up a Belkin F5D8001 PCI wifi adapter, with draft-802.11n. I based my purchase on the [hardware compatibility list]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCI"), which claims the device will work (including WPA2 personal) using the NetMW14x.inf driver.

I managed to grab the driver by installing the drivers for a Netgear WN511T (available [here]("http://kbserver.netgear.com/products/WN511T.asp")). The GUI for ndiswrapper is telling me this, though: "Hardware present: No". Why am I getting a different result than whoever wrote that in the compatibility list?

I can get the wifi card working with the Belkin-supplied net5416.inf driver, but that won't let me access a WPA2 secured network, although I can connect through WPA1.

Has anyone had better luck with other drivers? Anyone have a suggestion?

Thanks!

---

### Post by ubu_dynamite on 2009-01-05
My Belkin N1 Wireless Desktop Card F5D8001 (?ver. 2000df) is working with
ndiswrapper 1.53
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)
and the driver from belkin site
[http://www.belkin.com/support/article/?lid=en&pid=F5D8001&aid=5928&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D8001&aid=5928&scid=0)
F5D8001 version 2.02.01
```
sudo update-pciids
lspci -nn
```
00:07.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8361 [TopDog] 802.11n Wireless [11ab:2a02] (rev 03)

---

### Post by Chonnawonga on 2009-01-05
Thanks for the update, ubu_dynamite! I'll give that a try when I get back to my desktop tomorrow.

---

### Post by ubu_dynamite on 2009-01-06
I made this from these posts below and changed it to instal my Belkin N1 Wireless Desktop Card F5D8001 (ver. 2000df)
I,m using ubuntu hardy 32bit with f5d8001v2_ww_2.02.01_w2 driver

Attached drivers are from a 32 bit windows xp install.

```
sudo update-pciids
lspci -nn | grep Wireless

```
00:07.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8361 [TopDog] 802.11n Wireless [11ab:2a02] (rev 03)

[http://ubuntuforums.org/showpost.php?p=1741197&postcount=1](http://ubuntuforums.org/showpost.php?p=1741197&postcount=1)
[http://ubuntuforums.org/showpost.php?p=3532058&postcount=1](http://ubuntuforums.org/showpost.php?p=3532058&postcount=1)
[http://ubuntuforums.org/showpost.php?p=5248587&postcount=6](http://ubuntuforums.org/showpost.php?p=5248587&postcount=6)

STEP 1: CLEAN YOUR SYSTEM

IMPORTANT NOTE ABOUT CLEANING YOUR SYSTEM:

One of the most common reasons why many people can't get their wireless working is because their system is in a state of chaos. If you have made ANY previous attempts to get your wireless working -- either using ndiswrapper, net5416, or the netmw14x drivers -- this how-to will most likely not work UNTIL you reverse your previous changes. In many cases, it is much easier to simply reinstall ubuntu and come straight to this how-to. Alternatively, you can manually clean your system of the previous attempts, as outlined in various posts throughout this thread. But BE WARNED: If you have done ANY previous work on your wireless, there is almost no chance that this how-to will work unless you clean your system.

If you have a fresh install of Ubuntu, you need to remove any and all versions of Ndiswrapper that come installed by default on your system:

```
sudo rmmod ndiswrapper
sudo ndiswrapper -e net5416
sudo ndiswrapper -e netmw14x
sudo ndiswrapper -r net5416
sudo ndiswrapper -r netmw14x
sudo aptitude purge ndiswrapper-common ndiswrapper-utils-1.9
```

Don't worry if you get errors about not being able to find or remove these -- we're just making sure they're not present before we get started.

STEP 2: GET NEEDED PACKAGES

We'll need to install compiling tools (don't panic when you read that, just bear with me), the latest kernel headers, and then the source code for the latest ndiswrapper (seriously, don't panic. This will be very simple), and the wireless drivers from Belkin.

```
sudo aptitude update
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`
```

NOTE: The characters around `uname -r` are BACK TICS, NOT apostrophes. A back tic is usually located at the top left of your keyboard, to the left of the 1 key. The command WILL NOT WORK if you use apostrophes. Just copy/paste the commands from this how-to in to your terminal to avoid making typos.

At this point, you need to go to the ndiswrapper sourceforge site and get the latest version of the Ndiswrapper program.

```
wget http://dfn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.54.tar.gz
```

If that wget doesn't work, just go here: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

Uncompress the ndiswrapper source (in my example, the file name is ndiswrapper-1.54.tar.gz):

```
tar -xzvf ndiswrapper-1.54.tar.gz
```

STEP 3: COMPILE PROGRAM

Now we'll complile the Ndiswrapper program. In a terminal, go to the directory where you extracted ndiswrapper and execute the following:

```
cd YOUR-NDISWRAPPER-DIRECTORY
sudo make uninstall
```

IMPORTANT: Do the above command multiple times. You can stop when you get the message that says something about no files or directories found. This usually means running the command 2 or 3 times, but not more than about a dozen.

```
make
sudo make install
```

STEP 4: INSTALL DRIVERS

If that worked, then you now have Ndiswrapper installed. Now we need to install the drivers.

Now change directories to the DRIVER directory and install the driver.

```
cd YOUR-DRIVER-DIRECTORY
```
if you have a version 1xxx card

F5D8001 version 1xxx Drivers
```
sudo ndiswrapper -i net5416.inf
```

or if you have a version 2xxx card

F5D8001 version 2xxx Drivers
```
sudo ndiswrapper -i NetMW14x.inf
```

> may not be necessary!!
As stated in the other thread, it's necessary to force the wireless to associate with the driver: 
[http://ubuntuforums.org/showpost.php?p=3532058&postcount=1](http://ubuntuforums.org/showpost.php?p=3532058&postcount=1)
(lspci -nn will show device ids)
```
lspci -nn
sudo ndiswrapper -a id netmw14x (change id and driver with your cards id and driver version)

```

```

ndiswrapper -l
```

you should see a message that says driver present, hardware detected

```
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules
```

NOTE: If the above echo command gives you a permission denied error, try this code instead:

```
sudo -s
echo ndiswrapper >> /etc/modules
exit
```

May need to reboot here.

STEP 5: TEST WIRELESS

Your light on your card should be illuminated, and you're all set! Try running this to see if your wireless card is functioning properly:

```
iwconfig
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"******"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:17:3F:3C:14:86   
          Bit Rate=300 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

```
iwlist scanning
```

Even if it doesn't detect any wireless networks in range, it will still tell you if linux is recognizing your wireless card properly.
---------------------------------------------------------------------
If this works for you, make sure you store the 'Driver' folder with the .inf and .sys files somewhere safe, in case you decide to reinstall Ubuntu later on and need to install the drivers again.

---

### Post by caynus on 2009-01-15
Hi ubu_dynamite,

I'm having trouble updating the build and linux headers. I need to do this to install the latest ndiswrapper, right? But the computer I'm on does not have an internet connection and so I can't update in this way. Can I download the build and headers on another computer and transfer them? If I can, how do I install them? I guess it's not as easy as:

cd DIRECTORY-WITH-UPDATES
sudo aptitude update
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`

Thanks for any help!

---

### Post by ubu_dynamite on 2009-01-18
You could try this

[http://ubuntuforums.org/showthread.php?t=381532](http://ubuntuforums.org/showthread.php?t=381532)

Insert the install CD into a drive and at the prompt, type

Applications -> Accessories -> Terminal

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by caynus on 2009-02-01
That worked great! thanks ubu_dynamite, everything went find but I needed v1.54 because v1.53 wouldn't compile itself.

Thanks again, just need to get my fx5200 working now :P

---

### Post by loukoum82 on 2009-02-19
Sorry, but I followed all of this, and my F5D8001 is detected by the command ```
ndiswrapper -l
```
like this : ```
netmw14x : driver installed
	device (11AB:2A02) present
```
But when I do ```
iwconfig
``` I don't have My Wireless Card.

Some Help Please...

Maybe it's the wrong driver ? isn't it possible? How do I Know which is my card Version (1 or 2)?

---

### Post by ubu_dynamite on 2009-02-19
version is on your card and on the box it came in it,s a small sticker.

mine is ver. 2000df
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103917&stc=1&d=1235056631[/IMG]
did you do the rest of the howto after ndiswrapper -l and did you reboot?

---

### Post by Kaxsp on 2009-02-24
> **loukoum82 said:**
> Sorry, but I followed all of this, and my F5D8001 is detected by the command ```
ndiswrapper -l
```
like this : ```
netmw14x : driver installed
	device (11AB:2A02) present
```
But when I do ```
iwconfig
``` I don't have My Wireless Card.

Some Help Please...

Maybe it's the wrong driver ? isn't it possible? How do I Know which is my card Version (1 or 2)?

I have the same problem, and i'm sure my driver is 2xxx...

Any help?

---

### Post by ubu_dynamite on 2009-02-25
Did you try some other driver or howto before this?
Are you using ubuntu hardy?


I just removed ndiswrapper and my wireless driver and reinstalt
using ubuntu hardy 8.04
driver f5d8001v2_ww_2.02.01_w2

```
sudo update-pciids
lspci -nn | grep Wireless

```
00:07.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8361 [TopDog] 802.11n Wireless [11ab:2a02] (rev 03)

```
sudo rmmod ndiswrapper
sudo ndiswrapper -e netmw14x
sudo ndiswrapper -r netmw14x
sudo aptitude purge ndiswrapper-common ndiswrapper-utils-1.9
sudo aptitude update
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`
mkdir wireless
cd wireless
wget http://dfn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.54.tar.gz
tar -xzvf ndiswrapper-1.54.tar.gz
cd ndiswrapper-1.54
sudo make uninstall
sudo make uninstall
sudo make uninstall
```

```
sudo updatedb
locate ndiswrapper
```

There where still some ndiswrapper files left so i removed them.

```
sudo rm -r /etc/ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /lib/modules/2.6.24-22-generic/misc/ndiswrapper.ko
sudo rm /lib/modules/2.6.24-23-generic/misc/ndiswrapper.ko
sudo rm -r /lib/modules/2.6.24-22-generic/ubuntu/misc/ndiswrapper
sudo rm -r /lib/modules/2.6.24-23-generic/ubuntu/misc/ndiswrapper
sudo rm /usr/share/man/man8/ndiswrapper.8
sudo updatedb
locate ndiswrapper
```

Now al ndiswrapper files i had where in
/home/user/wireless

!!sudo make distclean!! gave me errors and did nothing i will remove it from the howto
!!sudo make!! I will remove sudo dont need it to run make

```
make
sudo make install
```

download the wireless driver

```
cd YOUR-DRIVER-DIRECTORY
```

I have a version 2xxx card so i installt with

```
sudo ndiswrapper -i NetMW14x.inf
```

I skipt the change id and driver part
and did ndiswrapper -l without sudo will remove it from the howto
 
```
ndiswrapper -l
```

```
netmw14x : driver installed
	device (11AB:2A02) present

```
I already have ndiswrapper in /etc/modules so i did a reboot
and my wireless is working

```
iwconfig
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"******"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:17:3F:3C:14:86   
          Bit Rate=300 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by loukoum82 on 2009-02-27
yeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeees !!!
it Works, i was so angry that i didn't reboot on linux since a week, but i just did it and my wireless works !!
Oh yeah! I can't put "winFuckedUp" in the trash!:guitar:
Thanks for this post.

---

### Post by ubu_dynamite on 2009-03-01
> **loukoum82 said:**
> Oh yeah! I can't put "winFuckedUp" in the trash!:guitar:

[https://help.ubuntu.com/community/HowToRemoveWindows]("https://help.ubuntu.com/community/HowToRemoveWindows")

---

### Post by loukoum82 on 2009-03-01
Sorry, it was a mistake, I wrote "can't" instead of "can". I know how to trash windows, "format c:", it is on another Hard Disk...
But thanks anyway.\\:D/

---

### Post by loukoum82 on 2009-04-22
it works.
BUT....
Sometimes I lost my connection, I don't no why...
When will we have a good driver for belkin!!?? Not a ndiswrapper' one.
I wait for it!

---

### Post by onecosmos on 2009-05-12
Hi Ubu_dynamite
Read most of your posts here for the Belkin card, excellent input, thanx,
however i have a question, did you manage to get the device working in 64 bit architecture or a 32 one?
Coz i used your method and the drivers you have uploaded, when i run 

dmesg | grep -e ndis -e wlan

the system complains about "bad magic", meaning that i try to load 32 bit drivers in to a 64 bit system (had a go with all 4 drivers!).
this post has a very good review on inspecting the state of the card..
[http://ubuntuforums.org/showthread.php?t=885847&highlight=network+unclaimed](http://ubuntuforums.org/showthread.php?t=885847&highlight=network+unclaimed)

please let me know if you run a 64 bit machine, so i dont waste my time, i am thinking of formating and installing the 32 bit version of ubuntu, unless you or anybody can point to a solution for 64 bit machines..

---

### Post by loukoum82 on 2009-05-12
Simplify your life, put the 32 bit version, that's what I did, and It was easier to resolve the problem.

But with Ubuntu 9.04, it doesn't work anymore...

---

### Post by onecosmos on 2009-05-12
Hi loukoum82
Thanx for your quick reply, but if possible i would like to stay on 64 coz need lots of memory and extended addressing for heavy simulations that i do often.
By the way, what do you mean with ubuntu 9.04 it doesnt work anymore? the wireless card? even in 32 bit?

---

### Post by loukoum82 on 2009-05-12
Since I have upgrade 8.10 to 9.04, my Belkin doesn't work anymore, the network icon stay on "look for network" status, and when i click on it, Ubuntu freeze, i have to restart.
Even after uninstall and re-install driver.

So, now, I just wait for a true driver for belkin, and not a ndiswrapper 'one.

Good luck.

---

### Post by Chonnawonga on 2009-05-12
Mine's working in 9.04. I did a clean install and I'm on a 32-bit system. I didn't have to use ndiswrapper: it worked out of the box.

I would recommend trying a "live" session of 9.04 and seeing what happens... although those don't always reflect an installed session 100% accurately.

---

### Post by onecosmos on 2009-05-13
Reading the last two post i was convinced to give a try to 9.04 in 32 bit, i managed to load the drivers for the card either way ndiswrapper and by ndisgtk, card seems to be functioning ok but when i input the WEP key to connect to the detected home network, it tries endlessly to connect, and if i click on the network icon the whole system crashes, i guess similar problem with loukoum82

My question is to Chonnawonga, do you use encryption ? If yes which kind, WEP , WPA etc.

---

### Post by loukoum82 on 2009-05-13
> **onecosmos said:**
>  i guess similar problem with loukoum82

Oh yeah! Exactly the same !

---

### Post by Chonnawonga on 2009-05-13
This router is on WEP, for reasons unrelated to this card. I'm not having any trouble with that. I haven't tried it on WPA, so I can't tell you if that works or not.

---

### Post by ubu_dynamite on 2009-05-14
Sorry for the late respons.

I,m using a 32 bit system.
Also the drivers i attached in [my post]("http://ubuntuforums.org/showpost.php?p=6503726&postcount=4") are from a 32 bit windows xp install.

> **onecosmos said:**
> Hi Ubu_dynamite
Read most of your posts here for the Belkin card, excellent input, thanx,
however i have a question, did you manage to get the device working in 64 bit architecture or a 32 one?
Coz i used your method and the drivers you have uploaded, when i run 

dmesg | grep -e ndis -e wlan

the system complains about "bad magic", meaning that i try to load 32 bit drivers in to a 64 bit system (had a go with all 4 drivers!).
this post has a very good review on inspecting the state of the card..
[http://ubuntuforums.org/showthread.php?t=885847&highlight=network+unclaimed](http://ubuntuforums.org/showthread.php?t=885847&highlight=network+unclaimed)

please let me know if you run a 64 bit machine, so i dont waste my time, i am thinking of formating and installing the 32 bit version of ubuntu, unless you or anybody can point to a solution for 64 bit machines..

Edit: 2 days ago wasn't that late ;)didn't get any mail.

---

### Post by onecosmos on 2009-05-14
Hi

Thanx people for the info, loukoum82 this might be especially interesting to you as it seems we had the same problem, as you can see i used the word had, luckily to solve this at least temporarily you can try the following

1) remove uninstall network manager 
2) visit the following post, and apply the case suited for you, in my case i typed the code for manually connecting to a WEP encrypted communication.
 
[http://ubuntuforums.org/showthread.php?t=571188&highlight=To%3A+Manual+Network+Configuration+Manager](http://ubuntuforums.org/showthread.php?t=571188&highlight=To%3A+Manual+Network+Configuration+Manager)

3) assuming that beforehand you had loaded successfully the drivers to your card by ndiswrapper then you should find your self connected

i will try wicd to see if this works with WEP encryption and the specified hardware and let you know, it seems that the already installed network manager in 9.04 has issues under WEP encryption and the given drivers and hardware.

---

### Post by loukoum82 on 2009-05-15
Thanks onecosmos.
I'll try this as soon I 'll be at home.
If it works, you'll know !):P

---

### Post by loukoum82 on 2009-05-16
It doesn't work...
when I do :
```

sudo iwconfig wlan1 essid "JAZZTEL_1232"

```

I have this :
```

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan1 ; Invalid argument.

```


It will never work ...!!!! ](*,)](*,)

---

### Post by PyrO_PrOfessOr on 2009-07-19
This was awesome - Thanks a lot ubu_dynamite!!

A friend of mine even wrote the whole procedure to a script for me for easy installation on Linux Live versions!

Thanks again!

---

### Post by elbeardo on 2009-10-24
Hi. Followed your steps and still haven't got anywhere - probably doing something wrong. I have a v2 card and when i type lspci -nn i get this for my wireless card....

01:06.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2202] (rev 03)

Tried with both version 2 drivers and the one of the v1 drivers. Even tried others drivers from here:

[http://ubuntuforums.org/archive/index.php/t-833363.html](http://ubuntuforums.org/archive/index.php/t-833363.html)

So far had no luck what so ever. I'm rebooting each time and cleaning out ndiswrapper, uninstalling and reinstalling. Any help would be GREATLY appreciated.

---

### Post by Mistoffeles on 2009-10-29
> **Chonnawonga said:**
> I must be updating Ubuntu. How else could I be expected to take seriously the phrase, "Unpacking replacement gnome"?

Sorry, this had to be done:

[IMG]http://home.cogeco.ca/~illuminati/unpacking.jpg[/IMG]

:D

P.S.: Thanks for the Belkin F5D8001 info., I almost sent it back to NewEgg.

---

### Post by Chonnawonga on 2009-10-29
Exactly.

---

### Post by TheBig3 on 2010-01-29
Has anybody tried this with 9.10 yet? I think I'm having problems with ```
sudo make uninstall
``` I keep getting error codes when I try. I've tried both 1.55 and 1.54 ndiswrappers.

I will try to post the whole process once updates are done.

---

### Post by TheBig3 on 2010-01-29
here is my terminal process

```
oem@Cherokee-Ubuntu:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
oem@Cherokee-Ubuntu:~$ sudo ndiswrapper -e netmw14x
Segmentation fault
Error: unable to find a version of ndiswrapper!
oem@Cherokee-Ubuntu:~$ sudo ndiswrapper -r netmw14x
Segmentation fault
Error: unable to find a version of ndiswrapper!
oem@Cherokee-Ubuntu:~$ sudo aptitude purge ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  ndiswrapper-common{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 98.3kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 140083 files and directories currently installed.)
Removing ndiswrapper-common ...
dpkg: warning: while removing ndiswrapper-common, directory '/etc/ndiswrapper' not empty so not removed.
Processing triggers for man-db ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

oem@Cherokee-Ubuntu:~$ sudo aptitude update
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-security/main Packages        
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done

oem@Cherokee-Ubuntu:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

oem@Cherokee-Ubuntu:~$ sudo aptitude install linux-headers-`uname -r`Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

oem@Cherokee-Ubuntu:~$ cd wireless
oem@Cherokee-Ubuntu:~/wireless$ tar -xzvf ndiswrapper-1.54.tar.gz
ndiswrapper-1.54/
ndiswrapper-1.54/AUTHORS
ndiswrapper-1.54/ChangeLog
ndiswrapper-1.54/INSTALL
ndiswrapper-1.54/Makefile
ndiswrapper-1.54/README
ndiswrapper-1.54/ndiswrapper.spec
ndiswrapper-1.54/ndiswrapper.8
ndiswrapper-1.54/loadndisdriver.8
ndiswrapper-1.54/utils/
ndiswrapper-1.54/utils/Makefile
ndiswrapper-1.54/utils/ndiswrapper
ndiswrapper-1.54/utils/loadndisdriver.c
ndiswrapper-1.54/utils/ndiswrapper-buginfo
ndiswrapper-1.54/driver/
ndiswrapper-1.54/driver/Makefile
ndiswrapper-1.54/driver/crt.c
ndiswrapper-1.54/driver/divdi3.c
ndiswrapper-1.54/driver/hal.c
ndiswrapper-1.54/driver/iw_ndis.c
ndiswrapper-1.54/driver/iw_ndis.h
ndiswrapper-1.54/driver/lin2win.h
ndiswrapper-1.54/driver/loader.c
ndiswrapper-1.54/driver/loader.h
ndiswrapper-1.54/driver/longlong.h
ndiswrapper-1.54/driver/mkexport.sh
ndiswrapper-1.54/driver/mkstubs.sh
ndiswrapper-1.54/driver/ndis.c
ndiswrapper-1.54/driver/ndis.h
ndiswrapper-1.54/driver/ndiswrapper.h
ndiswrapper-1.54/driver/ntoskernel.c
ndiswrapper-1.54/driver/ntoskernel.h
ndiswrapper-1.54/driver/ntoskernel_io.c
ndiswrapper-1.54/driver/pe_linker.c
ndiswrapper-1.54/driver/pe_linker.h
ndiswrapper-1.54/driver/pnp.c
ndiswrapper-1.54/driver/pnp.h
ndiswrapper-1.54/driver/proc.c
ndiswrapper-1.54/driver/rtl.c
ndiswrapper-1.54/driver/usb.c
ndiswrapper-1.54/driver/usb.h
ndiswrapper-1.54/driver/win2lin_stubs.S
ndiswrapper-1.54/driver/winnt_types.h
ndiswrapper-1.54/driver/workqueue.c
ndiswrapper-1.54/driver/wrapmem.h
ndiswrapper-1.54/driver/wrapmem.c
ndiswrapper-1.54/driver/wrapper.c
ndiswrapper-1.54/driver/wrapper.h
ndiswrapper-1.54/driver/wrapndis.c
ndiswrapper-1.54/driver/wrapndis.h
oem@Cherokee-Ubuntu:~/wireless$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
oem@Cherokee-Ubuntu:~/wireless$ cd ndiswrapper-1.54
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo updatedb
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ locate ndiswrapper
/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper/netmw14x
/etc/ndiswrapper/netmw14x/11AB:2A02.5.conf
/etc/ndiswrapper/netmw14x/11AB:2A02:800A:1799.5.conf
/etc/ndiswrapper/netmw14x/netmw145.sys
/etc/ndiswrapper/netmw14x/netmw14x.inf
/home/oem/wireless/ndiswrapper-1.54
/home/oem/wireless/ndiswrapper-1.54.tar.gz
/home/oem/wireless/ndiswrapper-1.55
/home/oem/wireless/ndiswrapper-1.55.tar.gz
/home/oem/wireless/ndiswrapper-1.54/AUTHORS
/home/oem/wireless/ndiswrapper-1.54/ChangeLog
/home/oem/wireless/ndiswrapper-1.54/INSTALL
/home/oem/wireless/ndiswrapper-1.54/Makefile
/home/oem/wireless/ndiswrapper-1.54/README
/home/oem/wireless/ndiswrapper-1.54/driver
/home/oem/wireless/ndiswrapper-1.54/loadndisdriver.8
/home/oem/wireless/ndiswrapper-1.54/ndiswrapper.8
/home/oem/wireless/ndiswrapper-1.54/ndiswrapper.spec
/home/oem/wireless/ndiswrapper-1.54/utils
/home/oem/wireless/ndiswrapper-1.54/driver/Makefile
/home/oem/wireless/ndiswrapper-1.54/driver/crt.c
/home/oem/wireless/ndiswrapper-1.54/driver/divdi3.c
/home/oem/wireless/ndiswrapper-1.54/driver/hal.c
/home/oem/wireless/ndiswrapper-1.54/driver/iw_ndis.c
/home/oem/wireless/ndiswrapper-1.54/driver/iw_ndis.h
/home/oem/wireless/ndiswrapper-1.54/driver/lin2win.h
/home/oem/wireless/ndiswrapper-1.54/driver/loader.c
/home/oem/wireless/ndiswrapper-1.54/driver/loader.h
/home/oem/wireless/ndiswrapper-1.54/driver/longlong.h
/home/oem/wireless/ndiswrapper-1.54/driver/mkexport.sh
/home/oem/wireless/ndiswrapper-1.54/driver/mkstubs.sh
/home/oem/wireless/ndiswrapper-1.54/driver/ndis.c
/home/oem/wireless/ndiswrapper-1.54/driver/ndis.h
/home/oem/wireless/ndiswrapper-1.54/driver/ndiswrapper.h
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel.c
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel.h
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.c
/home/oem/wireless/ndiswrapper-1.54/driver/pe_linker.c
/home/oem/wireless/ndiswrapper-1.54/driver/pe_linker.h
/home/oem/wireless/ndiswrapper-1.54/driver/pnp.c
/home/oem/wireless/ndiswrapper-1.54/driver/pnp.h
/home/oem/wireless/ndiswrapper-1.54/driver/proc.c
/home/oem/wireless/ndiswrapper-1.54/driver/rtl.c
/home/oem/wireless/ndiswrapper-1.54/driver/usb.c
/home/oem/wireless/ndiswrapper-1.54/driver/usb.h
/home/oem/wireless/ndiswrapper-1.54/driver/win2lin_stubs.S
/home/oem/wireless/ndiswrapper-1.54/driver/winnt_types.h
/home/oem/wireless/ndiswrapper-1.54/driver/workqueue.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapmem.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapmem.h
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.h
/home/oem/wireless/ndiswrapper-1.54/driver/wrapper.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapper.h
/home/oem/wireless/ndiswrapper-1.54/utils/Makefile
/home/oem/wireless/ndiswrapper-1.54/utils/loadndisdriver.c
/home/oem/wireless/ndiswrapper-1.54/utils/ndiswrapper
/home/oem/wireless/ndiswrapper-1.54/utils/ndiswrapper-buginfo
/home/oem/wireless/ndiswrapper-1.55/AUTHORS
/home/oem/wireless/ndiswrapper-1.55/ChangeLog
/home/oem/wireless/ndiswrapper-1.55/INSTALL
/home/oem/wireless/ndiswrapper-1.55/Makefile
/home/oem/wireless/ndiswrapper-1.55/README
/home/oem/wireless/ndiswrapper-1.55/driver
/home/oem/wireless/ndiswrapper-1.55/loadndisdriver.8
/home/oem/wireless/ndiswrapper-1.55/ndiswrapper.8
/home/oem/wireless/ndiswrapper-1.55/ndiswrapper.spec
/home/oem/wireless/ndiswrapper-1.55/utils
/home/oem/wireless/ndiswrapper-1.55/driver/.built-in.o.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.crt.o.d
/home/oem/wireless/ndiswrapper-1.55/driver/.crt_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.hal_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.ndis_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.ntoskernel_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.ntoskernel_io_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.rtl_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.tmp_versions
/home/oem/wireless/ndiswrapper-1.55/driver/.usb_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/Makefile
/home/oem/wireless/ndiswrapper-1.55/driver/built-in.o
/home/oem/wireless/ndiswrapper-1.55/driver/crt.c
/home/oem/wireless/ndiswrapper-1.55/driver/crt_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/divdi3.c
/home/oem/wireless/ndiswrapper-1.55/driver/hal.c
/home/oem/wireless/ndiswrapper-1.55/driver/hal_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/iw_ndis.c
/home/oem/wireless/ndiswrapper-1.55/driver/iw_ndis.h
/home/oem/wireless/ndiswrapper-1.55/driver/lin2win.h
/home/oem/wireless/ndiswrapper-1.55/driver/loader.c
/home/oem/wireless/ndiswrapper-1.55/driver/loader.h
/home/oem/wireless/ndiswrapper-1.55/driver/longlong.h
/home/oem/wireless/ndiswrapper-1.55/driver/mkexport.sh
/home/oem/wireless/ndiswrapper-1.55/driver/mkstubs.sh
/home/oem/wireless/ndiswrapper-1.55/driver/ndis.c
/home/oem/wireless/ndiswrapper-1.55/driver/ndis.h
/home/oem/wireless/ndiswrapper-1.55/driver/ndis_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/ndiswrapper.h
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel.c
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel.h
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel_io.c
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel_io_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/pe_linker.c
/home/oem/wireless/ndiswrapper-1.55/driver/pe_linker.h
/home/oem/wireless/ndiswrapper-1.55/driver/pnp.c
/home/oem/wireless/ndiswrapper-1.55/driver/pnp.h
/home/oem/wireless/ndiswrapper-1.55/driver/proc.c
/home/oem/wireless/ndiswrapper-1.55/driver/rtl.c
/home/oem/wireless/ndiswrapper-1.55/driver/rtl_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/usb.c
/home/oem/wireless/ndiswrapper-1.55/driver/usb.h
/home/oem/wireless/ndiswrapper-1.55/driver/usb_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/win2lin_stubs.S
/home/oem/wireless/ndiswrapper-1.55/driver/winnt_types.h
/home/oem/wireless/ndiswrapper-1.55/driver/workqueue.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapmem.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapmem.h
/home/oem/wireless/ndiswrapper-1.55/driver/wrapndis.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapndis.h
/home/oem/wireless/ndiswrapper-1.55/driver/wrapper.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapper.h
/home/oem/wireless/ndiswrapper-1.55/utils/Makefile
/home/oem/wireless/ndiswrapper-1.55/utils/loadndisdriver.c
/home/oem/wireless/ndiswrapper-1.55/utils/ndiswrapper
/home/oem/wireless/ndiswrapper-1.55/utils/ndiswrapper-buginfo
/var/cache/apt/archives/ndiswrapper-common_1.54-2ubuntu1_all.deb
/var/cache/apt/archives/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo rm -r /etc/ndiswrapper
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo rm -r /etc/ndiswrapper
rm: cannot remove `/etc/ndiswrapper': No such file or directory
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo rm -r /etc/modprobe.d/ndiswrapper
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo rm -r /etc/ndiswrapper/netmw14x
rm: cannot remove `/etc/ndiswrapper/netmw14x': No such file or directory
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo rm /var/cache/apt/archives/ndiswrapper-common_1.54-2ubuntu1_i386.deb
rm: cannot remove `/var/cache/apt/archives/ndiswrapper-common_1.54-2ubuntu1_i386.deb': No such file or directory
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo rm /var/cache/apt/archives/ndiswrapper-common_1.54-2ubuntu1_all.deb
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo rm /var/cache/apt/archives/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo updatedb
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ locate ndiswrapper
/home/oem/wireless/ndiswrapper-1.54
/home/oem/wireless/ndiswrapper-1.54.tar.gz
/home/oem/wireless/ndiswrapper-1.55
/home/oem/wireless/ndiswrapper-1.55.tar.gz
/home/oem/wireless/ndiswrapper-1.54/AUTHORS
/home/oem/wireless/ndiswrapper-1.54/ChangeLog
/home/oem/wireless/ndiswrapper-1.54/INSTALL
/home/oem/wireless/ndiswrapper-1.54/Makefile
/home/oem/wireless/ndiswrapper-1.54/README
/home/oem/wireless/ndiswrapper-1.54/driver
/home/oem/wireless/ndiswrapper-1.54/loadndisdriver.8
/home/oem/wireless/ndiswrapper-1.54/ndiswrapper.8
/home/oem/wireless/ndiswrapper-1.54/ndiswrapper.spec
/home/oem/wireless/ndiswrapper-1.54/utils
/home/oem/wireless/ndiswrapper-1.54/driver/Makefile
/home/oem/wireless/ndiswrapper-1.54/driver/crt.c
/home/oem/wireless/ndiswrapper-1.54/driver/divdi3.c
/home/oem/wireless/ndiswrapper-1.54/driver/hal.c
/home/oem/wireless/ndiswrapper-1.54/driver/iw_ndis.c
/home/oem/wireless/ndiswrapper-1.54/driver/iw_ndis.h
/home/oem/wireless/ndiswrapper-1.54/driver/lin2win.h
/home/oem/wireless/ndiswrapper-1.54/driver/loader.c
/home/oem/wireless/ndiswrapper-1.54/driver/loader.h
/home/oem/wireless/ndiswrapper-1.54/driver/longlong.h
/home/oem/wireless/ndiswrapper-1.54/driver/mkexport.sh
/home/oem/wireless/ndiswrapper-1.54/driver/mkstubs.sh
/home/oem/wireless/ndiswrapper-1.54/driver/ndis.c
/home/oem/wireless/ndiswrapper-1.54/driver/ndis.h
/home/oem/wireless/ndiswrapper-1.54/driver/ndiswrapper.h
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel.c
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel.h
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.c
/home/oem/wireless/ndiswrapper-1.54/driver/pe_linker.c
/home/oem/wireless/ndiswrapper-1.54/driver/pe_linker.h
/home/oem/wireless/ndiswrapper-1.54/driver/pnp.c
/home/oem/wireless/ndiswrapper-1.54/driver/pnp.h
/home/oem/wireless/ndiswrapper-1.54/driver/proc.c
/home/oem/wireless/ndiswrapper-1.54/driver/rtl.c
/home/oem/wireless/ndiswrapper-1.54/driver/usb.c
/home/oem/wireless/ndiswrapper-1.54/driver/usb.h
/home/oem/wireless/ndiswrapper-1.54/driver/win2lin_stubs.S
/home/oem/wireless/ndiswrapper-1.54/driver/winnt_types.h
/home/oem/wireless/ndiswrapper-1.54/driver/workqueue.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapmem.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapmem.h
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.h
/home/oem/wireless/ndiswrapper-1.54/driver/wrapper.c
/home/oem/wireless/ndiswrapper-1.54/driver/wrapper.h
/home/oem/wireless/ndiswrapper-1.54/utils/Makefile
/home/oem/wireless/ndiswrapper-1.54/utils/loadndisdriver.c
/home/oem/wireless/ndiswrapper-1.54/utils/ndiswrapper
/home/oem/wireless/ndiswrapper-1.54/utils/ndiswrapper-buginfo
/home/oem/wireless/ndiswrapper-1.55/AUTHORS
/home/oem/wireless/ndiswrapper-1.55/ChangeLog
/home/oem/wireless/ndiswrapper-1.55/INSTALL
/home/oem/wireless/ndiswrapper-1.55/Makefile
/home/oem/wireless/ndiswrapper-1.55/README
/home/oem/wireless/ndiswrapper-1.55/driver
/home/oem/wireless/ndiswrapper-1.55/loadndisdriver.8
/home/oem/wireless/ndiswrapper-1.55/ndiswrapper.8
/home/oem/wireless/ndiswrapper-1.55/ndiswrapper.spec
/home/oem/wireless/ndiswrapper-1.55/utils
/home/oem/wireless/ndiswrapper-1.55/driver/.built-in.o.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.crt.o.d
/home/oem/wireless/ndiswrapper-1.55/driver/.crt_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.hal_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.ndis_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.ntoskernel_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.ntoskernel_io_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.rtl_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/.tmp_versions
/home/oem/wireless/ndiswrapper-1.55/driver/.usb_exports.h.cmd
/home/oem/wireless/ndiswrapper-1.55/driver/Makefile
/home/oem/wireless/ndiswrapper-1.55/driver/built-in.o
/home/oem/wireless/ndiswrapper-1.55/driver/crt.c
/home/oem/wireless/ndiswrapper-1.55/driver/crt_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/divdi3.c
/home/oem/wireless/ndiswrapper-1.55/driver/hal.c
/home/oem/wireless/ndiswrapper-1.55/driver/hal_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/iw_ndis.c
/home/oem/wireless/ndiswrapper-1.55/driver/iw_ndis.h
/home/oem/wireless/ndiswrapper-1.55/driver/lin2win.h
/home/oem/wireless/ndiswrapper-1.55/driver/loader.c
/home/oem/wireless/ndiswrapper-1.55/driver/loader.h
/home/oem/wireless/ndiswrapper-1.55/driver/longlong.h
/home/oem/wireless/ndiswrapper-1.55/driver/mkexport.sh
/home/oem/wireless/ndiswrapper-1.55/driver/mkstubs.sh
/home/oem/wireless/ndiswrapper-1.55/driver/ndis.c
/home/oem/wireless/ndiswrapper-1.55/driver/ndis.h
/home/oem/wireless/ndiswrapper-1.55/driver/ndis_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/ndiswrapper.h
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel.c
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel.h
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel_io.c
/home/oem/wireless/ndiswrapper-1.55/driver/ntoskernel_io_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/pe_linker.c
/home/oem/wireless/ndiswrapper-1.55/driver/pe_linker.h
/home/oem/wireless/ndiswrapper-1.55/driver/pnp.c
/home/oem/wireless/ndiswrapper-1.55/driver/pnp.h
/home/oem/wireless/ndiswrapper-1.55/driver/proc.c
/home/oem/wireless/ndiswrapper-1.55/driver/rtl.c
/home/oem/wireless/ndiswrapper-1.55/driver/rtl_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/usb.c
/home/oem/wireless/ndiswrapper-1.55/driver/usb.h
/home/oem/wireless/ndiswrapper-1.55/driver/usb_exports.h
/home/oem/wireless/ndiswrapper-1.55/driver/win2lin_stubs.S
/home/oem/wireless/ndiswrapper-1.55/driver/winnt_types.h
/home/oem/wireless/ndiswrapper-1.55/driver/workqueue.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapmem.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapmem.h
/home/oem/wireless/ndiswrapper-1.55/driver/wrapndis.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapndis.h
/home/oem/wireless/ndiswrapper-1.55/driver/wrapper.c
/home/oem/wireless/ndiswrapper-1.55/driver/wrapper.h
/home/oem/wireless/ndiswrapper-1.55/utils/Makefile
/home/oem/wireless/ndiswrapper-1.55/utils/loadndisdriver.c
/home/oem/wireless/ndiswrapper-1.55/utils/ndiswrapper
/home/oem/wireless/ndiswrapper-1.55/utils/ndiswrapper-buginfo
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ 
```


Now is when I begin to have problems
```

oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ make
make -C driver
make[1]: Entering directory `/home/oem/wireless/ndiswrapper-1.54/driver'
make -C /usr/src/linux-headers-2.6.31-17-generic M=/home/oem/wireless/ndiswrapper-1.54/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  LD      /home/oem/wireless/ndiswrapper-1.54/driver/built-in.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/crt_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/crt.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/hal_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/hal.o
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/iw_ndis.o
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/loader.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/ndis_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/ndis.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.o
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.c: In function ‘IoConnectInterrupt’:
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.c:566: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/pe_linker.o
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/pnp.o
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/proc.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/rtl_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/rtl.o
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/wrapmem.o
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.o
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c:1747: error: unknown field ‘poll_controller’ specified in initializer
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c:1747: warning: initialization from incompatible pointer type
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c:1747: error: expected ‘}’ before ‘;’ token
make[3]: *** [/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/oem/wireless/ndiswrapper-1.54/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/oem/wireless/ndiswrapper-1.54/driver'
make: *** [all] Error 2
oem@Cherokee-Ubuntu:~/wireless/ndiswrapper-1.54$ sudo make install
make -C driver install
make[1]: Entering directory `/home/oem/wireless/ndiswrapper-1.54/driver'
make -C /usr/src/linux-headers-2.6.31-17-generic M=/home/oem/wireless/ndiswrapper-1.54/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/crt_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/crt.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/hal_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/hal.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/ndis_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/ndis.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel.o
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.o
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.c: In function ‘IoConnectInterrupt’:
/home/oem/wireless/ndiswrapper-1.54/driver/ntoskernel_io.c:566: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
  MKEXPORT /home/oem/wireless/ndiswrapper-1.54/driver/rtl_exports.h
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/rtl.o
  CC [M]  /home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.o
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c:1747: error: unknown field ‘poll_controller’ specified in initializer
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c:1747: warning: initialization from incompatible pointer type
/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.c:1747: error: expected ‘}’ before ‘;’ token
make[3]: *** [/home/oem/wireless/ndiswrapper-1.54/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/oem/wireless/ndiswrapper-1.54/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/oem/wireless/ndiswrapper-1.54/driver'
make: *** [install] Error 2

```


For some reason ndiswrapper is still not installed and I am stuck here.
Any help would be greatly appreciated.

---

### Post by ubu_dynamite on 2010-01-30
Haven't used the card for some time but ndiswrapper 1.54 is in karmic repositories no need to build from source have you tried that one?


To install ndiswrapper (with lan port connected):
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

Install the windows driver:
```
sudo ndiswrapper -i /driver_location/inf_file.inf
```

Check driver is installed:
```
ndiswrapper -l
```

Load module:
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```

Add to startup:
```
sudo ndiswrapper -m
```

---

### Post by TheBig3 on 2010-01-30
Thanks, finally it's installed. I had tried the ubuntu defaults before with out it working.

Just now I can't get it to access the network. I have manually setup both wired and wireless networks before, just not in Ubuntu (or any linux system). Any advice would be appreciated one more.

And once again...

Thank You Very Much!!!!!!

---

### Post by ubu_dynamite on 2010-01-31
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/9.10/internet/C/connecting-wireless.html](https://help.ubuntu.com/9.10/internet/C/connecting-wireless.html)

---

