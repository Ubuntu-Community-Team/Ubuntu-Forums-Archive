---
title: "some questions on sound and printing"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by alvinmoneypit on 2010-10-28
Hi,
I'm running Ubuntu 10.10 on a new AMD system.  
1) When I boot up, the startup sound is playing through the on board audio in 5.1 (at least it's playing though all my speakers) but when I load media into my players or even test the audio using the provided sound config tool, it is only in stereo using my front speakers only?  How should I configure it correctly?

2)  I have a lexmark X1150 printer.  It doesn't print.  I looked it up, people have been unable to get this printer to work for 6 years on Ubuntu.  Some say to use the ppd for z600 *which I can find nowhere) or to find the ppd for x1150.  I downloaded the package provided by lexmark fro xp and unpacked it, but I cannot find a file with a ppd.  How would I find it or otherwise get this printer working?

Thanks for all responses

---

### Post by cariboo on 2010-10-28
I'm not sure about your sound problem. For your printer problem, if you just go through the normal printer install dialog, you should get to a section where it allows to to pick the printer manufacturer and model, the z600 driver should be listed there.

Lexmark's support for low end consumer printers hasn't been very good until just lately. The only Lexmark printer I've had any dealings with lately was a high-end color laser, and it was detected automagically and the drivers loaded.

---

### Post by ArgusVision on 2010-10-28
You could open a terminial, enter "alsamixer", and check your settings. 

As far as printers go, You could look around in CUPS.
In your browser go to 127.0.0.1:631 
Go to "Adding a Printer and Classes"
Click add printer, and see if you can add it from there.
(I realize you may have already tried this.)

---

### Post by alvinmoneypit on 2010-10-28
Thanks Argus and Cariboo.

I did use the "add a printer" dialog in administration > printing.  I did NOT have a choice for Z600.  However, I did find a wiki that had a place where I could download it, so I did and got it printing, at least in black and white.  The color printing is extremely amiss, but that is what is evident from reading these forums,   

I wonder if there is any chance to get my scanner section of this 4 in one working???

On the sound.  Please be more specific about looking around in terminal.  I know very little about the terminal except some commands I've done by copying solutions for problems on this forum.  I was wondering is there an interface that manages all my sound device that I haven't found or downloaded yet.  This is only the 4th or 5th reboot on this system.  I''ve always had trouble getting linux to work with everything, but once it's working it seems to be superior and more stable than windows.  I've had v9 on my laptop for over 1 year now.

---

### Post by alvinmoneypit on 2010-10-28
Just a note:  I'm running 10.10 on this new system (I need to update my profile).  

Cariboo:  
I did look at the alsa mixer in the terminal.  when I switch from 2 ch to 6 ch, I can hear a loud "click" while doing so, and some faint "white noise" through the channels not broadcasting - seems to indicate they are on.  

Since this is my onboard audio from Asus, it's a case where the back "mic" and "line in" channels become "Center" and "surround" when hooked up to speakers.  I wonder if there is a driver missing or maybe a configuration I missed.  I'll look at the motherboard docs to make sure I didn't overlook something.

---

### Post by alvinmoneypit on 2010-10-28
I checked my wiring making sure it was connected as it was supposed to be to generate 6 channel sound.  No difference, still only playing 2 ch.  Then I went to the Alsamixer in terminal as Cariboo suggested.  While switching back and forth between 2 channel and 6 channel modes, it suddenly started working.  

I'll mark this one as "solved" and post the next question.  Thanks for all who replied and good luck to those reading.

---

### Post by ArgusVision on 2010-10-29
I hope the rest of your Ubuntuing goes smoothly.

---

