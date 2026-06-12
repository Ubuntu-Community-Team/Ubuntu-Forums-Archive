---
title: "XP wireless drivers"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by 1492 on 2010-09-14
How/where do I get the Windows XP wireless drivers (I need them for the ndiswrapper)?

Any help would be really appreciated.

---

### Post by Dude-PWB- on 2010-09-14
Wireless drivers for what wireless device?

You need to know which device, and then go to the manufacturers website and download the appropriate drivers for your device.

---

### Post by 1492 on 2010-09-14
Alright, thank you so much!

---

### Post by 1492 on 2010-09-14
Does it have to be XP drivers? Can it be Vista (because that's all I have found so far)?
I'm sooo close... I found the download, but it keeps timing out because the Dell site is loading so slowly.
:cry:

---

### Post by wilee-nilee on 2010-09-14
Usually if you do the MS update **choose custom** this might show the drivers your looking for.

---

### Post by anewguy on 2010-09-15
> **1492 said:**
> Does it have to be XP drivers? Can it be Vista (because that's all I have found so far)?
I'm sooo close... I found the download, but it keeps timing out because the Dell site is loading so slowly.
:cry:

Nope - can't be Vista - *only* XP.  

Also, isn't this the same issue we were going over in this thread?

[http://ubuntuforums.org/showthread.php?t=1568808]("http://ubuntuforums.org/showthread.php?t=1568808")

If so, and if this is the same computer, the wireless device was already identified as:

08:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 35) 


As mentioned in that thread, there are a couple of ways to go about this.  The preferred way is a native or restricted (native Linux, but not open source) driver.  The best way to do this is:

- temporarily hard wire your PC to your router
- open a terminal window
- type:
sudo apt-get update <press enter>
- then check in System/Administration/Hardware Drivers to see if there is a driver listed - if so, be sure it is enabled.


You may also want to see if there is a driver already available and whether or not it is active via:
- System/Adminnistration/Hardware Drivers - if there is a driver there be sure it is enabled


There may be other ways for this Intel based controller to be used as well.

A "last resort" option is ndiswrapper - a tool which allows you to use Windows XP wireless drivers in Linux.  It can be a little daunting if you only use ndiswrapper at the command line.  It is highly recommended that you also install ndisgtk - a GUI based tool used as a front-end to ndiswrapper.  You do not need to be on the net to install these.  The installation procedure was gone over in your other post.

The usage of ndiswrapper/ndisgtk using the Windows XP drivers was also addressed in that other post.

So, if you are convinced you must use ndiswrapper/ndisgtk, then you do indeed need the Windows XP drivers for your adapter.  You should go to Intel's website and search the support there for your adapter, then check for downloads - in particular it may say software and drivers, and be sure to download the Windows XP version of the driver.  If there is no Windows XP driver, then we'll have to face that bridge later.

But even more important than all that, as was mentioned in the other thread, it is *trying* to use the "iwlagn" driver.  I am not familiar with your adapter and therefore haven't had to set one up yet.  In that old thread, someone gave instructions for enabling a backports source and the instructions for getting this working.  There is a thread on luanchpad:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/120799](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/120799)

You can read through it if you want, but it appears the only working suggestion was at the end:

"Mark Rijckenberg said on 2010-08-13: 
If installing the linux-backports-modules-2.6.32 package from the lucid-proposed repository does not fix this wireless issue, then the only remaining option is to install the Alpha 3 release of Maverick Meerkat (Ubuntu 10.10 alpha 3) from a LiveCD session.
Keep in mind that Maverick is still in alpha phase and NOT ready for production machines.
You can get the iso here:
http://cdimage.ubuntu.com/daily-live/current/"

I can't do more to help you at this time, and would suggest you follow the instructions in the old thread.  There may be someone else out there who has gone through the backports method to get this working - if so,  I hope they will answer you.

Dave ;)

---

### Post by 1492 on 2010-09-15
Yes, it is the same computer.
I went to the Dell site, clicked on [COLOR=black]_Drivers and Downloads_ then _Drivers Home_ then typed in the service tag. Then a page with the computer and downloads for it came up. It had the option of 4 OS: Windows 7 64-bit, Windows Vista 64 and 32-bit, and BIOS. Nothing about XP, so I'm not quite sure what I need to do. I'll try that backport thing.[/COLOR]
 
I did find a cable to computer to the internet (at least I hope it will, I don't even know where the cable came from).
 
Thanks
 
[http://ubuntuforums.org/attachment.php?attachmentid=169575&stc=1&d=1284587556](http://ubuntuforums.org/attachment.php?attachmentid=169575&stc=1&d=1284587556)

---

### Post by 1492 on 2010-09-15
The Network Manager icon has disappeared. How do I get it back?

---

### Post by anewguy on 2010-09-15
I believe (haven't tried it) the way to put the network manager applet back (assuming you did not delete the network manager package) is to right-click in blank space on the top bar, click "Add to Panel", then scroll through and look for the network manager applet.


As far as your wireless driver is concerned:


I'm a little confused here - the lspci you did in the other post returned the wireless as noted above:

08:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 35) 

However, when I go to Dell's support site using the service tag you show in your image, that model of wireless does not appear in the driver list.


  You may need to contact Dell and explain to them that if they don't have a Linux driver (which you can bet they won't) that you do need a Windows XP driver for your wireless, and be sure to post the line identifying your wireless.

  You can also try searching Intel's site for a Windows XP driver for that adapter.

  At an absolute worst-case you may need to pick up either a PCMCIA or USB wireless adapter - but be sure it's on the list of those that work with ubuntu before you just buy one.

Dave ;)

---

### Post by 1492 on 2010-09-15
Okay, thanks again, however, the network manager is not in the add to panel list. I know I did not delete the package. Do I need to use the network manager to connect to the internet?

---

### Post by anewguy on 2010-09-15
Okay, here's an update for you that you probably won't like:

- while the driver code is present, the firmware code needed by the driver isn't, and this includes the backports.  The bug report and follow-up from launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451")) indicates that it won't ever work in 10.04 even with the backports, but that it has been moved up to Maverick.  So, as was indicated in one of the posts in the old thread, to get this to work you will probably need to download and install Maverick - but I think it may still be in alpha or beta testing only yet.  The tail end of the bug report does say it is fixed in a backports module -> linux-backports-modules-2.6.32 - 2.6.32-23.16, but I can't tell if that is a normal package or a testing package.  You may want to try it as you'd have nothing to loose.

So, perhaps finding a PCMCIA or USB wireless adapter that will work with ubuntu (post back if you need help searching for the list on the net) might actually be a better option for you at this time.

Dave ;)

