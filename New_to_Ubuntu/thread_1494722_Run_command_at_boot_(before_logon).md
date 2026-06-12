---
title: "Run command at boot (before logon)"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Da-Chosen-One on 2010-05-27
This command changes the brightness of my screen:

```
[COLOR="Red"]sudo echo -n 100 > /proc/acpi/video/GFX0/DD04/brightness[/COLOR]
```
100 is the maximum brightness and the command works perfectly. How do I run this script **before** the logon screen? Preferably as soon after boot as I can (obviously after PROC has been sorted out) I have read stuff about '*rc.local*' and '*init.d*', but I don't want to fiddle with stuff I don't understand. I know I can adjust screen brightness once it has logged on but it is for starting a special session (XBMC) which has no brightness controls,(and the logon screen can be hard to read).
Thanks for any help,
Craig

---

### Post by Ozymandias_117 on 2010-05-27
You should be able to put it in /etc/rc.local

---

### Post by Da-Chosen-One on 2010-05-27
I tried putting it in '*rc.local*'. It works perfectly and the screen brightness increases, but just as the logon screen background appears it dims back down. :confused: I am using a netbook and I think it has something to do with that. I experimented a bit and when I am at the grub boot screen, if I plug in to mains the screen goes to 100% brightness, and as soon as I unplug it goes back to 60%(ish). Is there anyway to disable this automated thing? Is there a way to make it run the command when every session is loaded, meaning XBMC. Or to run it once the logon box has appeared? Thanks again,
Craig

---

### Post by ManiDhillon on 2010-05-27
Well that's easy thing. It is due to the power management settings.
When your NetBook is running on battery, power management automatically lower down the brightness to save power.
You can change it in:
System > Preferences > Power Management

---

### Post by Da-Chosen-One on 2010-05-27
> **ManiDhillon said:**
> 
System > Preferences > Power Management
I have 'Dim display while idle' and 'Reduce backlight brightness' both unchecked for battery power but it only has an effect once the GNOME session has loaded, not XBMC. Sorry :-?

---

### Post by ManiDhillon on 2010-05-27
Then I am out of answers dude, as I've never tried that Media Center.
But you should also know that in Laptops/NetBooks if the OS interface has nothing to setup screen brightness than the only way is to increase using the dedicated keys because each Laptop will dim its display on battery to save power.

---

### Post by Da-Chosen-One on 2010-05-27
Aha! Tweaked my bios settings to disable automatic brightness correction. :D Thanks to both of you anyway.

---

