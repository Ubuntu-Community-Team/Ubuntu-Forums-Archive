---
title: "Need Help to install ndiswrapper and setup WiFi, PLEASE HELP......."
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Modern Mogul on 2008-05-05
Ok SO I am completely new to Linux and I just installed Ubuntu on one of my spare laptops that I stopped using becuase I am trying to make the transition to linux, I know its way better than Vista...

So I installed Ubuntu the other day, and it does not recognize my internal wireless network card... Ive been on numerous sites and believe that I can install ndiswrapper if 1) I knew what driver for the wifi card is needed and 2) i had a wired internet connection, but I have neither...

I did a clean install, completely wiping out the windows partition so i can't locate anything within the computer... So everything I do I would have to donwload on a different computer, copy it to a cd, and stick it on the desktop of the laptop running ubuntu (but its not installed)...

I downloaded ndiswrapper and copied it on to a cd, then copied it onto the laptop running Ubuntu...

I also downloaded and installed wifi radar, but the card is still not recognized...

OHHH and its the AMD64 version on a Gateway MX3417 Notebook which originally came with XP, but is Vista compatible (not sure if that makes a differnce)...

I tried sharing the internet connection with the other laptop that connects wirelessly (running Vista), lol, but thats another beast in itself...

I apologize in advance if this problem has already been addressed, but I have spent maybe a total of 8 hours within the past 2 days trying to find how to do this and have found nothing that works... 
:confused::confused::confused::(<<<<<<<<<<<<<< SO PLEASE HELP >>>>>>>>>>> :(:confused::confused::confused:

---

### Post by Modern Mogul on 2008-05-12
LOL, its been 6 days and no one has helped me... WOW...

---

### Post by Ayuthia on 2008-05-12
If you don't mind going to the Terminal, can you post the results of ndiswrapper -v and ndiswrapper -l?  Also, can you let us know what your network card is (lspci -nn) and which version of Ubuntu you are using (Feisty, Gutsy, Hardy)?  It will help us figure out what you might need to do.

---

### Post by Modern Mogul on 2008-05-12
Ok so I did got an internet connection and I installed ndiswrapper, and then I did the commands you said... I just copied and pasted the results, here it is...

rick@rick-laptop:~$ ndiswrapper -v
Error: no ndiswrapper utils found!

rick@rick-laptop:~$ ndiswrapper -l
Error: no ndiswrapper utils found!

rick@rick-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation MCP51 PCI-X GeForce Go 6100 [10de:0247] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
06:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)


Oh and I'm not sure which version of ubuntu I have... I actually didn't know there were different versions, I just went to the ubuntu website and downloaded the version for the AMD64...

By the way, thanks in advance...

---

### Post by Ayuthia on 2008-05-13
> **Modern Mogul said:**
> Ok so I did got an internet connection and I installed ndiswrapper, and then I did the commands you said... I just copied and pasted the results, here it is...

rick@rick-laptop:~$ ndiswrapper -v
Error: no ndiswrapper utils found!

rick@rick-laptop:~$ ndiswrapper -l
Error: no ndiswrapper utils found!
It looks like you are missing ndiswrapper-utils-1.9.  Try installing that and see if it helps.

Another option is to try this [link]("http://blog.alexrybicki.com/2008/04/ubuntu-804-hardy-heron-is-here.html").  It has a link to the drivers that you might need.  I think that you might need the 64-bit.  I am not positive though since I have a different wireless card.

---

### Post by Modern Mogul on 2008-05-13
Ok so I just got off the phone with Gateway and the guy told me this is the type of internet network card I have...

gemtex bcm4318e11gwmib-158g21a20 USA

so I went onto thegateway website and downloaded the driver for windows xp... stuck it onto a dvd-rw along with ndiswrapper-utils 1.9 

Now I don't know hot install the from the DVD-RW

---

### Post by Modern Mogul on 2008-05-13
Well I just installed the utils, the version i installed was 'ndiswrapper-utils-1.9_1.52-1_amd64.deb'

So now I just need to know how to use ndiswrapper to install the driver, I copied it onto my desktop from the dvd-rw

FYI - ndiswrapper -v shows me the version I installed, but ndiswrapper -l doesn't do anthing...

and the driver is a .exe file

---

### Post by Modern Mogul on 2008-05-13
ok so I downloaded both the WinXP64 and WinXp2K drivers from the website you gave me, and when i try ndiswrapper -i net8185.inf it tells me that it couldn't access the file, and that no so such file exists... here is exactly what it says...

rick@rick-laptop:~$ ndiswrapper -i net8185.inf
couldn't open net8185.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

and then when I tell it where the file is it gives me this...

rick@rick-laptop:~$ ndiswrapper -i /home/rick/Desktop/WinXP2K/net8185.inf
couldn't create /etc/ndiswrapper/net8185: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.

---

### Post by Ayuthia on 2008-05-13
> **Modern Mogul said:**
> ok so I downloaded both the WinXP64 and WinXp2K drivers from the website you gave me, and when i try ndiswrapper -i net8185.inf it tells me that it couldn't access the file, and that no so such file exists... here is exactly what it says...

rick@rick-laptop:~$ ndiswrapper -i net8185.inf
couldn't open net8185.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

and then when I tell it where the file is it gives me this...

rick@rick-laptop:~$ ndiswrapper -i /home/rick/Desktop/WinXP2K/net8185.inf
couldn't create /etc/ndiswrapper/net8185: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.
You need to have root access to run this function because it is writing things to /etc:
```
sudo ndiswrapper -i /home/rick/Desktop/WinXP2K/net8185.inf
```

---

### Post by tattrat on 2008-05-13
Hi, I have done this so many times, I will ad my take on it. If you haven't already done it, you will need to break open the .exe file to get the .inf file. This can be done on a windows machine, using winrar (free download), although there may be other ways. Extract both the .inf and .sys files and copy them to your ubuntu machine. Place them on the desktop.

(If there is more than one .sys file, then head over to the ndiswrapper website (i think you can get access to it via sourceforge) and find your card in the list for instructions on which .sys file or files are needed).

Now open up a terminal window and type:

```
cd Desktop
```

now type:

```
sudo ndiswrapper -i net8185.inf
```

Then check that everything has gone OK by typing:

```
ndiswrapper -l
```

If that gives you no error, then type:

```
sudo depmod -a
```

And when that has done type:

```
sudo modprobe ndiswrapper
```

Then in order to get the thing to start every time you boot, type:

```
sudo ndiswrapper -m
```

Now you want to make sure it kicks off after reboot, type:

```
gksudo gedit /etc/modules
```

This will open up the text editor

add:

```
ndiswrapper 
```

as the last line of the file and save.

Now if you type :

```
iwconfig
```

you should see your wireless interface as wlan0 or wlan1.

At this point I always right click the network icon in the sys tray in the top right hand side of the screen, and see if it lists available wireless networks.

If it does then you are done, well almost anyways....

I always blacklist the broadcom driver for good measure, thus:
(I am not certain it is strictly necessary, but it will do no harm).

```
gksudo gedit /etc/modprob.d/blacklist
```

and add the lines 

```
blacklist bcm43xx
blacklist b43

```
anywhere in the file.

Hope this helps, report back if you have any further problems.

---

### Post by Modern Mogul on 2008-05-13
Thanks a bunch guys... here is what i have now...

rick@rick-laptop:~$ ndiswrapper -l
net8185 : driver installed
        devidce (10EC:8185) present

so that one has no alteratives

and then I have this...

rick@rick-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL -8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap list
       configuration: latency=0 maxlatency=64 mingnt=32

rick@rick-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

rick@rick-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

and when i tried to type ndiswrapper into that .txt file, it was alraedy at the last line, it actuall had ndiswrapper twice... so i deleted one of them and then saved...

And its not working, wifi radar program doesn't pick up anything, I can't ping anything, and the network manager doesn't even show a wireless ability yet... Please Help...

---

### Post by tattrat on 2008-05-13
I would suggest that the next thing you try is to also add

```
blacklist rt2500

```

to /etc/modprobe.d/blacklist

Then reboot. I always use the gui based network tools to then disable all other network devices, and also to start the wireless running with ndiswrapper.

Try 

```
iwconfig 
```

to see what is there.

---

### Post by Ayuthia on 2008-05-13
> **Modern Mogul said:**
> 
rick@rick-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL -8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap list
       configuration: latency=0 maxlatency=64 mingnt=32

The UNCLAIMED part of this is telling you that the module has not been loaded.  Have you done sudo modprobe ndiswrapper?

---

### Post by Modern Mogul on 2008-05-13
Sudo modprobe does do anything, it just goes to the next command prompt

---

### Post by tattrat on 2008-05-13
> **Modern Mogul said:**
> Sudo modprobe does do anything, it just goes to the next command prompt

When it works, it doesn't give any output. Give it a try.

---

### Post by Modern Mogul on 2008-05-13
yea and after blacklist rt2500 and a fresh restart, iwconfig returns exactly the same thing, no wireless extensions for both lo and eth0...

by the way, after i did the sudo modprobe ndiswrapper i got the same thing for lshw -C network...

I know this is alot guys but thanks for helping me, not sure if I'll have to give up on this linux thing or not, hope we can get it to work... let me know if there is anything else I can do that would give you guys more info as to waht is going on...

---

### Post by Modern Mogul on 2008-05-13
if you have aol chat let me know so that maybe i can just chat with you to help me... I'm not sure what you mean by give it a try... i opened firefox andit says its still on offline mode... when i right click on the network manager it just has Enable Networking checked and the connection information is grey so i can't select it, then it has edit wireless networks, lol, when i click on that the little program opens but it doesn't show anything...

---

### Post by SurferGTO on 2008-05-14
im having basically the exact same problem. iwconfig shows no wireless extensions across the board. hardy on an hp dv2000 using ndiswrapper with the driver installed. no drivers are showing up in the hardware driver (restricted driver) list. I have been trying to get the wireless working in ubuntu since gutsy and have never gotten it to work. ive been forced to pay verizon for a usb modem that, imho, sucks.

edit: system>admin>windows wireless drivers shows the driver is installed but no hardware present.

---

### Post by SurferGTO on 2008-05-14
anyone? ive tried so many walkthrus, install guides, this and that... i feel like im going in circles. my heads about to explode! i was so looking foreward to hardy because i thought this wireless crap would have been resolved but sadly it would appear its only gotten worse!! at least for me... it seems like i had gotten farther than this before (if i remember, i at least had the hardware recognized at one point with gutsy). but id never had wireless with ubuntu. very very frustrating. im really about to just give up and go back to vista...

---

### Post by Modern Mogul on 2008-05-14
Hey Surfer, I'm not sure if this tut will help you, but I ended up doing a complete re-install since I am new to linux anyway, i'm not sure if you can do that, but now I am following this tut and waiting to see if it works... check it out...[http://ubuntuforums.org/showthread.php?t=771894&highlight=install+ndiswrapper+wireless+drivers+newbies]("http://ubuntuforums.org/showthread.php?t=771894&highlight=install+ndiswrapper+wireless+drivers+newbies")

---

### Post by tattrat on 2008-05-14
This is identical steps to those above. If you are, or already have done a reinstall, I would suggest, that you simply use the ndiswrapper which is already on the install cd/dvd. It works for me. 

All you need to do is go to system->amin->software sources and make sure that the cd is included as a source.

Then in the terminal, just type 

```
sudo apt-get install ndisgtk
```

This will install ndiswrapper, ndisgtk and ndiswrapper-utils. I don't really think it is necessary to compile a new version of ndiswrapper; your card has probably worked fine for a long time, using the version packaged in hardy. (perhaps this is your problem).

---

### Post by SurferGTO on 2008-05-14
Thanks all for the replys. The isntall disc i have is for Gutsy, I upgraded to hardy thru the update manager. ive tried all of these walkthrus and have absolutely no problem installing, or running ndiswrapper, or installing the driver. ndiswrapper just isnt recognizing my card as being installed (hardware not present) it did the same thing in gutsy.

---

### Post by adderx99 on 2008-05-15
> **SurferGTO said:**
> Thanks all for the replys. The isntall disc i have is for Gutsy, I upgraded to hardy thru the update manager. ive tried all of these walkthrus and have absolutely no problem installing, or running ndiswrapper, or installing the driver. ndiswrapper just isnt recognizing my card as being installed (hardware not present) it did the same thing in gutsy.

hi,
thanks to Ayuthia for linking my website guide.
i looked at the gateway drivers page for your laptop under MX3417 network drivers:
_[http://support.gateway.com/support/drivers/...]("http://support.gateway.com/support/drivers/search.asp?ref=std&st=browse&platform=10022&model=10944&os=&type=&mfg=&bios=")_
there seems to be 3 different manufactures listed, one for _[Intel]("http://support.gateway.com/support/drivers/getFile.asp?id=21082&dscr=Wireless%20Network%20Driver%20version:%20Intel%2010.6.0.46"),_ _[Broadcom]("http://support.gateway.com/support/drivers/getFile.asp?id=20988&dscr=Windows%20Vista%20(32-bit%20or%2064-bit)%20Broadcom%20Wireless%20Network%20Driver%20version:%204.102.15.61"),_ and one for _[NForce]("http://support.gateway.com/support/drivers/getFile.asp?id=20795&dscr=nVidia%20Nforce%20Network%20Driver%20version%2050.2.7")._
Make sure you're getting the proper driver.  Im not sure how it is on your laptop, but if you turn it over see an FCC listing and a label 'RF Listing' and one of those brands listed, then that is probably the proper card.
Then follow the instructions to load the driver via ndwiswrapper.  
youll need to extract the files from the exe, and copy them to an easy to remember directory.
interestingly enough, on my Gateway MX3422, i had to use the manufacturer's Win XP driver.  The Vista driver from gateway didnt work for me. 
do you know the exact make and model # of the card?
good luck.
-alex

---