---

### Post by theozzlives on 2010-09-15
I'd say search for name and model instead of service tag. You may find XP drivers that way. If you call and tell them your running Linux instead of the OS it came with, you're in for a fight.

---

### Post by anewguy on 2010-09-15
As far as network manager is concerned, I found this which seems simple enough:

[http://practicalswitchtoubuntu.blogspot.com/2009/02/restore-missing-network-manager-applet.html]("http://practicalswitchtoubuntu.blogspot.com/2009/02/restore-missing-network-manager-applet.html")

Dave ;)

---

### Post by 1492 on 2010-09-15
When running the command for Network Manager, it says no such file or directory exists- the same message I got on other attempts to restore it. Do I need it? 
On the Intel site, the closest thing to adapter number 6050 is 6250. I assume this will not work...

Thanks Ozzlives, I think I found it.

---

### Post by 1492 on 2010-09-15
> **anewguy said:**
> Okay, here's an update for you that you probably won't like:

- while the driver code is present, the firmware code needed by the driver isn't, and this includes the backports.  The bug report and follow-up from launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451)) indicates that it won't ever work in 10.04 even with the backports, but that it has been moved up to Maverick.  So, as was indicated in one of the posts in the old thread, to get this to work you will probably need to download and install Maverick - but I think it may still be in alpha or beta testing only yet.  The tail end of the bug report does say it is fixed in a backports module -> linux-backports-modules-2.6.32 - 2.6.32-23.16, but I can't tell if that is a normal package or a testing package.  You may want to try it as you'd have nothing to loose.

