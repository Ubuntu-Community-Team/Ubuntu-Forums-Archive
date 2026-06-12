---
title: "usb dvb sticks"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by fitzy17 on 2010-01-11
I am a complete new comer to Ubuntu. Im running 9.10 and everything is great. Except when I plugged in my tevion dvb stick and my computer did not recognise it. So I tried another dvb stick that I have* (unfortuneatly I don't know the name of this model*) and get the same problem Ubuntu doesn't recognise either of them. Can anyone please help point me in the right direction to get me started. Thanks

---

### Post by Cabs21 on 2010-01-12
here is a similar thread see if that helps.

[Try Me.]("http://ubuntuforums.org/showthread.php?t=183297")

bump

---

### Post by fitzy17 on 2010-01-12
thanks you for the suggestion. I tried this thread but got this message at the first part.
Connecting to thadathil.net|216.240.187.143|:8000... failed: Connection refused.
but i appreciate the help

---

### Post by Cabs21 on 2010-01-13
here is the URL linked to the the Link from before

[http://ubuntuforums.org/showthread.php?t=183297](http://ubuntuforums.org/showthread.php?t=183297)

hope this helps

---

### Post by muteXe on 2010-01-13
does it show up if you do a "sudo fdisk -l" from the command line?
that's a little 'L', not a "one".

---

### Post by fitzy17 on 2010-01-17
Thanks for the help. 'Really' but I went away and tried all sorts of things that I googled and through a miss match of all kinds of advice, I finally came across the solutions. I found out  my second stick is either an Afatech 9015 or 9013 and I've got it running with Kafine after recieving  'can't find demultiplexer plug-in'  error message. The solution to this being downloading 'libxine1-ffmpeg' from the synaptic manager.I've got to say this process has taken  me a lot of time 'days actually' as a newcomer to Ubuntu I must say when I tried the same process in Windows. I plugged in the stick it found the drivers in seconds  and it was up  and running in a minute or two. Even having said that i'm sticking with Ubuntu for now.

Thanks to muteXe and Cabs21 for you help

---

### Post by ubuntu1sttimer on 2010-01-18
FITZY17, you don't indicate what video standard is needed or where you live which might indicate it. One the things complicating this is that the US has two standards, NTSC which is the now old analog video, ATSC which is the new digital. Much of the rest of the earth uses DVB versions for land basted broadcasting and a different one for satalite use.

I have two Tevion "DVD Maker"s. They work well in windows but I have not been able to get them working in linux. They are slightly different but both are for NTSC analog video and sound. The difficulty is not Linux but rather that the maker of the devices wrote drivers for Windows but not for other operating systems like Linux. 

They are sold in the US and some other parts of the world by a German grocery chain called Aldi's. More info about this product series is available at [http://en.wikipedia.org/wiki/Medion](http://en.wikipedia.org/wiki/Medion) . They are a good product and sold at a good price. I recently purchased one for $20 US. 

I am writing all this in hopes that someone knowledgeable in video drivers will see it and want to have a go at writing a driver. Maybe at the same time make the driver handle some of the other USB video devices. Who knows, maybe someone will read this and already have a way to do it and will tell us how to make it will work for both of our systems.

---

### Post by afspeter on 2010-04-26
I have the same problem
I am a complete new comer to Ubuntu. Im running 9.10 and everything is great. Except when I plugged in my tevion dvb stick and my computer did not recognise it. So I tried another dvb stick that I have* (unfortuneatly I don't know the name of this model*) and get the same problem Ubuntu doesn't recognise either of them. Can anyone please help point me in the right direction to get me started. Thanks[/QUOTE]
[http://www.aldi.co.uk/uk/html/offers/special_buys3_13901.htm](http://www.aldi.co.uk/uk/html/offers/special_buys3_13901.htm) pal uk

---

### Post by afspeter on 2010-04-26
> **muteXe said:**
> does it show up if you do a "sudo fdisk -l" from the command line?
that's a little 'L', not a "one".
no

---

