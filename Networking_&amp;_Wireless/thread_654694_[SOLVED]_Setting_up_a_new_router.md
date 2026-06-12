---
title: "[SOLVED] Setting up a new router?"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by silent the spy on 2007-12-31
Hi, Ive been on Ubuntu for a while now after a huge windows crash. If I have a choice I do not want to go back !  my problem now is I bought a Netgear router WGR614 yesterday and I have no idea how to set it up. I have no LAN connection on my pc so I cant set it up by hardwire. Im left doing it wireless. 

Yesterday I tried the set up instructions on this forum but could only get the WG111 wireless dongle to see the alternative driver.... in the end I gave up and upgraded a minute ago to Gutsy  7.10 so everything is super fresh LOL


what I need is a total walk through please. Im familiar with terminals. My WG111 vs2 (ID 0846:6a00) is recognised at this moment without installing ndiswrapper

I'm a complete nube at routers but I think my router needs setting up as I plugged xbox 360 using LAN and it wouldn't connect.. 

I'm just about ready to take the thing back but I know Ubuntu can do this :)


thanks for any help
john

---

### Post by rustybronco on 2007-12-31
Open up a browser and type in 192.168.1.1, there should be a log in screen, user... admin, password... password, from there you can go to the wireless settings

---

### Post by silent the spy on 2007-12-31
I get nothing. At the moment im using my wired connection straight into my modem. 

I have the WG111 plugged in. Today there is no flashing light. I have no idea how to access the router. Sorry if I sound dumb... I am :)  this router stuff is completly new

---

### Post by rustybronco on 2007-12-31
> **silent the spy said:**
> my problem now is I bought a Netgear router WGR614 yesterday and I have no idea how to set it up. I have no LAN connection on my pc so I cant set it up by hardwire. Im left doing it wireless. 
thanks for any help
john
Wireless is not enabled by default in the router, you have to acess setup by cable at first, then you can enable the wireless settings. It's not a problem with ubuntu, that is the way you have to do it.
Take it to someone that has a ethernet nic, hook up to the router and set up the wireless (enable wireless, essid, security, mac addresses ect. ) , then take 'er home and use it.
or buy an ethernet card and do it yourself.
Dale.

---

### Post by silent the spy on 2007-12-31
Thanks Dale. Thats what I thought I'd have to do, though I had hoped there was a way around seeing as it comes with a set up cd... optimised for windows of course :(  great how they can do it wirelessly :-x:-(

john

---

### Post by rustybronco on 2007-12-31
> **silent the spy said:**
> Thanks Dale. Thats what I thought I'd have to do, though I had hoped there was a way around seeing as it comes with a set up cd... optimised for windows of course :(  great how they can do it wirelessly :-x:-(

johnNot unless something has changed in the last 1-1/2 years since I bought mine, you always had to set it up through a ethernet cable to turn on and set up  the wireless features. both my netgear and linksys routers are that way.
you said in the manual one can connect to the router wirelessly through windows ootb?, what version do you have? (I have a wgr614-v6)

---

### Post by silent the spy on 2008-01-01
v7

I was reading the manual on the cd and I guess ive read it wrong?  I read and interpreted that you plug in the router to the electric mains, (no talk of a hard wire to pc), put the cd in your windows pc, windows installs the software, asks you to plug in the dongle and then shows a list of wireless connections, you connect to the router/access point and all is fine and dandy. But like I say I am totally new at this wireless stuff and had hoped there was a similar way to do it on Ubuntu

Thanks for your help, much appreciated

john

---

### Post by ugm6hr on 2008-01-01
I think your USB wifi card needs ndiswrapper to work (although there is a native driver).  The *lsusb* output merely tells you that Linux recognises that it is plugged in, not that it is configured to work.  This might help:
[http://ubuntuforums.org/showthread.php?t=615568](http://ubuntuforums.org/showthread.php?t=615568)

Once the USB dongle is working, you should find it easy to configure with a few clicks from Network Manager in Ubuntu, and then going to the web address (something like 192.168.0.1) in Firefox.  I have never had a Netgear router before, but most routers have wifi pre-configured with no encryption so that you *can* configure them without wired ethernet (although it is a *lot* easier using wired ethernet).

---

### Post by silent the spy on 2008-01-01
Just what I needed! thanks its flashing now. rtl8187 is gone from the list. ndiswrapper is loaded. That part was easy to follow but I have no idea how to do the rest. I cant set up my router at all. I really do need a step by step guide please. I have looked at Network manager but like I say honestly have no clue... but im ready to learn if someone can help please?


john

---

### Post by ugm6hr on 2008-01-01
OK.  I should be able to help.

Give me a few minutes to see if your router's manual is available online.  It will make things a lot easier.

But before I start - have you made any changes to the router at all?

And you will need the manual with you...

---

### Post by silent the spy on 2008-01-01
Ok thanks a million! :)

Ive made no changes to the router. This is as far as ive gotten.

---

### Post by silent the spy on 2008-01-01
heres the page for my router with the manual available on the left side, if you havent found it that is :)

