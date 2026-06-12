---
title: "Firefox goes into full screen"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by bsmith52 on 2009-07-12
I must have changed a setting without realizing it. Whenever I get into Firefox, it goes into full screen mode.  In order to access the top gnome(?) panel (with Applications, System, etc.), I need to click on Edit-Preferences (nothing happens), then Edit-Preferences (again!) - Preferences screen appears - the top panel appears. I close it. I can access my applications.  Then as soon as I access Firefox again, I go back into full screen mode again.

I have tried just about every combination of Firefox Preferences.  None seem to have an impact.

Thanks for your help for this novice user.

Bill

---

### Post by mevets on 2009-07-12
Are you sure its fullscreen mode. Because everyone once in a while I will run into a bug where firefox loses it window borders and so it is streched over gnome-panel. This look different than firefoxs fullscreen mode. To fix the problem I always back my .mozilla folder and rename it so firefox gives me a new profile. You will lose all your settings if you do this though.

---

### Post by earthpigg on 2009-07-13
press f11?

---

### Post by xyphur on 2009-07-13
2nd, F11

---

### Post by bsmith52 on 2009-07-13
Pressing f11 gets me the top screen with Applications, Places, etc.  But it replaces the toolbar with my Refresh icon, etc with a message "[ubunto] Firefox goes into full screen - Ubuntu Forums - Mozilla Firefox" 

This gives me the top toolbar (Applications, etc), and my boxes with the open applications; as well as my sanity.  Thanks.

Will I need to clear out my .mozilla folder in order to get back to "normal"

Thanks for your help,
Bill

---

### Post by xyphur on 2009-07-13
...shouldn't need to, as from what I gather Firefox remembers it's last window state, so it should now remember to remain windowed instead of full screen on the next restart of the browser process.

...which is what I imagine was happening before. You simply managed to get around it by opening the preferences dialog, which apparently cannot co-exist with the browser while it's in full screen mode, so perhaps it forces a fall-back to windowed mode to allow display of that dialog.

Anyone else care to 2nd my hunch?

---

### Post by lovinglinux on 2009-07-13
See **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

---

