---
title: "problem with GUI"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-28
hi i have installed Ubuntu 8.04(Wubi)
my system hanged (not even keyboard or mouse worked)
so i pressed restart button, at that time update manager was installing some thing
after restart my system GUI changed 
i checked properties it is same as before
but now these are the changes i noticed
1)cant close an application(close ,minimize and maximize are missing)
2)Theme color has become grey 
3)All icons have changed
4)when i want to shutdown it comes to the login window there only i can shutdown or restart computer

it looks like windows 98
help me i am new to ubuntu
thanks in advance

i posted some of screen shots
[IMG]http://i40.tinypic.com/34dmmnk.png[/IMG]
[IMG]http://i44.tinypic.com/2nichp5.png[/IMG]

---

### Post by BOZG on 2009-02-28
Have you any idea what was downloading/installing at the time?

Have you tried updating again?

---

### Post by gkraju on 2009-02-28
> **BOZG said:**
> Have you any idea what was downloading/installing at the time?

Have you tried updating again?


i dont know waht was updated at that time 
but i updated at that time

---

### Post by Homunculi on 2009-02-28
do not know what happens at times .. 
but what your screen looks like happened on mine 
i booted into recovery mode and selected repair dk packages 
it worked when i came back up i had all the borders around the browser 

worth a shot ...

---

### Post by gkraju on 2009-02-28
> **Homunculi said:**
> do not know what happens at times .. 
but what your screen looks like happened on mine 
i booted into recovery mode and selected repair dk packages 
it worked when i came back up i had all the borders around the browser 

worth a shot ...

how to boot into recovery mode 
what i have to do can you tell me briefly

---

### Post by balaknair on 2009-02-28
When you start the system, you see the menu with a list of boot options. You'll find the 'Recovery Mode" option here just below the normal boot mode. Just use the 'Up" and "Down" arrow keys to select it and press enter. The system will boot into a recovery console.

If you have a 'hidden' boot menu when starting up(ie: you don't see the menu), you would normally see a message "Press ESC to enter menu" at start up right after the POST screen(The first screen that loads up with info about your system like type of motherboard, CPU etc. when you switch on your machine, on some machines as scrolling text and on some as an image). Press the 'esc' key at this stage to get to the menu, select 'Recovery mode' and press 'Enter'.

Once you boot into 'recovery mode' you can choose the 'repair broken packages' option to correct the errors.

Hope this is helpful

---

### Post by gkraju on 2009-02-28
> **balaknair said:**
> When you start the system, you see the menu with a list of boot options. You'll find the 'Recovery Mode" option here just below the normal boot mode. Just use the 'Up" and "Down" arrow keys to select it and press enter. The system will boot into a recovery console.

If you have a 'hidden' boot menu when starting up(ie: you don't see the menu), you would normally see a message "Press ESC to enter menu" at start up right after the POST screen(The first screen that loads up with info about your system like type of motherboard, CPU etc. when you switch on your machine, on some machines as scrolling text and on some as an image). Press the 'esc' key at this stage to get to the menu, select 'Recovery mode' and press 'Enter'.

Once you boot into 'recovery mode' you can choose the 'repair broken packages' option to correct the errors.

Hope this is helpful
i booted in recovery mode 
and i also selected the repair broken packages option it downloaded something and installed but it haven't worked the settings are same as before.

please help

---

### Post by balaknair on 2009-02-28
Try this to reconfigure/repair your GDM (write these commands down carefully including all the spaces and punctuation, and type them in carefully) :

1) Open a text console: ```
Ctrl+Alt+F1
```

2) Log in with your username and password

3) type in the command ```
sudo /etc/init.d/gdm stop
```

4) to reconfigure GDM
```
sudo dpkg-reconfigure gdm

```

5) restart GDM
```
sudo /etc/init.d/gdm start
```

Hopefully that will fix things. If not, maybe a forced reinstall of GDM might be needed, let's hope it doesn't come to that.
All the best.

PS: Whatever the outcome of the method above, please post it here in this thread so that it might be of use to others with similar issues. I've added a subscription to the thread so that I'll be notified when you post here, so you don't need to PM me(though you're more than welcome to do so).

Thanks
:D

---

### Post by gkraju on 2009-02-28
> **balaknair said:**
> Try this to reconfigure/repair your GDM (write these commands down carefully including all the spaces and punctuation, and type them in carefully) :

1) Open a text console: ```
Ctrl+Alt+F1
```

2) Log in with your username and password

3) type in the command ```
sudo /etc/init.d/gdm stop
```

4) to reconfigure GDM
```
sudo dpkg-reconfigure gdm

```

5) restart GDM
```
sudo /etc/init.d/gdm start
```



Hopefully that will fix things. If not, maybe a forced reinstall of GDM might be needed, let's hope it doesn't come to that.
All the best.

PS: Whatever the outcome of the method above, please post it here in this thread so that it might be of use to others with similar issues. I've added a subscription to the thread so that I'll be notified when you post here, so you don't need to PM me(though you're more than welcome to do so).

Thanks
:D
thanks  for your reply 
i have done what you said but it hasnt worked 
how to force reinstall of GDM

---

### Post by gkraju on 2009-02-28
balaknair as you asked for extra information about the system
1) theme can be changed but it doesn't changed only the scroll bar appearance alone is changing
2)Desktop Background is different from the one i selected

---

### Post by balaknair on 2009-02-28
To force GDM back to it's defaults, we can delete the Gnome settings files, so that on next startup, we have the default settings back.

Open your 'home' folder--> view hidden files by pressing **ctrl+h**--> select the following folders and delete them-**.gnome, .gnome2, .gconf, .gconfd, .metacity**

Restart the GUI by logging out and back in.

This returns your Gnome settings to the default.

---

### Post by kansasnoob on 2009-02-28
> hi i have installed Ubuntu 8.04(Wubi)
my system hanged (not even keyboard or mouse worked)
so i pressed restart button, at that time update manager was installing some thing
after restart my system GUI changed 

Since an update/upgrade was interrupted I would go to terminal and run:

```
sudo dpkg-reconfigure -phigh -a
```

It will take quite a while, so be patient! What that will do is basically stop, reconfigure, and restart every single package using the packages already installed.

A reinstall would probably be faster.

---

### Post by gkraju on 2009-02-28
[QUOTE=kansasnoob;6814889]Since an update/upgrade was interrupted I would go to terminal and run:

```
sudo dpkg-reconfigure -phigh -a
```

It will take quite a while, so be patient! What that will do is basically stop, reconfigure, and restart every single package using the packages already installed.

A reinstall would probably be faster.[/QUOT
i worked partially 
remaining problems 
1)till i cant close an application no close,minimize or maximize button visible i have to right click the application in taskbar and close it
2)alt+tab is not  working

please help

---

### Post by gkraju on 2009-02-28
ok problem solved last post is my mistake i have to change the appearance setting 
thanks everybody for your help..

---

