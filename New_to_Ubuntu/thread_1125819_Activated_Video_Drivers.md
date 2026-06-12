---
title: "Activated Video Drivers"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Allison720 on 2009-04-14
I unfortunatly activated the Nvida driver after installing Ubuntu.  Once i restarted i lost my gui and could only browse from the command line...how do i get back to my Gui desktop?

thank you in advance

---

### Post by skymera on 2009-04-14
Reinstall the driver but use EnvyNG, 

```
sudo apt-get update
sudo apt-get install envyng-core
sudo envyng -t 
```

Choose option 1, restart and all should be gravy

---

### Post by Allison720 on 2009-04-14
Thank you ! :)

---

### Post by Allison720 on 2009-04-14
i was able to get the update and install it.  when i did ...... sudo envyng -t  i received "list indices must be intergers" ?

it seems the install was ok; however when i restart i am still at the command line.  is there another step?

thank you again!

---

### Post by Lazy-buntu on 2009-04-14
Out of curiosity, what do you get if you run ```
gnome-session
```

---

### Post by Allison720 on 2009-04-14
i get

** (gnome-session:(6278): WARNING **: Cannot open display:

---

### Post by Allison720 on 2009-04-14
ugh

should be

** (gnome-session: 6278)  WARNING ** : Cannot open display:

---

### Post by Lazy-buntu on 2009-04-14
Looks like you're going to have to disable that nvidia driver. I'm not an expert at this so I couldn't tell you how to do that from the command line. Hopefully someone here can help you more than I can ;)

---

### Post by Allison720 on 2009-04-14
wow.. the smily faces are anoying

gnome-session 6278   Cannot open display

---

### Post by Allison720 on 2009-04-14
Thank you ! Lazy buntu

Anyone out there to assist?

---

### Post by glennric on 2009-04-14
To deactivate the nvidia drivers from the command line you will have to edit the file /etc/X11/xorg.conf.  Find the part that looks something like
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

```
and remove the line
```
	Driver		"nvidia"
```

---

