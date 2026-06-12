---
title: "[SOLVED] No Wireless connection"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by jkyahoo101 on 2008-07-18
Ok when I go to system/administration/network I see the ppoe connection but no wireless. I have the right drivers installed on the other machine but I can't seem to configure the wireless. Anyone know why?

---

### Post by jkyahoo101 on 2008-07-18
Does anyone know why? I am really desperate. I have to have the internet up on the other pc tonight.

---

### Post by jkyahoo101 on 2008-07-18
Ok now I am wondering something. If I can not get the network manager to work should I just install wicd? I just need a yes or no answer. I am very desperate and I need to get this internet going by tonight or my dad is going to switch back to XP!

---

### Post by jkyahoo101 on 2008-07-18
Ok I installed Wicd and it still doesn't work. It doesn't show any networks and it says not connected at the bottom. What do I do? I am about to give up.:(  I can't believe no responses yet.:(

---

### Post by sandeepy on 2008-07-18
wht's ur card config ?

---

### Post by sandeepy on 2008-07-18
this could be of help :

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feist](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feist)

you can follow from here based on your ubuntu flavor

---

### Post by Sealbhach on 2008-07-18
Hi, please show the result of this in the terminal

```
lshw -C network
```

It will help people on the forums to understand your problem.



.

---

### Post by jkyahoo101 on 2008-07-18
> **Sealbhach said:**
> Hi, please show the result of this in the terminal

```
lshw -C network
```

It will help people on the forums to understand your problem.



.

It said warning you should run this program as super-user.

The card is a d-link WUA-2340 USB Adapter. I run sudo ndiswrapper -l and it says the driver is installed and device is present. But when I open up wicd there are no networks.

---

### Post by sandeepy on 2008-07-18
> **jkyahoo101 said:**
> It said warning you should run this program as super-user.
then do :

sudo lshw -C network

---

### Post by jkyahoo101 on 2008-07-18
It says two things really fast and then does nothing.

---

### Post by sandeepy on 2008-07-18
> **jkyahoo101 said:**
> It said warning you should run this program as super-user.

The card is a d-link WUA-2340 USB Adapter. I run sudo ndiswrapper -l and it says the driver is installed and device is present. But when I open up wicd there are no networks.
did you try rebooting ? or restarting /etc/init.d/network ?

---

### Post by jkyahoo101 on 2008-07-18
I rebooted my system but I don't think that is what you are talking about so I am going to say no. How do I do that?

---

### Post by Sealbhach on 2008-07-18
Just searching on the forums I found this:

