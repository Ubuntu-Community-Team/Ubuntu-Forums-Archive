---
title: "How to assign service name in ubuntu"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by rajwraith on 2009-03-03
I use an internet connection where I need to put in my username and password to connect to my ISP.
In XP I had to assign the service name of my ISP by right clicking on the Connection Wizard thingy and just writing down "zip".
How can I do the same in ubuntu? Cause i really cant connect to the internet now, and i'm really starting to miss Ubuntu, and i simply don't like XP. Please help. I've tried googling it but alas! they were in vain.

---

### Post by khelben1979 on 2009-03-03
What type of modem are you using?

If you are using KDE you have the [KPPP]("http://en.wikipedia.org/wiki/Kppp") program which you can configure up and using for dialing up your ISP.

With Gnome you have [Wvdial]("http://en.wikipedia.org/wiki/Gnome-ppp").

---

### Post by rajwraith on 2009-03-07
I use pppoeconf to type in the pass and the username. Can i use pppoeconf to set my service name?And how do i set the service name with WvDial?

---This a sample config file of weave dial. Where do i change the values to put in the service name?

[Dialer Defaults]
Modem = /dev/ttyS2
Baud = 57600
Init = ATZ
Init2 = AT S11=50
Phone = 555-4242
Username = apenwarr
Password = my-password 

[Dialer phone2]
Phone = 555-4243 

[Dialer shh]
Init3 = ATM0 

[Dialer pulse]
Dial Command = ATDP

---

### Post by khelben1979 on 2009-03-07
Look on [this page]("http://support.real-time.com/linux/dialup/wvdial.html"). From what I can see it seems they have pretty good documentation on the subject.

---

### Post by rajwraith on 2009-03-10
i think i made a big boo boo. I don't use a dial up connection. My one's broadband. And gnome-ppp or wvdial doesn't really allow me to assign the service name. I've checked and googled and I messed up Ubuntu pretty bad which resulted in my sudo to go haywire. But that's ok now. Got any other solutions for this newbie?

---

### Post by GeorgeVita on 2009-03-10
Hi **rajwraith**,
what kind of modem are you using? (same question as khelben1979)
Manufacturer, model, type (ADSL or UMTS/3G)?
Do you have any other modem in your PC (s/w or h/w PSTN card)?

Connect your modem, open a terminal window and type: **lsusb**
then try: **ls /dev/ttyU* /dev/ttyA* /dev/ttyS***
copy paste all data to show how Ubuntu recognizes the modem and what kind of port assigns to it.

What is your Ubuntu version?

Do you know the "service name"?

In my case, I am using a ZTE MF636 (3G modem) for mobile broadband with Ubuntu 8.04 and the APN (internet service for my provider) is entered with AT commands through wvdial.conf (Init3 =AT+CGDCONT=1,"IP","internet").

Also post the output of your **sudo wvdial ...** command to see the modems respond.

Regards,
George

---

