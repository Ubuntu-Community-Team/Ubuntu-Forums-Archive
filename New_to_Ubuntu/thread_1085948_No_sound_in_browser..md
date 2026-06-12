---
title: "No sound in browser."
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Grifulkin on 2009-03-03
Okay so I downloaded and installed Kubuntu 8.04 in Windows and this all started about 6 months ago with me wanting a 64 bit operating system to replace windows, so far I have tried Ubuntu 8.04, 8.10, and Kubuntu 8.10 64 bit and now I have settled on Kubuntu 8.04 as looking the best with KDE 3.5 but now I seem to have one little problem with my 64 bit setup.  Any web browser I use I have no sound, I have tried the comprehensive sound thread to try and fix this, I have also disabled my on board sound and still nothing can someone try and help me fix this because I have no knowledge of how to fix this? Also, this is really noobish but I love Konqueror web browser but I have figured out how to put flash in it yet?  So please help?!

---

### Post by handy on 2009-03-03
We need more details?

Does sound work everywhere else i.e. video's, CD's, MP3's, games...?

Have you installed all of the codecs?

What is the name, model, processor used by your sound card?

---

### Post by Grifulkin on 2009-03-03
Amarok has sound and also all of the desktop sounds work, IM sounds work, it seems to just be the browser that has no sound also my card is a Creative Sound Blaster Audigy SE that uses the CA-0106 Family Chip.  It is the only Sound Blaster card that uses that chip.  Video's have sound as well.  And I'm not sure what codecs to get for a web browsers I just thought you got plug-ins for that.

---

### Post by Grifulkin on 2009-03-03
bump, please any help?

---

### Post by crapple on 2009-03-03
Try this

Go to System- Preferences - Sound

Make sure your device is selected in all places.

Hope this helps.

---

### Post by Grifulkin on 2009-03-03
> **crapple said:**
> Try this

Go to System- Preferences - Sound

Make sure your device is selected in all places.

Hope this helps.

Yeah I have tried that as well, it doesn't work but thank you:)

---

### Post by Grifulkin on 2009-03-03
Bump

---

### Post by HavocXphere on 2009-03-04
Try this:
Setting default ALSA output device:
asoundconf list
asoundconf set-default-device *[device_name_from_listing]*

---

### Post by Grifulkin on 2009-03-04
> **HavocXphere said:**
> Try this:
Setting default ALSA output device:
asoundconf list
asoundconf set-default-device *[device_name_from_listing]*

Thanks for the shot but that didn't work either.

---

### Post by Grifulkin on 2009-03-05
Thank you everyone that contiributed to helping me but I guess I was putting the flash player in the wrong folder.  The .so file that is but I still don't understand how to get flash to work in konqueror but that is a differnt thread until then I can use firefox.

---

