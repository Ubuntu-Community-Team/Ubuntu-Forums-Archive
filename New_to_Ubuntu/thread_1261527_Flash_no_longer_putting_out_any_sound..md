---
title: "Flash no longer putting out any sound."
date: 2009-09-08
forum: New to Ubuntu
---

### Post by osc1882 on 2009-09-08
So, I come home and my computer has been rebooted. Not sure why. Maybe the wife did it, don't know. 
Anyways, now flash videos no longer put out any sound. Everything else does, just not flash. I think I might have done a system update yesterday or the day before but I don't remember doing one that said I needed a restart.
Any idea's guys, I'm going crazy. 
Thank you.

---

### Post by j.bell730 on 2009-09-08
Taken from [this]("http://ubuntuforums.org/showpost.php?p=5678390&postcount=9") post.
Since you already have the Flash plugin, you don't need to download it, therefore, you should do this:
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox-addons/plugins
```

Then, if you run 64-bit:
```
sudo cp /usr/lib/libflashsupport.so /usr/lib32/
```

---

### Post by osc1882 on 2009-09-08
Thank you, I tried that and it didn't work... kinda. More info...
I cranked my speakers WAY up and then I could hear it, a little tiny bit.
I have all of my sound settings turned up that I can control (computer software end and youtube interface). Is there any way that it could be turned down in pulse? I find it interesting that pulse was added back in the day because it is able to control each program by themself, yet we have no gui to control things by and when it was first rolled out there was a lot of bugs from switching to a new sound system by default.

---

### Post by osc1882 on 2009-09-08
Shameless Bump.

---

### Post by osc1882 on 2009-09-09
Shameless bump the next day. lol.

---

### Post by osc1882 on 2009-09-09
Ok, so I fixed it
Some how it got turned down by pulseaudio and I was able to turn it back up by installing and useing " pavucontrol ". Good program. Maybe it should be encluded in Ubuntu by default.

---

