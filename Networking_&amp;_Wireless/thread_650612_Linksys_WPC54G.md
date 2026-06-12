---
title: "Linksys WPC54G"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by doublez on 2007-12-26
I installed ubuntu on a laptop I had sitting around to try it out and I like it alot, but I can't get my wireless card to work. I enabled the restricted drivers and I can find networks, but can't connect to them. I made sure the router settings are fine (mac address, passwords,) so it should work. I saw some threads about this, using something called ndiswrapper. I don't know what this is or how to use it though. If someone could help me it would help out alot.

Forgot to mention my laptop is a Dell Inspiron 8200 if that means anything.

Thanks

---

### Post by rustybronco on 2007-12-26
what version are you using ?, then do a search for that version
such as wpc54g v2 [http://ubuntuforums.org/showpost.php?p=3954576&postcount=1](http://ubuntuforums.org/showpost.php?p=3954576&postcount=1)

v3 [http://ubuntuforums.org/showpost.php?p=1943706&postcount=1](http://ubuntuforums.org/showpost.php?p=1943706&postcount=1)

---

### Post by doublez on 2007-12-26
On my router settings page it says that the router is v1.4 but I don't know where to find the cards version. Where would that be?

---

### Post by rustybronco on 2007-12-26
usually on the bottom of the device.

v2  [http://ubuntuhcl.org/pub/products.php?category_id=32&manufacturer_id=19](http://ubuntuhcl.org/pub/products.php?category_id=32&manufacturer_id=19)

---

### Post by OlyPerson on 2007-12-26
Mine's not working either (version 3).  Is there a driver for it or something?
I'm using a Dell Latitude CPx (old laptop).

---

### Post by doublez on 2007-12-26
Only the model is on the device, not the version number. I'm pretty sure its v1.

---

### Post by rustybronco on 2007-12-26
More than likely it's a v1, but post the output of    lspci -nn 
in the terminal

---

### Post by doublez on 2007-12-26
What do I do in terminal. When I open it a line is there, do I just type lspci -nn? When I do that a bunch of hardware is listed with some numbers.
I'm new to this kind of thing.

---

### Post by doublez on 2007-12-26
With a little research I figured out that I did type in the right thing. This is what comes up for "Network Controller"

03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

So I have a Broadcom BCM4306. The restricted driver (firmware) I installed was for broadcom 43xx, so it should be working right?

---

### Post by rustybronco on 2007-12-26
Yes it should be working correctly, that does not mean it is.
can you post the output of...
lshw -C network
and
iwlist scan 

also these links may be of help
[http://ubuntuforums.org/showthread.php?p=2431305#post2431305](http://ubuntuforums.org/showthread.php?p=2431305#post2431305)
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
 [http://ubuntuforums.org/poll.php?do=showresults&pollid=2252](http://ubuntuforums.org/poll.php?do=showresults&pollid=2252)

---

### Post by doublez on 2007-12-26
For lshw -C network I get (just the wireless part)...

       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:0c:41:2c:e8:a7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

for iwlist scan I get (just the wireless part)...

eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:75:46:BD
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-43 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 84ms ago


I did some searching and I found a few things that could help me. One was ndiswrapper. From what I read I install this then use it to install the windows driver. Is that right?

---

### Post by rustybronco on 2007-12-27
> **doublez said:**
> 
       configuration: **broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic** 
for iwlist scan I get (just the wireless part)...

eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:75:46:BD
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-43 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 84ms ago


I did some searching and I found a few things that could help me. One was ndiswrapper. From what I read I install this then use it to install the windows driver. Is that right?Don't jump to ndiswrapper just yet... The driver is installed and the card can see a wireless network  "linksys", are your router and wireless card using the same encryption? if so you may want to try and turn encryption off in both the router and in the network manager and see if you can connect.
read kevdogs finest in my signature when you get a minute, about connecting from the command line (network manager can be flaky at times ) that may help in the interim, time for me to get some sleep, but i'll be checking back in the morning.

---

### Post by doublez on 2007-12-27
I tried connecting with no encryption and it still just timed out trying to connect. I'll read through that link tomorrow.

---

### Post by rustybronco on 2007-12-27
You may then want to try the ndiswrapper method.
one method [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

reading material...
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

***edit *** is mac address filtering on in the router? (yes I know a dumb question, but it needs to be asked)

---

### Post by doublez on 2007-12-27
Yeah I have mac filtering on, but I made sure the address of the card is on the routers ok list and I tried connecting with it turned off. I tried connecting with no security and it timed out.

I'll try those links sometime today and I'll post my results.

---

### Post by doublez on 2007-12-27
I tired using ndiswrapper with the guide you posted and didn't get anywhere, but I don't know if I did it right either.

---

### Post by rustybronco on 2007-12-27
Which guide?

---

### Post by doublez on 2007-12-27
This one - [http://ubuntuforums.org/showthread.php?t=475963]("http://ubuntuforums.org/showthread.php?t=475963") - I don't know if I did some of the steps right so I uninstalled everything and I guess I'll try a different how to.

---

### Post by rustybronco on 2007-12-27
Go with kevdogs ndiswrapper on a fresh install if possible. [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
you do have the correct drivers for that card, correct?

---

### Post by doublez on 2007-12-27
I actually started that one but I ran into a problem because I didn't have the driver. Where should I get it from? Would it be safe to take the .exe of this site ([http://www.linuxant.com/driverloader/drivers.php]("http://www.linuxant.com/driverloader/drivers.php"), one of the first ones a search came up with) or should I take the one out of this guide ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851"))?

---

### Post by doublez on 2007-12-28
I'm working on this guide ([http://ubuntuforums.org/showthread.php?t=574501]("http://ubuntuforums.org/showthread.php?t=574501")) and I'm stuck at creating and placing the driver in ~/driver. I made the folder, but when I do the step after that 
      *****@Laptop:~/driver$ sudo ndiswrapper -i bcmwl5.inf
It says...
      couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

I downloaded the .exe to the driver folder and extracted it. I don't get how to do these steps.Ideas?

---

### Post by rustybronco on 2007-12-28
> Next create and **place** your Window's wireless driver into ~/driver:

```

cd ~
mkdir driver "Make the directory"
cd driver  " Change to the **driver** directory" 
```

you did change to the directory first and then placed the drivers into it, correct?

---

### Post by kevdog on 2007-12-28
Here is an example I found off Jamie Jacksons tutorial.  I think you need to install the cabextract utility or simply unzip the file on a windows machine and then bring the files over on a usb stick:

(Note: If you get "Couldn't find package cabextract" after line one, then [WWW] enable the "universe" repository. Then, re-run line one.)

sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
cabextract sp33008.exe

---

### Post by rustybronco on 2007-12-28
> **doublez said:**
> I downloaded the .exe to the driver folder and extracted it. 
missed that...

linksys web site for drivers [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download)
just in case

---

### Post by doublez on 2007-12-28
I think the problem is that I didn't use the terminal to download and extract the driver. I'll have to do what kevdog posted.

---

### Post by doublez on 2007-12-28
> **kevdog said:**
> Here is an example I found off Jamie Jacksons tutorial.  I think you need to install the cabextract utility or simply unzip the file on a windows machine and then bring the files over on a usb stick:

(Note: If you get "Couldn't find package cabextract" after line one, then [WWW] enable the "universe" repository. Then, re-run line one.)

sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
cabextract sp33008.exe


I run the step "wget...." and it does some things then gets to "==> PASV ... ". What is it doing because it doesn't seem like anything is happening.

---

### Post by kevdog on 2007-12-28
You are right about the pasv thing.  Just ftp into the server as anonymous with no password and download the file.  Here is the entire link:

ftp ftp.compaq.com
cd /pub/softpaq/sp33001-33500
get sp33008.exe

---

### Post by doublez on 2007-12-28
That worked and I got the file, now do I just move it into the driver folder and continue with the guide or do I have to extract it or something?
Thanks for all the help so far.

---

### Post by kevdog on 2007-12-28
Try the cabextract utility.

---

### Post by doublez on 2007-12-28
cabextract worked, but now I get this..

zach@Laptop:~/driver$ sudo ndiswrapper -i bcmwl5.inf
[sudo] password for zach:
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmwl5 ...
couldn't get manufacturer section - installation may be incomplete
zach@Laptop:~/driver$ ndiswrapper -l
bcmwl5 : invalid driver!

Now what do I do?

---

### Post by kevdog on 2007-12-29
Find another linksys driver -- possibly from the linksys web site.  Obviously that driver is no good!

---

### Post by rustybronco on 2007-12-29
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download#versiondetail)

> Driver Version 3.100.64
- supports version 3 hardware
- Adds SecureEasySetup support
- Compatible with hardware version ** 1.0, 1.1, and 3 only.**  Version 2 hardware, please use driver version 6.0.0.18

when you download and extract (unzip) the zip file from the linksys download link
these should be what you are looking for.

---

### Post by rustybronco on 2007-12-29
continuing...

---

### Post by rustybronco on 2007-12-29
drivers...

---

### Post by doublez on 2007-12-29
I finished kevdogs guide and it didn't work. It still says the driver being used is the bcm43xx and I blacklisted unenabled it under the restricted drivers, etc and it just won't work. I might come back to this someother time but for now I'll just have to be without wireless. Thanks for all the help anyways. I appreciate it.

---

### Post by rustybronco on 2007-12-29
The offer for the wusb v2 still stands...

---

### Post by kevdog on 2007-12-29
Again this will not make the changes permanent, however if you want to quickly switch between drivers, this is the way to do

sudo ifconfig <interface> down
sudo modprobe -r bcm43xx
sudo modprobe ndiswrapper
sudo ifconfig <interface> up

---

