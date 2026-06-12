---
title: "How Do I determine if TV Turner card is over ridding webcam?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-22
Ubunteros,

I have a tv turner which I installed into my PC. After this I installed Skype.

When I open skype and right click on it from tool bar I get:

Options--:Video Devices AND THEN "test window" to test video feed from webcam.

When I click on "TEST" nothing happens!

If I close Skype and open TVTIME and then open Skype again and go to:

Options--:Video Devices AND THEN "test window" NOW I CAN SEE my video.

I think what is happening is tv turner is over riding something inside? Or maybe I need to tell skype to use this web cam only? But I don't know how it is do or what I really must do.

Any help on this most welcome.

Thank you.

---

### Post by sdowney717 on 2009-03-22
what is your model of webcam, does it work great?
would you recommend it?


from terminal
run lsusb and show the printout

run gstreamer-properties 

select the video and set the default, does this help?

---

### Post by suomalainen on 2009-03-22
sdowney717,

Below is the output you requested.

I'm sorry but I'm unsure how to do this which you requested:

"run gstreamer-properties

select the video and set the default, does this help? "

Please explain. Sorry.


Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08af Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by sdowney717 on 2009-03-22
run it by typing it into terminal

---

### Post by suomalainen on 2009-03-22
sdowney717,

Sorry for the dumb question. I figured it out. But what exactly do you want me to choose from the drop down menus and from which drop down menus???

Thank you!

---

### Post by suomalainen on 2009-03-22
sdowney717,

This is what I see when I open the program you asked me to open. It's much different from yours.

P.S. A stupid question but what exactly are we looking to achieve?

Thank you

---

### Post by sdowney717 on 2009-03-22
under Default INPUT, select your webcam.
Maybe it will default to this webcam instead of the tv card

---

### Post by suomalainen on 2009-03-22
sdowney717,

Ok I got it now as per what your trying to determine!

Here is the problem. When I launch skype and then right click the icon and go to Options-->video devices and "test" I can't see my video!

If I launch tvtime then Skype and then Options-->video devices and "test" I can then see my video. All this in that test box area of Skype.

If I reboot and again launch Skype and call a contact who's online and then choose "show Video" or is it "show my video"??? then the person I'm talking with can see me but I can't see the minimized video image of me nor the video image within: Options-->video devices and "test".

Is there a solution for this???

---

