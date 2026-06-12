---
title: "Where is Thunderbird (icon?)"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by smileyguy on 2009-04-24
Synaptics tells me that Thunderbid is installed but I can't find it under the **Applications** menu.

Any tips?

---

### Post by Teabicky on 2009-04-24
Try this

Go to System> Preferences> Main Menu

From here go to internet and see of it is there.  If it is check the box and it should appear in your applications menu.

---

### Post by smileyguy on 2009-04-24
Not there:(

Firefox is there - that's not it is it . . .

---

### Post by El Zoido on 2009-04-24
Restart and check if it's there afterwards.
Works most of the time for me.

If not, open a console and type thunderbird to see if it starts.
If it does it is indeed installed.
You could then add a new starter on your own.

---

### Post by smileyguy on 2009-04-24
Restarted and not there:(

I reinstalled it via Synaptics (just using the reinstall option then restarted). I have the **Evolution Mail** app though. I don't think that's it though.

---

### Post by El Zoido on 2009-04-24
No, Evolution is a different App
It's not bad though, I use it on Ubuntu.
Of course, its all about personal taste...

---

### Post by LowSky on 2009-04-24
It wont be on the panel but under 
Applications > Internet > Thunderbird


open a terminal and type

```
thunderbird
```

---

### Post by smileyguy on 2009-04-24
When I enter that into the console I get the message:

[COLOR=Navy]The program 'thunderbird' is currently not installed.  You can install it by typing:
sudo apt-get install thunderbird
bash: thunderbird: command not found[/COLOR]

********************************

Then when I enter the command ([COLOR=Navy]sudo apt-get install thunderbird)[/COLOR] to install it I get this message:

[COLOR=Navy]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/COLOR]
Using Evolution for now but would like to try Thunderbird (especially since trying to get it working learns me so much!)

---

### Post by Flyingjester on 2009-04-24
that means the package manager is working, wait a bit, and try again.

---

### Post by kanikilu on 2009-04-24
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Do you by any chance still have Synaptic open? If so, close it before running apt-get.

---

### Post by BUKRITYA on 2009-04-24
This message usually means you have another package manager running. 
First try to close synaptic, update manager, adept etc. and check other desktops to see if any are open there. Then try the command again. If still the same message, then hit System->Administrarion->System Monitor and look something that might be locking the package database.

---

### Post by LowSky on 2009-04-24
Something tells me that you didn't install it

in synaptic click to install thunderbird and then at the top click on apply (usually a green checkmark)

or from terminal ```
sudo apt-get install thunderbird
```

---

### Post by smileyguy on 2009-04-24
> **kanikilu said:**
> Do you by any chance still have Synaptic open? If so, close it before running apt-get.
ah thanks - stupid me. seems to be working now thanks kanikulu.

It seems to be downloading now via that console command - was just about to download it manually from mozilla and try installing it myself (with gdebi).

---

### Post by smileyguy on 2009-04-24
All worked thanks. Apparently it was installed in the first place btu couldn't seem to find it.

Install from console worked:)

---

