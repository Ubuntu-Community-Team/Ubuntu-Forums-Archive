---
title: "command line to get to login?"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by degarb on 2011-02-22
I am set to auto login.  I accidentally chose open box session (playing around with lxde).  Open box is a blank screen!!!  No options.  So, I am lost as to how to get my machine back.

I have tried ctrl alt f2 and gdm-restart (this just restarts open box)  and logout (just log me out and kills gdm)

I need my log in screen so I can choose gnome or lxde!  (then I need to delete open box off system so this can't happen again)

---

### Post by komputes on 2011-02-22
> LogoutCommand program invoked when "Logout" is chosen in  the lxpanel menu. Generally, this can be "killall <something>".  Under LXDE, you can use "lxde-logout" to logout the session. Warning :  it seems that in latest (git) code, it is "Logout" instead of  "LogoutCommand" 

Source: [http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel)

---

### Post by Ben Page on 2011-02-22
Try: startx

---

### Post by degarb on 2011-02-22
yes, I tried startx.  It starts up gnome.  But on reboot, I just get blank screen again, and no gnome.  (going to a broken openbox).

If I hit logout in gnome, it just pops me off to commandline.  And If I go to prefs>login screen, I hit unlock and no dialog comes up to enter my password; so, I cannot change login away from automatic!   

I need a way to command line kill openbox and start the login, so I can choose gnome again (settings stick for next reboot). 

I cannot have a wife, 3 year old, and 5 year old, hitting ctrl alt f2 and sudo startx just to boot a machine!

---

### Post by Ben Page on 2011-02-22
Have you tried updating your OS, it may fix the issue. Also, try Ubuntu Tweak, in the Startup section choose Session Control. Reset fields to their default values or enter appropriate values manually: nautilus, gnome-panel, compiz

---

### Post by degarb on 2011-02-22
this is not an lxde issue!  Basically, I chose openbox session, and I cannot get out to the session chooser login (with reboot, commandline, or gui).   This is made worse since openbox is a blank screen and requires 1. Ctrl alt f2 2. user 3. password 4 start x , to get to a useable ubuntu.  (typing lxsession doesn't work to get to lxde)  My gdm configuration is locked and I cannot disable auto login.   So, the loop continues.

*googling command line way to get to linux login screen (gdm) nothing.  gdm restart just restarts open box

*admin>loginscreen>Autologin still locked.  No luck. 

*Logout in open box, doesn't give me the gdm login where I can choose my session, unlike lxde and gnome.

( Obviously, --on a off topic note, which doesn't concern my predicament much- I am not impressed with my first impressions of openbox.  Why  openbox--useless geekware- is installed as a session option when it is a blank screen, and can break half new users boxes is beyond me.)

---

### Post by degarb on 2011-02-22
> **Ben Page said:**
> Have you tried updating your OS, it may fix the issue. Also, try Ubuntu Tweak, in the Startup section choose Session Control. Reset fields to their default values or enter appropriate values manually: nautilus, gnome-panel, compiz


This is the best family laptop my budget can afford: 500 mhz, 500 meg, 6 gig hd. Old incompatible broadcom driver took me 2 days to get working. ( Any upgrade/reinstall would likely kill the machine.) It ran great and did everything they need.  I made mistake of trying lxde to make it run faster.  9.1 made mistake of making openbox an option.

---

### Post by degarb on 2011-02-22
what is the requirement of ubuntu tweak? (little hd space free, and ubuntu 9.10


I am still believe got to be a way to get my login screen back with command line and I just haven't hit on it.

---

### Post by komputes on 2011-02-22
Perhaps this will allow you to restart GDM:

```
sudo service gdm restart
```

If you are able to start processes (terminal or alt-f2 run box) try changing the auto log in settings by running
```

gksudo gdmsetup
```

---

### Post by FoxEWolf on 2011-02-22
This is very odd indeed, I have clicked Open Box Session" once before. The OS returned to the GNOME login after the next shutdown and reboot.

---

### Post by degarb on 2011-02-22
> **komputes said:**
> Perhaps this will allow you to restart GDM:

```
sudo service gdm restart
```

If you are able to start processes (terminal or alt-f2 run box) try changing the auto log in settings by running
```

gksudo gdmsetup
```


gdm restart just restarts a blank openbox.   gdmsetup just complains it cant open the gui.  I need a way to edit on command line the variable.

Now, after a reboot!!!!  startx complains it is already running!  And it wont start up any gnome any more!  (   /tmp/somefile is locked.  But, I try to delete it and restart, to get same complaint.

---

### Post by degarb on 2011-02-22
maybe sudo apt-get purge openbox ?
I don't know the lines.  Would this work?

---

### Post by sisco311 on 2011-02-22
> **degarb said:**
> what is the requirement of ubuntu tweak? (little hd space free, and ubuntu 9.10


I am still believe got to be a way to get my login screen back with command line and I just haven't hit on it.

Edit the /etc/gdm/custom.conf file. For details see:
[http://library.gnome.org/admin/gdm/2.28/gdm.html#daemonconfig](http://library.gnome.org/admin/gdm/2.28/gdm.html#daemonconfig)

---

### Post by degarb on 2011-02-22
Solved:  None of the gdm commands would work,  eventually startx failed to load gnome.  I was stuck in broken open box blank land!

I did have ctrl alt f2 commanline.  So I sudo apt-get purge openbox obconf obmenu
this uninstalled openbox (apparently)  and allowed me to reboot into gnome.

Now, I could change the login setting back to manual login (just in case).  I haven't been bold enough to reboot a second time just to check, though.

This wasted 2 hours of my day, but a reinstall would waste a week (only one partition on drive).

by the way, LXDE uses 27 percent of my 500 meg of ram and gnome uses 41 percent.  But gnome is running webilder and weather widget; so not sure how much ram they use.

---

### Post by degarb on 2011-02-22
> **sisco311 said:**
> Edit the /etc/gdm/custom.conf file. For details see:
[http://library.gnome.org/admin/gdm/2.28/gdm.html#daemonconfig](http://library.gnome.org/admin/gdm/2.28/gdm.html#daemonconfig)


I read about 14 months ago, but don't remember.  Do you use pico or vi, and how?

---

### Post by matt_symes on 2011-02-22
Hi

Might i suggest messing about with the OS using a Virtual machine. Virtual box maybe.

Kind regards

---

### Post by sisco311 on 2011-02-22
> **degarb said:**
> I read about 14 months ago, but don't remember.  Do you use pico or vi, and how?

You can use your favorite (CLI) text editor. New users often find nano (a free pico clone) easier and more intuitive than vi or vim. 
[uhelp]community/Nano[/uhelp]
[uhelp]community/VimHowto[/uhelp]

---

### Post by rburkartjo on 2011-02-25
de yea i have did what you say wasted. by i dont consider the time wasted you can always learn from you mistakes. cant tell you how many times i have pouched my system and 99% of time i have fixed without doing a new install. and i have really learned from the 1%. yea learned what not to do again. just go for it

---

