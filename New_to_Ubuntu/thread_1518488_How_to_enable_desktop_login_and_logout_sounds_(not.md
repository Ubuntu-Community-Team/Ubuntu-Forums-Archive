---
title: "How to enable desktop login and logout sounds (not the system sound prior to login)"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by thane1 on 2010-06-26
Have successfully changed the system-ready.ogg file to a file of my choice and have gotten it to play at sound level of -3.0 successfully via editing the    /usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop    file.  However for the life of me I cannot find out how to make ubuntu lucid lynx play the desktop-login and desktop-logout soundfiles when logging in and out.  Have always liked the Dapper sounds and have kept copies for this purpose.  Changed the Dapper .wav files to .oggs and substituted them for the  /usr/share/sounds/ubuntu/stereo    login and logout .ogg files.  They will play, if for example in terminal I enter         canberra-gtk-play id="desktop-login"   
Where is the config file (if there is one), which will let me enable these event sounds and if its not obvious, how do I enable the sounds?  System-Preferences-Sounds will not do it.  And so far I've had no success using the Applications-SystemTools-ConfigurationEditor route either.  Many thanks.

---

### Post by toniarregui on 2011-06-03
Once your sound files are in the usr/share/sounds/stereo folder, you have to change the rights and give yourself the right to play those files. SO you go to properties of the file, tab righs or permission or however it says it, and there you see twice "root".In the second you choose your username and give you the right read only. In the "others" entry you choose read only too. 
Done.

---

### Post by icekool666 on 2011-07-06
> **toniarregui said:**
> Once your sound files are in the usr/share/sounds/stereo folder, you have to change the rights and give yourself the right to play those files. SO you go to properties of the file, tab righs or permission or however it says it, and there you see twice "root".In the second you choose your username and give you the right read only. In the "others" entry you choose read only too. 
Done.

Hi there,
I have the same problem, I want to enable or restore the default for playing desktop-login.ogg at startup, i like that sound and it has just stopped for some reason (I just upgraded to 10.10, so a clean fresh install), it was sounding for the first few startups but is now silent.

I tried your step above but it doesn't make any difference and I opened the stereo folder as root and made the changes. The Gnome login/startup sound is fully enabled in all other settings and i havent messsed with any gdm changes.

If you have any ideas I would be very grateful.

btw, the drum beat sound is playing at the login prompt before getting to the desktop environment.

---

