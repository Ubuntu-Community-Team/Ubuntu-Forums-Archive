---
title: "chromium web browser backup"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-12-12
does anyone know of a good way or a program to backup the profile. all the ones i have found are exe files only. if anyone has an idea or has found and used a  program that works please share. really like this browser but also wise to backup. tks

---

### Post by x33a on 2009-12-12
Right now, i don't think there is anysuch extension available for linux.

I think, you can make a script and use cron to backup your chromium stuff on a regular basis.

---

### Post by rburkartjo on 2009-12-12
x33 tks for the reply pretty sure you are right but will leave this thread open just incase anyone has found something. i was thinking of just copying the .config/chromium/ file but must be an easier way

---

### Post by lovinglinux on 2009-12-12
Create a new text file called **chromiumbackup.sh** or whatever you like, then paste this:

```
#!/bin/bash

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

tar cvf ${HOME}/chromiumprofile-${TODAY}-${NOW}.tar ${HOME}/.config/chromium
```

Make the file executable, then create a launcher pointing to that file.

Can't get easier than that.

---

### Post by rburkartjo on 2009-12-12
cool beans loving /tks

---

### Post by rburkartjo on 2009-12-12
loving one more thing what would be the proper command to reinstall the backup/tks

---

### Post by lovinglinux on 2009-12-12
> **rburkartjo said:**
> loving one more thing what would be the proper command to reinstall the backup/tks

Something like this:

```
mv ~/.config/chromium ~/.config/chromium_old
tar -xf ~/chromiumprofile-[COLOR="DarkRed"]**XXXXXXXX-YY:ZZ**[/COLOR].tar
```

Where the values in red are the date and time of the backup.

---

### Post by rburkartjo on 2009-12-12
again loving tks

---

### Post by x33a on 2009-12-12
Also, if you use ```
tar cvzf
```

 you'll get a gzipped tar, that'll save you some space.

---

