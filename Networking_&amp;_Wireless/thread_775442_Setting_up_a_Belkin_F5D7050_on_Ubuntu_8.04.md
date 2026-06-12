---
title: "Setting up a Belkin F5D7050 on Ubuntu 8.04"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by chrisdudeperson on 2008-04-30
Hey guys,

I am a total begginer at ubuntu so i have no idea where to start when setting up a wireless connection.

I understand that i have to install a rt2500 driver for this but i'm not sure how. And i have no idea how to set up the rest. 

I'm using ubuntu 8.04 and a Belkin F5D7050.

Can someone please help?

Thanks
Chris

---

### Post by chrisdudeperson on 2008-04-30
please help!

---

### Post by epee on 2008-04-30
I suggest reading the various HOWTO articles and searching the forum. If you're hoping for step-by-step assistance, then you're not likely to get it - unless it's already been posted before!

You will also have to experiment and try stuff out.

But FIRST - search and read!

---

### Post by chrisdudeperson on 2008-04-30
look, 

i am completly usless at this stuff

the guides are even to complicated for me.

The more i try, the more p***** off i'm getting.

Is there a complete begginers guide explaining everthing about setting up a wireless network in ubuntu


thanks
chris

---

### Post by Prefix100 on 2008-04-30
This should work by default in a Ubuntu install.

Try the LiveCD again, and see if it works on the liveCD, it it does, reinstall, if not, then post again.

---

### Post by chrisdudeperson on 2008-04-30
what do you mean try the livecd?

reinstall ubuntu?

---

### Post by ToM-X on 2008-04-30
I have the same adapter and it should work by default. The live CD is ubuntu pre-installed on a cd, so you just boot from cd.

You can download it from here if you do not already have it.

```
http://www.ubuntu.com/getubuntu/download
```

---

### Post by chrisdudeperson on 2008-04-30
i've tried that

