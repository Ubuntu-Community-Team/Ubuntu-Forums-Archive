---
title: "Ubuntu 10.4 now starts in a terminal screen"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by mp512 on 2010-08-26
Help - New to linux, I've just installed 10.4 successfully. Displaying at about 800x640 on my flat screen
 
I would have liked a screen res of 1024x768 or 1280x1024. I used the drivers search for Nvidea and the auto procedure found and installed a driver which then displayed everything at 640x480. I was worse off.
 
I read that what I needed to do was edit /etc/X11/xorg.conf so I backed this up and tried an edit which didn't work so I restored the backup data.
 
On re-starting the system I was asked for a login which dropped me into terminal mode.
with the prompt
martin@bird:/$
 
I seem to be logged on twice. The command
martin@bird:/$ who
gives the following response
martin tty7
martin pts/0
 
My efforts to get to the normal gui at startup have been defeated.
As soon as I exit "terminal" I get into the login loop again.
 
How do I do get back to the default gui startup condition please?

---

### Post by farsight on 2010-08-26
I know I might be looking at it this in an over simplified manner, but when you log on (or click your name to log on) what session is displayed (this should be shown at the bottom of the screen as you type the password in). You want it to say something like GNOME, but I suspect it may be saying xterm?

Farsight

---

### Post by farsight on 2010-08-26
Hey again,

It seems that despite being a different problem, this other forum thread leads to a position much the same as yours, i.e the user is only faced with a screen in terminal asking for login info. I thought you might like to try the recommended resets for gdm given towards the end of the post:

[http://ubuntuforums.org/showthread.php?t=1560781]("http://ubuntuforums.org/showthread.php?t=1560781")

---

### Post by mp512 on 2010-08-26
Thanks for the response
It is xterm 
It quickly goes through to auto login and a very bare terminal window
 
Martin

---

### Post by mp512 on 2010-08-26
H'mm don't like the look of the repair procedure till I've got a file or two saved away somewhere.
Tried restarting gdm
sudo service gdm start
 
Response was 
Start: Job is already running: gdm
 
 
 
Martin

---

