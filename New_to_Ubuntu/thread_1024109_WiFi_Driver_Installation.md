---
title: "WiFi Driver Installation"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by ShadowKingpin on 2008-12-28
I'm sure this question has been asked A THOUSAND TIMES, but I just would rather get the answers for the question that I ask in my own words so that it is better understood.  

So, I have an Acer Aspier 5570z (5570-2997z) and am clueless on how to get WiFi.  I already have NDIS (However you spell it) installed and I have no clue about getting a Wireless Driver installed onto it.  If it makes it easier, I also have Wine installed.  

Anyways, I have no clue whatsoever on coding and such with Ubuntu hence me being on the beginner portion of the forums.  My friend tried coding and got a program called "WiFi Rader" under applications, and under internet.  Well the problem with that, is that he didn't finish the coding, so the program doesn't work.  My question is, how the heck do I get Wireless internet on my laptop? 

I have no clue on how to search for Access Points or nothing.  Can anyone please help?  I once again apologize for asking this since it has been asked many times before.

---

### Post by Michael.Godawski on 2008-12-28
hello ShadowKingpin, 

relax,

open the terminal 
applications > accessories > terminal 
and post the outputs of these commands:

```
sudo lshw -C network
iwconfig
ifconfig
sudo iwlist scan
```

After the sudo commands you will have to enter your login password. I won't be displayed, just type it in and hit enter.

---

### Post by ShadowKingpin on 2008-12-28
lo, eth0, and pan0 are all saying "Interface doesn't support scanning."  What do I do now?

---

### Post by Michael.Godawski on 2008-12-28
Can you post the exact wording of the outputs? just highlight the output with the mouse and press ctrl+shift+c to copy
and paste it with ctrl+v.
thx

---

### Post by ShadowKingpin on 2008-12-28
Sure!

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


Actually, I didn't get the chance to install the driver yet.  I'm assuming that's the reason why.  It's almost done downloading and I'll install it through NDIS, and let you know what happened.  After it finds access points on the terminal, how do I connect to them?

---

### Post by ShadowKingpin on 2008-12-28
ok so, I downloaded the driver for Acer Intel Processor.  There are so many files, how do I install the driver?

---

### Post by igknighted on 2008-12-28
There are linux native drivers for every wifi chip out there.  I would hold off on downloading anything right now.  Unless you know exactly what driver you need, and we don't have all the info yet, chances are things could get messed up so even the right driver wont work.

Can you run the command 'lspci'?  Your wifi card was not recognized as a network interface by the network subsystem, so this command will query the PCI bus and see what devices are connected.

---

### Post by Tom--d on 2008-12-28
Go to Add/Remove and Install "Windows Wireless Drivers" (Its a GUI to ndiswrapper) and install your Windows driver from there.

---

### Post by ShadowKingpin on 2008-12-28
ok so, the information i got when i put in the command in Terminal was:


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by ShadowKingpin on 2008-12-28
Ok so, I downloaded the Anthros Vista Driver and there are two .inf files: netathr and netathrx.  Since the NDIS Wrapper asks me for an .inf file im assuming it's one of those two.  Which one do I install?

---

### Post by ShadowKingpin on 2008-12-28
So I installed one of the .inf files and it says that the hardware is present.  The Other one said that it was invalid.  So, I tried the command again and the same messege appeared, Interface doesn't support scanning.  What do I do?

---

### Post by ShadowKingpin on 2008-12-28
*Bump*

---

### Post by ShadowKingpin on 2008-12-29
Anyone.....?

---

### Post by ShadowKingpin on 2008-12-29
I know I'm getting impatiant, but not having WiFi and sticking to ethernet is frustraiting.  Can anyone please help?

---

### Post by benerivo on 2008-12-29
I'm not on ubuntu, but instead on debian. As you've no replies, please try my method...

```
sudo apt-get install module-assistant madwifi-tools
```Then i would download the madwifi source with ```
wget http://http.us.debian.org/debian/pool/non-free/m/madwifi/madwifi-source_0.9.4+r3772.20080716-1_all.deb
```

And then install this downloaded file with```
sudo gdebi ~/madwifi-source_0.9.4+r3772.20080716-1_all.deb
```

Then do```
m-a- prepare
``````
m-a a-i madwifi
```Then reboot.

---

### Post by ShadowKingpin on 2008-12-29
> Then do```
m-a- prepare
``````
m-a a-i madwifi
```Then reboot.

I kept getting error messeges for inputting these.  Saying that nothing was found and that it can't continue.  I installed the package fully.  Don't understand why it isn't working.  What should I do now?

---

### Post by balloooza on 2008-12-29
Hi shadowkingpin, I hope you are still there, and are still using ubuntu as your OS, the solution iss simple, I am running ath242 on my eee pc. just run
```
sudo modprobe ath_pci
```
and then the wireless will work, just use the network icon in the top of the screen, right click the icon and make sure that "enable networking" and "enable wireless" is checked, and then left click it and set the network you want to connect to, these are the networks that I have successfully connected to:

wpa2 personal aes encryption (all the bells and linksys whistles)
and plain old unsecure

