---
title: "Can not Connect to Internet"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by 1492 on 2010-09-05
[FONT=Arial]I just downloaded Ubuntu and have been unable to connect to the internet.  I have a dual -boot Windows 7 / Ubuntu, and the wireless internet connection works just fine on Windows 7.  I went to the wireless troubleshooter.  I decided to try using Windows wireless drivers, so I went to the Microsoft webpage (was that where I was supposed to get them?) and downloaded something that I hope was the drivers I needed, but I have no idea how to get **ndisgtk **(I assume the it must be downloaded off the internet). (Sorry for rambling on so much).

I can only connect to the internet via a wireless connection, but I can still use the internet from Windows 7 on that computer and XP on another computer.

Wireless setup guide:
[https://help.ubuntu.com/8.04/interne...onnecting.html]("https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html")

trouble shooter:
[https://help.ubuntu.com/8.04/interne...eshooting.html]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html")

This has nothing to do with my problem with the internet, but is there an Ubuntu Linux equivalent of Windows Task Manager?


*Edit:*
I just need to get the Windows XP wireless drivers for the [/FONT]ndiswrapper now.  Any ideas on how to get those?

---

### Post by sandyd on 2010-09-05
> **1492 said:**
> [FONT=Arial]I just downloaded Ubuntu and have been unable to connect to the internet.  I have a dual -boot Windows 7 / Ubuntu, and the wireless internet connection works just fine on Windows 7.  I went to the wireless troubleshooter.  I decided to try using Windows wireless drivers, so I went to the Microsoft webpage (was that where I was supposed to get them?) and downloaded something that I hope was the drivers I needed, but I have no idea how to get **ndisgtk **(I assume the it must be downloaded off the internet). (Sorry for rambling on so much).

I can only connect to the internet via a wireless connection, but I can still use the internet from Windows 7 on that computer and XP on another computer.

Wireless setup guide:
[https://help.ubuntu.com/8.04/interne...onnecting.html]("https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html")

trouble shooter:
[https://help.ubuntu.com/8.04/interne...eshooting.html]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html")

This has nothing to do with my problem with the internet, but is there an Ubuntu Linux equivalent of Windows Task Manager?
[/FONT]
post the output of
```

lspci
```

and please post it in between the [code] tags please.

---

### Post by 1492 on 2010-09-06
Here it is:  [code] tags?

00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11) 
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) 
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11) 
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11) 
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11) 
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11) 
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11) 
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) 
02:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650] 
02:00.1 Audio device: ATI Technologies Inc RV710/730 
08:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 35) 
14:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01) 
14:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01) 
14:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01) 
20:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04) 
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04) 
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04) 
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04) 
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04) 
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04) 
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04) 
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04) 
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04) 
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04) 
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04) 
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04) 
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04) 00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11) 
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) 
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11) 
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11) 
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11) 
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11) 
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11) 
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) 
02:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650] 
02:00.1 Audio device: ATI Technologies Inc RV710/730 
08:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 35) 
14:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01) 
14:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01) 
14:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01) 
20:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04) 
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04) 
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04) 
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04) 
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04) 
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04) 
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04) 
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04) 
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04) 
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04) 
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04) 
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04) 
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

---

### Post by Isaacgallegos on 2010-09-06
Task manager: 
use $ top
press h for help, once you're in to see how to use it. 

or 
use $ pstree
if it's too long a list use $ pstree | less
You can run searches once inside less with / and ? key. 
For more info on pstree use $ info pstree

edit:
I totally for got about
System>Administration>System Monitor
I never use it because I like the terminal.

---

### Post by 1492 on 2010-09-06
Okay, thanks.

---

### Post by anewguy on 2010-09-06
While not the preferred way, using the Windows drivers is still a viable option.  No, you don't need any connection to the net for it.  Just do the following:

- while booted in Ubuntu, load the LiveCD - if a message comes up about a software disk being found just cancel it

- open the file explorer to the LiveCD via "Places"

