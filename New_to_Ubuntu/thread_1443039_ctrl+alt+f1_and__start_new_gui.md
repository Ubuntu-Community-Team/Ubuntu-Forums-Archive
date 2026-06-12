---
title: "ctrl+alt+f1 and  start new gui"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-03-30
i was wanting to know if i press ctrl + alt + f1 to get the command line how do i use it to strat another gui. I know that if i use ctrl +alt +f7 i can have the gui i started with but how do i start anoterh one?

---

### Post by aikiwolfie on 2010-03-30
Why would you want to have two desktop sessions running?

---

### Post by aikiwolfie on 2010-03-30
I found the following link with a quick Google.

[http://www.tuxfiles.org/linuxhelp/multiple-x.html]("http://www.tuxfiles.org/linuxhelp/multiple-x.html")

Ctrl+Alt+F8 in Ubuntu is being used for outputing some error logs or some such. If you use the command startx -- :1 in any of the first 6 virtual terminals, it does seem to work. Although I did run into issues with the USB keyboard. Which then crashed X.

I think there is a way to do this from the Gnome. Have a look at the Display properties or some such.

---

### Post by yetiman64 on 2010-03-30
> **lance bermudez said:**
> i was wanting to know if i press ctrl + alt + f1 to get the command line how do i use it to strat another gui. I know that if i use ctrl +alt +f7 i can have the gui i started with but how do i start anoterh one?

Is this question in regard to a locked up desktop perhaps? (gdm - graphical display manager frozen)

---

### Post by aikiwolfie on 2010-03-30
Check out tip 46 here [http://blog.vault9.net/open-source/50-amazing-ubuntu-tips/]("http://blog.vault9.net/open-source/50-amazing-ubuntu-tips/")

---

### Post by lance bermudez on 2010-03-31
yes the desktop locked up and i had to go to ctrl + alt + f1 to get a command line to enter sudo shutdown -r now to restart computer. firefox downloading videos with open tabs sometimes lockup firefox. after firefox locks up it sometimes will cause the computer to lock up. besides runing firefox i sometime have vlc or mplayer running also

---

### Post by undecim on 2010-03-31
the command "sudo service restart gdm" will usually reset a locked-up desktop.

It won't save any of your unsaved work though.

---

### Post by yetiman64 on 2010-03-31
When the desktop locks up by all means use CTRL + ALT + F1. At the black tty1 sceen enter your username then password. You will end up with a command prompt, then use 

```
sudo service gdm restart
```Enter your password again.

This restarts the graphical display manager and sends you to a login on tty7 (what you'd see on a normal login). Any programs like firefox etc will have been shutdown and will have to be restarted of course.

Hope this will help next time, I've had to use this myself a few times.

---

### Post by Chuck_N on 2010-05-01
[COLOR=Red]> **yetiman64 said:**
> When the desktop locks up by all means use CTRL + ALT + F1. At the black tty1 sceen enter your username then password. You will end up with a command prompt, then use 

```
sudo service gdm restart
```Enter your password again.

This restarts the graphical display manager and sends you to a login on tty7 (what you'd see on a normal login). Any programs like firefox etc will have been shutdown and will have to be restarted of course.

Hope this will help next time, I've had to use this myself a few times.[/COLOR]   

okay, thanks.
this thread has too many entries over too long a time. Time has been mostly my fault.  Now that I read this, I've copied it down and will try to apply it next time I freeze up.  It has been freezing less often since I tripled Ram by installing 512M more ram.   -chuck

---

### Post by Chuck_N on 2010-05-01
> **Chuck_N said:**
>    

okay, thanks.
this thread has too many entries over too long a time. Time has been mostly my fault.  Now that I read this, I've copied it down and will try to apply it next time I freeze up.  It has been freezing less often since I tripled Ram by installing 512M more ram.   -chuck

okay I froze up.   I tried  ctrl-alt-F1  and it did nothing.

I tried ctrl-alt-F1 later on , with the computer running, and I got to the command prompt okay.

---

