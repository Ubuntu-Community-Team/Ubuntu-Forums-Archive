---
title: "ORiNOCO make Error's"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by WeeJeWel on 2007-05-19
So I installed Ubuntu today, wondeful OS, except the Wifi compability...

So I found out I needed ORiNOCO for my SpeedTouch 120 that connects to a wifi router. Downloaded, unpacked and bang, error. 
> *** No rule to make target 'modules'. Stop.

I have Ubuntu 6.06 with 2.6.15-23-386 kernel, on a fresh install. Installed the packages linux-headers, linux-kernel-headers, make and that stuff. (Almost everything, except some drivers for other cards).

I know the SpeedTouch 120 is a hard one to install, but if someone knows what I should do I would be REALLY happy :D

Thanks in advance!
~WeeJeWel

---

### Post by tomiu on 2007-05-19
what driver do u use? from where did u download ur drivers?

---

### Post by WeeJeWel on 2007-05-19
[http://prdownloads.sourceforge.net/orinoco/orinoco-0.15.tar.gz?download](http://prdownloads.sourceforge.net/orinoco/orinoco-0.15.tar.gz?download) :-)

---

### Post by chili555 on 2007-05-19
An orinoco driver is already installed in Ubuntu. Is it not working for you? May we see:```
lsmod | grep orinoco
lsmod | grep prism2
lsmod | grep hostap
```Thanks.

---

### Post by WeeJeWel on 2007-05-19
I didn't knew it was already installed :) That's better. But what should I do now? When i type 
lsmod | grep orinoco
lsmod | grep prism2
lsmod | grep hostap
in the terminal it doesnt output anything. So what should I do now? (I love experimenting, but w/o internet it's kinda hard :P)

---

### Post by chili555 on 2007-05-19
Please open up a terminal and do:```
sudo tail -f /var/log/messages
```Leave this open so you can watch any messages the kernel issues; they will tell us if the commands we issue seem to work or seem to not.

If you search for 'orinoco' you will see the modules that are present are: orinoco_cs, orinoco, orinoco_pci, etc. There is no USB-specific module. We will watch 'messages' to see if one of these fires your SpeedTouch to life.

Plug it in. Open a new terminal and do:```
sudo modprobe orinoco
```Any signs of life at 'messages'? If not, try again with orinoco_cs. I think one of these will go.

Post back and let us know.

---

### Post by WeeJeWel on 2007-05-20
Okay, I did what you asked but it seems it doesn't do anything. My log:

> root@ubuntu:~# sudo tail -f /var/log/messages
May 20 12:22:46 ubuntu kernel: [4294882.563000] Bluetooth: L2CAP socket layer initialized
May 20 12:22:47 ubuntu kernel: [4294883.859000] Bluetooth: RFCOMM socket layer initialized
May 20 12:22:47 ubuntu kernel: [4294883.859000] Bluetooth: RFCOMM TTY layer initialized
May 20 12:22:47 ubuntu kernel: [4294883.859000] Bluetooth: RFCOMM ver 1.7
May 20 12:23:17 ubuntu kernel: [4294914.054000] usb 2-2: new low speed USB device using ohci_hcd and address 3
May 20 12:23:17 ubuntu kernel: [4294914.346000] usbcore: registered new driver hiddev
May 20 12:23:17 ubuntu kernel: [4294914.357000] input: HID 062a:0001 as /class/input/input3
May 20 12:23:17 ubuntu kernel: [4294914.358000] input: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:02.3-2
May 20 12:23:17 ubuntu kernel: [4294914.358000] usbcore: registered new driver usbhid
May 20 12:23:17 ubuntu kernel: [4294914.358000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver


When i type sudo modprobe orinoco or sudo modprobe orinoco_cs nothing changes. No output, no errors or whatever.
I hope I did something wrong cause i'm almost to give up :P

---

### Post by WeeJeWel on 2007-05-20
And in what folder should the drivers be located anyway?

---

### Post by chili555 on 2007-05-20
Rather that just tell you, I'd rather show you. As well, maybe some newbies  searching the forum will learn, too. Do:```
sudo updatedb
```This will take a few moments. Then do:```
locate orinoco_cs.ko
```The location of the driver, with it's complete path, will appear. Drivers, also known as kernel modules, are all .ko extension.

Are you certain your SpeedTouch works, or is supposed to work with orinoco? Do you have a link we can look at?

---

### Post by tturrisi on 2007-05-20
I believe you need separate  firmware  for orinoco usb.
[http://my.opera.com/subjam/blog/show.dml/473107](http://my.opera.com/subjam/blog/show.dml/473107)

---

### Post by WeeJeWel on 2007-05-25
Okay, sounds interesting, but how do I have to download files without having internet? :P I could plugin an utp cable but I don't have an utp pci card installed atm. Is there a windows way to download the files through svn? I can't seem to find a way to download only the orinoco files :) (or do i sound like a noob now? lol)

---

