---
title: "screen resolution change - getting no desktop"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-01-23
i changeed the screen resolution.....

after this i got a black screen..

i switched off..

and restarted... 

got username > password > black screen again 

how to get back ubuntu ??????

i am now in xp

---

### Post by kimikrishna on 2009-01-23
i enterd all options in recover mode on boot up.....

is there any possible way to change resolution from root command prompt from recoverey menu ?

---

### Post by kimikrishna on 2009-01-24
reply ? ! ? !

---

### Post by SunnyRabbiera on 2009-01-24
Hmm, you did try recovery mode right?
This place gets busy so no wonder you got a bit lost.

---

### Post by kimikrishna on 2009-01-24
friend , did you read my prevos posts  ??

I tried all the options in recover mode....

i open that shell root command prompt.. 

what to enter in that to get my screen ??

*this is what I get username > password > a black screen *

---

### Post by kimikrishna on 2009-01-24
no reply ???????? :( :( :(

now, i am in xp again..

havent use xp for 4 weeks after ubuntu.. :confused:

---

### Post by overdrank on 2009-01-25
Ok what is the model of the graphics card and what version of ubuntu are you using?
Have you tried the xfix option in recovery mode?
You may try the command ```
sudo dpkg-reconfigure xserver-xorg
``` from the command line.

---

### Post by kimikrishna on 2009-01-25
Intel (R) 82945G express chipset family

this is my  g card..

and i think its ubuntu 81.0
 [ i got the cd to home , so isnt it the latest ? ]

---

### Post by overdrank on 2009-01-25
> **kimikrishna said:**
> Intel (R) 82945G express chipset family

this is my  g card..

and i think its ubuntu 81.0
 [ i got the cd to home , so isnt it the latest ? ]

Ok have you tried the commands and xfix option that I suggested previously.

---

### Post by kimikrishna on 2009-01-25
i tried fix "xserver" option...

and that command .. i entered.. i cannot understand how to get back..

> sudo dpkg-reconfigure xserver-xorg

i cannot understand what to do with this.. 

TELL STEP BY STEP...

---

### Post by overdrank on 2009-01-26
> **kimikrishna said:**
> i tried fix "xserver" option...

and that command .. i entered.. i cannot understand how to get back..



i cannot understand what to do with this.. 

TELL STEP BY STEP...

Ok so the xfix option in recovery mode did not help you get back to your desktop correct?

If you want you may try, boot normally and use the ctrl, alt, F1 keys when you reach the login window. You will need to login on the command line. Same user name and password that you use normally.  Then use these commands ```
sudo /etc/init.d/gdm stop

```
then ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then
```
sudo /etc/init.d/gdm start

```
Hopefully this will return you to the desktop.

---

### Post by babloo75 on 2009-01-26
I had similar problem, may be it is of some help to you:

[http://ubuntuforums.org/showthread.php?t=1016537](http://ubuntuforums.org/showthread.php?t=1016537)

---

### Post by dollzii on 2009-01-27
Maybe you could change your resolution back in

```
~/.config/monitors.xml
```

---

### Post by Roadbloc on 2009-01-27
I dunno wheather this has been mentioned but it may be that ubuntu doesnt recognise your graphics card. If that is the case id reinstall and either just not bother changing the resolution or download a driver off add/remove.

I apologise if this is of no help. Maybe installing within xp may help....

---

### Post by kimikrishna on 2009-01-27
> **overdrank said:**
> Ok so the xfix option in recovery mode did not help you get back to your desktop correct?

If you want you may try, boot normally and use the ctrl, alt, F1 keys when you reach the login window. You will need to login on the command line. Same user name and password that you use normally.  Then use these commands ```
sudo /etc/init.d/gdm stop

```
then ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then
```
sudo /etc/init.d/gdm start

```
Hopefully this will return you to the desktop.

Thanks ovrdrank ! :popcorn:

THankssssssss..  :D

my probm is now 100% solved !! ;):KS

---

