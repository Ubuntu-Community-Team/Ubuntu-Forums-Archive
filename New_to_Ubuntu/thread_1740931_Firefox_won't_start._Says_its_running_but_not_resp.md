---
title: "Firefox won't start. Says its running but not responding."
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Nahjil on 2011-04-27
I have been getting the attached error message for several days every time I try to start firefox. I am currently using chromium, but this is bothering me. Would like to figure it out and get it fixed. If anyone can help it would be greatly appreciated. I would like to figure out how to see what processes are running as well. Thank you for your time.

---

### Post by Nahjil on 2011-04-27
Also I have tried restarting. It doesn't change anything.

---

### Post by dniMretsaM on 2011-04-27
I have this same problem (with FF4, not sure what you're running). I posted it in the Firefox 4 thread at the top of this section and am waiting for an answer. Chromium is nice, but it's missing some small things (ie no "Set as Background" option for pictures) that will keep me on FF for now. Probably for a long time now that the speed has greatly increased with the release of 4.

---

### Post by Fedz on 2011-04-27
Have you tried System > Admin > System monitor?

---

### Post by CoffeeRain on 2011-04-27
You could try going into Terminal and typing ```
killall Firefox
``` This should kill the Firefox process.

---

### Post by Nahjil on 2011-04-27
Thank you I had not. But I do not see any processes with mozilla or firefox running or sleeping.

---

### Post by dniMretsaM on 2011-04-27
Been there done that. Nothing. I also tried killalling firefox-4.0 and firefox-trunk. And if there WAS a process running, rebooting would take care of it. I've also tried reinstalling but that didn't help either.

---

### Post by Nahjil on 2011-04-27
alex@Lucy:~$ killall Firefox
Firefox: no process found
alex@Lucy:~$ 

This is the output I get, though I still get the same error message...

---

### Post by dFlyer on 2011-04-27
Have you tried moving your .mozilla folder to .mozilla_old than try starting the firefox program from the commandline.

---

### Post by dnairb on 2011-04-27
Have a look at

~/mozilla/firefox/[random letters].default/

In this folder, there is a file called lock when Firefox is running. If it is there, and Firefox is not running, try deleting it with sudo privileges.

---

### Post by CoffeeRain on 2011-04-27
The only thing I can think of is that you may have set it to open at login and it crashed at some point and it will keep trying to run again. Though you reinstalled it, so I guess that's not right.

---

### Post by aktiwers on 2011-04-27
```
top | grep firefox
```

```
killall firefox-bin
```?

---

### Post by dniMretsaM on 2011-04-27
I'll give those a try dnairb and aktiwers.

EDIT:```
top | grep firefox
```
Does nothing.
```
killall firefox-bin
```
No process found.

EDIT #2: No lock file. The only lock-like file is called parentlock.

---

### Post by dniMretsaM on 2011-04-27
> **dFlyer said:**
> Have you tried moving your .mozilla folder to .mozilla_old than try starting the firefox program from the commandline.

Tried this and it worked!!!

---

### Post by Nahjil on 2011-04-27
Alright well ~/mozilla/firefox/ doesn't exist. I tried searching mozilla and found six folders none of them containing firefox folders, I searched for firefox and found quite a few folders only one containing a folder with a default folder (no random letters) and no lock program. Any advice on completely removing firefox and reinstalling?

---

### Post by dniMretsaM on 2011-04-27
it's .mozilla not mozilla. It's a hidden file in your home directory. Press Ctrl+H and scroll down till you see it.

---

### Post by Nahjil on 2011-04-27
Well moving the .mozilla folder seems to have worked. Though I would like some info as to why and how to avoid it so it doesn't happen again.

---

### Post by dnairb on 2011-04-27
> **dniMretsaM said:**
> it's .mozilla not mozilla. It's a hidden file in your home directory. Press Ctrl+H and scroll down till you see it.

:oops: yeah, sorry my typing mistake

---

### Post by dFlyer on 2011-04-27
> **Nahjil said:**
> Well moving the .mozilla folder seems to have worked. Though I would like some info as to why and how to avoid it so it doesn't happen again.

Something in the hidden folder was corrupted. Moving the folder just recreated it. If there is nothing in the folder you can't replace you might just want to deleted the moved folder.

---

### Post by Nahjil on 2011-04-27
Thank you again. This has been bothering me for a week.

---

### Post by dFlyer on 2011-04-27
> **Nahjil said:**
> Thank you again. This has been bothering me for a week.

No problem, glad I could help. One thing you might want to think about is a plugin or extension added to firefox could have caused the problem in the first place.

---

### Post by Nahjil on 2011-04-28
I am currently running noscript adblock plus and a google toolbar. I was running fastest fox but, with the wipe I think I'll forgo it. Thank you for all your info.

---

### Post by lovinglinux on 2011-04-28
I recommend deleting the mozilla folder only as last resort, since there are important stuff inside it, like bookmarks and passwords.

Take a look at [my tutorials]("http://www.webgapps.org/blogs/firefox-tutorials"), there are several tips on how to troubleshoot and optimize Firefox on Ubuntu.

---

### Post by dniMretsaM on 2011-04-28
Well for me, there were none of those things since it was a fresh install.

---

### Post by lovinglinux on 2011-04-28
> **dniMretsaM said:**
> Well for me, there were none of those things since it was a fresh install.

In such situation, is easier to do that. But if you have a long lasting profile, then the user will most likely to want to keep his stuff.

---

### Post by Daliolores on 2011-05-06
hey there! i started firefox using the console by typing "firefox"! it told me that there is a problem with the vlc mozilla plugin. deinstalling the plugin solved the problem.

---

### Post by lovinglinux on 2011-05-06
> **Daliolores said:**
> hey there! i started firefox using the console by typing "firefox"! it told me that there is a problem with the vlc mozilla plugin. deinstalling the plugin solved the problem.

Use gecko-mediaplayer instead of vlc.

---

### Post by Daliolores on 2011-05-08
i'll have a try. thank you.

---

