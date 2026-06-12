---
title: "RTL8187 with ndiswrapper (network manager disabled)"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by panurge77 on 2007-07-06
(I have not worked it all out in hardy yet but I hope to do that soon)

rtl8187 native driver is prone to hang the connection at high traffic. Here's a workaround.

Frist thing first, download the driver. Some posts on the forum told me win98 driver is the only way to go. I trusted them, but you can check it out for yourself and test others, that is, if you don't trust our friends. You can grab an old version here, with win98 included (though the site says only ME/2000/XP).
[URL="http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html"]http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html
[/URL]

Now install ndiswrapper
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```You can also install ndisgtk package, which will give you a a simple gnome gui for managing ndiswrapper, but I wouldn't recommend it. It'll tell you it can't install the driver when there's nothing wrong with it, it'll tell you the driver is not installed when it is... I'm not one to point fingers, but don't trust the gui for that matter, he's a punk and I'm not playing games about my connection.

Digression gone, now you can disconnect your native driver:
```
sudo rmmod rtl8187
```And blacklist it.
```
sudo gedit /etc/modprobe.d/blacklist
```Add this line somwhere:
```
blacklist rtl8187
```Stop network manager. You can keep it if you like it, but then I can't tell you how to make it work, so let it go and don't be sad, she'll be back if you're really meant to be together.
But you're not. You dont want Network Manager because: 1) it won't work; 2) even if it works, not using it brings you 2 advantages: a) you'll be connected when the X fails to start and you want to dist-upgrade your alpha testing release praying that the devs fixed it already in a new package; b) you won't have to deal with that old fat keyringer manager asking you that silly same everyday, all that paranoia about hackers in the forest, and where was it that you sleep last night, let's end it here.

Stop network manager
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
   sudo /etc/dbus-1/event.d/25NetworkManager stop
```Create two files with only the word 'exit' in them. These files are:
```
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
```Go to System > Preferences > Sessions and uncheck the subject.

