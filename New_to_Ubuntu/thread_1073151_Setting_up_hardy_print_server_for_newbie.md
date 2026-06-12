---
title: "Setting up hardy print server for newbie"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by zulasmum on 2009-02-18
I've recently set up a headless server running hardy. With help from the forum I have managed to share files on our windows network and now I want to share a printer. The printer is now connected via usb into the server and I have downloaded and installed cups. What to do next? I think that I have to configure cups somehow and also samba. Some easy steps would be a great help.

---

### Post by jimmy the saint on 2009-02-18
The community documentation has a section dealing with sharing cups printers.  It walks you through setting up samba as well.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by cariboo on 2009-02-18
You can install printers using the cups web interface. install elinks, then at the prompt type:

```
elinks http://localhost:631
```

The above assumes you aren't running a gui, if you are just open firefox and in the address bar type:

```
http://localhost:631
```

Jim

---

### Post by zulasmum on 2009-02-18
Ok thanks, I have just added a printer using elinks and I can now see my printer on the network but I get the message "access denied". This must be something to do with users right? Do I need to adjust my samba conf file?

---

