---
title: "cannot access files using file browser or commander"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by rhenium3 on 2009-07-20
So I can access folders in terminal. But file browser and commander crash when I try to open them. File browser works for my external hard drive. The background does not work, everything else is functional.

No idea how this happened, my friend was just sending me files over Skype, which save in the home folder.

please help!

---

### Post by Tman5293 on 2009-07-21
Try using synaptic package manager to reinstall your file browser.

---

### Post by rhenium3 on 2009-07-21
there are a bunch of programs when I type in "fiel broswers", so which one do I reinstall? And do I need to reinstall Gnome Commander as well?

---

### Post by cariboo on 2009-07-21
If you are running gnome, look for nautilus, for kde search for dolphin.

---

### Post by rhenium3 on 2009-07-21
ok, no, didn't work :(

---

### Post by jeppewinther on 2009-07-21
Wonder what causes this.

Tried a full update?

```
sudo apt-get update
sudo apt-get upgrade
```

If that doesn't work, all I can think of is to purge the program,
```
sudo apt-get remove --purge nautilus
```remove the settings folder in your home library ```
rm -r /home/<User>/.nautilus
``` and reinstall it.
```
sudo apt-get install nautilus
```

---

### Post by rhenium3 on 2009-07-21
no idea what caused this, a friend was just sending files via skype... I updated to the new ubuntu (pretty) and it works fine now :) (when I say I I mean I took my laptop to work and got the IT guys to update ubuntu for me. They make me lazy ;) )

---

### Post by jeppewinther on 2009-07-21
Haha, well working is working.

Hope you don't have to go down that road again.

---

