---
title: "Why is time of pictures from digital camera off by timezone?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by janmartin on 2009-06-18
Hi all,

I have a "point and shoot" digital camera.
It is set to my local time. 

I am in Germany and we have "daylight saving" in summer, so today German time is GMT +2 hours.)

Also in System => Administration => Time and Date my Ubuntu Notebook is set to timezone "Germany/Berlin"

**Both camera and Notebook display exactly the same time on various displays.**

When I connect the camera as USB mass storage the time shown in "Date Modified" column of Nautilus is 2 hours in the future.

E.g. for a picture really taken at 3 pm the "Date Modified" as shown by Nautilus is 5 pm.
(Btw. other programs show the same wrong time, so its not Nautilus.)

This totally messes things up.

**What's wrong?**

The Big picture:
I am trying to archive pictures, then geocode the pictures with coordinates from my GPS logger. 

GPS loggers are always set to UTC, as this is what they receive from the GPS satellites.

Programs like gpsbabel expect the pictures to have the local time. But they don't.

---

### Post by mgmiller on 2009-06-18
As far as i know, the time info is in the exif data attached to the picture and is set by the camera.  Take a look in the setup section of the camera and although you may have it set to your local time, you may not have enabled it's "daylight saving time" mode.  I have a Canon  elf and the daylight savings mode is not obvious, you have to go into the time zone area to find it and turn it on and off.

---

