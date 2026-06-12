---
title: "Getting firefox back"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by patman0623 on 2009-11-08
When under Ubuntu 9.04, I at some point got Shiretoko as a replacement for the standard Firefox. In other words, I have the developer version installed. This is bad, obviously, because it has bugs; additionally, after my update to 9.10, I am still running the version compiled for 9.04.

How do I get FF 3.5 back and keep all my settings and add-ons?

---

### Post by t0p on 2009-11-08
I'm afraid I don't know Shiretoko's package name.  But assuming it's "firefox", you could type the following commands into a terminal:

```
sudo apt-get remove firefox
```

then  ```
sudo apt-get install firefox
```

Alternatively you can do it through Synaptic.  Just make sure you tell Synaptic not to "completely remove" it or you'll lose your settings.

---

### Post by peculiar penguin on 2009-11-08
^ firefox-3.5

> In other words, I have the developer version installed. This is bad, obviously, because it has bugs;It may been that way in the beginning, but it was updated like any other package and was at version 3.5.4 when I left for Karmic (where firefox is a meta package pointing at firefox-3.5 now).

Look at the title bar or the "about" window, if it's called Firefox and has the proper icon, the firefox-3.5 package must have been reinstalled during the update. If it's still "Shiretoko", just un- and reinstall the package yourself.

---

