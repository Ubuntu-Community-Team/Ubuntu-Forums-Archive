---
title: "Not connecting to Wireless Router"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by apostoj on 2007-03-30
Hello and forgive me if I posted in the wrong spot.
I am a total newbie to Linux.  I am so sick of MS,  I am trying to jump ship as fast as possible, after 16 years and they give us VISTA!!  What a puke of an OS.  1 gig of RAM reccomended...Please,  what crap

My problem, I have been battling the wireless connectivity.  
The card see's my router and every other router within a quarter mile...
I have a great signal. Even without any WEP or WAP security enabled,  I still can not connect to my network

What could be causing this?  I can not for the life of me get a grip on this.  I am a little frustrated.

Why will the card not accept access from the Router without any security.  I know it's something I am missing cause I am so new to this.

I beg you,  after trying to get a broadcom corp card to work for I am just about out of hair on my head. 

Oh please Linux Gods for give me for not leaving the dark side earlier, just one little accomplishment regarding getting my ubuntu box on the net would be so satisfying.

Sincerely
John

---

### Post by Floppyjoe on 2007-03-30
Can you tell us a bit more about your computer setup such as what wireless card you are using and what program you are using to connect.

---

### Post by apostoj on 2007-03-30
Dell Dimension 4400
Airlink101 AWLH3026T pci