So, perhaps finding a PCMCIA or USB wireless adapter that will work with ubuntu (post back if you need help searching for the list on the net) might actually be a better option for you at this time.

Dave ;)
 
Okay, thanks. I hadn't even thought of getting a USB adapter thanks

---

### Post by anewguy on 2010-09-15
Just check the online list first for devices known to work with ubuntu - I'd hate to see you buy an adapter without checking that and then find it doesn't work!

Dave ;)

---

### Post by 1492 on 2010-09-15
I did find some drivers, however, when I opened up the Windows wireless drivers thing and installed the .inf file, and clicked the configure network button, it said it could not find a network configuration tool.

---

### Post by anewguy on 2010-09-15
First off, what driver did you find - can you point me to a link for it?

What were you doing when you got your error?


Also, I think I found some drivers for you for XP.  The site is (I think) in French, but the first link says Windows XP drivers for this series:

[http://www.station-drivers.com/page/intel%20lan-wan.htm]("http://www.station-drivers.com/page/intel%20lan-wan.htm")


Dave ;)

---

### Post by 1492 on 2010-09-15
Well, now I only have the ones from the older thread because the ones I downloaded from Dell did not contain any .inf or .sys files and the ones from Intel are actually for a different adapter, so nevermind, sorry.

[http://ubuntuforums.org/showthread.php?t=1568808&page=4](http://ubuntuforums.org/showthread.php?t=1568808&page=4)

---

### Post by 1492 on 2010-09-15
If I used a USB adapter that worked with Ubuntu, would I need to download anything? (as in drivers)

---

### Post by 1492 on 2010-09-15
I decided to try getting a USB adapter. There is one on Amazon that says it works with Linux.  Does that mean all Linuxes?
[http://www.amazon.com/Palm-Power-Wireless-Long-Rang-Network/dp/B003IWBLJ6](http://www.amazon.com/Palm-Power-Wireless-Long-Rang-Network/dp/B003IWBLJ6)

---

### Post by anewguy on 2010-09-15
I'm not sure on that adapter, but obviously I'm limited to those I have had experience with.  This is the list I was talking about, but I'm not sure how current everything is, particularly with USB devices:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Upon further research, it appears the above list is WAY out of date.

What I think I would do, if it was me, is:
[LIST]
[*]do a search through this forum for that adapter and what luck people have had with it
[*]do the same, and possibly ask for opinions on what to get, on the [Ubuntu Networking and Wireless Forum]("http://ubuntuforums.org/forumdisplay.php?f=336")
[*]ask for suggestions/opinions on this forum.
[/LIST]

Be forewarned - you'll probably get some very biased replies, like theirs is the ONLY one to get, but you can weed that out or ask us for help there as well.

As far as would the one you're looking at require a driver, the answer is "yes", as any adapter requires a driver.  The trick is in whether or not it is a native driver included with ubuntu, a restricted driver you can load after hard-wiring to the net, a driver you must use ndiswrapper for, even a driver that is a real pain to get working.  That's why I would look around the forums first and ask some questions, as your best buy would be to find one that it supported "out of the box" by ubuntu, so you don't have to load anything to get it to work.  It might take a little homework, but you'll be a lot happier in the end.

Dave ;)

EDIT:  Pointers to more lists and info:

[http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html]("http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html")

Can't speak to it myself, but there was a post 8/8/2010 that said this worked great:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022")

>  Paz13
5 Cups of Ubuntu
 
Join Date: Apr 2008
Location: Brighton - England - UK
Beans: 44
Xubuntu 10.04 Lucid Lynx
Send a message via MSN to Paz13
	
Re: Recommend a out of box wireless device for 10.04?
I posted this in beginner talk where most people are, and i'm a beginner so it wasn't just to get attention.

Somebody recommended Zyxel G-202, random make i've never heard of it. Looked on-line apparently it's a good brand and very decent reviews around about 4 star.

I plugged it in and it worked instantly, i didn't know what to do after that just saw there looking at the screen like . I set up the setting for the wireless previously like the BSSID and that stuff so make sure you get all your wireless information, it might work stright away without any data input i wouldn't be suprised if it knew my WEP key aswell.

> 
Old May 3rd, 2010       #2
DavePlummer
5 Cups of Ubuntu
 
Join Date: May 2009
Beans: 41
    
Re: Best USB wireless adapter for 10.04
I'm using an SMC SMCWUSB-G EZ Connect adapter. It works out of the box. I bought mine from Newegg.com: [http://www.newegg.com/Product/Produc...-080-_-Product](http://www.newegg.com/Product/Produc...-080-_-Product)
DavePlummer is offline Report Post       Reply With Quote Multi-Quote This Message Quick reply to this message

Just a few things I found that might help you out.

Dave ;)

