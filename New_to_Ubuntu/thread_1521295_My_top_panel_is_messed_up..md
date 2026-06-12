---
title: "My top panel is messed up."
date: 2010-06-30
forum: New to Ubuntu
---

### Post by kirbyparufo on 2010-06-30
Somehow, my top panel got messed up. It keeps changing too. Sometimes, the shut down icon vanishes, or sometimes I get two Internet connection icons and lose the volume icon. My question is, should I delete my current panel and create a new one? If so, I'm not sure on how to restore almost everything.

Before I forget, I already tried resetting the panel by using the following commands:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```Using that code restores the panels to their correct state, but every time I shut down or restart they mess up again.

---

### Post by stepstools on 2010-06-30
I saw this somewhere - 

```
sudo debconf gnome-panel
``` (Run in terminal)

This code will reset **both** panels once you reboot your computer.

---

### Post by mhgsys on 2010-06-30
open a terminal and type:

```
gconftool-2 --recursive-unset /apps/panel
```

and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) type

```
sudo /etc/init.d/gdm stop
```

```
sudo /etc/init.d/gdm start
```

Panels will be back to default.

btw.. if it starts changing like that again.. 
try if it has anything to do with compiz choking up.

In System>Preferences>Appearance>Visual effects.. set them to none.

---

### Post by kirbyparufo on 2010-06-30
stepstools's solution reset the panels and logged me into root, but after restarting the problem persisted. mhgsys's solution seems to have solved the problem. Thanks to both of you for your willingness to help in any case! :D

---

### Post by k3lt01 on 2010-06-30
Mine totally disappeared yesterday, I just right clicked and "Add to panel" and it has been ok ever since. I don't know what caused it, that is the only thing that concerns me.

---

### Post by mhgsys on 2010-06-30
> **kirbyparufo said:**
> stepstools's solution reset the panels and logged me into root, but after restarting the problem persisted. mhgsys's solution seems to have solved the problem. Thanks to both of you for your willingness to help in any case! :D

You're welcome.

---

### Post by cakerapujangga on 2010-07-09
> **mhgsys said:**
> open a terminal and type:

```
gconftool-2 --recursive-unset /apps/panel
```

and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) type

```
sudo /etc/init.d/gdm stop
```

```
sudo /etc/init.d/gdm start
```

Panels will be back to default.

btw.. if it starts changing like that again.. 
try if it has anything to do with compiz choking up.

In System>Preferences>Appearance>Visual effects.. set them to none.

Hey, I'm new here and experience the same problem about the panel.
what is gdm means and how to restart it?

---

### Post by mhgsys on 2010-07-09
GDM is the GNOME Display Manager

you can restart it with 
```
 sudo service gdm restart
```

but I prefer the old way; 
in console (Ctrl+Alt+f1 ,f2, f3, etc) type

```
sudo /etc/init.d/gdm stop
```
to stop gdm

```
sudo /etc/init.d/gdm start
```
to start gdm

---

### Post by celiapgt on 2010-07-18
> **mhgsys said:**
> open a terminal and type:

```
gconftool-2 --recursive-unset /apps/panel
```

and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) type

```
sudo /etc/init.d/gdm stop
```

```
sudo /etc/init.d/gdm start
```

Panels will be back to default.

btw.. if it starts changing like that again.. 
try if it has anything to do with compiz choking up.

In System>Preferences>Appearance>Visual effects.. set them to none.

I followed your instructions to the book and now the upper panel is back in town! It is perfect! I was starting to pull my hairs.

Just one question. As I don't know what triggered the panel misbehavior, and I suppose your fix is some kind of gnome-panel resetting, I would like to know if your solution is permanent. With all respect I ask. 

Thanks, mhgsys, for your big help.

---

### Post by mhgsys on 2010-07-27
> **celiapgt said:**
> I followed your instructions to the book and now the upper panel is back in town! It is perfect! I was starting to pull my hairs.

Just one question. As I don't know what triggered the panel misbehavior, and I suppose your fix is some kind of gnome-panel resetting, I would like to know if your solution is permanent. With all respect I ask. 

Thanks, mhgsys, for your big help.

This will be and should be as permanent as it once was originally

So; I don't know what caused your panels to misbehave... but I bet it had/has something to do with compiz....

---

### Post by dsfitzpat on 2010-11-15
I've had problems with the top panel too, in both 10.04 and 10.10.  I haven't checked to see what happens with compiz turned off but I wouldn't be surprised if that's the problem.
Anyway, I've noticed that everything is really there, it's just not displaying properly.  If things are messed up when you log in, there's an easy way to fix it without the terminal:
1. Right click on the panel, choose Properties
2. Increase the size (default is 24) until the icons go back to normal (this should happen around 26 or 27)
3. Decrease the size back to 24, and the icons will remain as they should be.

---

### Post by anish.man on 2011-01-12
Thanks [mhgsys]("http://wwww.ubuntuforums.org/member.php?u=597090") the solution is work

---

### Post by kwhitefoot on 2011-03-19
Just thought I'd add my thanks to mhgsys :cool:

One thing though "gdm stop" killed X so the easiest way to start again was "startx".

---

### Post by rbishop on 2011-03-19
I am seeing the same thing happen to my panel from time to time, it is never a constant thing.  This makes me believe that it is probably a Compiz issue.  Normally when I see the issue, I reboot and all is back to normal.  I have not tried any of the solutions yet, but it hasn't become enough of an issue for me to worry about it.

Thanks for the solutions everyone.

---

