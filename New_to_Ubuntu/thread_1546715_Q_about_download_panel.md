---
title: "Q about download panel"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by paker on 2010-08-05
When I download from Firefox, the download panel opens up automatically and shows progress. Since a few days ago, the download panel disappears when Firefox is closed. I need to keep the download panel open. Fix?

---

### Post by mike555 on 2010-08-05
If you use the built-in downloader in Firefox , then of course it closes when you close Firefox .......... you might want to install a different downloader , like maybe ; gwget

---

### Post by paker on 2010-08-05
The download panel used to stay on. It started closing just a few days ago. My other ubuntu machine runs the same 9.10 and the download panel doesn't close.

---

### Post by lovinglinux on 2010-08-06
> **paker said:**
> The download panel used to stay on. It started closing just a few days ago. My other ubuntu machine runs the same 9.10 and the download panel doesn't close.

What you are experiencing now is the correct behavior. Your download dialog wasn't closing before, probably because of a bug. I have noticed such bug recently, not only with the download dialog, but with other dialogs as well, like the add-ons manager and error console, that are kept opened even if I close Firefox. This behavior is not desired, although I'm sure you like it. The reason why all Firefox dialogs should be closed when you exit Firefox, is because if you try to start Firefox again while a dialog is still open, Firefox won't be able to start, at least using the same profile. Besides, downloads can be resumed when you start Firefox again (most of the time anyway).

If you want to keep your downloads open after you close Firefox, then you should use an external download manager. You can integrate standalone download managers with Firefox by using [FlashGot]("https://addons.mozilla.org/en-US/firefox/addon/220/") extension. You can check the supported download managers in [this page]("http://flashgot.net/").

---

### Post by paker on 2010-08-06
> **lovinglinux said:**
> What you are experiencing now is the correct behavior. Your download dialog wasn't closing before, probably because of a bug. I have noticed such bug recently, not only with the download dialog, but with other dialogs as well, like the add-ons manager and error console, that are kept opened even if I close Firefox. This behavior is not desired, although I'm sure you like it. The reason why all Firefox dialogs should be closed when you exit Firefox, is because if you try to start Firefox again while a dialog is still open, Firefox won't be able to start, at least using the same profile. Besides, downloads can be resumed when you start Firefox again (most of the time anyway).

If you want to keep your downloads open after you close Firefox, then you should use an external download manager. You can integrate standalone download managers with Firefox by using [FlashGot]("https://addons.mozilla.org/en-US/firefox/addon/220/") extension. You can check the supported download managers in [this page]("http://flashgot.net/").Thanks for the explanation. I thought I got a download-panel-closing bug. I never guessed it was the other way around. I will follow your instructions tonight.

---

