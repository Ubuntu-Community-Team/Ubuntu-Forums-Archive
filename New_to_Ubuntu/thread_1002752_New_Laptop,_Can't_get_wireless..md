---
title: "New Laptop, Can't get wireless."
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Phospholipid on 2008-12-05
Hi everyone, 
This is my first post on this forum and I wish I was writing it on my new laptop, but alas, this is not the case. 

I just got a Dell Mini 9, and the hardware looks awesome. it came installed with Ubuntu Hardy Heron. I went to connect to my home wireless network when I found it wasn't in the drop down list on the desktop, I went to manual configuration. I failed to configure manually so I went back to the desktop and found network manager had dissapeared from the tool bar. I returned it there by right clicking and choosing it from the menu. 

The new network manager has no wireless connection on it! when I click I get a greyed out wired connection and manual configuration. 

I looked around the forums finding that I should try lshw to see if my device is up, but when I try it says no such command!

does anyone have any ideas what I need to do to get it working? 

Thanks for any advice or tips. This is the first linux computer of owned myself and I'm eager to get the best out of it.

---

### Post by newbee70 on 2008-12-05
> **Phospholipid said:**
> Hi everyone, 
This is my first post on this forum and I wish I was writing it on my new laptop, but alas, this is not the case. 

I just got a Dell Mini 9, and the hardware looks awesome. it came installed with Ubuntu Hardy Heron. I went to connect to my home wireless network when I found it wasn't in the drop down list on the desktop, I went to manual configuration. I failed to configure manually so I went back to the desktop and found network manager had dissapeared from the tool bar. I returned it there by right clicking and choosing it from the menu. 

The new network manager has no wireless connection on it! when I click I get a greyed out wired connection and manual configuration. 

I looked around the forums finding that I should try lshw to see if my device is up, but when I try it says no such command!

does anyone have any ideas what I need to do to get it working? 

Thanks for any advice or tips. This is the first linux computer of owned myself and I'm eager to get the best out of it.

I'm a newbee 2 so take this with a grain of salt.


when you looked at the grayed out connections did you see an unlock box at the bottom?

the next question if you right click on the monitor icon upper right toolbar, does it show that your connection has been "enabled" activated?

---

### Post by uberlube on 2008-12-05
1) Did you buy the laptop brand new from Dell with Ubuntu installed by them? 

2) What kind of wireless card does the laptop have?

---

### Post by iponeverything on 2008-12-05
right click on the toolbar -- go to add and readd the "notification area"

after the network manager is back, if you still don't see your router. Try changing the channel of your wireless router to something less than 10.

---

### Post by Phospholipid on 2008-12-05
Wow you're quick! thanks. 

iponeverything: Ive tried sorting out the tool bar with no success, I'll try changing the router's wireless channel. but I don't understand what the difference will be between channels?

Uberlube: 
(1)The laptop had Ubuntu preinstalled. 
(2)All I know of the wireless is that it's there. Manual just says "Internal WLAN, WWAN (Mini-Card).

Newbee70: my connection is enabled. and the grayed connection is on the left click of the network manager. When I firt booted it up there was a list of wireless signals there too but now it's gone.

---

### Post by swisscow on 2008-12-05
Try rebooting, go into the bios at boot and check to see if wireless is enabled - my eeepc sometimes the wireless switches itself off

---

### Post by chrisod on 2008-12-05
Also, since it's a brand new Dell you should have free Dell support if you need it. Although it's probably not a bad idea to come here first :)

---

### Post by Phospholipid on 2008-12-05
Hi guys,
I've tried a couple of other things now, but I still cant even tell if my wireless card is enabled at the hardware level. 
lshw is 'command not found' 
iwconfig says:
lo          no wireless extensions

eth0        no wirless extensions

eth 1       IEEE 802.22 Nickname:" "
            access point not associated

does this mean to say that my eth1 will be my wireless card?

---

