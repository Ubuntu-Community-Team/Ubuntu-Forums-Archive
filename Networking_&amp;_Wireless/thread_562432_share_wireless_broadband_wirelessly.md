---
title: "share wireless broadband wirelessly?"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by cobelloy on 2007-09-28
Hi, I have bigpond wireless broadband here in rural australia - the blue external modem, set up and working very nicely on ubuntu. (for those who dont know it is a bigpond branded maxon unit and it is the only modem option for a desktop pc with this provider, and the only broadband option where I live other than expensive sattelite which takes up to a year to get installed) The modem connects to the 3g/"NextG" wireless network via its antennas and connects to the computer via a usb cable and is designated ppp0 - it does not show up in Knetwork manager, but does show up in ifconfig.

eth0      Link encap:Ethernet  HWaddr 00:13:72:81:F1:49
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169

eth1      Link encap:Ethernet  HWaddr 00:02:72:63:0F:DD
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:124.178.144.172  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3136778 (2.9 MiB)  TX bytes:659423 (643.9 KiB)

as you can see I also have eth0 (ethernet port - unused) and eth1 (wireless dongle)

I would like to be able to share the internet connection with other computers in the house that have wireless adapters, one old laptop with puppylinux (it has no HDD), and a new one with windowsXP.

I also have a good wireless router that I tried to use in windows before I had the modem going in linux, but in windows the modem must be assigned the internal IP 192.168.0.1 - which is also the same IP that the router also must have - so the router was no good there.

[IMG]http://i87.photobucket.com/albums/k129/cobelloy/network.jpg[/IMG]

this is what I am trying to do.

---

### Post by spd106 on 2007-09-29
There are two parts to this, so we'll tackle them separately.

1. ICS - To share the PPP connection you will have to set up NAT, and forward the connection out to your home network. The PCs will then be masqueraded by the gateway PC that has the PPP link. There are several wiki pages about this, the easiest way is through the Firestarter application.
See [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

2. Wireless - You possibly have two option, depending on whether your devices support ad hoc mode or not. 
i) Ad hoc - It's rare for USB dongle drivers to support ad hoc on Linux, so I wouldn't hold out too much hope. Other than that you'll have to go through the wireless router.
See [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported),
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
and [https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

ii) Wifi router - It doesn't look like you will have an IP conflict because you can set the Ubuntu PCs IP address to what ever you want, as long as it's on the same subnet as the router. You'll have to change the IP address of the gateway to the Ubuntu PC, so it's best to set that manually (read static). By default the router will be set to use itself as the gateway, which would be wrong in this case.

There are many more pages in the wiki about this, so don't be afraid to have look around.

---

### Post by cobelloy on 2007-09-29
this is really hard.

the router is no-go because it wont run its setup program without an active internet connection plugged into its internet socket (it has five sockets on its rear panel, one for internet and four for wired network access, plus a wireless antenna to give wireless access to the network)

if I could use this computers ethernet port to 'send' the internet connection to the router's internet socket then it would be a simple thing to set up the router to share the internet - Ive done that before with sattelite internet

is there some way to set up an ethernet card to do that?

[IMG]http://i87.photobucket.com/albums/k129/cobelloy/net1.jpg[/IMG]

where the purple arrows are the internet signal, even if the main computer also had to get internet from the router the same as any other laptops etc

I still dont know how to share the internet

from the first link - the first instruction:

cobelloy@cobelloy-desktop:~$ $sudo ifconfig ppp0 192.168.0.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

and any attempts to modify /etc/network/interfaces has so far resulted in messing things up so that network manager wont run.

I have been able to share this in windows although that was not straight forward either - bigpond provide "connection manager" software which completely disables internet connection sharing in windows, stopping you from sharing one connection at home - forcing you to buy more $400 modems and internet plans

the only other option I am aware of is an expensive router designed to connect to this modem by usb and establish a connection, however that is not a wireless router it is a wired router which doesnt solve this problem anyway

---

### Post by spd106 on 2007-09-30
You don't need to change the PPP link, just the internal network.

What brand/model of router is it? You should be able to bypass the setup wizard and set things manually. All you need to change is the DHCP server settings in order to point the gateway to your PC. It should then just act as a switch, instead of a router. Bare in mind that this will bypass the built-in firewall (if it had one), we'll be using the Ubuntu PC for that instead.

Open System -> Admin -> Network and make sure the wired interface (eth0?) has roaming mode disabled (unticked) in Properties. Set the configuration to Static IP address and in the IP address and netmask something like 192.168.0.100 and 255.255.255.0, no gateway is needed.

From this point it's probably advisable to use [Firestarter]("https://help.ubuntu.com/community/Firestarter") to set up the sharing support. Select ppp0 as the Internet interface and eth0 as the local network device. You won't need DHCP, the router should be able to handle that. If not just set static IPs on the client PCs, making sure to use 192.168.1.100 (PC) as the gateway.

---

### Post by cobelloy on 2007-09-30
thank-you for your help,

