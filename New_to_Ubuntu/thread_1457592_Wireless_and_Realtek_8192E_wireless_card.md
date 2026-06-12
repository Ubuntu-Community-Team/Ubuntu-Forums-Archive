---
title: "Wireless and Realtek 8192E wireless card?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by SarahCasey on 2010-04-18
Alright, so I installed ubuntu onto my laptop and everything is good...except I can't connect to the internet. We have another computer at my house with linksys and I used to be able to connect to it with my laptop when it was running on windows vista. Now though, when i look for connection it says its enabled, but there are absolutely no wireless connections showing up. And I know there were a lot of different ones to choose from before.
Please help :( i love ubuntu so far and i just want to fix this problem
 
also, i am really not very computer savvy, so any advice needs to be really dumbed down for me to understand it
 
sarahcasey

---

### Post by nhasian on 2010-04-18
can you make sure that your wifi adaptor's hardware switch is ON?  sometimes its on the front or side of the notebook a physical on/off switch.  sometimes its a combination of function buttons like Fn +F8 or something like that.  once you are sure its on, then check to see if you can see the wifi networks.  if you cannot, open a up a terminal from applications -> accessories -> terminal then enter this command:

```
lshw -C network
```

please give us the output of that command so we can begin troubleshooting for you.

---

### Post by Running_Dualboot on 2010-04-18
[QUOTE=SarahCasey]Hey, i was reading your question and i'm having the same problem as you are, but nobody is responding to my question lol. How did you get your computer to work? I tried the get-update etc. thing but it didn't do anything at all. any advice? thanks
 
sarahcasey[/QUOTE]


I'm not sure what else you could do other than get connected to an Ethernet cable (You have to have a connection to get the updates) and say:

```
sudo apt-get update
sudo apt-get update
sudo reboot
```

Then go to your driver list and it should be there, if not please go to terminal and type:

```
lspci
lsusb 
```

then post what comes up with a screen shot

---

### Post by SarahCasey on 2010-04-18
> **nhasian said:**
> can you make sure that your wifi adaptor's hardware switch is ON?  sometimes its on the front or side of the notebook a physical on/off switch.  sometimes its a combination of function buttons like Fn +F8 or something like that.  once you are sure its on, then check to see if you can see the wifi networks.  if you cannot, open a up a terminal from applications -> accessories -> terminal then enter this command:

```
lshw -C network
```please give us the output of that command so we can begin troubleshooting for you.


  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:c800(size=256) memory:fdffc000-fdffffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:73:8d:71
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.124 latency=0 multicast=yes
       resources: irq:30 ioport:e800(size=256) memory:fcfff000-fcffffff(prefetchable) memory:fcfe0000-fcfeffff(prefetchable) memory:febe0000-febfffff(prefetchable)

okay....this is what i got

---

### Post by SarahCasey on 2010-04-18
I'm running Ubuntu 9.10...or whatever the most recent one is. i just downloaded it this morning and i'm pretty sure that's what its called...

I have a Toshiba Satellite M505 laptop
My wireless card is a RealTek 8192E

My problem is, is that I can not get wifi connection, though i know it works because i have another computer in my house running off of it. Right now, i'm using my laptop, but i have the ethernet cable plugged in it so that i can get internet, but that's the only way i can get online with it.

I looked on another forum post and i was able to find a link to supposedly work in installing a driver for this kind of wireless card, but the link didn't work. What do i do? This is really frustrating and i just want to get my internet working! Thanks for any help. 

:icon_frown:

---

### Post by dearingj on 2010-04-18
> **Running_Dualboot said:**
> I'm not sure what else you could do other than get connected to an Ethernet cable (You have to have a connection to get the updates) and say:

```
sudo apt-get update
sudo apt-get up**grade**
sudo reboot
```


Fixed that for ya :)

---

### Post by SarahCasey on 2010-04-18
I already did an upgrade update thing and it didnt' change anything. When i look into my hardware drivers it says that there is nothing found :/ so i don't know what that means

---

