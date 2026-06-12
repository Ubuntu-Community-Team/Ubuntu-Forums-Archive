---
title: "Cron issues"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Ninja_of_Techno on 2009-04-15
I am having trouble getting cron to execute my commands entered into crontab.  Here is my crontab file:```

# m h  dom mon dow   command
20 *  * * *  sh /home/david/sh/test2.sh
```

My other question is, does it matter if you use space, tab, or the number of spaces between the different "fields" in a crontab line?

I have established that cron is running and I have restarted it, it just won't execute the command when the time comes.  The command works fine when I execute it manually.

Any help would be greatly appreciated!

---

### Post by Hospadar on 2009-04-15
try replacing sh with /bin/sh

Also you can check cron errors by typing "mail" at a command line (it'll tell you which mail viewer to install, do that)

---

### Post by mprince on 2009-04-15
I think single spaces do matter in this part.

```
20 *  * * *
```


So it should read like this:

```
20 * * * *
```

---

### Post by Ninja_of_Techno on 2009-04-15
Okay, I installed mail and made the minor adjustments recommended by both of you.  The cron job still failed to run.  However, after the time it was supposed to run passed I ran mail and had a message.  It was an error in accesing the x server.  My question now is this: is it be possible to run a shell script using cron and have that shell script start amarok? Below is my script. ```

#!/bin/bash
amarokapp /home/username/Music/Playlists/playlist.m3u;
```

Best I can tell this should work just fine.  Unless cron has some limitation I don't know about.  I used the same cron job shown above with the proper space formatting.

---

