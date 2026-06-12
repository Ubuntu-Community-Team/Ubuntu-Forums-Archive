---
title: "Ubuntu wireless connection"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by king123440 on 2011-04-15
I installed Ubuntu on my Dell netbook. There's no wireless connection switch installed on my laptop so I can't access the internet. Can anyone tell me a special program that can do the job? Thanks.

---

### Post by Locke_99GS on 2011-04-15
Hook it up by wire, update the software, and install linux-firmware-nonfree.
```
sudo apt-get install linux-firmware-nonfree
```

If your wireless doesn't become available, post the output of lspci and we should be able to direct you to the proper driver for your wireless stuffs.
```
lspci
```

---

### Post by grahammechanical on 2011-04-15
Hi

Ubuntu installs a utility called Network Manager. There should be an icon of 4 concentric rings radiating upwards on the top panel and to the right. In your case it should have a red exclamation mark against it. This indicates that you do not have a network connection.

Can you make an ethernet connection? If you can, then do so. The network icon will change to two arrows going in opposite directions. Then go to System>Administration>Additional Drivers. Activate any drivers that are available.

If you are not offered the opportunity to activate a wireless driver, then may be you do not need one. May be the driver for your wireless adapter is built in to the operating system.

Right click the network manager icon and make sure that there is a tick mark against the lines Enable Networking and Enable wireless. Clicking on these lines acts like an on/off switch.

Left click the network manager icon. Do you see any wireless networks listed as available? Is your wireless network listed? If so, click on it and enter the wireless key or pass phrase.

By the way, if you are dual booting with Windows then it may be possible to switch wireless off in Windows. If you have done that then Ubuntu will not be able to switch it on (may be not). Make sure wireless is switched on in Windows. Then shutdown and boot into Ubuntu.

Regards.

---

### Post by Hippytaff on 2011-04-15
It might be worth posting the results of the wireless script in the link below to help people help you diagnose and fix the problem

---

### Post by Mean Mr Mustard on 2011-04-19
Hi everyone , glad to join the forum. ):P
If anyone can  help me out here I would be most grateful. My problem is that I have just downloaded ubuntu 10.10 to my desk top and it now runs as dual boot system with windows XP. The desk top is linked wirelessly to internet router downstairs and works fine. However when I boot up via ubuntu I cannot access internet. Connection icon at top has red exclamation mark which I cannot shift despite me trying to update network connection info. If I reboot back into windows I get internet access no problem?

---

### Post by mikewhatever on 2011-04-19
Hi Mr Mustard, welcome to the forums.
You probably need to install the driver for the wireless card. Hook up an ethernet cable for a minute, then open System->Administration->Additional Drivers.

---

### Post by Mean Mr Mustard on 2011-04-19
Thanks Mikewhatever for the welcome...and your advice its much appreciated.
 
To achieve cable connection to net means I will have to disconnect desktop PC  from upstairs location to plug into router downstairs!!!!! Ah well, nothings ever simple where PC's are concerned. :lolflag:

---

### Post by Mean Mr Mustard on 2011-04-22
Well I have hooked to internet via cable but when I look for additional drivers I get message  "No proprietry drivers are in use on this system. Well I have to say that I am now getting pretty ****** off with Ubuntu! I say this because I was looking for an alternative to Windows and was told Oh you should try Ubuntu, well I have and ALL I am getting is HASSLE! All I want to do is connect  to the internet via my wireless card which incidently works GREAT when I fire up same PC via WIndows. SO can somebody PLEASE help me out here before abandon Ubuntu FOREVER!

---

### Post by Hippytaff on 2011-04-22
whats the output of ```
lspci
``` :-)

Or download and run the wireless script linked below to save time.

---

