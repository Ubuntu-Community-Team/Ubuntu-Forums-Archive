---
title: "So, I closed Firefox, and my steaming music is still playing..."
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Bluenoser81 on 2010-10-22
I was streaming audio from a public radio station (cbc classical) with Firefox, like I usually do.  When I quit Firefox, probably 30 minutes ago now, the music continued to play...strange.  This is the first time this has happened.  I tried going back to the site and opening another stream, which just plays the stream a second time and creates an echo.  I tried muting and unmuting and fooling around with sound settings. Nothing.  I tried looking at "ps -e" but really don't know what I should be looking for in there to kill.  Any ideas? (yes, I could restart but I want to take the chance to learn here and troubleshoot).

---

### Post by fooman on 2010-10-22
try: system > administration > system monitor

click the processes tab and look for any firefox instances....* end process* for any of them.

hope that helps.

---

### Post by kaldor on 2010-10-22
> **Bluenoser81 said:**
> I was streaming audio from a public radio station (cbc classical) with Firefox, like I usually do.  When I quit Firefox, probably 30 minutes ago now, the music continued to play...strange.  This is the first time this has happened.  I tried going back to the site and opening another stream, which just plays the stream a second time and creates an echo.  I tried muting and unmuting and fooling around with sound settings. Nothing.  I tried looking at "ps -e" but really don't know what I should be looking for in there to kill.  Any ideas? (yes, I could restart but I want to take the chance to learn here and troubleshoot).

I will blame Flash or Java. Check for either of those processes, and "kill -9" them.

---

### Post by macem29 on 2010-10-22
firefox is a delinquent app on ubuntu...worked fine for me for years on XP machines,
everyday is a new adventure with it now, nothing tragic yet however

---

### Post by Bluenoser81 on 2010-10-22
Flash and Java aren't running. The only thing that is running that seems to be using a small amount of cpu is "pulseaudio" (and yes the music is still playing lol). No instances of Firefox open. Is it ok to kill pulseaudio or is that a service I would have to restart afterwards? EDIT: something called npviewer.bin is running, taking up 22% cpu usage, too.

---

### Post by Bluenoser81 on 2010-10-22
Ok, so it WAS a Flash related issue. I took a chance and ended the npviewer.bin process running (there was another one listed as 'sleeping' and 0% cpu).  Upon selecting npviewer, right-clicking, and selecting 'Open Files' I could decipher that it was connected to an IP on a socket and flash was involved. Problem solved. To test my sound I went to Youtube and watched a video..still working fine! Thanks for the suggestions, folks.

---

