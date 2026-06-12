---
title: "Webcam /dev/video directory missing?"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-10-26
After 5 days of searching/researching, I see that those 'buntuers who got their webcams working have a folder:

/dev/video

I have no such folder. Where can I see the "stock" directory tree of /dev that comes with Jaunty? 

How can I tell whether a driver for my webcam is installed correctly? The modprobe grep stuff works, but I'm missing a line about usbcore. That is where or what installs a directory named:

/dev/video   ?

---

### Post by SteveDee on 2009-10-27
> **Mark_in_Hollywood said:**
> ... where or what installs a directory named:

/dev/video   ?

Its not a directory that you are missing. When you connect a USB webcam, Linux creates a device "file" like this: /dev/video0  and if you connect a second usb webcam you should then see: /dev/video1 appear in the /dev directory. 

What make/model webcam are you using?

Once connected, type this in terminal:-
ls /dev/video*
and you should get a response:-
/dev/video0

Type this:-
lsusb
... and your camera identity should appear in a list with other connected USB devices.

If none of this works, try to borrow a webcam to check this out.

---

### Post by Mark_in_Hollywood on 2009-10-27
The output of the terminal, with a

Veo Stingray webcam plugged into the usb port is:

mark@Lexington-19:~$ ls /dev/video*
[COLOR="Orange"]/dev/video0[/COLOR]

and the lsusb output is:

Bus 002 Device 004: ID 0545:808b Xirlink, Inc. Veo PC Camera

my best understanding is that this specific piece of hardware is supported, but I cannot get the following to work: skype, camorama, camstream, xawtv, cheese, and gqcam.

---

### Post by SteveDee on 2009-10-28
OK, it looks like your webcam is supported via Video4Linux: [http://www.linuxtv.org/wiki/index.php/Gspca](http://www.linuxtv.org/wiki/index.php/Gspca)

I suggest you open Synaptic Package Manager and do a search for "v4l" to see what components are installed. I would install libv4l if this is not already installed.

If this doesn't work, you could take a look here: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)  ...and here:  [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

...or you could try updating to Karmic tomorrow....who knows, it might work?

Additional: Try this first:-
open a terminal and type; gstreamer-properties
In the dialog box that this launches, select the Video tab and use the Test button with the Video 4 Linux and then the Video 4 Linux 2 plugins. If either of these work, then read this document: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Mark_in_Hollywood on 2009-10-28
gstreamer-properties produced good results on the output, bad results on the input. Please see the attached screenshots.

---

