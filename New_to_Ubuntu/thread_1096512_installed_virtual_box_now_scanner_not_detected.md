---
title: "installed virtual box now scanner not detected???"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by stinger30au on 2009-03-15
this is pretty strange

my usb hp scanner 6300c works great untill i turn on suns virtual box

then it will not detect the scanner

if i restart pc, scanner works again

untill i start virtual box

dunno why, its not like i told virtual box to do anything to the usb ports or anything

any ideas???

---

### Post by cariboo on 2009-03-15
Have you got the guest addtions installed? When you have another OS running in VirtualBox go to Details-->Install Guest Additions, and let it install, then restart the vm and see if you can access your scanner.

Edit: as a test I just tried my Webcam, as my scanner isn't supported, but it is a usb device, and it worked as it should

Jim

---

### Post by stinger30au on 2009-03-15
they are added, but gscan2pdf now says no scanners detected

if i reboot pc and run gscan2pdf my scanner runs fine

the second i start up virtualbox, gscan2pdf says no scanners detected

this only happened after i installed the virtual box update this morning

major bummer :-((

---

### Post by drs305 on 2009-03-15
If you have usb enabled in virtualbox, it may be taking ownership of the usb devices. You can release the device in virtualbox and regain its use in ubuntu. You may have to recycle the power on the scanner to accomplish this after you have deselected it in vb.

I don't have my vm available at the moment so I can't give you the exact instructions, but I believe it is accessed and unticked via the Devices, USB Devices menu.

---

### Post by stinger30au on 2009-03-15
FIXXED IT!!

i shut down the os i was unning in virtual box and then went looking at setings


there is a usb device settings page and there was a tick in the use USB device box

dunno why cos i didnt tick it

removed tick, restarted, all good 

yippie!

---