### Post by Ayuthia on 2008-12-05
You are correct that it is going to be eth1.  Since it looks like you are using the Terminal, can you post the results of:
```
uname -a
lshw -C network
lspci -nn
sudo iwlist scan
```
The first command will help us see what kernel version you are using and if it is 32 or 64-bit (Since it came from Dell, I am guessing it will be 32).  The second command (hopefully it will work this time) is to see what you card is trying to use, and the third command lists out your PCI devices.  It will help us identify your wireless card.  I think that your card is a Broadcom 4312 (14e4:4315), but I just want to confirm it.  The last command is to look for wireless sites.

The kernel version will help us see if you have run any updates lately.  The driver for the Broadcom card has been working off and on in Hardy based on the kernel version.

---

### Post by Phospholipid on 2008-12-05
ayuthia:
heres the first three: 
> 
jak@jak:~$ uname -a
Linux jak 2.6.24-19-lpia #1 SMP Tue Jul 29 14:02:05 UTC 2008 i686 GNU/Linux
jak@jak:~$ lshw -C network
bash: lshw: command not found
jak@jak:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2382]
02:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Unknown device [197b:2381]
02:00.3 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2383]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)


---

### Post by Phospholipid on 2008-12-05
and the second half:
> jak@jak:~$ sudo iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:DF:CD:81:62
                    ESSID:"tengky84"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-15 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD001CDFCD81621021000642656C6B696E1023000F463544373233302D342D763830303010240007575053303030311042000E32303831393732333030343032371054000800060050F204000110110020463544373233302D340000000000000000000000000000000000000000000000100800020084
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1C:DF:B1:9D:7B
                    ESSID:"KARL AND SANDY"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-49 dBm  Noise level:-15 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD9A0050F204104A00011010440001021041000100103B0001031047001000000000000000011000001CDFB19D7B1021001242656C6B696E20436F72706F726174696F6E10230009463544373233302D3410240007412E30302E31311042000B42453730313634373531341054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1C:DF:38:75:2F
                    ESSID:"Flat23"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-32 dBm  Noise level:-15 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 

there were a few more but the forum thought I had 10 images in this code were I'm only allowed 8, who knew this had images!
My router is the ESSID 'Flat 23' would you mind explaining to me some of what's shown here? 
Any ideas as to why I don't have lshw? 
Hope this helps.

---

### Post by Ayuthia on 2008-12-05
Ok.  It looks like you do have a 4312 card (at least it will be when your system is up to date).  By any chance, do you have a working wired connection?  If so, you might want to get the system updated and that should get it back up and running.  If I recall correctly, 2.6.24-21 is where some of the bigger fixes were made.

By any chance, did you try:
```
sudo iwlist scan
```I am curious if it was able to find any wireless sites.  If you are concerned about the sudo command in there, it is being used to force the system to scan again.

EDIT:I must have been typing too slow.  Just saw the post above.

---

### Post by Ayuthia on 2008-12-05
```
ESSID:"Flat23"
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:5/5 Signal level:-32 dBm Noise level:-15 dBm
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 
```
This is showing the information for your router.  It is showing that that the mode is Managed so it is functioning as a router.  In some cases you will see ad-hoc connections which are wireless cards that are allow other computers to connect so that they can be networked.

The frequency is the channel that your router is sending out.  Each channel has its own set of frequencies so that if there are more than one router around using the same channel, you can change yours so that you don't receive interference.

The quality is the signal strength.  The Broadcom STA (wl) driver tends to show signal ratings from 0-5 instead of using 0-100 like most others.

