---
title: "Is there a &quot;Cntrl-Alt-Del&quot; Task Manager - like thing for Ubuntu?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by oingk on 2010-03-10
I'm new to Ubuntu, and I tried to log in to my msn account via ebuddy, when my computer crashed.

It's screen went all black and just stayed like that until I forced-shutdown by pressing my computer's shut down button.

Now I managed to start it again.

What should I normally do in situations like these?

In Windows if it crashes there's a hope if you press Contrl+Alt+Delete, where you can stop processes from Task Manager.

Is there something similar to Ubuntu, or is the normal way to shut down using the computer's shut-down button whenever it crashes?

---

### Post by steve-shinn on 2010-03-10
System>System Monitor

---

### Post by Method X on 2010-03-10
or just use command *top* in terminal or console.

You will see every process and you can kill it with pushing k button, and typing its PID number. Very useful.;)

---

### Post by oingk on 2010-03-10
What should I do in cases when I can not access this? i.e. in cases when my computer screen goes all blank or shows me things that I don't understand?

---

### Post by doas777 on 2010-03-10
CAD will open the shutdown options menu, so you can shutdown from there. if you want to start a new tasks, use Alt+F2 and enter your command.

I use the system monitor applet for my gnome panels so I can see the utilization at a glance. since it's there, if I double click on it, it launches the system monitor app, and I can kill processes from there. 

if all else fails I hit ctrl+Alt + F1 and login to a virtual terminal, and kill a process with :"
```
sudo killall <processname>
```

---

### Post by 2hot6ft2 on 2010-03-10
> **oingk said:**
> I'm new to Ubuntu, and I tried to log in to my msn account via ebuddy, when my computer crashed.

It's screen went all black and just stayed like that until I forced-shutdown by pressing my computer's shut down button.

Now I managed to start it again.

What should I normally do in situations like these?

In Windows if it crashes there's a hope if you press Contrl+Alt+Delete, where you can stop processes from Task Manager.

Is there something similar to Ubuntu, or is the normal way to shut down using the computer's shut-down button whenever it crashes?
If it's an application that freezes you can open a terminal and use
```
top
```
that will show you what's running and you can use
```
sudo killall appsnameintop
```
to kill it
ctrl+alt+del will reboot ubuntu.
You can also right click on the top panel and choose add to panel and add Force Quit then you will have an applet on the panel you can click on then click on the apps title bar that's acting up to force it to close.

---

### Post by oingk on 2010-03-10
> **doas777 said:**
> CAD will open the shutdown options menu, so you can shutdown from there


What's CAD?

---

### Post by Grenage on 2010-03-10
**C**ontrol **A**lt **D**elete ;)

---

### Post by beany1 on 2010-03-10
hes said twice - when the screen goes all black, as in no click buttons/gui/nothing! lol, if you cant type/click yeah hold down power button, or try switching between things lol i dont know what there called using ctl alt and the F keys should give you console access if the computer hasn't completely died then you can use the mentioned commands

---

### Post by marshmallow1304 on 2010-03-10
If all else fails, there is a method that is better than holding down the power button.
[http://lifehacker.com/298891/gently-restart-a-frozen-system](http://lifehacker.com/298891/gently-restart-a-frozen-system)

---

### Post by Morrad on 2010-03-10
Top and the gnome system monitor won't help him if his monitor is black.

What you can do is switch to a terminal session with ctrl-alt-F1, log in, and then use top to see what is frozen and do what these guys are suggesting by killing the program.

If this doesn't work, sometimes restarting the X server by hitting ctrl-alt-backspace in your frozen black screen (press ctrl-alt-F7 to get back to it) will work, but you will loose the stuff you were working on.  Also, I think by default Ubuntu has that option turned off, and I forget how you enable it easily.

---

### Post by marbertone on 2010-03-10
Try also CTRL+ALT+BACKSPACE , it used to work for me on openSUSE 9 and KDE, I think it'll work also for gnome... (!)
Cheers,
Mario Alberto

---

### Post by Method X on 2010-03-10
> **marbertone said:**
> Try also CTRL+ALT+BACKSPACE , it used to work for me on openSUSE 9 and KDE, I think it'll work also for gnome... (!)
Cheers,
Mario Alberto

It's no Ctrl+Alt+Del now, its Alt-shift-prinscreen(or sysreq)-k from now

---

### Post by 2hot6ft2 on 2010-03-10
Yeah I meant to mention something about crtl+alt+backspace but got diverted by the task manager part of the question and spaced out on the black screen part. Old Timers is running high today..that's my excuse and I'm sticking with it.

---

### Post by sandyd on 2010-03-10
hold down alt-printscreen while pressing r e i s u b (one at a time)

---

### Post by oldsoundguy on 2010-03-10
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key) .... a good read.

