---
title: "Two simple questions"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-13
1) How do you force quit a fullscreen application that freezes? Scorched 3D keeps freezing every now and then and every single key combination I can think of still doesn't quit it... I have to restart the computer by holding down the power button.

and 2) Why does my volume control not work in fullscreen applications?

---

### Post by rockerphil on 2009-03-13
ok, i'm not sure on the 2nd question, but i think i can help with the first one. my initial reaction to a frozen screen would be to hit Ctrl+Alt+F2, log in and then run:

```
killall <appname>
```

where <appname> is the name of the application causing you yo freeze up. if that doesn't work i'd try Ctrl+Alt+Backspace to "zap" the X session. if it works it should take you back to GDM allowing you to log in again. hope this helps, 

Phil

---

### Post by humphreybc on 2009-03-13
> if that doesn't work i'd try Ctrl+Alt+Backspace to "zap" the X session. if it works it should take you back to GDM allowing you to log in again.

Heh. [Funny you should mention that.]("http://ubuntuforums.org/showthread.php?t=1095588")

---

### Post by shark1997 on 2009-03-13
try ```
xkill
```

---

### Post by rockerphil on 2009-03-13
well, Ctrl+Alt+Backspace is SUPPOSED to "zap" your X session thus taking you back to your log-in screen (GDM for Ubuntu, KDM for Kubuntu)

---

### Post by humphreybc on 2009-03-13
Any idea why it wouldn't be working then? Maybe post in the other thread haha

---

### Post by rockerphil on 2009-03-13
no clue why Ctrl+Alt+Backspace wouldn't work, but another option would be to hit Ctrl+Alt+F2 (this will bring you to a log in shell, not your graphical log in manager), log in and run;

```
sudo killall Xorg
```

that will DEFINITELY stop your X server (aka Xorg)

---

### Post by humphreybc on 2009-03-13
Yeah but will it restart it or just kill it? How does one start it again without rebooting the computer?

---

### Post by aesis05401 on 2009-03-13
startx - restarts X.

Last time I saw a case where the key combo wasn't working to restart it was actually an overheating problem.  

If you are freezing and nothing will get you out of the frozen screen there is a possiblity your mobo is tripping a heat sensor and freezing.  Check your bios screen for temp readings and many have a time stamp for last time the CPU temp shutdown was tripped.

---

### Post by doas777 on 2009-03-13
have you tried Alt + F4 when the app freezes?

---

### Post by humphreybc on 2009-03-13
> **doas777 said:**
> have you tried Alt + F4 when the app freezes?

Yep. No key combination has any effect apart from ctrl+alt+backspace which just gives me a blank screen with a blinking cursor.

---

### Post by doas777 on 2009-03-13
> **humphreybc said:**
> Yep. No key combination has any effect apart from ctrl+alt+backspace which just gives me a blank screen with a blinking cursor.

sounds like somthing is seriously wrong. is there anything in your logs after you get back on?

---

### Post by Shazaam on 2009-03-13
Not a fix or an answer to your question about CTRL+ALT+Backspace but a better way to shut down a frozen pc is to hold down the ALT+Sys Rq (Print Screen) keys and then type in reisub. From here...
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by hyper_ch on 2009-03-14
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by humphreybc on 2009-03-14
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

If you have a look at my other posts you'll notice that I usually abide by these rules most of the time. In my experience (just because I only signed up here recently doesn't mean that I am a newbie to internet forum protocol) quite often descriptive titles of problems actually get less people viewing for the simple reason that a lot of people read the title and go "oh no, that's way too hard for me to fix!"

And the title is very descriptive, the thread is about two simple questions related to Ubuntu :)

---

### Post by humphreybc on 2009-03-14
> **Shazaam said:**
> Not a fix or an answer to your question about CTRL+ALT+Backspace but a better way to shut down a frozen pc is to hold down the ALT+Sys Rq (Print Screen) keys and then type in reisub. From here...
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Well I tested that just now and held down Alt+PRTSC/SYSRQ and waited a few moments while nothing happened...



AND THEN...






ATTACK OF THE SCREENSHOTS!!

Ironically this froze my computer after about 600 "Save Screenshot" windows opened and I didn't have a way of restarting other than holding down the power button!

---

### Post by detroit/zero on 2009-03-14
> **Shazaam said:**
> Not a fix or an answer to your question about CTRL+ALT+Backspace but a better way to shut down a frozen pc is to hold down the ALT+Sys Rq (Print Screen) keys and then type in reisub. From here...
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)
I always preferred ctrl-alt-sys req-k

