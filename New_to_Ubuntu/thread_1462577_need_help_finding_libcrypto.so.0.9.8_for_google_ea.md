---
title: "need help finding libcrypto.so.0.9.8 for google earth"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by lsc on 2010-04-25
I'm actually making progress in getting Google Earth to run in 8.10.  A great hint from [http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/](http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/) told me to unplug the Ethernet which allowed me to go into GE and disable startup tips. While I was there, I turned off atmosphere. Now the globe spins great; GE only crashes when I put it to work.

Reinstalled into my home directory where I can find the darn folder. Many posts suggest changing the name of libcrypto.so.0.9.8 in the google-earth folder to something else, but I don't see it. Is there a different location? I'm sure I shouldn't be messing with random ones.

Thanks!

Lorne

---

### Post by sandyd on 2010-04-25
> **lsc said:**
> I'm actually making progress in getting Google Earth to run in 8.10.  A great hint from [http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/](http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/) told me to unplug the Ethernet which allowed me to go into GE and disable startup tips. While I was there, I turned off atmosphere. Now the globe spins great; GE only crashes when I put it to work.

Reinstalled into my home directory where I can find the darn folder. Many posts suggest changing the name of libcrypto.so.0.9.8 in the google-earth folder to something else, but I don't see it. Is there a different location? I'm sure I shouldn't be messing with random ones.

Thanks!

Lorne
type ```

googlearth
```
in a terminal, and then when it crashes, c&p the terminal output

---

### Post by lsc on 2010-04-25
[QUOTE=carlee;9174524]type ```

googlearth
```
in a terminal, and then when it crashes, c&p the terminal output[/QUOTE

lorne@dell-desktop:~$ googlearth
bash: googlearth: command not found
lorne@dell-desktop:~$

---

### Post by oldos2er on 2010-04-25
That should be **googleearth**

---

### Post by lsc on 2010-04-25
> **oldos2er said:**
> That should be **googleearth**

Thankyou; I tried that as well. I take it no command needed?

Lorne

---

### Post by sandyd on 2010-04-25
> **lsc said:**
> Thankyou; I tried that as well. I take it no command needed?

Lorne
means you dont have google earth installed properly
here, enter this
leave the defaults in the installer
```

wget -c http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sudo sh ./GoogleEarthLinux.bin

```
then post back if theirs error messages.
and mind mi millions of typos, I do them all the time... (and yes, I sometimes spell my with mi, that was on purpose)

---

### Post by lsc on 2010-04-25
> **carlee said:**
> means you dont have google earth installed properly
here, enter this
leave the defaults in the installer
```

wget -c http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sudo sh ./GoogleEarthLinux.bin

```
then post back if theirs error messages.
and mind mi millions of typos, I do them all the time... (and yes, I sometimes spell my with mi, that was on purpose)

I'll work on that, have to uninstall first, I'll check back in 40. 

lorne

---

### Post by lsc on 2010-04-25
> **lsc said:**
> I'll work on that, have to uninstall first, I'll check back in 40. 

lorne

After deleting previous install and reinstalling via Terminal, GE launched correctly. Putting it to work produced-

lorne@dell-desktop:~$ googleearth
Mesa 7.0.3-rc2 implementation error: i915_program_error: Can't (yet) swizzle TEX arguments
Please report at bugzilla.freedesktop.org
Mesa 7.0.3-rc2 implementation error: i915_program_error: Can't (yet) swizzle TEX arguments
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/lorne/.googleearth/crashlogs/crashlog-4bd505f5.txt

Please include this file if you submit a bug report will to Google.

---

### Post by sandyd on 2010-04-25
> **lsc said:**
> After deleting previous install and reinstalling via Terminal, GE launched correctly. Putting it to work produced-

lorne@dell-desktop:~$ googleearth
Mesa 7.0.3-rc2 implementation error: i915_program_error: Can't (yet) swizzle TEX arguments
Please report at bugzilla.freedesktop.org
Mesa 7.0.3-rc2 implementation error: i915_program_error: Can't (yet) swizzle TEX arguments
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/lorne/.googleearth/crashlogs/crashlog-4bd505f5.txt

Please include this file if you submit a bug report will to Google.
now THATs not a google bug. Its a bug with the mesa 3d libraries.

[s]brb.. ill look it up...[/s]

Thats a bug with the current version of mesa thats for your ubuntu release (8.10)
you can either upgrade, or add [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

and then update all your packages.

uggh. and I just ate 1 L of yogurt and now I feel a bit sick...

---

### Post by lsc on 2010-04-25
> **carlee said:**
> now THATs not a google bug. Its a bug with the mesa 3d libraries.

[s]brb.. ill look it up...[/s]

Thats a bug with the current version of mesa thats for your ubuntu release (8.10)
you can either upgrade, or add [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

and then update all your packages.

uggh. and I just ate 1 L of yogurt and now I feel a bit sick...

Thanks, Carlee-

I'd be game for updating Mesa if I knew how. I was holding on to LTS 8 for a few weeks anyway with 10 imminent. Do I need to compile? (Yogurt's great stuff and can't upset you more than drinking a couple glasses of milk.)

Lorne

---

### Post by sandyd on 2010-04-26
> **lsc said:**
> Thanks, Carlee-

I'd be game for updating Mesa if I knew how. I was holding on to LTS 8 for a few weeks anyway with 10 imminent. Do I need to compile? (Yogurt's great stuff and can't upset you more than drinking a couple glasses of milk.)

Lorne

8.10 is not a lts, do you mean 8.04? in this case, just upgrade to 10.04 right now. theirs only... 3 days left, and upgrading early is a good way to avoid the slowness of the downloading rush. b sure to back up your data first. or you can simply add the repository I linked to, and then update all the packages through the update manager.

---

### Post by lsc on 2010-04-26
> **carlee said:**
> 8.10 is not a lts, do you mean 8.04? in this case, just upgrade to 10.04 right now. theirs only... 3 days left, and upgrading early is a good way to avoid the slowness of the downloading rush. b sure to back up your data first. or you can simply add the repository I linked to, and then update all the packages through the update manager.

You're correct-I've 8.04, not 8.10, and the Ubuntu-X says its packages are for Intrepid and later. So I'm guessing it's safer just to upgrade to Lucid.

Thanks!

Lorne

---

