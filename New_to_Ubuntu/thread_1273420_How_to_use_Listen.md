---
title: "How to use Listen"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by aa4bb on 2009-09-23
First time user here. I copied an mp3 onto my hard drive. I right-click and select Open with Listen. Nothing happens.

I opened Listen. I tried to "import" (from the File menu) the mp3. Nothing happens.

At some point yesterday, I got a message saying that I needed an encoder/decoder or whatever for mp3, but no longer am getting that message.

My intuition is failing me in getting Listen to work!

Is there a Listen manual? I couldn't find one on the listen-project.org web site.

---

### Post by rampageoberon on 2009-09-23
Try installing the package ubuntu-restricted-extras which should have the codecs

```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by mathay on 2009-09-23
As rampageoberon said, install the restricted extras and see if that helps. For more information, check out [this documentation]("https://help.ubuntu.com/community/RestrictedFormats").

If you're still having trouble, go to Music > Preferences. Click the 'Library' tab and choose the directory your music is located in. Check the boxes bellow as you see fit. Everything should be in order after that.

---

### Post by aa4bb on 2009-09-23
It replies that ubuntu-restricted-extras were not found.

---

### Post by rampageoberon on 2009-10-13
> **aa4bb said:**
> It replies that ubuntu-restricted-extras were not found.

The package ubuntu-restricted-extras (restricted by copyright) is available in multiverse.

To check if the multiverse repository is enabled go to System -> Administration -> Software Sources and check under Ubuntu Software.

Tick the multiverse checkbox and try run the command again.

Hope that helps.

---

### Post by lavinog on 2009-10-13
[Click here to install the ubuntu-restricted-extras package](apt:ubuntu-restricted-extras?section=universe?section=multiverse)

here is some more information:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by |Mitch| on 2009-10-13
sudo apt-get install xubuntu-restricted-extras

assuming you have xubuntu and not ubuntu

---

### Post by lavinog on 2009-10-13
[Click here to install xubuntu-restricted-extras](apt:xubuntu-restricted-extras?section=universe?section=multiverse)

---

