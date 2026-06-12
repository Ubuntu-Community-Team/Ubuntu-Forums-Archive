---
title: "Configuring a USB Modem"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by captain_buckethead on 2008-10-03
Sorry for the dumb question, but does anyone know where I can find how to configure a USB 56K Modem for Ubuntu?
Cheers
Glenn.

---

### Post by azwar on 2008-10-03
**_LOOK FOR MODEM_**

1. first plug in your usb modem and wait for few seconds. then open terminal or konsole type 'lsusb'.

2. from the konsole you should see if the modem detected by ubuntu or not. it should be like this


azwar@azwar-laptop:~$ lsusb
Bus 003 Device 002: ID 5986:0100 Bison Acer OrbiCam
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 001 Device 001: ID 0000:0000
azwar@azwar-laptop:~$


3. from here you can see the result. my wireless modem detected but not active and not configured.

**_ACTIVATE THE MODEM_**

4. then check back in (kubuntu) Kinfocenter (ubuntu) devices manager under usb devices to get the full vendor id and device id. result should be like this

HUAWEI Mobile

Manufacturer: HUAWEI Technologies


Class
0
((Defined at Interface level))
Subclass
0
Protocol
0
USB Version
1.01

[B][U]Vendor ID
0x12d1
(Huawei Technologies Co., Ltd.)
Product ID
0x1003[/U][/B]
(E220 HSDPA Modem)
Revision
0.00

Speed
12 Mbit/s
Channels
0
Max. Packet Size
64

5. record the vendor id & device id. 

5a. go back to konsole and type
'sudo modprobe usbserial vendor id : 0x12d1 device id : 0x1003'

now the modem is active.

**_CONFIGURING USB MODEM_**

6. go to network manager (ubuntu) or KPPP (kubuntu) and configure the modem. the modem device should be /dev/ttyUSB0.

7. now you have to configure your account like password etc given by your ISP provider.

p/s: I'm using a wireless modem on kubuntu, the differences only how to get the full vendor id & devices id. anything should be ok and same.

I hope you can now use the usb modem. tq.

---

### Post by zenkaon on 2008-10-03
you can always try:
```
sudo wvdialconf
```

to setup your modem, then edit /etc/wvdial.conf to setup your connection, then:

```
wvdial Defaults
``` 

to connect. Bit old skool, but it's always worked. Works for 3G GSM modems, and when I had a 56k modem back in the day, it worked then.

---

### Post by captain_buckethead on 2008-10-03
> **azwar said:**
> **_LOOK FOR MODEM_**

1. first plug in your usb modem and wait for few seconds. then open terminal or konsole type 'lsusb'.

2. from the konsole you should see if the modem detected by ubuntu or not. it should be like this


azwar@azwar-laptop:~$ lsusb
Bus 003 Device 002: ID 5986:0100 Bison Acer OrbiCam
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 001 Device 001: ID 0000:0000
azwar@azwar-laptop:~$


I have managed to get this far, and the id of my USB modem is:
[PHP]BUS 001 Device 007 ID:047e2892 Agere Systems, Inc (lucent)[/PHP]

But I cant find Gnomes device manager anywhere on My system (Im running Hardy Heron 8.04.1) so im kind of stuck.

Glenn.

---

### Post by darkworld on 2008-10-04
Hi

Ive got an o2 Novatell ovation MC930D wireless Usb modem

Ive managed to get all the info and get system to recognise and communicate with it. Ive loaded user name, password, I used *99(hash) into KPPP and eventually got a HSDPA connection. Great!

Now I dont know why I cant get webpages, I open firefox and doesnt find web, so I guess Ive got connection but what do I do now to direct firefox. Sorry total n00b at this.

---

### Post by captain_buckethead on 2008-10-08
I have still been trying to get my USB modem working. Ubuntu detects the modem alright, as it gives me the following response from lsusb
```

Bus 002  Device 003 Id:047e2892 Agere Systems, Inc (lucent)

```
I have also been told to run scanmodem to try and detect the modem, but the output that I get from that is:
```

grep: 01:05.1: No such file or directory
grep: 02:00.1: No such file or directory
grep: 01:05.1: No such file or directory
grep: 02:00.1: No such file or directory

```
but what really confuses me is that I cannot find devices manager on my system to continue with the setup process that AZWAR described in an earlier post:
> 
ACTIVATE THE MODEM

4. then check back in (kubuntu) Kinfocenter (ubuntu) devices manager under usb devices to get the full vendor id and device id. result should be like this

HUAWEI Mobile

Manufacturer: HUAWEI Technologies


Class
0
((Defined at Interface level))
Subclass
0
Protocol
0
USB Version
1.01

Vendor ID
0x12d1
(Huawei Technologies Co., Ltd.)
Product ID
0x1003
(E220 HSDPA Modem)
Revision
0.00

Speed
12 Mbit/s
Channels
0
Max. Packet Size
64

5. record the vendor id & device id.

5a. go back to konsole and type
'sudo modprobe usbserial vendor id : 0x12d1 device id : 0x1003'

now the modem is active.

CONFIGURING USB MODEM

6. go to network manager (ubuntu) or KPPP (kubuntu) and configure the modem. the modem device should be /dev/ttyUSB0.

7. now you have to configure your account like password etc given by your ISP provider.

p/s: I'm using a wireless modem on kubuntu, the differences only how to get the full vendor id & devices id. anything should be ok and same.


Can anyone help?

Glenn.

---

### Post by AndrewGearhart on 2008-10-15
> **captain_buckethead said:**
> I have managed to get this far, and the id of my USB modem is:
[PHP]BUS 001 Device 007 ID:047e2892 Agere Systems, Inc (lucent)[/PHP]

But I cant find Gnomes device manager anywhere on My system (Im running Hardy Heron 8.04.1) so im kind of stuck.

Glenn.

If you're like me... you should actually find that the ID: portion of that line from lsusb has a colon in it. This actually identifies first the vendor id and, second, the product id. you should be able to throw a 0x in front of each of these to use with the lines described next... 

That's where I am now... trying to get a Hardware USB Modem from Rosewell to work. This is my first modem adventure since 1997... so I'm really rusty... but I'm trying to get this to work so that I can cobble together a hylafax server as a demonstration of what we could potentially do at work.

Where I got hung up was with the modprobe command. Seems the actual syntax would be:
sudo modprobe usbserial vendor=0x572 product=0x1321

Hope that helps somebody else have a shorter experience than the 2.5 hours I spent this evening. SO happy it works now though! On to installing and configuring Hylafax now! :-)

---

### Post by geyids on 2008-10-17
Im also having a prob with my modem in Ubuntu 8.04 check these thread [here please]("http://ubuntuforums.org/showthread.php?t=664384")

---

### Post by captain_buckethead on 2008-10-18
> **AndrewGearhart said:**
> 
Where I got hung up was with the modprobe command. Seems the actual syntax would be:
sudo modprobe usbserial vendor=0x572 product=0x1321


Thanks Andrew

I did the following:```
lsusb
Bus 001 Device 011: ID 047e:2892 Agere Systems, Inc (Lucent)

```

So I took of the 0 and the semicolon and replaced it with 0x so I would get:
Vendor 0x47e Product 0x2892
```

sudo modprobe usbserial vendor=0x47e product=0x2892

```
and nothing happened. no error message. nothing. none of the modem lights are on, so I assume that nothing happened.
Tried it again without the = and still nothing.

HELP!!!

---

