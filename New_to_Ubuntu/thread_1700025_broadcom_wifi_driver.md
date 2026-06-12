---
title: "broadcom wifi driver"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-03-04
hi i have a broadcom wlan i got the additional drivers and it works but ever since i installed WINE i have had a problem with it disabling without being able to re-enable it i have to restart my laptop and that will fix it but 5 mins to hours later it will happen again i dont see how WINE will cause that or if my installing WINE was just a coincidence anyone else seen this problem?

---

### Post by fatality_uk on 2011-03-04
How did you get the additional drivers? Could you also let us know which version of Ubuntu?

---

### Post by mushroom08 on 2011-03-04
i have ubuntu 10.10 and i used system > admin > additional drivers when i first installed a week ago i put on WINE 2 nights ago and 1 hour after that is when the problem started

---

### Post by Hippytaff on 2011-03-04
have you tried unistalling wine, and trying wireless to see if that is actually the problem?

---

### Post by mushroom08 on 2011-03-04
its a intermittent problem but no i have not like now my wifi is working but this morning i had to restart 3 times before it would i will uninstall WINE and repost if the problem stops over the next 24 hours

---

### Post by Hippytaff on 2011-03-04
Before you do, it might just be network and router things...I often have to disconnect and reconnect. It's not a ubuntu/linux thing because the mrs has it with her xp so I'd see how it goes and then start some testing if it persists :-)

---

### Post by mushroom08 on 2011-03-04
now that you mention it yes when i was running XP i was getting tired of the errors i was having blue screens, freezes, long load times, and wifi driver problems. a friend of mine started using kbuntu and told me how good it ran compared to his factory win 7 that i switched im very new to this how would i go about testing?

---

### Post by Hippytaff on 2011-03-04
There are a number of different [diagnostic commands]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands") you can do from the terminal...but if you think it's something to do with installing wine, the first thing I would do is uninstall wine and see if the problem persists...then if it still persists it could be any number of things...what I like to call fun ;-)

---

### Post by mushroom08 on 2011-03-04
ok I've un-installed WINE i wasn't using it yet anyway if the problem keeps up ill use the commands and post the results if not what can i do to fix it with WINE?

---

### Post by Hippytaff on 2011-03-04
Don't know :? lets see if thats the problem first ;-)

---

### Post by mushroom08 on 2011-03-04
ok ill give it 24 hours

---

### Post by Hippytaff on 2011-03-04
;-) report back with your findings

---

### Post by mushroom08 on 2011-03-05
ok WINE was not the problem i ran one of the test commands heres what it told me when the wlan was working


  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:16:98:5b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic firmware=N/A ip=192.168.2.4 link=yes multicast=yes wireless=IEEE 802.11bg

and when it crashed


  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:16:98:5b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

is this any help or what other test should i run?

---

### Post by Hippytaff on 2011-03-05
This shows the link is dropping. It might be a driver thing - have a read of[ this ]("http://ubuntuforums.org/showthread.php?t=25683")

---

### Post by mushroom08 on 2011-03-05
i cant find the files it calls for (i dont have a dell i have a HP if that helps)

---

### Post by Hippytaff on 2011-03-05
I don't have much time s please forgive the brevity of my responses and links rather than explaining myself, but if your having trouble with that driver you might want to get the windows xp driver and install it using [ndisgtk]("http://linuxappfinder.com/package/ndisgtk")

