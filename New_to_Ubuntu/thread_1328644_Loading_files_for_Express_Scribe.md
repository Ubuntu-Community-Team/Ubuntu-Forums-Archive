---
title: "Loading files for Express Scribe"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Jasper7g on 2009-11-16
I have been using Express Scribe in Windows for years without a problem. Now that I want to switch to Ubuntu I find that I am unable to load mp3 files. The files can be located easily but the list of files to be loaded is greyed out. Can anyone tell me why this is and how I can resolve it? (Express Scribe is a small program for transcribing audio speech)

---

### Post by Jon Monreal on 2009-11-16
Try going to a terminal, typing "apt-get install ubuntu-restricted-extras" (without the quotes), and pressing enter. This package installs the codecs needed to work with MP3 files, which are not present by default due to the fact they are proprietary software.

---

### Post by Jasper7g on 2009-11-16
Thanks, I'll give it a try.

I've not been able to get that package to download.

---

