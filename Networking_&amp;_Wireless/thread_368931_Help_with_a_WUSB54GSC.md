---
title: "Help with a WUSB54GSC"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by wafflesoup on 2007-02-23
Alright, I'm pretty new to linux and I'm trying to get my linksys WUSB54GSC network adapter to work.

I used this [How To]("http://www.ubuntuforums.org/showthread.php?t=225206") except for using different drivers and such. I'm running version 1.37 of ndiswrapper.

If I run a ndiswrapper -l it shows
```
wusb54gsc : driver installed
        device (13B1:0026) present
```

and the led on the usb stick lights up and stays lit its just very faint even though I added to the rules so It should be getting enough power.

I'm not quite sure what the problem is, but If you need any other information then just let me know. For now I'll just be ](*,)

---

### Post by javaJake on 2007-02-25
I need what's in the file /var/log/syslog after you plug in your device. This should tell me what is going on.

---

### Post by wafflesoup on 2007-02-25
thank you so much for trying to help me. Here's what it says

```
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179745.640000] ohci_hcd 0000:00:13.1: wakeup
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179746.024000] usb 3-1: new full speed USB device using ohci_hcd and address 2
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179746.220000] usb 3-1: not running at top speed; connect to a high speed hub
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179746.232000] usb 3-1: no configuration chosen from 1 choice
Feb 25 10:31:59 Wafflesoup-linux NetworkManager: <debug info>^I[1172421119.923139] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057'). 
Feb 25 10:31:59 Wafflesoup-linux NetworkManager: <debug info>^I[1172421119.985991] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057_usbraw'). 
```

---

### Post by javaJake on 2007-03-02
> **wafflesoup said:**
> thank you so much for trying to help me. Here's what it says

```
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179745.640000] ohci_hcd 0000:00:13.1: wakeup
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179746.024000] usb 3-1: new full speed USB device using ohci_hcd and address 2
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179746.220000] usb 3-1: not running at top speed; connect to a high speed hub
Feb 25 10:31:59 Wafflesoup-linux kernel: [17179746.232000] usb 3-1: no configuration chosen from 1 choice
Feb 25 10:31:59 Wafflesoup-linux NetworkManager: <debug info>^I[1172421119.923139] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057'). 
Feb 25 10:31:59 Wafflesoup-linux NetworkManager: <debug info>^I[1172421119.985991] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057_usbraw'). 
```

