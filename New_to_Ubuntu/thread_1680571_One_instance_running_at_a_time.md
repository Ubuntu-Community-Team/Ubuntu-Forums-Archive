---
title: "One instance running at a time"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by JQadrad on 2011-02-02
Hello,

I'm trying to make a full switch to Linux. After several failed attempts I would really like to get rid of Windows on my laptop and use Linux. At this moment I have Linux Mint and try to figure out some things that I miss from Windows 7, like the multitouch touchpad, Dropbox without errors and shortcuts. I figured most of the things out by now (and put them in a tutorial for myself :P) so I know it for the next time.

The problem is that I'm used to the Windows 7 shortcuts, where pressing Win+3 results in Google Chrome start or toggle, Win+4 Explorer etc (in my case), but I want this functionality in Linux. I'm not really attached to Linux Mint or Ubuntu and don't really know what the difference are, since both are quiet easy to understand imo, but is there a option to make such a function? So Win+3 results in OR opening a new browser, OR bringing it back to the front, in other words, only one instance allowed?

Please give me some suggestions. Any help is appreciated :)

---

### Post by Sef on 2011-02-03
Moved to ABS.

---

### Post by migs73 on 2011-02-03
> **JQadrad said:**
> Hello,

I'm trying to make a full switch to Linux. After several failed attempts I would really like to get rid of Windows on my laptop and use Linux. At this moment I have Linux Mint and try to figure out some things that I miss from Windows 7, like the multitouch touchpad, Dropbox without errors and shortcuts. I figured most of the things out by now (and put them in a tutorial for myself :P) so I know it for the next time.

The problem is that I'm used to the Windows 7 shortcuts, where pressing Win+3 results in Google Chrome start or toggle, Win+4 Explorer etc (in my case), but I want this functionality in Linux. I'm not really attached to Linux Mint or Ubuntu and don't really know what the difference are, since both are quiet easy to understand imo, but is there a option to make such a function? So Win+3 results in OR opening a new browser, OR bringing it back to the front, in other words, only one instance allowed?

Please give me some suggestions. Any help is appreciated :)

To assign shortcuts, go to System>preferences>keyboard shortcuts.

Then click on 'add', to create a custom shortcut. A box will appear, just type in a name for your shortcut and the command you want it to run, now it is a bit complicated!!!

The command to open Chrome would be 'chromium-browser' without the quotes, to get it to only open once and to bring to front ('focus' is the term) I'm afraid I don't know.
To assign the key presses, click on the right of the row where it says 'Disabled' and press the key combo you want then apply. (NB the 'Win' key is actually called the 'super' key and will come up as Mod4 when pressed on the shortcut config tool)

