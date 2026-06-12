---
title: "simple query in the definition of sound"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by mountdiat on 2010-10-12
peace, mercy and blessings of God
 
I have a simple query in the definition of sound
 
when I have installed Ubuntu10.4  for the first time is not defined sound
And followed these steps:::::::::::::::::::::::::::::::::::::::::::::  :::::::::::::
 1-Removing PulseAudio
   sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
 2-Removing ALSA packages
 sudo /etc/init.d/alsa-utils stop sudo apt-get remove alsa-base  alsa-utils 3-Blacklisting ALSA Kernel Modules sudo dpkg-reconfigure  linux-sound-base 

 4-[SIZE=2]Installing OSS    [/SIZE] 
  [SIZE=2]5-Configuring Applications to Use OSS[/SIZE]
 [SIZE=2]gstreamer-properties[/SIZE] [SIZE=2]::::::::::::::::::::::::::::::::::::::::::::::::::  ::::::::::::::::::::::::::::::::::::::::::::::::::  ::::::::::::::::::[/SIZE]
It was then the definition of sound, [SIZE=6]but[/SIZE] .......
*Can not open the volume control
**sound icond does not appear
***Low sound almost
            **************************************************  ***
But when install virtualbox and  install  fresh Ubuntu 10.4
Only you choose the appropriate definition of the sound ”” oss  or    PlseAudio””'did not show any of the previous problems
[SIZE=4]Question 1:-[/SIZE]How do Iselect  the sound driver  directly as in virtualbox??
 Question 2:-  if failed:-how can i solve  previous problems??
 

 my motherboard is gigabyte g41  
 

 please help .................

---

### Post by CharlesA on 2010-10-12
Duplicate thread.

[http://ubuntuforums.org/showthread.php?t=1594499](http://ubuntuforums.org/showthread.php?t=1594499)

---