### Post by Locke_99GS on 2011-04-23
You need to give us some information (like that of which we've requested a couple of times already) before we can actually help you.

Remember that Ubuntu isn't just free-as-in-beer, but free-as-in-speech as well. To live up to this promise, they try to not include proprietary drivers out-of-box. Jockey (the program that tries to install proprietary drivers for you) only actually works with a very small handful of devices - though they do tend to be the most common offenders. I honestly don't know why the jockey devs, or Ubuntu devs for that matter, haven't actually made an attempt to improve it's usefulness.

Also, please mind that Linux is not Windows.

---

### Post by wep940 on 2011-04-23
> **Mean Mr Mustard said:**
> Well I have hooked to internet via cable but when I look for additional drivers I get message "No proprietry drivers are in use on this system. Well I have to say that I am now getting pretty ****** off with Ubuntu! I say this because I was looking for an alternative to Windows and was told Oh you should try Ubuntu, well I have and ALL I am getting is HASSLE! All I want to do is connect to the internet via my wireless card which incidently works GREAT when I fire up same PC via WIndows. SO can somebody PLEASE help me out here before abandon Ubuntu FOREVER!
 
First off, you are hijacking this thread - please open a new thread with your problem.
 
When you hard-wire a connection, do the following in a terminal window:
 
sudo apt-get update <press enter>
 
It will ask for a password - it's just your normal Ubuntu password and it won't show on the screen as you type it.
 
After that, go back and try the Hardware Drivers or Additional Drivers again.
 
Remember to disconnect the hardwire cable before you try to use the wireless.
 
Also, you will need to right-click on the network manager icon and be sure that "Enable Wireless" is checked so it is active.

---

### Post by Mean Mr Mustard on 2011-04-25
Many thanks to those that took the time to reply to me...here is the info I hope will explain the problem. I am no expert here so please bear with me. Many thanks
 
[FONT=Times New Roman][SIZE=3]B UHCI #4 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]03:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]03:04.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]03:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)[/SIZE][/FONT]

---

### Post by wep940 on 2011-04-25
Please note this thread was opened by king123440, so unless you are king123440 you should be posting all of your questions in a new thread.  Since you are new to ubuntu you probably just don't know how things work here on the forums.  When you have a question, even if it looks similar to one in an open thread, you should open your own thread.  You can probably imagine the confusion that results when 2 sets of questions are being answered, more information requested, etc., and you have no idea if the poster is talking to the Original Poster or to other person.  This is why we don't like hijacked threads.  Right now, we have no idea what happened to or how things went for king123440, as you sort of took over the thread.
 
Not trying to be mean or anything - we all were new to the forum at one point.  Keeping seperate threads really does help here.
 
Best of luck with Ubuntu, and welcome!

---

### Post by Mean Mr Mustard on 2011-04-25
OK wep940...many thanks for the advice  so have now moved to my own thread. My apologies to king123440.

---

### Post by Mean Mr Mustard on 2011-04-29
Please see below...My apologies to one and all.

---

### Post by Mean Mr Mustard on 2011-04-29
> **wep940 said:**
> First off, you are hijacking this thread - please open a new thread with your problem.
 
When you hard-wire a connection, do the following in a terminal window:
 
sudo apt-get update <press enter>
 
It will ask for a password - it's just your normal Ubuntu password and it won't show on the screen as you type it.
 
After that, go back and try the Hardware Drivers or Additional Drivers again.
 
Remember to disconnect the hardwire cable before you try to use the wireless.
 
Also, you will need to right-click on the network manager icon and be sure that "Enable Wireless" is checked so it is active.
 
Tried using sudo apt-get update as suggested (and yes I know I'm in the wrong thread!) but STILL no change! No wireless connection and Network Manager shows Enable Wireless Connection as STILL being greyed out. Just about had enough of ubuntu...whats the point if you cannot get it to work properly?](*,)

---

### Post by Locke_99GS on 2011-04-29
It takes time for volunteers around the world to baby step people through issues in other peoples' threads. If you get frustrated so easily, you may want to consider sticking with whatever OS you're presently familiar and comfortable with. Apparently not everybody can cope with Linux's learning curve.

---

### Post by Hippytaff on 2011-04-29
> **Locke_99GS said:**
> It takes time for volunteers around the world to baby step people through issues in other peoples' threads. If you get frustrated so easily, you may want to consider sticking with whatever OS you're presently familiar and comfortable with. Apparently not everybody can cope with Linux's learning curve.

I know what you mean, but that's a bit harsh...but I know what you mean ;)

---

### Post by Mean Mr Mustard on 2011-05-01
My sincere thanks to everybody who constributed ..but there are far more important things in my life than ubuntu...I guess its not for me, bye. ):P

---

