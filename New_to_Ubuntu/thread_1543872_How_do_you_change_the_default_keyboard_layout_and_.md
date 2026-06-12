---
title: "How do you change the default keyboard layout and mappings on ubuntu server?"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by kinygos on 2010-08-01
I've installed Ubuntu Server 10.04 LTS, and am trying to configure it to boot with the keyboard layout set to GB, qwerty.

I've installed console-data so can change the keyboard layout by running *sudo dpkg-reconfigure console-data* and selecting *pc / qwerty / British / Standard / Standard*

However, when I reboot the server, the keyboard layout is back to US again.

I have found the file /etc/default/console-setup and made the following changes:

[I]XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""
[/I]
Unfortunately, this doesn't make any difference.

How do I configure Ubuntu Server to load the keyboard layout, mapping, and locale that I want at boot?

---

### Post by jarviser on 2010-08-01
Does that version have System/Preferences/Keyboard then Layout tab?

---

### Post by kinygos on 2010-08-01
I'm not sure what you're referring to, but I've finally found the answer:

I need to run *sudo dpkg-reconfigure console-setup* then make the appropriate selections.

Thanks to all that read my post :)

---

