---
title: "How to connect Reliance USB"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by halovivek on 2009-06-02
Hi 
Last Week i bought the USB to connect internet.
[Link]("http://connectindia.in/Reliance-Data-Card")
I am from India. Could you please help me how to connect to Internet using USB?

I am getting software only for Windows not for linux.

---

### Post by ChaiTan on 2009-06-02
What's the model name of the modem?

---

### Post by clive littlewood on 2009-06-02
Hi

Try this      [http://www.techbangalore.com/having-reliance-netconnect-usb-card-to-work-on-linux/](http://www.techbangalore.com/having-reliance-netconnect-usb-card-to-work-on-linux/)


Clive

---

### Post by halovivek on 2009-06-10
Thanks for the post i will check and get back to you today midnight - Indian standard time.

---

### Post by ankscorek on 2009-06-10
i am using a ZTE modem on 

ubuntu jaunty

19d2:fff6

i added the vendor id and product id to the menu.1st file

also when i log in the 

#tail -f /var/log/messages shows my modem is attached to ttyUSB0

here is the problem-->

#wvdialconf

it is unable to detect my modem on any serial port or on ttyUSB0<*1>

i am typing this from windows 

my ubuntu box is offline

any suggestions will be appreciated

---

### Post by t0p on 2009-06-10
You might find my tutorial on using a cellphone as a modem helpful (see the link in my sig).  I realise you are using a USB dongle, not a cellphone, but the principle is the same, especially if you are using wvdial.

I have found the [Vodaphone Mobile Connect Card Driver for Linux]("https://forge.betavine.net/frs/?group_id=12") to be an excellent way to connect.  It says "Vodafone" in the name, but it actually works with any mobile service provider.

---

### Post by ankscorek on 2009-06-10
hey tOp r u suggesting me to use usb-modeswitch package

but dmesg already confirms that my generic converter is already connected on ttyUSB0

incase u want me to use usb-modeswitch how do i do that please?i mean anything beyond 
#sudo dpkg -i usb-modeswitch.deb

---

### Post by halovivek on 2009-06-11
Hi tried the tutorial but it says it does not find the modem.
i can go ahead with this much only.


Bus=05 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=fff6 Rev= 0.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=USB Storage
S:  SerialNumber=000000000002
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=89(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=0a(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms


how to go ahead more?

---

### Post by ankscorek on 2009-06-11
i am following this link 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=134&postdays=0&postorder=asc&start=15&sid=d10963b82e71638e4e54a4613f156950](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=134&postdays=0&postorder=asc&start=15&sid=d10963b82e71638e4e54a4613f156950)

now the problem is that it is a product id fff1 however it is displayed as fff6

so i suppose we need a usb mode switch

tOp-->a help is appreciated

i tried the the message state also but also

wvdialconf is not recognising me on ttyUSB0

do i do a mknod in that case

i was successful using the usb mode switch to get the product id to fff1

so do i do a mknod /dev/ttyUSB0 c 188 0

even after doing all the stuff and even the hardware is switched to modem mode the wvdialconf is unable to initialise my modem any suggestions please

**[COLOR="Red"]well after checking from proc devices i came to know that productid=fff6 is zte recognised as storage device onto ttyUSB0.when i do usb mode switch the proc devices recognises it as cdma modem(id=fff1) but detatches itself from ttyUSB0..where does it get attaches /var/log/messages just tells it is getting detatched..any hints please[/COLOR]**

---

### Post by halovivek on 2009-06-11
hallo anyone please help :) need to update around 600 MB of update. In Reliance USB i am getting around 100 -120 Kpbs speed ( i am using that in windows). If i get this i will be fully in Linux only.

---

### Post by ankscorek on 2009-06-12
after using usb mode switch it is switching my device to modem mode but i think [COLOR="black"]**the error it says no active driver found needs to be looked into**[/COLOR] anyways here is the crude solution i worked out

for the benefit of people who could not pull it out here is a solution i worked out for ubuntu jaunty

[B][COLOR="DarkOrange"]i added the target vendor and product id to my menu.1st file

then used this command

/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch_zte_mf627.conf

that was it was up and working..

to be noted the command is to be issued as soon as u plug in the modem ..u might have to issue this command two to three times or more ..wvdialconf will detect ur modem at 9600bps[/COLOR][/B]

i know this is a crude method but with jaunty buliding in usbserial module i had no choice left and hence had to go this way
the method i wrote on top has given success ..

any better solutions are invited please

---

### Post by Dexter_Greycells on 2009-06-21
I have a Reliance NetConnect ZTE MG880 CDMA1X modem. I am running Jaunty Jackalope (9.04). After 2 weeks of searching through Google and Ubuntuforums I stumbled upon the following link which helped the detection and configuration of the modem - 

[http://jeysundar.blogspot.com/2009/05/reliance-net-connect-on-ubuntu-kubuntu.html](http://jeysundar.blogspot.com/2009/05/reliance-net-connect-on-ubuntu-kubuntu.html)

The connection drops if you don't use it often. And you will always need to use the <sudo pon reliance> command to switch it on.

---

### Post by halovivek on 2009-06-26
> **Dexter_Greycells said:**
> I have a Reliance NetConnect ZTE MG880 CDMA1X modem. I am running Jaunty Jackalope (9.04). After 2 weeks of searching through Google and Ubuntuforums I stumbled upon the following link which helped the detection and configuration of the modem - 

[http://jeysundar.blogspot.com/2009/05/reliance-net-connect-on-ubuntu-kubuntu.html](http://jeysundar.blogspot.com/2009/05/reliance-net-connect-on-ubuntu-kubuntu.html)

The connection drops if you don't use it often. And you will always need to use the <sudo pon reliance> command to switch it on.

I tried this one also. Still it is not working. Anyone can tell me how to check and go. I will post all the output what you have need to help me.

---

### Post by t0p on 2009-06-26
Terribly sorry I haven't got back to you before now!  I didn't subscribe to this thread, so I'm afraid it dropped from my notice.  But anyway!

My adventures in using a mobile phone as a modem, and more recently using a mobile broadband usb dongle, have taught me a few things about this subject.  The link in my sig leads to a tutorial I wrote some time ago about using **wvdial** to connect via a cellphone - but I think you have tried that already?  I have also given advice about usb dongles in [this thread]("http://ubuntuforums.org/showthread.php?t=1184045") and [this one]("http://ubuntuforums.org/showthread.php?t=1193984").

Unfortunately, my experience has been with gprs and 3G modems.  I have never used a cdma modem.  So I don't know how relevant anything I say may be.  Sorry!

---

