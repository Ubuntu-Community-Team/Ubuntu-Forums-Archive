---
title: "text to speech ubuntu 10.4 finally"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by wb5hqh on 2010-08-22
I couldn't get KTTSmgr to work on the new versions and so I finally decided to try getting a windows program on WINE. I installed WINE did the update then dist-upgrade.
I downloaded Speakonia into the Downloads folder.
I then downloaded Microsoft Text-to-Speech Engines[B].
===============================
[/B] Opened a terminal.
cd Downloads
wine speakoniasetup-1.0.exe
wine msttsl.exe
==============
When the install programs start, just take the defaults.

I then found the Speakonia program on the application bar, left click and put it on the desktop. I use the Mary voice myself. Not perfect, but very good.

---

### Post by lkjoel on 2010-08-22
To make KTTSMGR work, simply type this in a Terminal Window:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install festival festival-freebsoft-utils kttsd

```

---

### Post by AlphaLexman on 2010-08-22
Have you tried 'espeak' it is in the repo's, but IMO it sounds kind of like the movie 'War Games' computer voice.

---

### Post by jmszr on 2010-08-22
@AlphaLexman,

If you install the packages "Gespeaker" and "Gespeaker-mbrola-en", you get a GUI for espeak along with a lot of various voices. The en is for English speakers, of course - there are 18 or so languages.

---

### Post by lkjoel on 2010-08-22
> **AlphaLexman said:**
> Have you tried 'espeak' it is in the repo's, but IMO it sounds kind of like the movie 'War Games' computer voice.
```
sudo apt-get install cowsay
(cowsay -f daemon "Hello! How are you?"); espeak -v en "Hello! How are you?" > /dev/null 2>&1

```
:lolflag:

---

### Post by MorleyPotter on 2010-09-21
> **lkjoel said:**
> ```
sudo apt-get install cowsay
(cowsay -f daemon "Hello! How are you?"); espeak -v en "Hello! How are you?" > /dev/null 2>&1

```:lolflag:

Just out of interest what does the "> /dev/null 2>&1" actually do?

---

### Post by lkjoel on 2010-09-21
> **MorleyPotter said:**
> Just out of interest what does the "> /dev/null 2>&1" actually do?
It redirects the output and the error to nothing.

---

