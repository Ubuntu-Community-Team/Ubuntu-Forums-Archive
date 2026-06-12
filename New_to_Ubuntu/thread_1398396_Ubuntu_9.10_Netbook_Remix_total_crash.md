---
title: "Ubuntu 9.10 Netbook Remix total crash"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Josheppe on 2010-02-04
So I tried out UNR 9.10 last night for the first time. I'm new to this whole Ubuntu thing if you already haven't guessed. Anyway, while I was messing around with the configurations, I decided that I'd clean the program list up more by removing some of the add-ons that I wouldn't use (games and such).

When I came across the Python program, it looked like I didn't need it from the description, so I proceeded to remove it. It allowed me to do it so I didn't think it would matter, but boy what was I wrong! After about 25% through uninstalling, my screen goes completely black and I'm prompted to input my username and password. The best way I can describe the screen is that it looked almost identical to the MS command prompt.

However, for no matter what I typed, it wouldn't accept it and I couldn't go anywhere or do anything to get out of it. When I power off my computer and when I try to go back into Ubuntu, the screen flickers a few times and all I'm left with is a black screen with pixel tears on it every time.

Is this something I did or is there an error somewhere? Long story short, I reinstalled everything completely and tried the same thing and it happened again this morning, so I'm guessing that there is a flaw somewhere. I'd really like to use this OS more but I think that this experience has ruined it for me. Any suggestions? Thanks.

---

### Post by snowpine on 2010-02-04
From the command line (the thing that looks like the DOS prompt), try typing:

```
sudo apt-get install ubuntu-netbook-remix
```

This should reinstall the things you removed and get you back to a default situation. Next time be careful uninstalling things! I haven't used the Software Center but there should some kind of "details" you can click to see exactly what's going to be removed. If other applications depend on something you remove (like Python), Linux will uninstall them all.

---

### Post by Josheppe on 2010-02-04
Thank you! I will remember that if it happens again, but I won't be touching that program if I reinstall a third time. I didn't think that one program could cause such a disaster, so I'm still not sure exactly what went wrong.

---

