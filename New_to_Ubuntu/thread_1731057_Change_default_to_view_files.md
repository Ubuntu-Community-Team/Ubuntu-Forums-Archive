---
title: "Change default to view files"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by jmumby on 2011-04-16
somehow I have managed to make shotwell my default file viewer. So when I every try to open a folder it gives an error from shotwell telling the folder is not a file. How do I change it back to Nautilus.

thx

---

### Post by fabricator4 on 2011-04-16
> **jmumby said:**
> somehow I have managed to make shotwell my default file viewer. So when I every try to open a folder it gives an error from shotwell telling the folder is not a file. How do I change it back to Nautilus.

thx

Open "Computer" from places (you should be able to do this at least) then right click on the folder for the device.  Select "Open with Other Application" then select "Nautilus file manager" (which might just be called "file browser in the list) and make sure the box "remember this application for folder files" is selected.

Chris.

---

### Post by K_45 on 2011-04-16
If that doesn't work run this in a terminal:

```
sudo find /usr/share/mime -type f -exec chmod a+r '{}' \;
```then reboot. This will reset all file associations back to default.

---

### Post by yetiman64 on 2011-04-16
Another way is use ALT + F2, type in "nautilus" (without the quotes) then click "run". On any folder in the window that opens right click and select "Open with other application", scroll down and select "Open folder" while checking the tickbox "Remember this application for "folder" files" is TICKED.

It is the previously mentioned tickbox being on by default which would have caused your problem when you have previously attempted to open a folder with shotwell. It is a known nuisance that setting.

---

### Post by jmumby on 2011-04-18
> **fabricator4 said:**
> Open "Computer" from places (you should be able to do this at least) then right click on the folder for the device.  Select "Open with Other Application" then select "Nautilus file manager" (which might just be called "file browser in the list) and make sure the box "remember this application for folder files" is selected.

Chris.

This worked, thx

---

