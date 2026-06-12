---
title: "SH/DASH Simple Script to retrieve the video from Youtube / Dailymotion"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by honeybear on 2011-06-25
Hi, 

So here we have the video from firefox:

```
cd ~/.mozilla$ cp  firefox/qudi6lhi.default/Cache/2C9A22F2d01cp 2C9A22F2d01  dailymotion.avi
```

So, how to proceed? Size? Content? Extension?

```
$ type  
``` is not working... :( 

Any ideas to detect those videos?

---

### Post by TeoBigusGeekus on 2011-06-25
See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

---

### Post by lovinglinux on 2011-06-25
[Video Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/3006/") is the best. Keep in mind it might be against the EULA of some services to download the videos. Also watch for copyright issues. Don't redistribute the videos and don't store them for long term.

---

### Post by honeybear on 2011-06-25
> **TeoBigusGeekus said:**
> See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

the command takes ages....
```
lsof > checkurl
```

---

### Post by TeoBigusGeekus on 2011-06-25
The command should be
```
lsof | grep Flash
```

---

### Post by honeybear on 2011-06-25
> **TeoBigusGeekus said:**
> The command should be
```
lsof | grep Flash
```

Thank you but for unknown reasons it gives nothing.
Then I tried to do lsof simply alone, and it never stops ... I do not know. I hangs and always add something

---

### Post by TeoBigusGeekus on 2011-06-25
Ok, let's do it together.
Open a youtube page with a ***_[COLOR="Red"]VIDEO THAT YOU OWN[/COLOR]_***, and let it load completely.
Don't close the page, open a terminal and post us the output of
```
lsof | grep Flash
```

---

### Post by honeybear on 2011-06-25
Ah OK, now I see that sometimes it hangs. For x reasons, it works. 
I post now on your link to your thread a small code bash.

---

