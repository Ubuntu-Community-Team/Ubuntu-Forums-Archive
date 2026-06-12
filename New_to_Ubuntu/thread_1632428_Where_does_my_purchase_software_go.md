---
title: "Where does my purchase software go?"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by cor2y on 2010-11-28
So i made a purchase today via the ubuntu software center.
The transaction went through the software downloaded and installed but i have no idea where it is or how do i get it back when i do for example a clean install.
I cant find the files

---

### Post by jtarin on 2010-11-28
Most installed applications appear
      in the Applications menu in the corner of the screen,
      in the same category as they came from in the Software Center.
    


      For example, if you installed a program from the
      Office department, it will appear inside
      Applications &#9656; Office.
    


      Utilities for changing settings may appear inside
      System &#9656; Preferences or
      System &#9656; Administration.
    


      If you are using Ubuntu Netbook Edition,
      an application appears in its category on the home screen.
    


      Some items, such as media playback or Web browser plugins,
      do not appear in the menus.
      They are used automatically when Ubuntu needs them.
      For a Web browser plugin, you may need to close the browser and
      reopen it before the plugin will be used.
    
Could you post the name of the software you installed?

---

### Post by cor2y on 2010-11-28
Sorry for the misunderstanding.
I purchased the fluendo codec pack today from the ubuntu software center, however while the software center downloaded and installed the software it didnt provide a link or anything to the file if for example i wanted to download it and save/sync it somewhere like say ubuntuone , a usb key or even on the harddrive.
The Software Center will download and reinstall the purchase software but you dont get access to it to save somewhere else.

---

### Post by mikewhatever on 2010-11-28
The downloaded installation files are usually stored/cached in /var/cache/apt/archives/. Not quite sure about payed apps.

---

### Post by cor2y on 2010-11-28
Thanks [mikewhatever]("http://ubuntuforums.org/member.php?u=160645") not easy to find but found it and backed it up.
Why they refused to give you access to the deb package you paid for either by sending a link to it in the confirmation email or allowing it to be synced to ubuntuone if its enabled like with the music store.
Marking as solved.

---

### Post by mikewhatever on 2010-11-28
Don't you get a validation key for future installations? The package version and its dependencies may change in future Ubuntu releases, so that you might have a problem installing the backed up .deb.

To facilitate file system browsing, press ctrl+l in the file browser windows, type the location (/var/cache/...) into the location bar and hit enter.

---

