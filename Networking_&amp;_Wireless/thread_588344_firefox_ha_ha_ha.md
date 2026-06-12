---
title: "firefox ha ha ha"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by xieu90 on 2007-10-23
well welcome to this topic, can anyone here tell me where the firefox store its bookmark ?
or how can I export it to pendrive in terminal (recovery mode)

---

### Post by animeh on 2007-10-23
Easy.
- close Firefox.
- copy/move your bookmarks.html file (and bookmarks.bak) to the location you prefer to keep it.
- open Firefox.
- enter about:config in the Firefox location bar, right-click on any of the listed preferences, and choose New -> String.
- enter the preference name: browser.bookmarks.file
- for the value, enter the new file path (including the file name) of your bookmarks.html file.

Using this method, not only can you share your bookmarks file with other Firefox users on the same computer (and possibly same network. I’m not sure.), but share the file with SeaMonkey users, or Mozilla Suite users, or Netscape users. If you share with SeaMonkey/Mozilla/Netscape, just remember that live bookmarks will not function.

---

### Post by kerry_s on 2007-10-23
first you need to find what your usb is, so> **fdisk -l**
once you know what your usb is->
**cp /home/you-name/.mozilla/firefox/*.default/bookmarks.html /dev/your-usb**

done

---

