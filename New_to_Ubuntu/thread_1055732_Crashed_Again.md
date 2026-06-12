---
title: "Crashed Again"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by MooseMagnet on 2009-01-31
This is the second time it's crashed in two weeks. This time I added some text to xorg.conf, trying to get the stupid touchpad to work. Trying to use gsynaptics, instead of synaptics - Intrepid on Dell Inspiron

It crashed when I restarted the laptop.

When it crashed, it displayed text only. These are the last few lines:

No resume image, doing normal boot...
Ubuntu 8.10 rich-laptop tty1
rich-laptop login:

Then I enter login and password, and it gives me the terminal prompt. I tried several things, but could not get the system back.

How can I get the system back if it does this again? This is the second time it's done it in the past 2 weeks. I've lost data and had to rebuild from iso disk each time.

Thanks.

---

### Post by MooseMagnet on 2009-01-31
Bump.

---

### Post by Nepherte on 2009-01-31
gsynaptics is simply a graphical program to change some settings of a synapticz touchpad. It's not some driver that can replace synaptics, it just uses synaptics. You could undo your changes in xorg.conf. You can edit the file with:
```
sudo nano /etc/X11/xorg.conf
```

You could also regenerate a xorg.conf file with:
```
sudo dpkg-reconfigure xorg-server
```

But perhaps you want to make a backup of the current one first before something totally screws it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

You might be able to figure out what's wrong by looking at /var/log/Xorg.0.log:
```
view /var/log/Xorg.0.log
```
or simply query the error messages:
```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by MooseMagnet on 2009-01-31
I would not understand what I was reading. 

Thanks anyway.

---

### Post by MooseMagnet on 2009-01-31
All I want to do is get the touchpad to work. But that seems to be asking way too much of Ubuntu. It worked perfectly in Dapper, Edgy, and Feisty.
But it's horrible in Intrepid. I was told Intrepid is the best for laptops. All I want to do is get the stupid touchpad to work.

---

### Post by Nepherte on 2009-02-01
Just post the output of:
```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by MooseMagnet on 2009-02-01
I got the touchpad working again. Really makes a difference. 

Here's the results:

rich@rich-laptop:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
rich@rich-laptop:~$ 

Mostly, I'm looking for what to do if/when it crashes to the text screen again. How to recover without rebuilding from the iso disk.

Thank you for helping.

---