Hopefully someone can let us know the command required to do the precise actions you want (I'm going to do a bit of googling to see if I cna find out myself), but at least you're half way there.


Mike

---

### Post by migs73 on 2011-02-03
Looks like there will have to be a shell script to do this ( a small program to allow the functionality).

I am thinking of 'xwit' as the app to use in the script.

the logic would be;

If Chrome is open, xwit -focus (bring Chrome to front)

else open chrome

End if

PS I know that won't execute, I am showing the logic, not the code. That's the bit I need to work on!

---

### Post by migs73 on 2011-02-03
I am not on ubuntu just now but was thinking this script might do it;

```
#!/bin/sh
/usr/sbin/pidof chromium-browser > /dev/null 2&>1 if [ $? -gt 0 ] ; then xwit –focus -names chromium-browser
else chromium-browser
fi

```


????? Anybody got any other ideas. I'll test/refine (see if it works at all!!) later tonight.

---

### Post by JQadrad on 2011-02-03
Thanks for the reply. I will try it out tonight. I'm not really good with shell scripting ofcourse, but you're never too old to learn :P

So the idea is to put that code in a shell script and call that script with a hotkey?

---

### Post by JQadrad on 2011-02-03
I'm looking at the program Kupfer right now, but I'm not sure how to use it. Pressing <Ctrl><Space> and typing chromium will focus on the window or create a new instance as I want, but you have to add triggers to do this with a hotkey. It's almost what I want I think..

Edit: I finally figured out how to add a trigger, but it is not what I'm looking for. It brings focus on a running app or opens the app, but it only blinks when the app is open on workspace 1 and you are on workspace 3. Besides that I can't add a trigger for gnome-terminal. 

So yes, I think I will have to try to understand shell scripting and wmctrl or xwit..

---

### Post by migs73 on 2011-02-03
I've got it!!

Found the (almost) solution here;

[http://ubuntuforums.org/showthread.php?t=633179](http://ubuntuforums.org/showthread.php?t=633179)

Script for Chrome as you want it is;

```
#!/bin/bash

#check if Chromium is open, if so, give it focus, else open Chromium

chromwin=`wmctrl -l | grep -m 1 -o "Chromium"`
if [ $chromwin = "Chromium" ];
	then
		wmctrl -R Chromium
	else	
		chromium-browser &
fi
```

I called the file 'ChromiumSwitch'.

To use it as you want, first install wmctrl

```
sudo apt-get install wmctrl
```

then open gedit

```
gedit
```

paste the above script into it and save it to your desktop as 'ChromiumSwitch'

right click on the file, select properties then the permissions tab and check the box for 'Allow executing of the file as program'

Now you can double click on the file and select run, it'll open a Chrome window. open another (different) window and put it in front of chrome, double click on the file and select run again and it should bring chrome to the front.

If the above does not work check you have done everything above correctly or post back.

Next you need move the file to usr/local/bin you will need sudo for this as it is 'owned' by root, the easiest way I have found to do this is to use 'nautilus-gksu' type it in to the Ubuntu software Centre and install it. You may have to log out and back in after to make it work.

It now allows you to browse to the folder and before opening it, right click and select 'open as administrator' and put in your password.
Now you can drag and drop/cut'n' paste your script (ChromiumSwitch) into it.

Right that's the script finished with, now to your keybindings.

System>preferences>keyboard shortcuts

click on 'add'

Give it a name (Chromium Switch)

in the command field type 'usr/local/bin/ChromiumSwitch' without the quotes. Click 'Apply'

Now on the right hand side of the row, click, and then press the shortcut keys you want to use (Super+3) this will appear as Mod4+3. Click 'Close'.

That should be you done! Give it a try.


Regards

Mike  :)

---

### Post by migs73 on 2011-02-03
For those of you interested, I couldn't get xwit to behave the way I wanted, and couldn't get the 'only if chrome not already open' bit of the other script to work either!!! Not much of a first attempt!

---

### Post by JQadrad on 2011-02-03
Hey thanks for the reply again. I was already working on a shell script 

```
#!/bin/bash

sleep 1;

pid=`pidof skype`
if [ $? -eq 1 ] ; then
        echo "skype down"
else
        pid_id=`wmctrl -p -G -l | awk "/$pid/"' {print $0}' | cut -f 1 -d " " | cu$
        focus_id=`xprop -root | awk '/_NET_ACTIVE_WINDOW\(WINDOW\)/{print $NF}' | $
        if [ "$pid_id" == "$focus_id" ]; then
                echo "do minimize"
        else
                echo "do focus"
        fi
fi

```

I think I need to combine it a bit with your script to run or focus on the window. I try to figure out how to minimize the window, but that isn't working yet.

---

### Post by migs73 on 2011-02-03
> **JQadrad said:**
> Hey thanks for the reply again. I was already working on a shell script 

```
#!/bin/bash

sleep 1;

pid=`pidof skype`
if [ $? -eq 1 ] ; then
        echo "skype down"
else
        pid_id=`wmctrl -p -G -l | awk "/$pid/"' {print $0}' | cut -f 1 -d " " | cu$
        focus_id=`xprop -root | awk '/_NET_ACTIVE_WINDOW\(WINDOW\)/{print $NF}' | $
        if [ "$pid_id" == "$focus_id" ]; then
                echo "do minimize"
        else
                echo "do focus"
        fi
fi

```

I think I need to combine it a bit with your script to run or focus on the window. I try to figure out how to minimize the window, but that isn't working yet.

The script I posted will open Chrome if it is not already open, and if it is already open it will bring it to the front (focus), what do you want to minimise?

Combined with the keyboard shortcuts it replicates the behaviour you described in your first post. If you have other things you would like to do let me know and I'll have a bash at it. 

BTW I'm new to scripting too!! There is no better way to learn than to try it.

---

### Post by JQadrad on 2011-02-04
I want to minimize the window if it is already the active window, so this would toggle the browser. I found out that ```
wmctrl -R :ACTIVE: -b toggle,shaded
``` shrinks the window to the titlebar, but this isn't working for all my open windows.

You're code was working yesterday for me, but today it won't. Don't know what's going wrong, but I guess I'll figure it out..

I didn't know you could do so much with shell scripting. It's fun and functional.

---

### Post by buren on 2011-03-30
The esiest way i think to do it is usting this shell scipt: 

```


#!/bin/bash

#check if Chromium is open, if so, give it focus, else open Chromium


wmctrl -a chromeium || chromeium-browser &

```

mark the file as executable and then move it to /usr/local/bin

---

