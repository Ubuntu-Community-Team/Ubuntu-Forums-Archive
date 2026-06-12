---
title: "How can I transfer video from camera to hard disc drive?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by sdim on 2009-06-11
Hi,everyone.
How can I capture video shot on a SONY Handycam camera (mini DV tape)to my PC?
Do I need a firewire port or can it be done in another way,i.e. through a USB port?

Many thanks.

---

### Post by halitech on 2009-06-11
what outputs do you have on the cam? that will determine how you can get it off

---

### Post by reeseslover531 on 2009-06-11
you need a firewire port on your computer as well as the correct cable. If it is a mini-dv cam it probably has a firewire port on the camera somewhere, look for it and then plug it into your computer. There are many dv capture programs for linux such as Kino.

---

### Post by sdim on 2009-06-11
Thanks for the replies.
Indeed,the camera has a firewire connection plug.
So,I'll probably need a firewire port on the pc.
Is it OK if I use a 5 year-old card that has 2 USB and 2 firewire ports...or will it be unusable on Linux?
I'm asking that before I insert it in the PCI slot (I need to remove a TV card that isn't any longer compatible with Vista,and of course not at all compatible with Linux).

---

### Post by reeseslover531 on 2009-06-12
Yeah I don't know for sure, but I would bet that the 5 year old card will work just fine!

---

### Post by sdim on 2009-06-12
Thanks.
I put it into the slot,and it seems to have been correctly recognised through lshw.
Now I'll have to see about the application I must use to transfer the video.
Many thanks again.

---

### Post by ricardisimo on 2009-06-15
I have a slot on the front of my Handycam DCR-DVD650 that says "A/V R". Is that the firewire port? I don't think a firewire came with the camera, which seems odd. How do I tell if I have a firewire port? Is there such a thing as a firewire-to-USB adapter?

Finally, why does the USB connection do absolutely nothing? So far as I can tell, absolutely nothing registers on the comp when I plug it in and choose either USB connection on the Handycam's touchscreen. Any thoughts? Thanks.

---

### Post by Iusedtowearatie on 2009-06-15
All you need to know about Firewire (1394):
[http://en.wikipedia.org/wiki/FireWire](http://en.wikipedia.org/wiki/FireWire)

On a Sony videocam you would probably find the smaller type, i.e. the so called "4-circuit" - if you have a Firewire interface, that is.

Typically 1394 is used because of high transfer rate requirements, like DV-video, transfer rates that are higher than what USB 2.0 typically support. Some videocams still have USB connectors, but typically for transferring still pictures.

I have not heard of any USB/Firewire adapter, but that doesn't mean there isn't one...

As for things connected to USB not showing up on the computer: Try switching the equipment on... :D

---

### Post by ricardisimo on 2009-06-15
No, I found the cable that goes in there (I did get one), and it's like a weird, small USB on the camera end, and RGB on the other. I imagine it plugs into a Player/Recorder or directly into a TV. We'll see.

---

### Post by Cheesemill on 2009-06-15
The USB connector on video cameras is usually only used for transferring still images from the memory stick. You'll need to use the firewire port for transferring video (it may be labeled IEEE1394 or i-Link).

---

### Post by Cheesemill on 2009-06-15
This is for ricardisimo, not the OP

I've just looked at the instructions for your camera, it doesn't have a FireWire port as it records onto DVD.

You just need to put the DVD you've recorded into your PC and rip the video off it that way.

---

### Post by ricardisimo on 2009-06-16
Unfortunately, those minidiscs are not reading in either of my disc drives, nor in my DVD player.

Meanwhile, there are two "USB Connect" functions in the Camcorder's menu options, and neither does a thing. That can't be right.

---

### Post by lisati on 2009-06-16
ricardismo: I haven't actually used a DVD camcorder but remember reading somewhere that you might have to "finalise" the disk before trying to read it in another machine. The output labelled A/V R is likely to be for connecting an AV cable from your camcorder to a TV or VCR

---

### Post by ricardisimo on 2009-07-13
Lisati -

Thanks. The "finalize" option on the camera itself was exactly what did the trick. I've been meaning to post a "thank you" for a while, but I've been too busy ripping and re-editing my home movies.

---

### Post by jadhav333 on 2009-08-16
I have a sony handycam DCR HC36E.. It has the following output connections: 1) Usb 2) DV 3) A/V out

The usb gets detected in the lsusb command.. 
Bus 004 Device 004: ID 054c:00c0 Sony Corp. Handycam DCR-30

But it doesnot mount/or reflect anywhere else in the system

How can I transfer the video files on the miniDVs onto my PC..

Thanks

---

