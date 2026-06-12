---
title: "Did I just kill a Koala?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-11
Hi all. This is a bit weird... But I managed to get my other computer to not to boot, except in terminal mode, which is kind of out of my world at the moment. I had just installed Docky on it and was arranging the desktop for my liking, IE. deleting the bottom panel and creating another to the right side of the screen. I made it to auto-hide in error, and as I for some odd reason couldn't get my hands on it anymore to re-configure it, I created a new one on top of it. I just began to tweak it to suit my purposes when the machine just froze. I waited a while, until shutting the system down(by holding the physical power button down until the thing shut down). I tried to restart it, first normally, I got to insert my login info, and then it froze again, with failsafe mode the exact same story. With xterm I get the terminal up and running, I'am able to use nautilus and thats about it. What to do?

---

### Post by lockalidiot on 2010-02-11
UPDATE! After typing "exit" on the xterm I managed to first boot with failsafe and then reboot with just ordinary GNOME. Sitrep is as follows: Panels are not working. No response of any kind to my frantic klicking attempts. Also my system monitor indicates that one of my cpu cores is working at 100% continuously for some time now... Should I just delete all my panels and then add a completely new one? If so, how do I do this with terminal? What I should do?

---

### Post by audiomick on 2010-02-11
I would try looking in
system> administration> system monitor for what ever it is that is using so much cpu (resources tab, I think), and think about killing it. If it is gnome, you probably don't want to kill it...

---

### Post by lockalidiot on 2010-02-11
It appears to be gnome-panel, using from 92%-100% CPU.. Is it "safe" to kill it? What to do after killing it. btw, I cannot access those drop-down menus... Just absolutely 0(zero) response.

---

### Post by audiomick on 2010-02-11
No, I wouldn't kill that. I don't know enough about it, but fear that it might leave you without a GUI. It is obviously trying to deal with whatever you told it to do. I am getting out of my depth here, but I think I would let it go for a while and see if it gets through what ever it is trying to do. If it is still trying to carry out your last instructions, telling it to do more stuff might just lock it up more.

sorry that I can't be more help...:(

---

### Post by lockalidiot on 2010-02-11
It's ok. I appreciate every bit of advice I can get.
I suppose this is due me accidentally placing two panels at the same spot.

---

### Post by audiomick on 2010-02-11
> **lockalidiot said:**
> It's ok. I appreciate every bit of advice I can get.
I suppose this is due me accidentally placing two panels at the same spot.
That would be my guess. As I said, let it chew on it for a while. Maybe it will get somewhere. In the meantime, maybe someone else will have a better suggestion here...

---

### Post by lockalidiot on 2010-02-11
Hopefully... WHERE ARE ALL THE GURU PEOPLE!!! :P Help me!!

---

### Post by ElSlunko on 2010-02-11
Not a Guru. But you might want to reset your panels with :

```
rm -r ~/.gconf/apps/panel 
```



Log out then back in.

---

### Post by lockalidiot on 2010-02-11
I'm might give this a try. Any other opinions? Should I run this? I don't want to mess up my 'puter any more than I have to... Would that fix it? What that command does and what to do after that has been run?

---

### Post by philinux on 2010-02-11
> **lockalidiot said:**
> I'm might give this a try. Any other opinions? Should I run this? I don't want to mess up my 'puter any more than I have to... Would that fix it? What that command does and what to do after that has been run?

Open a terminal and use this.

```
killall gnome-panel
```

This will remove the panels and restart them. They will appear back where they were in 1 second flat.

---

### Post by ElSlunko on 2010-02-11
Try what phil said first.

If that doesn't work my suggestion pretty much removes the entry that contains the configuration for your gnome panels.

Your configurations are saved inside a hidden folder inside your Home directory called .gconf. You can also view your gnome configurations with "gconf-editor" which you can run from terminal or the run menu (alt+f2).

After removing it, logging out and logging in, gnome will recreate the folder with the default settings inside for gnome-panel.

Alternatively you could move the folder for backup purposes.

---

### Post by lockalidiot on 2010-02-11
Tried the killall, didn't work. I suppose I'll have to do it the hard way. It's just that I read about the "command of death" few moments ago and the "rm -r" kind of resembles it, so I wanted to get a confirmation about that one... Nothing personal! I just don't know all this stuff, so I'm rather too careful than not.

---

### Post by lidex on 2010-02-11
> **lockalidiot said:**
> I'm might give this a try. Any other opinions? Should I run this? I don't want to mess up my 'puter any more than I have to... Would that fix it? What that command does and what to do after that has been run?
Should work -- or this:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by lockalidiot on 2010-02-11
Thanks lidex! And equally everyone else! That last one worked, even though looked even more scary than the other rm -r command... I tried them all, just for record. The rm -r didn't work for some reason. I'll reboot now and well see how it goes.

---

### Post by audiomick on 2010-02-11
Looks like you are running again. Great.
For future reference, if you are unsure of a command, open the man page and try and work out what it does. In this case, it would have been
```
man rm
```
about the man pages themselves
```
man man
```

---

### Post by lockalidiot on 2010-02-11
Thank you again to everyone who so kindly offered their help and eventually made it possible to clean up this mess. I'm running smooth and clean!

---

### Post by rnerwein on 2010-02-11
hi

if something happens again it would be nice to run followin command in a root shell.
1. figure out the processes id of the running process.
if the runaway process take the time in system mode use "strace" if the  cpu usage is in user mode use "ltrace"

2 . run: strace -f -o process_debug.txt -p PID ( PID is the process of the runaway process )
    after about 3 or 4 seconds cancel the strace comand with "ctr c".

3. with strace you see all the systemcalls the process calls.
    (ltrace will show you the the library calls too ( huge output !!! )
4. if you can't figure out whats going on. developer will do. even if i am online and can see the output i can guess where the problem is. but don't forget to stop the trace because there is a lot of output. you will see how fast your cpu is !

ciao

---

