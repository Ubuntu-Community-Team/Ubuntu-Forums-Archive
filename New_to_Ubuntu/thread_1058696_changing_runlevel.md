---
title: "changing runlevel"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by abraxas334 on 2009-02-03
I need to change to run level 3 to install something. If i press ctrl+alt+F3 i do get a run level 3 session but my tty7 session is still active when i type finger. I tried
```
sudo gdm stop
```
but that didn't seem to kill the session. So how do i stop the xserver from loading? Or how can i kill it effectively! I also tried 
```
sudo killall X
``` which jsut told me that no X sessions were killed. 
thanks

---

### Post by WatchingThePain on 2009-02-03
Some run levels don't use x at all.

---

### Post by abraxas334 on 2009-02-03
yes runlevel 3 for example, but how do i get  my computer to run just in runlevel 3?

---

### Post by jimv on 2009-02-03
This command will put you in runlevel 3:

telinit 3

---

### Post by abraxas334 on 2009-02-03
> sudo telinit 3nothing happened when i typed that. 

I mean i can get into run level 3 with ctrl+alt+F3 but then my tty7 session is still running and i somehow need to kill that!

---

### Post by ibutho on 2009-02-03
Debian does not use runlevels in the same way as most Linux distros. Runlevels 2 - 5 are configured the same and the default is 2. If you need to shutdown X to install graphics drivers etc, you need to stop your login manager by doing something like 
```
/etc/init.d/gdm stop
```

---

### Post by jimv on 2009-02-03
Nothing is supposed to happen (well, nothing noticeable).  What are you trying to install?

---

### Post by callan79 on 2009-02-03
> **jimv said:**
> This command will put you in runlevel 3:
telinit 3


On my system 'sudo telinit 3' does nothing.

It does nothing if I issue the command from a terminal within X/GNOME. It also does nothing if I use CTRL+ALT+F3 to move to a text interface and then issue the command.

Am I losing my mind?

I get an "ubuntu restart" event in /var/log/messages, but GNOME doesn't actually shut down. Nothing actually happens.

A book I'm reading suggests you can mess with /etc/inittab to define your default runlevel. But this file does not seem to exist. Perhaps something to do with Upstart - [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

Cheers
Callan

---

### Post by jimv on 2009-02-03
Type 'runlevel' in the console.  You'll get back two numbers.  The one on the right is your current runlevel.  It should be 2.

Now type 'telinit 3' and then 'runlevel' again.  What does the number on the right say?  It says 3.  There is no difference in Debian or Ubuntu between runlevels 2-5.

If you want to shutdown Gnome, switch to a different TTY (control+alt+f[something]), login, and type 'sudo /etc/init.d/gdm stop'.

---

### Post by abraxas334 on 2009-02-03
> 
Type 'runlevel' in the console. You'll get back two numbers. The one on the right is your current runlevel. It should be 2.

ok i did this first time round it was 2 and 3 and after typing the telinit thing it was 3 and 3.
I need to kill my xserver session to be able to install the latest nvidia drivers 180.


> 
It does nothing if I issue the command from a terminal within X/GNOME. It also does nothing if I use CTRL+ALT+F3 to move to a text interface and then issue the command.

Am I losing my mind?

I get an "ubuntu restart" event in /var/log/messages, but GNOME doesn't actually shut down. Nothing actually happens.

A book I'm reading suggests you can mess with /etc/inittab to define your default runlevel. But this file does not seem to exist. Perhaps something to do with Upstart - [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

yeah same here!
I tried the gdm stop bit and all i get is this:
```

gdm[6573]: WARNING: GDM already running. Aborting!
GDM already running. Aborting!

```
and then sometimes (but only sometimes) a new screen saying something like:

```

There already appears to be and X server running on display:0 should another display number be tried? Answering no will cause GDM to start the server on :0 again.

And then options yes and no


```
If i then press CTRL+ALT+F3 i get to a black consol like from the olden days but if i type finger i am still logged in with tty7 session, which is the one i am trying to get rid of!

---

### Post by jimv on 2009-02-03
Ok, do this:

Reboot.  When you get to the login screen, do not log in.  Press control+alt+F1.  You should get a black terminal screen.  Login here.  Type 'sudo /etc/init.d/gdm stop'.  Now try installing whatever it is you're trying to install.

If that doesn't work, go back to that same black terminal screen and type these commands:

'sudo killall gdm'
'sudo killall Xorg'

Then try your install.

---

### Post by abraxas334 on 2009-02-03
hey jimv!
The first thing you suggested didn't work and i had tried that before, but the 
'sudo killall gdm'
worked well. I have now got the Nvidia drivers working :) now i just have to get my second screen working and mission accomplished
thanks alot!

---

