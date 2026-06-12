---
title: "Two Monitors on Ubuntu 10.10"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by YankeeFan on 2010-12-21
Greetings,
I've installed Ubuntu 10.10 on a brand new Dell pc with two 23" monitors.  Through the initial install I could set up the monitors to be seen individually, meaning I could see different apps on each monitor.  After an update and a reboot, I now see the same items on both monitors.  It's as though Ubuntu now only sees one monitor.  I've gone through the System >> Preferences >> Monitors and tried to change those settings but nothing helps or works.  Also, the resolution has changed and I cannot restore it to the default settings.

I'm new to Ubuntu's internal set ups and config files so if anyone can help me with the scary details, I'd be very grateful.  

How do I restore the monitors to their actual resolutions and how do I get Ubuntu 10.10 to see both monitors as separate ones?

Let me know if I can provide any information.

Thanks for any tips.

---

### Post by seawolf167 on 2010-12-21
Try downloading your video driver software (assuming AMD/NVIDIA) and change the monitor options through the video software suite.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by YankeeFan on 2010-12-21
Thank you so much for your post.  I was able to get this working.

Notes:
I had to also go to System >> Preferences >> Monitors and make changes there also.  Using just the Graphics Card GUI, I would change the settings and reboot and I'd still see the same stuff on both monitors.

Your fix restored my resolution but not my refresh rate.  It should be 75 and I can only pick 60 (default?)

There also seems to be a delay in moving windows around my screens.  It seems to be some type of problem with the graphics accelerator, maybe?  This new system is smokin' fast and I shouldn't see this slowness effect.

Any thoughts on these?

Thanks a ton for the tip on fixing the two monitors seeing the same apps.

Much appreciated.
JohnC

---

### Post by seawolf167 on 2010-12-21
If you are using LCD monitors then the refresh rate isn't an issue (you only have to change it with old school CRT monitors).

After you get the driver software suite installed that should take over and run everything for you (you can play with the various settings for AA, crossfire, etc.). I have gotten lags before & after the driver install as well, the usual fix for me is:

Install drivers, reboot, adjust settings
Ensure compiz isn't causing problems (right click desktop, select change desktop background, select visual effects tab, turn off desktop effects)

If that works and there is no more lag, then slowly turn on the effects to find which one is causing problems (through CompizConfig-Settings-Manager)

If that doesn't work, uninstall all video drivers, re-download, reinstall, etc.

EDIT: Up till 10.04 I usually didn't bother with compiz since to me it seemed like way more trouble than it was worth for some fancy desktop effects

---

### Post by YankeeFan on 2010-12-22
Thanks for the reply.  Sorry for the lag in re-posting.

A co-worker tried to work on this and everything got bunged up.  I ended up doing a complete re-install of Ubuntu 10.10 and everything just worked this time.  Go figure.

Thanks again for all the help.

JohnC

---

