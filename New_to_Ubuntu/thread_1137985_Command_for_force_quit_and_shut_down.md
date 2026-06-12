---
title: "Command for force quit and shut down?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by zzzonked on 2009-04-26
So I wanted to create a launcher to force quit applications whenever I need to, may I know what's the command for force quitting an application?

Also, I wanna create another launcher for that popup window to appear, asking me if I want to shut down/restart/hibernate/etc. May I know what the command for this is?

Thanks.

---

### Post by me.translucent on 2009-04-26
for killing a process the command is killall process_name.
and for shutting down your system the command is shutdown -h now
if you want to shutdown after a specific time 10 mins for instance you can write 
shutdown -h 10
but for the shutdown command you need root privilege.

---

### Post by gn2 on 2009-04-26
Right click on a panel, select Add to Panel, and select Force Quit.
Now when you need to force an application to close, click on the panel icon then click on the application.

Same for Quit.

To force a shutdown, press Ctrl+Alt+Backspace then at the bottom left corner click Options, then select shutdown.

No terminal required ;)

---

### Post by zzzonked on 2009-04-26
> **gn2 said:**
> Right click on a panel, select Add to Panel, and select Force Quit.
Now when you need to force an application to close, click on the panel icon then click on the application.

Same for Quit.

To force a shutdown, press Ctrl+Alt+Backspace then at the bottom left corner click Options, then select shutdown.

No terminal required ;)

Yeah I know that :) Thing is, I wanna get rid of the panel completely. I'm moving everything to awn. I've just discovered the command for the shut down popup is gnome-session-save --kill, so I've created a launcher for that already. Now I need to know what the command for force quitting is :)

---

### Post by VCoolio on 2009-04-26
You can make a launcher with the command
xkill
Clicking it will make your cursor like x, clicking on a window will kill it.

---

### Post by beachwood23 on 2009-07-20
> **VCoolio said:**
> You can make a launcher with the command
xkill
Clicking it will make your cursor like x, clicking on a window will kill it.

Thanks, this helped me too!

---

### Post by ~sHyLoCk~ on 2009-07-20
```
killall appname

pkill processname

kill processID
```

---

### Post by hariks0 on 2009-09-14
In commands of CompizConfig Settings Manager or Ubuntu Tweak, I use 

Super+r for "gnome-terminal" 
super+e or "nautilus ~" [or "nutilus /" if you want to open the root "/"]
super+l for "gnome-session --logoff-dialog"
super+delete for "xkill" etc

One can make launchers for these too. Please refer

[http://ubuntuforums.org/showthread.php?t=891922&page=2](http://ubuntuforums.org/showthread.php?t=891922&page=2)

for more info.

---

