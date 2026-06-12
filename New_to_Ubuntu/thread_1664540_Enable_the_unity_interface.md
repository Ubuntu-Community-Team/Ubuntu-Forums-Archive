---
title: "Enable the unity interface"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by OJsimpson on 2011-01-11
I just recently discovered I have ubuntu 11.04, but I dont have the unity interface for some reason. I have the graphics acceleration and all that, im just not sure how to enable it unity O_o

---

### Post by mikewhatever on 2011-01-11
Ask in the 11.04 testing subforum. ;)
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by Paqman on 2011-01-11
> **OJsimpson said:**
> I just recently discovered I have ubuntu 11.04

Natty (11.04) is not ready for use yet, it's still in alpha. If you're a beginner with Ubuntu you definitely should not be running it, as it almost certainly will break to a greater or lesser degree during development. In fact, even if you're quite an advanced user, running an alpha build can be a hassle.

I'd recommend you ditch Natty and re-install with a stable release, either 10.04 or 10.10.

---

### Post by chrisw92 on 2011-01-17
are you sure your not running 10.04 or any other previous versions?

if not then I would go with Paqman's recommendation and install a stable release and then wait until 11.04 is publicly released.

---

### Post by wojox on 2011-01-17
It could be the bug. Run this in the terminal to see what release you really have:

```
cat /etc/lsb-release
```

---

### Post by ogrishmania on 2011-04-17
> **wojox said:**
> It could be the bug. Run this in the terminal to see what release you really have:

```
cat /etc/lsb-release
```

I have 11.04 (after running that command) and I have the same issues. I have upgraded from 10.10 and gnome interface is default. How to change this?

---

### Post by PPPilot on 2011-04-17
OK, first off do you have to log in to get into a session? If not, you have selected the option to do an auto login during install. If this is the case then Natty will take a look at your hardware and if it does not support the Unity interface it will start up in the Classic Gnome interface.

Now if you are seeing the login screen, when you click on your name, a panel will appear at the bottom of the screen. Select Sessions. This will show you a menu which will allow you several start up options among them, Unity, Classic Gnome, Gnome (2D) and others. If you select Unity and log in, you will get a message box if your hardware is not compatible with Unity and it will tell you to select the Classic Gnome or Gnome (2D) sessions.

Now the question is, if you are setup for auto login, how do you get back to seeing the login screen? Go to System>Administration>Login Screen. Select "Unlock"and enter your password. Then select "Show the screen for choosing who will login". Click "Close" and reboot. You will now see the Login Screen and you will be able to select a session per above.

Good Luck...

---

### Post by mikewhatever on 2011-04-17
> **PPPilot said:**
> ...

Now the question is, if you are setup for auto login, how do you get back to seeing the login screen? Go to System>Administration>Login Screen. Select "Unlock"and enter your password. Then select "Show the screen for choosing who will login". Click "Close" and reboot. You will now see the Login Screen and you will be able to select a session per above.

Good Luck...

Just log out. :P
...but chances are, the Unity interface won't run, even if selected.

---

### Post by Blasphemist on 2011-04-17
> **mikewhatever said:**
> Just log out. :P
...but chances are, the Unity interface won't run, even if selected.

I don't understand unless this is an attitude.

PPPilot's suggestion is correct in IMHO

---

### Post by PPPilot on 2011-04-17
I guess I was not clear. I was trying to diagnose the problem not fix it. My feeling is that his hardware does not support Unity and if he follows my suggestion he will at least know if his hardware is the issue.

I know first hand as the first time I tried to login to a Unity session, it told me my hardware would not support Unity so I am running it in the Classic Gnome mode. I can run Natty in KDE with no problems so Unity may have some issues.

---

### Post by mikewhatever on 2011-04-17
> **Blasphemist said:**
> I don't understand unless this is an attitude.

PPPilot's suggestion is correct in IMHO

Are you suggesting that mine was somehow incorrect?

---

### Post by score100 on 2011-04-18
I tried the beta last week with the same problem. I knew about the logging out thing, but there was no choice called "unity" in the dropbox. Only Ubuntu, Ubuntu Classic, and failsafe gnome as far as I remember. Netbook interface wasn't an option either.

---

### Post by PPPilot on 2011-04-18
You are correct. After I did the latest update, they have changed the session menu and Unity is no longer mentioned. I believe that the option of Ubuntu (in italics) must be the unity desktop but if your hardware is not compatible, they no longer tell you it just goes ahead and runs something. I say something because on my machine I get a screen with fonts about a half inch high. I'm glad I still have Lucid on my machine. 

You run Beta and take your chances

---

### Post by embain14 on 2011-05-07
I dont know what the deal is but I know it solved all of my problems when I upgraded to 11.04 from 10.10 my compiz and animations and all that jive got all messed up working now thanks!

---

