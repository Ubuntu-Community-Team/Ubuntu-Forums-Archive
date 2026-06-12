---
title: "firefox menu can't be clicked"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by cbbnewbie on 2010-08-23
hello, can somebody help me with my problem please, I'm using firefox but suddenly when i click on links the right click doesnt work eg. on saving images, it works fine in chromium, tried to google it and it said that it may be caused by the yahoo toolbar, and that need to be uninstalled but when i click on the menu _T_ools i can't click it and all the others (Files|Edit etc.) what can i do?? thanks

---

### Post by gcd1094 on 2010-08-24
That sounds pretty weird... You should probably try reinstalling firefox, or maybe just restarting it, that's all I can think of.  Hopefully that works, but if not, then good luck trying to figure it out.;)

---

### Post by lovinglinux on 2010-08-24
Start in safe mode and disable the extension.

```
firefox -safe-mode
```

If that doesn't help, see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by jtarin on 2010-08-24
Duplicate

---

### Post by jtarin on 2010-08-24
In your Gnome terminal issue the command ```
firefox -safe-mode
```Firefox will open a dialogue showing it is safe mode.


> Note: The following changes cannot be undone.
You can elect to make the following changes:

Disable all add-ons: If you select this box and then click Make Changes and Restart then Firefox will start back up in its normal mode, except all your extensions, themes, and plugins will be disabled (not uninstalled).
Reset toolbars and controls: If you select this box and then click Make Changes and Restart then Firefox will start back up in its normal mode, except any toolbar customizations you have made will be lost, such as position of buttons and toolbars.
**Delete all bookmarks except for backups:** If you select this box and then click Make Changes and Restart then Firefox will delete your current bookmarks and replace them with the default set (This item is labeled Reset bookmarks to Firefox defaults in Firefox 3.5).
Reset all user preferences to Firefox defaults: If you select this box and then click Make Changes and Restart then any changes you have made to Firefox's options will be set back to their default settings.
Restore default search engines: If you select this box and then click Make Changes and Restart then any of the default search engines you deleted will be restored.

---

### Post by it_fixxer on 2010-09-05
@jtarin

firefox -safe-mode

Reset toolbars and controls: If you select this box and then click Make Changes and Restart then Firefox will start back up in its normal mode, except any toolbar customizations you have made will be lost, such as position of buttons and toolbars. 

FYI...worked after starting in safe mode
Tkx

---

