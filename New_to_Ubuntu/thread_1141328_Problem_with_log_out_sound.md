---
title: "Problem with log out sound"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by linuxneeewb on 2009-04-28
I was recently able to fix the sound problems with my computer dealing with no sound at all in Ubuntu with the following post:

[http://ubuntuforums.org/showthread.php?t=1137642](http://ubuntuforums.org/showthread.php?t=1137642)

But, I still have a problem with the log out sound. I do not have the normal log out sound. When I log out I hear a loud beeping sound even if I have the sound muted. I would appreciate any help in fixing this problem.

Thanks

:popcorn:

---

### Post by Didius Falco on 2009-04-28
That sounds like it is your pc speaker. I hate that beep - shrill and loud.

Open a Terminal window and type ```
modprobe -r pcspkr
```.

Then log out or reboot. No annoying beep at logout? You can permanently turn off the pc speaker in Ubuntu by blacklisting it.

Open /etc/modprobe.d/blacklist.conf, scroll down to the end of the file and add:

```
#turn off pc speaker
blacklist pcspkr
```

Save and your done - you can do ```
modprobe -r pcspkr
``` again, unless you want to hear it one final time. After you log out and/or reboot, no more pc speaker.

---

### Post by linuxneeewb on 2009-04-28
I tried the command:

modprobe -r pcspkr

and got:

FATAL: Error removing pcspkr (/lib/modules/2.6.28-11-generic/kernel/drivers/input/misc/pcspkr.ko): Operation not permitted

I did do in System -> Preferences -> Sound and turned off alert sounds.

By the way, I have an HP TX2500 Tablet PC. I hope that does not mean the drivers are significantly different.

Any more help in resolving this problem is appreciated. 

:guitar:

---

### Post by Didius Falco on 2009-04-28
What version of Ubuntu are you using?

---

### Post by linuxneeewb on 2009-04-28
I am using Ubuntu 9.04.

---

### Post by Didius Falco on 2009-04-28
Did you try the command with a sudo in front, i.e. :

```
sudo modprobe -r pcspkr
```Have you added this setting:

 ```
#turn off pc speaker
blacklist pcspkr
```

to the  /etc/modprobe.d/blacklist.conf file? That's the important step - the one that will silence the pc speaker in Ubuntu from now on.

---

### Post by linuxneeewb on 2009-04-28
I used the command 
sudo modprobe -r pcspkr
and it does prevent the annoying beeping sound when logging off, but you have to do it every time. If you do not use the command
sudo modprobe -r pcspkr
it will beep. 

Also, I do not want to permanently turn off my speakers. I want to be able to use them. Any more help is appreciated. 

:lolflag:

---

### Post by Didius Falco on 2009-04-28
Adding that setting only turns off the pc speaker - the little tiny one inside your pc case. It won't turn off any other speakers.

---

### Post by linuxneeewb on 2009-04-29
Well that seems to have turned off the annoying beeping sound when I log off, but I still can't hear the official Ubuntu log off sound. 

:lolflag:

---

