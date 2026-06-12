---
title: "Ctrl+Alt+Del equivalent in Ubuntu?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by tesseract1 on 2009-07-29
Is there a ctrl+alt+del equivalent in Ubuntu?  Sometimes a program crashes or something hangs.  Is there a process terminator like there is in Windows?

---

### Post by Arup on 2009-07-29
Magic sysreq keys alt+printscreen+r+e+u+i+s+b

---

### Post by jerome1232 on 2009-07-29
ctrl+alt+backspace used to reset the gui but that was disabled. You can always assign a keyboard shortcut to force quit. 

You can hit ctrl+alt+f1 to get a tty, and use kill to kill the process.

---

### Post by l-x-l on 2009-07-29
> **jerome1232 said:**
> ctrl+alt+backspace used to reset the gui but that was disabled. You can always assign a keyboard shortcut to force quit. 


ctrl+alt+backspace has been replaced by Right-Alt + "K" + SysRq (Print Screen)

---

### Post by jmszr on 2009-07-29
tesseract1,

Right click on top panel > click on Add to Panel > Scroll down to System Monitor > Drag and Drop icon in top panel or click on System Monitor and then Add.

To kill processes: Click on System Monitor in top panel > Click on Processes > Click on offending process > End Process.

If screen is frozen this thread's Post #2: [http://ubuntuforums.org/showthread.php?t=1134427](http://ubuntuforums.org/showthread.php?t=1134427)  will explain how to enable Ctrl+Alt+Backspace to restart xserver.

---

### Post by nhasian on 2009-07-29
if an application is frozen and you want to terminate it, another easy way to do it is to press ALT-F2 and enter the command:

```
xkill
```

then click on the application that isnt responding and it will close it.

---

### Post by HotForLinux on 2010-05-25
> **nhasian said:**
> if an application is frozen and you want to terminate it, another easy way to do it is to press ALT-F2 and enter the command:

```
xkill
```then click on the application that isnt responding and it will close it.

This is bad. 
The ESC key should cancel the xkill.
Many problems wouldn't exist if people used to think in how to undo as much as in how to do. 

It is much more important than it seems.

---

### Post by kansasnoob on 2010-05-25
[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

You can enable Ctrl + Alt + Backspace to kill X:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Enabling%20Ctrl-Alt-Backspace%20for%20Ubuntu](http://www.ubuntu.com/getubuntu/releasenotes/1004#Enabling%20Ctrl-Alt-Backspace%20for%20Ubuntu)

---

### Post by wojox on 2010-05-25
> **HotForLinux said:**
> This is bad. 
The ESC key should cancel the xkill.
Many problems wouldn't exist if people used to think in how to undo as much as in how to do. 

It is much more important than it seems.

What? That the same thing as putting the Force Quit applet in your panel. I don't understand why that's wrong.

---

### Post by KdotJ on 2010-05-25
> **nhasian said:**
> if an application is frozen and you want to terminate it, another easy way to do it is to press ALT-F2 and enter the command:

```
xkill
```

then click on the application that isnt responding and it will close it.

+1
I liked the skull and cross bones you can get lol

---

### Post by HotForLinux on 2010-05-26
> **wojox said:**
> What? That the same thing as putting the Force Quit applet in your panel. I don't understand why that's wrong.

"Force Quit" is better designed because it is easy to discover how to cancel the killing procedure, that it launches, quite easily: ESC or click in a window title bar. Clicking in a window bar to cancel the operation is easy to do but not to discover. It is not the best design until you discover it. Esc is a more logical solution. The best thing would be to have a little message that says "Press ESC to cancel". Simple programes have to be designed in an easy to understand and learn way. If you have to read manuals or know in advance how they work... bad.

"Force Quit" does almost the same as an xkill launcher in the panel, except that esc cancels the killing procedure and the cursor has another shape. Therefore, instead of two there should be only one program that does that. It is bad to have all the programs duplicated just because one is already oin your panel... etc...

---

### Post by Excedio on 2010-05-26
I did a nice keybind. Ctrl+Alt+Page_Down opens gnome-system-monitor

Works wonders. :-)

