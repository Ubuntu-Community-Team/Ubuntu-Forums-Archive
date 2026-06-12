---
title: "syntax on script"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-02-20
is this script note or how would you change not i want to run beachbit (a cleanup app note though it has a confirm dialog displayed after you select files to clean and before it does not have to run with sudo . note i run periodically./tks

#!/bin/bash
sudo rm -rf /tmp/*
bleachbit &
sudo shutdown -r now

---

### Post by Paddy Landau on 2010-02-20
You might want to explain your question more clearly. I haven't understood what you've written.

---

### Post by rburkartjo on 2010-02-20
okay to be more clear i want to run this at shutdown bleacbit is a cleaner file that cleans the chromium cache etc it always asks for a confirmation before it runs i want to make sure it runs . then the next:sudo rm -rf /tmp/* and finally the last: sudo shutdown -r now

---

### Post by Paddy Landau on 2010-02-20
There's no need to clear /tmp. Linux does that automatically.

If you want to run bleachbit first, then don't use '&' -- that will cause it to start in the background, and then the shutdown will start immediately, causing bleachbit to end.

Here's your script:
```
#!/bin/bash
bleachbit
sudo shutdown -r now
```There is a way to tell Linux to run bleachbit as part of the shutdown process, so all you do is shut down, and Linux will automatically run bleachbit. But, I don't know how to do that; perhaps someone on this forum will chip in and let you know how to do that.

---

### Post by rburkartjo on 2010-02-20
tks paddy will leave this thread open for awhile to see if anyone can answer how to do this at shutdown

---

### Post by Paddy Landau on 2010-02-20
I see that you [already asked this question]("http://ubuntuforums.org/showthread.php?t=1394968") earlier this month. Did the method suggested not work for you?

You may have some luck looking up the following:

[LIST]
[*]update-rc.d
[*]invoke-rc.d
[*]init.d
[*]rc0.d, rc1.d, ..., rc6.d and rcS.d
[/LIST]
However, I vaguely remember something about these methods being superseded by a new method in 9.10. Sorry, that's all I remember.

---

### Post by rburkartjo on 2010-02-21
paddy no i couldnt that to work but the changes to the script that you provided work great. i will just run periodically/tks

---

### Post by Paddy Landau on 2010-02-21
> **rburkartjo said:**
> ... the changes to the script that you provided work great. i will just run periodically/tks
Good, I'm glad to hear.

You can place a launcher on your panel, so when you want to turn off, just click the launcher instead of the usual turn-off process.

Right-click your panel and select Custom Application Launcher.

---

### Post by rburkartjo on 2010-02-21
good idea paddy just did that

---