this is the driver that I am using right now

---

### Post by ShadowKingpin on 2008-12-29
> **balloooza said:**
> Hi shadowkingpin, I hope you are still there, and are still using ubuntu as your OS, the solution iss simple, I am running ath242 on my eee pc. just run
```
sudo modprobe ath_pci
```
and then the wireless will work, just use the network icon in the top of the screen, right click the icon and make sure that "enable networking" and "enable wireless" is checked, and then left click it and set the network you want to connect to, these are the networks that I have successfully connected to:

wpa2 personal aes encryption (all the bells and linksys whistles)
and plain old unsecure

this is the driver that I am using right now


My friend, I am still using Ubuntu and love the OS to death, but getting WiFi seems more of a problem then what it already should be.  I went to Terminal and input the code, then input my password.  Nothing happened.  It just went back to the same command.  Nothing happened.  I made sure that Networking was Enabled, and for some reason, "Enable Wireless" couldn't be found.  I still can't search for any access points.  I'm so lost...

---

### Post by balloooza on 2008-12-29
When you are typing your password nothing will happen, this is normal but your password will still go in. Was this your problem?

---

### Post by ShadowKingpin on 2008-12-29
Yes.  It still went in, it's just nothing happened.  I don't understand what has happened.  I'm so lost.  My WiFi indicator on the front of my laptop won't flash for some reason (maybe because of not finding an access point?), I have no way of searching for an access point, and I can't find the "Enable Wireless" at the top.  I'm sorry I'm such a bother on this subject.  I LOVE Ubuntu to death, but not having WiFi is VERY frustraiting.  That's why a lot of my friends unfortiantly went back to Windows.  I really do NOT want to go back to Windows because XP & Vista have never came close to working as good as Ubuntu, but if I can't get WiFi by next fall (Still a long time away), I will have to go to Vista just for Wireless Internet.

---

### Post by balloooza on 2008-12-29
can you run:
```
modprobe -l | grep -F ath_pci
```
and post your results, this is not a fix, but it will help me determin if you have the ath_pci driver installed
Also most of the fancy features like the switches and the indicato lights are not supported by linux, even if they are, you still need the driver


ooooo wait I think I know, still post the other stuff, run
```
sudo modprobe -r ndiswrapper
```
(that is the fix, I hope)

---

### Post by ShadowKingpin on 2008-12-29
The first response is:

/lib/modules/2.6.27-9-generic/volatile/ath_pci.ko

And nothing happened to second one.  The same as the code you gave me in the previous reply, nothing at all happened.  It asked me for my password, I gave it, and nothing happened.

---

### Post by balloooza on 2008-12-29
can you run
```
sudo modprobe ath_pci
```
again and then check the network

---

### Post by ShadowKingpin on 2008-12-29
I entered in the code in terminal and entered in my password.  Nothing happened.  I went to the 2 computers at the top (for the network manager) and nothing came up under wireless.

---

### Post by balloooza on 2008-12-29
can you right click the icon and see if there is a "enable wireless"
and also make sure that all the switches for wireless are on.
tell me if there is a "enable wireless' option, and also check if there are any networks, somtimes it just takes a minuit to refresh

---

### Post by ShadowKingpin on 2008-12-29
Never found "Enable Wireless".  I have no clue why.  I waited for a little and nothing has popped up.  Anywhere else I can find "Enable Wireless"?

---