Now you can configure you connection the honoured way, with virtue and a text editor:
```
sudo gedit /etc/network/interfaces
```You want to see something like this. Just write down that dirty words where the ***** go:
```
auto wlan0
iface wlan0 inet dhcp
wireless-key ******
wireless-essid ******
```Or you can go to System > Administration > Network and ask your vassals to do it.
(This really works with wep, but now I'm using wpa and I don't know how to make it work at boot. I need to restart the connection every boot. Anyone got wpa in perfect start?

Get into the folder you have extracted the windows driver you'll be using and:
```
sudo ndiswrapper -i Netrtuw.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Add ndiswrapper here
```
sudo gedit /etc/modules
```Word have reached me just now that you won't need to reboot your beloved machine. Instead, just tell it softly:
```
sudo /etc/init.d/networking restart
```This simple command will tell you about it all
```
iwconfig
```Now if something went wrong, I happen to have a disclaimer for you just in case:
1- I'm exiled on Windows, so I wrote everything from memory and google. Neither one being completely sworn to truth, I therefore renounce all my rights and privileges in the matter of disputing over whatever.
2- I should be working as this poor government of my country pays me to; instead I'm eating chocolate and typing this guide. As I'm being completely irresponsible for your benefit only, I consider myself in position of asking you any forgiveness necessary.


Finally, here's the [launchpad bug link]("https://bugs.launchpad.net/ubuntu/+bug/124801") if you want to help with the connection hanging problem with rtl8187 natve driver.

---

### Post by kevdog on 2007-07-06
Great guide

PS: you can change the title of the thread if you want!

---

### Post by atlfalcons866 on 2007-07-06
mine is connected to my router but cant connect to the internet

---

### Post by Jexel on 2007-07-06
OMG it works!!! Now I just gotta test it to see if it breaks :S but nevertheless ndiswrapper works!!! I'm connected to the internet!!!!!!!!

Thank you sooo much!

But I got one final question. There's no icon displaying any connectivity so how would I be able to check if I'm actually connected to the internet without having to open up a browser?

---

### Post by kevdog on 2007-07-06
The icon comes from network-manager-gnome that was disabled.  The only other way I know how to do what you want is to type:
iwlist scan

That will show you something known as quality -- ie 49/100.  This is kind of your bar meter.  It will also show you other routers in the area.

If you need to know if you are actually connected to the wireless router,
ifconfig
gives the information.  Of course there is always the good old ping command that would tell you if you can reach the internet.:p

---

### Post by atlfalcons866 on 2007-07-06
this might be a kernel bug but i was using 2.6.20-16-generic. The wireless wouldnt work on the internet. i switched back to 2.6.20-15-generic and it is perfect

---

### Post by panurge77 on 2007-07-07
> **Jexel said:**
> But I got one final question. There's no icon displaying any connectivity so how would I be able to check if I'm actually connected to the internet without having to open up a browser?
I use iwconfig
[QUOTE=atlfalcons866]this might be a kernel bug but i was using 2.6.20-16-generic. The wireless wouldnt work on the internet. i switched back to 2.6.20-15-generic and it is perfect[/QUOTE]
Hmm... dunno.
It works here with 16
Try adding ndiswrapper to /etc/modules

---

### Post by kevdog on 2007-07-07
Just a clarification please,

With network manager disabled, no icon appears in the system tray correct??

If someone was a novice, other than typing the command to start network manager at the command line, could this program be started within the menu?? (System->Administration->Network)???

Ive heard people just recommending to uninstall the program, but Ive heard this is quite a feat!  Before recommending this method I would like to ensure that network manager couldnt be started easily or people would get frustrated by a GUI /or icon saying no network connected in the system tray!

---

### Post by panurge77 on 2007-07-07
I'm not sure I get your point. Do you want to start network manager just for the icon? Until edgy we had no icon.

System->Administration->Network will lead to gui configuration for /etc/network/interfaces

If disabled or uninstalled, the icon wont be there anyway

---

### Post by smoocat on 2007-07-08
Obrigado, panurge77!  Finally a method that bypasses Network Manager (I'd been suspecting it was the culprit, but couldn't figure out a way around it).  Is ndiswrapper still the recommended method, if the native rtl8187 driver gave me connectivity?

Also, one question before I try your guide:  Since I'm using KDE/Kubuntu as opposed to Gnome, would I need to make any changes to the steps you outlined or would it be pretty much the same?

Thanks in advance for bearing with me ;)

---

### Post by panurge77 on 2007-07-09
I disabled networmanager because I couldn't make it work with nidswrapper driver and linux native driver was dropping my connection. If you have good experience with the native driver, might as well stay with networkmanager. If you want only to disable networkmanager and stay with native driver, it's up to you, no reason for going to ndiswrapper if your connection works.

BTW, I posted the problem about connection dropping with rtl8187 driver so others who had this problem can share their info, if any.
[https://bugs.launchpad.net/ubuntu/+bug/124801](https://bugs.launchpad.net/ubuntu/+bug/124801)

And well, I'm sorry, but I know very little about kde. I guess you would use kate instead of gedit? Does it use the same networkmanager app?

---

### Post by smoocat on 2007-07-09
> **panurge77 said:**
> I disabled networmanager because I couldn't make it work with nidswrapper driver and linux native driver was dropping my connection. If you have good experience with the native driver, might as well stay with networkmanager. If you want only to disable networkmanager and stay with native driver, it's up to you, no reason for going to ndiswrapper if your connection works.

BTW, I posted the problem about connection dropping with rtl8187 driver so others who had this problem can share their info, if any.
[https://bugs.launchpad.net/ubuntu/+bug/124801](https://bugs.launchpad.net/ubuntu/+bug/124801)

And well, I'm sorry, but I know very little about kde. I guess you would use kate instead of gedit? Does it use the same networkmanager app?

My issue was the same--the native driver was dropping my connection (like crazy sometimes).  Couldn't make ndiswrapper work, either, but I assumed I just had the wrong driver or something (never seriously considered networkmanager to be the culprit).  I'm going to try and figure out how to do this with KDE now.  I'll post any changes (if any) I needed to make.

---

### Post by panurge77 on 2007-07-09
Good luck with kde
And take a look on the launchpad if you'd like to help. There's already an answer from a dev asking for some logs.

---

### Post by smoocat on 2007-07-10
Worked like a charm!  Only difference for KDE: after disabling networkmanager, I went into Adept package manager and removed knetworkmanager, which is KDE's graphical frontend for the utility.

Also, in editing /etc/network/interfaces, I only achieved connectivity after commenting out (#) everything but wlan0.  I had eth0, eth1, eth2 sections that came before it.  After that, dropped connections became a thing of the past--no drops all day long.  Beats my XP connectivity by a longshot, and that's with supposedly native drivers!

Thanks, Panurge.  Good night, até amanhã..

---

### Post by kevdog on 2007-07-10
Panurge,

Ever tried the native r8187 drivers with the aircrack patch??
[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

---

### Post by panurge77 on 2007-07-10
> **kevdog said:**
> Panurge,

Ever tried the native r8187 drivers with the aircrack patch??
[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

No. I just bumped into this page yesterday or the otherday but did not really read it all. Have you tried it?
Looks like there's some dirty work needed. I dont know the tricks about kernel and drivers. Do you need to compile the whole kernel or only the driver modules?

---

### Post by kevdog on 2007-07-10
I dont have a rtl8187 card, so even if I was able to compile and patch the necessary files, I counldn't tell you if it would work!

---

### Post by alex77 on 2007-07-16
> **panurge77 said:**
> You want to see something like this. Just write down that dirty words where the ***** go:
```
auto wlan0
iface wlan0 inet dhcp
wireless-key ******
wireless-essid ******
```

Will this work if I want to use WPA? Or is this just for WEP?

---

### Post by panurge77 on 2007-07-16
I'm sorry, but I don't know much about WPA. I only tried WEP, my access point is too oldschool.

---

### Post by kevdog on 2007-07-16
That configuration will not work with WPA only wep.  Consult the stick at the top of the networking forums by weiman.  This is the best WPA tutorial available if you want to perform a manual configuration.  You can do something else if you want network manager to handle the WPA connection with dhcp -- network manager can not do static IP addresses

---

### Post by Jexel on 2007-07-17
on a side note are there any advantages of putting the word "exit" inside the files /etc/default/NetworkManager and /etc/default/NetworkManagerDispatcher compared to just going to System=>Preferences=>Sessions and just unchecking Network Manager?

---

### Post by panurge77 on 2007-07-17
Good question. I did not know you could disable it just unchecking the sessions config. I took that piece about disabling networkmanager from [help.ubuntu.com]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")

---

### Post by swarup on 2007-07-18
I have a Novatel Wireless Ovation U720 USB modem (an aircard) which is what I use to go online with. It is a Sprint aircard connection. Up until now, I've been the only person using the aircard. But I would like to get a wireless router (the Kyocera KR1 EVDO Mobile Router) so other computers in the house will also be able to go online using the aircard. It is known that the Novatel aircard modem works will with the Kyocera. All the computers are running on Feisty Fawn. And I have purchased three WG111v2 Netgear wireless adaptors, one for each computer. My question is: The Kyocera mobile router is $155 from the internet. If I purchase it, am I going to be able to configure the WG111v2 Netgear adapters to work with Feisty? There has been so much discussion about this back and forth, that I am somewhat confused. Some write on the forums that they got great success, and others say it is not working at all. On the basis of your experience, should I be able to configure the Netgear WG111v2 to work with Feisty using the tutorial at the beginning of this thread? Thanks!

---

### Post by panurge77 on 2007-07-18
If it uses realtek8187, I don't know why it wouldn't work.  But I have NO experience with the WG111v2 Netgear adapter. My wireless is onboard.

---

### Post by swarup on 2007-07-19
> **panurge77 said:**
> If it uses realtek8187, I don't know why it wouldn't work.  But I have NO experience with the WG111v2 Netgear adapter. My wireless is onboard.

How does one know if it uses realtek8187 or not?

---

### Post by panurge77 on 2007-07-19
Well, you could google it, check the device specs on its box or manual or homepage. You can also ask windows or other os that is using it correctly. 
Yeah, boring work. There should be an easy way. Is it a usb device? Probably. So type this in the term:
```
lsusb
```
You should see something like this
```
Bus 005 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. 
```

---

### Post by swarup on 2007-07-19
> **panurge77 said:**
> Well, you could google it, check the device specs on its box or manual or homepage. You can also ask windows or other os that is using it correctly. 
Yeah, boring work. There should be an easy way. Is it a usb device? Probably. So type this in the term:
```
lsusb
```
You should see something like this
```
Bus 005 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. 
```

Yes, it is a usb device. Here is the lsusb output:   

Bus 001 Device 016: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

It is a Netgear device, that I already knew.  But that doesn't mean it won't work with RTL8187, does it?

---

### Post by panurge77 on 2007-07-19
Sorry, my bad. That command did not help us much. Let's try google then...
ok. I did a quick search and did not find much, but this might help.
[http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html](http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html)
From what I see in this site, it does not look as if this netgear adapter uses rtl8187 chipset.

---

### Post by swarup on 2007-07-21
> **panurge77 said:**
> Sorry, my bad. That command did not help us much. Let's try google then...
ok. I did a quick search and did not find much, but this might help.
[http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html](http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html)
From what I see in this site, it does not look as if this netgear adapter uses rtl8187 chipset.

Some people have written me on other sites saying that in fact the Netgear WG111v2 does use the rtl8187 chipset. So I'll have to find out more about this. If it does use that chipset, then do you think your tutorial would be a good option for me?

---

### Post by panurge77 on 2007-07-22
If so, then yes

---

### Post by swarup on 2007-07-23
> **panurge77 said:**
> If so, then yes

It looks like the WG111v2 does use that chipset. When I plug in my Netgear WG111v2 here is the output data that I get--

Here is the relevant lshw output:

```
description: Generic USB device
product: NETGEAR WG111v2
vendor: NETGEAR WG111v2
physical id: 2
bus info: usb@1:2
version: 1.00
serial: 00146CB02782
capabilities: usb-1.10
configuration: driver=rtl8187 maxpower=500mA speed=12.0MB/s
```

So it says that the "driver=rtl8187" -- that is the point, isn't it? 

There is a fellow who writes to the Ubuntu support forum by the name dcstar, who uses this WG111v2 with the native network manager of Ubuntu. And he says it works fine like that. 

He (dcstar) writes, "My RTL8187 based WG111v2 seemed to work "out of the box" with Feisty (once I plugged it into a USB port with sufficient power capability), and it came up in the nm-applet." His posting can be read here: [http://ubuntuforums.org/showthread.php?t=504014&page=2](http://ubuntuforums.org/showthread.php?t=504014&page=2)

Mine hasn't seemed to have been able to get on line yet that way, but it may be close.

My Kyocera K1 aircard router arrived, and I hooked my evdo aircard into the router, and plugged the WG111v2 into the laptop, and tried the native connection as dcstar suggested. As I say it hasn't connected. I have a feeling the WG111v2 is still not properly configured-- although it may be close. Ubuntu recognizes that a WiFi connection is there on my USB port.

I ran dmesg to see what sort of output it gives. Please take a look and see if you can tell me where the connection is failing. I really can't fully comprehend what all the below means. But I see references to Wiphy3, with attempts to connect. And then after that, Wiphy4. And then an attempt to connect. And then Wiphy 5. Please kindly see below and let me know what you think:

```
[260015.392000] usb 1-1: new full speed USB device using uhci_hcd and address 15
[260015.560000] usb 1-1: configuration #1 chosen from 1 choice
[260016.644000] wmaster0: Selected rate control algorithm 'simple'
[260016.644000] wiphy3: hwaddr 00:0f:b5:d4:59:90, rtl8187 V1 + rtl8225
[260023.688000] wmaster0: Does not support passive scan, disabled
[260023.728000] wlan0: starting scan
[260025.752000] wlan0: scan completed
[260045.808000] wlan0: starting scan
[260047.832000] wlan0: scan completed
[260067.884000] wlan0: starting scan
[260069.908000] wlan0: scan completed
[260089.964000] wlan0: starting scan
[260091.988000] wlan0: scan completed
[260212.040000] wlan0: starting scan
[260214.064000] wlan0: scan completed
[260334.084000] wlan0: starting scan
[260336.108000] wlan0: scan completed
[260413.064000] usb 1-1: USB disconnect, address 15
[260420.316000] usb 1-1: new full speed USB device using uhci_hcd and address 16
[260420.480000] usb 1-1: configuration #1 chosen from 1 choice
[260420.480000] airprime 1-1:1.0: airprime converter detected
[260420.480000] usb 1-1: airprime converter now attached to ttyUSB0
[260420.480000] usb 1-1: airprime converter now attached to ttyUSB1
[260420.484000] usb 1-1: airprime converter now attached to ttyUSB2
[260420.484000] airprime 1-1:1.1: airprime converter detected
[260420.488000] usb 1-1: airprime converter now attached to ttyUSB3
[260420.488000] usb 1-1: airprime converter now attached to ttyUSB4
[260420.488000] usb 1-1: airprime converter now attached to ttyUSB5
[260420.492000] airprime 1-1:1.2: airprime converter detected
[260420.492000] usb 1-1: airprime converter now attached to ttyUSB6
[260420.492000] usb 1-1: airprime converter now attached to ttyUSB7
[260420.492000] usb 1-1: airprime converter now attached to ttyUSB8
[260420.496000] airprime 1-1:1.3: airprime converter detected
[260420.496000] usb 1-1: airprime converter now attached to ttyUSB9
[260420.496000] usb 1-1: airprime converter now attached to ttyUSB10
[260420.500000] usb 1-1: airprime converter now attached to ttyUSB11
[260689.720000] usb 1-1: USB disconnect, address 16
[260689.720000] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[260689.720000] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[260689.720000] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[260689.720000] airprime 1-1:1.0: device disconnected
[260689.720000] airprime ttyUSB3: airprime converter now disconnected from ttyUSB3
[260689.720000] airprime ttyUSB4: airprime converter now disconnected from ttyUSB4
[260689.720000] airprime ttyUSB5: airprime converter now disconnected from ttyUSB5
[260689.720000] airprime 1-1:1.1: device disconnected
[260689.720000] airprime ttyUSB6: airprime converter now disconnected from ttyUSB6
[260689.720000] airprime ttyUSB7: airprime converter now disconnected from ttyUSB7
[260689.720000] airprime ttyUSB8: airprime converter now disconnected from ttyUSB8
[260689.724000] airprime 1-1:1.2: device disconnected
[260689.724000] airprime ttyUSB9: airprime converter now disconnected from ttyUSB9
[260689.724000] airprime ttyUSB10: airprime converter now disconnected from ttyUSB10
[260689.724000] airprime ttyUSB11: airprime converter now disconnected from ttyUSB11
[260689.724000] airprime 1-1:1.3: device disconnected
[260754.552000] usb 1-1: new full speed USB device using uhci_hcd and address 17
[260754.720000] usb 1-1: configuration #1 chosen from 1 choice
[260755.804000] wmaster0: Selected rate control algorithm 'simple'
[260755.804000] wiphy4: hwaddr 00:0f:b5:d4:59:90, rtl8187 V1 + rtl8225
[260762.836000] wmaster0: Does not support passive scan, disabled
[260762.872000] wlan0: starting scan
[260764.896000] wlan0: scan completed
[260784.952000] wlan0: starting scan
[260786.980000] wlan0: scan completed
[260807.036000] wlan0: starting scan
[260809.064000] wlan0: scan completed
[260829.088000] wlan0: starting scan
[260831.112000] wlan0: scan completed
[260847.304000] usb 1-1: USB disconnect, address 17
[261288.920000] usb 1-1: new full speed USB device using uhci_hcd and address 18
[261289.088000] usb 1-1: configuration #1 chosen from 1 choice
[261290.172000] wmaster0: Selected rate control algorithm 'simple'
[261290.172000] wiphy5: hwaddr 00:0f:b5:d4:59:90, rtl8187 V1 + rtl8225
[261298.676000] wmaster0: Does not support passive scan, disabled
[261298.716000] wlan0: starting scan
[261300.740000] wlan0: scan completed
swarup@swarup-laptop:~$
```

If you think it would work better using the tutorial you suggest on this thread, please let me know.

---

### Post by panurge77 on 2007-07-24
The problem I had with the native driver was it would hang at high traffic. It was mostly ok for browsing, and it connected as it should, out of the box. But it would hang the connection if I open some file transfers or a torrent.

Did you set your password at NetworkManager? What kind of  secutiry you use? I guess my ndiswrapper method only works with WEP. I only have WEP on my old access point, and I really dont know about WPA. I'm sorry, but I can't sort you dmesg log either.

If you're planning to use the wep, you can try my workaround, I hope it helps some.

---

### Post by swarup on 2007-07-25
I got the whole system up and running with the Linux native driver. I'm using the standard native network manager. I haven't done any heavy duty file downloads yet, but it is working really well for browsing. I have a novatel u720 evdo aircard, connected to a kyocera K1 mobile router, and am using the Netgear WG111v2 adaptor which is using the RTL8187 chipset. 

The only question I have at this point is, that when the aircard is connected directly into my laptop's USB type 1 port, I get download speeds of 1.2 mb/sec on [www.speedtest.net](www.speedtest.net). But when I plug my aircard into the router and hook up my Netgear WG111v2 adapter, then the download speed decreases to 700 kbps. Any idea why this would be? Could it be the driver?

---

### Post by darkhacker902 on 2007-08-11
I have ubuntu ultimate and it has KwifiManager and the such like, if I follow this, will I be able to use Kwifi manager or any other utility for wireless?

I originally had ubuntu feisty, and tried this with no success, but I was wandering if anything would be different with ubuntu ultimate.

---

### Post by Genecks on 2007-08-14
swarup, I think it's Ubuntu's fault. I don't know what's up, but I seem to be able to use the wg111v2 with Puppy Linux. I downloaded a dotpup, and installed that to get it working. I personall think it's not only the driver, ndiswrapper, etc. but it's also the way Ubuntu is designed. Maybe it's because of how Debian-type systems work.

Darkhacker, I suppose not. This tutorial is for stopping networkmanager from screwing up one's network connection.

It's funny how people yammer aobut wg111v2 working out of the box. It does, but when you start doing certain web activities, it doesn't work anymore. I think I was one of the few on this forum to state that using ndiswrapper is better than the native support long ago.

---

### Post by darkhacker902 on 2007-08-17
Ok I war drive and the such like here so I need help:

Iwconfig Shows that the adapter is on, but not connected to a wifi network.

Wireless Assistant Shows my ESSID. Linksys. But wont let me connect. The problem is that My wifi network is open, and a lot of my networks I connect to are the same.

I tried deleting the parameter "wireless key:" from the /etc/networking/resources and then i tried <blank>, then leaving it empty, and it never connects :(. 

What i Do? 


I can say that it is working however, because when I went to connect to another wifi network with a key, it worked like no other and I was vary pleased. I dont necessarily want to put a WEP key on this network so bypassing that at all will be a blessing.

Thanx to all who have helped me, and thanx Mucho for this thread.

---

### Post by panurge77 on 2007-10-06
Try configuring it with the gui.
Go to System > Administration > Network

---

### Post by azaotl on 2008-01-04
Thank you very much!!!!!! Now my card is working!!!!!! and without reboot the pc--- AWSOME!...
I admire people like you! thanks for your time!!!:)

---

### Post by valen75 on 2008-02-20
Impresionante!
Espanihs people, este método si funciona, después de tres dias ya tengo conexión!
Muchas gracias!

---

### Post by jss43 on 2008-04-28
Excellent!  

I tried compiling my own drivers and wasn't having any success so I tried using ndiswrapper as a last resort and it worked like a charm.  Before I'd have to restart my wireless several times a day and now it's rock solid.

It even works fine in hardy with network manager, which makes life much easier.

---

### Post by Zenith270 on 2008-04-28
Okay, I'm using the NetGear WG111v2... which had dodgy performance in Gutsy until I installed ndiswrapper and the windows drivers, where I *finally* got it to work decently if I configured the connection manually via etc/network/interfaces - it would not auto-connect to the detected network, no matter how many times I tried.

Then, I upgraded to Hardy this afternoon, and it worked for a hot second but is now broken. If I have Network Manager set to roaming, it will auto-detect the network and will appear to "connect" but with 0% signal, and will not connect in reality, as the connect info lists 0.0.0.0 in all fields, and the internet doesn't work.

When I try to manually configure the connection as before, nothing seems to happen. The device is detected, and my connection settings are accepted, but they don't seem to get the connection functioning.

I've checked and NDISWRAPPER is listed as the driver for the device, which is good, but I can't seem to figure out if maybe something else is getting in the way, in a similar manner as the SSB module getting in the way of the NDISWRAPPER module for user's using wlan with broadcom chipsets. Does anyone know if I should be blacklisting/rmmod'ing something to get this thing working in Hardy?

I will try to OP's step by step instructions, although I'm slightly hesitant about getting rid of Network Manager. But I have a couple questions in case this doesn't work out:

Is there another network manager-type program that would perhaps work better with the USB dongle than Ubuntu's network manager? The drivers used to work flawlessly, and my network is fine, so I'm guessing the problem has to be somewhere on the Ubuntu side.

And, is there something else I should perhaps be trying to get the WG111v2 to work?

---

### Post by infecticide on 2008-05-08
I am having the same issue since updating to Hardy, the wireless driver loads as evidenced by dmesg:

[19941.102786] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[19941.229848] usb 2-9: reset high speed USB device using ehci_hcd and address 6
[19941.365913] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,04/04/2006,5.1221.0412.2006) loaded
[19944.348957] wlan0: ethernet device 00:15:af:0f:17:e2 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0BDA:8187.F.conf
[19944.348988] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[19944.352692] usbcore: registered new interface driver ndiswrapper
[19954.359784] wlan0: no IPv6 routers present
[19968.579223] eth1: no IPv6 routers present




I have a static IP address set in /etc/network/interfaces which is also set correctly but there is 0 packet traffic.

I think this may be a kernel related problem but that's just a guess.

---

### Post by Doc Horn on 2008-06-04
works like a charm, also for Archlinux here :)

thanks a lot!

---

### Post by infecticide on 2008-06-04
Which driver are you using?  (link please) :D 

What is your lsusb information?
> 
Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp.


---

### Post by staubio on 2008-06-12
If some of you believe network manager to be the culprit, has anyone tried wicd? It isn't in the ubuntu library out of the box but seems to work fine, but I'm only getting slightly better results than I was with nm, though I'm still using the realtek driver with the NetGear device.

---

### Post by goofeyfoot on 2008-06-15
Just a comment.

I am using an AMD 64 distro.

I have the 8187 wireless card.

I used the following method to work around. And so far, so good.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Would like to know whether others have been similarly satisfied.

Best regards.

Michael

---

### Post by panurge77 on 2008-06-28
Hello all. I've been away from linux for a long time. I just installed hardy now, 64 bits for a change. Hope I'll get it all working again.

Someone said above that ndiswrapper is now working with networkmanager. It does not work here. It freezes everything. So let's try the manual stuff again. Just got to remember how to set up the WPA stuff.

---

### Post by panurge77 on 2008-06-29
Very frustrating indeed. I get a kernel freeze when I modprobe ndiswrapper.

Goofey: are you using 8187L or 8187B? Which driver did you use?

---

### Post by kevdog on 2008-06-29
panurge

Welcome back, you were missed.  Are you working with Hardy 64 bit.  A lot of users having issues with kernel freezes.  Not exactly sure if its ndiswrapper related or something else.  Seems to be more a kernle problem.

---

### Post by panurge77 on 2008-06-29
Hello kevdog. Maybe this 64bits is really problem, but it shouldn't be so. The bad thing is I used my last CD-R so I can't check the 32bits kernel now... or maybe I can... I can try an usb install. Anyway, I really wanted to stay with 64bits. It's time we leave 32 behind. 

I'll try the 32bits anyway so I can update the original post. A lot of people use realtek and this stuff is always a problem. Buying another card is not a problem resolved. The sad thing is there are those native drivers that never work. It's the same thing since rtl8180... You install linux and your internet seems to work but it's always failing. You look into launchpad and there's always someone saying the problems are fixed and it's never true. 

It's the only thing that I have a hard time setting up. I hold to windows because of games, but there's lots of people who are not into gaming and don't use linux because of these little (or very big) stuff, like wireless. You get a notebook with wireless problems and the non-geek will not give linux another try.

---

