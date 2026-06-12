---
title: "Equivalent of cntrl-alt-del ?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by rng on 2011-06-08
In rare case that an application gets stuck in ubuntu (gui), what is(are) the equivalent(s) of windows control-alt-delete key combination?

---

### Post by marcio_mi on 2011-06-08
it depends, do you want the equivalent of calling up the task manager?

if only the application froze then 
1. you can open system monitor from the menus (or the dash if you're using unity). There you select the process that is frozen and kill.

2. ALT+F4 while on the frozen application should kill it.

If the all graphical user interface is locked then you have several option:
1. ALTGR+SYSR+F should kill the application which is consuming all the memory (if that is the reason why the interface froze)

2. ALTGR+SYSR+K kills the GUI and goes back to the login (also closes all open application, so you lose your work!)

3. CTRL+ALT+F1 takes you to a terminal whatever the state of the graphical interface. from there you can list processes id and kill the one that is creating troubles.

---

### Post by Paqman on 2011-06-08
> **marcio_mi said:**
> ALT+F4 while on the frozen application should kill it.


If this doesn't work you can also hit Alt-F2, type "xkill" and click on the offending window.

---

### Post by LowSky on 2011-06-08
my favorite command is CTRL+ALT+Backspace... you have to enable it from keyboard shortcuts, but what it does is basically Kill X and restarts it.

You will lose any unsaved data, but its great if you don't feel like restarting completely. Very good to apply new hardware settings.

---

### Post by rng on 2011-06-08
Thanks for your replies. A few clarifications please: 

My keyboard does not have ALTGR key- will Control+ALT work?

SYSR key is also not there. Any alternative key combination?

What is the best way to find process that is causing problem and kill it once I get to terminal/konsole?

---

### Post by marcio_mi on 2011-06-08
> **rng said:**
> Thanks for your replies. A few clarifications please: 

My keyboard does not have ALTGR key- will Control+ALT work?

yep, that should do the trick

> SYSR key is also not there. Any alternative key combination?

uhm, I thought it was standard on all keyboards. Don't you have a key with "Print Screen /System Req" somewhere?

> What is the best way to find process that is causing problem and kill it once I get to terminal/konsole?

try typing 

```
top
```

it should give you the necessary information to try to pick the process that it's causing trouble. (using the man page for top will give you more details on the output, type ```
man top
``` press "q" while reading the man pages to get back to the prompt)

---

### Post by marcio_mi on 2011-06-08
reading on the internet I found that some new netbook/notebook models don't have the sysrg key anymore...well, probably useful for windows but not for linux, what about all the magic sysrq keys now? anyway it mentioned there that you can find combination of keys that mimic the sysrq key. what computer model do you have?

---

### Post by rng on 2011-06-08
PrintScreen/SysRq key is there. I had quickly googled images of SYSR and it showed key with penguin image, which I do not have on my keyboard. 

From konsole, I note down PID number in output of 'top' command and type 'kill <pid-number>'

Thanks for your help.

---

### Post by marcio_mi on 2011-06-08
> **rng said:**
> PrintScreen/SysRq key is there. I had quickly googled images of SYSR and it showed key with penguin image, which I do not have on my keyboard. 

From konsole, I note down PID number in output of 'top' command and type 'kill <pid-number>'

Thanks for your help.

great! ):P

---

### Post by rng on 2011-06-08
I just tried to 'enable' from keyboard shortcuts the ctrl+alt+backspace combination, but could not do it properly. Now when I press this combination, I get this error: 

Error while trying to run (Ctrl+Alt+Backspace)
which is linked to the key (<Control><Alt>BackSpace)

Did I mess up something?

---

### Post by jaacko on 2011-06-08
> **LowSky said:**
> my favorite command is CTRL+ALT+Backspace... you have to enable it from keyboard shortcuts, but what it does is basically Kill X and restarts it.

You will lose any unsaved data, but its great if you don't feel like restarting completely. Very good to apply new hardware settings.

I'll just borrow this thread... Could you be more specific on how to enable the command. I really miss ctrl-alt-backspace from the old days.

---

### Post by rng on 2011-06-08
I opened system > preferences > keyboard shortcuts

then I clicked on Add, wrote 'kill x' in name and control-alt-backspace in command. I think I went wrong here. How do I correct this now? I can't find any entry with control-alt-backspace combination now. 

Please help.

---

### Post by Andrethe7th on 2011-08-08
> **marcio_mi said:**
> 

3. CTRL+ALT+F1 takes you to a terminal whatever the state of the graphical interface. from there you can list processes id and kill the one that is creating troubles.

I'm going to bump this thread to ask what the shortcut is to get back to the desktop once you're done with the terminal.

---

### Post by 3rdalbum on 2011-08-08
> **Andrethe7th said:**
> I'm going to bump this thread to ask what the shortcut is to get back to the desktop once you're done with the terminal.

Control-Alt-F7 is usually the terminal that X runs on.

Also, I don't know why people are asking about "re-enabling Control-Alt-Backspace". You can kill X just as easily, and more reliably, by using Alt-Printscreen (SysRq)-K.

It's more difficult to accidentally press, too, so you're less likely to lose data, especially when a Windows user does something on your computer for a minute and decides they need a task manager running.

---

### Post by Andrethe7th on 2011-08-08
> **3rdalbum said:**
> 
Also, I don't know why people are asking about "re-enabling Control-Alt-Backspace". You can kill X just as easily, and more reliably, by using Alt-Printscreen (SysRq)-K.
.
It's probably since it doesn't work on all keyboards.  Like my laptop.
  Thanks for explaining that.

---

### Post by bhadotia on 2011-08-08
> **rng said:**
> I opened system > preferences > keyboard shortcuts

then I clicked on Add, wrote 'kill x' in name and control-alt-backspace in command. I think I went wrong here. How do I correct this now? I can't find any entry with control-alt-backspace combination now. 

Please help.
Remove the above shortcut. Then go to System > Preferences > Keyboard. Click on the Layouts tab. Click on the Options... button at the bottom just above the testing space. Now the Keyboard Layout Options sub-window opens up. Over here you'll find the option for "Key sequence to kill the X server". Enable the shortcut under that and you are done ;) [This is the method I use on my ubuntu 10.04]

---

### Post by bhadotia on 2011-08-08
> **marcio_mi said:**
> 
If the all graphical user interface is locked then you have several option:
1. ALTGR+SYSR+F should kill the application which is consuming all the memory (if that is the reason why the interface froze)

2. ALTGR+SYSR+K kills the GUI and goes back to the login (also closes all open application, so you lose your work!)

Thanks for the info ;)

---