### Post by balloooza on 2008-12-29
I forgot too tell you, after you make these changes, just wait about 45 seconds before you check for wirelesss networks, and also can you tell me if the wireless is a two position switch, or a push on push off thing, if it is a push on push off thing, look for networks, then push it again, wait 45 seconds then click on the "two computer" icon (network manager applet"

to use wireless two things need to be in place, 
1. the driver needs to be installed (that was what you did before)
2. the wireless radio needs to be on

so can you post what you have done, in detail from the time you ran the "ooooooo run "sudo modprobe -r ndiswrapper" command, because I think it should be working now

---

### Post by ShadowKingpin on 2008-12-29
2 switch?  Push on or push off?  I'm clueless on this.  Sorry bro.  You mean the switch in front of my laptop?

---

### Post by cdnLilwolf on 2008-12-29
> **ShadowKingpin said:**
> 2 switch?  Push on or push off?  I'm clueless on this.  Sorry bro.  You mean the switch in front of my laptop?

Presumably there is a picture of two computers more or less linked together or sometimes it is a globe of sorts.  When I have a wireless connection on my Aspire One I have signal strength bars.  They are all found on the panel or in the Mickeysoft world, what you would call a task bar.

Right-click on that icon for more options.

---

### Post by balloooza on 2008-12-29
yes, dose the switch on the front of your laptop have a spring in it, or is it like a lightswitch (on or off)(sory if I am confusing you)
as i said,  i think it is working now, can you tell me, line by line what is in the drop down menue when you left click the network manager in the taskbar.

---

### Post by ShadowKingpin on 2008-12-29
When I right click on the 2 computers, the only options I have are: Enable Networking, Connection Information, Edit Connections, & About.  I'm not finding anything about more information.

---

### Post by ShadowKingpin on 2008-12-29
> **balloooza said:**
> yes, dose the switch on the front of your laptop have a spring in it, or is it like a lightswitch (on or off)(sory if I am confusing you)
as i said,  i think it is working now, can you tell me, line by line what is in the drop down menue when you left click the network manager in the taskbar.

It has a spring in it.  It's not a on or off switch.

---

### Post by balloooza on 2008-12-29
OK some of this stuff is not working, but, I know that driver works,

Is networking enabled, this means is the box, when you RIGHT click the network icon is the "enable networking box checked
[ATTACH]98012[/ATTACH]

you make sure that you have the wireless switch on, and then once you are positive it is on (a light will be on) wait 45 seconds then LEFT click (normal click) on the applet, and tell me what it says, make sure it is not a right click, post what it says. screenshot of what you should be posting
[ATTACH]98013[/ATTACH]

My desktop is a little different, because I use the netbook remix, but it is still ubuntu

---

### Post by balloooza on 2008-12-29
sory about this problem, just remember that I have the driver running right now.
run these two commands again
```
sudo modprobe -r ndiswrapper
```
```
sudo modprobe ath_pci
```
after you reply to the last post, try restarting your compputer, somtimes a refresh is good, and then try connecting to the network again.

---

### Post by ndefontenay on 2008-12-29
Had the Athero driver problem just yesterday.

I've installed the ndiswrapper thingy, downloaded the driver from internet ([www.wireless-drivers.com](www.wireless-drivers.com)), choosed the .inf.

The hardware was displayed as present then I tried to connect but it wouldn't work.

I did a reboot and as soon as I was in, I got a prompt for a password on my wireless network. I input it and I got connected.

There was another prompt for a password with a button accept and a button "deny". I tried plenty of passwords in it and it wouldn't go. I denied and it didn't ask anything more. Wireless still works.

Also, your ethernet network has priority over the wireless. The icon won't display in the task bar until you unplug it.

---

### Post by balloooza on 2008-12-29
> **ndefontenay said:**
> 

Also, your ethernet network has priority over the wireless. The icon won't display in the task bar until you unplug it.

that might be just what what our problem is, but still try a reboot.
I think that we are overlooking somthing big, I wish our thread had more acivity, we need some fresh ideas. I am confident that the driver currently installed should work, but a reboot might clear up anything that is running and preventing you from accesing.

---

### Post by ShadowKingpin on 2008-12-30
So.....nothing is happening.  I believe the problem is that my WiFi light will not go on in the front of the laptop.  I keep trying to get it to turn on but it won't for some odd reason...

---

### Post by ShadowKingpin on 2008-12-30
> **balloooza said:**
> OK some of this stuff is not working, but, I know that driver works,

Is networking enabled, this means is the box, when you RIGHT click the network icon is the "enable networking box checked
[ATTACH]98012[/ATTACH]

you make sure that you have the wireless switch on, and then once you are positive it is on (a light will be on) wait 45 seconds then LEFT click (normal click) on the applet, and tell me what it says, make sure it is not a right click, post what it says. screenshot of what you should be posting
[ATTACH]98013[/ATTACH]

My desktop is a little different, because I use the netbook remix, but it is still ubuntu

I do not have any Wireless options.  I've tried unplugging the ethernet for a while, I search for "Enable Wireless" I can't find anything.

---

### Post by balloooza on 2008-12-31
can you post the results of
```
 sudo lshw -C network
```
this will tell me what driver you are using so i can see if you installed it correctly

---

### Post by ShadowKingpin on 2008-12-31
*-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:59:6a:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=69.89.254.153 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:4e:26:a5:4a:32
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by balloooza on 2008-12-31
i found your problem, the driver was not succesfully installed run
```
sudo modprobe -r bridge
```
then
```
sudo modprobe ath_pci
```
then restart

when you are back up and running check if there are any networks to connect to (left click the network icon), if not make sure the wireless is on (flick the switch once and wait 45 seconds) then see if there are any networks. if still not right click the networking icon and make sure "enable networking" is checked. then wait 45 seconds. if still not post
```
 sudo lshw -C network
```
again

---

### Post by ShadowKingpin on 2008-12-31
*-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:59:6a:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=69.89.254.153 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:82:e9:e3:f3:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by balloooza on 2008-12-31
did you do the things that I told you to in the post?
is there still no network

---

### Post by ShadowKingpin on 2008-12-31
I did what you told me.  I input the first code, then the 2nd, then restarted, then waited 45 seconds and nothing happened, then input the 3rd code and gave you the info.

---

### Post by balloooza on 2008-12-31
can you tell me the output of
```
modinfo ath_pci
```
then also run
```
sudo modprobe -b ath_pci
```
this is getting confusing, and a little hard, because it should be working once the module loads (modprobe)

---

### Post by balloooza on 2008-12-31
I found a guide:
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)
I can help you through it, and download this file instead of the wget one, then put it in your home folder (your name in the places bar) it looks like our drivers were outdated (maby)
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

---

