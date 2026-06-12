---
title: "Alt Ctrl Del - Ubuntu equivalant crashing"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by loseby on 2010-02-19
Alt Ctrl Del will bring up task mgr in Windows most times when screen goes blan or some sort of crash but what key combination does something similar in Ubuntu ?

main reason is that my Internet browsers crask quite often to a blank black screen and instead of pressing the reset button on my computer I want to know if there is another way around this ?

btw: installed Chrome and was hoping that woould fix that Firefox crashing but as soon as I maximised it the screen went blank

---

### Post by Electric Bill on 2010-02-19
In Karmic Ctrl Alt Del brings up this -

[IMG]http://newportyachtdirectory.com/Ubuntu_Forums/ShutdownMenu.png[/IMG]

You have 60 sec to decide before it shuts down.

Bill

---

### Post by dondiego2 on 2010-02-19
> **Electric Bill said:**
> In Karmic Ctrl Alt Del brings up this -have 60 sec to decide before it shuts down.

Bill


Same in Gnome.

---

### Post by argos3016 on 2010-02-19
you can make a keybinding in system > preferences > keys or something similar.
Make a new keybinding putting on gnome-system-monitor or xterm -e top or directly an xkill.
BE CAREFUL WITH XKILL!!

---

### Post by argos3016 on 2010-02-19
[URL="http://www.linuxhowtos.org/Tips%20and%20Tricks/sysrq.htm"]http://www.linuxhowtos.org/Tips%20and%20Tricks/sysrq.htm
[/URL]

---

### Post by trikster_x on 2010-02-19
I know exactly what you are going through, I get the same thing on one of my older boxes now and then because of firefox.  If it is just one program hanging and  not a complete system lockup, try opening a terminal and type:

```
killall name-of-misbehaving-app
```

That will force close all running instances of that app.  Love this for when I get a rickroll link from one of my so-called "friends".

If you have a complete lockup, the best thing to try is press and hold "alt+print screen/sysrq" and type "reisub"  this is the safest way to attempt to reboot a non-responsive system.  It basically does everything that shutting down the computer normally would do, only through key-presses instead of a command line or GUI.

Hope this helps :)

---

### Post by argos3016 on 2010-02-19
sudo killall5?

---

### Post by trikster_x on 2010-02-19
> **argos3016 said:**
> sudo killall5?

Probably not the best choice, since it would close any other currently running applications as well, and that could end up causing some major problems unless that was the intention of the user.

---

### Post by Ozymandias_117 on 2010-02-19
ctrl+alt+backspace kills all user processes and ends the session, putting you back to the login screen.

---

### Post by skymera on 2010-02-19
> **Ozymandias_117 said:**
> ctrl+alt+backspace kills all user processes and ends the session, putting you back to the login screen.

I believe  this had changed ti ALT+PRNT SCREEN + K to restart X

---

### Post by San_SS! on 2010-02-19
What I usually do when something crashes, is login in one of the tty(Ctrl + Alt + F1 .. F6).
 and from there list the running processes with 
```

ps aux

```

find the one that's causing problems and kill it with the *kill* command.

After that try to go back to X with Ctrl + Alt + F7 if it is still not responsive just restart the X with Ctrl + Alt + Backspace.

---

### Post by loseby on 2010-02-20
> **Electric Bill said:**
> In Karmic Ctrl Alt Del brings up this -

[IM
You have 60 sec to decide before it shuts down.

Bill

well it doesnt work as the screen remains completely blank but maybe not enough time giving

will try running Chrome again and see what happens when it crashes

---

### Post by hyperdude111 on 2010-02-20
You can add the "Force Quit" applet to the top panel.

---

