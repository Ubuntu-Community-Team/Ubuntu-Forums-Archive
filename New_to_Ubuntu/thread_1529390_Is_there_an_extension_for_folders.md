---
title: "Is there an extension for folders?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Mariane on 2010-07-12
I would like to configure my KDE interface so that by default if I click on a folder it is opened by Konqueror and not by Dolphin. Konqueror has a location field at the top which shows the path to whatever it is displaying while Dolphin does not have this. So for example I can type in there ".something" and it will display the contents of the hidden directory .something. 

It is also very useful for backups. I can have 2 Konqueror windows opened showing folders with very similar contents and read right away which is the backup folder - so I don't overwrite a new version with an old one when what I wanted to do was to overwrite the old version with the new one :). 

Finally Konqueror displays remote files and folders in just the same way as it displays local files and folders. 

I know that to say "always open txt files with Kwrite" you have to associate the .txt extension with Kwrite in the Control Panel. But how do I associate folders? Is there a hidden extension to the folder names which says "this is a folder"? 

Mariane

---

### Post by jtarin on 2010-07-12
> Konqueror has a location field at the top which shows the path to whatever it is displaying while Dolphin does not have this.
[Dolphin can be configured to show the full path. ]("http://www.mepis.org/docs/en/index.php/Dolphin#Show_the_full_file_location_path")

---

### Post by Mariane on 2010-07-12
Thank you, that is good to know. If nobody gives me the answer I will do this. 

Mariane

---

### Post by klytu on 2010-07-12
> **Mariane said:**
> Thank you, that is good to know. If nobody gives me the answer I will do this. 

Mariane

In the KDE Menu, System Settings-Default Applications (it's in the Personal section) look at the File Manager section. From there you may choose whatever file manager you want.

From the command line this is as close as I could get to that menu: ```
/usr/bin/systemsettings -caption "System Settings" -icon preferences-system
```

---

### Post by Mariane on 2010-07-12
Thank you very much! 

On my configuration it was:
Start button
System
System settings
Default applications
File manager

Mariane

---

