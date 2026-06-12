---
title: "Ubuntu 10.04: Flash/Fire take over sound device"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by BrandonLC on 2010-07-25
I upgraded to 10.04 and now there are sound issues....it's a familiar story.

I've been up and down dozens of suggested solutions for fixing Firefox/Flash based audio issues for about 10 hours. From re-installing PulseAudio to wiping flash.

I get not sound from Flash, until I turn on Analog Stereo Output. Analog Stereo Output will get me sound, but Firefox/Flash will hog the device until the application is closed. With duplex doesn't make a difference.

So system sounds, and sound for applications like RhythmBox, won't return until I close Firefox.

Wow..this is annoying, and it's happened after each Ubuntu upgrade, and the solution has been different each time.

What do you think I should try next?

---

### Post by collinp on 2010-07-25
I've never had this kind of issue while running pulseaudio.

Are you sure that pulseaudio is running?

---

### Post by muteXe on 2010-07-25
Do you dual-boot? If so does this happen in windows?

---

### Post by BrandonLC on 2010-07-25
No dual booting. 

Well, I assume PulseAudio is running because it was never turned off as far as I know. How can I verify?

---

### Post by BrandonLC on 2010-07-25
Ok....looks like it is running.

4711     1  3 11:46 ?        00:04:09 /usr/bin/pulseaudio --start --log-target=syslog

---

### Post by puca mor on 2010-07-25
> So system sounds, and sound for applications like RhythmBox, won't return until I close Firefox.

I have the same problem. I checked and pulse audio is running. 

Is it something to do with needing Rythmbox to run with pulseaudio instead of alsa - so it can handle a browser and rhythmbox both outputting sound?

---

