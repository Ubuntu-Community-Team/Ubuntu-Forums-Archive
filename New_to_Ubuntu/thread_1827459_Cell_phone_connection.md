---
title: "Cell phone connection?"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-08-18
I've looked, but haven't found, a good source of info on how to set up my cell to work with 11.04. (Tried with 10.04 but wound up with VBox. Never do that again!)

Have a Sony Ericsson W760i and would like to be able to connect to Sony and get updates for the phone. Anybody know if there is a "program" for 11.04 that will allow the USB connection between the phone and computer that will provide this?

Thanks.

---

### Post by androssofer on 2011-08-18
> **flyfishingphil said:**
> I've looked, but haven't found, a good source of info on how to set up my cell to work with 11.04. (Tried with 10.04 but wound up with VBox. Never do that again!)

Have a Sony Ericsson W760i and would like to be able to connect to Sony and get updates for the phone. Anybody know if there is a "program" for 11.04 that will allow the USB connection between the phone and computer that will provide this?

Thanks.

do u need the program to install the updates for u? or is it a file u load to the phone and it updates from that?

if so, its prob a windows program made by sony that u need... :-(. so WINE might be the option. however!

i found this if its of any help:

> **GonZo said:**
> **More information,**

  you can use [Wammu]("http://wammu.eu/") to read contacts, SMS, calendar,... Wammu is in ubuntu repositories. Just download it with "Add and remove..."

**Configuration**

Phone conected with USB wire, "Phone" selected as option, start Wammu, select Autodetection, USB cable,... the autodetection took some minutes for me. Once detected, wammu saves configuration and it will not ask you again. In case autodetection fails here are my settings.

Name:       Sony Ericsson W760i
Device:     /dev/ttyACM1
Connection: at19200

**Tests**
Tested sms', contacts and calls retrieving. Contacts individual modification takes some seconds and must be done quitely: it can break connection (must reconnect the usb wire and restart wammu to solve it). Sending sms directly from ubuntu works too.

**Modem**
At least for me, when connecting as "Phone" mode, ubuntu detects the modem and launches the assistant, asks for your company (in my case is Yoigo which is listed in the assistant), and configures it automatically. Connection and navigation not tested (my desktop pc is in a room without coverage). 

on [this]("http://ubuntuforums.org/showthread.php?t=899801") thread.

it also mentions bluetooth connections...? tht might b worth a try.

---

### Post by flyfishingphil on 2011-08-18
I spend quite a bit of time flyfishing and go to many areas where I may travel several miles just to get a cell phone connection so I need to be able to get into the 'net and check my business email account. 

I have AT&T service and, for a low price, I can get a data plan but want to be able to connect to the 'net with the laptop via the cell. Not high knowledge level here so will that even work?

I'll check out the Wammu and see what it provides.

Thanks for the assist.

EDIT:

Looked at the Wammu reviews and it looks like it leaves a lot to be desired. Also looked at WINE but that caused another question: Which WINE is the best choice? Q4 is reviewed well, but are there other parts needed?

---

### Post by androssofer on 2011-08-18
> I have AT&T service and, for a low price, I can get a data plan but want to be able to connect to the 'net with the laptop via the cell. Not high knowledge level here so will that even work?

you can do it with an Android fone, its called "tethering" however i dont know about other types of fone.

---

### Post by flyfishingphil on 2011-12-28
Gave up and went to an Atrix 2. Found out tethering is a "plan" you have to subscribe to at AT&T to do just about anything. Still looking for a way to view all of the cell phone and will post back here if I find anything that works.

---

