---
title: "Sound"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by sbentjies on 2009-03-23
I have a Soundblaster card that lspci recognizes and it works in sound test, but won't play any sound from the browser. If this is a plugin issue, what am I missing. Any further help would be greatly appreciated.


sbentjies

---

### Post by GepettoBR on 2009-03-23
Will it not play ANY sound from the browser, or just not Flash? For example, if there's a streaming midi or wav, will that play?

try installing mozilla-mplayer (assuming you're on Firefox).

---

### Post by taurus on 2009-03-23
What site(s) did you check out with your browser, firefox I assume?  If you need plugins for your web browser, just install the ubuntu-restricted-extras package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
Don't forget to restart firefox.

---

### Post by wbee on 2009-03-23
sbentjies,

Two short answers:

1. If the card was an upgrade from onboard sound,go into your bios and disable the internal sound.

2. Double click the speaker icon on the system tray and check that all the mute functions are unclicked(no red in the icons). Then,play with the check marks in the digital source boxes until it works.

Long Answer:

Search for Markbuntu's comprehensive guide to Unbuntu Sound.

------------

W

---

### Post by Sylslay on 2009-03-23
Notice the same story with firiefox 3.07 than in recent days did any update of system. At begun evrything works fine.
I just switched back to kernel 2.6.24-23-generic
from kernel 2.6.24-24-generic, and I can sitll liten any internet radio. :-) and watch youtbe

---

### Post by sbentjies on 2009-03-25
It does not play sound on YouTube or from the media player in Ubuntu.

---

### Post by sbentjies on 2009-03-25
I'd like to thank all of the posters above-the combination of those package installs and turning off onboard sound in the BIOS was a success. As usual our community ROCKS!

sbentjies

---

