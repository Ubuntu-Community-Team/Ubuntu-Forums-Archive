---
title: "USB microphone not working in Skype"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Aregnaz on 2010-06-13
Hello,

I have recently installed Skype Static on my Hardy 8.04. I plugged in the USB, and the microphone did not work during testing. PulseAudio is currently installed. Not sure if I need to uninstall and use esound. If so, how do I install. I tried running commands in my terminal, but cannot input password. Your help is greatly appreciated!

---

### Post by diablo75 on 2010-06-14
To see if PulseAudio is hurting your sound config, try killing it and then run skype.  You can do a process kill from the terminal (sudo pkill pulseaudio) and then run skype to see if that helps.  If you do this, be sure to go to Skype audio settings panel while pulse is off to play with the available sound settings and see if you can select your microphone as an input source.

If you want to remove PulseAudio you should be able to just type "sudo apt-get remove pulseaudio" into a terminal.  When it asks for a password, you'll just type it (there won't be any ***'s showing up for each character you type but they ARE being typed).  At least that's all you need to do if you're running 10.04.

I remember having problems with Skype and Pulse/ALSA back when Skype released a new version that was advertised as supporting PulseAudio, but there was a glitch that affected some users (like me) which could only be dealt with by digging up the previous version of Skype from an old repository.

Currently I'm running 10.04 with Pulse and it works fine for me.  You might have better luck with your system if you upgraded from 8.04.

---

### Post by dez93_2000 on 2011-06-14
I've got a Trust HD Widescreen webcam. Video worked out of the box but no audio. Audio works fine in windows.
I tried the suggestions on this & other pages. pkilling pulse did nothing. My solution was painfully simple but dumb that it has to be done at all:

1. to to system > preferences > sound > input
2. select the radio button for the webcam. Even though there's nothing else on my system, it didn't auto-select this once it had been recognised. "ubuntu has detected a new microphone, but has decided that you would probably prefer to have nothing at all".

---

### Post by thane1 on 2011-06-14
I have a MS Lifecam, which works out of the box for video, but won't offer audio in ubuntu out of the box.  To fix this I installed pavucontrol from the repos.  

Once installed, start up a Terminal session, type in pavucontrol at the prompt, but don't press <enter> yet.  Start up Skype and start a "test call".  

While waiting for the test call to connect, left click on the Terminal pavucontrol line to change the mouse focus back to the pavucontrol line.  As soon as you hear the test call female voice, press <enter> on the pavucontrol line in Terminal and it will open a configuration screen for Skype.  

Select whatever you want for your audio there and in my experience, it should work.  Cheers.

---

