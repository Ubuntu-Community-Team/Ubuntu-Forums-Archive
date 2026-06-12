---
title: "mp3 problem"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by ltcnr2g on 2009-03-25
I just had my computer wiped clean of windows and had linux installed. Purchased a new mp3 player and computer does not find new hardware when i plugged into the usb port. The player does require windows, but i wonder if linux has a program to support the player?

---

### Post by gorucan on 2009-03-25
Give more details about your mp3 player?
Which distro are you using?

---

### Post by Anthon on 2009-03-25
The brand and model of the player would help a bit. I have e.g. a Sony that uses the MTP protocol (Over USB) and that is not seen as a USB drive and needs special software/plugins

---

### Post by KCG102282 on 2009-03-25
The name of the player would help, but in the mean time if you have the option of MSC or MTP choose MSC.

---

### Post by Temposs on 2009-03-25
hello

Generally, when you have Ubuntu/Linux and you want to buy new hardware like an MP3 player or anything else, it's best to first research if the mp3 player you'd like to buy will work well with Ubuntu. Then you will not end up with a new piece of hardware that doesn't work easily.

Often, it is possible to make a piece of hardware work that doesn't work initially, through workarounds that people find through trial and error. But first, you need to tell us what model mp3 player you have. Also, you need to tell us exactly what does or does not happen when you plug in the mp3 player.

Lastly, open a terminal through Applications->Accessories->Terminal, and type:

```
lsusb
```

and then copy and paste the output here so we can see it.

---

### Post by ltcnr2g on 2009-03-25
I have a Samsung YP-S3J

---

### Post by fela on 2009-03-25
> **ltcnr2g said:**
> I have a Samsung YP-S3J

Is there an MTP mode on the player that you can set in the player user interface? If there is, set it. Then in Rhythmbox enable the MTP plugin (edit > plugins) and see if it comes up.

---

### Post by ltcnr2g on 2009-03-25
lisa@lisa-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 012: ID 04e8:5091 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000

---

### Post by decoherence on 2009-03-25
These folks claim to have an "S3" working... not sure if it's the same as yours.
[http://forum.ubuntu-fr.org/viewtopic.php?id=295400]("http://forum.ubuntu-fr.org/viewtopic.php?id=295400")

It's in French so run it through Google Translator if you need to. From the looks of it, you just need to make sure MTP is there and edit a udev rule...

---

### Post by fela on 2009-03-25
Well my sister bought a mp3 player a couple months ago. It was a job getting it to work with Windows or MacOSX so I thought hey why not try Linux, and it turned out that all I needed to do was enable MTP on it. It still won't work with Windoz or Mac though. I wonder why...:confused:

---

### Post by ltcnr2g on 2009-03-25
what is MTP and where do i find it on the computer?

---

### Post by fela on 2009-03-25
> **ltcnr2g said:**
> what is MTP and where do i find it on the computer?

Well if you use Rhythmbox then you can find it in Edit > Plugins. There will be a plugin called something like 'mtp media device'. If not, try looking in synaptic for 'mtp'. You might need to install libmtp or something similar.

---

### Post by ltcnr2g on 2009-03-25
everything is enabled except for DLNA/UPnP sharing and support

---

### Post by ltcnr2g on 2009-03-25
I found this in Rhythmbox and clicked on edit and then plug ins, where i found that everything was enabled

---

### Post by ltcnr2g on 2009-03-25
where is synaptic?

---

### Post by decoherence on 2009-03-25
> **ltcnr2g said:**
> where is synaptic?

Follow the menus...

System > Administration > Synaptic Package Manager

---

### Post by ltcnr2g on 2009-03-25
i found libmtp.7 and the box was green, I assume it already exists on the system.

---

### Post by fela on 2009-03-25
> **ltcnr2g said:**
> i found libmtp.7 and the box was green, I assume it already exists on the system.

Type libmtp in the search box in Synaptic. If there's a libmtp8 available, install it. That's what comes up on mine.

---

### Post by fela on 2009-03-25
Try installing mtpfs and mtp-tools aswell.

---

### Post by ltcnr2g on 2009-03-25
found them both and installed them

---

### Post by ltcnr2g on 2009-03-25
do you have any other suggestions. Would be greatly appreciated

---

### Post by fela on 2009-03-25
> **ltcnr2g said:**
> found them both and installed them

Great! Is the player working now?

---

### Post by halitech on 2009-03-25
> **ltcnr2g said:**
> what is MTP and where do i find it on the computer?

MTP - Media Transfer Protocal

[http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol)

Have you actually checked the MP3 player to make sure it has MTP enabled?

what is the output of ```
sudo mount
``` and ```
sudo fdisk -l
``` from the terminal with the MP3 player plugged in?

---

### Post by llamabr on 2009-03-25
All good advice.  Sometimes, with the actual mp3 player, you have to look in the menus and change the format.  I don't know this player, but try looking for a 'settings menu' and see what format is set.

---

### Post by ltcnr2g on 2009-03-25
it asks me if i want to format whole memory.

---

### Post by ltcnr2g on 2009-03-25
the computer is not recognizing the mp3 player when it is plugged into the usb port

---

### Post by ltcnr2g on 2009-03-25
I think this is too much of a headache. I will just take it to a friends computer that has windows and put music onto it.

---

### Post by fela on 2009-03-25
> **ltcnr2g said:**
> it asks me if i want to format whole memory.

Yes, you have to select yes if you want to convert it to MTP. Otherwise the computer probably won't recognize it.

WARNING: FORMATTING WHOLE MEMORY WILL DELETE ALL DATA ON DEVICE in case you didn't know that.

PS. Don't give up on Linux just because it won't work at first for you!

---

### Post by halitech on 2009-03-25
> **ltcnr2g said:**
> lisa@lisa-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 012: ID 04e8:5091 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000

> **ltcnr2g said:**
> the computer is not recognizing the mp3 player when it is plugged into the usb port

according to the output above, the compoter DOES see the device, it's just in a format it can't access

> **ltcnr2g said:**
> I think this is too much of a headache. I will just take it to a friends computer that has windows and put music onto it.

if there is no music on it now, then now is the time to convert it, will also make it easier to deal with in windows so you won't need the software to put music on it from any computer.

---

