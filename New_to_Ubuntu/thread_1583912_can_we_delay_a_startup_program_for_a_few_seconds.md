---
title: "can we delay a startup program for a few seconds?"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by sallam on 2010-09-28
Greetings
Sometime too much speed i not desirable!
ubuntu is too fast. That's great.
But I have Firefox in my startup programs list, and by the time it fires up and the 12 tabs of my home pages open, the wireless lan is still working to connect. This results in all tabs with error connecting.

Is it possible to delay Firefox so that it starts up a few seconds after startup and not immediately? I noticed there is a command that can be edited[PHP]firefox %u[/PHP]

---

### Post by SlugSlug on 2010-09-28
best way it to make a little script to launch firefox and launching that script at startup

```

#!/bin/bash
sleep 10;
exec firefox
exit
```

---

### Post by sallam on 2010-09-28
Many thanks.
Where do create that script? in gedit?
and what extension should it has please?

---

### Post by Tibuda on 2010-09-28
no need to create a script.
```
bash -c "sleep 10; firefox"
```

---

### Post by sallam on 2010-09-28
Thanks, but both solutions didn't work. The result was that Firefox didn't start at all..

---

### Post by TeoBigusGeekus on 2010-09-28
Try with this one
```
#!/bin/bash
sleep 10
firefox
```
Save it as firefox_launch.sh, make it executable (either right click it and check the allow executing option from the permissions tab or simply
```
chmod -x /path/to/file/firefox_launch.sh
```).
Then add this to your startup scripts:
```
sh /path/to/file/firefox_launch.sh
```
Don't forget to post us if you've made it.

---

### Post by lovinglinux on 2010-09-28
Alternatively, you could use [StayInOnlineMode]("https://addons.mozilla.org/en-US/firefox/addon/13233/") to keep Firefox connected and [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/") to prevent tabs from loading the content until you need them. This makes Firefox start faster and saves you some memory.

---

### Post by SlugSlug on 2010-09-28
sorry,

create that in what ever editor you want (gedit is fine)

save it to your home folder (if you start it with a . it will be hidden)

say ~/.firefox_startup

extensions dont really matter you just need to make it executable

chmod 770 ~/.firefox_startup

then add that to your startup applications

---

### Post by sallam on 2010-09-28
After restarting the laptop twice, Tibuda's command, typed in starup application window for Firefox, worked:
```
bash -c "sleep 20; firefox"
```
Thanks everyone for your wonderful help.

---

