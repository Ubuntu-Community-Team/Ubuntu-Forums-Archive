---
title: "How to connect to mobile network"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by 2blue on 2009-07-19
I am having trouble installing a mobile network. It is a USB memory-stick like divice with a built in wizard that guides you through the installing prosess. It works fine in Windows but the wizard doesn't start in Ubuntu. When I connect the USB network device to the laptop a Ubuntu installing program starts automatically, and it needs a lot of configuration. 

The only info I have is the name of the mobile network, the "phone" number and a pin and puck code. When I fill the Ubuntu installing/configuration forms it doesn't really work. I get to register a network on the laptop but I don't get a connection to the mobile network. In the Ubuntu installng/configuration process I do get a list of operators to choose from and mine is on the list. However some of the lines I am forced to leave empty. 

I suspect this USB device is a bit tricky because when it is used in Windows it over-rides the ordinary network-managing software, leaving it out of use. All networks in the area are managed through the software that comes with the USB device (which is very annoying).
Any Idea how to go about this?

---

### Post by ugm6hr on 2009-07-19
I'm afraid it will be impossible to help without knowing some actual details.

Country, USB modem model, network, tariff at a minimum.

Is this a 3G/HSPDA modem?

This may contain all the necessary settings: [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

---

### Post by lisati on 2009-07-19
> **ugm6hr said:**
> I'm afraid it will be impossible to help without knowing some actual details.

Country, USB modem model, network, tariff at a minimum.

Is this a 3G/HSPDA modem?

This may contain all the necessary settings: [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

I concur.

I suspect that the reason that the "Wizard" only works in Windows is that it was designed for Windows - Windows software doesn't work without help on Ubuntu.


edit: There is hope. I have a 3g phone by ZTE. The software it came with only works with Windows, but it can be used with Ubuntu. Some of the settings need to be done manually, because Ubuntu doesn't list the provider I use.

---

### Post by nubimax on 2009-07-19
I have an Sony Ericsson MD300 device and it will only support windows vista, XP and Mac OSX OS.  I only use it when traveling in Mexico I have to use another provider for linux.
M

---

### Post by /usr/sbin on 2009-07-20
I have a 3 dongle. I configured it by going to network connections, i cant remeber it all, please correct me if im wrong but then i selected new wireless broadband, then it said what country and what provider, then i clicked next then i clicked finish and it worked.

---

### Post by 2blue on 2009-07-20
I live in Norway, network (on a windows laptop) usually says EDGE, but now when you mention it I notice it does say HSPDA and UMTS some times. The USB modem (the usb memory pen like thing) and network is delivered by Telenor. On the USB modem it says "Qualcomm 3G CDMA, FCC ID NCMOGIO225, Model GIO225" (The two last "O"s, right before the numbers might be "0")"Designed by Option, Made in Ireland" . Are these some of the numbers I am suppose to fill in when configurating?

---

### Post by ugm6hr on 2009-07-21
A quick google revealed this:
[http://forum.ubuntu.no/viewtopic.php?f=24&t=1420&p=10605&hilit=mobile+broadband#p10605](http://forum.ubuntu.no/viewtopic.php?f=24&t=1420&p=10605&hilit=mobile+broadband#p10605)
> Endelig! :)

Nå virker Telenor USB modemet i ubuntu 904. Ubuntu finner automatisk modemet når jeg plugger det inn, og så velger jeg Norge og Telenor. Så åpner jeg Networkmanager (høyreklikk og velg Edit Connections), gå til Mobile Broadband. Velg telenor og klikk Edit. Her legger du til:

Dailup nr: *99#
Username: ditt telefonnummer på modemet
Password: ditt telefonnummer på modemet
APN: telenor

Så får jeg spørsmål om å lage Keyring user and password, her klikker jeg bare videre og velger unsafe storrage. Du kan sikkert også velge ett brukernavn og passord her, men da blir det sikkert bare en hel haug med masing etter passord hver gang du skal logge deg på. Så fikk jeg enda ett spørsmål om å slå inn ett passord til telenor, og her brukte jeg telefonnummeret til modemet. Etter alt dette, så logget modemet seg på og jeg kunne laste ned informasjon via nettet :) Jeg slår av WLAN mens jeg bruker 3G modemet (fysisk bryter på laptoppen).

Så, nå håper jeg andre også kan få brukt Telenor modemet i ubuntu..

Perhaps you might be able to use that.  according to Googlge Translate, it appears it works with:
> Dailup no: * 99 #
Username: your phone number on your modem
Password: your telephone number on the modem
APN: Telenor 

Perhaps you could report back here if it does work, and update the wiki page I recommended earlier with details, since Norwegian network detail is somewhat limited.

---

### Post by 2blue on 2009-07-21
Thank you very much ugm6hr! Give me two days and I'll give a report as soon as I get home (There is pretty good  network where I am now, much faster than the mobile network so I left it at home). Might sound a bit silly but I have never used the Norwegian Ubuntu forum. I have to do something about that.

---

