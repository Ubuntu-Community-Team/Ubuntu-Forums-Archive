---
title: "Clicking noise from hard drive while operating on battery power"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by sabatorious on 2009-09-03
Hello. I just made the jump from Windows to Ubuntu and its gone mostly smooth. I have a couple of issues, one of which really concerns me. There seems to be a clicking noise every 10 seconds or so coming from my hard drive. It only happens while I am on battery power, using Ubuntu (but not while using Windows). Once I plug in the laptop, the noise is gone.
 
I have researched a little bit on the internet and found that there is a little bit of chatter out there on the subject, but nothing very recent. Is there anything I can do to fix this? It concerns me, as it could potentially ruin my hard drive (and its very obnoxious to hear in class!). 
 
Thanks to anyone out there who can help this ex-Windows user in this new linux world.

---

### Post by scorp123 on 2009-09-03
> **sabatorious said:**
> There seems to be a clicking noise every 10 seconds or so coming from my hard drive. Did that disk do that before? Because from your description I'd say that your disk will die soon and take all the data with it into the digital Nirvana ...

Just to be sure, I'd recommend you compare the noise you hear with the noises from this web site:

[http://datacent.com/hard_drive_sounds.php](http://datacent.com/hard_drive_sounds.php)

Yes, no kidding: The guys there recorded typical sounds of dying hard drives. So if your disk sounds anything like one of their recordings I'd say it's time to buy a new disk.

---

### Post by Sealbhach on 2009-09-03
This could be the laptop load cycle bug. I used to suffer from it, but it was finally fixed for me in 9.04.

There's an epic thread about it here:

[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

What version of Ubuntu are you using?

If you want to test if this is your problem and to find out how to fix it, see the second post in that thread by UbuntuDemon.

.

---

### Post by scorp123 on 2009-09-03
> **Sealbhach said:**
> This could be the laptop load cycle bug. I didn't know about that one .... OK, that does sound quite plausible.

OK, forget my theory about the dying disk :D

---

### Post by sabatorious on 2009-09-03
I bought the laptop last saturday, so I hope the disk isn't dying!
 
I'm using version 9.04, so that seems weird to me that it would fix your click and mine still has a problem ... but I'll look at that post.   Thanks.

---

### Post by sabatorious on 2009-09-03
seems like a *very* technical fix.  I was hoping there was a simpler explanation.

---

### Post by Sealbhach on 2009-09-03
There's an easy way to check if this is what is happening. Go on battery, and if the clicking starts run this command in a terminal:
```

sudo hdparm -B 254 /dev/sda
```
To set it back to what it was before this is the command:

```
sudo hdparm -B 128 /dev/sda
```
These are just temporary commands, when you log back in your settings will revert to what they were before. But it might tell you if APM is the problem.

.

---

### Post by sabatorious on 2009-09-03
This command took care of the clicking. Thanks.

So is the only way to fix it to go through that tutorial that ubunto damon wrote up?

---

### Post by Sealbhach on 2009-09-04
> **sabatorious said:**
> This command took care of the clicking. Thanks.

So is the only way to fix it to go through that tutorial that ubunto damon wrote up?

Try it with the value of 128 while on battery:

```
sudo hdparm -B 128 /dev/sda
```
The "ugly fix" isn't that bad, I'll help you with that if you need to apply it, although it is already supposed to be fixed in Jaunty - but maybe not for your hardware.

.

---

### Post by myrelative on 2011-06-10
> **Sealbhach said:**
> Try it with the value of 128 while on battery:

```
sudo hdparm -B 128 /dev/sda
```The "ugly fix" isn't that bad, I'll help you with that if you need to apply it, although it is already supposed to be fixed in Jaunty - but maybe not for your hardware.

.

I have the same problem on 11.04, it is not fixed.
hardware is eee PC 1015px. hdparm -B 254 fixes it temporarily. value was 128 before. not a problem with ms windows.

---