the router is netgear MR814v3 and there is no mention of an alternate way to access its settings in any of its documentation, to set it up I connect a computer to one of its wired ports and go to 192.168.0.1 and if it has been reset (which it has) it redirects to its setup URL which first searches for an internet connection at its internet port, the only options then are to cancel the router setup or plug in the internet - it wont go any further

as for firestarter I did have it installed but it wouldnt work, it took ages to start then it would hang - I also thought this would simplify the situation, if I waited long enough I could get to the bit where it asked which was the internet connection - the box had eth0 selected, but when I clicked the arrow to see the other options the system hung and needed to be reset

not to worry though, I have given up and bought a router that can pair with the modem, it has firmware that can dial the modem, it cost a lot less than I thought and it is also acts as a wireless access point

---

### Post by spd106 on 2007-10-01
Firestarter can be annoying when it refuses to work. This can happen when any of the interfaces it's been told to use aren't activated. Normally it should just work, so I'm not quite sure what's going on there.

Looking through the Netgear website, there is this page on bypassing the wizard, [http://kbserver.netgear.com/kb_web_files/n101472.asp](http://kbserver.netgear.com/kb_web_files/n101472.asp)

I'm not sure how useful that would be, but it sounds like it would work.

[QUOTE=cobelloy]not to worry though, I have given up and bought a router that can pair with the modem, it has firmware that can dial the modem, it cost a lot less than I thought and it is also acts as a wireless access point[/QUOTE]

Sorry that I couldn't help,  but I'm glad to see you've found a solution.

---

### Post by warduke on 2007-10-01
check and see if your router will work with alternate firmware.  google DD-WRT for an example.

I use it on a few of my routers and they are now Godly compared to when I bought them.

---

### Post by cobelloy on 2007-10-12
it cant just be easy can it?

the new router I bought only does this job with 3rd party firmware - one of a few linux based alternatives will suffice, but try as I might it wont accept any new firmware, even the official acer firmware.

however it will still be really useful because I can plug my two external hard drives into the usb ports to share them easily around the computers here.

of course that still leaves me with the original dilemma, how to share internet from my computer.

-interface ppp0 is only 'there' when it is active, and it is not always active - and it gets a dynamic IP when it logs on, and I have to insert the usbserial module every time i boot (sudo insmod /lib/modules/2.6.17-50-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280)

-firestarter wont work - it hangs every time I start it (it is now removed, have tried reinstalling it, same problem)

-I have guarddog and guidedog - can i use those to help me configure internet sharing, if so how?

-eth0 and eth1 (wired and wireless adapters), when activated, disable ppp0 as the internet gateway, and since ppp0 does not show up in knetwork manager I cant set it to be the default gateway, if the other network interfaces are disabled then it becomes the default gateway when it logs on to the internet

-I am using kubuntu by the way - the modem instructions were for kppp, and I just wanted to follow the instructions I had, not modify them for a gnome dialer

:( please help

---

### Post by sharke on 2007-10-14
cobelloy
have you seen this may help.
[https://maxon.com.au/udocuments/Quick_Start_Guide.pdf](https://maxon.com.au/udocuments/Quick_Start_Guide.pdf)
Regards
Sharke

---

### Post by cobelloy on 2007-10-18
that is instructions for the 'ethermax docking station'

which isnt what i bought, it is much more expensive and is not really a router, it is a device that can dial that modem and route internet to one ethernet cable which then needs to be plugged into a computer or a router,

but thanks anyway, I am still going with this, I will have some more time to mess with it again tomorrow

---

### Post by sharke on 2007-10-18
> **cobelloy said:**
> thank-you for your help,

the router is netgear MR814v3 and there is no mention of an alternate way to access its settings in any of its documentation, to set it up I connect a computer to one of its wired ports and go to 192.168.0.1 and if it has been reset (which it has) it redirects to its setup URL which first searches for an internet connection at its internet port, the only options then are to cancel the router setup or plug in the internet - it wont go any further

as for firestarter I did have it installed but it wouldnt work, it took ages to start then it would hang - I also thought this would simplify the situation, if I waited long enough I could get to the bit where it asked which was the internet connection - the box had eth0 selected, but when I clicked the arrow to see the other options the system hung and needed to be reset

not to worry though, I have given up and bought a router that can pair with the modem, it has firmware that can dial the modem, it cost a lot less than I thought and it is also acts as a wireless access point

TRY This in windowa 
Disconnect netgear from power   shutdown computer   plug power to netgear   connect computer to lan port on netgear   boot computer to windows   goto start run   enter [http://www.routerlogin.com/basicsetting.htm](http://www.routerlogin.com/basicsetting.htm)   and if remembered correctly it should take you to the basic setup for netgear with out requiring a connection .
Regards
Sharke

---

### Post by cobelloy on 2007-10-21
OK

i still have no joy

the router firmware cannot be changed - it will not accept new firmware, so I cannot use it to dial the modem

so I need to share the internet from my PC

firestarter will not work - so I cannot use that.

this link: [https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing") is no use because the first instruction is to set the IP of the internet connection to be 192.168.0.1 and I cannot do this as it recieves an IP from the server when I log on, changing the IP will break the connection.

surely there is a way to share the ppp0 internet without it having to be 192.168.0.1 ?

please help - I am going mad here

---

