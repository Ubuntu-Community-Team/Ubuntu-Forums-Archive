---
title: "Second NIC will not recognize."
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by randomnumber on 2007-01-23
I have been thinking about setting up a server with my desktop, just for the experience of it. I want to install a second NIC so that I can place the desktop between the modem and the router.

The second NIC will not recognize. It is a linksys nc100.
-------------------------------------------------------------------------
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:6E:FE:0B  
          inet addr:192.168.1.203  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe6e:fe0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:20593145 (19.6 MiB)  TX bytes:1467416 (1.3 MiB)
          Base address:0xcf80 Memory:fe9e0000-fea00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6355 (6.2 KiB)  TX bytes:6355 (6.2 KiB)
-------------------------------------------------------------------------
lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600 Ultra] (rev a1)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller (LOM)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
03:0c.0 Non-VGA unclassified device: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)


There was probibly a better way to post the above but I don't know it.

Thanks in advance. BTW I consider myself to be a advance user, just a little more experienced than a "newb". I can use terminal a little. If you notice the card is seen in lspci (last line) but not ifconfig. It seems to not have a driver.

---

### Post by dmizer on 2007-01-23
well, i have just the thing for your linksys nc100 card.

[http://www.ubuntuforums.org/showthread.php?t=264954](http://www.ubuntuforums.org/showthread.php?t=264954) <- it's for a pcmcia adapter, but the problem is identical.  you can simply ignore the steps regarding the pcmcia stuff.

---

### Post by randomnumber on 2007-01-23
I tried the suggestion but it seemed to not do anything.

I edited the file to the new spec and even rebooted. Perhaps I missed something.

---

### Post by randomnumber on 2007-01-23
Maybe there is not a driver for this card. I see many people having the same problem with nc100 cards with no solutions.

---

### Post by dmizer on 2007-01-28
humm ... have you tried connecting to the internet with that card alone? (ie with the original adapter disconnected or disabled)

---

### Post by abygomez on 2007-01-28
hi,

i am new to ubuntu. i was able to configure my wifi card (belkin) using this procedure.

[https://help.ubuntu.com/community/Wi...211b_driver%29](https://help.ubuntu.com/community/Wi...211b_driver%29)

It works well in a 64 bit wifi atmosphere because the password length is small. but when it comes to a 128 bit wifi atmosphere i could not type in all the 26 charecters in to the password box. is there any way to enter all the 26 hexadecimal charecters in to the password box.

---

### Post by randomnumber on 2007-01-28
I disconnected the network cord from the first one and connected it to the new one. The LEDs lit up and everything. The OS sees the card but doesn't know how to use it, it seems. I have considered just going and getting a new one, they only cost 20$. It is something I was just wanting to experiment with.

The first NIC is onboard. I should be able to disable it in the bios if you think that would do anything.

---

### Post by randomnumber on 2007-01-29
> **abygomez said:**
> hi,

i am new to ubuntu. i was able to configure my wifi card (belkin) using this procedure.

[https://help.ubuntu.com/community/Wi...211b_driver%29](https://help.ubuntu.com/community/Wi...211b_driver%29)

It works well in a 64 bit wifi atmosphere because the password length is small. but when it comes to a 128 bit wifi atmosphere i could not type in all the 26 charecters in to the password box. is there any way to enter all the 26 hexadecimal charecters in to the password box.

this is not a wifi card. just a 10/100 nic. Thanks though

---

### Post by dmizer on 2007-01-29
keep in mind that if you're using two nics, they will have to be configured on a different subnet.  (ie, they can't both be 192.168.1.x).  you will not be able to make them both work on 192.168.1.x

humm, try posting the output of:
lsmod

as well as:
dmesg

and the contents of:
/etc/network/interfaces

the better way to post those kind of entries is with [code] tags ... used just like [quote] tages when you're quoting someone.

as an asside, i wouldn't suggest putting any computer on the outside of a router.  i've read it many places ... you have to go THROUGH a hardware firewall (router), but you just have to go around a software firewall (firestarter).

---

### Post by randomnumber on 2007-01-30
Why do so many setups I see have a server on the outside of a router. What is the benefit. I was thinking that I could start my sever from the Internet if i set it up this way.

I am going to try to post the file as attachments. If you want the the other way I would be glad to comply. I just thought it would look better with these very large files.

---

### Post by randomnumber on 2007-01-30
guess the attachments did not work: demesg was too large and all the file had to be txt

Sorry

---

### Post by dmizer on 2007-01-30
> **randomnumber said:**
> Why do so many setups I see have a server on the outside of a router. What is the benefit. I was thinking that I could start my sever from the Internet if i set it up this way.

i don't know of any real benefit.  i can only think of problems with the arrangement.  it's possible that some of the setups you saw were doing internet connection sharing with a hub instead of a router.  a cheaper, but less secure setup.  you already have a router, so i suggest you make use of it.

another problem is that some older routers' dhcp capabilities were not so hot, so the server's dhcp address was a moving target which necessitated either a static local network, or the arrangement you're talking about.  but now, most retail level routers are capable of attaching an ip to a mac address, so you can retain your dhcp network and not have your server jumping all over the place every time it starts/restarts.

not sure what you mean by "starting your server".  if you mean that you intend to send a magic packet, you're going to be disappointed because your server will get triggered constantly.  if you just mean starting apache or some other server related service from remote, you can forward port 22 for ssh just as easily as you forward port 80.  remember, anything exposed directly to the unfiltered internet will require some _serious_ security considerations.

to boot, a modem -> server -> hub -> localnet type network will be more difficult to configure, and also be more prone to failure.  i do highly suggest avoiding such a headache unless there's a real need for it.  i've been there, it's no fun.

something that will allow you to make use of both of your network cards as well as be interesting for you to play with though (on a server level) would be to build an isolated subnet where you can test routing protocols and do packet sniffing in a controlled environment.

anyway ... i do need to see your dmesg output.  the [code] tags will keep the post from scrolling off to infinity.

---

### Post by randomnumber on 2007-01-30
ok, you convinced me.  I meant that I was wanting to be able to boot the server/pc from the internet. I turn off the PC because it is too noisy. 

I just realized that if i zip the file i can put them on the server. So all files are in Zip.  Guess I am still learning this forum stuff.

Thanks.

---

