---
title: "How to enable USBSerial to allow Palm pilot to Sync"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by VTT Alps on 2009-03-28
I'm trying to get my Palm TX to sync with Unbuntu 8.04.   I'm using Gnome-Pilot.    I have selected USB as the connection type.   When Gnome-Pilot tells me to press the Sync button,  I get the following error

Failed to connect using device "Cradle", on port /dev/pilot.  Check your configuration, as you requested old-style usbserial ttyUSB syncing, but do not have the usbserial  "visor" kernel module loaded.  You may need to select a sub device.

Question:  Where can I get the visor kernel module,  and how do I load it.

If anyone has the answer, please send it my way.  

Thank you very much.  

:confused:

---

### Post by gandaran on 2009-03-28
a simple google search turns up a lot of information!
[http://ubuntuforums.org/showthread.php?t=877238](http://ubuntuforums.org/showthread.php?t=877238)
[http://kaybyrd.com/?p=58](http://kaybyrd.com/?p=58)
[https://help.ubuntu.com/community/PortableDevices/PalmOS](https://help.ubuntu.com/community/PortableDevices/PalmOS)

---

### Post by VTT Alps on 2009-03-28
Bad news:  I tried the advise in the last link you suggested.   Now my computer won't boot.  Here is what I modified:

gksudo gedit /etc/udev/rules.d/10-custom.rules

Then added the following lines

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

Next

gksudo gedit /etc/modules

Then added visor to the last line of the file

I get a boot time Error  Set: 138 Can't access TTY: Job control turned off.

Unless This can be fixed, I will need to relaod unbuntu and I will loose a few weeks worth of data and pictures.  Not to mention a LOT of time.

Any ideas.

---

### Post by sgosnell on 2009-03-28
Your original error was in trying to use a serial connection when you only have a USB port on your computer, most likely.  You need to use USB, not serial.  I'm not sure exactly what the choices are in gnome-pilot, because I don't use it.  I prefer JPilot, which works well for me.  If you kept a copy of the files you edited, it would be easy enough to restore them.  Boot from a live CD or a USB device, and copy them back.  If you didn't make a copy, then you need to try to edit the files to put them back into the same state they were in originally, then try to connect the Palm using a USB connection.

---

### Post by gandaran on 2009-03-28
try booting the live cd, use sudo -i nautilus then delete every line you have added, reboot maybe this will work.

---

### Post by VTT Alps on 2009-03-28
My system is working again.   Using Sudo Nautilus worked great to change the files back.  

Thank you VERY VERY MUCH !!!!  For that good advise. 

Note: I still can't hook my Palm pilot up.    I am using a USB connection,  and I selected USB in Gnome-Pilot.   At this point,  I'm have no idea how to make it work.  I will review the links you posted and see if I did something wrong.

Cheers.

---

### Post by sgosnell on 2009-03-28
Try JPilot, with a wifi connection.  I never use a cable, preferring the wifi connection by far.  It's quick and easy.  File, Preferences, Settings, enter net:any.

---

### Post by VTT Alps on 2009-03-28
Looks like it's Syncing now.  I must have typed something wrong the first time.   Thanks to everyone for the help.

Cheers.

---

### Post by fwc67 on 2009-03-30
thanks, this was helpful to me too.  I learned that I can use j-pilot also, instead of Gnome-pilot, but I was wondering how do you access other applications on the palm like pocket tunes

---

### Post by sgosnell on 2009-03-30
You should never try to sync music to a Palm.  It's too slow and buggy.  To transfer music to your SD card, use a card reader.  That's much faster and more reliable, and you can get one for $10 or less.

---

### Post by Tootler on 2009-04-13
> **sgosnell said:**
> Your original error was in trying to use a serial connection when you only have a USB port on your computer, most likely.  You need to use USB, not serial...

I don't think so. Gnome-pilot offers USB as an option which I checked but got the same error message. I tried both the subsequent options of I have synced before and I have not synced before but with the same result.

This thread was one of quite a number that came up when I searched, many of which had links to other threads. It seems there are problems with syncing Palm OS devices to Ubuntu and there are many workarounds posted.

although JPilot seems to come off best it seems more a case of least worst rather than best and my conclusion which I also saw on another thread is that syncing to Palm OS devices with Linux has not been properly sorted out. 

For the time being I will carry on using Windows to sync my Palm until it becomes clear that syncing is reliable and will work without having to resort to various workarounds to get it working.

Geoff

---

### Post by sgosnell on 2009-04-13
By all means, do what works for you.  IME, though, syncing with Linux is more reliable than syncing with Windows, unless you have third-party conduits written for Windows only.  My Lifedrive syncs to JPilot flawlessly, every time, unless I forget to change the IP address on the Palm, when my Linux box gets a new IP from the router.  That's not a Linux problem, though, and simply changing to the proper IP fixes it immediately.  I haven't tried a USB sync in a long time, because wifi is so much easier.

---

### Post by shakma on 2009-04-21
> **Tootler said:**
> I don't think so. Gnome-pilot offers USB as an option which I checked but got the same error message. I tried both the subsequent options of I have synced before and I have not synced before but with the same result.

Geoff

HEY, HEY!!!

I've been trying to get this to work for two years now, and I just figured it out tonight!  

I'm syncing a Palm TX with the standard usb sync cable, and here are the settings that _work_:

Name: Cradle (or whatever you want to call it)
Type: USB (*important*)
Timeout: 2 (or however long you want it to try - don't worry, it'll work!)
**Device:** *usb:* <-- this is the key!  Don't leave it as "/dev/pilot" or you'll be in the same boat full of errors as everyone else
Speed: 57600 (I just left this - doesn't seem to make a difference for usb anyway...)
>Forward

At this point, I left it on "Yes, I've used sync software with this PDA before."  I had been using PalmDesktop (Windows) for years.  If this is not the case and yours is brand new, try "No" I guess...
>Forward

Now, when it asks you to, hit the ol' HotSync button on the usb cord and... VOILA:guitar:
"Successfully retrieved Owner Name and ID from PDA." should be your reward!
>Forward

Give your device a name and location for Ubuntu to reference (defaults are fine for me).
>Forward

**Success**
"Congratulations, gnome-pilot is configured!"
God, that was sweet to read.

*But wait!  There's more!*
Now, to actually use this, you've got to set up the "Conduits" tab and tell it *what to do* when you sync in the future.  NOTE: Everything is Disabled when you get to this point, so if you don't enable any conduits for syncing, you won't be accomplishing much.  By default, Evolution is the "PalmDesktop"-like program you'll be syncing with.  There is plenty of help out there for setting up Evolution for yourself.  I will not go into that here, but I recommend setting up a personal Evolution account for yourself before you press HotSync again...

Alright, it's late and I need to teach in the morning.  Hopefully this helps someone.  I know I got tired of searching for this over and over and only finding "Try Google, jerk..." or "It just worked for me!  w00t!"

Hopefully this helps someone.

Peace.
shakma

---

### Post by aiko.uda on 2009-04-21
Thank you! It was a great help!!!

---

### Post by LargePiece on 2009-04-21
Those settings didn't work for me. *sighs*. I've been browsing the forums on and off for the past few months hoping I'd find something that would work for my poor old Lifedrive. Visor restarts my lifedrive, I really thought this usb: option might work. Doh!

With the above settings my Lifedrive just times out.

---

### Post by knitmom on 2009-05-31
> **shakma said:**
> HEY, HEY!!!

I've been trying to get this to work for two years now, and I just figured it out tonight!  

I'm syncing a Palm TX with the standard usb sync cable, and here are the settings that _work_:

Name: Cradle (or whatever you want to call it)
Type: USB (*important*)
Timeout: 2 (or however long you want it to try - don't worry, it'll work!)
**Device:** *usb:* <-- this is the key!  Don't leave it as "/dev/pilot" or you'll be in the same boat full of errors as everyone else
Speed: 57600 (I just left this - doesn't seem to make a difference for usb anyway...)
>Forward
......
Hopefully this helps someone.

Peace.
shakma

Thanks, that helped me a whole bunch!!!!  I finally got kpilot to read my palm TX!!!!!  It's backing it up now. :D

knitmom!

---

### Post by LargePiece on 2009-11-23
If anyone's having trouble with visor restarting/crashing your palm device, there's a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/421673](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/421673)

I ended up removing the modemmanager package and after a year of plugging away at this annoying problem, I can finally sync my lifedrive! Ace.

---