[http://kbserver.netgear.com/products/wgr614v7.asp](http://kbserver.netgear.com/products/wgr614v7.asp)

---

### Post by ugm6hr on 2008-01-01
I am assuming you are using Ubuntu 7.10 (Gutsy), and haven't changed the default desktop.  The Netgear Manual is a bit unclear on whether the wifi is preconfigured, but I suspect it it.

Plug the router into the mains and phone socket, and turn it on.

There should be a networking (Network Manager) icon in the top right panel (see pic) - it will either be a computer screen or 4 grey bars.

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

If you right-click on it and make sure that *Enable Network* & *Enable Wireless* are ticked (if not - left click on them).

Then left-click on the same icon, and you should get a drop-down list like in the picture.  One of the options should be your network, which should not have a padlock symbol, and is probably called something like *netgear*.  Left-click on this entry, and a new option dialogue will open.  Select *None* for encryption, and then click Connect.

Right-click the same icon again, and select *Connection Information*.  Hopefully this will now have an IP address listed (that is something like 192.168.1.2).

Open Firefox and go to the following web address:
**[http://192.168.1.1](http://192.168.1.1)**
When prompted, enter **admin** for the router user name and **password** for the router password,
both in lowercase letters. (For security reasons, the router has its own user name and
password).

Now you should be able to use the manual to set up your wifi security and enter your ISP settings.  

Take note of this: If you are configuring the router from a wireless computer and you change the router&#8217;s SSID, channel, or security settings, you will lose your wireless connection when you click Apply. You must then change the wireless settings of your computer to match the router&#8217;s new settings.

Hope that gets you up-and-running.

---

### Post by silent the spy on 2008-01-01
Ubuntu 7.10 installed yesterday. Nothign altered as far im im aware.


When I click the little tv monitor in the right top corner I don't get that box like yours. I get a list  

wired network (dot in it as im using it now)
wireless network  (nothing no box to tick)
________________________________________

connect to other wireless network...
create new wireless network....
manual configuration

---

### Post by ugm6hr on 2008-01-01
Just need to check that the USB dongle is working:
```
iwconfig
ifconfig
```

Post output.

EDIT: Can you enable wireless and network if you right-click?

EDIT2: If you go to manual configuration, what settings do you have - I use roaming mode for wireless (see pic).

---

### Post by bigken on 2008-01-01
the address for netgear is 192.168.0.1 not 192.168.1.1 when you enter router just run the wizard

---

### Post by silent the spy on 2008-01-01
```
eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@charlie:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:80:C9:60:C1  
          inet addr:82.46.48.91  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:80ff:fec9:60c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:864773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163364550 (155.7 MB)  TX bytes:7438170 (7.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4955 (4.8 KB)  TX bytes:4955 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:2F:ED:59:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```


right click, Both boxes are checked, sorry forgot to post last time.

EDIT :  yep same as you, roaming mode enabled. Im not picking up any wireless networks. I can with my psp but even that isnt picking up the netgear

---

### Post by ugm6hr on 2008-01-01
One more:
```
lshw -C network
iwlist scan
```

PS: I thought you said you don't have an ethernet port?  You are currently connected with ethernet.
Maybe try unplugging the ethernet cable and seeing if it will scan.  Perhaps a restart is in order too (funny how that fixes things sometimes).

Edit:
If your PSP doesn't pick up your Netgear - then it clearly isn't broadcasting...  Looks like you have to use ethernet to set it up.

---

### Post by silent the spy on 2008-01-01
> **ugm6hr said:**
> 
PS: I thought you said you don't have an ethernet port?  

I dont have an ethernet port on my pc. 

> You are currently connected with ethernet.

no usb from my modem to my pc

> 

Edit:
If your PSP doesn't pick up your Netgear - then it clearly isn't broadcasting...  Looks like you have to use ethernet to set it up.

but it should be broadcasting as thats how windows would install?

should I try factory resetting it and see what happens. (Little button on the back in a hole)

---

### Post by ugm6hr on 2008-01-01
> **silent the spy said:**
> should I try factory resetting it and see what happens. (Little button on the back in a hole)

Yes.

---

### Post by bigken on 2008-01-01
what i want to know is if you have no ethernet what is eth0 

and if it is a ethernet port just use the cable to setup the router 1st then move onto the wirless

---

### Post by rustybronco on 2008-01-01
router set up on my netgear is 192.168.1.1 
screen shot of the login (admin), password ( default is"password" ) and some setup screens.

---

### Post by silent the spy on 2008-01-01
still not transmitting. could I have a duffer, is that possible?

---

### Post by ugm6hr on 2008-01-01
> **silent the spy said:**
> still not transmitting. could I have a duffer, is that possible?
Yes.
Hmmm... Does your PSP pick up any other local wifi networks?

---

### Post by silent the spy on 2008-01-01
I havent got a LAN port its closed over. Next to it is my USB port. Thats what im using for internet from my modem a USB cable. If I had a LAN port I would just plug it into the router. The only LAN connection port I have is on my xbox360

---

### Post by silent the spy on 2008-01-01
> **ugm6hr said:**
> Yes.
Hmmm... Does your PSP pick up any other local wifi networks?

yes its working fine. I can pick up several different ones round the house. Only one has no security. My pc picks up none and my router netgear is not transmitting even with my psp next to it, nothing

---

### Post by ugm6hr on 2008-01-01
> **silent the spy said:**
> yes its working fine. I can pick up several different ones round the house. Only one has no security. My pc picks up none and my router netgear is not transmitting even with my psp next to it, nothing

Do all the lights come on?  The router should have wifi on by defualt - it certainly doesn't suggest that isn't the case in the manual.  I'll have another look now.

If your PC is still not picking up any local networks - then the USB dongle isn't working either.  Maybe try Wicd (instead of NM) - see the link below.  Won't solve the Router problem though.
These commands will give info re: USB:
> lshw -C network
iwlist scan

EDIT:
In the picture - the circled light should be on - it indicates that wifi is broadcasting.

---

### Post by bigken on 2008-01-01
the wireless could be dissabled in the router is there green light on that looks like a radar ?

---

### Post by silent the spy on 2008-01-01
> **ugm6hr said:**
> Do all the lights come on?  

power light, test light. internet light, LAN lights all work but no wireless light even after resetting

> 
The router should have wifi on by defualt - it certainly doesn't suggest that isn't the case in the manual.  I'll have another look now.

I think it should be on because of the way windows sets it up using a smart wizard

> 

If your PC is still not picking up any local networks - then the USB dongle isn't working either. 

im not sure. I have to move the psp round the house to get some and they arent strong signals. its certainly is looking, ie blue light flashing now and again

>  Maybe try Wicd (instead of NM) - see the link below.  Won't solve the Router problem though.
These commands will give info re: USB:



thanks I'll need to get the router sorted first. seeing as its still newyears day here in England im stuffed til tomorrow to take it back to PCworld and ask them if its transmitting.

thanks for all your help. very much appreciated. I'll let you know tomorrow what happens

john

edit : no radar, thats the only one not working

EDIT :  the radar light is working because I just did a reset and the test light lights up, when it goes out the radar flashes once. So it is working.

---

### Post by ugm6hr on 2008-01-01
If you could get access to an ethernet connected computer - you could check yourself.  Remember not to mention Linux to PC World - they will blame you (cos they are stupid).

The important thing is it is not broadcasting wifi.

---

### Post by silent the spy on 2008-01-01
> **ugm6hr said:**
> If you could get access to an ethernet connected computer - you could check yourself.  Remember not to mention Linux to PC World - they will blame you (cos they are stupid).

The important thing is it is not broadcasting wifi.

I have no access today so its gonna have to wait til tomorrow. Good advice on PCworld. I would have given them reason to blame me, phew! a close call thanks!

---

### Post by bigken on 2008-01-01
its so sad to say dont tell them your using linux as they will say that is the cause

---

### Post by rustybronco on 2008-01-01
> **silent the spy said:**
> still not transmitting. could I have a duffer, is that possible?**wireless is not enabled by default**
> To Avoid the SmartWizard

   1. Unplug the router power cord.
   2. Turn off the computer.
   3. Plug in the router to power.
   **4. Attach the computer to one of the router's LAN ports.** 
then open up a browser window and type in 192.168.1.1

---

### Post by silent the spy on 2008-01-01
> **rustybronco said:**
> **wireless is not enabled by default**

am I the only one who thinks thats dumb?

---

### Post by rustybronco on 2008-01-01
> **silent the spy said:**
> am I the only one who thinks thats dumb?**No...**
starting from the word "netgear" you will have leds for power, a check mark (self test), wireless, internet, 1, 2, 3, 4 
the wireless led isn't lit is it? there you go...

---

### Post by silent the spy on 2008-01-01
> **rustybronco said:**
> **No...**
starting from the word "netgear" you will have leds for power, a check mark (self test), wireless, internet, 1, 2, 3, 4 
the wireless led isn't lit is it? there you go...

no wireless led. correct. I should have seen it earlier but I guess I may have thought it would come on through the set up process. I think I thought some how the windows smart wizard did it and if that were the case then maybe there was a way I could do it in Ubuntu. Hey ya cant blame a man for wishing LOL

annoying thing is I chucked out a LAN card a while back, aint it alwyas the way :(

---

### Post by rustybronco on 2008-01-01
> **silent the spy said:**
> 
annoying thing is I chucked out a LAN card a while back, aint it alwyas the way :(might have few lying around...

---

### Post by rustybronco on 2008-01-01
> **silent the spy said:**
> windows smart in the same sentence?

---

### Post by silent the spy on 2008-01-01
> **rustybronco said:**
> in the same sentence?

LOL  it was a typo

---

### Post by silent the spy on 2008-01-01
> **rustybronco said:**
> might have few lying around...

its a long walk from England :D

---

### Post by ugm6hr on 2008-01-01
@silent the spy:
Agree - Netgear are stupid.  The "factory reset" button on my Linksys, Toshiba and Dynamode routers (at various locations) all default to unencrypted wifi on to allow people without LAN to setup.  The Windows Wizard will presumably not work without LAN either, which makes the *plug and play* idea a mockery.

Do you want to try and complete the USB setup (*lshw -C network* & *iwlist scan*)?

Out of interest - if your computer is within cable range of your router, I would actually recommend you use a cable anyway (reliability / speed).  PCI Ethernet cards are *very* cheap (and sometimes free on freecycle).

---

### Post by silent the spy on 2008-01-01
> **ugm6hr said:**
> 

Do you want to try and complete the USB setup (*lshw -C network* & *iwlist scan*)?

yes please

> 

Out of interest - if your computer is within cable range of your router, I would actually recommend you use a cable anyway (reliability / speed).  PCI Ethernet cards are *very* cheap (and sometimes free on freecycle).

could do, its a pain though. never heard of freecycle, thanks I just checked out my local group. if I cant get one I will see about getting a card tomorrow from a pc shop rather than pc world

---

### Post by ugm6hr on 2008-01-01
Post the output:
```
iwlist scan
lshw -C network
```

The top command should list all available wifi networks, and the bottom should list all network connectors and what driver is being used.

If you don't want to get an ethernet card - do you have access to any computer (e.g. at work / friends etc) with ethernet?  You can just turn the wifi on with any computer (making sure it is not encrypted, the SSID is being broadcast, and that it is set to allow wifi changes to setup), and then do the rest on wifi.

---

### Post by silent the spy on 2008-01-01
```
iwlist scan
```

lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.





```
lshw -C network
```

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:ed:59:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.45+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 00:11:80:c9:60:c1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=82.46.48.91 multicast=yes




> 

If you don't want to get an ethernet card - do you have access to any computer (e.g. at work / friends etc) with ethernet?  You can just turn the wifi on with any computer (making sure it is not encrypted, the SSID is being broadcast, and that it is set to allow wifi changes to setup), and then do the rest on wifi.

Thanks I'll have to do at it a firneds if they have LAN, im self employed

---

### Post by ugm6hr on 2008-01-01
```
wlan0     No scan results

       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.45+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
```

Looks like everything is in order - ndiswrapper being used OK.  Assuming you've used the correct Windows driver in ndiswrapper, that should be OK.

It seems to be scanning, but just can't "see" any networks.  Presumably all the other networks that your PSP can see are not near the computer.  If they are, then there is still a residual issue, which may need sorting out after you get your router to broadcast.

PS: To turn wifi on at a friends, you just need to power it on and plug the ethernet cable into a computer, and go to 192.168.1.1 from browser.  Should be self explanatory from there.

---

### Post by silent the spy on 2008-01-01
> **ugm6hr said:**
>  Presumably all the other networks that your PSP can see are not near the computer. 

one that the psp can see is 10% . I have to hold the psp up against the wall. If I do the same with the dongle I don't get it..

but the psp has to be moved around to find it so im not sure if the dongles working or not.

---

### Post by ugm6hr on 2008-01-01
> **silent the spy said:**
> one that the psp can see is 10% . I have to hold the psp up against the wall. If I do the same with the dongle I don't get it..

but the psp has to be moved around to find it so im not sure if the dongles working or not.

Hmmm.... Not worth worrying about it if the PSP only just picks it up.  It'll be apparent when you've got your own signal to pick up.

If you are going to be on your computer for a while, you can just repeat the *iwlist scan* multiple times (up arrow repeats last command in Terminal) - it may just catch a signal intermittently.  But don't get obsessed by it!  A reboot may be necessary too.  Also uncertain whether the USB network connector interferes (maybe try it with the USB cable modem unplugged).

Either way - probably best to leave things until the router is broadcasting its SSID.

---

### Post by bigken on 2008-01-01
this whole issue is due to lack of a network card give yourself a break and try again when you get a network card then you will see just how easy this is to setup :)

---

### Post by silent the spy on 2008-01-02
afternoon :-)

I bought a card, thought I may aswell have it just incase of future problems. Thing is I dont know how to install the driver that came with it. It is a Linux driver so hopefully everything runs smooth. I  dont understand the part in blue, how to copy the driver. 



*************************************************

**   Silan SC92031 PCI  Fast Ethernet Adapter  **

**                                             **

**   LINUX driver                              **

*************************************************



Introduction:

=============



    The instructions are for linux driver installation. You must

    compile the source code to generate sc92031.o and use insmod command to

    insert sc92031.o as module.



Contents of the Subdirectory:

=============================



    readme.txt                This file.

    sc92031.c                 The linux core driver source code file

    Makefile                  Makefile for generating driver object file

    

Kernel Supported

================

    This driver support linux kernel version 2.4.x/2.5.x now.



Installation

============

    1) Create a temporary directory:

        # mkdir /temp



    2) Change to the temporary directory:

        #cd /temp



    3)[COLOR="Blue"] Copy driver (sl_linux.tgz) from CD-ROM to the temporary directory[/COLOR], and follow the commands: 

       # mount -t iso9660 /dev/cdrom /mnt

       # cp /mnt/sl_linux.tgz /temp



    4) untar the archive file:

       # tar xzvf sl_linux.tgz

       # cd sc92031

    

    5) Compile the driver source files and it will generate sc92031.o, and

       copy it to correct driver installation path (The installation directory

       is different in different kernel versions. In 2.4.x kernel, the path is 

       /lib/modules/KERNEL_VERSION/kernel/drivers/net/, and in 2.2.x kernel,

       the path is /lib/modules/KERNEL_VERSION/net/)

       # make install



    6) Check configuration file (/etc/modules.conf or /etc/conf.modules,it 

       depend on your Linux distribution) for loading kernel modules. Make sure

       there is the following content in the configuration file, where # is 

       interface number :

        alias eth# sc92031 

  

    7) Reboot now:

        shutdown -r now 



    8) Install your driver module (If the driver module is in the wrong place,

       an error message will appear, and say that can't find the driver 

       module):

        insmod sc92031.o



    8) Use ifconfig command to assign the IP address, where # is network 

       interface number:

        ifconfig eth# <IP>



    9) Check the interface works:

        ping <remote_host_IP>