---

### Post by 1492 on 2010-09-16
Thanks again.

---

### Post by anewguy on 2010-09-16
Glad to try to be of help - let us know how things turn out!  I'm sure there will be plenty of people wanting to know what adapter you do get and what your experience with it is (including my ever-curious self!).

Best of luck!

Dave ;)

---

### Post by 1492 on 2010-09-16
I figured I'd use the SMC SMCWUSB-G EZ Connect adapter because it works out-of-the-box, and because I can get it at Office Depot. Hopefully it works.

This makes me so mad, I found something that apparently came with the modem, and I assume it is for connecting your computer to it. However, on the new computer, there is no plug to plug it into. On my old computer there is. Oh, well.

Again, thank you so much for all your help.  I really appreciate it.

---

### Post by 1492 on 2010-09-17
Can I use anything beside the USB port for an adapter, because I usually use the 2 USB ports on my computer (not a big deal, I'll be happy enough to get the internet working at all). The ports are listed below. There are 2 that I have no idea what they are, so I took a picture. Don't laugh....

[USB symbol][lightning bolt]eSATA

EC

something with 1394 written over it

Would there be wireless adapters than can be used with any of these

---

### Post by anewguy on 2010-09-17
If you don't want to use your USB ports, then check to see if your laptop has a PCMCIA slot (it would normally look like a box about 2" long and 1/4" high with a hinged door that pushes in).  If so, you can check the web and the forums for PCMCIA wireless adapters that work with Linux (I know there are some, I would just need to check again).

I forgot which make/model you're running this on again - if you could post that back I can check the specs to see if you have a PCMCIA port and then check to see what adapters might work (I suspect these will probably require installing a driver).

Dave ;)

EDIT:  Just looked back through the thread and got the info on your laptop.  Checked Dell's site - it appears you have 2 regular USB ports, and 1 port it says is a shared eSATA and USB port - you may be able to use that port.  It should be the one that says USB/eSATA on it (or at least the symbols).  I would try one of the devices you normally plug in to a USB port there first (perhaps a mouse?) to see if it works ok.  If so, go for it using that port.

---

