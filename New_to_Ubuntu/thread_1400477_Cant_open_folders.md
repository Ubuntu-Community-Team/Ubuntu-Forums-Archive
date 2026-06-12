---
title: "Cant open folders"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by LazyPony on 2010-02-06
Hey I'm fairly new, but Im pretty sure this is'nt supposed to be going this way,.
Whenever i select an icon in Places>... my screen will go grey, pop back to normal and nothing will have opened. Although, Places>Search for files, works just fine. I can make folders using "mkdir" command in the terminal. I have dwlded the WoWtrial version and everything goes just fine accept for pathing. It opens a window to let me select a file but nothing works. I mean no paths are accepted. Ive checked out a forum on here that said to make a folder but i cant open home folder to make that folder although I have the folder that was made through the terminal, but that path is not accepted either. Or i dont know how to find the wow installation file to copy the items in the folder and make another. Any suggestions? 
"walkthroughs greatly appreciated" :)

---

### Post by warfacegod on 2010-02-06
Applications> Accessories> Terminal:

```
nautilus
```

That won't fix the problem but it should get you into your folders.

---

### Post by LazyPony on 2010-02-06
(nautilus:25201): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
???

---

### Post by warfacegod on 2010-02-06
```
sudo apt-get purge nautilus

sudo apt-get install nautilus
```

---

### Post by LazyPony on 2010-02-06
will  have to access my folders through the terminal? or will it be accessable through Places>?

---

### Post by NCLI on 2010-02-07
If you run these two commands in the terminal, you SHOULD be able to access them through Places.

---

### Post by LazyPony on 2010-02-07
I ******* love you guys, You made me moist.
You guys happen to know how to install the wow trial version?

---

### Post by NCLI on 2010-02-07
You'll want to install Wine first, just type "Wine" into the search box in the Software Center, then install the version marked "Beta Release." This is important, as the other version doesn't support WoW all the well.

If you find Wine too difficult, PlayOnLinux(Also available in the Software Center) has received much praise, but as I haven't tried it myself, I can't recommend it.

You can find help and advice if you have problems running Windows programs [here]("http://appdb.winehq.org/").

---

### Post by LazyPony on 2010-02-07
aaahh, I have the non beta release, and i have read somthing about having to uninstall the non beta and install the beta then unstalling that and back to the normal one, does that help the whole "Invalid Path" thing?

---

