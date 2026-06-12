---
title: "Is it possible to get a linksys WUSB11v4 adapter to work?"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by SunnyRabbiera on 2008-02-28
Alright I have someone new to convert to linux but heres the thing, everything works except internet on her machine and she can only do wireless...
I have seen some topics on this particular model but none of them seem to cover gutsy.

---

### Post by SunnyRabbiera on 2008-02-28
Bump

---

### Post by myddewji13 on 2008-02-28
i dont see why not...try it with ndiswrapper and xp/win 2000 drivers the worst thing that happens is you are back to square 1

---

### Post by SunnyRabbiera on 2008-02-28
well I have read up on ndiswrapper but have found nothing real useful concerning this.
I am going to give ndiswrapper a shot but I dont know if it will work.

---

### Post by rustybronco on 2008-02-28
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

> 
   1.
      Card: Linksys WUSB11v4, 802.11b, USB 1.1

      usbid: 13B1:000B
    *
      Chipset: M4301A, made by Ali
    *
      Driver: Linksys Windows XP driver from [ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe](ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe) (driver is not available through [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp)). Install with WUSB11v4.inf
    *
      Other: Works with snapshot of 2005-08-21.

you may have to use wicd or wifi radar instead of NM.

---

### Post by SunnyRabbiera on 2008-02-28
> **rustybronco said:**
> [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)



you may have to use wicd or wifi radar instead of NM.

Alright will will try that
first I will try wifi radar as its in the repository and I can transfer the packages needed to an external hard drive and install them onto the other computer.
wicd is out of the question I guess as it says you need to add a repo to use it and I cant use repos if I dont have a connection eh?
But is there anything else I need to do or learn?

---

### Post by rustybronco on 2008-02-28
maybe read Kevdog's tutorial on ndiswrapper. plus the drivers from the last post I linked.
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by SunnyRabbiera on 2008-02-28
alright it seems that I do have what I need as it seemed to install...
however the adapter is not connecting to anything nor does it seem to be functioning...
is there a next step?

---

### Post by rustybronco on 2008-02-28
did you have any error messages when you installed ndiswrapper and the drivers?

post the output of **ndiswrapper -l**
**lshw -C network**
**iwlist scan**

---

### Post by SunnyRabbiera on 2008-02-28
I will have to go onto the other computer for errors...
maybe tomorrow I will hook the other computer to my modem and try working this from there.

---

### Post by SunnyRabbiera on 2008-02-29
bump

---

### Post by SunnyRabbiera on 2008-02-29
bumpity bump

---

### Post by SunnyRabbiera on 2008-02-29
bumpity bump bump...
hello?

---

### Post by Ivorydawn on 2008-02-29
Post the output of the commands that rustybronco suggested, it will make life much easier for someone trying to help you.

---

### Post by SunnyRabbiera on 2008-02-29
I know, I am just trying to keep this from going into the abyss just in case I have problems

---

### Post by rustybronco on 2008-02-29
stickey it, or put in your favorites.

---

### Post by SunnyRabbiera on 2008-02-29
alright here is what I got:
ndiswrapper -l
lspmusb: driver installed
netusb: driver installed
wusb11v4: driver installed
device  (13B1:00B) present

but here is what I got when typing in iwlist scan:

lo interface doesnt support scanning

---

### Post by rustybronco on 2008-02-29
still need to see **lshw -C network** please.
and if you would be so kind **iwconfig**

---

### Post by SunnyRabbiera on 2008-02-29
well there was no error with lshw -C network
it just wizzed by with no errors or anything

---