I am clicking on the icon (looks like two networked computers with a red dot in the upper right hand corner.  When I click on that icon the spinning motion starts around the icons and then...nothing.
Then it ask for my wep 64 passphrase....

Am I missing a program, am I that lame that I am not worthy of the honor of Unbutu??

Ohhhh...yea...I am using the new 7.04 beta,  I loaded it on Tuesday of this week.

---

### Post by Floppyjoe on 2007-03-30
Make sure you disable all the network interfaces in System/Administration/Networking.

---

### Post by apostoj on 2007-03-30
I only have one network card in the box...
What else is there to disable.

If the OS see's the other networks then it's working right?
If my MN-730 router config util sees the the Ubunto box it should connect right?
What is stopping the Ubuntu box from getting access through the router?

this is the problem...:confused: 
the only thing under the System/Administration/Networking is a modem and the nic.
You want me to disable the PCI Wireless card?

---

### Post by Floppyjoe on 2007-03-30
> **apostoj said:**
> I only have one network card in the box...
What else is there to disable.

If the OS see's the other networks then it's working right?
If my MN-730 router config util sees the the Ubunto box it should connect right?
What is stopping the Ubuntu box from getting access through the router?

this is the problem...:confused: 
the only thing under the System/Administration/Networking is a modem and the nic.
You want me to disable the PCI Wireless card?

That is affirmative. Disable the PCI wireless card. This is required when you are using network-manager which comes installed with 7.04

---

### Post by apostoj on 2007-03-30
then what?  It's the only card on my system!!
There is no other nic

---

### Post by Floppyjoe on 2007-03-31
> **apostoj said:**
> then what?  It's the only card on my system!!
There is no other nic
Then network-manager will manage your network interfaces instead of the /etc/network/interfaces settings being used.

---

### Post by apostoj on 2007-03-31
I am Sorry SloppyJoe,  but I don't understand.
where is the network manager?

Under
System/admin/ I have two choices "Network" and "Network Tools".  I don't have know of 
Network-Manager.

God I feel like and idiot....

I have such a mental block with this MS BS I feel brain washed...am I not thinking right...
Dang it!!

---

### Post by Floppyjoe on 2007-03-31
> **apostoj said:**
> I am Sorry SloppyJoe,  but I don't understand.
where is the network manager?

Under
System/admin/ I have two choices "Network" and "Network Tools".  I don't have know of 
Network-Manager.

God I feel like and idiot....

I have such a mental block with this MS BS I feel brain washed...am I not thinking right...
Dang it!!
It is a little applet that shows up as an Icon on the top menu bar. It looks like some power bars/meter. It may show up as two networked computer screens if it using wired ethernet. Don't feel Bad. Hang in there. It doesn't make sense to deactivate your only network device but this is required for the network-manager applet to work properly.

---

### Post by Russty of Oz on 2007-03-31
Dont feel like an idiot, I am having the exact same problem, I just found this thread and I too can't work out what to do.

When I look under System/Administration I only find Network and Network Tools.  Under Network I have disabled the roaming in the wireless section and put in my network name and access key but I still can't connect to it.  This is on a laptop, and it has an orange light that comes on when connected to a network or it blinks when it can't connect, but it is not showing up at all!!!  My network shows up under the available networks, so why won't it connect :confused: 

Russty

---

### Post by Russty of Oz on 2007-03-31
Well I just disabled the networking using the two little computer icons, is that what we are suppose to do?   What next?

Russty

---

### Post by Floppyjoe on 2007-03-31
> **Russty of Oz said:**
> Well I just disabled the networking using the two little computer icons, is that what we are suppose to do?   What next?

Russty
No you are supposed to disable the network interfaces in System/Administration/Networking.

---

### Post by Russty of Oz on 2007-03-31
OK I have enabled networking and I have enabled the wireless networking and selected my network name and key, so where do we go now?  It can see the local networks but can't connect to anything?

Russty

---

### Post by Russty of Oz on 2007-03-31
[PHP]No you are supposed to disable the network interfaces in System/Administration/Networking.[/PHP]

Do you mean disable the wireless and wired networking in System/Administration/Network ?  Mine doesn't show up the word "Networking" just  Network and Network Tools.

---

### Post by Floppyjoe on 2007-03-31
> **Russty of Oz said:**
> OK I have enabled networking and I have enabled the wireless networking and selected my network name and key, so where do we go now?  It can see the local networks but can't connect to anything?

Russty
Did you also disable the network interfaces in System/Administration/Networking?

---

### Post by Floppyjoe on 2007-03-31
> **Russty of Oz said:**
> [PHP]No you are supposed to disable the network interfaces in System/Administration/Networking.[/PHP]

Do you mean disable the wireless and wired networking in System/Administration/Network ?  Mine doesn't show up the word "Networking" just  Network and Network Tools.
try network

---

### Post by Russty of Oz on 2007-03-31
Network shows the Wireless Connection and Wired Connection, when I disable these still nothing happens..   Do I need to reboot or something?

Russty

---

### Post by Russty of Oz on 2007-03-31
I will have to work on this again later, I have to go out now.  It just seems strange that all the wireless networks nearby show up and yet the computer won't connect to them?  Is there some driver or something I need to install to get my wireless to work?

Russty

---

### Post by Floppyjoe on 2007-03-31
I'm posting from my Vmware installation of Ubuntu Feisty. I am probably wrong about the disabling interfaces part here. Feisty comes built in with Network-manager. When I disable Network interfaces here it seems to not behave like it did in previous versions of Ubuntu.

---

### Post by apostoj on 2007-03-31
I am dizzy now...
Network-Manager is a now show.  

Ooofff....I need to listen to some killers for a minute...I can't get my head wrapped around my error.

This is nothing in the top bar except the menu and two computer icons with the red Euro stop sigh...thingy...thingy...I am saying thingy now...
What has happened to my skills.....
there was a time when...oh well...I blame that piece of dung vista:lolflag: 

Is network-manager an add on to the bar?
I am really fishing now....

---

### Post by Floppyjoe on 2007-03-31
This beta is behaving differently than previous versions of Ubuntu with respect to Network-Manager. You will probably need to disregard my previous suggestion to disable the network adapters in System/Administration/Network.  Man I hate eating crow!

There must be some other way to get your wireless connection working in Feisty Fawn. tell me what is the output of:
```
iwconfig
```
and
```
ifconfig
```
when you reactivate the network Interfaces in Sytem/Administration/Network?

---

### Post by apostoj on 2007-03-31
I am working on two machines.  One to communicate the other...well I am in some kind of misery....
I have and out put file but for some reason I can't get the darn thing over to the MS partician.
I should have it up in a minute or two....I am pooped...

---

### Post by apostoj on 2007-03-31
Ok, here it is...

bigdog@bigdog:~$ iwcongig
bash: iwcongig: command not found
bigdog@bigdog:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=81/100  Signal level:-44 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bigdog@bigdog:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)

