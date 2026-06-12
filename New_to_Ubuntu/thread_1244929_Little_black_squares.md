---
title: "Little black squares"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-08-20
[IMG]http://img22.imageshack.us/img22/1659/screenshothfj.png[/IMG]
There's these black squares around the applications bar.
They're there no matter what program I have open, it just starts up like that.

---

### Post by SoftwareExplorer on 2009-08-20
Do you have desktop effects enabled? What happens when you move the windows? Do the dots follow the windows?

---

### Post by Elep.Repu on 2009-08-20
> **SoftwareExplorer said:**
> Do you have desktop effects enabled? What happens when you move the windows? Do the dots follow the windows?

No sir, the dots do not follow the windows.
I have desktop effects enabled, the dots stayed when I disabled the effects.

[update]
I did:
```
sudo dpkg-reconfigure xserver-xorg
```

and it was fixed.
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by kerry_s on 2009-08-20
those look like dead pixels.
i've only seen it that bad on macs.

---

### Post by Elep.Repu on 2009-08-20
When I did the above command, it worked, but after a restart my bar is looking like this:

[[IMG]http://img38.imageshack.us/img38/3630/screenshotcrd.png[/IMG]]("http://img38.imageshack.us/i/screenshotcrd.png/")

And sure, I tried the command again, but restart still leads to the same thing.

[turns out running the command doesn't do anything, it's just the *switching in and out of single user mode* that makes it look normal.]

---

### Post by kerry_s on 2009-08-20
wow, that is so strange. have you tried changing your theme?

---

### Post by Elep.Repu on 2009-08-20
Changing the theme does nothing.

I restarted and it happened again,
goes away temporarily by going into single mode and back into regular mode.

Logging out and logging in does not make the problem reoccur, only restarting.

---

### Post by kerry_s on 2009-08-20
i'm thinking driver issue then, try using the "vesa" driver & see if that happens.

---

### Post by Elep.Repu on 2009-08-20
> **kerry_s said:**
> i'm thinking driver issue then, try using the "vesa" driver & see if that happens.

I'm sorry, how do I do that?

---

### Post by Elep.Repu on 2009-08-20
I went to Hardware Drivers, within the System menu, and supposedly another version of an nvidia driver was being used. I reactivated the top one (but I think I was running a better one before), and the dots moved back to the Applications menu again.

---

### Post by philinux on 2009-08-20
I've experienced this a couple of times before. I think it was the nvidia driver or compiz. The dots used to move about too. 

One thing to try is changing your theme and updating to make sure you got the latest graphics driver.

---

### Post by Elep.Repu on 2009-08-21
I gave up, after trying everything, and just reinstalled..(like usual.) (Sounds like Windows.)

---

### Post by themusicalduck on 2009-08-21
Just as a suggest in case it happens again, you can download the latest NVidia drivers from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

They're usually more up to date than the version in the repos.

---

### Post by ibuclaw on 2009-08-21
> **Elep.Repu said:**
> I gave up, after trying everything, and just reinstalled..(like usual.) (Sounds like Windows.)

and this resolved the issue?

---

### Post by Elep.Repu on 2009-08-21
> **tinivole said:**
> and this resolved the issue?

Yes, actually.

---

