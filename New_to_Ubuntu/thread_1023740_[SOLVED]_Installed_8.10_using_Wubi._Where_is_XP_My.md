---
title: "[SOLVED] Installed 8.10 using Wubi. Where is XP My Documents?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2008-12-28
I need to access my Windows XP folders in order to retrieve emails for Thunderbird. How can I make the folders appear?

Thanks

---

### Post by appi2012 on 2008-12-28
Go to Places -> and click on the hard drive that isn't "filesystem" or a usb drive. That should mount the drive, and add a link on your desktop. Now you should be able to access the files.

---

### Post by northern lights on 2008-12-28
I'm not 100% sure how Wubi-installs manage devices, as I never used it, but you can screw anything up if it isn't 100% equivalent, so do the following, if it doesn't appear under "Places" in the panel:

Open a Terminal (Applications > Accessories > Terminal) and run```
sudo mkdir /mnt/XP
sudo mount /dev/sda1/ /mnt/XP/
```

Your Windows drive/partition should now appear in the places menu or be accessible via */mnt/XP/*.

---

### Post by appi2012 on 2008-12-28
TRANQU111TY: both methods will work, one just does it through command line, whereas the other uses the User Interface.

---

### Post by TRANQU111TY on 2008-12-28
> **northern lights said:**
> I'm not 100% sure how Wubi-installs manage devices, as I never used it, but you can screw anything up if it isn't 100% equivalent, so do the following, if it doesn't appear under "Places" in the panel:

Open a Terminal (Applications > Accessories > Terminal) and run```
sudo mkdir /mnt/XP
sudo mount /dev/sda1/ /mnt/XP/
```

Your Windows drive/partition should now appear in the places menu or be accessible via */mnt/XP/*.

This method worked but I needed to open it up in the dir as it doesn't appear in the Places menu.

Thank you!

---

### Post by northern lights on 2008-12-28
> **TRANQU111TY said:**
> This method worked but I needed to open it up in the dir as it doesn't appear in the Places menu.
You can't manually edit places, but you could, if you access it often, create launcher in the panel.

If you want to do so, right-click the panel and choose "Add to panel..." and seubsequently "Custom Application Launcher". Pick a name of your choice and in the "command" box type ```
nautilus /mnt/XP/Documents\ and\ Settings/YOURWINDOWSUSERNAME/My\ Documents/
```where YOURWINDOESUSERNAME obviously needs to be replaced by, well, your Windows username. Backslashes denote spaces.

---