ra0       Link encap:Ethernet  HWaddr 00:18:02:24:70:B5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50263 errors:9 dropped:0 overruns:0 frame:0
          TX packets:58353 errors:2 dropped:2 overruns:0 carrier:0
          collisions:7 txqueuelen:1000 
          RX bytes:4124878 (3.9 MiB)  TX bytes:13503 (13.1 KiB)
          Interrupt:17 

bigdog@bigdog:~$ 

I hope this helps....
I can not tell you how much I appreciate everything you and everyone does.  It seems so frustrating to a newbi,  I had the same problem with DOS 3.1 100 years ago so I never ever give up.  I love this stuff and I am on a mission.  Let's PARTY!!!

---

### Post by Russty of Oz on 2007-03-31
**Well this is what I got when I did those commands.**


peter@peter-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0

peter@peter-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:96:3C:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:2C:CB:2B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12753 errors:2 dropped:109 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15120 (14.7 KiB)  TX bytes:24254 (23.6 KiB)
          Interrupt:17 Memory:c8218000-c8218fff 

eth1:avah Link encap:Ethernet  HWaddr 00:12:F0:2C:CB:2B  
          inet addr:169.254.6.122  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:c8218000-c8218fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9128 (8.9 KiB)  TX bytes:9128 (8.9 KiB)

peter@peter-laptop:~$ 


[B]I hope this shows where the problem is!

This is actually not my laptop, but a friends who is in hospital at the moment, I told him I would get Ubuntu working for when he gets home.  I hope I can. 

Russty:) [/B]

---

### Post by apostoj on 2007-03-31
You guys didn't give up on us did ya?

---

### Post by Floppyjoe on 2007-03-31
> **apostoj said:**
> You guys didn't give up on us did ya?
I did some research and came up with this post apostoj:

[http://www.ubuntuforums.org/showpost.php?p=2155494&postcount=7](http://www.ubuntuforums.org/showpost.php?p=2155494&postcount=7)

According to this post Network-Manager and ralink based wireless network adapters are not currently compatible. He has a suggested work around but not much detail in the description.

---

### Post by Floppyjoe on 2007-03-31
> **Russty of Oz said:**
> **Well this is what I got when I did those commands.**


peter@peter-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0

peter@peter-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:96:3C:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:2C:CB:2B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12753 errors:2 dropped:109 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15120 (14.7 KiB)  TX bytes:24254 (23.6 KiB)
          Interrupt:17 Memory:c8218000-c8218fff 

eth1:avah Link encap:Ethernet  HWaddr 00:12:F0:2C:CB:2B  
          inet addr:169.254.6.122  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:c8218000-c8218fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9128 (8.9 KiB)  TX bytes:9128 (8.9 KiB)

peter@peter-laptop:~$ 


[B]I hope this shows where the problem is!

This is actually not my laptop, but a friends who is in hospital at the moment, I told him I would get Ubuntu working for when he gets home.  I hope I can. 

Russty:) [/B]

Russty I have read in another thread that when you have eth1:avah listed as a network interface that means you've been monkeying around with the iwconfig commands and may have a lot of trouble if it is possible at all to get wireless working. I don't have any personal experience with that so I can't confirm it myself.

---

### Post by apostoj on 2007-03-31
You have got to be kidding me......
I am totally bummed by this..

I have spent hours upon hours trying to get cards I have found on the internet that are supposed to work with this OS and...First it broadcom now it's......
Pfffff...
What the hell the computer see's the card it sees the network but some how some way the OS will not pass the proper info!!  this is to much man.....

I am just frustrated....

---