- navigate to the /pool/main/n folder.  You will find 2 folders here - ndisgtk and ndiswrapper.  Please note that ndisgtk is just a GUI'd front end to ndiswrapper, and there is a specific sequence in which these packages must be installed.

- navigate to the ndiswrapper folder

- double-click on the ndiswrapper-common file to begin it's installation. Wait for this to finish.

- double-click on the ndiswrapper-utilities file to begin it's installation.  Wait for this to finish.

- now navigate back 1 folder to /pool/main/n, then to the ndisgtk folder

- double-click on the ndisgtk file to begin it's installation.  Wait for it to finish.

- load the Windows driver .sys and .inf files to your desktop

- open ndisgtk via System/Administration/Windows Wireless Drivers

- do add (or new, whatever the option is), and point it to the .inf file for your Windows driver on your desktop.

Now right-click on the network manager icon in the top bar.  Be sure "Enable Wireless" is checked.  Close that, then just left-click on the network manager icon and see if you can see wireless networks.

If you use any type of encryption, etc., on the router, you will need to set this up in your connection as well.

Dave

---

### Post by sandyd on 2010-09-06
No need to use ndisgtk
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451)
^^

make sure you have Lucid proposed enabled.
then run
```

sudo apt-get install linux-backports-modules-2.6.32
```

---

### Post by coffeecat on 2010-09-06
Your wireless adapter is...

> **1492 said:**
> 08:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 35) 

You shouldn't need ndiswrapper. Forget about ndiswrapper for now. The driver and firmware should come in a default installation - Intel wireless chipsets should just work.

Look at top right of screen - on the panel. Click on the Network Manager icon. Are wireless networks showing? Thereafter it's as easy as Windows and easier than Windows XP.

**Edit:** Whoops! Just seen Carlee's posts about the bug affecting this wireless chipset. Discount what I said.

---

### Post by coffeecat on 2010-09-06
Edit: sorry - posted in error

---

### Post by 1492 on 2010-09-06
"live CD" ? I can't find it. Is that actually a cd, because I can't find it on the computer.

Also the network manager icon disappeared.

---

### Post by Isaacgallegos on 2010-09-06
It's what disk you used to install ubuntu.

---

### Post by anewguy on 2010-09-06
> **carlee said:**
> No need to use ndisgtk
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451)
^^

make sure you have Lucid proposed enabled.
then run
```

sudo apt-get install linux-backports-modules-2.6.32
```


Carlee - first off, not arguing here, instead trying to learn if there is a way to do this off-line from Ubuntu.  Why?  Note in the opening post the OP said their only internet access is wireless, and they can't get the wireless working in Ubuntu.  So, I'm curious if there is a way for the OP to do the equivalent of what you are saying via Windows and then copy what is needed over to Ubuntu for installation.