---

### Post by ugm6hr on 2008-01-02
Have you tried just plugging the PCI ethernet (presumably it is PCI) card in and turning the computer on?

I suspect it will just work.  Interestingly, the driver says it supports kernel 2.4 / 2.5, whereas Ubuntu (and the majority of modern Linux ditros) uses kernel 2.6.  Presumably, the driver was just included in the kernel for 2.6.

---

### Post by silent the spy on 2008-01-02
> **ugm6hr said:**
> Have you tried just plugging the PCI ethernet (presumably it is PCI) card in and turning the computer on?

I suspect it will just work.  Interestingly, the driver says it supports kernel 2.4 / 2.5, whereas Ubuntu (and the majority of modern Linux ditros) uses kernel 2.6.  Presumably, the driver was just included in the kernel for 2.6.


Yea I tried it. Computer froze. On re boot it wanted to boot from CD so I did. Then/now it boots from a list, (forgive my ignorance im still learning)  has a count down to boot from the first/top one ubuntu 7.10 I think. It lights up when I plugged in the LAN cable but I couldnt acces the router from a browser so I presumed it needed the driver. Its a nice headache, atleast im learning something LOL

EDIT : and the USB dongles stopped flashing :-D

---

### Post by bigken on 2008-01-02
remove the usb dongle remove the cd and boot the system with the network card  connected to your router tell us what happens

---

### Post by silent the spy on 2008-01-02
> **bigken said:**
> remove the usb dongle remove the cd and boot the system with the network card  connected to your router tell us what happens

nothing. The light on the router comes on, channel 1 I had it plugged into. On the pc nothing, no network found from the tv, goto manual configuration shows a hardwire is it? with the usual roaming etc. Network tools shows no ethernet device only a loopback interface.

my usb cable connection is playing up now. It wont plug and play like before. Im having to reboot. on reboot It been moved to etho 1 and I cant start firestarter anymore, No etho 0
 I use firestarter as I haven't figured out how to make IP tables run any other way. Yep still learning :-)

john

---

### Post by bigken on 2008-01-02
ok unplug your usb modem and dissable any firewalls with a router you dont need a firewall


when you done all this reboot and run this command 

lshw -C network

---

### Post by silent the spy on 2008-01-02
> **bigken said:**
> ok unplug your usb modem and dissable any firewalls with a router you dont need a firewall

Ive got no firewalls running as it wont start, it says theres no device. My usb modem was unplugged, still nothing. All I had in was my router, my keyboard (non usb) my mouse (usb) 

john

EDIT. ok I'll try that command on reboot

---

### Post by bigken on 2008-01-02
and your using roaming yes 


did you try the  lshw -C network     ?


Just a though try the routers ip address in your browser (192.168.0.1 or 192.168.1.1)

---

### Post by silent the spy on 2008-01-02
> and your using roaming yes 


yep

> 

did you try the  lshw -C network     ?

sorry for the delay, my USB modem is messed up and I forgot to put cable in so re boot after re boot. can we swear on this message board LOL


lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 01
       serial: 00:a1:b0:01:06:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sc92031 driverversion=2.0c latency=32 maxlatency=40 mingnt=20 module=sc92031 multicast=yes





> Just a though try the routers ip address in your browser (192.168.0.1 or 192.168.1.1)

I tried that nothing, no netwrok so came up with the usual cant find page

---

### Post by bigken on 2008-01-02
ok lets install the driver when you load the cd copy and paste the diver file onto your desktop right click the tgz file and select extract here then open a terminal 
and type 

cd Desktop

then 

cd sc92031(name of extracted file/folder)

then 

make install 


you might have to use sudo 

if you swear you will get your hand slapped :lolflag:

---

### Post by silent the spy on 2008-01-02
Ok im not swearing honest :-)  but you may... at me LOL  I dont understand this part 


~/Desktop/sc92031$ make install
Makefile:37: *** Linux kernel source not configured - missing config.h. Stop.

