---
title: "What is OpenJDK"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-01-28
Notifier tell me this morning I have updates. Clicking on the updater it tells me OpenJDK has security updates(see screenshot) What is OpenJdk and how do I know if I need it. Don't want to get something I don't need. Also wondering if nasties are able to come into system through the updater?  I guess I still have the Windows mindset, paranoid about virus, spyware, keylogger, etc.  Slowly getting away from that way  of thinking though. It actually is more relaxing to sit down in front of a linux box compared to a windows box.

---

### Post by Cypher on 2009-01-28
OpenJDK-JRE is the Java Runtime Environment. There is also a version of the JRE distributed by Sun (the creators/inventors of Java).

Since either you or a package you are using installed OpenJDK for you, updating it would be good.

THe updater is directly linked to the servers maintained by Ubuntu. So the only way any "nasties" can get to your system through the updater is for the servers to be compromised and appropriate files added.

This is fairly unlikely and you can trust the files coming through the authenticated official repositories. If you add third party repositories yourself, then you cannot gaurantee that level of security..

---

### Post by philinux on 2009-01-28
[http://swik.net/Java/Open+Source+Java(OpenJDK)/What+is+OpenJDK%3F/9cjr](http://swik.net/Java/Open+Source+Java(OpenJDK)/What+is+OpenJDK%3F/9cjr)

---

### Post by S0m3th1ngw13rd on 2009-01-28
Ok did the update and now I have no sound little speaker icon on panel has a red x next to it.  I have a soundblaster XFI extremegamer was working great before. on the recommended updates was also some pulseaudio stuff could that break my soundcard drivers? Going to SYSTEM-PREFERENCES-SOUND brings me to sound preferences from the drop down list I see ALSA  OSS  and Pulsaudio none of which work(no sound when I test.

---

### Post by Martje_001 on 2009-01-28
> **S0m3th1ngw13rd said:**
> Ok did the update and now I have no sound little speaker icon on panel has a red x next to it.  I have a soundblaster XFI extremegamer was working great before. on the recommended updates was also some pulseaudio stuff could that break my soundcard drivers?
That's very likely. Try adding another user, does it work there? If yes: Delete your .* folders in your homedirectory.

---

### Post by sadaruwan12 on 2009-01-28
OpenJDK is a substitute or a the open source version of it's commercial counterpart Java(SunJDK).

And updating this want harm your PC in any way 'cos all the updates stream through th Ubuntu server do don't worry just update it and some web components need this to run properly.

---

### Post by S0m3th1ngw13rd on 2009-01-28
> **Martje_001 said:**
> That's very likely. Try adding another user, does it work there? If yes: Delete your .* folders in your homedirectory.

Added another user and no sound there either. Are there other steps I can take?

---

### Post by Martje_001 on 2009-01-28
Maybe. You can read this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Good luck.

---

### Post by S0m3th1ngw13rd on 2009-01-28
Got it working again by following this thread:

[http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+soundblaster](http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+soundblaster)

Thanks everyone

How do I mark thread solved?

---

### Post by jespdj on 2009-01-28
> **S0m3th1ngw13rd said:**
> How do I mark thread solved?
Use the Thread Tools menu at the top right of this page.

---

### Post by S0m3th1ngw13rd on 2009-01-28
> **jespdj said:**
> Use the Thread Tools menu at the top right of this page.

Option not even there, edited first post and added [solved] to title

Thanks again

---

### Post by Martje_001 on 2009-01-28
This function is temporary disabled (it was causing problems IIRC)

---

