---
title: "Random Rebooting and Sound Card Not Detected in Intrepid"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by HolyDonut on 2009-03-23
I was having problems with my sound card not being detected by the volume control and getting some error about Gstreamer plugins before updating to Intrepid. 

When I first updated to Intrepid, all my problems were fixed. But suddenly Intrepid started randomly rebooting and nothing in the syslog is helpful in figuring out what happened.

Then the volume control was suddenly unable to find a mixer track again and I started getting the Gstreamer error again saying "No volume control Gstreamer plugins and or devices found."

Anyone have any ideas about what might be causing this? It's not a hardware problem since my system is stable in Windows XP.

---

### Post by lavinog on 2009-03-24
There are some issues with alsa drivers on some devices. What is your soundcard?
can you post the output of lspci?

---

### Post by markbuntu on 2009-03-24
Go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that is not entirely helpful go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