### Post by Russty of Oz on 2007-03-31
> Russty I have read in another thread that when you have eth1:avah listed as a network interface that means you've been monkeying around with the iwconfig commands and may have a lot of trouble if it is possible at all to get wireless working.

Well all I have done is to disable then enable the wired connection, I wouldn't even know how to fiddle with the commands!  This is a really fresh install I haven't changed any settings yet, I just found that it wouldn't connect to my network.

Should I do another install and see if that fixes it?

Russty

---

### Post by Russty of Oz on 2007-03-31
> I am just frustrated....

You are not alone! ](*,) 

Russty

---

### Post by apostoj on 2007-03-31
Ook....
How do you know what chipset this on the card before you buy it?

Dear Community,

Please help me select the right card Wireless PCI that Fiesty will love and cherish.
Can you tell me the card to get.  I live 2 miles from Fry's here in "The OC".  I can never have enough NIC's as far as I am concerned and I want and need you to help guide me to ubunto utopia.

Again,  thanks for what you have done SloppyJoe!!

John

---

### Post by Floppyjoe on 2007-03-31
> **apostoj said:**
> Ook....
How do you know what chipset this on the card before you buy it?

Dear Community,

Please help me select the right card Wireless PCI that Fiesty will love and cherish.
Can you tell me the card to get.  I live 2 miles from Fry's here in "The OC".  I can never have enough NIC's as far as I am concerned and I want and need you to help guide me to ubunto utopia.

Again,  thanks for what you have done SloppyJoe!!

John
Did you try the solution offered by the following quote?
> **xombie said:**
> The ralink based wifi devices are currently not compatible with Network Manager. To make the legacy devices work with feisty disable wireless networking in NM and use Administration>Network to disable roaming and configure the device. I have both rt2500(pci) and rt73(usb) working this way.

The rt2x00 drivers based on the dscape stack are compatible with NM but are mostly broken. I got the rt2500pci to work but not the rt73usb driver. These drivers and the dscape stack are under heavy development and probably won't be included until 2.6.22.

---

### Post by chili555 on 2007-03-31
Try here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by apostoj on 2007-03-31
I thought I tried everything last night until my wife found me asleep on my keyboard....
I need to just get a good reccomendation so I have a sense of accomplishment here.
I would rather spend the money on a card that works then spend another 8 hours trying to get something to work.  

Chilli,  that is where I got the idea for the card I got on the URL you sent me...

So,  give me a card that you know will work right out of the box.  Bullet proof Wireless NIC.

Right now, time is more important than money....have you tried to work and learn some new OS with your 18 month old boy clicking your mouse and banging on your keyboard when you turn your head....

You guys starting to get my delima?

---

### Post by apostoj on 2007-03-31
Hey I just went down and got a linksys PCI WMP54G and this is supposed to work and it's not.....
Isn't Ubuntu plug and prey?  It see's my network it see everybody and thier brother network.

hey I am totally new to this and I am getting tired of this.  What just exactly is going on.

Do I need to clean stuff up (how?) after removing a placing the new card into the box and booting it up?
Do I have to config the card...do I need to start a fire in my yard and do a chant to get this thing to attach to my wireless network.  

Darn.  I just don't know about this anymore.  I am gonna loose it.

---

### Post by Floppyjoe on 2007-04-01
There are several different chipsets for the linksys PCI WMP54G depending on what version you have and probably a couple of different ways to get the different versions to work. If you search the Forums for "WMP54G" you will find various different threads about them.

---

### Post by apostoj on 2007-04-01
It's just the weirdest thing with this card,  the darn thing.  I don't think I know what I am doing...obviously.  Last night the config is not sticking and tonight it is..the light on the back is solid,  it tells me I have 95% connectivity...

I noticed that Network Tools there is the Loopback and my unknown device....
I think somewhere somehow this is causing confusion.

My router see's my unbuntu box with two different MAC's....

Geezo...

I will see what I can do.

Thanks again floppyjoe

---

### Post by apostoj on 2007-04-01
How can I purge the box of it's current settings for the wireless cards then reset the setting with the new card.