[http://ubuntuforums.org/showthread.php?t=822062&highlight=WUA-2340+USB+Adapter](http://ubuntuforums.org/showthread.php?t=822062&highlight=WUA-2340+USB+Adapter)

with a link to this:

[http://www.spy-hill.com/help/wifi/WUA-2340.html](http://www.spy-hill.com/help/wifi/WUA-2340.html)

It seemed to solve the problem there.

Messy stuff, by the looks of it but can be done.

Hope this helps.

.

---

### Post by Tigin on 2008-07-18
hmm may be u can tell us something about your system . like 32bit or 64bit and the brand and model of your network card .

for becoming a super user : 
go to  system>preferences>main menu>system tools> ?** cannot find the word should be something like ROOT CONSOLE mark the box next to it so you will have it on your applications menu click on it and type the command


for me   it worked as "   [B]lshw -class network
[/B]   "

under root console

/cheers

---

### Post by jkyahoo101 on 2008-07-18
Ok I did that all the way up to this part.

To verify that the driver is installed:

    talisker: Drivers# ndiswrapper -l neta5agu : driver installed

Now how do I do the part under that. Do I just paste this into the terminal?

talisker: root# modprob ndiswrapper talisker:root# iwconfig wlan0 IEEE 802.11g ESSID: off/any Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated Bit Rate=108 Mb/s Encryption key: off Power Management: off Link Quality:0 Signal level: 0 Noise level: 0 Rx invalid nwid:0 Rx invalid crypt: 0 Rx invalid frag: 0 Tx excessive retries:0 Invalid misc: 0 Missed beacon: 0

I am very confused as you can see. My system is 32bit btw. The card is a d-link WUA-2340 USB Adapter as I said earlier.

---

### Post by Sealbhach on 2008-07-18
I think it should be:

```
sudo modprobe ndiswrapper
```

The he did

```
iwconfig
```

The he says he cofigured the wireless connection, I assume you can do that in Network Manager..??

Also, do
```

lsusb
```

to check if the device is seen as a USB device.

---

### Post by sandeepy on 2008-07-18
you might want to do :

/etc/init.d/network restart

 Signal transmission also appears to be 0. Just to be sure, is your wireless card manually switched on ?

---

### Post by jkyahoo101 on 2008-07-18
dale@dale-desktop:~$ sudo modprobe ndiswrapper
dale@dale-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dale@dale-desktop:~$ lsusb
Bus 002 Device 002: ID 05dc:a430 Lexar Media, Inc. (My jump drive) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 07d1:3a08 D-Link System (Guessing my adapter)
Bus 001 Device 001: ID 0000:0000

My device is plugged in and thats all I can do to turn it on.

---

### Post by sandeepy on 2008-07-18
well then i wud suggest not using ndiswrapper and going with some method ... sorry

---

### Post by jkyahoo101 on 2008-07-18
Well what should I do I have to have this working by tonight or my dad is going to switch back to XP.

---

### Post by Tigin on 2008-07-18
what is your wireless card ? brand and model please and tell us please you have 32 bit or 64 bit ubuntu ...

---

### Post by Sealbhach on 2008-07-18
Does it show a wireless connection in Network Manager?#


.

---

### Post by jkyahoo101 on 2008-07-18
My system is 32bit. The card is a d-link WUA-2340 USB Adapter.

I do not have the network manager. I have wicd and it shows no networks and I am positive my network is up.

---

### Post by Tigin on 2008-07-18
The windows driver you trying to use , is it 32 bit too ? or 64 bit , if it is 64 bit i believe you have to find and install XP 32 bit driver for the wireless card.


/cheers

---

### Post by jkyahoo101 on 2008-07-18
Yes the driver is 32bit and XP. And it says driver installed when I type sudo ndiswrapper -l

---

### Post by Sealbhach on 2008-07-18
You could try the automated ndiswrapper.

[http://www.easylinuxwifi.org/](http://www.easylinuxwifi.org/)

Just download it and extract it to your home folder.


This is how you use it (according to the help file that comes with it):

> Extract the dowloaded file (Which I guess you have already done ;) )
Place the folder Auto-NDIS-0.1 in your home directory
Open up a terminal and type the following command 'sudo python ~/Auto-NDIS-0.1/auto-ndis.py'
or open up a terminal and type 'su' and then the type 'python ~/Auto-NDIS-0.1/auto-ndis.py'
From that point on just follow directions and enjoy :)

Hope it helps.

.

---

### Post by jkyahoo101 on 2008-07-18
I tried that and my card isn't supported.

---

### Post by jkyahoo101 on 2008-07-18
I have good news. I got a list of wireless networks now. I just went into wicd preferences and typed wlan0 for the wireless interface. The problem is now I can't connect to my network. I typed in the right WEP key and everything.

---

### Post by Sealbhach on 2008-07-18
OK, found another webpage on Google which looks promising

[http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html](http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html)

it says:

> Now in a perfect world, you would be done now. However network-manager in hardy will not display any wireless networks for you to connect to. Rest assured your wireless adapter is installed and working, the problem is with network-manager.

So just follow the instructions relating to WICD and you should be there!


.

---

### Post by jkyahoo101 on 2008-07-18
That is the link I used to set up the drivers. Look in the post above also.

---

### Post by jkyahoo101 on 2008-07-18
I am so close. Does anyone know why it won't connect? My adapter must be working cause I see the networks.

---

### Post by Sealbhach on 2008-07-18
> **jkyahoo101 said:**
> I am so close. Does anyone know why it won't connect? My adapter must be working cause I see the networks.

Does it give you any hints at all?

You could have a go at this:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

.

---

### Post by jkyahoo101 on 2008-07-18
No.

---

### Post by jkyahoo101 on 2008-07-18
I think I am just going to buy a new usb adapter. What is a usb adapter that is guaranteed to work with Ubuntu with no problems and that works with a d-link router?

---

### Post by Sealbhach on 2008-07-18
> **jkyahoo101 said:**
> I think I am just going to buy a new usb adapter. What is a usb adapter that is guaranteed to work with Ubuntu with no problems and that works with a d-link router?

Probably better to start a new thread.

What happens when you do this?

```
sudo dhclient wlan0
```

.

---

### Post by jkyahoo101 on 2008-07-18
The weird part is it works perfect now. Wicd works flawlessly and connects and disconnects only when I tell it to. I guess I should of posted that it was working around 45min ago. Thank you everyone that tried to help me. I went through 5 distros trying to get wireless to work and this one is the only one that works for me. This is a very nice distro and very easy to use even for a windows user. I even installed Ubuntu inside of my XP install I liked it so much.

---

### Post by Sealbhach on 2008-07-18
> **jkyahoo101 said:**
> The weird part is it works perfect now. Wicd works flawlessly and connects and disconnects only when I tell it to. I guess I should of posted that it was working around 45min ago. Thank you everyone that tried to help me. I went through 5 distros trying to get wireless to work and this one is the only one that works for me. This is a very nice distro and very easy to use even for a windows user. I even installed Ubuntu inside of my XP install I liked it so much.

That's great news. Well done!

The only issue now might be that you need to do things next time you start up.

Enjoy Ubuntu! 

It would help others f you go to Thread Tools and mark this thread as solved.


.

---

### Post by jkyahoo101 on 2008-07-18
Ok. And I don't think I have to worry about rebooting because I already rebooted and that is when it started working right. And thanks again for all the help. This thread is officially solved.

---

### Post by sputnikkk on 2008-07-21
Another - WIcd success story - bump!

Wicd - FTW !

---

