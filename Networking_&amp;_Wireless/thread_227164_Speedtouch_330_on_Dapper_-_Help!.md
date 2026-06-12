---
title: "Speedtouch 330 on Dapper - Help!"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by AdamSebWolf on 2006-08-01
Hi,

I'm having problems installing my Speedtouch on Dapper Drake. I've tried the SpeedtouchConf script, except there's no gcc as standard and without the internet I can't get gcc, so the script fails. I just tried the guide from here [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html") and that doesn't currently work. I've gone back over the whole thing and double-checked for any faults, but I can't find any. While booting, if I hit Alt+Ctrl+F1 for the text console, there are 4 error messages given reading something like:
FirmwareHelper[###] error loading speedtouch with driver speedtch

Running the dial script from the above guide results in the speedtouch not dialling up.

Please can somebody recommend a surefire and proven method of getting the speedtouch working on Dapper without problems?

nb. Given that the Speedtouch 330 is the probably the most popular UK broadband modem due to BT's mass distribution of them to broadband users, it'd be great to solve the speedtouch problems once and for all so that all Ubuntu users would have another thing less to worry about :KS I'd be more than willing (once this is sorted) to work with someone to devise a one-stop script or application to get Speedtouch working that could be shipped with Ubuntu...

---

### Post by Jagot on 2006-08-01
I'm afraid I don't have the same modem so I have no experience of this, but you may want to have a look at these entries in the wiki:

[https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo](https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo)
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

---

### Post by AdamSebWolf on 2006-08-02
Hi,
I've tried both the approaches listed there, and when I run the connecting "dial" script, it says...

```
connect(0.38): No such device
```

As a reasonable newbie to linux, I don't understand how to rectify this problem by myself. As I've already tried several alternative methods to no avail, could it be incorrect or bad firmware? 

A description of how linux uses things like init.d and ppp and how it uses devices on boot could also really help me understand what's going on. At the moment this is very much like poking in the dark...

---

### Post by AdamSebWolf on 2006-08-02
I've just tried using new firmware in case the original was corrupted, and I've still no success...

Somebody please help!

---

### Post by Karlos on 2006-08-03
put your ubuntu cd in your cd drive
a window should pop up saying that you can install off the cd
say yes
search for 'build-essential'
it is a meta package containing tools needed to build modules, programs, etc
when it is installed run the speedtouchconf script again
this time it will work
regards
karlos

---

### Post by AdamSebWolf on 2006-08-03
Thanks dude, I'll give it a try, I hope it works!

Any ideas why the current attempts have failed totally?

---

### Post by Karlos on 2006-08-03
it's because you haven't got gcc installed, which is contained in the build-essential meta package.
if you still cant get it going after that then make sure you have the right firmware.

---

### Post by azmansell on 2006-08-13
> **AdamSebWolf said:**
> Thanks dude, I'll give it a try, I hope it works!

Any ideas why the current attempts have failed totally?

hiya adam did this work in the end? if so please post the steps you took.

i used to have mine working on breezy, i ordered the dapper disks and gave my copy of breezy to a friend. when i finallly got round to installing dapper i found it wouldnt work and my friend lost the disk so im back on (hic) windows for now!!  (cue admin telling me not to swear on the forum!)

cheers bud

---

### Post by ncarter on 2006-08-13
It looks the newer kernel in Dapper looks for the firmware files in a different location.  If you get errors like this after upgrade:
 grep speedt.*stage /var/log/syslog
Aug 12 21:34:49 localhost kernel: [17179690.180000] speedtch 1-2:1.0: no stage 1 firmware found!
Aug 12 21:39:55 localhost kernel: [17179589.348000] speedtch 1-2:1.0: no stage 1 firmware found!

You will probably be getting a helpful message from firmware_helper
 grep firmware_helper /var/log/syslog
Aug 12 21:34:49 localhost firmware_helper[4939]: main: error loading '/lib/firmware/speedtch-1.bin.4' for device '/class/firmware/1-2:1.0' with driver 'speedtch'

So you need to copy your speedtouch firmware from
/lib/hotplug/firmware to /lib/firmware

sudo cp /lib/hotplug/firmware/speedtch* /lib/firmware

and reboot.

Nick

---

