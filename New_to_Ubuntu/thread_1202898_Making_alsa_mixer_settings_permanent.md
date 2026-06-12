---
title: "Making alsa mixer settings permanent"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by kevindubrow on 2009-07-02
Hi, I am running Ubuntu Netbook Remix on a HP Mini 1000. After doing some fixes found on the internet, I got my internal microphone working. The problem is that I have to make these changes to the mixer every time at startup:

In the alsamixer command:

Master = 68
Headphone = 79
PCM = 100
Front = 100
Capture = 60 (Space Bar to enable)
Capture 1 = Disabled
Analog Loopback = Off
Analog Loopback 1 = Off
DAC0 – Enabled 84
DAC1 = Disabled
Import0 = Enabled 100
Import1 = Disabled
Input Source = Line
Input Source1 = Line
Mux = 0
Mux1 = 0

How do I make these changes permanent? Oh, and if it is useful for anyone, the following website teaches you how to get sound working on the HP Mini and one of the replies tells you how to get the internal microphone working: [http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html](http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html)

Thanks a lot!

---

### Post by radioact1ve on 2009-07-04
This might work:

- Get the settings exactly the way you want them.
- *sudo alsactl store* into the terminal.
- Edit the /etc/rc.local file as root and then add in the line *alsactl restore* before exit 0
- reboot


I'm still having sound issues with my hp mini 110. Tried the solution mentioned above to no luck. Headphone work for now, that will have to do...

---

### Post by kevindubrow on 2009-07-04
It worked! Thank you so much!

Is there any way to keep the regular mixer settings permanent too? Another thing I have to do after every reboot is open the volume control from the task bar, unmute the headphone bar and speaker bar, and mute the PC beep bar.

Again, thank you for getting my microphone settings working correctly, If I could just get the sound mixer settings to stay, I would be completely happy with how Ubuntu ran on my computer. 

If I were you I would try to reinstall and try that sound fix, it seems to work for a lot of people. If not, the person who started the topic posted a link to an optional way to fix the sound which also worked for me (I tried both separately...and now that I think about it, I'm still using the optional fix he suggests).

---

### Post by MontoyaF1 on 2009-12-31
> 
- Get the settings exactly the way you want them.
- *sudo alsactl store* into the terminal.
- Edit the /etc/rc.local file as root and then add in the line *alsactl restore* before exit 0
- reboot

I just upgraded to Ubuntu 9.10 and the External Amplifier button is checked.  I tried the above but it still won't save my changes, so everytime I reboot I have to go into Alsamixer to uncheck that stupid box.  What gives?

---

### Post by MontoyaF1 on 2010-01-03
Anybody?

---

### Post by omelette on 2010-07-05
> **radioact1ve said:**
> This might work:

- Get the settings exactly the way you want them.
- *sudo alsactl store* into the terminal.
- Edit the /etc/rc.local file as root and then add in the line *alsactl restore* before exit 0
- reboot


I'm still having sound issues with my hp mini 110. Tried the solution mentioned above to no luck. Headphone work for now, that will have to do...


Oldie but goodie - works for my Dell laptop running Ubuntu 10.04 also!!!

Many thanks to the contributor.  Should this be classed as a bug?

---

### Post by lidex on 2010-07-07
Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

