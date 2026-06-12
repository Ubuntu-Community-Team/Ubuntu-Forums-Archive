---
title: "how do i get usb port name"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by cristalshield on 2009-08-05
hi im trying to use my phone sony ericsson c902 with wammu, at the setting options it ask me for the usb port name, the problem is that i dont know the name or how to get it.

does anyone knows how to get that name???

---

### Post by TMAN 1 on 2009-08-05
Perhaps try this,

[http://ubuntuforums.org/showthread.php?t=997426](http://ubuntuforums.org/showthread.php?t=997426)

---

### Post by credobyte on 2009-08-05
Terminal:
```
lsusb

```

---

### Post by cristalshield on 2009-08-05
> **credobyte said:**
> Terminal:
```
lsusb

```

i tried both methods but i still dont know witch is the usb name
[COLOR=Red]
angel@angel-laptop:~$ lsusb[/COLOR]

Bus 002 Device 002: ID 0fce:d0d4 Sony Ericsson Mobile Communications AB 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]
angel@angel-laptop:~$ tail -f /var/log/messages[/COLOR]

Aug  5 10:25:12 angel-laptop kernel: [ 8958.744214] usb 2-1: new high speed USB device using ehci_hcd and address 2
Aug  5 10:25:12 angel-laptop kernel: [ 8958.881838] usb 2-1: configuration #3 chosen from 1 choice
Aug  5 10:25:13 angel-laptop kernel: [ 8958.939305] cdc_acm 2-1:3.1: ttyACM0: USB ACM device
Aug  5 10:25:13 angel-laptop kernel: [ 8958.945430] cdc_acm 2-1:3.3: ttyACM1: USB ACM device
Aug  5 10:25:13 angel-laptop kernel: [ 8958.946014] cdc_wdm 2-1:3.7: cdc-wdm0: USB WDM device
Aug  5 10:25:13 angel-laptop kernel: [ 8958.946048] usbcore: registered new interface driver cdc_wdm
Aug  5 10:25:13 angel-laptop kernel: [ 8958.946854] usbcore: registered new interface driver cdc_acm
Aug  5 10:25:13 angel-laptop kernel: [ 8958.946861] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug  5 10:25:13 angel-laptop kernel: [ 8958.991479] usb0: register 'cdc_ether' at usb-0000:00:1d.7-1, CDC Ethernet Device, 02:80:37:10:03:00
Aug  5 10:25:13 angel-laptop kernel: [ 8958.991636] usbcore: registered new interface driver cdc_ether

---

### Post by TMAN 1 on 2009-08-05
Did you manage to get this working?

---

### Post by cristalshield on 2009-08-05
> **TMAN 1 said:**
> Did you manage to get this working?


nop i havent get it working yet, i still dont know the usb name

---

### Post by anewguy on 2009-08-05
Not familiar with the app at all, but looking at the portion of the log you provided it's hard to tell what the app is expecting - does it perhaps want the ttyACM0 and ttyACM1 devices the log shows it created?

Dave :)

EDIT:  you also may want to try cdc_acm or cdc_wdm0

---

### Post by cristalshield on 2009-08-06
thx you newguy ill try yours too and then i let you know the results

---

### Post by cristalshield on 2009-08-29
bad news guys i still cant get this wammu working, i cant find the usb port name, is this always so difficult to get. cuz i tried everything you told me to do, and the program always tell me that cant open the port i choose, i dont know anythin about this:KS

---

### Post by brawd on 2009-08-31
I've been trying to connect to my W910i for days and I seem to have succeeded. So, what I did......

Set the W910i to connect with USB, which meant I had to disconnect and then reconnect the USB cable.
Started Wammu and took the option to configure it.
Told it to automatically find phone.

Left it for half an hour and came back to it and hey presto there it was.

Previously I'd assumed that it couldn't find the phone but it turned out it was still looking.

After that Wammu pretty much took care of everything for me.

Hope this helps and I wasn't just lucky.

regards,

brawd.

---

### Post by rystraum on 2011-02-10
2 year old thread, I know. I just wanted to post here the fix if people who still search lands here.

As long as /var/log/messages show that it's created a ttyACM0 or ttyACM1, you can use
/dev/ttyACM0 or /dev/ttyACM1 in Wammu guided / manual configuration and  it can be found by the automatic search under USB cables. You always  have to look in /var/log/messages while plugging the cable because  sometimes these devices do not get created. At least, in my case, a  couple of unplug-plugging the usb cable brought it up eventually.

---

### Post by rvchari on 2011-02-10
check out with sony ericcson site if the phone has drivers. long back i had w302 and i could not use it other than external storage (something like a pen-drive)
now i am done away with that and nokia has taken its place. connecting nokia was a breeze... it was automatic !

i connect using blue-tooth. you can try that first to see if your phone is detected. then go to next step of getting a usb port connection

---

