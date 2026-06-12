---
title: "Device Manager for 11.04"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by sheshan123 on 2011-08-03
I need to disable my laptop's keyboard and touchpad as I have replaced them with external ones. They are malfunctioning so is it safe to disable them? Will the laptop experience any problems with them disabled? And, in order to disable them, can you recommend a good and easy-to-use software such as the default device manager in windows? It would be of great help. Ty! :guitar:

---

### Post by skatinjj on 2011-08-03
> **hawthornso23 said:**
> Try 

```
xinput --list
```

See if you can spot the input device you want to enable or disable. You should then be able to turn it off and on with code like

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0 
```  

and


```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1 
```


If you get it to work then simply set up keyboard shortcuts with those commands.

Quoted from, [http://ubuntuforums.org/showthread.php?t=1789365]("http://ubuntuforums.org/showthread.php?t=1789365")

---

### Post by skatinjj on 2011-08-03
Sorry, all ran from the terminal =)

---

### Post by sheshan123 on 2011-08-03
This may work but I'm not quite sure about the name of the devices. Isn't there a much easier way, maybe a software with GUI and easy disable and enable. And one more thing, after disabling the device, will it still continue to consume power and maybe start up when the pc is turned on?

---

### Post by skatinjj on 2011-08-03
If you disable it through the OS, it will be on until the OS tells it to turn off.

You can check your BIOS settings to see if there is an option to disable them.

As for a GUI interface, I do not know.  I use CLI 80% of the time I am on my PC at home and I am at work so I can't go poking around my desktop.

---

### Post by sheshan123 on 2011-08-03
lol, ty anyways. I'll try my hand on the codes. :)

---

### Post by skatinjj on 2011-08-03
If you can't get it working with the codes, I am still here or there are plenty of other experienced people floating around here that may have an answer

---