It seems to work no matter what, and lands you right back at your GDM.

To answer another question, to get back to a desktop after entering the ctrl-alt-f2 terminal, use ctrl-alt-f7 - it'll take you right back to your desktop without starting a new session. (I believe startx and similar methods start a new session? I could be wrong..)

---

### Post by humphreybc on 2009-03-14
Seems that the sysrq key combinations aren't working at all for me... it just keeps taking screenshots!

---

### Post by mosquetero on 2009-03-14
After doing Ctrl + alt + F2 and kill the application, how can you come back to the desktop?? The only way I see is rebooting the computer!

---

### Post by carml on 2009-03-14
@ humphreybc
To stop a not responding application you can use a button on the top panel.
At the first the button isn't present,just right click on the top panel,select "Add to Panel" and look for an icon called "Forced Quit" or similar (I'm sorry,but my Ubuntu install is in Italian,so I translate what I see into English :) ),then everytime an application freezes,you have only to click to that launcher and you've quite done .
I hope this helps you.:)

---

### Post by detroit/zero on 2009-03-14
> **humphreybc said:**
> Seems that the sysrq key combinations aren't working at all for me... it just keeps taking screenshots!
Left-ctrl & left-alt??

Sometimes the right-alt key has different usages, like displaying special characters. For example: &#261;&#263;&#281;&#324;ó&#347;&#380;&#378;, &#260;&#262;&#280;&#323;Ó&#346;&#379;&#377; are all done with right-alt on my keyboard, and can't be done with left-alt. Similarly, I can't use the right-alt key for any system functions, like ctrl-al-sys req-k, or ctrl-alt-{L/R}arrow for switching desktops, etc.

---

### Post by doas777 on 2009-03-14
> **mosquetero said:**
> After doing Ctrl + alt + F2 and kill the application, how can you come back to the desktop?? The only way I see is rebooting the computer!

your desktop is usually on the tty at Ctrl + Alt + F7. sometimes it changes. I use bastille, so it adds logging ttys at F7 and F8, so I use F9.

if your not sure, just cycle from F1 to F9 until you see your desktop.

also if you drop into a tty, you can try
```
sudo /etc/init.d/gdm stop
```
followed by 
```
startx
```


have fun

---

### Post by humphreybc on 2009-03-14
> **carml said:**
> @ humphreybc
To stop a not responding application you can use a button on the top panel.
At the first the button isn't present,just right click on the top panel,select "Add to Panel" and look for an icon called "Forced Quit" or similar (I'm sorry,but my Ubuntu install is in Italian,so I translate what I see into English :) ),then everytime an application freezes,you have only to click to that launcher and you've quite done .
I hope this helps you.:)

Thanks, I know this works for windowed applications where you can still see the panel, and I have been doing this already, but I was wondering how to force quit a *fullscreen* application.

> Left-ctrl & left-alt??

Sometimes the right-alt key has different usages, like displaying special characters. For example: &#261;&#263;&#281;&#324;ó&#347;&#380;&#378;, &#260;&#262;&#280;&#323;Ó&#346;&#379;&#377; are all done with right-alt on my keyboard, and can't be done with left-alt. Similarly, I can't use the right-alt key for any system functions, like ctrl-al-sys req-k, or ctrl-alt-{L/R}arrow for switching desktops, etc.

Yep I used the left CTRL and left ALT buttons. I've tried most things but they all don't seem to work with the sysRQ key. All I get is a crapload of screenshot windows!

---

### Post by Shazaam on 2009-03-14
Sorry for the screenshots. Did you type in... 
```
R E I S U B
```
(doesn't need to be upper case) while holding down the key combo? After typing that in let go of the two keys.

---

### Post by humphreybc on 2009-03-15
Do you hold down just ctrl+alt or ctrl+alt+sysRQ as well?

---

### Post by robert shearer on 2009-03-15
Yes ctrl+alt**+**sysRQ it is a stretch but with a little practice you can then type the reisub.

Type each letter and **wait** a second then type the next. 
By the time you get to u a blank screen should appear and then typing b will reboot the computer.

Another version is here...

[http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

---

### Post by humphreybc on 2009-03-15
> **robert shearer said:**
> Yes ctrl+alt**+**sysRQ it is a stretch but with a little practice you can then type the reisub.

Type each letter and **wait** a second then type the next. 
By the time you get to u a blank screen should appear and then typing b will reboot the computer.

Another version is here...

[http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

NICE this actually works!!

---