The remaining lines talk aout about the encryption that your router is using.  In this case, you are using WPA2.  You might try this guide:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
or
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wieman01](http://ubuntuforums.org/showthread.php?t=202834&highlight=wieman01)

They provide some help with WPA2.  I have not had a chance to do too much with WPA2 because my router does not support it.

---

### Post by Phospholipid on 2008-12-05
I can change the encryption if that would help me, but I'm not seeing how to actually connect via the wireless sytem. 
I'll try to cable up and update now and I'll post my results A.S.A.P.
Cheers

---

### Post by Ayuthia on 2008-12-05
> **Phospholipid said:**
> I can change the encryption if that would help me, but I'm not seeing how to actually connect via the wireless sytem. 
I'll try to cable up and update now and I'll post my results A.S.A.P.
Cheers

You might try connecting without encryption just to see if you can connect.  Once you have encryption removed you can try the following:
```
sudo iwconfig eth1 essid Flat23
sudo dhclient eth1
ping -c1 www.ubuntu.com
```

---

### Post by newbee70 on 2008-12-05
> **Phospholipid said:**
> Wow you're quick! thanks. 

iponeverything: Ive tried sorting out the tool bar with no success, I'll try changing the router's wireless channel. but I don't understand what the difference will be between channels?

Uberlube: 
(1)The laptop had Ubuntu preinstalled. 
(2)All I know of the wireless is that it's there. Manual just says "Internal WLAN, WWAN (Mini-Card).

Newbee70: my connection is enabled. and the grayed connection is on the left click of the network manager. When I firt booted it up there was a list of wireless signals there too but now it's gone.

good the guru's are here;

Now we get to learn something from the pro's, on how to troubleshoot this problem right. 

sit back and take notes:  Thanks guys!

---

### Post by Phospholipid on 2008-12-05
Thanks ayuthia
I wired up, got OS updates. Then took off encryption from my router, followed your terminal commands, and I can get online! hurrah.
Only a slight problem now though, the GUI doesn't seem to realise that I have a connection. I brought up the Network monitor, mouseover message says: "Network Connection: eth1", which is great. when I go to configure en error message comes up saying: "The interface does not exist". Whats going on?

---

### Post by Ayuthia on 2008-12-05
> **Phospholipid said:**
> Thanks ayuthia
I wired up, got OS updates. Then took off encryption from my router, followed your terminal commands, and I can get online! hurrah.
Only a slight problem now though, the GUI doesn't seem to realise that I have a connection. I brought up the Network monitor, mouseover message says: "Network Connection: eth1", which is great. when I go to configure en error message comes up saying: "The interface does not exist". Whats going on?

I think I am going to need a little help from others on this one.  I am currently in Gentoo and compiling updates (It has been running for a couple hours now--418 updates) and I am using openbox with a manual connection right now.  This means that I cannot access my Ubuntu partition right now.  At the pace the compiling is going, it has at least another hour or so.  Sorry.

Just a guess right now, but it almost sounds like roaming is currently not enabled.  I think that you change that through System->Administration->Network (or something like that).

---

### Post by Phospholipid on 2008-12-05
Thanks all, I learned some new terminal goodness (it's more efficient than GUI!) 
I have sorted it out!!!!
Ayuthia: your last post got me playing with that menu again, I enabled automatic mode, et voila! it found a load of wireless signals, great! 

Still wondering why I dont have lshw though. any ideas on that? 

Thanks again everyone who posted!

---

### Post by Ayuthia on 2008-12-05
> **Phospholipid said:**
> 

Still wondering why I dont have lshw though. any ideas on that? 

Thanks again everyone who posted!

Glad to see it working!  As for lshw, can you check and see if it is in /usr/bin:
```
ls -l /usr/bin/ls*
```The file should be there.  The only thing that I can think of is that there is some kind of permission issue.

---

### Post by Phospholipid on 2008-12-05
No it's not in there. Theres a few other commands that work but lshw is'nt present. What ways can I get hold of new commands?

I'm still getting used to the terminal commands, I can't remember any of them! apart from navigational commands.

cheers

---

### Post by Ayuthia on 2008-12-05
> **Phospholipid said:**
> No it's not in there. Theres a few other commands that work but lshw is'nt present. What ways can I get hold of new commands?

I'm still getting used to the terminal commands, I can't remember any of them! apart from navigational commands.

cheers

Interesting.  I am not for sure about what package lshw is found.  It comes with the base install.  This might be because Dell packaged it.  I saw that you did not have the -generic attached to the end of your kernel version.  Is that what comes with the laptop or did you install a different version?

---

### Post by Phospholipid on 2008-12-07
I'm using the Dell version. 
I've got lshw now, what I did was to go on the terminal type in aptitude to get the package manager then search for lshw in the search bar. 

Outside of aptitude though I seem to be having real trouble installing programs. I'm trying to get Netbeans IDE installed but I'm finding it difficult to install the JDK.

---

