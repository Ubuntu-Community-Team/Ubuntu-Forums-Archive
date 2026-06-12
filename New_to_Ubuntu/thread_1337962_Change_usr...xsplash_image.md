---
title: "Change usr/.../xsplash image"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by isee on 2009-11-25
Hello!

I don't seem to have privileges in my /xsplash folder.  I'd like to rename usr/share/images/xsplash/bg_2560x1600.jpg, and move ~/Backgrounds/bg_2560x1600.jpg into /xsplash.

I believe this will change my splash screen image to match my desktop.  I've managed to change my GDM screen using gnome-control-center at the GDM screen, so this would make them all consistent.

I have only used the File Browser to try this, as I am noob and don't know any terminal commands.

Anybody help with the commands please?

---

### Post by wojox on 2009-11-26
```
gksudo nautilus
```

Now your in your file browser as root. Be Careful.

---

### Post by zeroseven0183 on 2009-11-26
Hi! I found a comprehensive HowTo article in changing xsplash: [http://ubuntuforums.org/showthread.php?p=8378244](http://ubuntuforums.org/showthread.php?p=8378244)

The second portion includes the command on how to change the background.

Hope that helps.

---

### Post by zeroseven0183 on 2009-11-26
> **wojox said:**
> ```
gksudo nautilus
```Now your in your file browser as root. Be Careful.

I was also thinking of giving this command but hesitated.

Anyway, it would be better if isee could have a backup of the original xsplash background in case anything bad happens.

---

### Post by isee on 2009-11-26
Thanks much!

Thats an excellent guide!  I like the idea of using Firefox from the GDM.

wojox how do I exit nautilus when I am done?

---

### Post by isee on 2009-11-26
OK well nautilus worked well, got what I wanted done with some success.  Just a matter of image scaling as the transitions are a little off.

Thanks again!

---

