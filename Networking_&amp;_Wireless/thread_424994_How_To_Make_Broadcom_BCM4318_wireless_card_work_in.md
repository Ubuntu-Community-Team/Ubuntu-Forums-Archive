---
title: "How To: Make Broadcom BCM4318 wireless card work in feisty"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by sohaibma on 2007-04-27
Wireless support in Feisty is fantasic and better than ever.
Setting up my BCM4318 card was quite easy and done in a few simple steps. 
Here's how I did it:

**Note:** I am using BCM4318 [AirForce One 54g] 802.11g card but this should work on any BCM43xx.


Go to System > Administration > Synaptic Package Manager

Then search for BCM43xx-fwcutter and install it (right click, and select Mark for installation. then press apply).

During installation, it will ask to fetch the appropriate drivers. Allow it to fetch the drivers.

After the installation is complete, go to System > Administration > Network. Then go to wireless properties and select your wireless network.

This is how it worked with me.
I hope it works for you too.
Good Luck

---

### Post by Izaksly on 2007-04-27
it worked for 2 minutes, when i clicked on one of the wireless networks i have around here, it said it was connected, but i didnt have internet.
and then, it stopped working, and i didnt find any wireless connections,

---

### Post by sohaibma on 2007-04-27
you need to provide some more details.
are you using bcm4318?
are you using roaming mode in wireless settings?

try to use the windows driver that came with your card instead of fetching from the internet.  If you have installed the driver in windows the driver is probably in the following directory:
WINDOWS > system32 > Drivers. (it is probably a file named bcmwl5.sys)

i have attached my windows drivers.
hope this helps

---

### Post by ShdwNova on 2007-04-29
Worked perfectly for me on two different computers both using Broadcom 4318's. 
Thx sohaibma. I've been trying to get wireless to work just how I like it since Breezy.

---

### Post by Guranic on 2007-04-29
I got my bcm4318 working with this, but it is not too stable yet.. I have D-link dsl-g604t AP/dsl-router and I had dns problems with Edgy (and rt61 card), I had to put static address and dns to get it work. Now I have Asus laptop and it has bcm4318 internal wlanif. It is working but sometimes almost everyday it makes router crash. I have to boot router and after that everything works again. I'm using roaming mode, is it problem for the bcm4318? I got the laptop only few days ago so I haven't tested it with other accesspoints.

Other weird thing is that network-manager-applet gives about 50% link strength and if I start Gnome panel applet it shows more than 95% strength... Router is less than 10 meters away. All suggestions will be nice to hear.

---

### Post by sohaibma on 2007-04-29
Mine works fine in Roaming Mode, and i've tried it with 4 or 5 different accesspoints.The only problem I encounter is that I have to make 2 to 3 attempts before it connects. There have been no router crashes as well. I think you should try it with other accesspoints before reaching a conclusion for the router crashes, as it may only occur with the current router that you are using.


> Other weird thing is that network-manager-applet gives about 50% link strength and if I start Gnome panel applet it shows more than 95% strength... Router is less than 10 meters away. All suggestions will be nice to hear.
I haven't tried them both on feisty, network-manager-applet works fine for me. but when i was using edgy I was using both, and they both showed different strengths like yours. So I don't think there's anything to worry about. but I would recommend you to stick to the network-manager-applet.

I hope this helps.

---

### Post by Guranic on 2007-05-01
Thanks for sharing your experiences. I really want to stick with network-manager applet because it is pretty convenient with laptop and different networks. I found a thread from here which told to comment out all interfaces from /etc/network/interfaces, now I'm trying that.. For me the whole networking problem is not a big deal as far as it is working like right now. The driver and firmware could be better, though. 

I will give a try with other accesspoints soon. I'll post if problem occurs only with d-link router.

---

### Post by lenix on 2007-05-02
I think that bcm4318 is officially unstable with bxm43xx:

[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

Have you tried ndiswrapper?:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by dumbjaw on 2007-05-02
Whew, I'm glad you guy's are talking about this I got here just in time. 
I had mine working in Edgy using ndiswrapper, upgraded to Feisty today and nothing. I'm going to try the roaming advice and repeat attempts. hopefully that will work. It seems as though every computer is different, since Breezy some have luck with fwcutter some with ndiswrapper and some with bcm43xx.

---

### Post by Floppyjoe on 2007-05-02
I was using a bcm4318 with ndiswrapper on my laptop in Edgy Eft. When I updated to Feisty Fawn I just needed to enable roaming mode to get it to work. It works with the bcm43xx driver(with firmware from [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net)) or the ndiswrapper but when I use the bcm43xx driver the computer seems to be flakey. Also the speed isn't as fast.

---

### Post by dumbjaw on 2007-05-03
I think I have discovered other problems. Roaming is on and wireless light turns off and on. If I scan nothing comes up. /ect/modules is NONE EXISTENT, can't write to it in gedit.  Still reading as eth1 though. I'm also having problems with fwcutter not reading bcmwl5.sys, weird.  I'll try again tomorrow when I can find an ethernet. Oh, and any problems with OpenOffice? It's doing the same thing it did to me on my first install of Dapper, locking up. Thanks for the firmware link -- I'll work on it tomorrow.

---

### Post by bedfojo on 2007-05-03
Guys, I'll repeat what I said on another thread.  I have a Broadcom bcm4138 in my Acer Aspire 3613WLMi.

Edgy wireless was fine with ndiswrapper but was borked under Feisty.

I had to completely remove ndiswrapper and network-manager.

Then compile myself the latest ndiswrapper (1.42). See the ubuntu wiki for instructions.

Reinstall the windows drivers.

Install wicd instead of network-manager. You'll need to download from their site (sorry no link since I'm not on my home machine) as it's not in the repos.

Now all OK for me, with much better speeds than using the bcm43xx driver which is limited to 11Mb/s.

Only problem is that the system can cope with a hidden SSID, but otherwise OK.

---

### Post by sohaibma on 2007-05-04
the only time i got ndiswrapper to work was in edgy, and that too wasn't a reliable solution. This is because it often did not connect. BCM43xx-fwcutter works smoothly on feisty, no i haven't faced any problems at all.

please note: i used the copy from the repos.

---

### Post by dumbjaw on 2007-05-08
This is insane. I completely uninstalled ndiswrapper. Using the native bcm43xx everything works it seems faster than before but if I change networks it can see EVERYTHING but won't connect.

 Cell 01 - Address: 00:90:4C:7E:00:6E
                    ESSID:"Qdoba Cherry Street"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-55 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 36ms ago
          Cell 02 - Address: 00:17:9A:4C:BA:AC
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=67/100  Signal level=-80 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 100ms ago
          Cell 03 - Address: 00:14:6C:18:37:B8
                    ESSID:"SubwayHotSpot"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-83 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 68ms ago
          Cell 04 - Address: 00:0D:97:00:1D:7B
                    ESSID:"TulsaMetroNet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=67/100  Signal level=-80 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 1428ms ago

Right now I'm posting from Qdoba cherry street everything else is a bust. Any one see any problems that I don't?

---

### Post by Guranic on 2007-05-09
It seems that my problems were more keyring related.. Still using native driver with fwcutter, but after solved keyring problem NMapplet connects right away in roaming mode. It is not solid stable yet, thouhgt.. Sometimes I have to choose my accesspoint from NMapplets list after boot because it won't connect at first try. But it works stable enough for daily usage...

---

### Post by sohaibma on 2007-05-17
Guranic, I face the same problem as you but it occurs rarely.
I have to reboot too, to solve the problem.

Please inform me if you find a solution for this problem.

---

### Post by therantinggeek on 2007-05-21
> **sohaibma said:**
> Wireless support in Feisty is fantasic and better than ever.
Setting up my BCM4318 card was quite easy and done in a few simple steps. 
Here's how I did it:

**Note:** I am using BCM4318 [AirForce One 54g] 802.11g card but this should work on any BCM43xx.


Go to System > Administration > Synaptic Package Manager

Then search for BCM43xx-fwcutter and install it (right click, and select Mark for installation. then press apply).

During installation, it will ask to fetch the appropriate drivers. Allow it to fetch the drivers.

After the installation is complete, go to System > Administration > Network. Then go to wireless properties and select your wireless network.

This is how it worked with me.
I hope it works for you too.
Good Luck

I have confirmed this works.  A wired LAN connection is needed to grab the package bcm43xx-fwcutter - during installation, let it fetch the drivers and install them for you.  Then, pick your network connection.  If successful, you should be prompted to enter the WEP/WPA key.  Once you enter this, you should be seeing a signal strength monitor in your system tray.

