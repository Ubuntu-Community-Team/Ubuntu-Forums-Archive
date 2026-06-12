---
title: "Problem connecting to inetrnet using a d-link glb 802c modem"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by fahadrather on 2009-01-06
I have a problem connecting to internet using my modem because when i enter the command sudo pppoeconf, it shows like this:
I found 1 ethernet device:                               
           eth0                                                     
 Are all your ethernet interfaces listed above?   (If No, modconf will be started so you can load the card drivers manually).                                   

when i enter yes then it starts detecting and then:

Sorry, I scanned 1 interface, but the Access             
Concentrator of your provider did not respond. Please    
check your network and modem cables. Another reason       
 for the scan failure may also be another running pppoe   process which controls the modem.

i have a d-link glb 802c modem and the problem is that i cant connect in windows..i use ubuntu 8.04

---

### Post by fahadrather on 2009-01-06
i even tried the 7.10 live cd but it showed exactly the same error....i switched off the modem and entered the command sudo pppoeconf it showed the same error...i think ubuntu does not detect my modem.....i used my laptop(8.04) but it again showed the same error...

---

### Post by kestrel1 on 2009-01-06
From what I can make out the glb 802c is an ADSL modem/router.
You wouldn't see the modem/router itself as you should be connected via Ethernet cable.
Go to a terminal window & type:
```
ifconfig
```
& post the result here.

---

### Post by fahadrather on 2009-01-07
i am sorry for the late reply...it was almost 3 am when i  this wrote this  and i had to go to sleep...