It has to be XP driver though. Also you will either have to uninstall the current driver or blacklist it. in a terminal type ```
man modprobe
``` or search modprobe online to learn how to use modprobe - this is the tool/command used to install and uninstall drivers (it's very straightforward if you know the name of the driver you want to install/uninstall)

I call by in a bit to see how your getting on

---

### Post by mushroom08 on 2011-03-05
i got rid of the driver i was useing and got that windows driver program and i dl the driver from the HP site but cant install it because it is a .exe and not a .inf file /edit i tryed extracting the files but ubuntu wont do it

---

### Post by Hippytaff on 2011-03-06
You should be able to extract the inf and sys files....also [this is worth a look]("http://bcm43xx.berlios.de/")

---

### Post by mushroom08 on 2011-03-06
when i tried to extract the file i got this error message

Archive:  /home/mushroom/Downloads/sp33008.exe
[/home/mushroom/Downloads/sp33008.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/mushroom/Downloads/sp33008.exe or
          /home/mushroom/Downloads/sp33008.exe.zip, and cannot find /home/mushroom/Downloads/sp33008.exe.ZIP, period.

---

### Post by Hippytaff on 2011-03-06
apparently you can extract the inf and sys files from an exe with this p7zip-full
```
sudo apt-get install p7zip-full
```

---

### Post by mushroom08 on 2011-03-06
im not sure what i did but now my comp isnt listing my wlan card at all

---

### Post by Hippytaff on 2011-03-06
Excellent....glad you got it sorted ;-)

---

### Post by mushroom08 on 2011-03-06
wait my card ISNT showing up now as in i dont have any wifi options my comp is no longer recognizing i have a wlan is what ment

---

### Post by Hippytaff on 2011-03-07
Sorry thought you fixed it. Once you have removed the original driver install the one as per the instructions, or you might want to try the Broadcom one from additional drivers again

---

### Post by mushroom08 on 2011-03-07
i have installed a fresh copy of ubuntu to see if that will fix it ill post in a day or two

---

### Post by Hippytaff on 2011-03-08
I was going to suggest that that might be easier if you have everything important backed up. Let me know. Sorry I haven't had much time to get into the nitty gritty.

---

### Post by mushroom08 on 2011-03-15
srry its been a awhile got parts i've been needing for the car been busy anyway ya the reinstall did not work in fact my wifi is not working at all now

---

### Post by burcs on 2011-03-16
> **mushroom08 said:**
> srry its been a awhile got parts i've been needing for the car been busy anyway ya the reinstall did not work in fact my wifi is not working at all now

[_This_]("http://ubuntuforums.org/showpost.php?p=8297863&postcount=6") worked for me, when nothing else would.

---

### Post by Hippytaff on 2011-03-16
Try giong to system->administration->additional drivers. Install the bcm one. if it's not there try the **firmware-b43-installer** package from synaptic package manager...failing this try using the the .inf and .sys files from the windows XP driver with ndisgtk again. the extraction error you got before can be gottne around by installing p7zip full as in a previous post

---

### Post by mushroom08 on 2011-03-16
its already installed

---

### Post by Hippytaff on 2011-03-16
Which?

---

### Post by mushroom08 on 2011-03-16
the driver and the package i looked at both of them

---

### Post by Hippytaff on 2011-03-16
is the windows driver on a disc or did you download it?

It should be as simple as extracting the inf and sys files to a folder. Pointing ndisgtk at the inf file and away to go

---

### Post by mushroom08 on 2011-03-16
the windows driver i dl from the hp site

---

### Post by Hippytaff on 2011-03-16
How are you trying to extract the files?

---

### Post by mushroom08 on 2011-03-16
right click > extract

---

### Post by mushroom08 on 2011-03-16
ok thats weird i just tried removing the b43 driver to try the windows one again and i get a error and it wont let me

---

### Post by josephmills on 2011-03-16
go to terminal and type in 
```

lspci

```
then paste it here

---

### Post by mushroom08 on 2011-03-16
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

---

### Post by josephmills on 2011-03-16
> 
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controlleryou need a b43 driver do you have that yet? you can go to termanial and type n 
```

ifconfig

```if your wlan0 comes up then I think you have it. you can post ifconfig here but take out your eth0 and lo we dont need to see that. also try 
```

iwconfig

```
but as mentioned above we dont need your address and mac number and all that jazz

---

### Post by wep940 on 2011-03-16
The OP has already tried B43 once before, however I think there is something that needs to be done first before doing anything else:
 
- if you tried ndiswrapper via ndisgtk, it probably blacklisted the B43 and other
  included drivers.  You would need to edit the blacklist.conf file and comment out
  those entries
 
- if you have ndiswrapper loaded (via modprobe or by adding it to the modules file)
  it can quite often interfere with other drivers
 
So, my suggestion is to first be sure the blacklist.conf file is not blacklisting the B43 or other included Broadcom drivers (B43-legacy or some such thing and ssb).  If it is, comment out those entries.
 
Uninstall ndiswrapper and ndisgtk (don't get me wrong - I'm not against ndiswrapper/ndisgtk at all).
 
Reboot.
 
Try the B43 driver again or is another driver is also listed try that in it's place.
 
If you just can't figure out how to get this to work, let me know and we'll get the driver files for you.  It's just that in your case you have the ubuitious Broadcom 4318, and the restricted drivers should work for you.
 
So, if you can't get by wirelessly, temporarily hard-wire a connection between your PC and your router, do a sudo apt-get update in a terminal window, then check restricted drivers again and try enabling them 1 at a time.  If B43 doesn't work, disable it and try the other (I *think* either something with SSA or ssb or something like that should also show up - I would try the SSA if available).

---

### Post by josephmills on 2011-03-16
ok so I am going to make a video on how to install that b43 driver it will be up in an hour or so I will post a link

---

### Post by mushroom08 on 2011-03-16
yes i have b43 that driver is not working which is my problem in the first place

---

### Post by mushroom08 on 2011-03-16
i have reinstalled my entire OS and have not tried ndisk yet so its not the problem and yes im hardwired to my modem my laptops all i have right now


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by josephmills on 2011-03-16
go to termainail and type in 
```

lspci -vnn | grep 14e4

```
and then paste that so we can see

---

### Post by mushroom08 on 2011-03-16
was making dinner srry and here it is

mushroomstamp@MushroomEmpire:~$ lspci -vnn | grep 14e4
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

### Post by josephmills on 2011-03-16
> **mushroom08 said:**
> was making dinner srry and here it is

mushroomstamp@MushroomEmpire:~$ lspci -vnn | grep 14e4
05:02.0 Network controller [0280]: Broadcom Corporat. Yon BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
ok so after looking at this you 100% need a b43 driver I went though some of my computers and found one with the same chip set and it is running real good with it and can even pick up packets in mon0 mode here is that video that I was talking about'
[http://www.youtube.com/watch?v=hAHN-YnmrLw](http://www.youtube.com/watch?v=hAHN-YnmrLw)
Also have you upgraded and updated? 
```
 
sudo apt-get update

```
```

sudo apt-get upgrade

```
also is there a button to turn on your card or is it something like fn+f2 ?

---

### Post by mushroom08 on 2011-03-16
ok i already had the driver installed but the two codes you posted did somthing now its working thx :popcorn:

---

### Post by josephmills on 2011-03-16
I am glad that you got it working have fun :P

---

### Post by wep940 on 2011-03-16
It was probably the sudo apt-get update, as I recommended at the end of my post as well.  I'm just glad it's working for you.

---

### Post by Hippytaff on 2011-03-17
Perserverance will succeed. Glad you got it sorted :-)

---

### Post by mushroom08 on 2011-03-17
now if i could only get the car finished lol for every problem i fix i find another one *sigh* guess thats what i get for buying on craigslist ](*,)

---