I think there is old card residue and I...I have fallen and can't get up.
This is what my router is looking at right now.
Bigdog has two mac's and it's not true....

192.168.2.153  bigdog  00-18-39-13-E0-F0  
192.168.2.34  capostolilt  00-0E-35-9C-33-49  
192.168.2.170  bigdog  00-18-02-24-70-B5  
192.168.2.155  Me-PC  00-0F-B5-D4-24-B4  
     
  
--------------------------------------------------------------------------------

---

### Post by Floppyjoe on 2007-04-01
My router will sometimes keep an interface in memory even after it is not logged on anymore. I'm not sure why it does this.

---

### Post by apostoj on 2007-04-01
This is to much.  I don't even know what to ask anymore....
My attitude has gone to poo....

---

### Post by FishRCynic on 2007-04-01
I don't have to disable anything with network manager

I did have to manually find my wireless network though

I do not know if this will help you

when you single click on the network manager do you get the wireless connection menu

left click (right handed mouse)


it should show you the wireless network
if there is not one listed create one

if you are using wep then make sure you type in the key correctly as hex  or ascii depending
on what you set up in the router - (if you have hex and you type ascii it will not connect)

if it is already created - are you static or dhcp
menu

System
    Network
                 wireless networking properties
                             disable roaming
                                         set up dhcp (or static) as necessary  - 
                                         manually enter your wireless network information

                                              

save and go back to the network manager and try again

this has worked for me 3 times
but none have been your exact chipset

i am currently running feisty beta clean install - with updates as of this time.

---

### Post by trommas on 2007-04-01
> **apostoj said:**
> This is to much.  I don't even know what to ask anymore....
My attitude has gone to poo....

Don't feel bad man. Things will work out. Wifi is currently in heavy development, and feisty is at the bleeding edge. (Hopefully things looks better at release).

If I where in your shoes, I would do a fresh install (to get rid of hacks), and if wifi still don't work, uninstall Network Manager via Synaptic (you'll find it in the menus), then reboot, and finally setup static settings going to System > Administration > Network

I've read several places that this is known to work. Good luck!

---

