---
title: "Ear Candy has broken my music playing"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by cpcpcp on 2011-04-03
Ear Candy is Bad. It has broken sounds & I  can't remove Ear Candy as the package is reported broken:(  So I seem snookered.
I try to play music (MP3, Ogg whatever) in VLC or Totem and the volume control fades down to zero. I push it up and it fades down again. ie manually changing the apps volume (e.g. for Totem) just results in a  battle for the app volume that EC wins, continually pushing it back to  zero.
 
How do I get rid of Ear Candy please  / fix the problem?

It seems to be known bug of Ear candy
[https://bugs.launchpad.net/earcandy/+bug/608876](https://bugs.launchpad.net/earcandy/+bug/608876)

It is un-installing the broken package that I cannot handle?

PS for those who follow the link and look at the bug what is this Pulse thing? :confused:

---

### Post by Dutch70 on 2011-04-03
(.pulse) is a folder where your settings are stored. (it is "dot"pulse btw) 

Have you tried uninstalling from synaptic package manager? 

If not, give that a shot, but first while you're in synaptic, click the "edit" button and select fix broken packages. See if you can uninstall from within synaptic then. Mark it for "complete removal" 

You may also want to try opening a terminal and running...
```
sudo apt-get -f install
```

Then...
```
sudo apt-get remove earcandy 
```
and...
```
sudo apt-get --purge earcandy
```

---

### Post by cpcpcp on 2011-04-03
> **Dutch70 said:**
> (.pulse) is a folder where your settings are stored. (it is "dot"pulse btw) 

Have you tried uninstalling from synaptic package manager? 

If not, give that a shot, but first while you're in synaptic, click the "edit" button and select fix broken packages. See if you can uninstall from within synaptic then. Mark it for "complete removal" 

You may also want to try opening a terminal and running...
```
sudo apt-get -f install
```Then...
```
sudo apt-get remove earcandy 
```and...
```
sudo apt-get --purge earcandy
```

Synaptic Package manager said it had fixed the dependency but
when untalling and it has been going for awhile now a window opened titled 
Debcon on cjp-desktop
which said 
General type of mail configuration:
and the drop down box gave the options of 
no configuration 
Internet Site - (visible)
Internet with smart host
satellite system
or Local only

Since Earcandy ought to have nothing to to do with email I will quit now and try your other instructions  - it will not let me stop the process so it is reset time - leaving according to the warning the system in a broken state, bed and look again tomorrow

---

### Post by cpcpcp on 2011-04-04
For now I have disabled ear candy in  startup applications and restarting has fixed teh problem.

I will have a go later at removing this dreadful prog.

Thanks for your help Dutch70

---

### Post by Dutch70 on 2011-04-04
Your welcome, hope everything goes well for you.

---

