---
title: "Is remix support Wine?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Harshana on 2009-11-02
Hi Everybody............
 I bought netbook computer and i'm thinking to install UBUNTU REMIX FOR NETBOOKS.And i also want to install WINE too.I downloaded REMIX.But i could not find a link to download WINE.
The ADSL modems to buy in here(Srilanka) does not have ubuntu drivers and they are USB.
There for cant use ADSL with ubuntu.So i want to install wine first to use internet.So i want to know are..

1. Will Wine compatible in UBUNTU REMIX edition?
2. Will modem drivers work with Wine?
3. Is there any way to download Wine(as a file or set of files)
for manual inasattation?:KS

---

### Post by unamanic on 2009-11-02
1) Wine will run on a netbook, but they are not very powerfull so I wouldn't recomend it.
2) Wine is for running applications not drivers.

I recommend doing this, download UNR and load it in on a USB stick.  Boot into the live linux environment and give the ADSL modem a try.  They might not supply the drivers, but they may already be part of Ubuntu.

---

### Post by Aearenda on 2009-11-02
To answer your specific questions:
1. Yes, Wine will install in the Netbook Remix; but....
2. No, modem drivers will not work in Wine, since they are not application programs but bits of the operating system. For traditional network drivers, ndiswrapper provides a way of getting Windows drivers to work in Ubuntu, but I don't think it applies here either owing to the USB connection.
3. You install Wine using the same tools as anything else in Ubuntu - for example Synaptic Package Manager, or the command 'sudo apt-get install wine'. Don't try to install it any other way.

To address your broader issue, I suggest you start another thread asking for help in getting your USB modem to work (after searching the forums just in case anyone has already done it), since the title of this one will not attract attention from people who can help (I don't have a USB modem).

---

### Post by Harshana on 2009-11-02
> **unamanic said:**
> 1) Wine will run on a netbook, but they are not very powerfull so I wouldn't recomend it.
2) Wine is for running applications not drivers.

I recommend doing this, download UNR and load it in on a USB stick.  Boot into the live linux environment and give the ADSL modem a try.  They might not supply the drivers, but they may already be part of Ubuntu.

Thanx.But
What is UNR?
I did not get what should i do.U mean Load UNR to USB stick and boot form it... and then..........?

---

### Post by Harshana on 2009-11-02
Thanx.But
What is UNR?
I did not get what should i do.U mean Load UNR to USB stick and boot form it... and then..........?

---

### Post by Harshana on 2009-11-02
> **Aearenda said:**
> To answer your specific questions:
1. Yes, Wine will install in the Netbook Remix; but....
2. No, modem drivers will not work in Wine, since they are not application programs but bits of the operating system. For traditional network drivers, ndiswrapper provides a way of getting Windows drivers to work in Ubuntu, but I don't think it applies here either owing to the USB connection.
3. You install Wine using the same tools as anything else in Ubuntu - for example Synaptic Package Manager, or the command 'sudo apt-get install wine'. Don't try to install it any other way.

To address your broader issue, I suggest you start another thread asking for help in getting your USB modem to work (after searching the forums just in case anyone has already done it), since the title of this one will not attract attention from people who can help (I don't have a USB modem).

Ok. Thank you very much....!
:popcorn:

---

### Post by unamanic on 2009-11-02
UNR = Ubuntu Netbook Remix

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Boot from the USB stick you make from those instructions and try it out.  You do not need to install it to try it.  You may find that your modem just works.

---

### Post by Harshana on 2009-11-02
> **unamanic said:**
> UNR = Ubuntu Netbook Remix

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Boot from the USB stick you make from those instructions and try it out.  You do not need to install it to try it.  You may find that your modem just works.

Ok....:D

Thanx
:popcorn:

---