### Post by trommas on 2007-04-01
Oh, I almost forgot. Installing Edgy might do the trick as well (It's easy upgrading to feisty later).

If you don't want to do this (or it fails) let me know... I've seen a lot of other work-arounds on the forum.

---

### Post by apostoj on 2007-04-01
Hey there!!
I feel a lot better today...I love living on that edge of blood.  It's just my nature to jump into something new and take on a beta to begen with.

I will do a nice uninstall of my current install.
Then go from there regarding this adventure.

I can not thank you enough....

I actually thought I was stepping on some of my GUI clicks.  I see the net I want when I click to two computers with the caution sign that tells me I am not connect then I go to system admim/network/wirless click on that and do a config wep key, ESSID and DHCP...
Then things just spin...I think I might be confusing the thing.
So...after reading the thread I don't think am to far off.
I don't like going back,  I just will keep plowing forward just to keep you on your toe's...

---

### Post by tomato on 2007-04-01
I have a Linksys rt61 chipset wireless NIC, and I had the same exact problem you're having. This is a post that fixed me right up, along with the specific section to pay attention to:
[http://ubuntuforums.org/showthread.php?t=392415&highlight=wireless+rt61](http://ubuntuforums.org/showthread.php?t=392415&highlight=wireless+rt61)

> Quote:
The big problem is the Network-Manager, now activated by default. It can't manage the rt61-legacy driver (because it doesn't use wpa_supplicant). I found this solution to deactivate it:


Disabling network manager in your gnome session will not work as that is just the 'notification area' for the network-manager service. To disable network-manager, either uninstall it (which will break ubuntu-desktop package) or do this:

Stop network manager

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
Now you have to configure your card on your own. I wrote the WPA configuration in "/etc/network/interfaces", i.e. with WPA2:

Quote:
auto ra0
iface ra0 inet static
address 192.168.1.8
netmask 255.255.255.0
gateway 192.168.1.1

pre-up ifconfig ra0 up
pre-up iwpriv ra0 set AuthMode=WPA2PSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwconfig ra0 essid MYESSID
pre-up iwpriv ra0 set WPAPSK="MyPassphrase"
If there's also an ethernet-NIC, deactivate it for testing:

sudo ifconfig eth0 down

I had some problems with routing and activated ethernet. I was wondering, why internet over the wireless-card didn't work, till I found out, that feisty tried to connect over the unplugged ethernet-NIC.

Is there a way to tell ubuntu the preferred network-adapter?

Hope this helps you.

SirMatlock


I'm pretty new to Linux too, but once you get in there and start working on it it starts to lose some of its mystique and becomes easier. 

Basically, my wireless NIC would see the access point's signal but wouldn't connect until I disabled network manager and manually entered my network information in the /etc/network/interfaces file. This is what my /etc/network/interfaces file looks like for WPA2 with AES encryption using dhcp (the other example in the quoted section above is using a static IP):

> 
auto lo
iface lo inet loopback

auto ra1
iface ra1 inet dhcp

pre-up ifconfig ra1 up
pre-up iwpriv ra1 set AuthMode=WPA2PSK
pre-up iwpriv ra1 set EncrypType=AES
pre-up iwconfig ra1 essid linksys_SES_47227
pre-up iwpriv ra1 set WPAPSK="your pass phrase here"


Oh yeah, I also disabled MAC filtering on my router too. That was preventing the connection for some reason.

I was about ready to give up on my wireless problem -and Ubuntu- until I got this fixed.

Hope this helps. Good luck.

---

### Post by tomato on 2007-04-01
I forgot to mention that my connection drops sometimes, and I haven't figured out why yet. But, I renew it with:

> sudo ifdown ra1

then

> sudo ifup ra1

and the connection is good.

---

### Post by iduriduridur on 2007-04-01
FIX FOR RTxx and RAxx cards in Feisty

1. Synaptic Package Manager > remove network-manager and network-manager-gnome

2. Set your card up under System > Administration > Network

3. Reboot

RA0 works now. It used to come up bring up the laptop but I guess network Manager breaks it and turned it off. Now the light stays Lit.

---

### Post by apostoj on 2007-04-06
iduriduridur!!!!

Howdy to you all,  I thank you all for your input and I am sorry for not getting back to you sooner regarding this issue getting the wireless card to work....

Well I get lost in some of the solutions that have been posted.  I mean, I have a lot to learn from the community and the power of Linux.  

As I write this I am currently downloading updates for Feisty Fawn!!
I am online and so stoked I can hardly stand it!!!  I am saying good by to the Microsoft bloated rip off software!!  That piece of poo put's a 1 gig foot print on my system and needs a gig of ram to run it!!  And it's still slower that a sloth.  I feel good and I can not thank you all. 

iduriduridur fix at the very end of this thread fixed the problem.  It was the easiest of them all for me, even tho, I want to use all the commands and learn to bang bang around the Ubuntu system...I digress, I am not very good with the command line,  but I jones to be in the biggest way.

I hope to learn a vast amount and someday maybe even add a widget or two and have the community say to me, "That is so Cool, apostoj!!"....:guitar: 

So now I am just going to surf away today, enjoy the speed of my linux box and spread the word.

One other thing!! The encouragement from you all kept me going, it could have been easy to give in and just relent to the easy of what I know.  Without the community...hell I would be downloading somekind of patch right now and praying the the MS patch doesn't hose my system.

Thank you All!!
Without intending to offend "God Bless on this Good Friday and Happy Easter!!"

Sincerely
John
):P

---

### Post by apostoj on 2007-04-06
Crap!!!
The 280 updates that unbutu wanted to give me when I got online hosed my system!!
Now what...that is the question I am now asking.
Recovery mode just takes me to Root....
What do I do?
Is there away to save my system?
I am writing from the XP side of my XP dual boot Ubuntu system.

RollerCoaster day....

John

---

