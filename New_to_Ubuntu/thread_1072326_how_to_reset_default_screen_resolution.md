---
title: "how to reset default screen resolution"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by jrandolph on 2009-02-17
I need to know how to reset the screen resolution to default from recovery mode -
New install of 8.10 and i accidently picked the wrong resolution and when i log in all i get is a black screen

---

### Post by jrandolph on 2009-02-17
Sorry but - bump - please

---

### Post by crho85 on 2009-02-17
you could always try editing your xorg file (if you feel comfortable with that)

If you feel up to the task just let me know

---

### Post by jrandolph on 2009-02-17
Well i would be up to it but i think i tried that and i said i could not edit it - ie. permission denied
but if u can help then by all means lets do it

---

### Post by Metallion on 2009-02-17
First make a backup of the file by opening a terminal and typing this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now you can edit the file by typing this:

```
sudo gedit /etc/X11/xorg.conf
```

If something goes wrong you can put the backup back this way:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Could you post the contents of the file here too? Maybe we can give you some specific instructions for adding resolutions to it.

---

### Post by jrandolph on 2009-02-17
I would imagine the part of the file u want displayed is the screen section but i cant copy and paste cuz i am on my mobile 
- if i add in 
Modes     what resolution should i put in

---

### Post by crho85 on 2009-02-17
> **jrandolph said:**
> I would imagine the part of the file u want displayed is the screen section but i cant copy and paste cuz i am on my mobile 
- if i add in 
Modes     what resolution should i put in

here is an example of the screen portion of xorg:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        [B]SubSection "Display"
               Modes             "1024x768"[/B]
        EndSubSection
End Section
```

i set my res at 1024x768, but you can use whatever resolution you would like. it can also accept multiple ones

---

### Post by jrandolph on 2009-02-17
so after editing it to look like that i presume i save and exit?

then what?

---

### Post by Metallion on 2009-02-17
After editing you can press alt + control + backspace to restart X. If you did something wrong, the X server might not start and you won't have your GUI at all. If that happens, just reboot the computer, choose recovery mode from the grub menu and use the command I posted for putting the backup back.

---

### Post by jrandolph on 2009-02-17
Still nothing on startup - going to do another install - didnt have anything on it anyway due to the fact that i just nuked my hd anyway - thanks for the help anyway

---

