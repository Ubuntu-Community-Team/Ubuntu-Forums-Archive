---
title: "WUSB11 cannot detect"
date: 2005-06-01
forum: Networking &amp; Wireless
---

### Post by David C on 2005-06-01
I've just installed the latest atmel drivers at [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)

But I am unable to see my wireless network usb adapter under System > Admin > Networking.

The Power LED is lighted up on my adapter so that means its correctly plugged into the USB port and is correctly drawing power from my PSU, but why is it not detecting?

I very much appreciate any help I can get. This is my first switch from Windows to Linux.

---

### Post by betrayed on 2005-06-01
Did you also install the firmware for the card?  Also can you post the results of dmesg?

---

### Post by David C on 2005-06-01
I haven't installed anything else other than the atmel drivers. Where\What should I be looking for, to get the firmware?

I'll post the dmesg asap. I need to find a spare USB thumbdrive to copy the output onto my current PC as my Ubuntu setup has no direct internet connection at the moment.

---

### Post by David C on 2005-06-01
Hmm, I've inserted my USB thumbdrive on my Ubuntu system, and hotplug doesn't seem to work. I don't see the USB drive on my "Computer".

---

### Post by betrayed on 2005-06-01
[http://ftp.ankara.edu.tr/ubuntu/pool/multiverse/a/atmel-firmware/atmel-firmware_1.0-0ubuntu1_i386.deb](http://ftp.ankara.edu.tr/ubuntu/pool/multiverse/a/atmel-firmware/atmel-firmware_1.0-0ubuntu1_i386.deb)

this is the firmware.  I was using a atmel card in my machine as well but I could dual boot windows to get the files I need. For now if the usb thumbdrive isn't working you could use a cd rw to transfer files.  I have gone that approach before as well.

The firmware is needed because the drivers do not include it and the drivers load the firmware from the machine onto the card

---

### Post by David C on 2005-06-01
Thanks, how do I install the firmware?

---

### Post by betrayed on 2005-06-01
sudo dpkg -i the file
then you should be able to unplug the device and plug it back in.  You should see some messages in your dmesg.   About loading the drivers and the firmware being loaded.  if all goes well it will set the device as wlan0

---

### Post by David C on 2005-06-01
[QUOTE=betrayed]sudo dpkg -i the file
then you should be able to unplug the device and plug it back in.  You should see some messages in your dmesg.   About loading the drivers and the firmware being loaded.  if all goes well it will set the device as wlan0[/QUOTE]

I had an unexpected version number at end of file, when trying to do a

```
sudo dpkg -i <filename>
```

---

### Post by betrayed on 2005-06-01
```
betrayed@whitey:~/Desktop$ sudo dpkg -i atmel-firmware_1.0-0ubuntu1_i386.deb
``` 

works fine for me you could also download it from [http://thekelleys.org.uk/atmel/](http://thekelleys.org.uk/atmel/) and just grab the tar and untar and run the install script.  If I remember right that is how I did it the first time.

---

### Post by David C on 2005-06-01
[QUOTE=betrayed]```
betrayed@whitey:~/Desktop$ sudo dpkg -i atmel-firmware_1.0-0ubuntu1_i386.deb
``` 

works fine for me you could also download it from [http://thekelleys.org.uk/atmel/](http://thekelleys.org.uk/atmel/) and just grab the tar and untar and run the install script.  If I remember right that is how I did it the first time.[/QUOTE]
 Yeah it works now, after I reburned it onto my cd-r. 

If you noticed, I deleted my post hoping that you wouldn't catch my embarassing mistake. I guess I was too late :D

The .deb installed itself with no errors. Unfortunately, I don't see anything new on my dmesg and in System -> Admin -> Network, my wireless adapter is not listed.

---

### Post by betrayed on 2005-06-01
what does lsusb return
and after you did make install on the cvs drivers did you 
depmod -a
or reboot?

After each step I had to unplug and replug in the device to get it to reset the firmware

---

### Post by betrayed on 2005-06-01
Until I get a response on the last one the only other thing I can offer is I have two wusb11 cards.  One is on the atmel chipset wusb11 v2.6 and the other is on the prism2 chipset wusb11 v2.5

---

### Post by David C on 2005-06-01
[QUOTE=betrayed]what does lsusb return
and after you did make install on the cvs drivers did you 
depmod -a
or reboot?

After each step I had to unplug and replug in the device to get it to reset the firmware[/QUOTE]
 lsusb returns nadda.

Yes to, depmod -a, reboot and unplug & replug.

---

### Post by betrayed on 2005-06-02
hmm guess my next question is are you sure that the firmware installed. and what version of wusb11 do you have

---

### Post by David C on 2005-06-02
[QUOTE=betrayed]hmm guess my next question is are you sure that the firmware installed. and what version of wusb11 do you have[/QUOTE]

WUSB11 v2.6

I'm pretty sure my firmware is installed, but how do I go about checking it to set my mind at ease?

---

### Post by betrayed on 2005-06-02
I am thinking on the firmware thing but I do remember one thing that I do everytime with that card. 
```

sudo gedit /etc/rcS.d/S40hotplug 
then look for these lines
#echo /sbin/hotplug > /proc/sys/kernel/hotplug
#echo /bin/true > /proc/sys/kernel/hotplug

```

remove the # from both and restart.  I had some issues with the drivers being able to load the firmware and that fixed it

So are you seeing any notice that the machine even sees the device?  hotplug sees a new highspeed device or is nothing happening when you plug it in?

For the firmware you can check in synaptic just search for atmel.  The drivers I can't think of a way to make sure they installed

---

### Post by David C on 2005-06-02
[QUOTE=betrayed]I am thinking on the firmware thing but I do remember one thing that I do everytime with that card. 
```

sudo gedit /etc/rcS.d/S40hotplug 
then look for these lines
#echo /sbin/hotplug > /proc/sys/kernel/hotplug
#echo /bin/true > /proc/sys/kernel/hotplug

```

remove the # from both and restart.  I had some issues with the drivers being able to load the firmware and that fixed it

So are you seeing any notice that the machine even sees the device?  hotplug sees a new highspeed device or is nothing happening when you plug it in?

For the firmware you can check in synaptic just search for atmel.  The drivers I can't think of a way to make sure they installed[/QUOTE]


Did the edit and rebooted.

When I replug the adapter, hotplug doesn't say anything. Nothing hapens.

Did a "whereis" and didn't find nothing.

Something is wrong somewhere. To be sure, I re-installed the firmware. No errors, output says that everything is installed correctly.

Did a "whereis" again. Nothing.

---

### Post by betrayed on 2005-06-02
hmm i guess the biggest concern is that the system doesn't see the device connect at all to the system.  Even when I didn't have a driver installed it still showed an unknown device connecting.  When you built the cvs berlios drivers I am assuming you had the kernel headers that match your current kernel and you have not done a kernel upgrade since then.

---

### Post by betrayed on 2005-06-02
could you post the result of 
```
dmesg | grep usb
``` 
after you have plugged in the device.  We may have to modprobe by hand.

---

### Post by David C on 2005-06-02
```


usbcore : registered new driver usbfs
usbcore : registered new driver hub
home/zeus/at76c503a/at76_usbfuc : USB Device firmware upgrade (DFU) v0.12beta23-static loading
usbcore : registered new driver at76c503-rdmd


```

I had to manually typed that in here, as I switch from my KVM.

---

### Post by betrayed on 2005-06-02
well it is seeing it.  how about the results of
iwconfig

---

### Post by David C on 2005-06-02
[QUOTE=betrayed]well it is seeing it.  how about the results of
iwconfig[/QUOTE]

iwconfig gives me nothing (as in no devices detected).

---

### Post by betrayed on 2005-06-02
modprobe -r at76c503a-rfmd
modprobe -v at76c503a-rfmd

and if that does nothing try

modprobe -r at76c503-rfmd-acc
modprobe -v at76c503-rfmd-acc
hopefully that will find it and you will have a wlan0
you could run tail -f /var/log/syslog and watch what is going on as you try

---

### Post by David C on 2005-06-02
[QUOTE=betrayed]modprobe -r at76c503a-rfmd
modprobe -v at76c503a-rfmd

and if that does nothing try

modprobe -r at76c503-rfmd-acc
modprobe -v at76c503-rfmd-acc
hopefully that will find it and you will have a wlan0
you could run tail -f /var/log/syslog and watch what is going on as you try[/QUOTE]
 I redid the modprobe -r at76..-rfmd & modeprobe -v at76..-rfmd

syslog has activity about loading drivers for atmel wireless.

but an iwconfig doesn't show me anything abt wlan0.

whereis at76c503a also shows nothing.

---

### Post by betrayed on 2005-06-02
in the syslog is there a bit aabout loading firmware
It should say something like loading firmware, got it.  If it doesn't say got it it should say something about downloading the firmware from various sites.

---

### Post by David C on 2005-06-02
[QUOTE=betrayed]in the syslog is there a bit aabout loading firmware
It should say something like loading firmware, got it.  If it doesn't say got it it should say something about downloading the firmware from various sites.[/QUOTE]
 There are 4 lines that popup. They are all saying the Wireless LAN Driver loaded, something about atmel v0.1-23-static loading.

Also, my USB Thumbdrive is not working when I put it into the system. Hotplug doesn't detect anything also.

---

### Post by betrayed on 2005-06-02
hmm ok, well it sounds like it is load try
```
sudo ifconfig wlan0 up
then 
ifconfig
``` 
See if it shows wlan0 if so you should be able to configure it with iwconfig

As for the thumb drive I don't have one as of yet so I have no idea where to start

---

### Post by David C on 2005-06-02
[QUOTE=betrayed]hmm ok, well it sounds like it is load try
```
sudo ifconfig wlan0 up
then 
ifconfig
``` 
See if it shows wlan0 if so you should be able to configure it with iwconfig

As for the thumb drive I don't have one as of yet so I have no idea where to start[/QUOTE]
 ```
Error while getting interface device up:  No such device.
```

---

### Post by betrayed on 2005-06-03
[QUOTE=David C]```
Error while getting interface device up:  No such device.
```[/QUOTE]
 I have not abandoned this but am gone until sunday check back then

---

### Post by David C on 2005-06-04
[QUOTE=betrayed]I have not abandoned this but am gone until sunday check back then[/QUOTE]
 thanks!

I really feel like giving up, this is giving me a ton of headache.

---