---

### Post by pzkfw on 2010-05-27
[http://ubuntuforums.org/showthread.php?t=1135994&page=2](http://ubuntuforums.org/showthread.php?t=1135994&page=2)

> **pzkfw said:**
> This was one of my biggest problems when I switched  over to Linux.  A full screen application would lock up the desktop  enviornment (Gnome/KDE) and I couldn't kill it.  However, I found out a  few "tricks" that make handling crashes in Linux 500000x better than in  Windows.  Windows has decent management when something crashes, but yet  again it's usually when your application is full screen and completley  locks up, even ctrl+alt+del won't switch focus or alt-f4 won't end it.

Here is how to "recover" from any kind of crash in Linux that goes full  screen and you can't get focus:

```
First, press **CTRL+ALT+F1**.
```This brings you to one of  your six terminals.  The others are ctrl+alt+[f2,f3,f4,f5,f6].  Ctrl+F7  brings you back to your desktop but we're not interested in that because  the problem is still going to be there.

It will ask you to log in.  Log in as your typical name.  This is linux  so you can be logged in as the same user twice.  
You probably remember what process/thing is causing the problem.

Type:
```
$ps aux | grep processname
```"ps aux" is your entire process  list and |grep processname filters it by the name.  It should return a  name along with a process ID  (PID).  Next type:
```
$killall pid
```where pid was the PID of the process.  You may  have to type sudo before killall.

If none of that works, just restart X.
You can do so by hitting **CTRL+ALT+BACKSPACE**
or log into one of your terminals with the above ctrl+alt+f1 and type
```
#sudo /etc/init.d/gdm stop
#sudo /etc/init.d/gdm start
```which restarts gnome.  (replace gnome  with kdm if you're using kde)


You'll find that if you restart your desktop or restart X server then  you won't ever have to do a hard reset due to a crash.

I'm not familiar with this forum's policies on sudo so replace sudo with  sudo -i or su or whatever you like to use if that's the case.

---

### Post by reiki on 2010-05-27
For new people, think simple solutions. 

Right-click the panel, choose Add to Panel, scroll down the list a little until you see Force Quit. Add it to your panel. To use it just follow the directions that show when you hover over it or click it.

There are lots of ways to kill a hung application. Some more elegant than others. Some requiring command lines use in other terminals.

If you're new, keep it simple. Force Quit works and it's easy.

---

### Post by sdennie on 2010-05-27
> **HotForLinux said:**
> This is bad. 
The ESC key should cancel the xkill.
Many problems wouldn't exist if people used to think in how to undo as much as in how to do. 

It is much more important than it seems.

You have to realize that xkill is probably 20 years old.  There are a whole host of old-school programs that begin with x (bring up a terminal and type x<Tab>) that are not considered user friendly or even relevant anymore but, they are included in all versions of linux or Unix because they represent a way to interact with the fundamental functions that X provides.

---

### Post by HotForLinux on 2010-05-29
> **sdennie said:**
> You have to realize that xkill is probably 20 years old.  There are a whole host of old-school programs that begin with x (bring up a terminal and type x<Tab>) that are not considered user friendly or even relevant anymore but, they are included in all versions of linux or Unix because they represent a way to interact with the fundamental functions that X provides.

Yes, I know that and debian was still including them in the menus.

Yet, Xkill/Force__Quit ... too much, too similar, for too little...  doesn't seem a good practice

---

### Post by daimaru on 2010-05-29
first congrats to all for answering a post from 2009-... but to input my douchy thoughts.. you can still hit ctrl+alt+backspace to restart the xserver or use the terminal commands :
(sudo service gdm restart || sudo /etc/init.d/gdm restart)

If you want to use ctrl+alt+backspace you have to enable killing xserver in System->prefs->keyboard   hit the options button (or someting like that) and find the entry that says "kill xserver..." enable the checkbox and your good to go.

---