### Post by 2hot6ft2 on 2010-04-18
**[EDIT: For anyone with the [COLOR="Navy"]RTL8192E[/COLOR] card (that's E not SE, 32 bit) the solution is on page 5 of this thread posts 43 and 44 here]("http://ubuntuforums.org/showthread.php?t=1457592&page=5")**

[**For those that need the 64 bit driver you can find it in the quote at the bottom of this post #44**]("http://ubuntuforums.org/showpost.php?p=9146770&postcount=44")

It would be more help to know what wifi adapter you have.
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

### Post by SarahCasey on 2010-04-18
lspci -

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
02:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by SarahCasey on 2010-04-18
lsusb-

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by trig on 2010-04-18
do you have ehtho or wireless

---

### Post by 2hot6ft2 on 2010-04-18
> **SarahCasey said:**
> lspci -
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

Looks like you have a Realtek 8192 adapter and in this thread it looks at first glance like the windows driver was needed with Windows Wireless Driver (ndisgtk)
[Realtek rtl8192e wireless not seen]("http://ubuntuforums.org/showthread.php?t=1239342")
I'll try and find the driver. You can install ndisgtk like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ndisgtk
```
Then it will be in
System > Administration > Windows Wireless Driver

> **SarahCasey said:**
> lsusb-
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 

I wouldn't be at all surprised if you have trouble with that too. It's a webcam right?

---

### Post by 2hot6ft2 on 2010-04-18
There are some new drivers here

[Realtek Drivers Page]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE")

But we need to find out exactly which driver you need as there is more than one version that is 8192.
There is the 8192SE, 8192E, 8192U and 8192SU.

So run
```
lspci -nn
```
and post the results.

There will be a line similar to this
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [**10ec:8192**] (rev 01)
The 8 characters separated by a colon will tell us which card you have.

---

### Post by anewguy on 2010-04-18
Did anyone notice that the OP's lshw -C network shows the adapter (RTL8101E/RTL8102E) and the driver (driver=r8169 driverversion=2.3LK-NAPI) is loaded?

I'm wondering if perhaps:

- perhaps the r8169 driver, apparently included in Ubuntu, is not the correct one for the RTL8101E/RTL8102E adapter.  Following the post from 2hot6ft2, if you use ndiswrapper to load the windows drivers, I suspect you may need to blacklist r8169.

I was thinking of having the OP check for roaming mode enable, wireless enabled in network manager, etc., but not sure it would make any difference since the lshw is showing the adapter as unclaimed (kind of hard from what I know to do an iwlist xxxx scanning when the adapter is unclaimed so you don't have ethx or wlanx or whatever to put in the iwlist command).

Dave ;)

---

### Post by nhasian on 2010-04-18
SarahCasey,

this is your wifi adaptor:

> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

you can install the windows driver using ndiswrapper or you can use the new Ubuntu 10.04 Lucid Lynx has the driver built in.  The release candidate comes out this thursday but you can grab the latest liveCD from here to test it:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by 2hot6ft2 on 2010-04-19
> **anewguy said:**
> Did anyone notice that the OP's lshw -C network shows the adapter (RTL8101E/RTL8102E) and the driver (driver=r8169 driverversion=2.3LK-NAPI) is loaded?

I'm wondering if perhaps:

- perhaps the r8169 driver, apparently included in Ubuntu, is not the correct one for the RTL8101E/RTL8102E adapter.  Following the post from 2hot6ft2, if you use ndiswrapper to load the windows drivers, I suspect you may need to blacklist r8169.

I was thinking of having the OP check for roaming mode enable, wireless enabled in network manager, etc., but not sure it would make any difference since the lshw is showing the adapter as unclaimed (kind of hard from what I know to do an iwlist xxxx scanning when the adapter is unclaimed so you don't have ethx or wlanx or whatever to put in the iwlist command).

Dave ;)
Yes I did notice that. I also noticed that it appears to be the driver for the Ethernet adapter, not the wireless adapter which is what doesn't work. And now that we know that there is a linux driver for the 8192 the OP wont need ndiswrapper once we find out which of the (4) 8192 cards she has. Unless of course the driver doesn't work very good.

Wireless adapter on top and Ethernet on bottom.
Ethernet has an IP Address. The Ethernet adapter is using the r8169 driver so blacklisting it would disable the wired connection.
Am I missing something?
> **SarahCasey said:**
> ```
***-network UNCLAIMED**     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       **bus info: pci@0000:03:00.0**
       **version: 01**
       **width: 32 bits**
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: **ioport:c800**(size=256) **memory:fdffc000-fdffffff**
 ** *-network**
       description: [B]Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/B]
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       **bus info: pci@0000:07:00.0**
       [B]logical name: eth0
       version: 02[/B]
       serial: 00:26:18:73:8d:71
       **width: 64 bits**
       clock: 33MHz
       capabilities: bus_master cap_list rom [B][SIZE="4"][COLOR="Red"]ethernet physical
       configuration: broadcast=yes driver=r8169[/COLOR][/SIZE][/B] driverversion=2.3LK-NAPI **ip=192.168.1.124** latency=0 multicast=yes
       resources: irq:30 **ioport:e800**(size=256) **memory:fcfff000-fcffffff**(prefetchable) memory:fcfe0000-fcfeffff(prefetchable) **memory:febe0000-febfffff**(prefetchable)

```
okay....this is what i got> **SarahCasey said:**
> lspci -
**03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)**
**07:00.0 Ethernet controller:** Realtek Semiconductor Co., Ltd. **RTL8101E/RTL8102E PCI Express Fast Ethernet controller** **(rev 02)**
I'll check in on this again in the morning I'm off to bed now.

---

### Post by anewguy on 2010-04-19
> **2hot6ft2 said:**
> Yes I did notice that. I also noticed that it appears to be the driver for the Ethernet adapter, not the wireless adapter which is what doesn't work. And now that we know that there is a linux driver for the 8192 the OP wont need ndiswrapper once we find out which of the (4) 8192 cards she has. Unless of course the driver doesn't work very good.

Wireless adapter on top and Ethernet on bottom.
Ethernet has an IP Address. The Ethernet adapter is using the r8169 driver so blacklisting it would disable the wired connection.
Am I missing something?

I'll check in on this again in the morning I'm off to bed now.

No, you got it right!  I missed the break where the regular network controller came in - I guess I was up too late to be posting anything.

Sorry for the erroneous post, and glad you caught it!

Thanks!
Dave ;)

---

### Post by 2hot6ft2 on 2010-04-19
> **anewguy said:**
> No, you got it right!  I missed the break where the regular network controller came in - I guess I was up too late to be posting anything.

Sorry for the erroneous post, and glad you caught it!

No problem. I do that sometimes too, and glad that you agree with the assessment as it is. Now if the OP will post the lspci -nn so we can get the right driver and wrap it up.:)

---

### Post by SarahCasey on 2010-04-19
wow, really thanks for all the help on this, i wasn't expecting so much. i'm gonna try reading through all that slowly and figuring it out...im having a bit of trouble but thank you guys so much for helping me

---

### Post by SarahCasey on 2010-04-19
here is what happened when i put in lspci -nn

sarahcasey@SarahCasey-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
02:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
02:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
02:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

---

### Post by anewguy on 2010-04-19
> **2hot6ft2 said:**
> No problem. I do that sometimes too, and glad that you agree with the assessment as it is. Now if the OP will post the lspci -nn so we can get the right driver and wrap it up.:)

Noticed searching the net on the USB manufacturer and Product Id's that there have been some problems using the windows drivers with ndiswrapper for this device.  For my own education, is there some sort of "native" driver for this device (doesn't have to have been included in Ubuntu, just something that is native Linux and not using ndiswrapper)?  Perhaps this is one of those "download the firmware and put it in the proper folder, like r8169?

I'll be watching to see how this goes.

Again, sorry for my late night error and sure hope it didn't throw things off track!  I'm usually a little better than that!

Dave ;)

---

### Post by Running_Dualboot on 2010-04-19
> **trig said:**
> do you have ehtho or wireless


Ubuntu can easily connect to any etho, also if you read what she saud, she need help with wireless.

---

### Post by 2hot6ft2 on 2010-04-19
> **SarahCasey said:**
> 
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [**10ec:8192**] (rev 01)

Ok. You have the RTL8192E adapter so you're going to have to use the windows driver since I don't see a linux driver for that one here:
[RTL8192E Driver Page]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E")

So head on over there and get the one at the very bottom for
(support Win2K/WinXP/Vista), Win2K/WinXP/Vista driver ver.1677.1)
Since I think it will work better than the one for win 7.
You're going to need to install ndisgtk like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ndisgtk
```
Then it will be in
System > Administration > Windows Wireless Drivers

Once you download the driver to your home folder double click on it then
double click on RTL819xP_Driver
then WinXP
then select the net819xp.inf file
and click on Extract.

Then go to
System > Administration > Windows Wireless Drivers
Click on Install New Driver
Browse to the .inf file and select it.
Click on Open, then Install, then Close.
That should do it once you reboot without the wired connection you should have a working wireless driver which you can setup in network manager in the top right panel.

---

### Post by SarahCasey on 2010-04-19
k let me try all that, give me a few minutes. dont leave me! lol

---

### Post by 2hot6ft2 on 2010-04-19
> **anewguy said:**
> 
I'll be watching to see how this goes.

Again, sorry for my late night error and sure hope it didn't throw things off track!  I'm usually a little better than that!

You didn't throw it off track. But you did have me second guessing what I had read...:P

---

### Post by SarahCasey on 2010-04-19
Okay, problem. I did everything so far, but when i went to windows wireless drivers, there isn't anything there. So i clicked install but i don't know where the file is, like it's not giving me the option of where i might find it :((( so close

---

### Post by 2hot6ft2 on 2010-04-19
> **SarahCasey said:**
> k let me try all that, give me a few minutes. dont leave me! lol
No problem. And the reason I said to use the win xp driver is that the xp drivers are "usually" more stable. At least that's how I feel about them. If that one gives you problems you still have the rest in the zip file for vista you can try before trying the win 7 one.
Stick with the x86 ones unless you installed 64 bit ubuntu, which I should have asked now that I think of it.

---

### Post by 2hot6ft2 on 2010-04-19
> **SarahCasey said:**
> Okay, problem. I did everything so far, but when i went to windows wireless drivers, there isn't anything there. So i clicked install but i don't know where the file is, like it's not giving me the option of where i might find it :((( so close
It should be in the folder it opened to which is your Home Folder.
Just scroll down to it.
Where was the zip file when you opened it?
It should still be there.

---

### Post by Jon Monreal on 2010-04-19
You could give [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") a try to install the Windows drivers.

A search of these forums turns up [some success]("http://ubuntuforums.org/showthread.php?t=1191590") with ndiswrapper.

That first link contains a comprehensive guide. If you need further help, please feel free to ask.

---

### Post by 2hot6ft2 on 2010-04-19
If it was on the Desktop just move the .inf file to Places > Home folder
Then when you click on Install New Driver then on Location it will be right there in that folder.

---

### Post by SarahCasey on 2010-04-19
Well the first time i downloaded it, it just said open with "Archive Manager" so i just did that
I downloaded it again, but i saved it this time, and when i opened it when it finished loading all it says by Location is a slash like "/" 
when i went to install it i couldn't find it anywhere

---

### Post by SarahCasey on 2010-04-19
what the hell. I'm getting frustrated lol. 
So, i went to Wireless Network Drivers. Nothing there, so i clicked Install. Found the 819xP Windows Driver folder, so i clicked on it to install it. And it says "Not a valid driver .inf file"

---

### Post by 2hot6ft2 on 2010-04-19
Go to
System > Administration > Windows Wireless Drivers
Click on Install New Driver
Then on Location
Select the .inf file
And click Open or Install
Then Close

No need to get flustrated. We'll get it.
Your home folder is the one with your username so if it's sarah then put it in the sarah folder.

EDITED: Removed the driver since it doesn't work and removed the reference to it.

---

### Post by SarahCasey on 2010-04-19
Okay, i'm really sorry i read it wrong the first time but I followed your first instructions exactly just now, extracted the file and found the .inf
I tried to install it and it said invalid driver but i'm sure i picked the right one

I'll try the second set of instructions though. wow i'm really sorry im so bad at this. thank you so much for helping me

---

### Post by aust77 on 2010-04-19
the directory "/" is your generic linux file system.

head to Places-Computer then click on File System. then you be in the "/" dir.

---

### Post by 2hot6ft2 on 2010-04-19
> **SarahCasey said:**
> Okay, i'm really sorry i read it wrong the first time but I followed your first instructions exactly just now, extracted the file and found the .inf
I tried to install it and it said invalid driver but i'm sure i picked the right one

I'll try the second set of instructions though. wow i'm really sorry im so bad at this. thank you so much for helping me
You're welcome and you'll get the hang of it. Having to use a windows driver is a heck of a thing to have to deal with as a new user.

---

### Post by SarahCasey on 2010-04-19
> **2hot6ft2 said:**
> Ok. I'm going to attach the driver to this at the bottom.
Click on it and save it to your home folder.
That's Places > Home folder
Once it downloads go there
Right click on it and select rename.
Remove the .zip from the end so you're left with
net819xp.inf
Then go to
System > Administration > Windows Wireless Drivers
Click on Install New Driver
Then on Location
Select the .inf file
And click Open or Install
Then Close

No need to get flustrated. We'll get it.
Your home folder is the one with your username so if it's sarah then put it in the sarah folder.

Okay. Update. I definitely have the .inf file, and i got all the install new driver stuff figured out. When i installed it, it said "Invalid Driver" and it wouldn't let me change the name of the zip file because it already had the original in the file. I don't think thats a problem, because it just means that i had it right the first time and just wasn't looking in the right spot. Anyways, should I try rebooting anyways to see if it worked even though it said invalid driver?

---

### Post by 2hot6ft2 on 2010-04-19
If it doesn't like the xp driver delete it and open the zip file and extract the .inf file from the the VistaX86 folder and see if it likes that one better.

Did you install ubuntu x86 or ubuntu AMD64?

---

### Post by SarahCasey on 2010-04-19
> **2hot6ft2 said:**
> If it doesn't like the xp driver delete it and open the zip file and extract the .inf file from the the VistaX86 folder and see if it likes that one better.

Did you install ubuntu x86 or ubuntu AMD64?

nope it doesn't like that one either...and i don't know what ubuntu i installed. It's whatever one that i just went straight to ubuntu.com and clicked download. so its 9.10 32 bit. sorry i don't know more. I feel like i may be getting the hang of this now though

---

### Post by 2hot6ft2 on 2010-04-19
If you open a terminal and run
```
file /sbin/init
```
it will show if it's 32 bit or 64 bit
You may want to go back to where you got the driver from and get the windows 7 driver and give it a shot then.
Unless the zip file was corrupted it should take one of them.

---

### Post by SarahCasey on 2010-04-19
> **2hot6ft2 said:**
> If you open a terminal and run
```
file /sbin/init
```it will show if it's 32 bit or 64 bit
You may want to go back to where you got the driver from and get the windows 7 driver and give it a shot then.
Unless the zip file was corrupted it should take one of them.

Okay, thank you so much for the help and just giving this question some actual thought and attention. I extracted and tried all the other .inf files and none of them took, so tomorrow i'm gonna start working on the windows 7 driver. Thanks a lot for the help really. If i need help tomorrow i'll probably send you a message if you're on here. again, THANK YOU :P

oh, and its 32-bit

---

### Post by 2hot6ft2 on 2010-04-19
Ok, I just tried installing them too and I got the same invalid driver message so it's not just you or your download.
I'll be here as far as I know. Good night.

And you're welcome

---

### Post by 2hot6ft2 on 2010-04-19
Looks like there is a linux driver for it here:
[http://rs110.rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz](http://rs110.rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz)

Save it in your home folder and I'll post a quick how to for installing it.

---

### Post by 2hot6ft2 on 2010-04-19
I was going to give 2 ways to install it but I'll just give the normal way so you don't get overwhelmed.
Download and save the file to your home folder then go to
Places > Home folder
Right click on the
rtl8192e_linux_2.6.0011.1029.2009.tar.gz
package and select Extract here
Then open a terminal and use
```
cd rtl8192e_linux_2.6.0011.1029.2009
```
then
```
make
```
and
```
sudo make install
```

That's it
:guitar:

And it's reported that it works better than the windows driver and will work with WPA 2 Personal security.
WhoooHooo.

For future use after a kernel upgrade these are the instructions on re-installing the driver once you cd into the drivers folder with
```
cd linux_2.6.0011.1029.2009
```
> **chili555 said:**
> I suggest:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
reboot
```'make clean' removes any files created in your previous 'make' done against the old kernel. You are quite correct that the process needs to be re-run every time a new kernel, known in Ubuntu-speak as linux-image, is installed. The clue will be when your wireless conks out with no warning.
For those that need the 64 bit driver, here is a post with that driver
> **mcguire said:**
> Realtek (kidman) sends me today the driver v14 which works on 64 bits (tested on lucid).
On my Samsung R580 laptop, it disconnects often but it is usable. When it disconnects, sometimes, it can not reconnect automatically so I have to unload the module and reload it, then it works again for some time.

I've uploaded it to my personal server so that everybody can download it :
[http://ftp.jdsystem.info/rtl8192e_linux_2.6.0014.0401.2010.tar.gz](http://ftp.jdsystem.info/rtl8192e_linux_2.6.0014.0401.2010.tar.gz)

Hope this help

EDIT : I've also attached this driver to [bug 508746]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746") on Launchpad.

---

### Post by anewguy on 2010-04-19
2Hot6ft2:  i'll let you keep helping the user since they have a rappore with you now, but I thought I'd pass along a couple of things:

see this link:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")

Might give some guidance on getting away from the XP driver.

Also, I've seen indications that this driver:

rtl8192se_linux_2.6.0010.1116.2009

is the one to get, unpack, make and make install on to get the device working.

You may want to check both of these out.

dave ;)

---

### Post by 2hot6ft2 on 2010-04-19
> **anewguy said:**
> 2Hot6ft2:  i'll let you keep helping the user since they have a rappore with you now, but I thought I'd pass along a couple of things:

see this link:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")

Might give some guidance on getting away from the XP driver.

Also, I've seen indications that this driver:

rtl**8192se**_linux_2.6.0010.1116.2009

is the one to get, unpack, make and make install on to get the device working.

You may want to check both of these out.

dave ;)
That's for the 8192SE  NOT the 8192E but thanks I found the right one.
Yeah, both the bug report and the driver are for the SE. She has the E card.

And I think it's done now except for her downloading making and installing the linux driver.
I will go back and give the normal
make
make install
instructions so she knows how it is usually done.

---

### Post by Iowan on 2010-04-19
Merged threads as they appear to be the same issue.

---

### Post by anewguy on 2010-04-19
Sorry again!  I don't know what's going on with me the last couple of days but I sure seem to be good at getting myself confused at what I was looking for, and as a result make 2 stupid posts like I have in this thread!

Dave ;)

---

### Post by 2hot6ft2 on 2010-04-19
> **anewguy said:**
> I sure seem to be good at getting myself confused at what I was looking for
Don't get discouraged. At least you're trying and if they were actually the same then it would have been very good info. to have.
:lolflag:

---

### Post by MasterColdSoul on 2010-04-20
> **SarahCasey said:**
> Okay, thank you so much for the help and just giving this question some actual thought and attention. I extracted and tried all the other .inf files and none of them took, so tomorrow i'm gonna start working on the windows 7 driver. Thanks a lot for the help really. If i need help tomorrow i'll probably send you a message if you're on here. again, THANK YOU :P

oh, and its 32-bit

I have a laptop with a 8192E wireless. The wireless driver does not work in 64 bit in Linux from my understanding, so since your running 32 bit your fine there.

I don't know if the windows 7 driver will work, I wouldn't bet on it. 

If you have Ndiswrapper installed then your mostly there.

get this file 

[http://rapidshare.com/files/377918065/net819xp.inf.html](http://rapidshare.com/files/377918065/net819xp.inf.html)

that should be the file you need (our wireless cards share the same ID so they should be identical)

then once you have downloaded it find it with Ndiswrapper and after it's installed just restart and it should work fine.

Now I am no expert, but since I share the same wifi card hopefully this helps since I also have a working driver.

---

### Post by lotharmat on 2010-04-20
I have emailed realtek and they sent me the 64 bit driver

it is called rtl8192e_linux_2.6.0012.1210.2009 - I have had it working fine on Karmic.

If you need to get it send an email to Realtek [HERE]("http://www.realtek.com/contact/contentView.aspx?Langid=1&PNid=6&PFid=6&Level=1&Conn=1")

If enough people email them they should put the drivers on their website.

Or failing that I could try and email the drivers to anyone who needs them.

---

### Post by 2hot6ft2 on 2010-04-20
> **lotharmat said:**
> I have emailed realtek and they sent me the 64 bit driver

it is called rtl8192e_linux_2.6.0012.1210.2009 - I have had it working fine on Karmic.

If you need to get it send an email to Realtek [HERE]("http://www.realtek.com/contact/contentView.aspx?Langid=1&PNid=6&PFid=6&Level=1&Conn=1")

If enough people email them they should put the drivers on their website.

Or failing that I could try and email the drivers to anyone who needs them.
Thanks for adding that. I was about to go looking for the thread that had the info. for the 64 bit linux driver that I read about last night.

Found it anyway. Here's a post with a link to the 64 bit driver
> **mcguire said:**
> Realtek (kidman) sends me today the driver v14 which works on 64 bits (tested on lucid).
On my Samsung R580 laptop, it disconnects often but it is usable. When it disconnects, sometimes, it can not reconnect automatically so I have to unload the module and reload it, then it works again for some time.

I've uploaded it to my personal server so that everybody can download it :
[http://ftp.jdsystem.info/rtl8192e_linux_2.6.0014.0401.2010.tar.gz](http://ftp.jdsystem.info/rtl8192e_linux_2.6.0014.0401.2010.tar.gz)

Hope this help

EDIT : I've also attached this driver to [bug 508746]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746") on Launchpad.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> I was going to give 2 ways to install it but I'll just give the normal way so you don't get overwhelmed.
Download and save the file to your home folder then go to
Places > Home folder
Right click on the
linux_2.6.0011.1029.2009.tar.gz
package and select Extract here
Then open a terminal and use
```
cd linux_2.6.0011.1029.2009
```then
```
make
```and
```
sudo make install
```That's it
:guitar:

And it's reported that it works better than the windows driver and will work with WPA 2 Personal security.
WhoooHooo.

For future use after a kernel upgrade these are the instructions on re-installing the driver once you cd into the drivers folder with
```
cd linux_2.6.0011.1029.2009
```For those that need the 64 bit driver, here is a post with that driver

I did all that but this is all that happened when i entered the code

sarahcasey@SarahCasey-laptop:~$ cd linux_2.6.0011.1029.2009
bash: cd: linux_2.6.0011.1029.2009: No such file or directory
sarahcasey@SarahCasey-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
sarahcasey@SarahCasey-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
sarahcasey@SarahCasey-laptop:~$

---

### Post by anewguy on 2010-04-20
Did you do this first:

Download and save the file to your home folder then go to
Places > Home folder

Right click on the
linux_2.6.0011.1029.2009.tar.gz
package and select Extract here

These were in 2hot6ft2 before the start of the code boxes showing you what to type in the terminal.  The first step is pretty obvious - downloads the file.  The second step is needed to extract the files from the compressed file you downloaded, and it creates the directory for those files as well (the one that isn't found when you try to "cd" to it in the copy of the output you posted).


If you didn't do the download, you need to do that first.

If you did do the download, you need to extract the tar.gz file as noted.  This will unpack the files so that you can actually do the rest of what you were trying to do.

Dave ;)

---

### Post by SarahCasey on 2010-04-20
> **anewguy said:**
> Did you do this first:

Download and save the file to your home folder then go to
Places > Home folder

Right click on the
linux_2.6.0011.1029.2009.tar.gz
package and select Extract here

These were in 2hot6ft2 before the start of the code boxes showing you what to type in the terminal.  The first step is pretty obvious - downloads the file.  The second step is needed to extract the files from the compressed file you downloaded, and it creates the directory for those files as well (the one that isn't found when you try to "cd" to it in the copy of the output you posted).


If you didn't do the download, you need to do that first.

If you did do the download, you need to extract the tar.gz file as noted.  This will unpack the files so that you can actually do the rest of what you were trying to do.

Dave ;)

Yeah i downloaded it, and then i extracted it and that's what happened :/ 
I dont see how i could have messed it up, like i'm pretty sure i did everything right

---

### Post by anewguy on 2010-04-20
Okay, then maybe there's just a little typo somewhere else along the lines.  If you check your home folder, either by "Places" or by "ls" in the command line, does it show any new folder with a name similar to the "linux_2.6.0011.1029.2009" -> maybe you'll recognize something with a different yet similar name.

If you find one, post back so we can verify what it is.

In the mean time, I'll be busy for a few minutes - I'm going to do the download and see what folder the extract actually creates so I can verify it with you.

I'll be back shortly.....

Dave ;)

---

### Post by SarahCasey on 2010-04-20
> **anewguy said:**
> Okay, then maybe there's just a little typo somewhere else along the lines.  If you check your home folder, either by "Places" or by "ls" in the command line, does it show any new folder with a name similar to the "linux_2.6.0011.1029.2009" -> maybe you'll recognize something with a different yet similar name.

If you find one, post back so we can verify what it is.

In the mean time, I'll be busy for a few minutes - I'm going to do the download and see what folder the extract actually creates so I can verify it with you.

I'll be back shortly.....

Dave ;)

Kk, so I looked in my home folder, downloads, then i found rt8192e_linux_2.6.0011.1029.2009.tar.gz
after I extracted it, the new one says the same thing, just without the .tar.gz

---

### Post by anewguy on 2010-04-20
Okay, a couple of things to note:

- my download automatically went to my Downloads folder - I wasn't given a choice in where to save it, but everything relates the same.

- the actual downloaded tar.gz from link in the above post actually comes back as:

rtl8192e_linux_2.6.0014.0401.2010.tar.gz

- the folder that is created when you extract the files from the download is:

rtl8192e_linux_2.6.0014.0401.2010

So, you need to change your "cd" command (of course, relative to where it was extracted) to:

cd rtl8192e_linux_2.6.0014.0401.2010


Everything else should work the same after that.

Dave ;)

---

### Post by anewguy on 2010-04-20
Woops......guess you beat me to it and you actually have the foldername as it was mentioned in the instructions, instead of the one that downloaded for me (don't know why I got a different file when I just clicked on the link, oh well......)

At any rate, following 2hot6ft2's previous instructions, just change the "cd" command to "cd rt8192e_linux_2.6.0011.1029.2009".  From there everything should be the same.

Sorry for the confusion from my last post, but it really did download a different file for me.

Dave ;)

EDIT:  I see why mine was different - I clicked on the link for the 64-bit driver instead.  Sorry!

---

### Post by anewguy on 2010-04-20
Hopefully we're not crossing paths here again......I have to change the watering in the yard and change some laundry around, so I'll be gone for about 5 - 10 minutes.  I'll check back right away when I get back to the computer.

Dave ;)

---

### Post by SarahCasey on 2010-04-20
> **anewguy said:**
> Okay, a couple of things to note:

- my download automatically went to my Downloads folder - I wasn't given a choice in where to save it, but everything relates the same.

- the actual downloaded tar.gz from link in the above post actually comes back as:

rtl8192e_linux_2.6.0014.0401.2010.tar.gz

- the folder that is created when you extract the files from the download is:

rtl8192e_linux_2.6.0014.0401.2010

So, you need to change your "cd" command (of course, relative to where it was extracted) to:

cd rtl8192e_linux_2.6.0014.0401.2010


Everything else should work the same after that.

Dave ;)

It did the same thing :[

sarahcasey@SarahCasey-laptop:~$ cd rtl8192e_linux_2.6.0011.1029.2009
bash: cd: rtl8192e_linux_2.6.0011.1029.2009: No such file or directory
sarahcasey@SarahCasey-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
sarahcasey@SarahCasey-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
sarahcasey@SarahCasey-laptop:~$ 

I didn't put the exact same code as you put, because my file said something different. Is that a problem?

---

### Post by anewguy on 2010-04-20
Check the location of the downloaded file and the folder created when the files were extracted via "Places".  Is it by any chance in "Downloads"?

If so, do this first:

cd Downloads -> this would change your default from your home folder to your Downloads folder.

Then go ahead and try the cd, make, make install, etc., again.

Dave ;)

BTW - if it is different than "Downloads" (perhaps Desktop?) just change the word "Downloads" above to what ever the folder name is - remember everything is case sensitive.

---

### Post by SarahCasey on 2010-04-20
> **anewguy said:**
> Check the location of the downloaded file and the folder created when the files were extracted via "Places".  Is it by any chance in "Downloads"?

If so, do this first:

cd Downloads -> this would change your default from your home folder to your Downloads folder.

Then go ahead and try the cd, make, make install, etc., again.

Dave ;)

BTW - if it is different than "Downloads" (perhaps Desktop?) just change the word "Downloads" above to what ever the folder name is - remember everything is case sensitive.

Okay, it is in Downloads, but i don't understand where you want me to change the name? like in the code? like cd Downloads rtl8192....etc?

I have to go to the store, but i'll be back on here and i'll send you a message to see if you're here to help lol

---

### Post by anewguy on 2010-04-20
Quite understandable - I sometimes don't make things as clear as they should be :(. 

You can just copy and paste this line in to use in place of the "cd rtl8192e_linux_2.6.0011.1029.2009":

cd Downloads/rtl8192e_linux_2.6.0011.1029.2009

Hopefully that will get you there!

Dave ;)

---

### Post by 2hot6ft2 on 2010-04-20
> **anewguy said:**
> Quite understandable - I sometimes don't make things as clear as they should be :(. 

You can just copy and paste this line in to use in place of the "cd rtl8192e_linux_2.6.0011.1029.2009":

cd Downloads/rtl8192e_linux_2.6.0011.1029.2009

Hopefully that will get you there!

Dave ;)
Alrighty then...
If you downloaded it to the Downloads folder like it sounds like you have then yes just cd into it after extracting it like anewguy said
```
cd Downloads/rtl8192e_linux_2.6.0011.1029.2009
```

That was my mistake I said to use
> cd linux_2.6.0011.1029.2009
Somehow I managed to cut part of the name off of it, namely the first part (rtl8192e_):(

Then run
```
make
```
and ```
sudo make install
```

Thanks anewguy. I've been pounding the web looking for a solution to something else for hours.

---

### Post by SarahCasey on 2010-04-20
okay, i did it! the code went in without the same message coming up. Now do i need to restart my computer?

---

### Post by 2hot6ft2 on 2010-04-20
Here's a nautilus extension I guess you would call it that is one of the very first things I install because it's such a time saver. And I'll throw in my second favorite app. while I'm at it.
```
sudo apt-get install nautilus-open-terminal alien
```
You have to reboot or run
```
sudo killall nautilus
```
before the open terminal will be available as a right click option for any folder you're in as (Right click and select Open in Terminal). That way you can open the terminal in the folder you're in and not have to cd to it.

Alien is great for converting packages to installable .deb files so you could go to
Places > Downloads Right click and select Open in Terminal then run
```
sudo alien rtl8192e_linux_2.6.0011.1029.2009.tar.gz
```
And it will create a file named
rtl8192e_linux_2.6.0011.1029.2009.deb
in the same folder.
Which you can double click on then on Install Package to install the driver.

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> okay, i did it! the code went in without the same message coming up. Now do i need to restart my computer?
To set up the wireless shut the pc down and unplug the wired (Ethernet cable) and boot up again then use the network manager applet in the top right panel to set up your wifi.
Right click on it and select Edit connections
Then Wireless and Add or Edit and put in your connection info. and you should be good to go.

**********
Just so you know NM (Network Manager) has a nasty habit of getting IP Addresses for any network adapter that is connected meaning it will get one for both your wired and wireless adapter if you're plugged in and the wifi adapter is on.

While this should be a good thing it will then get confused as to which one to use so doing anything on the net will be slow at best.
The easy fix if your pc has a wifi switch (like most laptops) is to turn wifi off while using a wired connection and back on when you want to use wifi.

Another option is to right click on NM and select Edit connections then Wireless and each connection and Edit. Then clear the check box at the top for Connect Automatically.
You have to re-enable it when not using a wired connection to connect automatically again.

---

### Post by SarahCasey on 2010-04-20
Okay, so i have it installed and everything is good. Now, I unplugged the cable and went up to edit connections, and when i click add a wireless its asking me for the SSID and stuff, how do i figure out what those are? Is there any way to find out? lol if not, can i just reset the router i guess and then get the new numbers or adress or whatever? im a bit confused

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> Okay, so i have it installed and everything is good. Now, I unplugged the cable and went up to edit connections, and when i click add a wireless its asking me for the SSID and stuff, how do i figure out what those are? Is there any way to find out? lol if not, can i just reset the router i guess and then get the new numbers or adress or whatever? im a bit confused
Left click on network manager and see if yours is listed. If it is click on it.
The SSID is the name you gave your wireless network in the router.
Most routers you can access the setup by putting
192.168.1.1
or
192.168.0.1
into the address bar of any web browser
up where it says [http://ubuntuforums](http://ubuntuforums).......
and hit Enter BUT you'll have to be connected first.
Then you will need to know your login info. to change settings
If you haven't set it up tell use what make and model it is and we can find the default username and password for you.

Guess it's back to the wired connection to set it up. That is if you haven't setup your wireless network yet in the router.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> Left click on network manager and see if yours is listed. If it is click on it.
The SSID is the name you gave your wireless network in the router.
Most routers you can access the setup by putting
192.168.1.1
or
192.168.0.1
into the address bar of any web browser
up where it says [http://ubuntuforums](http://ubuntuforums).......
and hit Enter BUT you'll have to be connected first.
Then you will need to know your login info. to change settings
If you haven't set it up tell use what make and model it is and we can find the default username and password for you.

Guess it's back to the wired connection to set it up. That is if you haven't setup your wireless network yet in the router.

Alright, I know that there isn't any sort of password set up so I'll be using the defaults i suppose. the model is WRT54G its a Linksys 2.4 GHz Broadband Router

I put in Admin for Username and then just password for the password, just cause i thought it might work but it didn't :/

****oh, and there are still no wireless connections showing up in the network connections box.

---

### Post by 2hot6ft2 on 2010-04-20
user name = not required /give any
password = admin

or
Default admin username - admin
Default admin password - admin

---

### Post by Don Mega on 2010-04-20
I also had this long battle before go to SYSTEM>ADMINISTRATION>UPDATE MANAGER  click on CHECK when it is finished if a list of packages come up click INSTALL UPDATES then reboot then REPEAT STEPS. I spent 2 weeks fighting this wifi issue and all it took was these simple steps:popcorn: try it out first maybe it'll work.....

---

### Post by 2hot6ft2 on 2010-04-20
> **Don Mega said:**
> I also had this long battle before go to SYSTEM>ADMINISTRATION>UPDATE MANAGER  click on CHECK when it is finished if a list of packages come up click INSTALL UPDATES then reboot then REPEAT STEPS. I spent 2 weeks fighting this wifi issue and all it took was these simple steps:popcorn: try it out first maybe it'll work.....
I don't know what that has to do with logging into the router, but ok...:confused:

Sarah, you don't need to do that.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> user name = not required /give any
password = admin

or
Default admin username - admin
Default admin password - admin

Okay, I got it and now i have the IP Address and the "Subnet Mask" but those were the only two things that really had any numbers. I know this probably sounds like a stupid question, but what now? When i look in my network connections, there isn't anything to choose from, my linksys thing isn't showing up. And when i click to add a connection it asks for my SSID and that wasn't on the page or anything :[[[

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> Okay, I got it and now i have the IP Address and the "Subnet Mask" but those were the only two things that really had any numbers. I know this probably sounds like a stupid question, but what now? When i look in my network connections, there isn't anything to choose from, my linksys thing isn't showing up. And when i click to add a connection it asks for my SSID and that wasn't on the page or anything :[[[
By default the SSID is linksys
So if you saw linksys when you left clicked on network manager it was probably yours.
I'll type up a good setup for you give me a couple minutes so nobody will be stealing your wifi.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> By default the SSID is linksys
So if you saw linksys when you left clicked on network manager it was probably yours.
I'll type up a good setup for you give me a couple minutes so nobody will be stealing your wifi.

When i click on Network Manager theres nothing there at all, just the Auto Etho in Wired connections, which is the one thats plugged in my laptop. 
im about to cry this is like the third day i have dragged you into this and its still confusing me :[

---

### Post by Don Mega on 2010-04-20
Once you can scan the area for available networks you can connect to you SSID and enter your Key and connect **BUT** if you aren't even seeing any wireless SSID's out there your wireless card isn't functioning you can see if it isn't working correctly by checking your notification icon where it tells you if you are disconnected or connected to etho or wireless **IF **it says disconnected to Wireless remove it (if it is a removable card remove it and put it back in if it is Built in wifi turn off then on) THEN check the Icon again if it says DEVICE NOT READY it isn't installed correctly....DO THIS NEVER REBOOTING

---

### Post by 2hot6ft2 on 2010-04-20
I'm not sure about the standard linksys firmware since I changed mine to dd-wrt. So yours may be a little different you'll have to find these settings.

Under Wireless > you have things like Wireless mode choose AP
Heck, I'll just attach some pics. of mine with my personal setting info. blocked out.

---

### Post by Don Mega on 2010-04-20
**REBOOT BEFORE TRYING MY LAST POST TURN ON WIRELESS IF BUILT IN WHEN UBUNTU IS LOADING** so the wireless says disconnected

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> When i click on Network Manager theres nothing there at all, just the Auto Etho in Wired connections, which is the one thats plugged in my laptop. 
im about to cry this is like the third day i have dragged you into this and its still confusing me :[
I feel for you but hang in there we'll get it.
open a terminal and run
```
ifconfig
```
and we'll see if it's detected.
Also ```
iwconfig
```
Also if you right click on network manager is Enable Wireless checked or greyed out?
If it's greyed out you can run
```
sudo ifconfig wlan0 up
```
It would be so much faster if one of use was there to do it for you but that's not how this works.

---

### Post by Don Mega on 2010-04-20
if you try my senario and see that it isn't functioning properly then try the update task i posted after rebooting with wireless on... say "don mega didn't work" if my steps didn't help hope it does

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> I'm not sure about the standard linksys firmware since I changed mine to dd-wrt. So yours may be a little different you'll have to find these settings.

Under Wireless > you have things like Wireless mode choose AP
Heck, I'll just attach some pics. of mine with my personal setting info. blocked out.

My wireless settings page looks different than yours, the only thing that says AP is "AP Isolation" then says on or off, default is off. So do you want me to turn it on?

Maybe I'm just not cut out to be a Ubuntu user. lol

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> My wireless settings page looks different than yours, the only thing that says AP is "AP Isolation" then says on or off, default is off. So do you want me to turn it on?

Maybe I'm just not cut out to be a Ubuntu user. lol
I'm not sure what they mean by isolation so I would leave it off.
Just give it a unique SSID for now so you'll know it's yours and make sure to click save or Apply.

And you'll be fine once you clear this hurdle.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> I feel for you but hang in there we'll get it.
open a terminal and run
```
ifconfig
```and we'll see if it's detected.
Also ```
iwconfig
```Also if you right click on network manager is Enable Wireless checked or greyed out?
If it's greyed out you can run
```
sudo ifconfig wlan0 up
```It would be so much faster if one of use was there to do it for you but that's not how this works.

ifconfig:
sarahcasey@SarahCasey-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:73:8d:71  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe73:8d71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5572972 (5.5 MB)  TX bytes:1132456 (1.1 MB)
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

iwconfig:
sarahcasey@SarahCasey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Not lookin too good...But Enable Networking is checked. Do you want me to reboot like Don Mega is sayin? since you've been leading me through this you would know whether thats gonna help my situation

---

### Post by 2hot6ft2 on 2010-04-20
While you're connected to a wired connection your wireless network WILL NOT show up when left clicking the network manager applet.

Networks should show up when you're Not connected by wired.

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> 
Not lookin too good...But Enable Networking is checked. Do you want me to reboot like Don Mega is sayin? since you've been leading me through this you would know whether thats gonna help my situation
You're right it's not looking like the driver is loaded. Go ahead and reboot unplugging the ethernet cable in the process and then left click on NM and see if any networks show up.

---

### Post by Don Mega on 2010-04-20
reboot because now in your iwconf configuration it isn't seeing the wireless card

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> While you're connected to a wired connection your wireless network WILL NOT show up when left clicking the network manager applet.

Networks should show up when you're Not connected by wired.
  

Okay, I completely unplugged the cable so my laptop had no internet connection. I clicked the Network Manager, went to configure VPN, and when i looked in wired, Auto Eth0 was there. When i looked in wireless though, theres nothing. It's just blank. I really don't think i messed up the driver when i installed it, but maybe i did something wrong. And yeah, this would be a thousand times easier if i could just give it to you to fix :P


*****Just now rebooted, took out the internet cable but still nothin is showing up in the wireless box :[

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> Okay, I completely unplugged the cable so my laptop had no internet connection. I clicked the Network Manager, went to configure VPN, and when i looked in wired, Auto Eth0 was there. When i looked in wireless though, theres nothing. It's just blank. I really don't think i messed up the driver when i installed it, but maybe i did something wrong. And yeah, this would be a thousand times easier if i could just give it to you to fix :P
VPN? Thought you were just trying to setup wifi at this point.
What do you get with ```
ifconfig
``` now? Looking for something that starts with **wlan0**

---

### Post by Don Mega on 2010-04-20
okay type: gksudo gedit /etc/modprobe.d/blacklist   if your driver is there delete it then save it then close then reboot again ( you must know the driver ) IF not go to system>administration>hardware drivers   and see if anything list there

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> VPN? Thought you were just trying to setup wifi at this point.
What do you get with ```
ifconfig
``` now? Looking for something that starts with **wlan0**


It just says VPN i don't even know what it means :[ but that's just what comes up when i click the little computer network thing on the upper right side of my computer. options are: Wired Network (which i can't click)
       Auto Eth0
       Disconnect
       VPN Connections > which goes to VPN Configuration

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:26:18:73:8d:71  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe73:8d71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1305339 (1.3 MB)  TX bytes:381873 (381.8 KB)
          Interrupt:30 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I don't see a wlan0

Have i been looking at the wrong thing for Network Connections this whole time? the VPN is throwing me off track now. please say no lol

---

### Post by SarahCasey on 2010-04-20
> **Don Mega said:**
> okay type: gksudo gedit /etc/modprobe.d/blacklist   if your driver is there delete it then save it then close then reboot again ( you must know the driver ) IF not go to system>administration>hardware drivers   and see if anything list there

There's nothing in my hardware drivers 
gahhhh

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> 
I don't see a wlan0

Have i been looking at the wrong thing for Network Connections this whole time? the VPN is throwing me off track now. please say no lol
The VPN is for a Virtual Private Network.
Scratching my head because the wlan0 would be the wifi.
Is this a laptop with a wifi switch?
If it is try switching it on.
If not then we need to find out why the driver isn't loading.

---

### Post by 2hot6ft2 on 2010-04-20
Try this
```
sudo modprobe r8192e_pci
```
```
modinfo r8192e_pci
```

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> The VPN is for a Virtual Private Network.
Scratching my head because the wlan0 would be the wifi.
Is this a laptop with a wifi switch?
If it is try switching it on.
If not then we need to find out why the driver isn't loading.


Yeah, it has a wifi switch, and its on. It was on when i was trying to connect without the internet cable. so i dont know what's going on either lol.
I know you have put so much effort into helping me, but do you think i should just give up on ubuntu? I don't want to, but you know a lot more about this than me and i don't want to be a hopeless cause lol.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> Try this
```
sudo modprobe r8192e_pci
``````
modinfo r8192e_pci
```


sarahcasey@SarahCasey-laptop:~$ sudo modprobe r8192e_pci
[sudo] password for sarahcasey: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module r8192e_pci not found.
sarahcasey@SarahCasey-laptop:~$ modinfo r8192e_pci
ERROR: modinfo: could not find module r8192e_pci

What's it ignoring?? D:

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> Yeah, it has a wifi switch, and its on. It was on when i was trying to connect without the internet cable. so i dont know what's going on either lol.
I know you have put so much effort into helping me, but do you think i should just give up on ubuntu? I don't want to, but you know a lot more about this than me and i don't want to be a hopeless cause lol.
NO don't give up. Wireless is perhaps the most irritating things there is in linux and we'll get it going even if I have to get chili555 to come do some troubleshooting on it.
Once you get past this the rest is a LOT easier, trust me.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> NO don't give up. Wireless is perhaps the most irritating things there is in linux and we'll get it going even if I have to get chili555 to come do some troubleshooting on it.
Once you get past this the rest is a LOT easier, trust me.

kk im trusting you lol.

---

### Post by Don Mega on 2010-04-20
it looks like you need to go to this web site
 [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E")
and download the software to your desktop <>or download it then go to the tool bar in firefox click downloads then right click on the file click on open containting folder then copy and paste to desktop **THEN** go to system>administration>synaptic package manager   and on right search field type ndiswrapper check box then click apply on top to install after completion go to system>administration> windows wireless drivers and follow steps to install driver. if this works after reboot then you have to create a folder as root user in a terminal to save the .inf and .sys file in. and then uninstall driver and reinstall with files that are in new location ( sounds hard but it isn't just takes awhile)

---

### Post by SarahCasey on 2010-04-20
> **Don Mega said:**
> it looks like you need to go to this web site
 [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E")
and download the software to your desktop <>or download it then go to the tool bar in firefox click downloads then right click on the file click on open containting folder then copy and paste to desktop **THEN** go to system>administration>synaptic package manager   and on right search field type ndiswrapper check box then click apply on top to install after completion go to system>administration> windows wireless drivers and follow steps to install driver. if this works after reboot then you have to create a folder as root user in a terminal to save the .inf and .sys file in. and then uninstall driver and reinstall with files that are in new location ( sounds hard but it isn't just takes awhile)

I'm pretty sure i've already tried those files and they didn't work :/

---

### Post by Don Mega on 2010-04-20
opps didn't get it out quick enough lol

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> sarahcasey@SarahCasey-laptop:~$ sudo modprobe r8192e_pci
[sudo] password for sarahcasey: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module r8192e_pci not found.
sarahcasey@SarahCasey-laptop:~$ modinfo r8192e_pci
ERROR: modinfo: could not find module r8192e_pci

What's it ignoring?? D:
Ok, I don't know why t's looking at ndiswrapper and the driver is not installed. First lets get rid of ndiswrapper
```
sudo apt-get purge ndiswrapper ndisgtk
```
Since there is a linux driver you wont be needing it. And there is a good post that is pretty detailed on this so I'm going to have you run the stuff in it. So here it is
anything after the $ sign you run in a terminal.
The driver it links to is NOT there. arrrrg so change it to the driver you already downloaded.
> **idavidmiller said:**
> The following procedure worked without any issues with a Samsung N130 Netbook and the Linux Realtek r8192e driver using Ubuntu 9.10, 32-bit version. From a shell terminal session do:

0. Need headers and source packages:

$ sudo apt-get install linux-source linux-headers-`uname -r`

1. Download Realtek r8192e driver archive from: 

    [http://rapidshare.com/files/327944041/rtl8192e_linux_2.6.0012.1210.2009.tar.gz.html](http://rapidshare.com/files/327944041/rtl8192e_linux_2.6.0012.1210.2009.tar.gz.html)

Note: Click the "Free User" button under the left speedometer and wait for the countdown timer to end. Then click Download button. Save file.

2. After downloading is complete, change to the download folder and extract driver archive to a working folder:

$ cd "~/your/download/folder" # (whatever your pathname is)

$ tar -xvjf rtl8192e_linux_2.6.0012.1210.2009.tar.gz


3. Installing the kernel source package (step 0. above) puts an archive file only in    /usr/src. Need to extract the source archive to /usr/src.

First,  get the source package version number:

$ dpkg -p linux-source | grep Depends:

This gives the version number of the source package. Use the version numbers only in the the following command. Example: for output of

 "Depends: linux-source-2.6.31"

use 2.6.31 for the "$your_version_number" below:

$ sudo tar -C /usr/src -xvjf /usr/src/linux-source-$your_version_ number.tar.bz2


4. Build and install driver.

Change into the rtl8192e_linux_2.6.0012.1210.2009 folder:

$ cd rtl8192e_linux_2.6.0012.1210.2009

$ sudo make

IMPORTANT NOTE: Must be superuser (sudo -s) for next command to make install without errors!

$ sudo -s make install

5. Add module to kernel and check module info:

$ sudo modprobe r8192e_pci

$ modinfo r8192e_pci

Module should be fired up at this point. You should get an output listing from modinfo that includes something like the following:

filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/r8192e_pci.ko
license:        GPL
version:        0012.1210.2009
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards

$ lspci -vv 

This should show info about all the drivers attached to PCI devices in the listing produced. Scroll through the listing. Should show under "Network controller:"

Kernel driver in use: rtl819xE
Kernel modules: r8192e_pci


6. You now have to configure a wireless connection for your wireless setup using Network Connections from System menu: SSID, DHCP or fixed IP, security settings (WEP, key, etc.), Infrastucture or Ad Hoc, auto-connect, etc. Be sure to connect to this setup. You may find an auto SSID name already listed there. If so, edit this auto connection.

7. Check network configuration:

$ iwconfig wlan0

Note: if wlan0 does not work try wlan1 or just omit this and use iwconfig only.

If the wireless is connected, your wireless SSID will show up in the output as ESSID as well as other wireless connection data:

wlan0     802.11bg ESSID:"your_wireless_SSID"  Nickname:"rtl8192E"

The exact output may be different on your system: wlan1 instead of wlan0, 802.11bgn instead of 802.11bg, etc., but these elements should all be present in this essential form.

6. Edit /etc/modules (gksudo gedit /etc/modules,  sudo vim /etc/modules, sudo nano /etc/modules or whatever editor you use) and add line:

r8192e_pci


This will install the module at boot time.

An addtional note. This wireless driver seems to cause problems with the power manager sleep (suspend) and hibernate modes. There is a fix for this that worked on my netbook. Edit /usr/lib/pm-utils/sleep.d/55NetworkManager to read as shown below adding the lies in bold:

case "$1" in
    hibernate|suspend)
        **modprobe -r r8192e_pci**
        suspend_nm
        ;;
    thaw|resume)
        **modprobe r8192e_pci**
        resume_nm
        ;;
    *) exit $NA
        ;;
esac


These lines remove the driver on supsend/hibernate and activate it again when waking up from suspend or hibernate.

See the following for details:

[http://www.backports.ubuntuforums.org/showpost.php?p=8574835&postcount=3](http://www.backports.ubuntuforums.org/showpost.php?p=8574835&postcount=3)

---

### Post by Don Mega on 2010-04-20
yes what 
2hot6ft2 said if ndiswrapper didn't work before REMOVE NDISWRAPPER !!! YAY
 these steps should work.

---

### Post by SarahCasey on 2010-04-20
okay, the very first step lol 1. the rapidshare link didn't work. I clicked it and it said there was an error on the page. did it work for you?

---

### Post by Don Mega on 2010-04-20
try putting linux-source linux-headers in the search field in synaptic package manager to install it.

---

### Post by SarahCasey on 2010-04-20
> **Don Mega said:**
> try putting linux-source linux-headers in the search field in synaptic package manager to install it.

easy killer, what is a synaptic package manager?

---

### Post by Don Mega on 2010-04-20
it is linux-source-2.6.31

---

### Post by Don Mega on 2010-04-20
go to system>admin>synaptic package manager

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> okay, the very first step lol 1. the rapidshare link didn't work. I clicked it and it said there was an error on the page. did it work for you?
No just use the one you already downloaded and when it says cd to the folder use
```
cd Downloads/rtl8192e_linux_2.6.0011.1029.2009

```
instead of those in the instructions

---

### Post by Don Mega on 2010-04-20
after you install that follow the rest of his steps ( check linux-source-2.6.31 then click apply on top)

---

### Post by SarahCasey on 2010-04-20
> **Don Mega said:**
> go to system>admin>synaptic package manager

K, so linux-source says 'to be installed' when i click on it.

---

### Post by SarahCasey on 2010-04-20
I "applied" linux-source

Where's 2hot6ft2??

---

### Post by Don Mega on 2010-04-20
Yes synaptic package manager is a faster way of installing packages rather then downloading .deb or .tar packages and having to extract and all that mess

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> No just use the one you already downloaded and when it says cd to the folder use
```
cd Downloads/rtl8192e_linux_2.6.0011.1029.2009

```instead of those in the instructions

k, just me being dumb and i definitely didn't see this post. alright, im about to try it again, just be patient with me :]

---

### Post by 2hot6ft2 on 2010-04-20
I'm here just digging for more info...

---

### Post by Don Mega on 2010-04-20
not sure but follow the rest of the steps (try geting the driver installed through synaptic) and i hope it works for you I have to leave but I check later on you good luck:popcorn:

---

### Post by SarahCasey on 2010-04-20
Okay, right at the end of step 5, i thought i followed it correctly here is what it says :

    Kernel driver in use: r8169
    Kernel modules: r8169


and that's not right i don't think....

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> Okay, right at the end of step 5, i thought i followed it correctly here is what it says :

    Kernel driver in use: r8169
    Kernel modules: r8169


and that's not right i don't think....
You mean this part?
> $ lspci -vv

This should show info about all the drivers attached to PCI devices in the listing produced. Scroll through the listing. Should show under "Network controller:"

Kernel driver in use: rtl819xE
Kernel modules: r8192e_pci
Remember you have r8169 for your ethernet adapter so it should show both I don't believe it's a one or the other type thing.
I'll go back and make sure of the number but that sounds like the ethernet.

Yep, that's the ethernet adapter
>        capabilities: bus_master cap_list rom [B]ethernet physical
       configuration: broadcast=yes driver=r8169[/B] driverversion=2.3LK-NAPI ip=192.168.1.124 latency=0 multicast=yes


---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> You mean this part?

Remember you have r8169 for your ethernet adapter so it should show both I don't believe it's a one or the other type thing.
I'll go back and make sure of the number but that sounds like the ethernet.


Yes, you're right. lol. just bein stupid again, thats me. Well i have a real problem now, i promise lol. i put in iwconfig and heres what happened

sarahcasey@SarahCasey-laptop:~/Downloads/rtl8192e_linux_2.6.0011.1029.2009$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> Yes, you're right. lol. just bein stupid again, thats me. Well i have a real problem now, i promise lol. i put in iwconfig and heres what happened

sarahcasey@SarahCasey-laptop:~/Downloads/rtl8192e_linux_2.6.0011.1029.2009$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
That just means that we still don't have the driver loading for it for some reason your ifconfig should still look good. I think thats' what you were expecting to see when you ran iwconfig

iw only shows wireless
if shows interFaces

---

### Post by 2hot6ft2 on 2010-04-20
What did you get from these in step 5
5. Add module to kernel and check module info:

```
sudo modprobe r8192e_pci
```

```
modinfo r8192e_pci
```

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> What did you get from these in step 5
5. Add module to kernel and check module info:

```
sudo modprobe r8192e_pci
``````
modinfo r8192e_pci
```

sudo modinfo:

sarahcasey@SarahCasey-laptop:~/Downloads/rtl8192e_linux_2.6.0011.1029.2009$ modinfo r8192e_pci
filename:       /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/r8192e_pci.ko
license:        GPL
version:        V 1.1
author:         Copyright(c) 2008 - 2010 Realtek Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     77F4CE369109B480FFDD8B6
alias:          pci:v000007AAd00000047sv*sd*bc*sc*i*
alias:          pci:v000007AAd00000044sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.31.9 SMP mod_unload modversions 586 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)



sudo modprobe:
sarahcasey@SarahCasey-laptop:~/Downloads/rtl8192e_linux_2.6.0011.1029.2009$ sudo modprobe r8192e_pci
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by 2hot6ft2 on 2010-04-20
We made some progress
> **SarahCasey said:**
> sudo modinfo:

sarahcasey@SarahCasey-laptop:~/Downloads/rtl8192e_linux_2.6.0011.1029.2009$ modinfo r8192e_pci
filename:       /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/**[COLOR="DarkGreen"]r8192e_pci.ko[/COLOR]**
license:        GPL
version:        V 1.1
author:         Copyright(c) 2008 - 2010 Realtek Corporation <wlanfae@realtek.com>
description:    **[COLOR="DarkGreen"]Linux driver for Realtek RTL819x WiFi cards[/COLOR]**
srcversion:     77F4CE369109B480FFDD8B6
alias:          pci:v000007AAd00000047sv*sd*bc*sc*i*
alias:          pci:v000007AAd00000044sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.31.9 SMP mod_unload modversions 586 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)



sudo modprobe:
sarahcasey@SarahCasey-laptop:~/Downloads/rtl8192e_linux_2.6.0011.1029.2009$ sudo modprobe r8192e_pci
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by 2hot6ft2 on 2010-04-20
Now lets see if it's listed with
```
lspci -vv 
```
Put the results in a code box by highlighting it all and clicking on the # sign at the top of the reply box to make it easier to read.

---

### Post by SarahCasey on 2010-04-20
> **2hot6ft2 said:**
> We made some progress

yay progress!

Do you want to just wrap this up and hopefully if i get a chance to get on here tomorrow and youre online, i'll just message you and we'll see whats up? Thanks for all the help, yet again lol. :P

---

### Post by anewguy on 2010-04-20
> **Don Mega said:**
> okay type: gksudo gedit /etc/modprobe.d/blacklist   if your driver is there delete it then save it then close then reboot again ( you must know the driver ) IF not go to system>administration>hardware drivers   and see if anything list there


Please take this only as a constructive critizism, not an attack, but.....

Please follow the flow of the help that is being given and that the OP is following.  You're interjecting things here that just make confusion.

Dave ;)


Everyone else - I'll take the heat on this one when it's reported, but maybe it will help.....

---

### Post by SarahCasey on 2010-04-20
Well hold on, i don't see a # sign....

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> yay progress!

Do you want to just wrap this up and hopefully if i get a chance to get on here tomorrow and youre online, i'll just message you and we'll see whats up? Thanks for all the help, yet again lol. :P
That's fine we can pick it up tomorrow. Perhaps chili555 will drop in and make it a 2 or 3 command solution from here.
Thanks anewguy, but he did step out gracefully a while ago by PM. Just so you know...
:guitar:

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> Well hold on, i don't see a # sign....
Third from the right in pic.

---

### Post by SarahCasey on 2010-04-20
My reply box doesn't have that.... :[ it only has the top row.

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> My reply box doesn't have that.... :[ it only has the top row.
It uses java so if you're up for running a few commands we can get your multimedia fixed up for you. The medibuntu server has been down a few days now but maybe it wont throw too many errors.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to **decline the Java terms of use since we'll install suns java next.**
Next we want the sun version of Java since it works better and will pass the test on this page.
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
It will say there is an update available but the main thing is it works.
```
sudo apt-get ininstall sun-java6-jre sun-java6-plugin
```
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And you're done.

VLC Player will be in Applications > Sound and Video > VLC

And yes I have that saved for a quick copy and paste...

---

### Post by SarahCasey on 2010-04-20
It said an error occurred and something with "medibuntu" could not be found. My brain is fried for today but i will most likely be back tomorrow. I have a busy rest of the week, but whenever I do get the time to get back and figure this out i will send you a message and see if you're still interested lol. Thank's again, have a good night everybody that helped!

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> It said an error occurred and something with "medibuntu" could not be found. My brain is fried for today but i will most likely be back tomorrow. I have a busy rest of the week, but whenever I do get the time to get back and figure this out i will send you a message and see if you're still interested lol. Thank's again, have a good night everybody that helped!
The medibuntu server has been down a few days now so that's not surprising. But if you ran it all you now have the # sign for a code box. I'll talk to you when you come back.
Goodnight.
And you're welcome

---

### Post by SarahCasey on 2010-04-20
SOLVED!!!!!!!!!!!
 
idk what it was, i just now as i was about to shut my computer down decided to give it one last try and i have successfully connected to my wifi!!! ahhhhhh best day of my life!!!!!! THANK YOU

---

### Post by 2hot6ft2 on 2010-04-20
> **SarahCasey said:**
> SOLVED!!!!!!!!!!!
 
idk what it was, i just now as i was about to shut my computer down decided to give it one last try and i have successfully connected to my wifi!!! ahhhhhh best day of my life!!!!!! THANK YOU
LOL. Great. Now don't forget to use the Thread Tools at the top of the thread to mark it as solved.
:guitar:
And you're still welcome....

---

### Post by Running_Dualboot on 2010-04-22
Awesome it's solved, and it only took 14 pages of posts :)

---

### Post by 2hot6ft2 on 2010-04-25
> **Running_Dualboot said:**
> Awesome it's solved, and it only took 14 pages of posts :)
Maybe not, sounds like it's not working again.
Let's see we were here. I think #8 is what's missing.

5. Add module to kernel and check module info:

```
sudo modprobe r8192e_pci
```
```
modinfo r8192e_pci
```

Module should be fired up at this point. You should get an output listing from modinfo that includes something like the following:

filename: /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/r8192e_pci.ko
license: GPL
version: 0012.1210.2009
author: Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description: Linux driver for Realtek RTL819x WiFi cards

```
lspci -vv
```

This should show info about all the drivers attached to PCI devices in the listing produced. Scroll through the listing. Should show under "Network controller:"

Kernel driver in use: rtl819xE
Kernel modules: r8192e_pci


6. You now have to configure a wireless connection for your wireless setup using Network Connections from System menu: SSID, DHCP or fixed IP, security settings (WEP, key, etc.), Infrastucture or Ad Hoc, auto-connect, etc. Be sure to connect to this setup. You may find an auto SSID name already listed there. If so, edit this auto connection.

7. Check network configuration:

```
iwconfig wlan0
```

Note: if wlan0 does not work try wlan1 or just omit this and use iwconfig only.

If the wireless is connected, your wireless SSID will show up in the output as ESSID as well as other wireless connection data:

wlan0 802.11bg ESSID:"your_wireless_SSID" Nickname:"rtl8192E"

The exact output may be different on your system: wlan1 instead of wlan0, 802.11bgn instead of 802.11bg, etc., but these elements should all be present in this essential form.

[B]8. Edit /etc/modules 
```
gksu gedit /etc/modules
```

and add line:

r8192e_pci


This will install the module at boot time.[/B]

An addtional note. This wireless driver seems to cause problems with the power manager sleep (suspend) and hibernate modes. There is a fix for this that worked on my netbook. Edit /usr/lib/pm-utils/sleep.d/55NetworkManager to read as shown below adding the lies in bold:

```
case "$1" in
    hibernate|suspend)
        **modprobe -r r8192e_pci**
        suspend_nm
        ;;
    thaw|resume)
        **modprobe r8192e_pci**
        resume_nm
        ;;
    *) exit $NA
        ;;
esac
```


These lines remove the driver on supsend/hibernate and activate it again when waking up from suspend or hibernate.

See the following for details:

[http://www.backports.ubuntuforums.or...35&postcount=3](http://www.backports.ubuntuforums.or...35&postcount=3)

---

### Post by SarahCasey on 2010-04-25
Okay, i got to #8 but when i'm in the modules box i put in r8192e_pci and it says that it can't find the file /edit/modules?

---

### Post by 2hot6ft2 on 2010-04-25
> **SarahCasey said:**
> Okay, i got to #8 but when i'm in the modules box i put in r8192e_pci and it says that it can't find the file /edit/modules?
```
gksu gedit /**etc**/modules
```
not
/**edit**/modules
LOL
It will be ok. Copy and paste will help prevent typos like that.
just add
> r8192e_pci
to the bottom of the file on its own line and Save then Close the file.

---

### Post by SarahCasey on 2010-04-25
lol yea, thanks i put it in and saved it so i'm going to reboot and see if its still workin

---

### Post by 2hot6ft2 on 2010-04-25
> **SarahCasey said:**
> lol yea, thanks i put it in and saved it so i'm going to reboot and see if its still workin
Go for it.

---

### Post by SarahCasey on 2010-04-25
okay so that sucked lol. It wasn't working so i just went through the whole "sudo make" and all that and its working now but i'm going to try the edit gksu thing one more time to make sure i didn't just type something in wrong

---

### Post by SarahCasey on 2010-04-25
SOLVED! for real this time. lol. thank you!

---

### Post by 2hot6ft2 on 2010-04-25
> **SarahCasey said:**
> SOLVED! for real this time. lol. thank you!
Way to go. See I told you that you would get the hang of it.
:guitar:
You're welcome....again...

---

### Post by djwazza on 2010-05-05
Hello I am also a noob when dealing with Linux and have just put 10.04 on my Samsung N150 Netbook as I was fed up with the speed of Win 7.  This has the Realtek 8192E as determined using the info here and it doesn't work.  I have the Ndiswrapper with rtl819xp installed and with hardware present.

I've read through this thread (got confused in places) and tried the Linux driver install at page 5.

This is what I get once I try 'make':

[FONT=monospace]david@david-netbook:~/rtl8192e_linux_2.6.0011.1029.2009$ make
make: *** /lib/modules/2.6.32-22-generic-pae/build: No such file or directory. Stop.
make: *** [all] Error 2

I've also updated the Kernel to 2.6.32-22; what am I doing wrong?  Why doesn't 'make' work?  

I really would like to start using Ubuntu but a Netbook that can only connect with a wire is pretty useless.

Please help!
[/FONT]

---