Kudos to the original author who started this thread...I only wish I found this a LONG time ago!

---

### Post by sohaibma on 2007-05-25
thanks for helping out thereantinggeek, i forgot to mention this
You need to download the BCM43xx-fwcutter package using wired internet connection (cause it requires internet).

enjoy ;)

---

### Post by neekz on 2007-06-01
:( I can't find it on my list. I think I have all the repositories checked but it doesn't show up the closest thing I see is "bmconf".  

  Some help will be greately appreciated.

 EDIT- Sorry I just wrote it in search and it showed up.

---

### Post by gunbladeiv on 2007-06-02
it works with just fine.  I did with the synaptic package manager.  but i dont know what this is.  Can someone figure this thing out?

gunblade@gunblade-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 76:8A:CC:02:19:9C
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=60/100  Signal level=-77 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 6412ms ago

---

### Post by gunbladeiv on 2007-06-02
im having trouble with my broadcom 4318.  Yes i did post that my wireless light up.  But my bcm seem like unstable.  It can get connected to the access point.  and when it get connected,suddenly it'll turn off.  The lights didnt light up.  Can someone help me with this problem? Do i use the wrong driver?

---

### Post by ffderrick on 2007-06-02
I have an Hp 5003cl laptop and this method worked for me.
After a reboot, I let the network manager applet run for longer than seemed necessary and finally I was asked for my wireless password.
This should work with other Hp 5000 series laptops.

---

### Post by gunbladeiv on 2007-06-02
where can i download the tarball of netwrk manager?
i lost mine due to stupid thing i've done,now my eth0 and wireless wont work..please help me... URGENT

---

### Post by sohaibma on 2007-06-03
search for the software on [http://packages.ubuntu.com](http://packages.ubuntu.com) and download it manually from there.
make sure you also download and install the dependencies for network manager.

---

### Post by voam on 2007-06-06
> **sohaibma said:**
> Wireless support in Feisty is fantasic and better than ever.
Setting up my BCM4318 card was quite easy and done in a few simple steps. 
Here's how I did it:

**Note:** I am using BCM4318 [AirForce One 54g] 802.11g card but this should work on any BCM43xx.


Go to System > Administration > Synaptic Package Manager

Then search for BCM43xx-fwcutter and install it (right click, and select Mark for installation. then press apply).

During installation, it will ask to fetch the appropriate drivers. Allow it to fetch the drivers.

After the installation is complete, go to System > Administration > Network. Then go to wireless properties and select your wireless network.

This is how it worked with me.
I hope it works for you too.
Good Luck

I have used this method. It worked on my Linksys router but when I try to connect to a 2wire router I am not able to connect. Well, with WEP disabled on the router I am able to connect intermittently, but more often than not, I am unable to connect. The weird thing it is entirely stable using the Linksys router. Unfortunately, the laptop ( an Acer Aspire 3000) needs to work with the 2wire router as I used the linksys just to make sure the drivers are working before I give it back. When I delievered the system suddenly wireless does not work. Now I have the laptop and the router to try and fix the problem. But so far all I have had is frustration...:(

---

### Post by BrandonG777 on 2007-06-13
Let me try to make this stupid simple

Open a Terminal
 sudo apt-get install ndiswrapper-common
 sudo apt-get bcm43xx-fwcutter
 Yes

Try to connect to your network. I use Kubuntu so it's a slightly different process but that should work for any varient of Ubuntu

---

### Post by richieboy on 2007-06-16
THANKS, SOHAIBMA!!!:popcorn:

after i upgraded to feisty i went crazy with wireless.  now it works.  but...how do i enable roaming mode?  i have network-manager and network-managet-gnome installed according to synaptic but i can't open them from cli or from menu. is it the same thing as network selector panel applet? i know it's a little off topic, but could you please guide me?
thanks,
rich

---

### Post by sohaibma on 2007-06-19
network-manager applet is the one that you can see next to the battery icon on the top gnome-panel. It is just an applet to make things easier and more user friendly. It cannot be accessed from the menu.

to select a network or to switch to roaming mode you have to go to system > administration > network, and do it from there.

I hope this helps you.

---