fahad@fahad-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:ec:41:07:95  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9600 (9.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.144.8.6  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:319066 (311.5 KB)  TX bytes:24113 (23.5 KB)

---

### Post by fahadrather on 2009-01-07
:( no replies yet...

---

### Post by kestrel1 on 2009-01-07
How are you connecting your machine to the router?
Are you using ethernet cable?

---

### Post by fahadrather on 2009-01-07
Yeah...

---

### Post by kestrel1 on 2009-01-07
Can you post the result of the following command:
```
sudo dhclient
```

---

### Post by fahadrather on 2009-01-07
fahad@fahad-desktop:~$ sudo dhclient
[sudo] password for fahad: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

socket: Address family not supported by protocol - make sure
CONFIG_PACKET (Packet socket) and CONFIG_FILTER
(Socket Filtering) are enabled in your kernel
configuration!

---

### Post by kestrel1 on 2009-01-07
That aint looking good.
Go to System - Preferences - Network Configuration
The select your eth0 connection & edit
Under IPv4 is it set to Automatic (DHCP)
If not set it to Automatic (DHCP)
Then reboot your machine & post the output from:
```
sudo dhclient
``` &
```
ifconfig eth0
```

---

### Post by fahadrather on 2009-01-07
i cant edit this....for some reason..

---

### Post by fahadrather on 2009-01-07
:(:(:(:confused::confused::confused:

---

### Post by kestrel1 on 2009-01-07
You went to the wrong place.
That is System - Administration - Network tools
I said:
Go to System - Preferences - Network Configuration
:D:D:D:D

BTW what version of Ubuntu are you using 8.04 or 8.10

---

### Post by fahadrather on 2009-01-07
I use 8.04

---

### Post by kestrel1 on 2009-01-07
OK. I am on 8.10 at present, but when I get home I will boot up my 8.04 system & look again. I know the configuration of the menu's differs a bit, so I could be pointing you in the wrong direction.
I should get home & on my 8.04 system in about 3.5 hours.

---

### Post by fahadrather on 2009-01-07
There is no network tools in system>preferences     there is only network proxy.....thats why i tried other things :confused:

---

### Post by kestrel1 on 2009-01-07
Sorry for the misinformation. I will let you know where it is later.

---

### Post by fahadrather on 2009-01-07
There is no network tools in system>preferences     there is only network proxy.....thats why i tried other things

---

### Post by kestrel1 on 2009-01-07
Got here a bit sooner than I thought.
Anyway, in 8.04 go to System - Administration - Network
Click on the unlock button & select the wired connection. Then click Properties.
Is it set to Enable Roaming Mode? If not set it to roaming mode & then reboot the machine & give us the outputs from the commands as above.
If it is set to Enable roaming mode untick the box & use the drop down menu next to Configuration to set it to Automatic Configuration (DHCP)
Reboot & post output as above.

---

### Post by fahadrather on 2009-01-07
Sorry dude there are some huge problems here...i use a choking gprs connection which is so slow that i am desperate to get that modem working but there are some electricity issues as well...there is no electricity at the moment.never mind...its a long story i tell it some other time...i am using my mobile phone browser to post this...i will get go touch as soon as it comes back..sorry for the inconveience...

---

### Post by kestrel1 on 2009-01-07
Not inconvenient to me dude. :lol:
Pain about you electric though

---

### Post by fahadrather on 2009-01-07
fahad@fahad-desktop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

socket: Address family not supported by protocol - make sure
CONFIG_PACKET (Packet socket) and CONFIG_FILTER
(Socket Filtering) are enabled in your kernel
configuration!





fahad@fahad-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:ec:41:07:95  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9600 (9.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe400 


it is when i have dhpc selected

also take a look at the image...it shows something strange........or is it that my router is faulty and i am getting head aches by banging my head against the wall??

---

### Post by fahadrather on 2009-01-07
the modem doesn't work in windows as well....and in ubuntu when i type 192.168.1.1 ,it says enter user name and password....i enter it but it still keeps on asking even though the user name and password are correct i.e admin, admin...but it does show modem settings in windows....

---

### Post by kestrel1 on 2009-01-07
I am just popping over to the D-link website to have a look at the routers manual. Back soon, when I have inwardly digested the manual.

---

### Post by kestrel1 on 2009-01-07
Can't find the manual that I wanted yet, but could you do a few things please.
Post the result of:
```
lsusb
```
&
```
lspci
```
last thing, if you look at your panel at the top of the screen you have an icon that looks like a couple of monitors. If you right click on these you should get a menu, in there you will see Connection Information.
Can you post that as well.
I will have another look for the manual now.
& if you look on your top panel you should have

---

### Post by fahadrather on 2009-01-07
keep posting....i will keep refreshing the page...and oh yeah i got no manual or cd with this piece of garbage....i got only head ache and tension and depression for rs1850 thats almost 40$...

---

### Post by fahadrather on 2009-01-07
fahad@fahad-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0915:0005 GlobeSpan, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0421:00bf Nokia Mobile Phones 
Bus 001 Device 001: ID 0000:0000  
fahad@fahad-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:03.0 Communication controller: Agere Systems Unknown device 0620
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by kestrel1 on 2009-01-07
There is no manual on the D-Link website & the only reference to it is on the India site as it looks like it is only available in India.
Don't get depressed, we will crack this thing if it is the last thing we do :lolflag:

---

### Post by kestrel1 on 2009-01-07
You said earlier, that if you type 192.168.1.1 you get the login screen, but are unable to login using admin & admin.
Is this from Ubuntu or Windows?

---

### Post by fahadrather on 2009-01-07
thanks for the support.......i had to reboot because the settings were kept on dhpc and i couldnt get info on that i had to switch it back to roaming mode...

---

### Post by kestrel1 on 2009-01-07
From the screen shot I can see that you have one network config with the two screen, but it looks like you have a second that was still refreshing it self. Am I correct or just dreaming?
If so what do you get from that one when it has refreshed itself.

---

### Post by fahadrather on 2009-01-07
> **kestrel1 said:**
> You said earlier, that if you type 192.168.1.1 you get the login screen, but are unable to login using admin & admin.
Is this from Ubuntu or Windows?

it in ubuntu....in windows i see the settings but i cant change them...i can change them temporarily but not permanently... i mean i change the settings..go somewhere else, comback and the previous settings are restored...i do save the settings...my friend here told me that vpi should be 0 and vci 35 but by default vci is 32...

---

### Post by fahadrather on 2009-01-07
> **kestrel1 said:**
> From the screen shot I can see that you have one network config with the two screen, but it looks like you have a second that was still refreshing it self. Am I correct or just dreaming?
If so what do you get from that one when it has refreshed itself.

on the left is the network monitor for the gprs connection that i am using right now... on the right is the network monitor(still refreshing on roaming mode)Ethernet one..

---

### Post by kestrel1 on 2009-01-07
Once the network monitor has refreshed can you post the output from the Connection Information again?

---

### Post by fahadrather on 2009-01-07
thats the problem...it isn't stopping...i dont know how much more refreshment it will take...its going on and on and on since the last reboot..(roaming mode enabled).. it stops when i keep dhpc or static ip adress but then i cant click on connection information

---

### Post by kestrel1 on 2009-01-07
I have a feeling that your router is not setup as a DHCP server. Are you able to confirm this, if you can see the settings from Windows.

---

### Post by kestrel1 on 2009-01-07
Just had a thought. Can you run the live CD for Ubuntu & see if you get anything then.

---

### Post by fahadrather on 2009-01-07
i did try an ubuntu 7.10 live cd but showed exactly the same error

---

### Post by kestrel1 on 2009-01-07
If you could run a live CD again & type:
```
sudo dhclient
```
I am a bit concerned about the output that you got before from this command.
I am wondering if there is a problem with your network card or something else.
Is there a hard reset on your router? These are often very small buttons that have to be pressed by using a pencil ir something similar. Often with D-link gear you have to hold this button in whilst powering the equipment up.
If you do this, you may be able to gain access to the routers configuration with the admin/admin user & pass.
Just another thought, did you trye using Admin/Admin as the user/pass, note the capital A.
If I don't reply I may have gone to bed & have nightmares about bloody routers. :lol:
So I may catch up tomorrow.

---

### Post by fahadrather on 2009-01-07
i am in windows now..

---

### Post by fahadrather on 2009-01-07
i think we will have to do it in the morning(in your case) afternoon(in mine)....its almost 3 am and i can hardly keep my eyes open...i may also have nightmares about this particular router...but i do wanna see barcelona beat madrid by at least 50 goals...messi scoring most of em..hehe...goodnight(as if we are having a chat on IM)

---

### Post by kestrel1 on 2009-01-07
Got me before I retire for the evening.
Is there anywhere in the tabs that mentions DHCP. I would imagine it would be under LAN or possibly services.
Also under the Admin tab can you change the password?
How are you able to gain access to the router in Windows & not Ubuntu?
In Windows If you go to Start - Run & type:
```
ipconfig
```
What do you get back?

---

### Post by fahadrather on 2009-01-08
nothing....a window opens and closes...thats it.

---

### Post by fahadrather on 2009-01-08
you may take a look at these

---

### Post by kestrel1 on 2009-01-08
Sorry, my fault.
I should have said type this in the run box:
```
cmd
```
Then at the DOS type prompt type:
```
ipconfig
```
Must have been too tired last night.
I apologize for my mistake.

It looks like your router is set to dish out IP addresses via DHCP, so that bit is OK.
Post the output from above commands & see what we get.

---

### Post by fahadrather on 2009-01-08
I took the router to place where i bought this from...he set this thing up to work in windows...xp and vista both can now be connected but ubuntu shows the same error!! i am in windows at the moment..

---

### Post by kestrel1 on 2009-01-08
Cool, at least you have one OS working with it.
Is this a dual boot seup (Windows & Ubuntu) or two seperate machines?
If it is a dual setup, can you run Ubuntu & re-type:
```
ifconfig
```
As post the result.
If it is a seperate machine, can you check your Ethernet connection.
I have a feeling that the router only has a single ethernet port though, so I suspesct a dual boot system.

---

### Post by fahadrather on 2009-01-08
eth0      Link encap:Ethernet  HWaddr 00:16:ec:41:07:95  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:420 (420.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.144.43.185  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:349 (349.0 B)  TX bytes:3290 (3.2 KB)



it is dual boot on both machines....xp on one and vista on one

---

### Post by kestrel1 on 2009-01-08
Can you run the Live CD again & post the result of:```
sudo dhclient
```
You could even post the reult of```
ifconfig
```
but I think the dhclient should help.

---

### Post by fahadrather on 2009-01-08
Good news first the internet started working on the live cd i dont know how the bad news is that when i was just jumping in joy...electricity was cut...:-(

---

### Post by kestrel1 on 2009-01-08
Hope your lecky is back on now.
I had a feeling that it was going to work on the live CD. I think there is a problem with your dhclient on your installed Ubuntu.
I will see if there is a way of sorting this without re-installing.

---

### Post by fahadrather on 2009-01-08
eth0      Link encap:Ethernet  HWaddr 00:16:ec:41:07:95  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:420 (420.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.144.43.185  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:349 (349.0 B)  TX bytes:3290 (3.2 KB)



this was in the live cd

---

### Post by kestrel1 on 2009-01-08
That is what you should be getting in your installed Ubuntu.
I am having terrible trouble with the forum at present, I don't know if you are.
Anyway I still have to look into your dhclient problem, I will get straight on it.

---

### Post by deepclutch on 2009-01-09
I am using D-link GLB-802C for past 6 months in Kerala ,India.This router is specifically made for India with dataone,MTNL easy setup available.
I use bridge mode(where by I dial from Linux to connect).

---

### Post by kestrel1 on 2009-01-09
I have been unable to find a fix for the dhclient problem, as I think that it what is causing the problem where by you are not getting an IP address via DHCP.
I have managed to knacker my 8.04 system, so I will be re-installing it over the weekend. It was actually something I was looking into to try & fix the dhclient prob, but it didn't work. Still it was about time it was re-installed :)
There was big problems with the site last night & I was unable to post then, but hopefully they have sorted it out now.

---

### Post by kestrel1 on 2009-01-10
I had a thought, should have thought of it before though.
You could setup your machine with a staitic IP address if dhclient isn't working correctly.
No time to explain right now, but should be back in a few hours.

---

### Post by kestrel1 on 2009-01-10
OK, to set up a static IP address do the following:
Left click on the Network Monitor icon in your top panel & select Manual Configuration.
Once the Network Settings window opens, click on Unlock & enter your password. Then click on Wired Connection & select Preferences.
Untick the Roaming Mode box & from the drop down list under Configuration select Static IP Address.
In the IP Address text box enter an IP address in the same range as your router & preferably out of the DHCP range. I see from an earlier screen shot that your DHCP server side of the router is set to a range of 192.168.1.3 to 192.168.1.34, so you can choose an IP address of 192.168.1.35 - 255
I would suggest using 192.168.1.40, no real reason, just a round number (40 that is)
Then under the Subnet Mask, which in your case will be 255.255.255.0. Final step, under Gateway Address enter the address of your router, in your case 192.168.1.1 I do believe.
Click on OK & then Close. With any luck you will get a connection to the router. To confirm this Right click on the Network Monitor icon & select Connection Information.
With any luck you will see a window with the settings that you have just entered. If not restart the machine, but you shouldn't need to do that.
Anyway, let us know.

---

