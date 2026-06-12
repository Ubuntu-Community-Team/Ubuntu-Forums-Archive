---
title: "Window Decorator Problem"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-15
I have emerald and compiz enabled.
Works fine until I either log out and back in or restart.
After restart it's back to using Metacity and GTK (Dust theme) instead of emerald, and compiz isn't even enabled.
It just as if compiz fusion and emerald wernt even installed. Yet checking the settings, they are all correct.

emerald --replace is in the compiz settings.
Emerald is selected as the Window decorator.
Window manager is compiz.
But...it's just returned to default.

If I right click the fusion icon and choose "re-load window manager" everything works and is activated.
But the problem occurs once again when I either log out or restart. 

Why arnt the setting sticking, even when it still shows them as being enabled?

---

### Post by NightwishFan on 2009-06-15
You can try using GNOME Session, which is called something like Started Applications in the preferences menu.

Simply add emerald --replace as an autostarted application.

I am quite sure that adding it as the default window manager in compiz settings should work though. Try setting it as /usr/bin/emerald instead of emerald --replace.

---

### Post by Gp. on 2009-06-15
It's not just that.
Even if I choose not to use emerald, the settings in appearance are set to "None" for effects.
I change it to "extra", works, but yet again it changes back to "none" when I log out or restart!
Wth!

The settings wont stay.

---

### Post by NightwishFan on 2009-06-15
Did it always do this?

---

### Post by Gp. on 2009-06-15
Nope, only after I installed emerald.

---

### Post by NightwishFan on 2009-06-15
It should not revert the settings to none. This problem seems to be a bit out of my hands. Perhaps try resetting all compiz settings back to default, if that does not work, try purging Emerald, and see if it fixes the problem. If it does, then try to reinstall it.

---

### Post by CatKiller on 2009-06-15
Just a thought. It's marked as deprecated, but you could try setting /desktop/gnome/applications/window_manager/current and /desktop/gnome/applications/window_manager/default in gconf-editor to /usr/bin/compiz.

---

### Post by Gp. on 2009-06-15
> **NightwishFan said:**
> It should not revert the settings to none. This problem seems to be a bit out of my hands. Perhaps try resetting all compiz settings back to default, if that does not work, try purging Emerald, and see if it fixes the problem. If it does, then try to reinstall it.

Tried resetting to defaults.
I don't get this.

How can I completely remove everything? Compiz, Emerald, all of and start again?
And I mean COMPLETELY remove.

---

### Post by Sarai the Geek on 2009-06-15
> **Gp. said:**
> Tried resetting to defaults.
I don't get this.

How can I completely remove everything? Compiz, Emerald, all of and start again?
And I mean COMPLETELY remove.

```
sudo apt-get remove compiz emerald
```

To reinstall:

```
sudo apt-get install compiz emerald
```

You don't need emerald to run compiz, but you do need compiz to run emerald. So if you don't want emerald, just write compiz instead of compiz emerald when reinstalling.

---

### Post by Gp. on 2009-06-16
Yeah, I know lol and I do want emerald but...I don't get why this issue is happening.
And before in 8.10 I had this issue and I tried to reinstall it all and it did the same thing!
I hope this will fix it, I'll post my results when I get a chance to try some things later.

---

### Post by Gp. on 2009-06-16
Okay well that removal command didn't do its job...

Heres what happened...

```
 sudo apt-get remove compiz emerald
[sudo] password for kyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libiso9660-5 libdvbpsi4 libmatroska0 liblua5.1-0 libemeraldengine0 libtar
  libvcdinfo0 libebml0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz emerald
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1516kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 175504 files and directories currently installed.)
Removing compiz ...
Removing emerald ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

```

Yet, after that, I went to enable Extra effects again, and sure enough, there loads emerald and compiz?
But I thought I just deleted you!!!

---

### Post by b.a.w on 2009-06-16
Just a note if the above doesn't work. I had this same problem. Mine was caused by I guess an incompatibility of Gnome setting desktop effects and then loading fusion-icon during start-up. I would have a composite desktop for about two seconds and then it would revert to Metacity. I was able to solve it by setting the Gnome desktop effects to none and just using fusion-icon to control compiz.

---

### Post by Gp. on 2009-06-16
Sorry for double post XD
But yeah, what should I do because I feel like we are on the same track here with having the icon at startup.

---

### Post by Gp. on 2009-06-16
I also have the icon set to startup.
Thing is, when I choose the settings for the icon, it also changes the value to Extra in appearance...:S

What I did was changed it to non, made sure the settings were correct in the fusion icon then reloaded it, and emerald and compiz are working but the setting has changed back to extra?

---

