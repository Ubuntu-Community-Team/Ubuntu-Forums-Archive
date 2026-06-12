---
title: "trash bin disappeared"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Kid Charlemagne on 2009-03-22
I'm running Ubuntu 8.04. My trash bin vanished. I was able to manually put a trash bin icon on the task bar, but an icon for trash is no longer in places or desktop. Is there a way to get the trash icon back on places?

---

### Post by drs305 on 2009-03-22
If your desktop hasn't been disabled, you should be able to get the icon back on the desktop with:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible 'true'
```

***Edited and expanded in response to post #5:***
This command will automatically place the correct value in gconf-editor's settings without having to open the editor and do it manually. 

The instructions in the following post will open the gconf editor tool, and allow you to use a gui app to explore and change all the settings by navigating through the various levels.

---

### Post by leonardo_neo on 2009-03-22
If you want trash icon on your panel......

Right click on some empty space on your panel--->Add to panel--->select trash

If you want trash icon on your desktop............

press alt+f2----> type gconf-editor---->apps----->nautilus---->desktop--->select trash_icon_visible

:)

---

### Post by blandman3 on 2009-03-22
or just drag and drop, it seemed to work on mine!

---

### Post by Kid Charlemagne on 2009-03-23
Thanks. I'm getting conflicting advice about what code to use. Are you sure on yours?

---

### Post by mvalviar on 2009-03-23
> **leonardo_neo said:**
> If you want trash icon on your panel......

Right click on some empty space on your panel--->Add to panel--->select trash

If you want trash icon on your desktop............

press alt+f2----> type gconf-editor---->apps----->nautilus---->desktop--->select trash_icon_visible

:)

Follow this one. 

drs305's code is meant issued on a terminal. You can also copy and paste it in a terminal (Ctrl-Shift-v to paste to terminal). Both are actually correct.

---

### Post by Kid Charlemagne on 2009-03-23
No luck with drs305's code. So I followed leonardo's instructions, but the trash bin icon was already checked as visible. Do I need to follow any other procedure to restore the icon?

---

### Post by drs305 on 2009-03-23
If you ran the command I posted it would have put the tick in the checkbox that you saw with leonardo_neo's instructions, if it wasn't there to begin with.

You could try to reinstall gnome-applets if you are running out of ideas:
```

sudo apt-get update && sudo apt-get install gnome-applets

```

You do have other icons on the desktop, don't you?

---

### Post by karlr42 on 2009-03-23
The fact it's not in the Places menu either seems to indicate the Trash folder has actually been deleted

---

### Post by Kid Charlemagne on 2009-03-23
The only icon I see on the desktop is a Dell contract, but I don't think there were any other icons besides this and the trash bin to begin with. It's a new computer. The trash folder is present, it's just the icon that disappeared. The trash bin icon I put on the taskbar works fine. Thanks.

---

### Post by Kid Charlemagne on 2009-03-24
Should I just paste that command code into the terminal to reinstall gnome-applets? Will it affect anything else?

---

### Post by drs305 on 2009-03-24
> **Kid Charlemagne said:**
> Should I just paste that command code into the terminal to reinstall gnome-applets? Will it affect anything else?

The command will reinstall the gnome-applets, which is a collection of small apps. It won't delete configuration files or affect other settings. 

You can see some of the applets contained by highlighting it in synaptic, right click and select Properties, and selecting the Description tab.

---

### Post by Kid Charlemagne on 2009-03-24
I switched desktop modes from Dell Desktop to Classic Desktop and noticed the Trash Bin icon is on the Classic Desktop. Do you know if there is a way to just move it to the Dell screen?

---

### Post by Kid Charlemagne on 2009-08-22
I tried this code and it said invalid operation update.

---

### Post by drs305 on 2009-08-22
> **Kid Charlemagne said:**
> I tried this code and it said invalid operation update.
Try it again. Typo...
```
sudo apt-get update && sudo apt-get install gnome-applets
```

---

### Post by Kid Charlemagne on 2009-08-24
I tried again and it said newest applets already installed.

---

### Post by drs305 on 2009-08-24
Kid,

I am not familiar with the Dell Desktop. You might try looking in gconf-editor to see if a section on Dell has been added. The standard ubuntu trash icon setting is controlled in gconf-editor's /apps/nautilus/desktop/trash_icon_visible

You could open gconf-editor ('gconf-editor') and do a search for "trash_icon": Edit, Find, Search For: trash_icon  (or trash) and also tick "Search also in key names". That *might* turn up something.

I spent some time trying to find an answer to your request but wasn't successful. For windows, you restore the trash icon by right clicking the Desktop, View, Show Desktop Icons - I don't know what Dell has done in Ubuntu.

Hope someone using the Dell Desktop can provide you with an answer.

---

### Post by Kid Charlemagne on 2009-08-26
Thanks for all your help. Actually I am running Ubuntu 8.04 on a Dell mini Inspiron 9. It is a netbook, sometimes also called an Inspiron 910.  I'm not sure how to follow your last set of instructions. Should I just enter that code into the terminal?

---

### Post by Kid Charlemagne on 2009-08-26
Thanks for all your help. Actually I am running Ubuntu 8.04 on a Dell mini Inspiron 9. It is a netbook, sometimes also called an Inspiron 910. I'm not sure how to follow your last set of instructions. Should I just enter that code into the terminal?

---