### Post by walt.smith1960 on 2010-09-18
> **1492 said:**
> I decided to try getting a USB adapter. There is one on Amazon that says it works with Linux.  Does that mean all Linuxes?
[http://www.amazon.com/Palm-Power-Wireless-Long-Rang-Network/dp/B003IWBLJ6](http://www.amazon.com/Palm-Power-Wireless-Long-Rang-Network/dp/B003IWBLJ6)

I fell into this trap. An adapter that works with Linux and an adapter that is plug and play with Linux can be two different things.  I bought an adapter from Amazon that is supposed to work with Linux. I spent time on it but never got it to work. I would recommend an adapter known to be plug & play.

---

### Post by anewguy on 2010-09-18
Hence the recommendations from others that I posted previously for USB adapters that work out of the box (you don't have to do anything but plug it in) with ubuntu.

Dave

---

### Post by walt.smith1960 on 2010-09-18
> **anewguy said:**
> Hence the recommendations from others that I posted previously for USB adapters that work out of the box (you don't have to do anything but plug it in) with ubuntu.

Dave

Now to let the companies whose product we didn't buy because they don't work well with Linux  know WHY we didn't buy their product. ;)

---

### Post by anewguy on 2010-09-18
> **walt.smith1960 said:**
> Now to let the companies whose product we didn't buy because they don't work well with Linux  know WHY we didn't buy their product. ;)
I'm with you 100%, but unfortunately it just falls on deaf ($) ears.  You know - they got in business to make money so why would they ever give away anything that might help them sell MORE product?  ;) ;) ;)

Sometimes you really have to wonder, don't you?

And a note to 1492 - did you buy your adapter yet?  How's it working?


Dave ;)

---

### Post by 1492 on 2010-09-23
I just got the SMC SMCWUSB-G EZ Connect adapter. I booted up Ubuntu, plugged it in, and nothing happened. I tried putting in the CD. The Autorun thing didn't work, so I opened up the Windows wireless drivers program (because I can't get to the Network Manager) and selected the .inf file under Driver>WindXP64. It said that it was an invalid driver. I then used the one for Vista, which seemed to install fine. I clicked configure network and it said that it could not find network configuration tool. What do I need to do?

Edit:
Also, using the cable that came with it, it will fit the eSata  port (my two USB mice do not, though).

---

### Post by anewguy on 2010-09-24
Well, looks like whoever it was that said it worked out of the box may have had a different version.'

First off, you can't autorun a Windows CD in linux, so there is no surprise there.  

Second, if you selected the Windows XP 64 bit drivers but you are running "normal" ubuntu (i.e., you didn't download the 64-bit of ubuntu), then the 64-bit driver won't work either.

Third, even though it looks like things work with Vista drivers, it has always been my understanding that ndiswrapper (which is what system/administration/windows wireless drivers points to) only works with Windows XP drivers.  The others appear to load but don't actually work.

So what would I do now?
[LIST]
[*]If possible, hard-wire your PC to your router temporarily, then do "sudo apt-get update" in a terminal window
[*]check under system/administration/hardware drivers and see if there is a driver listed there for your wireless - if so, enable it.
[*]Try plugging the adapter into 1 of your 2 known-good USB ports to see if something better happens (I know you use your USB ports, so this is just a test to see if the so-called combo sata/USB port is really a combo port and works as it should)
[*]Via system/administration/windows wireless drivers, remove any devices/drivers that show until nothing is there, then try adding again but use the Windows XP 32-bit driver.
[*]With the adapter plugged in, do the following in a terminal window:

lsusb <press enter>

Copy the results and post back here in a reply.
[/LIST]

I'm sorry you've run into this again with an adapter that was supposed to work right out of the box.

BTW - you say you can't get to network manager.  Does the icon show?  What happens if you right-click on it? (e.g., if the right-click works, be sure the "Enable Wireless" is checked).  What happens if you left-click on it?  Did you by any chance delete network manager and install wicd?

Dave ;)

---

### Post by 1492 on 2010-09-24
I am running 64-bit Ubuntu.

I tried all .inf (Windows Me, xp 32-bit & 64-bit, Vista, 98, and  whatever else there was) on the CD, and the drivers for the Mac.

I haven't been able to connect to the internet at all, wireless or otherwise.

I tried the regular USB ports, that made no difference.

I can't get to Network Manager because the icon is gone completely. I  guess it's possible I accidentally deleted it. Also, there was something  under system>... but I can't remember what the name was. I do  remember that it had something to do with connecting to the internet,  though.

I think it probably has something to do with the network manager.

And no, I did not install wicd.

I did see something on the forums about how to fix the network manager problem, so I'll check and see if that works.

I also checked to see if the adapter was defective by running it on Windows 7 on the same computer, and it worked fine.
Again, thank you so much for all your help.

---

### Post by 1492 on 2010-09-26
I plugged in the adapter in the USB/eSATA port entered
```
lsusb
```and then a list appeared. I then plugged the adapter into the regular USB port (because I wasn't sure if it mattered or not), and plugged the mouse into the USB/eSATA port. I put in lsusb again, and nothing happened (the wireless mouse also stopped working at some point after this). I tried to close the terminal, and it said something about doing so would kill some process. I decided to just click cancel and open another terminal. I typed on lsusb again. Nothing happend, I got the same message, and clicked ok. It froze after that. I rebooted, opened the terminal, typed in lsusb, and it froze. I tried one more time, & it froze again. I had problems with it freezing the other day too.

Should I try getting wicd?

---

### Post by 1492 on 2010-09-26
Where can I get wicd?

---

### Post by cavalier911 on 2010-09-26
WICD won't help your situation until the wireless adapter is installed.
The wireless adapter must be plugged into the USB port **before **you boot into Lubuntu.
The SMC SMCWUSB-G EZ Connect adapter is reported to use native linux driver zd1211rw which is included in the lubuntu install.
No ndiswrapper is required.
When you type ifconfig in the terminal and your adapter is listed you know it's installed.
```

wlan0     Link encap:Ethernet  HWaddr 00:13:49:54:2A:B5  
          inet addr:192.168.123.3  Bcast:192.168.123.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:334713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:472102676 (450.2 MiB)  TX bytes:23380374 (22.2 MiB)
          Interrupt:10 Memory:f4000000-f4002000 

```
If it doesn't work **copy/paste the list from lsusb command** here as anewguy requested.
That has the chipset id of the wireless adapter.

---

### Post by 1492 on 2010-09-28
Here is the what I got when I put in lsusb:
```
    Bus 002 Device 009: ID 8086:0188 Intel Corp. 
   
  Bus 002 Device 004: ID 046d:c52b Logitech, Inc. 
   
  Bus 002 Device 003: ID 083a:4505 Accton Technology Corp. SMCWUSB-G 802.11bg
   
  Bus 002 Device 002: ID 8087:0020  
   
  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
   
  Bus 001 Device 007: ID 413c:8160 Dell Computer Corp. 
   
  Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. 
   
  Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. 
   
  Bus 001 Device 004: ID 0c45:6406 Microdia 
   
  Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
   
  Bus 001 Device 002: ID 8087:0020  
   
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


and when I put in ifconfig

```
    lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:156 errors:0 dropped:0 overruns:0 frame:0
            TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:12208 (12.2 KB)  TX bytes:12208 (12.2 KB)
   
   
  
```

---

### Post by anewguy on 2010-10-01
Sorry I haven't gotten back to you - I share my brother inlaw's DSL connection and the DSL modem went bad over a week ago and we had to wait until late last night to get it working again.

First, as already mentioned, network manager or wicd won't help until the driver is working for the device.  However, just so you have network manager back, right-click in a blank space in the top bar and select the add to option - scroll through until you find network manager and enable it.

As far as drivers, I'm having a hard time understanding why it's not recognized out of the box, so I'd like you to post the output of a couple of things back here:

- in a terminal window:  lshw -C network

- then copy and paste the contents of the /etc/modprobe.d/blacklist.conf file back here

Dave ;)

EDIT:  It also appears that while that one port is supposed to be a dual USB/SATA port it doesn't work that way.  So, if you don't have enough USB ports, get a small USB hub.

---

### Post by 1492 on 2010-10-08
I can't add the Network Manager.  When I click the 'add' option, the task manager is not listed. I think I might have deleted it. Also, the USB/eSATA does work as a USB port for all USB things. I'm not quite sure what I did that it wouldn't work.

---

### Post by anewguy on 2010-10-08
I don't find it surprising that the combo USB/eSATA port doesn't work with USB.  It seems like a strange combination to me and I suspect it may mean something other than what it says.  I suspect only your true USB ports will work as USB ports.

As far as adding back network manager - what does it matter if task manager is there or not?  Is network manager there?

Dave

---

### Post by 1492 on 2010-10-08
The USB port *does* work, and I meant the Network Manager, not the task manager.

---

### Post by 1492 on 2010-10-08
I think that I deleted the Network Manager or something.I could not put in lshw -C network because I couldn't get Linux to load. I turned on the computer and chose Linux. It loaded the splash screen and froze. I then restarted the computer and this time I was able to get to the login menu. I hit enter and it froze. I restarted; repeated. This happened about 2 more times. Then it said something about a problem with a Windows file & that it was fixing it or something. It froze. I then restarted again. This time it came up with the splash screen and Ubuntu written across it with some dots over it. I restarted one last time & the same thing happened. I then booted into Windows 7. It said something about problems with some file do you want to do a system restore? Your personal files won't be deleted, but some programs might be etc. I hit yes (the only option) and then it started loading or something (I have no idea what it was doing or supposed to be fixing). It restarted, I let it time out & boot into Windows 7, & it loaded normally, so, at this point, I gave up trying to boot-up Ubuntu.

---

### Post by 1492 on 2010-10-08
I think that I deleted the Network Manager or something.I could not put in lshw -C network because I couldn't get Linux to load. I turned on the computer and chose Linux. It loaded the splash screen and froze. I then restarted the computer and this time I was able to get to the login menu. I hit enter and it froze. I restarted; repeated. This happened about 2 more times. Then it said something about a problem with a Windows file & that it was fixing it or something. It froze. I then restarted again. This time it came up with the splash screen and Ubuntu written across it with some dots over it. I restarted one last time & the same thing happened. I then booted into Windows 7. It said something about problems with some file do you want to do a system restore? Your personal files won't be deleted, but some programs might be etc. I hit yes (the only option) and then it started loading or something (I have no idea what it was doing or supposed to be fixing). It restarted, I let it time out & boot into Windows 7, & it loaded normally, so, at this point, I gave up trying to boot-up Ubuntu.

---

### Post by anewguy on 2010-10-08
Hummm.....maybe I missed something here.  Do you dual boot, having installed Ubuntu in a separate partition, or did you install it within Windows - the wubi option?

Dave

---

### Post by 1492 on 2010-10-11
I have a dual boot Ubuntu & Windows 7

---

### Post by anewguy on 2010-10-11
I'm more than a little confused here that it gave a Windows error message when you were running Ubuntu.

---

### Post by 1492 on 2010-10-11
Today I booted up Ubuntu & it was normal, except that it is now running extremely slow. Like when I clicked on any of the menus, it takes about 40 seconds to respond, even though it had been working normally before I had the error message about Windows. Also, what is a super-user?

Here is what I got when I put in lshw -C network:
```


WARNING: you should run this program as super-user.
     *-network DISABLED      
          description: Wireless interface
          product: WiMAX/WiFi Link 6050 Series
          vendor: Intel Corporation
          physical id: 0
          bus info: pci@0000:08:00.0
          logical name: wlan0
          version: 35
          serial: 00:23:15:18:67:1c
          width: 64 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
          resources: irq:38 memory:f8000000-f8001fff
     *-network DISABLED
          description: Ethernet interface
          product: RTL8111/8168B PCI Express Gigabit Ethernet controller
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 0
          bus info: pci@0000:20:00.0
          logical name: eth0
          version: 03
          serial: 00:26:b9:ca:0f:a0
          width: 64 bits
          clock: 33MHz
          capabilities: bus_master cap_list rom ethernet physical
          configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
          resources: irq:37 ioport:5000(size=256) memory:f8404000-f8404fff(prefetchable) memory:f8400000-f8403fff(prefetchable) memory:f8420000-f843ffff(prefetchable)

```

---

### Post by 1492 on 2010-10-17
Is there a way I could download the Network Manager off of the internet using Windows 7 & a jump drive to put the Network Manager back on Ubuntu (because I might have deleted it)?

---

### Post by 1492 on 2010-10-17
If I were to install Ubuntu again, would it just replace what was already installed?

---

### Post by 1492 on 2010-10-19
It works! I finally connected to the Internet. I just reinstalled Ubuntu, and it worked. I think I deleted the Network Manager. Also, when I installed it the first time, I somehow installed it wrong (I didn't use the installer I guess). Now that I have installed correctly, it also fixed the problem of the small partition (when I installed it the first time, I never was given any options like that, the installation was completely different). It works. Thank you all so much.

---

### Post by anewguy on 2010-10-19
Glad you got it working!  Enjoy!

Dave ;)

---

### Post by 1492 on 2010-10-20
One more question. On three other computers, (2 running XP and this one under Windows 7) the Internet speed is 11Mbps. On Linux it is 1Mbps. Why is that?

---

### Post by anewguy on 2010-10-22
I'll assume this is wireless?  Usually that seems to be a product of the driver or the tweaking of some settings.  I am not familiar with the settings - I just remember seeing this several times in the forum.

Dave ;)

---