Again, not arguing!! (I'm sometimes misinterpreted that way) ;)

Dave

---

### Post by sandyd on 2010-09-06
> **anewguy said:**
> Carlee - first off, not arguing here, instead trying to learn if there is a way to do this off-line from Ubuntu.  Why?  Note in the opening post the OP said their only internet access is wireless, and they can't get the wireless working in Ubuntu.  So, I'm curious if there is a way for the OP to do the equivalent of what you are saying via Windows and then copy what is needed over to Ubuntu for installation.

Again, not arguing!! (I'm sometimes misinterpreted that way) ;)

Dave
ooh. thanks for reminding me...


OP, can you post the output of
```

uname -a
```Ive got everything for you here, in one HUGE package that you can download at once.

I just don't know if your using amd64, pae, or 32bit

or you could just pleaseeeeeeee go somewhere with wired internet? downloading this will take less than 5 min (you don't need to be connected to the net while installing)

Download Drivers (and propper kernel)
32bit - [http://dl.dolphinaura.com/cache/linux_modules_pkg/32bit.zip](http://dl.dolphinaura.com/cache/linux_modules_pkg/32bit.zip)
64bit - [http://dl.dolphinaura.com/cache/linux_modules_pkg/amd64.zip](http://dl.dolphinaura.com/cache/linux_modules_pkg/amd64.zip)
32bit-pae [http://dl.dolphinaura.com/cache/linux_modules_pkg/pae.zip](http://dl.dolphinaura.com/cache/linux_modules_pkg/pae.zip)

---

### Post by anewguy on 2010-09-07
Or, continue with ndiswrapper/ndisgtk to get it working, then do Carlee's instructions to really "fix" it. After that, just remove ndiswrapper and ndisgtk.

Dave ;)

---

### Post by sandyd on 2010-09-07
> **anewguy said:**
> Or, continue with ndiswrapper/ndisgtk to get it working, then do Carlee's instructions to really "fix" it. After that, just remove ndiswrapper and ndisgtk.

Dave ;)
you know, the funny thing is, ive never used ndiswrapper so I don't trust it lol ):P

---

### Post by anewguy on 2010-09-08
> **carlee said:**
> you know, the funny thing is, ive never used ndiswrapper so I don't trust it lol ):P

I was forced in the past to use it, and again with the adapter I currently use in my desktop (WG311v3).  I personally have never had a problem with it.  I know some people seem to think they need to get the source and compile it, due to some old posts on the net and in the history on the forum.  Some also try to use just ndiswrapper, which requires more entries at the command line to get everything set up, and also to blacklist existing dummy drivers that step on the "good" driver.  I've done that in the past myself many times, but due to more typing at the command line it also obviously can mean more chance for error.  Ndisgtk is just a GUI'd front end to ndiswrapper, and takes care of just about everything.  All of this is also easy to reverse - use ndisgtk to remove the device/driver, then use the package manager to remove all of ndiswrapper and ndisgtk.

I am also very much in favor of using restricted or other native drivers when ever that is possible.  Sometimes, as I suspect might be the case here, it's quickest just to use ndiswrapper to get online, then do everything needed to get the native driver, then remove ndiswrapper.  Sometimes it just seems quicker and the steps are fairly simple.

I understand your hesitation too - there have been many horror stories involving ndiswrapper, but almost every one of those I saw were either caused by trying to compile ndiswrapper from source, from not blacklisting drivers that step on the driver being installed, or from entering an incorrect driver name - it will show a device, but it won't work.  That's simple to correct however - just remove the device and add in the correct device (2 lines at the command line or 2 cycles through ndisgtk).  There are some incidences where ndiswrapper doesn't work and of course some where problems are caused.  I know for every instance I have had someone use it it has seemed to work.  There are exceptions when the device has some type of on/off "button" or key sequence, but I think that is common no matter what the driver is that is used.

That all being said, I much prefer using native or restricted drivers whenever possible - it just makes the most sense.  Sometimes ndiswrapper can be used as an easy stepping stone to get those.

All the best -

dave ;)

---

### Post by 1492 on 2010-09-08
By the way I did not install Ubuntu using a cd.  I just downloaded it, and when I restarted the computer, the dual-boot menu came up.

I put in
sudo apt-get install linux-backports-modules-2.6.32
it came up with:

"E: Invalid operation intall"


When I put in "name -a"

It came up with

Kinux ubuntu 2.6.32 -24 - generic #39-Ubuntu SMP Wed Jul 28 05 : 14 : 15 UTC 2010 x86_6 4 GNU/Linux

---

### Post by sandyd on 2010-09-08
> **1492 said:**
> By the way I did not install Ubuntu using a cd.  I just downloaded it, and when I restarted the computer, the dual-boot menu came up.
wait. what?

you mean you didn't burn the ISO to a cd, or mount the CD in windows?

---

### Post by 1492 on 2010-09-08
I don't know what you mean by 'mount a cd in windows' 
I just pressed the download button.  I actually thought I was putting it on a flash drive.

---

### Post by 1492 on 2010-09-08
Also, (and realize, I have no idea what I'm doing) it shows only about 180 mb on my hard drive when I'm running Ubuntu.  The hard drive has about 200GB. What did I do?

---

### Post by sandyd on 2010-09-08
> **1492 said:**
> Also, (and realize, I have no idea what I'm doing) it shows only about 180 mb on my hard drive when I'm running Ubuntu.  The hard drive has about 200GB. What did I do?
umm... stop.
we will have to fix that first.

go into windows -> control panel -> programs and features.
Anywhere on that list, do you see the words "ubuntu" or "wubi"?

---

### Post by 1492 on 2010-09-08
programs and features?
I can't find it

---

### Post by sandyd on 2010-09-08
> **1492 said:**
> programs and features?
that is what its called in windows 7...

ok. whatever stands for Add/Remove programs in your control panel I mean.

---

### Post by 1492 on 2010-09-08
Oh, sorry, I was using the computer running XP.

---

### Post by 1492 on 2010-09-08
I do not see Ubuntu or Wubi

---

### Post by 1492 on 2010-09-08
Oh, duh. I'm using the computer using XP... without Ubuntu

---

### Post by 1492 on 2010-09-08
Sorry, that was dumb


Okay, found it. What do I do now?

I found Ubuntu, but a message came up telling me Wubi might not have uninstalled correctly. I never uninstalled it.

---

### Post by 1492 on 2010-09-08
What should I do to change it?

---

### Post by sandyd on 2010-09-08
> **1492 said:**
> Sorry, that was dumb


Okay, found it. What do I do now?

I found Ubuntu, but a message came up telling me Wubi might not have uninstalled correctly. I never uninstalled it.
ok. It ooks like you have wubi (ubuntu) half installed.
Can you try removing it?

---

### Post by anewguy on 2010-09-08
Wubi, running Ubuntu "inside" Windows as opposed to dual-booting, is a different animal.  That can explain some of your problems.  I would follow sandyd's instructions and delete wubi first.  From there, I STRONGLY recommend you go to the ubuntu download page and download the 10.04 desktop ISO image.  After it finishes, burn that image to a CD (note: you don't just copy it to a CD, there will be an option in your CD burning software to burn from an image file).  The result will be what we call a LiveCD - a CD you can boot Ubuntu from without changing anything on your computer.  This allows you to "test drive" it a little.  When you decide you want to install it, I would recommend what they call "dual booting" - this essentially lets Windows and Ubuntu exist on your hard drive and gives you a menu at boot time so you can decide which OS you want to run.  There are a LOT of instructions here for doing so, but if you are nervous or unsure, just post back and we'll help you.  Remember we've all been there, so we know you can be confused, nervous and a little ticked off all at the same time, but hang in there - we are here to help you!

To recap:

- delete wubi.  If you don't know how, post back here and someone can help you with that (I've never used wubi so I can't help you there).

- download the ISO image of the 10.04 desktop CD from the Ubuntu download site

- using your burning software, look for the option to burn an image file to a CD and use it to burn the downloaded image to a CD.  If you need help with this just post back.

- boot that CD and try out Ubuntu a little.  It will run slower since it is running from memory and the CD.

- if you like what you've tried, or just plain want to install Ubuntu, use the CD you burned to install as a "dual boot".  If you need ANY help or have ANY questions about this, just post back.  At this particular step things really are easy, but we also want to be sure you understand before you start.


Also - if you don't want to use a CD but want to use a USB flash drive, try using unetbootln to create the flash drive.  It is available for both Windows and Linux.

Just my 2 cents worth......


dave ;)

---

### Post by 1492 on 2010-09-09
> **sandyd said:**
> ok. It ooks like you have wubi (ubuntu) half installed.
Can you try removing it?

I never knew that I installed it, but alright.

Also, anewguy, read this post from the beginning of this thread:

> [FONT=Arial]I just downloaded Ubuntu and have been unable to connect to the internet        [COLOR=Red]  I have a dual -boot Windows 7 / Ubuntu,[/COLOR] and the wireless internet connection works just fine on Windows 7.  I went to the wireless troubleshooter.  I decided to try using Windows wireless drivers, so I went to the Microsoft webpage (was that where I was supposed to get them?) and downloaded something that I hope was the drivers I needed, but I have no idea how to get **ndisgtk **(I assume the it must be downloaded off the internet). (Sorry for rambling on so much).[/FONT]

---

### Post by sandyd on 2010-09-09
> **1492 said:**
> I never knew that I installed it, but alright.

Also, anewguy, read this post from the beginning of this thread:
here : -> [http://ubuntuforums.org/showpost.php?p=9823807&postcount=12](http://ubuntuforums.org/showpost.php?p=9823807&postcount=12)

and now, burn the ubuntu iso onto a cd.

---

### Post by 1492 on 2010-09-09
Thanks you.  Also, I only have 180 mb available when I use Ubuntu. I have a 200gb hard drive.  How do I fix that?

---

### Post by sandyd on 2010-09-09
> **1492 said:**
> Thanks you.  Also, I only have 180 mb available when I use Ubuntu. I have a 200gb hard drive.  How do I fix that?
yeah, I know, uninstall wubi, burn the cd, then install it right right way.

---

### Post by 1492 on 2010-09-09
I *have *Ubuntu installed.  It is a dual-boot.  When I turn on the computer I choose either Ubuntu or Windows 7.  And actually, I apparently have a 320 Gb hard drive, and about 150Gb free, so nevermind about that (I have no idea how that much space is used, but that's not really important to me right now). I am not using Wubi.

---

### Post by sandyd on 2010-09-09
> **1492 said:**
> I *have *Ubuntu installed.  It is a dual-boot.  When I turn on the computer I choose either Ubuntu or Windows 7.  And actually, I apparently have a 320 Gb hard drive, and about 150Gb free, so nevermind about that (I have no idea how that much space is used, but that's not really important to me right now). I am not using Wubi.
post screenshot of  Control Panel -> Administrative Tools ->Computer Management -> Disk Management

you might have to change it to icon view before you can see the icon

---

### Post by 1492 on 2010-09-09
Where do I get the ".inf" & ".sys" files (for the XP drivers)?
l

---

### Post by 1492 on 2010-09-10
Where do I get the files I need to use with ndistkg.

---

### Post by 1492 on 2010-09-12
[http://ubuntuforums.org/attachment.php?attachmentid=169277&stc=1&d=1284314740](http://ubuntuforums.org/attachment.php?attachmentid=169277&stc=1&d=1284314740)

---

### Post by Kixtosh on 2010-09-12
Sorry ... my mistake!

---

### Post by corrytonapple on 2010-09-12
> **1492 said:**
> I *have *Ubuntu installed.  It is a dual-boot.  When I turn on the computer I choose either Ubuntu or Windows 7.  And actually, I apparently have a 320 Gb hard drive, and about 150Gb free, so nevermind about that (I have no idea how that much space is used, but that's not really important to me right now). I am not using Wubi.
So you somehow went through the installer on the CD or USB drive and you installed Ubuntu? That is the only way to get that menu that you see. It is called GRUB. If you don't know where all that space went, then post a screen-shot of Disk Utility. Get to it by going to at the top of the screen, **System>Administration>Disk Utility. **When it is open, go to your Hard disk at the side in the panel. Click it and then post a screens hot of what you see. To do so, go to the top of the screen, and then to **Applications>Accessories>Take Screen-Shot.** When you do, make sure you get in your Disk Utility window. See my screen-shot.

---

### Post by 1492 on 2010-09-12
I did not install Ubuntu using a CD or USB drive. I just downloaded it on my computer.

---

### Post by 1492 on 2010-09-12
The computer came with about 200gb free.  That doesn't really matter. I just want to connect to the internet on Ubuntu, and change it to allow me to use more than 185MB of disk space on Ubuntu.
If someone can just tell me how to make the computer allow me to use more than 185MB on Ubuntu and how to get the XP wireless drivers, thats all I need.

---

### Post by 1492 on 2010-09-12
How do I change the amount of disk space that Ubuntu can use or whatever you call it?

---

