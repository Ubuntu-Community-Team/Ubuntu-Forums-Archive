---
title: "Firefox help! PLEASE"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-09-18
This is extremely annoying and I can't fix it. It is covering the whole screen. The weird thing is that it is NOT full screened. I checked under the view menu and it's unchecked. then i clicked it and it made it more full screen (taking the menu bar away). I can't see my task bar (I know it's not called that in linux, sorry). Grrrr. I think it's maximized. When I do finally get it back to regular, it's fine (restored). But when I close it and reopen it, it goes back to the default. Grrrr!!! I looked in the preference and don't see anything! Is there a way to reinstall firefox? Is there a fix?

---

### Post by mgranet on 2009-09-18
Press F11 when FF is full screen. You may have it in kiosk mode.

---

### Post by kakashi_12 on 2009-09-18
That didn't change the default though :( I close it and it still goes back to the way it was.

---

### Post by mgranet on 2009-09-18
Perhaps FF is remembering the state from when it's in kiosk.

You might try modifying your profiles.ini file located in ~/.mozilla/firefox (depending on config. It will be somewhere in .mozilla) to read:

```
StartWithLastProfile=**0**
```

May work or may not. Maybe someone else knows how to easily clear the FF config.

---

### Post by oldsoundguy on 2009-09-18
One way to clear it and start again is to do just that.
Uninstall it ... re-boot ... re-install it .. but write down all of your plugs in prior to doing that.  and install xmarks and save your bookmarks on line.

When it is re-installed, bulk install all of your plug ins.

---

### Post by kakashi_12 on 2009-09-18
I don't see where that directory is. ??? is it in etc? or where?

---

### Post by mgranet on 2009-09-18
It's hidden in your home directory. All files or folders that are hidden from view are prefaced with a '.'

I'm not sure how to show hidden files in Nautilus.

---

### Post by sena_akada on 2009-09-18
one of the reasons i stopped using gnome. i had to manually resize it until it stayed. it seemed to happen at random

---

### Post by kakashi_12 on 2009-09-18
I forgot the command to change directories in the terminal

---

### Post by sena_akada on 2009-09-18
if you alt-tab can you minimize firefox?

---

### Post by mgranet on 2009-09-18
> **sena_akada said:**
> one of the reasons i stopped using gnome. i had to manually resize it until it stayed. it seemed to happen at random

Agreed. KDE has a submenu when you right click on the titlebar that allows you to do what ever you please with the windows, including forcing them to sizes and positions.

---

### Post by kakashi_12 on 2009-09-18
Tried that. didn't work

---

### Post by mgranet on 2009-09-18
This will get you to the appropriate directory. You can then list(dir) with 'ls', then 'cd *directory name*' from there:

Open a new terminal.

```
cd /.mozilla
```

---

### Post by kakashi_12 on 2009-09-18
ok, i finally got to the dir and the file. i changed the number to 0. it still didn't do anything :(

---

### Post by lovinglinux on 2009-09-18
See **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

---

### Post by kakashi_12 on 2009-09-18
sorry but that didn't help either.

---

### Post by kakashi_12 on 2009-09-18
No wait. That did help! I closed firefox first, then deleted the file. The solution said to del the file first, then close. I figured i had to do it the other way around, so i did. Thank you all so much ! :) :)

---

### Post by lovinglinux on 2009-09-18
> **kakashi_12 said:**
> No wait. That did help! I closed firefox first, then deleted the file. The solution said to del the file first, then close. I figured i had to do it the other way around, so i did. Thank you all so much ! :) :)

I have changed the text, because it wasn't very clear indeed. Any profile editing or deletion requires to close Firefox first. Thanks for pointing that out.

---