EDIT. Even using sudo same result

---

### Post by bigken on 2008-01-02
try configure.sh

---

### Post by silent the spy on 2008-01-02
bash: configure.sh: command not found

---

### Post by bigken on 2008-01-02
its being so long since i did this try 

./configure

---

### Post by silent the spy on 2008-01-02
bash: ./configure: No such file or directory


its ok to swaer at me, I understand LOL

---

### Post by bigken on 2008-01-02
can you post a list of the file in the driver folder

try install.sh

---

### Post by silent the spy on 2008-01-02
txt ??????? (??? are in diamonds for some reason)
make file
read me.txt
sc92031.c

---

### Post by bigken on 2008-01-02
read your private messages

try make

also take a look at this 

[http://www.linuxsurf.com/forum/viewtopic.php?t=4465](http://www.linuxsurf.com/forum/viewtopic.php?t=4465)

---

### Post by silent the spy on 2008-01-02
read message thanks. 

Makefile:37: *** Linux kernel source not configured - missing config.h. Stop.

---

### Post by bigken on 2008-01-02
ok try this 

sh  sc92031.c

or 

./ sc92031.c

---

### Post by silent the spy on 2008-01-02
sh sc92031.c

sc92031.c: 1: /*****************************************************************: not found
sc92031.c: 2: sl.c: not found
: not found3: -------------------
sc92031.c: 4: begin: not found
sc92031.c: 5: Syntax error: "(" unexpecte



./ sc92031.c
bash: ./: is a directory

---

### Post by silent the spy on 2008-01-02
is the driver not already in? sc92031 bottom line. 



lshw -C network
WARNING: you should run this program as super-user.
*-network DISABLED
description: Ethernet interface
product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
vendor: Hangzhou Silan Microelectronics Co., Ltd.
physical id: 9
bus info: pci@0000:00:09.0
logical name: eth0
version: 01
serial: 00:a1:b0:01:06:88
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sc92031 driverversion=2.0c latency=32 maxlatency=40 mingnt=20 module=sc92031 multicast=yes

---

### Post by bigken on 2008-01-02
[quote=silent the spy;4059533]yep



sorry for the delay, my USB modem is messed up and I forgot to put cable in so re boot after re boot. can we swear on this message board LOL


[B] lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 01
       serial: 00:a1:b0:01:06:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sc92031 driverversion=2.0c latency=32 maxlatency=40 mingnt=20 module=sc92031 multicast=yes[/B]




this is telling me your adapter is working read the router manual to check the ip address

---

### Post by silent the spy on 2008-01-02
I did. I also checked online on NetGears site. I tried both of their adresses from their website 
[http://kbserver.netgear.com/kb_web_files/n101676.asp](http://kbserver.netgear.com/kb_web_files/n101676.asp)

nightmare!

---

### Post by bigken on 2008-01-02
the tell tale sign was when you said the green light on port one which sort of tells me the card and router are communicating


remove firestater

---

### Post by silent the spy on 2008-01-02
time to give oit a break and get a new card. Look what turned up hmmmm

[http://broadbandforum.in/bsnl-dataone-broadband/3712-dataone-intex-lan-card-linux/](http://broadbandforum.in/bsnl-dataone-broadband/3712-dataone-intex-lan-card-linux/)

[http://ubuntuforums.org/showthread.php?t=517097](http://ubuntuforums.org/showthread.php?t=517097)

[http://ubuntuforums.org/showthread.php?t=640426](http://ubuntuforums.org/showthread.php?t=640426)

[http://ubuntuforums.org/showthread.php?t=162810](http://ubuntuforums.org/showthread.php?t=162810)

thanks for everyones help. I think I need a new LAN card so this one is going back. Case adjorned LOL

---

### Post by silent the spy on 2008-01-11
im back :)  

returned the above card. Shopped around, in the end after some advice I settled on this [http://svp.co.uk/product/edimax_en_minus_9130txl_10_100mbps_lan_pci_adapter_4956](http://svp.co.uk/product/edimax_en_minus_9130txl_10_100mbps_lan_pci_adapter_4956)

Edimax EN-9130TXL 10/100Mbps LAN PCI Adapter is its name in case the above link stops working.

I plugged it in, ubuntu saw it straight away. Though I cant access it. Its there in the top right on the monitor when I click, but its often grayed out/un selectable. When it is selectable I click it and after a few seconds it reverts back to my wired usb network connection. If I remove my usb out of the back of my computer the realtek network also disappears. 

quick recap : With my last card I had a channel light (1,2,3 or 4) on the router when hard-wired but could not access it because I had no network. This time I have no channel light but I have a network.

heres some out put 

```
 lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 01)
00:0b.0 SCSI storage controller: Adaptec AHA-7850 (rev 03)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

```

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 10
       serial: 00:0e:2e:f2:17:6c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:11:80:c9:60:c1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=82.46.48.91 multicast=yes

```


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:80:C9:60:C1  
          inet addr:82.46.48.91  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:80ff:fec9:60c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15435299 (14.7 MB)  TX bytes:817888 (798.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:0E:2E:F2:17:6C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

many thanks for any help :)
john

---

### Post by ugm6hr on 2008-01-11
OK.  The LAN card is working fine.  It has the supported Realtek chipset, and the correct driver is installed.

However, the ip address is provided by the USB network device.  Try *lshw -C network* and *ifconfig* with the USB device unplugged (and the LAN card plugged into the router, with the router on). Remember to turn the computer on **with the USB device unplugged**.

Hopefully, that should assign the new LAN card as eth0, and it should just work.

If not - go to System -> Administration -> Network:
See if there are any Wired Connections listed.  Click on Properties for them, and post screenshots of the Properties page.  It is worth trying turning Roaming On/Off with DHCP on for the Realtek Card (eth1 at the moment).  Roaming has to be Off for the USB device (if listed).

EDIT:
One more thought....  I don't know how you have edited Ubuntu settings to connect with your USB modem.  It is worth unplugging the USB device and restarting the computer with a LiveCD.  That *should definitely* connect to the router.  At least it would confirm all the hardware is working.

If it does - then manual control of the interface should set it up... (where *interface* is **eth0** or **eth1** (representing the Realtek card).  You may also have to *ifconfig down* the USB interface.
```
sudo ifconfig *interface* down
sudo dhclient -r *interface*
sudo ifconfig *interface* up
```

---

### Post by silent the spy on 2008-01-12
> **ugm6hr said:**
> OK.  The LAN card is working fine.  It has the supported Realtek chipset, and the correct driver is installed.

However, the ip address is provided by the USB network device.  Try *lshw -C network* and *ifconfig* with the USB device unplugged (and the LAN card plugged into the router, with the router on). Remember to turn the computer on **with the USB device unplugged**.

Hopefully, that should assign the new LAN card as eth0, and it should just work.

it wouldnt asign the LAN card as etho 0, it remianed etho 1

> 

If not - go to System -> Administration -> Network:
See if there are any Wired Connections listed.  Click on Properties for them, and post screenshots of the Properties page. It is worth trying turning Roaming On/Off with DHCP on for the Realtek Card (eth1 at the moment).  Roaming has to be Off for the USB device (if listed).

I tried turning on/off roaming, it made no difference. USB wasnt listed as I disconnected it like you said. I have plugged it back in now to type. If I set USB etho 0 to roaming OFF I get no internet.

not sure if you mean the attached properties screen shot? (sorry couldn't get the pic to appear here) 


> 


EDIT:
One more thought....  I don't know how you have edited Ubuntu settings to connect with your USB modem.

It was plug and play, I didnt alter anything.

>   It is worth unplugging the USB device and restarting the computer with a LiveCD.  That *should definitely* connect to the router.  At least it would confirm all the hardware is working.

I tried this but couldn't get it to boot from a live cd. It only used it to start. I almost forgot I need to post in Ubuntu install that I couldn't install from the live cd without going to the install with driver update option. I don't have a driver update cd but I found it was the only way to install ubuntu. I didn't insert a driver or other cd when asked I just pressed enter and it carried onto the install page. Everything installed ok... I presume :confused:

I downloaded the live CD from a link on this site. I did this because I updated with the update manager but got a blue screen on my lcd. I presumed it had messed up but later found out it is a boot fault with the splash screen. I lost a hard drive in the process, re installing back to 6.10.  not very happy as its a major balls up in my book. 

anyway back to this.....


> 
If it does - then manual control of the interface should set it up... (where *interface* is **eth0** or **eth1** (representing the Realtek card).  You may also have to *ifconfig down* the USB interface.
```
sudo ifconfig *interface* down
sudo dhclient -r *interface*
sudo ifconfig *interface* up
```

with this should I try it anyway?  

and

if I do and it looses my internet USB how would I get it back please?  you know before I drop of the face of the internet LOL :)

cheers for your help. Sorry i wasdnt around to reply earlier, Am a bit busy at minute, gotta shoot again now.

 Learning lots though thankyou
john

---

### Post by ugm6hr on 2008-01-12
I'm a bit confused.  You initially said you had 7.10, but now 6.10... which is it?

Does the 7.10 LiveCD not work?

As for trying to get connected... This should be safe:

Install *dhcpcd* from Synaptic:
```
sudo apt-get install dhcpcd
```

Boot up with USB modem and wifi dongle unplugged, and ethernet plugged into router.
```
sudo ifconfig eth1 up
sudo dhcpcd eth1
ifconfig
```

If that doesn't work, a reboot with USB plugged in should get you back online.

---

### Post by silent the spy on 2008-01-12
> **ugm6hr said:**
> I'm a bit confused.  You initially said you had 7.10, but now 6.10... which is it?


sorry for the confusion. Im on 7.10  I was on 6.10, I used the update feature, when it booted it got to the ubuntu screen with the knightrider kit type thingy (oh showing my age LOL)  then my screen went blue, no signal, I thought the upgrade had screwed up..,., so I re install 6.10, download 7.10, burn it to cd, my hard drive crashes big time, unrecovable, so I intstall 7.10 on another hard drive. I found out the upgrade had been ok, its a problem with the log in screen apperntly, all I had to do was type in my log in and then password and it would have booted. Its what I do now as I havent got round to sorting it.

> 


Does the 7.10 LiveCD not work?


no not in the sense of trying it. It only comes up with install or run  and then it just boots the pc, no live cd feature. Dont ask I have no idea whats going on, im still learning :confused:


> 
As for trying to get connected... This should be safe:

Install *dhcpcd* from Synaptic:
```
sudo apt-get install dhcpcd
```

Boot up with USB modem and wifi dongle unplugged, and ethernet plugged into router.
```
sudo ifconfig eth1 up
sudo dhcpcd eth1
ifconfig
```

If that doesn't work, a reboot with USB plugged in should get you back online.

got to sudo ifconfig eth1 up

```
sudo dhcpcd eth1
Error, eth1: timed out

```

the monitor is spinning with a little graphic. I just plugged my usb back in and hey presto internet and Realtek network has re appeared , I click it, graphic spins, then pc goes back to the USB network and the Realtek is greyed out again.

Wont be on til tomorrow now. Is it time to use a hammer? :lolflag:

---

### Post by ugm6hr on 2008-01-12
Judging from that, it looks like the router is not assigning an IP address  to the ethernet card with DHCP.

The only thing I can think that would do this would be a problem with the router.  Or if the router does not have DHCP on.  But, I recall the router manual specifically mentions that DHCP is on.

I wonder whether the problem is with the router or the router default settings.  Have you software reset the router (with the button on the back) and tried it?

If that doesn't work, then I suspect the problem is with the router.  Do you know anyone with an ethernet card who could try it out for you?


As a side note...

> It only comes up with install or run and then it just boots the pc, no live cd feature

Your explanation of what happens with the LiveCD doesn't make sense.  You have a 7.10 LiveCD, right (downloaded from [www.ubuntu.com)?](www.ubuntu.com)?)  And when you put it in the drive, and boot from it (with BIOS set to boot from CD), you get an option to run or install?  And when you choose this, what happens?  It is supposed to boot into Ubuntu, with an icon for ubiquity labelled Install on the desktop.  It will not install unless you select the install icon.  That is the LiveCD trial.  The installation will run through a series of questions about your location, keyboard type, hard drive partitions etc.  But you can *use* the LiveCD without installing.

So I'm still confused as to how you installed with a LiveCD 7.10 if it doesn't work.  You cannot install from a LiveCD unless it works, as far as I know.  Unless you also downloaded an Alternate (text-installer) CD.

One other thing - you cannot upgrade from 6.10 to 7.10 without upgrading through 7.04.  So I think you should clarify the whole situation with regard to what setup your computer is running at the mo.

However, your ethernet should work with any version of Ubuntu - so don't stress too much about this.

---

### Post by silent the spy on 2008-01-13
> **ugm6hr said:**
> Judging from that, it looks like the router is not assigning an IP address  to the ethernet card with DHCP.

The only thing I can think that would do this would be a problem with the router.  Or if the router does not have DHCP on.  But, I recall the router manual specifically mentions that DHCP is on.

I wonder whether the problem is with the router or the router default settings.  Have you software reset the router (with the button on the back) and tried it?

If that doesn't work, then I suspect the problem is with the router.  Do you know anyone with an ethernet card who could try it out for you?

I tried resetting it, still no connection, weird I had a connection light with the other LAN card. 

I see someone Tuesday and try it, if that fails I'll need to take it back I guess.


> 

As a side note...



Your explanation of what happens with the LiveCD doesn't make sense.  You have a 7.10 LiveCD, right (downloaded from [www.ubuntu.com)?](www.ubuntu.com)?)

yep


>   And when you put it in the drive, and boot from it (with BIOS set to boot from CD), you get an option to run or install? 

yep


>   And when you choose this, what happens?  It is supposed to boot into Ubuntu, with an icon for ubiquity labelled Install on the desktop. 

it doesn't do this. It did when I first installed but like I said it wont boot or install from the top choice on the menu. other choices are check hard drive for defects, boot from hardrive, check cd for defects etc

I have to use the 3rd down I think, install with driver update cd. But seeing as I don't have an update cd I choose it anyway, it asks me to insert driver cd and press enter, I just press enter, it then caries on.

 If I choose the first option on the above mentioned menu it goes to a DOS input, some infams command or something like that, it suggestions type help for suggestions. I do, I don't understand what to do from there so I type reboot, it does, I try again, I get the same...


... so I choose another choice install with updated driver cd

> 
 It will not install unless you select the install icon.  That is the LiveCD trial. 

This is after the menu choice I mention above. But it does not do this anymore.


>  The installation will run through a series of questions about your location, keyboard type, hard drive partitions etc.  But you can *use* the LiveCD without installing.

yea Ive done that in the past, it wont do it anymore

> 

So I'm still confused as to how you installed with a LiveCD 7.10 if it doesn't work.  You cannot install from a LiveCD unless it works, as far as I know.  Unless you also downloaded an Alternate (text-installer) CD.

it did work when I first did it, now it wont. Sometimes I have a list of boot options, boot from ubuntu 7.10, ubuntu recovery, and a few bellow that, command line I think etc. This is probably why it wont run from the cd. But im still learning abait slowly so I dont understand what it wants or means, I just let it count down or choose the top one, it all boots fine

> 
One other thing - you cannot upgrade from 6.10 to 7.10 without upgrading through 7.04.  So I think you should clarify the whole situation with regard to what setup your computer is running at the mo.

I cant remember what last one was. This install is 7.10 clean  not an upgrade. The upgrade I mention was offered in the update manager menu so I guess it was the right one? I ended up with a wrecked harddrive as described above so this is as I say a clean install of 7.10

> 

However, your ethernet should work with any version of Ubuntu - so don't stress too much about this.

I think its hammer time ](*,):roll:

---

### Post by ugm6hr on 2008-01-13
> **silent the spy said:**
> it did work when I first did it, now it wont. Sometimes I have a list of boot options, boot from ubuntu 7.10, ubuntu recovery, and a few bellow that, command line I think etc. This is probably why it wont run from the cd. But im still learning abait slowly so I dont understand what it wants or means, I just let it count down or choose the top one, it all boots fine


This is very bizarre.  If you *sometimes* have a list of boot options - you are *sometimes* booting from HD.

There is no good reason that the LiveCD now doesn't work, if it worked before - except that there is a fault with the LiveCD.  Did you check the md5sum on it?

Anyway - there is almost certainly no problem with the ethernet card.  Not so sure about the router.

I'm afraid I'm now out of ideas, if it turns out there is no problem with the router (except re-installing Ubuntu fresh).

---

### Post by silent the spy on 2008-01-13
> **ugm6hr said:**
> This is very bizarre.  If you *sometimes* have a list of boot options - you are *sometimes* booting from HD.

There is no good reason that the LiveCD now doesn't work, if it worked before - except that there is a fault with the LiveCD.  Did you check the md5sum on it?

no how do I do that please?  I think I read about that some time ago but i didnt do it this time.

> 

Anyway - there is almost certainly no problem with the ethernet card.  Not so sure about the router.

My modem has a USB output and a LAN. Im using the usb. Now I have a LAN card I tried using the LAN output straight into the pc. No network. No internet. Which backs up the router not showing a connection.  

I dont know what to do?

---

### Post by ugm6hr on 2008-01-13
I really am a bit stumped now.  

I'm afraid I am not sure how you check an md5sum *after* burning the CD (only before with .iso file).

But the fact that the LiveCD doesn't work properly now does suggest there is a problem with it.

The only other thing I can think of is that all that messing with ndiswrapper has interfered with your LAN settings.  But, on the other hand, lshw returns the correct driver....

To see what happens if you stop ndiswrapper loading:
```
gksudo gedit /etc/modules
```
And remove the ndiswrapper line

Then try rebooting and see what happens.

Not sure how to remove the ndiswrapper alias from /etc/modprobe.d - but that might be necessary too (probably).

Apart from a re-installation to ensure that everything is as default, I'm not sure what else to try.  I's also suggest getting a new LiveCD (or perhaps the alternate CD) if you are going to go down this route.

Sorry this has all gone horribly wrong.... :(

---

### Post by silent the spy on 2008-01-13
> **ugm6hr said:**
> I really am a bit stumped now.  

I'm afraid I am not sure how you check an md5sum *after* burning the CD (only before with .iso file).

But the fact that the LiveCD doesn't work properly now does suggest there is a problem with it.

I think theres a problem with my hardrive and its looking at the cd to correct it. It wants to boot from it sometimes. 

When I just rebooted I got an options page, ubuntu 7.10, ubuntu 7.10 recovery, something else, other systems, a whole host of options. I use the top one ubuntu 7.10. 


> 
The only other thing I can think of is that all that messing with ndiswrapper has interfered with your LAN settings.  But, on the other hand, lshw returns the correct driver....

To see what happens if you stop ndiswrapper loading:
```
gksudo gedit /etc/modules
```
And remove the ndiswrapper line

Then try rebooting and see what happens.


nope didn't sort it.  The monitor just spins and spins, monitor occasionally comes up with a asterix, then it spins again and again and then I get dizzy LOL no number lights on my router 

> Not sure how to remove the ndiswrapper alias from /etc/modprobe.d - but that might be necessary too (probably).


I don't know either :)


> Apart from a re-installation to ensure that everything is as default, I'm not sure what else to try.  I's also suggest getting a new LiveCD (or perhaps the alternate CD) if you are going to go down this route.

I dont want to loose this harddrive. Its the only one I got. I guess I may just take the router back and say it was suggested by your staff for use on Linux, I speciaifcally asked what one...but I cant get it to work

> Sorry this has all gone horribly wrong.... :(

hey man , **** happens  :D

---

### Post by ugm6hr on 2008-01-14
Let me just refresh my memory about the various issues at present:

1. Your new Realtak LAN card loads the correct driver, but does not attain an ip via DHCP.  Network Manager (NM) spins to indicate it is trying to connect.  No light comes on to indicate a connection with the router.

2. Your 7.10 LiveCD does not boot from Option 1 or 2, but will boot from the "Install using Driver CD" option (3).

3. Your HD sometimes gives you a normal GRUB boot menu, but sometimes not.

My thoughts:

1. Possible problems:
a. Problem with ethernet (CAT5/6) cable - presumably you are using the new cable with the router?  Are the contacts seated OK in the sockets?  Although if this was the problem, NM would not spin at all, it would just sit there with a red triangle over a computer screen icon.
b. Problem with router - unlikely, given the issue remains with your ethernet modem.  Does the light turn on on the modem to indicate a connection?
c. Problem with LAN card - only possible issue would be with the connection to the ethernet cable (i.e. loose connection) - as (a).
d. Problem with NM - but it wouldn't connect manually either...

2. Don't know why this would happen.  I have just booted my LiveCD (7.10), and seen that there is a check CD for defects option - maybe try that.  Also - option 3 (the Driver CD option) boots to a LiveCD environment anyway.  So try booting to that (option 3) with the USB device unlugged and the ethernet plugged into your modem or router (or both) to see if it will connect from the LiveCD.  If so - at least we know it is a software issue.

3. This is a bit more worrying. I'm not sure I fully grasp what happens - so I think I'll leave this.  But if you are saying that sometimes when you boot your computer (without LiveCD etc), you *don't* get the list of boot options, then there is clearly a problem with GRUB or your MBR.  I don't think this has anything to do with the networking problem though.  How many options do you get? Are you dual booting?  You should only have 2 Ubuntu options (Normal and Recovery), a memtest option, and then a list of any other OS you are dual-booting with.  But I thought you weren't dual-booting.

So - still back to trying the LiveCD again.  But just use Option 3 (since that works for your computer).

---

### Post by silent the spy on 2008-01-14
> **ugm6hr said:**
> Let me just refresh my memory about the various issues at present:

1. Your new Realtak LAN card loads the correct driver, but does not attain an ip via DHCP.  Network Manager (NM) spins to indicate it is trying to connect.  No light comes on to indicate a connection with the router.

correct

> 

2. Your 7.10 LiveCD does not boot from Option 1 or 2, but will boot from the "Install using Driver CD" option (3).


correct

> 

3. Your HD sometimes gives you a normal GRUB boot menu, but sometimes not.


correct. Though I think at this time its giving me GRUB boot menu every time

> 
My thoughts:

1. Possible problems:

a. Problem with ethernet (CAT5/6) cable - presumably you are using the new cable with the router?  Are the contacts seated OK in the sockets?  Although if this was the problem, NM would not spin at all, it would just sit there with a red triangle over a computer screen icon.


Yep using new cable. Have tried another and same no connection. Sits in the socket as far as I can tell. Wont go in any other way.

> 
b. Problem with router - unlikely, given the issue remains with your ethernet modem.  Does the light turn on on the modem to indicate a connection?

not sure what you mean. 

modem when plugged straight into LAN on pc , lights on modem indicating pc activity flashes alot. But I get no internet so not sure if its working

If you mean light on LAN card to indicate connection. It doesn't look like it. Though my pc is hard to see round the back where it is. But I checked and cant see any. I may pull it out later  but I don't think its on.


> 
c. Problem with LAN card - only possible issue would be with the connection to the ethernet cable (i.e. loose connection) - as (a).

am I that unlucky LOL ????

> 
d. Problem with NM - but it wouldn't connect manually either...


gremlins? :-)

> 
2. Don't know why this would happen.  I have just booted my LiveCD (7.10), and seen that there is a check CD for defects option - maybe try that.  Also - option 3 (the Driver CD option) boots to a LiveCD environment anyway.  So try booting to that (option 3) with the USB device unlugged and the ethernet plugged into your modem or router (or both) to see if it will connect from the LiveCD.  If so - at least we know it is a software issue.


using option 3 , it just boots to my pc, no live cd. If I remeber correct the other day when doing all this my pc decided to crash. on boot up it said harddrive failure or soemthing and insert cd to boot. I inserted ubuntu 7.10 and after a mess around it booted... using option 3 I think. Now im left with the GRUB everytime I boot.


> 3. This is a bit more worrying. I'm not sure I fully grasp what happens - so I think I'll leave this.  But if you are saying that sometimes when you boot your computer (without LiveCD etc), you *don't* get the list of boot options, then there is clearly a problem with GRUB or your MBR.  I don't think this has anything to do with the networking problem though.  How many options do you get? Are you dual booting?  You should only have 2 Ubuntu options (Normal and Recovery), a memtest option, and then a list of any other OS you are dual-booting with.  But I thought you weren't dual-booting.



Im not duel booting as far as I know. There is a list under memtest, though I cant off hand remember what it says. I'll look next time.

 This hard drive was a slave and split, 200 gig. When the other main one crashed beyond repair I took it out, put the pin in for this to be treated main drive, cant remember what the name is, resized it and fresh install. It had never had any operating system installed on it before.


> So - still back to trying the LiveCD again.  But just use Option 3 (since that works for your computer).

If I could do a fresh install I would as my hard drive is split. I wouldn't loose much, only a headache redoing and installing my email thunderbird

---

### Post by ugm6hr on 2008-01-14
I think you need to set your computer to boot from CD first in order to boot the LiveCD.

If you always get GRUB - it is looking at your HD first, so will always boot from that.  To get to your BIOS, it is usually F2 or F12 (or F-something, or otherwise Del) when you initially turn the computer on (before GRUB menu loads).

Look for something that says Boot priority (or something like that), and list CD first.  Then try the LiveCD again.

As for reinstalling - it is pretty quick.  You could just backup everything on home directory to the other partition, and then copy back again when reinstalled.  There is a backup utility that will do it easily for you linked below (see Beginner stuff).

---

### Post by silent the spy on 2008-01-14
> **ugm6hr said:**
> I think you need to set your computer to boot from CD first in order to boot the LiveCD.

If you always get GRUB - it is looking at your HD first, so will always boot from that.  To get to your BIOS, it is usually F2 or F12 (or F-something, or otherwise Del) when you initially turn the computer on (before GRUB menu loads).

Look for something that says Boot priority (or something like that), and list CD first.  Then try the LiveCD again.

sorry my mistke. I know how to go into BIOS and set it to boot from cd. I still dont get liveCD. As above, my pc boots after selecting install/run. No sorry as above it goes into a DOS command line input, infracsms?  or something.

> 

As for reinstalling - it is pretty quick.  You could just backup everything on home directory to the other partition, and then copy back again when reinstalled.  There is a backup utility that will do it easily for you linked below (see Beginner stuff).

cheers :-)

---

### Post by ugm6hr on 2008-01-14
> **silent the spy said:**
> sorry my mistke. I know how to go into BIOS and set it to boot from cd. I still dont get liveCD. As above, my pc boots after selecting install/run. No sorry as above it goes into a DOS command line input, infracsms?  or something.

Does the Install with Driver CD option work still?  Have you tried the Check CD for errors option?

---

### Post by silent the spy on 2008-01-14
just having lunch, will check after

---

### Post by silent the spy on 2008-01-14
> **ugm6hr said:**
> Does the Install with Driver CD option work still?  Have you tried the Check CD for errors option?

checked cd for errors. It went to a DOS prompt type screen. I should have written it down I know, I thought I'd remember it , oh my what a fool, sorry.  I then tried install/run , the top choice, it also went to the same screen. I typed help, it came up with the same list of commands I spoke of earlier, I think its stuff on the disc. I didn't understand any of them so typed reboot. I then ....

.... Install with driver cd, I hit enter, then enter again, I am now in LiveCD mode. I had to put another monitor on as I had no signal. I have saved my desktop with the monitor showing. It is greyed out, it was selectable, I selected it, it span, then connected back to the USB network.

 I then removed the USB cable, both networks disappeared ...  the monitor span.. when I put my mouse over it it said '*requesting a network address from the wired network ' * It just kept spinning, no connection lights on router 1,2,3 or 4

---

### Post by silent the spy on 2008-01-14
I took note of the other operating system choices on reboot. They are

Ubuntu, kernel 2.6.20 - 16 generic (on/dev/hda3)
Ubuntu, kernel 2.6.20 - 16 (recovery mode) (on/dev/hda3)
Ubuntu, kernel 2.6.20 - 15 generic (on/dev/hda3)
Ubuntu, kernel 2.6.20 - 15 (recovery mode) (on/dev/hda3)
ubuntu memory test 86+

I dont choose any of those, I choose ubuntu 7.10 

nightmare huh :-)

---

### Post by ugm6hr on 2008-01-14
Looks like you have a second installation of Ubuntu on hda3.  Maybe that's where your "messed up" installation is...

Bit concerning that the Check CD doesn't work.  Can't remember what it is supposed to do.

The screenshot looks like you would expect it to if the ethernet cable is unplugged.  When you say "both networks disappear" when you unplug the USB - is there still an entry that says "Wired Network"?  If so - is it greyed out?

The fact that it spins suggests that it connects, but is struggling with getting an IP adress.... back to the DHCP issue again.  Not sure why though.

Hmmm.... I think at this stage I'm definitely struggling.  

It appears there is an issue with the LiveCD that you installed with - so I do wonder if the DHCP installation in Network Manager is broken.  Unfortunately, I have no idea how you would check that (without downloading and writing a fresh LiveCD).  Seems a bit unlikely, but then everything you have encountered so far seems unlikely!

The other thing worth trying is turning roaming off from the LiveCD.  That would deactivate Network Manager, and allow manual connection (with DHCP on).  Maybe try it in your modem on maual too.  Although, to be honest, I'm just guessing now....

---

### Post by silent the spy on 2008-01-15
> **ugm6hr said:**
> Looks like you have a second installation of Ubuntu on hda3.  Maybe that's where your "messed up" installation is...

can I just delete it?  if its of no use that is

> 

Bit concerning that the Check CD doesn't work.  Can't remember what it is supposed to do.

The screenshot looks like you would expect it to if the ethernet cable is unplugged.  When you say "both networks disappear" when you unplug the USB - is there still an entry that says "Wired Network"?  If so - is it greyed out?


yes still says "wired network" not greyed out,

> 
The fact that it spins suggests that it connects, but is struggling with getting an IP adress.... back to the DHCP issue again.  Not sure why though.

Hmmm.... I think at this stage I'm definitely struggling.  

It appears there is an issue with the LiveCD that you installed with - so I do wonder if the DHCP installation in Network Manager is broken.  Unfortunately, I have no idea how you would check that (without downloading and writing a fresh LiveCD). **_ Seems a bit unlikely, but then everything you have encountered so far seems unlikely!_**


you should see the rest of my life :lolflag: :)

> 

The other thing worth trying is turning roaming off from the LiveCD.  That would deactivate Network Manager, and allow manual connection (with DHCP on).  Maybe try it in your modem on maual too.  Although, to be honest, I'm just guessing now....

Ok i'll try later thanks. And I forgot to take my modem to my friends when I went earlier.. duh!

---

### Post by ugm6hr on 2008-01-15
> **silent the spy said:**
> ...  the monitor span.. when I put my mouse over it it said '*requesting a network address from the wired network ' * It just kept spinning, no connection lights on router 1,2,3 or 4
> 
yes still says "wired network" not greyed out,

So - not greyed out.  But "spins" forever.

Again - suggests the LAN card works OK, and detects a connection (not greyed), but is not being given an IP by the DHCP server (spins forever) on the router.

I'm no networking expert, but I think that must either be a problem with the router, or the Network Manager configuration.

---

### Post by silent the spy on 2008-01-15
I just put the LAN cable from my pc into my xbox 360. I could then select the realtek network, it didn't revert back to the USB one, I tried to connect to xbox live but it wouldn't, I didn't think it would as its going through my pc but I thought maybe when I run the network test on the 360 it may talk back to the pc and show me the card/cable was working but it didn't. why did I think this may do something? buggered if I know , but with everything else failing I thought what the heck. When I took the cable out of the 360 the monitor span and reverted back to the USB network. What does this tell me? I have no idea :D

---

### Post by ugm6hr on 2008-01-15
> **silent the spy said:**
> I just put the LAN cable from my pc into my xbox 360. I could then select the realtek network, it didn't revert back to the USB one, I tried to connect to xbox live but it wouldn't, I didn't think it would as its going through my pc but I thought maybe when I run the network test on the 360 it may talk back to the pc and show me the card/cable was working but it didn't. why did I think this may do something? buggered if I know , but with everything else failing I thought what the heck. When I took the cable out of the 360 the monitor span and reverted back to the USB network. What does this tell me? I have no idea :D

I have no idea either!  But it does seem like the Realtek card *can* work, doesn't it?

I don't have an Xbox 360 - does it have a web-browser built in like the Nintedo Wii?  If so, you might be able to configure the router from the Xbox.  And if you plug the Xbox into the router - does the light come on on the router to indicate a connection?

PS: You probably can just delete the hda3 partition if you don't think there is anything on there.  Obviously, I have no idea if there is anything important on there without looking!

---

### Post by silent the spy on 2008-01-15
I cant configure the router from the xbox, I tried last week. I can only run a test page. Unless there's something im missing.  I get a light on the router with it plugged into the xbox. woo hoo :-) sorry got excited LOL

I have a wii, *cough* its my sons honest . Though there's no LAN connection only USB. I don't have the LAN adapter. Thats why I bought the wi fi router. So I .... I mean he can go online.

---

### Post by silent the spy on 2008-01-15
my xbox gets an IP from the router but it fails an MTU test what ever that is?

My xbox wont connect to my pc through the router. Theres a test to do it, but I aint running windows anyway so I thought it would fail but there wasnt any light on the router no matter where I plugged the cable in.

just trying anything here to get a response out of it.

edit : what this all tells me is there is no signal coming out of the LAN card

---

### Post by silent the spy on 2008-01-24
update time :-)

took my router to a friends, couldn't do it, well he couldn't and wouldn't let me on his pc LOL but he got me a copy of xp legit. I had tried to set up duel boot but couldn't so used another separate hard drive to install xp

xp installed, found my card, set up my router using the supplied router cd. Everything worked easily. This morning I turned on my XP pc, my LAN connection couldn't connect, said cable was out, it wasn't. I plugged in my usb dongle and got a wi fi connection. At this moment im on xp using wi fi. So its all set up, it all works. Just need to find out if the LAN card is broken or if its windows having a turn LOL

I will update this thread when I get inside my pc and go back to ubuntu/ swap the hard drive or set up duel boot. wont be today, maybe not even tomorrow but when I do I hope the usb dongle works.

I have emailed and talked with the LAN card manufacturer enquiring if the card could be faulty or if it simply does not work with Linux. They replied they would send me readings of it working on linux, I asked for them to download and try the ubuntu 7.10 from here as its a new distro. 

not sure if I left anythign out. Anyway I'll update this as I go along, hopefully it can be marked as solved sooner rather than never 

john

---

### Post by ugm6hr on 2008-01-24
If XP is misbehaving with LAN too, then there are 3 possibilities:
1. The ethernet card is broken
2. The router is broken.
3. The cable is broken.

It would be very unusual for both Ubuntu and XP to be unable to maintain a connection with ethernet.  Bizarre that XP would work initially, but not afterwards.

I have had similar problem with a previous router that was faulty (i.e. only worked on wifi after a year or two).

I would say to just return the LAN card as faulty - but it would be important to make sure that it isn't the router.  Have you tried the Xbox on the router with the internet connection turned on (I understand the MTU test will fail if you can't get online).

---

### Post by silent the spy on 2008-01-24
was on my to do list, now on my done list. Xbox live online using the same cable I used from pc to Router. so the cable works, the Router works. My guess the card is faulty?

---

### Post by ugm6hr on 2008-01-24
> **silent the spy said:**
> was on my to do list, now on my done list. Xbox live online using the same cable I used from pc to Router. so the cable works, the Router works. My guess the card is faulty?

How unlucky are you?  A "fake" ethernet card, and a broken one.

And it's only taken 3 weeks to get this far!

I bet with all that messing around, the USB wifi will need to be reconfigured in Ubuntu again too!  At least you'll be a networking expert by the time you're online and wireless in Ubuntu ;)

Probably worth getting the ethernet card replaced under warranty (unless it is not worth the postage).

---

### Post by silent the spy on 2008-01-24
> **ugm6hr said:**
> How unlucky are you?  

you can see why i dont bet !


> 

I bet with all that messing around, the USB wifi will need to be reconfigured in Ubuntu again too!  At least you'll be a networking expert by the time you're online and wireless in Ubuntu ;)

aint that always the way. I think the saying goes "if you keep getting ill you should be a doctor" LOL


> 
Probably worth getting the ethernet card replaced under warranty (unless it is not worth the postage).

I would hope there is no postage. Im sure the sale of good act in the uk covers me for faulty products, but im not 100% sure

wow what a trip huh :-D nightmare 3 weeks! and im still on usb not ethernet, and yes I did notice a speed increase last night, im sure I did, unless it was just relief :mad::lolflag:

EDIT: and my sons nintendo wii is online wi fi. atleast I can say this router works! famous last words LOL

---

### Post by hahahan on 2008-01-24
Hi,

If your wifidongle is a Netgear wg111 v2 it's based on a rtl8187 chipset and you don't need ndiswrapper. The driver shipped with ubuntu is a little crappy Here : [http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187) a good driver and guide is available

---

### Post by silent the spy on 2008-01-25
> **hahahan said:**
> Hi,

If your wifidongle is a Netgear wg111 v2 it's based on a rtl8187 chipset and you don't need ndiswrapper. The driver shipped with ubuntu is a little crappy Here : [http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187) a good driver and guide is available


```

wlan0: ERROR while getting interface flags: No such device
john@charlie:~$ rmmod rtl8187
ERROR: Module rtl8187 does not exist in /proc/modules


```

its a game I tell ya!  


so im back to the beginning, nothing works, nothings chnaged. I booted with my LAN cable in, and my USB dongle in. Nothing, not a thing! no network. I took out my LAN cable, hoping the USB dongle would just work, zero nothing.  So I put my usb modem back in as before and low and behold up pops my greyed out realtek network, un selectable!!! and im online as before using my direct connection to my modem via usb

windows it all just worked. This, well :-(  very, very disappointed

what now? is it time to use a hammer yet?

edit : I think the rtl8187 was removed. I'll put it back in and hopefully everything works and I can take it all back what I just said

---

### Post by silent the spy on 2008-01-25
HA!!!! something working. We have internet. I believe through a wired connection. No usb dongle yet. 

Watch this space I guess as I figure out what's what and then can mark this solved.... hopefully :-)


but for the mean time I just did whats on that page anyway [http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187)

```
wget http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget http://patches.aircrack-ng.org/rtl8187_2.6.22.patch
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.22.patch
make
make install
```

I thought stuff it, what with the way things have gone who cares! :lolflag: rebooted, no usb dongle so plugged in the LAN cable and here I am.

---

### Post by silent the spy on 2008-01-25
spoke to soon!

put my pc back together and put it back in place, reason was to unplug the other hard drive I installed windows on as I couldnt get it to boot with it. I think I have the jumper on the wrong pins. Set it as slave but its not is it, so Im gonna have to work that one out.

anyway the frigin LAN card does not work again! back to the beggining. So the million dollar question why didnt I just leave my pc strewn across the floor and live around it! after all it was working :popcorn::lolflag:

if we were allowed to swear on this forum the air would be blue :-(

---

### Post by silent the spy on 2008-01-25
online wait for it.............................


................... wirelessly!!!!!!

I put ndiswrapper back in to load at boot, page 9 I think was where I removed it. Blinky blink on the blue led on the dongle, first attempt I couldn't get it to link when manually configuring it and inputting my passkey. I dont know why, maybe I was doing something wrong.

So I rebooted, went to the same manual set up and suddenly here I am. 

LAN card is still not working. I wonder if it is broke, a duffer. I think I will wait for the lady at Realtek to get back to me with proof it does work with 7.10 as she said she would. Maybe then I can return this one as it was intermittent on xp and then on 7.10

---

### Post by ugm6hr on 2008-01-25
> **silent the spy said:**
> LAN card is still not working. I wonder if it is broke, a duffer. I think I will wait for the lady at Realtek to get back to me with proof it does work with 7.10 as she said she would. Maybe then I can return this one as it was intermittent on xp and then on 7.10

Your realtek chipset is the same one that about 70% of ethernet cards use (including mine).  It does work with any Linux (for the last few years anyway), including Ubuntu 7.10.

Only other possibility is that it is not securely seated in the PCI slot - hence the intermittent problem.  Or that there is a problem with your PCI slot - maybe the gold-plating on the contacts is not up to par?  But I think a duff card is still more likely.

If you are going to dismantle your PC (again) - try putting it in a different PCI slot.

---

### Post by silent the spy on 2008-02-22
I tried a different pci slot, same thing happens with the LAN card. The women from Realtek who said she would test it and get back to me didnt. I asked her to try this build of Ubuntu. Make of it what you will. Anyway wi fi works, LAN doesnt. I think everyone provided enough info in this thread for it to work, just for some reason the LAN doesnt.

Thanks to everyone, I think I will mark this as solved.

---