### Post by rustybronco on 2008-03-01
> **SunnyRabbiera said:**
> well there was no error with lshw -C network
it just wizzed by with no errors or anything
No It should have shown something like this.
```
WARNING: you should run this program as super-user.
  *-generic DISABLED      
       description: IRDA interface
       product: FIR Port Type-DO
       vendor: Toshiba America Info Systems
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: irda0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list irda logical
       configuration: driver=donauboe latency=64 module=donauboe
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:14:a5:d4:94:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.2.101 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

Not looking for errors, i'm looking for information.

---

### Post by SunnyRabbiera on 2008-03-01
I got none, it just wizzed by and gave no output

---

### Post by rustybronco on 2008-03-01
Based on the available information given, this is what I see.

Yes it is possible to get a WUSB-V4 working, the (only?) way would seem to get it up and working is by using ndiswrapper + the proper drivers. it has been done sucessfully in the past no reason it won't again.

Your drivers appear to be loaded properly and the device is being recognized.
> alright here is what I got:
ndiswrapper -l
lspmusb: driver installed
netusb: driver installed
wusb11v4: driver installed
device (13B1:00B) present hopefully one was an inf and the other was a sys.

you said you were going to try wifi radar from the repositories, if wifi didn't work then try connecting from the command line. details on how to do it can be found in Kevdog's guide. [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) 
but you still will need to find the device name such as wlan1,wifi0, eth0 ect. 

you can try a different wireless manager such as wicd, [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
but if wifi radar didn't allow you to connect, wicd might not ether.

as far as lshw- c network not providing any output, I would check the cd used to install linux for errors and if none are found, search for like problems on launchpad, if still none are found, please file a bug.
on 100+ installs I have not seen it do that, not impossible, but very odd.

---

### Post by SunnyRabbiera on 2008-03-01
well for the system I used linux mint, do you think this might be a mint issue?
I can get the live back on there and check for errors.
as for that guide I will try it out.

now if lshw doesnt work does it mean I have to re install the whole system again?

---

### Post by rustybronco on 2008-03-01
> **SunnyRabbiera said:**
> well for the system I used linux mint, do you think this might be a mint issue?
now if lshw doesnt work does it mean I have to re install the whole system again?No ndiswrapper will work fine on linux mint.
No reinstall is needed, a simple **sudo apt-get install lshw** should do nicely.

---

### Post by SunnyRabbiera on 2008-03-01
alright, I will have to wait for a bit to get the external hard drive I share with my husband, I cant very well install it if I dont have a connection now :D

---

### Post by SunnyRabbiera on 2008-03-01
alright I reinstalled the package and stuff...

but nothing, I dont have any output using lshw -C network.

So what next? I know lshw works as it seems to list things when I hook the computer up to my cable modem but when I just have the usb adapter in it doesnt do a thing... its plugged in right and this adapter has worked in the past.
So what is going on here and is there any way I can fix it?

---

### Post by rustybronco on 2008-03-01
I see you have asked on the mint forums about your device, I don't use mint but it seems you may have to preface the command with sudo in mint (why I don't know ). what version of mint are you installing?
I may download it have a look see if it will list my hardware.

---

### Post by SunnyRabbiera on 2008-03-01
but I did, I typed in the command as sudo lshw -C network

I have no idea why this is not working, ubuntu and mint are essentially the same

---

### Post by rustybronco on 2008-03-01
> **SunnyRabbiera said:**
> but I did, I typed in the command as sudo lshw -C network

I have no idea why this is not working, ubuntu and mint are essentially the same99% the same...
what terminal are you running these commands in?

---

### Post by SunnyRabbiera on 2008-03-01
I am using the standard terminal for ubuntu and gnome... the same one in your screenshot except yours is for hardy mine is for gutsy (Terminal 2.18.2)
what do I have to use something else?

---

### Post by rustybronco on 2008-03-01
Just making sure... no output in the terminal for lshw -c network (or lshw)  is bugging me to no end.
and I don't have an answer for it.
Maybe someone has the answer why.
down loading mint 4.0 as I type.

---

### Post by SunnyRabbiera on 2008-03-01
but the thing is mint uses the same version of lshw as ubuntu does... most of it is the same so none of this makes sense to me.
I know the mint team mods some things but I see no reason for this not to work.
If anything I would expect this sort of thing to happen in gutsy more then mint, though this still might be a gutsy issue in the end.
I hope not, as I want this to work for my friend and I dont want them to go back to XP just for this, not after all the hell it put them through

---

### Post by rustybronco on 2008-03-01
You could always try another distro, but I don't see any that will work ootb with that device. all that I have found use ndiswrapper+drivers.
what about 7.04,  ndiswrapper+ the drivers. 
did you check the cd for errors and do a reinstall? the first time I downloaded mint today the file was corrupt so i'm am trying a different location.
Other than the problem is above what I am capable of without it in front of me.

---

### Post by SunnyRabbiera on 2008-03-01
the CD is fine, all checks out.
I know this doesnt work out of the box no matter what I use.
using feisty I dont know, I never had luck with it and I dont see a way of downloading it.
look I know the system on the other computer is fine, but this is getting frustrating.
The only thing I did was use the lighter version of mint as the normal version is too slow on the other computer as its older, but from the looks of it the light version is no different then the normal version except it has no desktop effects (as the other computer is a bit old for that sort of thing), but at the core its all the same thing.

---

### Post by rustybronco on 2008-03-02
[quote=SunnyRabbiera]the CD is fine, all checks out.[/quote]How right you are, that is because the command in mint is 
**lshw -class network** 
lshw -c network gave me usage of lshw, man lshw would had done the same.
lshw showed my network, you may have had to scroll back to find it. 
```
 *-network
          description: Wireless interface
          product: RT2600 802.11 MIMO
          vendor: RaLink
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: wmaster0
          version: 00
          serial: 00:16:b6:59:90:aa
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=rt61pci ip=192.168.2.105 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
```what guide did you follow to install ndiswrapper?
kevdog's guides are some of the best...[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

when you installed ndiswrapper you had no errors and the install went fine correct?

check for dmesg errors **dmesg | grep ndiswrapper**

can you see the networks with networkmanager?

using wifi radar can you see the networks?

have you tried this guide yet? [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by SunnyRabbiera on 2008-03-02
yeh I followed the guides I found on the net, ndiswrapper was actually an easy one as mint came with it loaded by default.
and no I dont see the networks with network manager
same with wifi radar.

---

### Post by SunnyRabbiera on 2008-03-02
nope the new command doesnt do squat...
so if this command is not working I guess I have to use gutsy or something on the other computer????

I am not getting this

---

### Post by SunnyRabbiera on 2008-03-02
alright i broke down and installed gutsy on the other computer, and you know what?
still nothing...

what the @#$%^&

---

### Post by SunnyRabbiera on 2008-03-02
alright I am thinking that this command is not what I need as this is a USB adapter

did you factor that?

---

### Post by rustybronco on 2008-03-02
Yes...  with the very first post you made in this thread. the title said the device and version.

"w"=wireless "usb"=usb "11"=11mbps... chipset is an ali m4301a, linksys page [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper)

download page for drivers ect...  [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859929435&packedargs=sku%3DWUSB11&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2943529435B01&displaypage=download](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859929435&packedargs=sku%3DWUSB11&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2943529435B01&displaypage=download)
I have even downloaded the .exe for it on to my laptop.

it appears  that it will only use up to wep128 encryption (no wpa ect. )

looks just like my wusb54g v4.

just because the wusb11 worked at one time doesn't mean it's working now, keep that in mind. 
but ndiswrapper said device was found so that is a good sign!

one last time... try this guide step by step, and let us know if you have any **errors or difficulties or if you are unsure of the next step** and at what step you had the question/errors/difficulties..
just saying that you tried something and it doesn't work doesn't give anyone a clue on how to help you get that device up and working. 

This guide------> [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

or if you choose a different how-to, post a link to it, so someone can follow along with you.

or you can find a device that is plug and play with your chosen operating system. and smile :)

---

