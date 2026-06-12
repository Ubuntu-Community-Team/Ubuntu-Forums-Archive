---
title: "how make devilspie run in background in Jaunty"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-19
Found old instructions on how to make devilspie run as a service (or would it be daemon or something?) at boot up... but they refer to System > Preferences > Sessions, which is no longer there.
I tried putting /usr/bin/devilspie in the Startup Applications and that didn't work.

I've verified that my devilspie config file (or whatever you call it) is good... can execute from terminal and it has the desired result... until I close the terminal and kill it.

Anyway, read somewhere about rc.local and tried that... must be doing something wrong.
Just added 
/usr/bin/devilspie just before the exit 0 
Doesn't seem to work. Don't see devilspie in processes either.

So... something simple I'm overlooking?

(BTW, how to I get word to the powers that be that it doesn't make sense to align windows left on a desktop where you align the icons left? ... that means any app window that opens will cover some or all of your icons.. so I'm trying to get devilspie working before I go nuts)

---

### Post by super kim on 2009-08-19
> **aharown07 said:**
> but they refer to System > Preferences > Sessions, which is no longer there.


try "System > Preferences > Startup Applications" you should always look for the simplest solution to any problem first :)


i dont know what devilspie was so i google it and here is what they say about their program:
[quote=http://live.gnome.org/DevilsPie]
**Devil's Pie**

  
**Introduction**

 A totally crack-ridden program for freaks and weirdos who want precise control over what windows do when they appear. If you want all XChat windows to be on desktop 3, in the lower-left, at 40% transparency, you can do it. [/quote]

---

### Post by aharown07 on 2009-08-19
As I indicated in the OP, already tried Startup Applications. Didn't work.

As for somebody's opinion of devilspie, don't care.
I just want windows to default to a sensible place on the screen.

---

### Post by Clorow on 2009-08-19
```
echo devilspie& >> ~/.profile
```

---

### Post by aharown07 on 2009-08-19
> **Clorow said:**
> ```
echo devilspie& >> ~/.profile
```
Thanks! 
Not working though. Other ideas?

---

### Post by whitethorn on 2009-08-19
Hi, you could try adding 

```

/usr/bin/devilspie &

```

to /etc/rc.local

It'll be run as root at startup, so you might want to try restarting your pc once.  Only problem is it might not work since it'll be run as root.

---

### Post by aharown07 on 2009-08-19
> **whitethorn said:**
> Hi, you could try adding 

```

/usr/bin/devilspie &

```to /etc/rc.local

It'll be run as root at startup, so you might want to try restarting your pc once.  Only problem is it might not work since it'll be run as root.
That's pretty much what I've got in there now, except for the & ... what does that do? Just curious. 
Easy enough to try it. 

(Yes, I have been rebooting each time I try something different)
One other question, how about turning it into a service? Is there a way to do that? Maybe I'm talking nonsense. Don't know enough about Linux yet to have a clue.


Edit: one more question. Should any of this stuff in the rc.local file be uncommented...
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
```

OK, yet one more edit: the code isn't working with "&" at the end either.

---

### Post by Nepherte on 2009-08-19
You don't have to uncomment something in rc.local. Are you sure devilspie is not running when adding it to the startup applications or do the devilspie rules don't work? You can verify it is running with:
```
ps -A | grep devilspie
```

---

### Post by whitethorn on 2009-08-19
Well it's possible to create a startup script, I've never really done it before just changed a couple around.  As far as I know, you need to put 3 cases into ur script 

start, stop, and restart  

then move it to /etc/init.d/  and make it executable

and then you need to create symlinks to the file from the different runlevels found in

/etc/rc1.d .. /etc/rc6.d  

Since you're only gonna need it when you have ur Xserver up and running, you only need to create a symlink from /etc/rc5.d/

Name it S99devilspie

the 
S is for Start  and 
99 is for the order, since we want it to start after everything else has started.

just make sure u use 

```
ls -l
```

in /etc/rc5.d/ to see what the other symlinks look like.

---

### Post by aharown07 on 2009-08-19
> **whitethorn said:**
> Well it's possible to create a startup script, I've never really done it before just changed a couple around.  As far as I know, you need to put 3 cases into ur script 

start, stop, and restart  

then move it to /etc/init.d/  and make it executable

and then you need to create symlinks to the file from the different runlevels found in

/etc/rc1.d .. /etc/rc6.d  

Since you're only gonna need it when you have ur Xserver up and running, you only need to create a symlink from /etc/rc5.d/

Name it S99devilspie

the 
S is for Start  and 
99 is for the order, since we want it to start after everything else has started.

just make sure u use 

```
ls -l
```in /etc/rc5.d/ to see what the other symlinks look like.
Whitethorn, 
This sounds like "getting warmer," because the instructions I found mentioned setting the order late.
But I'm afraid I'm too new to all this to know what most of your post means.

To take just the last part, are you saying I cd to the /etc/rc5.d/ directory and then do a "ls -l"?
I really haven't a clue what a symlink even is!  Though it's easy enough to remedy that w/a bit of reading.. but maybe you can save me some time :D

---

### Post by whitethorn on 2009-08-19
Ah hell, my post disappeared!  Took me forever, quick rundown.  I added devilspie to my startup applications, logged out and back in, it worked.  

Are you using Compiz?  If you are then you either have to start devilspie afterwards or use the Place Windows plugin. To start devilspie after compiz

```

gedit /home/$USER/devilspie_starter

```
Paste the following
> 
#!/bin/bash
sleep 30 && devilspie

save and quit
```

chmod +x /home/$USER/devilspie_starter

```
Then in Application Startup add the path to the file
Box 1: Devilspie
Box 2: /home/nameofyouuser/devilspie_starter

You can name the file however and save it where you want in your homefolder. Log out and back it, should be working.

Getting it to run as a service, you first need a init script before you can start symlinking it.

---

### Post by aharown07 on 2009-08-19
I'm just using the default Metacity.
When you put it in startup apps, was it using the method described above or some other way? I can create the file as you've described though and try that. With or w/o Compiz, should work, shouldn't it?

---

### Post by aharown07 on 2009-08-19
Solved!

... but I have no idea how. Just did the same thing again and put "devilspie" in startup apps. Only now it works. 
Thanks everybody. Wish I knew what I was doing wrong before.

---

