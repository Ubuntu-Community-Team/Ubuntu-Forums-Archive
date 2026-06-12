---
title: "panasonic voice recorder rr-us430"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by eskararriba on 2008-12-07
hello everybody, 

I'm checking if my usb-devices work on linux, and the only one that's making trouble is my voice recorder, panasonic rr-us430. 
when I connect it, absolutely nothing happens. 
anyone got any idea of what I might do, or try, to get it work?

(in windows it s not listed as a folder or disc either - it only runs in an own program called voice recording)

thanks a lot everyone

---

### Post by halitech on 2008-12-07
without the device connected, open a terminal and type ```
lsusb
```
then plug it in, wait 45 seconds and run the same command and then post the output here

---

### Post by eskararriba on 2008-12-07
hm... surprisingly it DOES recognise the device, in some way - only I don't know what to do with this... there we go:

boerries@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

boerries@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04da:2390 Panasonic (Matsushita) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
boerries@ubuntu:~$ 

thanks for your help!

---

### Post by halitech on 2008-12-08
did a lot of searching and from what I can find, this device doesn't work under linux :(

try in the terminal typing```
sudo fdisk -l
``` with it connected and disconnected and see if there is any change

---

### Post by eskararriba on 2008-12-08
no change at all. hmpf. seems like I m condemned to keep windows until I get another recorder...

anyway, halitech: thanks a lot for your help.

---

### Post by halitech on 2008-12-09
bummer, wish we had been able to get it working

---

### Post by frozenjim on 2010-07-12
I don't give up so easily.  My device is the Panasonic RR-US360 and it's a fine little USB digital voice recorder.  Of course Panasonic - like Sony and others - have to play their childish games and force you to use their "MAGIC" software in order to the most basic of things.

Anyhow...  it works just great for me if I don't bother with USB.  Most of these devices have a "MIC" and "EARPHONE" plugin.  So just get a 1/4" to 1/4" cable (from any electronics store on Earth) and plug device's "EARPHONE" jack into your computers "MIC" jack.  

From there it's as simple as using the built-in sound software of your choice.  My copy of Ubuntu came with "Sound Recorder" which worked just great (once I remembered to unmute my mic-in channel).

So, don't buy Windows, buy a $2.00 1/4" cable instead.

---