still cant find any networks :(

---

### Post by chrisdudeperson on 2008-04-30
any other ideas?


thanks
chris

---

### Post by chrisdudeperson on 2008-04-30
i hate to repost but i really want this fixed and my post keeps on getting pushed off by other posts ¬_¬


thanks 
chris

---

### Post by Prefix100 on 2008-04-30
are you certain that that is your model?

It should defiantly work,

what does lsusb give you?

I have the same model and it works out of the box for me,
```

jonny@jonnyatLinuxMode:~$ lsusb
**Bus 005 Device 004: ID 050d:705a Belkin Components **
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1532:0007  
Bus 002 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by jackjones on 2008-04-30
Don't see it on this list
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)
How can you tell it will work?
(I'm a newbie and can't get my wireless working either)

The "help" file in Heron seems wrong.
When I look at
Help -> Internet -> Wireless Networking -> Troubleshooting,
there's the following:
3.2.1 Check for device recognition
Open device manager
System -> Preferences -> Hardware Information.

Hmmm, there is no "Hardware Information" option under System -> Preferences.

It's not clear that Heron is ready for primetime.  Maybe they'll get it cleaned up in the next edition.

---

### Post by chrisdudeperson on 2008-04-30
Bus 001 Device 007: ID 04f2:0200 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 06f2:0011 Emine Technology Co. 
Bus 001 Device 003: ID 050d:705a Belkin Components 
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub 
Bus 001 Device 001: ID 0000:0000  


And yes jackjones i thought the same untill i found out that people had done it

Thanks
Chris

---

### Post by Prefix100 on 2008-04-30
I know it works cause im using it right now :)

Ok, seriously dude, that should be working out of the box.

Type ifconfig into console and show the output.

---

### Post by chrisdudeperson on 2008-04-30
here ya go:



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15200 (14.8 KB)  TX bytes:15200 (14.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:ad:79:c8  
          inet6 addr: fe80::217:3fff:fead:79c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57346 (56.0 KB)  TX bytes:100386 (98.0 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:17:3f:ad:79:c8  
          inet addr:169.254.8.105  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

---

### Post by olbill on 2008-04-30
I hope my past troubles help you.   The Belkin F5D7050 comes in at least four versions with four different chipsets.   Since you mention the rt2500usb chipset I will assume you have a version 2 as I do.  The problem with my F5D7050 is that it reports as a version 1.  The system installer does its duty and loads the rt73usb driver which will not work with my F5D7050.  If you are sure that your F5D7050 is a version 2 (see the [www.belkin.com](www.belkin.com) site) the  rt2500 sticky at top of the wireless page may help you.  If yours is a version 2, do not forget to blacklist the rt73usb driver before installing ndiswrapper.

I hope this is less of a trial for you than it has been for me.  Other versions of this card seem to work out of the box, but the version 2 has been a beasty for me.  Best regards and I hope this helps you.

---

### Post by chrisdudeperson on 2008-04-30
i'm not too sure what version i have
how can i find out

---

### Post by chrisdudeperson on 2008-04-30
ok, just found out how to from a friend,

i am version 3


thanks
chris

---

### Post by ToM-X on 2008-04-30
> **chrisdudeperson said:**
> i'm not too sure what version i have
how can i find out

On mine there is a sticker on one side. Silver it is.

---

### Post by chrisdudeperson on 2008-04-30
yer i found this thing on belkin which relates to my FCC ID


Version
 FCC ID
 
1xxx
 K7SF5D7050
 
2xxx
 K7SF5D7050A
 
3xxx
 K7SF5D7050B
 
4xxx
 RAXWN4501H
 
5xxx
 K7SF5D7050E

---

### Post by olbill on 2008-04-30
Check the FCC ID on the back of the card.   Mine says K7SF5D7050A.  I believe the [WWW.BELKIN.COM](WWW.BELKIN.COM) site shows which numbers apply to which version.  Another way is to check the files on your windows install disk.  If they contain the rt2500usb files you can be pretty sure it is version 2.

---

### Post by chrisdudeperson on 2008-04-30
yup,

my last post just said that!

i am on version 3.



Thanks
Chris

---

### Post by olbill on 2008-04-30
I apologize for th noise. I hope all works out well for you.

---

### Post by chrisdudeperson on 2008-04-30
thanks,

where do i go next?

i know i'm version 3 and the linux recognises my hardware

any ideas?


thanks
chris

---

### Post by Prefix100 on 2008-04-30
I can't help you beyond this point, but something doesnt seem write with your ifconfig. Someone who is more experienced will be able to tell you if thats wrong or not,

Jonny

---

### Post by chrisdudeperson on 2008-04-30
ok i may start a new post looking into this problem tommorow.

Thanks for all your help guys,
Much appreciated :)

---

### Post by epee on 2008-05-01
Well, bumping the thread isn't going to help, and might just get up someone's nose.

There is no 'Ubuntu Wireless Networking for Dummies'. Even for those of us with too many years experience (which in my case includes writing OS drivers for network devices) it is not plain sailing. Although, of course, it does mean I can figure out things by reading the various posts etc.

For example, did you check out [this]("http://ubuntuforums.org/showthread.php?t=400236") post?

Did you search the forums for any mention of "Belkin FD57050"?

---

### Post by Sambo320 on 2008-05-03
I have version 4000. My device is not even detected with lsusb. I am using the zd1211rw driver. Does anybody have an idea why my device will not show up?

---

### Post by gazz1982 on 2008-05-10
hi I have exactly the same problem as chris, same belkin usb stick, installed ndiswrapper 

same FCC ID etc...

tried this:
[http://blog.mcnicholl.com/2008/03/11/ubuntu-710-gutsy-and-belkin-usb-wireless-networking/]("http://blog.mcnicholl.com/2008/03/11/ubuntu-710-gutsy-and-belkin-usb-wireless-networking/")

when i type:

sudo /etc/init.d/networking restart 
the following is returned:

No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

does this help anyway with debuging?
I'm going round in circles!!!!!!!!!

---

### Post by james_vanb on 2008-05-10
I have Belkin F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu hardy herron and a Desktop running ubuntu hardy herron.  Responding on Desktop using Belkin rt73.  Install has been the same using ndiswrapper and the install cd as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules (or gedit if using ubuntu)

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

This also worked for a Zonet ZEW 1502, without blacklisting anything.

Hope it works for you.

---

### Post by thewOndErEr57 on 2009-01-15
Hi there, I know that this is a very old topic, but I thought I would bring it up to date. The instruction given is no longer applicable for Intrepid. There were some people who used ndiswrapper as the stop gap for Hardy and Intrepid for this device.

However, we have a Intrepid proposed kernel release due soon, which will include native support for this device with driver rtl8287. I have written a full tutorial on how to make this work for device F5D7050 with Intrepid.

Please see the full tutorial here:
[Belkin F5D7050 with Intrepid natively!]("http://linuxsoftwareblog.com/blog/?p=30")

---

### Post by dj_flx on 2009-02-28
Has anyone got this working with Xubuntu 8.04 with a F5D7050 Rev. 5000?

I tried the above, but it won't authenticate on my WEP 64bit network. It just keeps asking for the key over and over again.

---

### Post by james_vanb on 2009-02-28
Had similar problem - Installed WiFi-Radar - Combined with Network Manager seemed to solve the problem.

---

