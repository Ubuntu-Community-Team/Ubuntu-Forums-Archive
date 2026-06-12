---
title: "Help please"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by noober on 2009-02-22
So I have been looking and reading up on Ubunto for a couple of weeks now.  I thought I understood how to do everything but evidently I dont.  I did a complete switch on my laptop it is a amd compaq presario v2000 with the ati 200m.  Every thing seems to work fine except I cant go on the internet.

Now to be honest I dont even know how to search for available wireless connections.  Everyplace I think wouldve done it, ask me to put addresses in and security fields etc.  

So please help me set up.
Thanks
noober

---

### Post by llamabr on 2009-02-22
Hi.  If you're logged into gnome, you should be able to click that little black computer in your upper right task bar, and see available wireless networks.

Also, as a more positive reminder, you'll get more people to read your post, and likely get quicker and better answers, if your subject title is more informative.

Hope that helps.

---

### Post by mkvnmtr on 2009-02-22
Start by looking for Hardware Drivers. You should find it on the upper panel. If not it will be under system administration. Look and see if you have a driver to enable.

---

### Post by noober on 2009-02-22
All the drivers say enabled that I see.  The network computer symbol in the top right corner brings me to a screen with a wired, wireless, mobile tab.  there is no connections showing up under the wireless though.

---

### Post by llamabr on 2009-02-22
This is hardly ever a driver problem.

Do you know the network exists?  What options are given when you click the little computer at the top right?  Do you see any available networks?

---

### Post by uprooted on 2009-02-22
find out what type of wireless card you are using, ensure that the manufacturer has a free driver for linux, if not you might have to use a restricted driver before your internet works, check system >> administration >> drivers , and see if there is a driver that needs to be installed or turned on, same goes for poor screen resolution with some nvidia drivers, just putting it out there...

---

### Post by noober on 2009-02-22
ok exactly when the left click the two computers on the top screen i get
wired network
auto etho
wireless networks
vpn connections>
connect to hidden wireless network
create new wireless network


The top three are faded and not clickable

Hope that clarifies

---

### Post by noober on 2009-02-22
yes the networks exsist cause its my network.  Worked fine before.

---

### Post by noober on 2009-02-22
> **uprooted said:**
> find out what type of wireless card you are using, ensure that the manufacturer has a free driver for linux, if not you might have to use a restricted driver before your internet works, check system >> administration >> drivers , and see if there is a driver that needs to be installed or turned on, same goes for poor screen resolution with some nvidia drivers, just putting it out there...

The only driver that it says needs to be turned on is ati/amd propietary FGLRX graphic driver.  I tried turning it up but it didnt go through I presume cause it couldnt download.

---

### Post by carml on 2009-02-22
Try to go to System->Administration->Network then unlock,select the wireless flag: there you should be able to select the wireless network you want to use.:)

---

### Post by steveneddy on 2009-02-22
> **llamabr said:**
> Hi.  If you're logged into gnome, you should be able to click that little black computer in your upper right task bar, and see available wireless networks.

[COLOR=Red][B]Also, as a more positive reminder, you'll get more people to read your post, and likely get quicker and better answers, if your subject title is more informative.
[/B][/COLOR] 
Hope that helps.

I suppose you can get onto the internet via a wired connection?

You have plugged an Ethernet cable into your laptop, right?

---

### Post by ja660k on 2009-02-22
possibly you havnt set up your wireless, for ubuntu it works a little different then with windows,

you need to install drivers yourself

---

### Post by noober on 2009-02-22
> **carml said:**
> Try to go to System->Administration->Network then unlock,select the wireless flag: there you should be able to select the wireless network you want to use.:)

I dont see anywhere to unlock anything

---

### Post by noober on 2009-02-22
> **steveneddy said:**
> I suppose you can get onto the internet via a wired connection?

You have plugged an Ethernet cable into your laptop, right?

No I havent will the drivers then beable to download?

---

### Post by ja660k on 2009-02-22
well 
do you still have windows on the computer? ie dual boot?

if not
you need to work out what driver you need. for that you run in terminal

lspci
and
iwconfig

and paste the result of it please

---

### Post by noober on 2009-02-22
> **ja660k said:**
> well 
do you still have windows on the computer? ie dual boot?

