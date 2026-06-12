---
title: "How on earth do you connect to the internet"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by shoutroom on 2007-06-30
Hello guys...
After learning that Linux is capable of offering me a much safer and secure OS interface in comparison to Windows (I just knew about Linux and I am a complete newb at it), I burned an Ubuntu live cd and dual booted the OS with my computer. However, after fiddling around for a few days, I figured no way to fix my internet connection when working with Ubuntu.(I'm using a broadband connection) Using my normal vista premium, things worked well. I can connect to the internet swift and fast. But when booting the computer into Ubuntu, I followed the FAQ advices, configuring my network settings to the automatic detect one. After a few minutes, a small hit box popped up on the small connection icon located at the top right corner of the panel. The box read: Connection Established - You can now connect to the wired network (I'm not connecting to the internet via wireless). However, when I tried to ping websites, I didn't receive any packets back; or when I surfed through the internet using firefox,I saw the usual error which is displayed when my internet breaks down.

I had been looking through the net for a solution to this for quite some time...however, no luck.:(

I will appreciate any attempts in helping me get through this problem.


Regards, Sunyan

---

### Post by solar george on 2007-06-30
Open a terminal (Applications>Accessories>Terminal) and type ifconfig and post the output here. 

Also what make/model of modem are you using?

---

### Post by newbun on 2007-06-30
If you don't mind, guys I'll join in this thread because I think I'm in a similar position.

I've installed UBUNTU 7.04, but have no net connection

Ok, I have a USB/ADSL504 Binatone modem which I use for my broadband connection on Windows xp.  ( I still have the original adsl cd for the modem.....will it work on Ubuntu??)  Anyway,  I did what you requested of the previous poster, and got the following:

eth0      Link encap:Ethernet  HWaddr 00:07:95:18:80:C4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6352 (6.2 KiB)  TX bytes:6352 (6.2 KiB)

I'm a newb, and have NO IDEA what all this means.  

I need a net connection via the USB/adsl modem and probably need the software driver for the modem, so that UBUNTU can recognise it??  I'm guessing that the system is not 'seeing' the usb modem, even though its plugged into one of 2 usb ports.

If anyone can help, I'd be grateful - thanks
If someone DOES reply (hopefully) please,please keep your suggestions basic(for now) until I get the hang of this wonderful alternative to Windows XP.  It would also help, if the above was explained?

As an extra bit of info:  lsusb ( I saw this in some other post) gives:

Bus  002 Device 002: ID 2001:5100 D-Link Corp.  [hex]
Bus  002 Device 001: ID 0000:0000
Bus  001 Device 001: ID 0000:0000

---

### Post by solar george on 2007-06-30
I don't have any knowledge of USB adsl modems - I would recommend a combined router-modem because all the setup is (usually) done via a web interface.

Try looking at [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-usb](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-usb)

---

### Post by newbun on 2007-06-30
Ok, plan B is that I have a netgear wireless adsl modem router, which is how I'm sending this using xp.

The Ubuntu system is an amd athlon which the usb/adsl modem is 'connected' to.  So, IF I get a USB wireless  adaptor for the athlon, and plug it into one of the USB ports, how will UBUNTU treat it....will it recognise that it's a wireless adaptor, or is that too simple - and does  it need other stuff to tell it what it is??

Please help if you can.

thanks

---

### Post by solar george on 2007-06-30
You will need to check compatibility - see
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

---

### Post by newbun on 2007-06-30
Ok, I'll check those links.  Are you saying that IF the (intended) USB wireless adaptor is compatible....thats it????  Can I then connect to the net, that way???

---

### Post by solar george on 2007-06-30
Yes (hopefully).

That is I can see no reason why you shouldn't be able to connect, use wep encryption for the easiest setup.

---

### Post by newbun on 2007-06-30
Netgear 
 WG111v2 
 rtl8187 
 ? 
 Yes 
 Yes 
 Works out of the box with Feisty. 
 2007-06-07 
 USB 
 
I can get THIS model....one of those links(2nd) says it SHOULD work. Can you tell me if it's just plug&play with Ubuntu.....or (as I said before) is that too easy???

---

### Post by newbun on 2007-06-30
Just saw your latest reply....thanks for all your help, you've been very patient.

---

