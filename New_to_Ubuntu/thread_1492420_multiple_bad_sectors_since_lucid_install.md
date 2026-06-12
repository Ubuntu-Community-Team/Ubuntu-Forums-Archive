---
title: "multiple bad sectors since lucid install?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by ghostofzuul on 2010-05-24
since i've installed lucid, when booting up between the splash screen and the desktop i get lines of multiple i/0 errors. 

i checked disk utility and it's reporting multiple bad sectors on my hard drive
 
i don't think that the lucid install is the culprit but since i have no idea i was curious if anyone thinks it's related. 

not worried about the hard drive, i have a back up formatted and ready to go if this one goes nuclear. 

thanks.

---

### Post by bodhi.zazen on 2010-05-24
All hard drive have bad sectors, even when new.

There was a bug report about this behavior in karmic, I do not have the link handy, but you can probably find it if you search.

So long as you have back ups you probably do not need to do anything further.

If you are interested you can look at smartmontools

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by sandyd on 2010-05-24
> **bodhi.zazen said:**
> All hard drive have bad sectors, even when new.

There was a bug report about this behavior in karmic, I do not have the link handy, but you can probably find it if you search.
**-> [https://launchpad.net/bugs/438136](https://launchpad.net/bugs/438136)**
So long as you have back ups you probably do not need to do anything further.

If you are interested you can look at smartmontools

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
This bug doesn't apply anymore in lucid, because a fix was released.

---

### Post by ghostofzuul on 2010-05-24
> **bodhi.zazen said:**
> All hard drive have bad sectors, even when new.

There was a bug report about this behavior in karmic, I do not have the link handy, but you can probably find it if you search.

So long as you have back ups you probably do not need to do anything further.

If you are interested you can look at smartmontools

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

good to know. thanks a lot for the info. i'll have to install smartmontools for sure.

---

### Post by sandyd on 2010-05-24
Wrong thread...

---

### Post by nhasian on 2010-05-24
you can get more detailed information about your drives by going to System-> Administration-> Disk Utility.

You can see how many bad sectors it has, check the SMART status, run tests on it, etc.  if you have 1 or 2 bad sectors its not a big deal, but if it says you have 150 bad sectors then its time to replace the drive :)

---

### Post by bodhi.zazen on 2010-05-24
> **carlee said:**
> This bug doesn't apply anymore in lucid, because a fix was released.

Ah good to know, thank you. I was never affected by the bug in question so I have not been tracking it.

---

### Post by warfacegod on 2010-05-24
I'm not entirely convinced that Palimpset isn't still throwing false positives in Lucid. I just install 10.04 64 bit onto a brand new laptop and no sooner do I boot into it, Palimpset tells me there are 300 some odd bad sectors. Checked it with gsmartcontrol, no bad sectors. To test this, I reinstalled 10.04. This time it says there are 80 something bad sectors. gsmartcontrol still says 0.

Palimpset has done this on every single HDD I have used in various computers in the last 9 months.

Any way:

```
sudo apt-get install gsmartcontrol
```

If it says your drive passes, you're likely just fine.

Go to: System> Prefs.> Startup Apps.> disable Disk Notifications.

No more messages. Even better, use Synaptic and get rid of Palimpset entirely.

---

### Post by ghostofzuul on 2010-05-25
i installed gsmartcontrol and both discs passed and don't show any errors. 

however, disc utility shows that i have bad sectors on the hard drive that has my OS. 

i might try to uninstall palimpset to see if that makes a difference. 


in another thread i mentioned my 2nd hard drive doesn't show up in "places" any more and in order to be able to mount it i have to go to disk utility. i'm curious if this is all related. what's more, when i first start my machine, disk utility doesn't populate. i usually have to wait about a half hour after i turn on my machine before it's functional.

---

### Post by philinux on 2010-05-25
Disk utility or gnome-disk-utility is palimpsest.

And it looks like it's still got problems like karmic.

---

### Post by bodhi.zazen on 2010-05-25
> **carlee said:**
> This bug doesn't apply anymore in lucid, because a fix was released.

It appears to still be problematic, perhaps a different bug ?

I would suggest reporting this behavior as a bug report on launchpad.

---

### Post by ghostofzuul on 2010-05-25
also interesting to note that i did NOT experience these issues in jaunty or karmic. not until i upgraded to lucid did the errors occur.

i reported it as a bug:

[https://bugs.launchpad.net/ubuntu/+bug/585525](https://bugs.launchpad.net/ubuntu/+bug/585525)

although i've never reported a bug before so i'm not sure i did it properly.

---

### Post by warfacegod on 2010-05-25
You may have had the bug but didn't know because Disk Notifications was disabled in Startup App.

---

