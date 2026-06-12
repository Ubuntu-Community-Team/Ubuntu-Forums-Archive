---
title: "welcome message"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Hari. on 2009-07-25
I would like to greet the user whomever logs into the system(not shell) by using a shell script.
It wolud be great if someone also guides me how to display  the welcome message on a pop window at 
the system start up
i started  writing shell scripts recently and administrating system very recently,so please help me

---

### Post by VCoolio on 2009-07-25
If you mean a black notification window on the top right of the screen you can make a startup script like 
```
sleep 10 && notify-send -i /path/to/icon "Title here" "Message here"
```

If you want a window (which then needs to be clicked away) you can install zenity and use that:

```
sleep 10 && zenity --info --text="Message here"
```

In both cases you can get the username by `whoami`. That is with the quotes that are usually on the ~ button. You could also use $(whoami). So as a message do "Welcome to Ubuntu, `whoami`.
Just add the script to startup applications and you're done. If you don't want to do that for every user check ~/.config/autostart, you can make a .desktop file and for every user put it in that folder, or just put it in /etc/xdg/autostart/.

---

