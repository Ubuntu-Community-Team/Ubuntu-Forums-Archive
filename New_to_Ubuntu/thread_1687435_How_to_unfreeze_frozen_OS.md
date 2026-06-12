---
title: "How to unfreeze frozen OS"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by eeprom on 2011-02-13
[SIZE=3]Hello,
Every now and then my computer freezes up.  It's happened once while editing a spreadsheet in open office calc, and it's happened twice while running Rhythmbox.  I've had to shutdown the computer each time because I don't know how to break the loop.  In Windows, CTRL + ALT + DEL will open the task manager where I can kill the process.  Is there a way to kill a process in Ubuntu when the computer freezes?

Also, is there a way to see what processes are running from a terminal?  If so, please tell me the command.

thanks
EE

[/SIZE]

---

### Post by jimestesphl on 2011-02-13
Go to System-Administration-System Monitor.  This is the Linux version of Task Manager.  Click on Processes to see what's running and "end process" of the offending program.

---

### Post by zhogan85 on 2011-02-13
There are two ways I know of two kill processes. The first, press alt-f2, then type xkill. Your cursor will then become an x and simply click on the offending program and it will be killed. The second method I know of is adding a force quit function to the panel at the top of the screen. Right click on the panel, click add to panel, and add force quit. Then if a program freezes, you can click on that and then end the process. Hope this helps. If it's your entire OS that's frozen, and neither of these work, unfortunately I'm not sure what to do, as I'm still learning Ubuntu myself.

---

### Post by rburkartjo on 2011-02-14
eep you might want to try this


Easily "Force Quit" or "End Task" on a program in Linux with a keyboard shortcut 

[http://www.thetechrepo.com/main-articles/505-easily-qforce-quitq-or-qend-taskq-on-a-program-in-linux-with-a-keyboard-shortcut](http://www.thetechrepo.com/main-articles/505-easily-qforce-quitq-or-qend-taskq-on-a-program-in-linux-with-a-keyboard-shortcut)


note the default shortcut keys that is assigned my differ from the ones in the article. also note that right mouse click cancels.

---

### Post by lordjj on 2011-02-14
For a frozen OS: 
If you want to shut it down safely, without risking corrupting files through a hard reset, you can do this:
hold: alt + printscrn (on some laptops you have to hold fn & printscrn)
and press R,E,I,S,U,B slowly in that order 
(so you'd be pressing 3 keys at a time; or 4 with fn)

If there's a particular process thats frozen, for example a fullscreen program called "program1":
Hit Cntrl+Alt+f1
login with your username and password
type in
```
sudo pkill -9 program1
```
then hit Cntrl+Alt+f7 to go back to graphical mode

(in some places, I've read its Sysreq instead of Printscreen, but Printscreen works with me -its on the "insert" button on my laptop)

To see running tasks: In the top panel, System > Administration > System Monitor > Processes
or, open a terminal (Cntrl+Alt+T) and type
```
gnome-system-monitor
```

---

### Post by eeprom on 2011-02-17
[SIZE=3] Thank you all for the help.  I tried the shortcut keys for xkill.  It appears to work well.[/SIZE]

---

### Post by mn_voyageur on 2011-02-17
I keep "Force Quit" on my top bar.  (Right-click on the bar and add it to the panel.)

MarkN

---