ctrl/alt/bkspace will soon be a dead keyboard combination.

I use (right of the spacebar)Alt/SysRq/(the letter)k to kill all and sign back in when I have no desktop.  Otherwise I have a force quit applet in the panel for a single application.

---

### Post by oingk on 2010-03-10
OK I tried contr-alt-F1 and go to this place, which I guess you call the console. There, I type top and press Enter, I see my processes, I press k, I chose the PID number I want to kill, but then it asks me something that I forgot, even if I tried so hard to memorise.

But anyway, I didn't know what to say but also I didn't know how to come back to desktop so I Control-Alt-Del to restart.

When I'm in Console, how can one return to desktop?

---

### Post by marshmallow1304 on 2010-03-10
> **oingk said:**
> When I'm in Console, how can one return to desktop?

Ctrl+Alt+F7

---

### Post by oingk on 2010-03-10
> **carlee said:**
> hold down alt-printscreen while pressing r e i s u b (one at a time)

This works fine and seems useful.

---

### Post by oingk on 2010-03-10
thanks.

So in console, when I press k and type a PID number (say 1925), it sais:
[FONT=Lucida Console][B]
Kill PID 1925 with signal [15]:[/B][/FONT]

In which case what should I answer to kill the process?

---

### Post by doas777 on 2010-03-10
> **oingk said:**
> thanks.

So in console, when I press k and type a PID number (say 1925), it sais:
[FONT=Lucida Console][B]
Kill PID 1925 with signal [15]:[/B][/FONT]

In which case what should I answer to kill the process?
I don;t tend to kill within top, but I would imagine it's looking for 'y'

---

### Post by oingk on 2010-03-10
> **doas777 said:**
> 
if all else fails I hit ctrl+Alt + F1 and login to a virtual terminal, and kill a process with :"
```
sudo killall <processname>
```


How do I log-in to a virtual terminal from console?

---

### Post by oingk on 2010-03-10
> **doas777 said:**
> I don;t tend to kill within top, but I would imagine it's looking for 'y'

Yes that's right. So that works.

---

### Post by doas777 on 2010-03-10
> **oingk said:**
> How do I log-in to a virtual terminal from console?
you're already there. VTTYs (virtual touch tone yoke or virtual teletypewriter) are the command line terminals available with Ctrl + Alt F(1-6). as someone pointed out, F7 is your desktop TTY.

---

### Post by oingk on 2010-03-10
OK so in summary, the things I can try are:

-Control-Alt-Del to go to shutdown menu.

-Control-Alt-F1 to go to console, type "top" to see processes, press "k", type PID number of process to kill, type "y", press Control-Alt-F7 to go to desktop.

-Click on the force-quit icon that I added thanks to that guy's suggestion, which lets me kill a process.

-Alt-Printscreen-r e i s u b which restarts my computer.

Among some other things you said that I'm still processing in my mind.

Thanks to all for your help.

---

### Post by doas777 on 2010-03-10
you've got a good attitude and  approach to learning this stuff. you'll go far.

---

### Post by J V on 2010-03-10
I tend to map system monitor to ctrl shift esc, and xkill to ctrl alt x

```
gconftool-2 --type string --set /desktop/gnome/keybindings/custom10/action "gnome-system-monitor"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom10/binding "<Shift><Control>Escape"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom10/name "System monitor"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/action "xkill"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/binding "<Control><Alt>X"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/name "Kill Application"
```

---

### Post by oingk on 2010-03-10
O:) Thanks! I hope I do.

---

### Post by juanoleso on 2010-03-10
> **J V said:**
> I tend to map system monitor to ctrl shift esc, and xkill to ctrl alt x


Gonna do this when I get home.

thnx

---