Gosh, sorry about the horrible horrible response times! :(

That log you have shown me says this at about the fourth line: "no configuration chosen from 1 choice". That is a clear sign that your rule you punched in is not working. Can you show me what the following commands say after plugging in your device:

```
cat /etc/udev/rules.d/99-custom.rules
lsusb
```

We'll have this problem fixed in no time. :D

---

### Post by wafflesoup on 2007-03-02
Well thank you for all you help. When I put in ```
cat /etc/udev/rules.d/99-custom.rules
``` the first time it said No such file or directory  exists, which means I must have done something wrong. I went back to FAQ and followed the directions again. now its says 
```
BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
``` 

and lsusb says
```
Bus 003 Device 002: ID 13b1:0026 Linksys 
```

Unfortunately I seemed to have messed up a few other items while tinkering with other aspects of Ubuntu, and I am considering reinstalling.

---

### Post by javaJake on 2007-03-02
> **wafflesoup said:**
> Well thank you for all you help. When I put in ```
cat /etc/udev/rules.d/99-custom.rules
``` the first time it said No such file or directory  exists, which means I must have done something wrong. I went back to FAQ and followed the directions again. now its says 
```
BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
``` 

and lsusb says
```
Bus 003 Device 002: ID 13b1:0026 Linksys 
```

Unfortunately I seemed to have messed up a few other items while tinkering with other aspects of Ubuntu, and I am considering reinstalling.

Well, if you think that just because the above file was missing means your system is messed up, then please realize that you had to manually punch in that file yourself - it isn't installed for you.

That file should work as it is. Did you install ndiswrapper and its drivers correctly?

---

### Post by kihon on 2007-03-11
Im getting a similar problem with a belkin F5d7051 dongle. 

I have setup the 99-custom.rules file so that the bConfigurationValue is set to 1 (And after inserting the USB dongle, I checked that the value is set in the correct folder. 

However the syslog is still showing the "no configuration chosen from 1 choice"  line. 

I have not yet installed ndiswrapper (as I tried this before, installing the ndiswrapper made no difference as the dongle does not appear to be powering up correctly).

Any ideas? My kernel is 2.6.17-10

thanks

---

### Post by leetcharmer on 2007-03-11
I'm receiving similar problems.  My light won't even turn on :/

---

### Post by javaJake on 2007-03-13
> **kihon said:**
> Im getting a similar problem with a belkin F5d7051 dongle. 

I have setup the 99-custom.rules file so that the bConfigurationValue is set to 1 (And after inserting the USB dongle, I checked that the value is set in the correct folder. 

However the syslog is still showing the "no configuration chosen from 1 choice"  line. 

I have not yet installed ndiswrapper (as I tried this before, installing the ndiswrapper made no difference as the dongle does not appear to be powering up correctly).

Any ideas? My kernel is 2.6.17-10

thanks

OK, what does lsusb say after you plug in your device? What's in the file /etc/udev/rules.d/99-custom.rules?

---

### Post by javaJake on 2007-03-13
> **leetcharmer said:**
> I'm receiving similar problems.  My light won't even turn on :/

OK, after you plug in your device, what does lsusb say? What's in the files /var/log/syslog and /etc/udev/rules.d/99-custom.rules?

---

### Post by kihon on 2007-03-14
Ok found the solution.

I had to put the following in the 99-custom.rules file

BUS=="usb", SYSFS{idVendor}=="050d", SYSFS{idProduct}=="7051", RUN+="/bin/sh -c 'echo 1 > /sys/bus/usb/devices/%k/bConfigurationValue'"

using 
BUS=="usb", SYSFS{idProduct}=="7051", SYSFS{idVendor}=="050d", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

did not work for me. but as soon as I used the first one, everything worked.

---

### Post by javaJake on 2007-03-14
> **kihon said:**
> Ok found the solution.

I had to put the following in the 99-custom.rules file

BUS=="usb", SYSFS{idVendor}=="050d", SYSFS{idProduct}=="7051", RUN+="/bin/sh -c 'echo 1 > /sys/bus/usb/devices/%k/bConfigurationValue'"

using 
BUS=="usb", SYSFS{idProduct}=="7051", SYSFS{idVendor}=="050d", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

did not work for me. but as soon as I used the first one, everything worked.

That's what I was going to check in my posts. Congrats on figuring it out! :D

---

### Post by leetcharmer on 2007-03-26
> **kihon said:**
> Ok found the solution.

I had to put the following in the 99-custom.rules file

BUS=="usb", SYSFS{idVendor}=="050d", SYSFS{idProduct}=="7051", RUN+="/bin/sh -c 'echo 1 > /sys/bus/usb/devices/%k/bConfigurationValue'"

using 
BUS=="usb", SYSFS{idProduct}=="7051", SYSFS{idVendor}=="050d", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

did not work for me. but as soon as I used the first one, everything worked.

why would that work???

my lsusb says it's Linksys 13b1:0026

So why would you be using 050d and 7051?

---

### Post by javaJake on 2007-03-26
> **leetcharmer said:**
> why would that work???

my lsusb says it's Linksys 13b1:0026

So why would you be using 050d and 7051?

Because he has a different device. Each device has its own unique product ID, and each company has their own unique vendor ID. I believe this is how USB devices are recognized, but I'm not sure.

---

### Post by leetcharmer on 2007-03-26
Is he not talking about the WUSB54GSC??

---

### Post by javaJake on 2007-03-26
> **leetcharmer said:**
> Is he not talking about the WUSB54GSC??

Oh, duh, thanks for that correction, I forgot which thread I was in. *chuckle* :D

---

### Post by leetcharmer on 2007-03-26
So why would you be using 050d and 7051 when device is: 13b1:0026?

---

### Post by leetcharmer on 2007-03-26
Would this thing work easier in Dapper than Edgy/Feisty?

---

### Post by Shmook on 2007-03-27
I'm using the same computer for Windows (with connectivity) and Ubuntu (without), and am having similar trouble with my WUSB54GSC.

My technique for getting the windows drivers was downloading them in windows, burning them to a cd-r, then copying them when I'm in Ubuntu -- could this be the source of my troubles?

---

### Post by javaJake on 2007-03-28
> **leetcharmer said:**
> Would this thing work easier in Dapper than Edgy/Feisty?

Yes, because Dapper's older kernel does not have the power protection "feature".

---

### Post by javaJake on 2007-03-28
> **Shmook said:**
> I'm using the same computer for Windows (with connectivity) and Ubuntu (without), and am having similar trouble with my WUSB54GSC.

My technique for getting the windows drivers was downloading them in windows, burning them to a cd-r, then copying them when I'm in Ubuntu -- could this be the source of my troubles?

Could be, but I'd need to see "ndiswrapper -l", "lsusb", and the file /var/log/syslog to tell. Be sure to only collect the information after plugging in the device and letting it register (2-3 seconds).

---

### Post by leetcharmer on 2007-04-01
Alright, to make things a bit easier ... I'm tryin' to get this workin' with Dapper.  I got it finding networks when I do 'iwlist wlan0 scan,' but it won't connect to any of them.

I'm posting my dmesg and syslog files.

---

### Post by javaJake on 2007-04-01
> **leetcharmer said:**
> Alright, to make things a bit easier ... I'm tryin' to get this workin' with Dapper.  I got it finding networks when I do 'iwlist wlan0 scan,' but it won't connect to any of them.

I'm posting my dmesg and syslog files.

Hmmm, very strange. According to your files everything went fine. Are the networks close by? A lot of times you can see the networks but can't connect to them (just because the router reaches farther then your card). Also, can you give me your /etc/network/interfaces file?

Besides that I'm plain out of ideas. Google around for other users using the WUSB54GSC, I suppose. Post on the ndiswrapper mailing list, too. In general, look around for help. I can't help anymore. Sorry. :(

I went to the NDisWrapper Wiki to get information about how others got their device to work, and they linked to my HOWTO. What a big help that was. ;)

---

### Post by leetcharmer on 2007-04-02
I'm making these posts from connecting online with the WUSB54GSC on the Windows side, so -- it should be able to connect after finding them on the Ubuntu side.  The only thing commented in the network/interfaces file is all references to eth1.

---

### Post by TheBenny on 2007-10-15
I was having this same problem with my WUSB54gsc, everything checked out fine per the guide, and the helpful posts in this thread, was still getting the errors everybody else was getting ( ifconfig wlan0 up erroring out) Then i rebooted and unplugged the ethernet cable... ifconfig wlan0 up worked, and so did iwlist scanning, i can see my network .  so if you have this issue, try unplugging the hard line :P

---

### Post by javaJake on 2007-10-15
Someone also recently copied (grrr) my HOWTO and made their own for the WUSB54GSC. Despite the means of creation, it's still useful for WUSB54GSC owners, and reportedly works. See the HOWTO here:

[http://ubuntuforums.org/showthread.php?t=459617](http://ubuntuforums.org/showthread.php?t=459617)

---

### Post by dnpate on 2008-05-27
I get the error message of "No such file" for usb8023.sys and rndismp.sys.  Where can i find these?

---

### Post by javaJake on 2008-06-29
> **dnpate said:**
> I get the error message of "No such file" for usb8023.sys and rndismp.sys.  Where can i find these?

In a Windows XP installation. I also included them in an attachment for a WUSB54GS HOWTO I made. You can go ahead and grab the files from there, but don't follow the instructions. Instead, use the instructions I linked to above.

**Edit:** Duh, gotta tell you where the HOWTO is. ;)
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

---