if not
you need to work out what driver you need. for that you run in terminal

lspci
and
iwconfig

and paste the result of it please

I do not still have windows on this computer

Here is the result and thanks for your help in advance

magna@Mobile-Launcher:~$ lspci 
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
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller 
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller 
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller 
magna@Mobile-Launcher:~$ 





Iwconfig

magna@Mobile-Launcher:~$ lspci 
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
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller 
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller 
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller 
magna@Mobile-Launcher:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 

magna@Mobile-Launcher:~$

---

### Post by steveneddy on 2009-02-22
Plug an Ethernet cable into the laptop to see if it connects.

This should be an automatic connection.

What type of wireless router are you using?

Is the wireless internet connection on the router turned on?

---

### Post by llamabr on 2009-02-22
This is hardly ever a drivers problem.

How do you know that the network even exists?  Can you verify with another machine that it's actually there?

Can you physically plug your laptop into the router?  It should connect automatically from there.

---

### Post by sandyd on 2009-02-22
read this
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by noober on 2009-02-22
> **llamabr said:**
> This is hardly ever a drivers problem.

How do you know that the network even exists?  Can you verify with another machine that it's actually there?

Can you physically plug your laptop into the router?  It should connect automatically from there.


It exsists because it is mine. I can access it from my pda.
Ive pluged it in now. Hard line works but, I need wireless.

I read your thing Carlee but when I go to my drivers, it only list the ati/amd fglrx graphics driver, which i clicked activate and it is still listing there and saying not activated even after reboot.

---

### Post by noober on 2009-02-22
> **carlee said:**
> read this
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I am doing this right now and after the sudo ./ndiswrapper_setup  it asks me for my password in the terminal, but wont let me type I tried pasting my password but that didnt work either

---

### Post by noober on 2009-02-22
I am using the update manager and updating everything I will then try again after a reboot.

---

### Post by llamabr on 2009-02-22
It's unlikely for this to be a driver problem, nor do you need a wrapper.

So the pda sees it and is able to connect?

---

### Post by noober on 2009-02-22
Yes, I assure you it is not the network.  PDA works xbox works. I am definately new to Ubunto but the update is 259 files...could that be it??

---

### Post by llamabr on 2009-02-22
Wouldn't hurt to do an update.

Sounds like a permissions issue.  What's the output of ifconfig?

---

### Post by noober on 2009-02-22
Give me a minute on ifconfig after i installed everthing the broadcom driver showed up under the hardware drivers

---

### Post by matteojg on 2009-02-23
> it asks me for my password in the terminal, but wont let me type I tried pasting my password but that didnt work either

This is normal behaviour and is simply a built in security feature: When you type a password in a terminal the cursor does not move but the password *is* entered after you press return.

---

### Post by noober on 2009-02-23
Sorry I havent posted ifconfig yet.  It does show up wireless networks now.  But it will not connect mine is secured and I know the passwords. One of the ones showing up isnt secured and i cant connect to that one either.  What is Security ring in ubunto?

---

### Post by grappler on 2009-02-23
I agree with other comments: this is almost certainly not a driver problem. Your iwconfig seems to show that the wireless card is recognised.

I have found wicd much better at handling wireless connections than the gnome network manager. 

```
sudo apt-get install wicd
```

in a terminal with a working internet connection of course - ie ethernet cable plugged in.  That's easy to configure for passwords etc. It will appear as an icon in the panel.

---

### Post by noober on 2009-02-23
ifconfig

magna@Mobile-Launcher:~$ sudo apt-get install wicd
[sudo] password for magna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd
magna@Mobile-Launcher:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd
magna@Mobile-Launcher:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:2c:90:56  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2c:9056/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2418 (2.4 KB)  TX bytes:5655 (5.6 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:71:39:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-71-39-91-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

magna@Mobile-Launcher:~$ 


wicd goes thru and then says couldnt find package wicd

---

### Post by noober on 2009-02-23
Ok so I reinstalled this morning then updated, then activated the broadcom driver, then updated agian, rebooting all the way through.

Then did ndiswrapper using [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)


And it worked.  So thanks to everybody.:p

---

