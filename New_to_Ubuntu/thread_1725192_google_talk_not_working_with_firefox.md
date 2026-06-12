---
title: "google talk not working with firefox"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by a.sarkar on 2011-04-09
Dear All,

Google talk browser plugin stopped working with firefox recently. Earlier it was working just fine. However seamonkey and chromium-browser still works nicely with the plugin.

When I run firefox from command line the error message it shows is:
```

LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk.so [/opt/google/talkplugin/libnpgoogletalk.so: cannot open shared object file: Permission denied]

```The permissions of the file in question are as follows which seems ok to me.
```
-rw-r--r-- 1 root root 267K 2011-01-12 04:58 libnpgoogletalk.so
```

Googling the topic I found that clearing cookies and caches might do the trick. However that didn't help either.
Any help would be appreciated.

---

### Post by a.sarkar on 2011-04-10
The version of firefox was 3.6.16, on my system (10.04 with openbox).
Downloaded the beta version of firefox - version 4.0b11 and used that. 
The beta version of firefox seems to work just fine, with google video plugin, without any problem.

So this is a workaround I guess - use the beta version of firefox instead of the one which
comes preloaded in ubuntu. Wonder if this is due the changes ubuntu makes to firefox or because old version of firefox is incompatible with google plugin.

Will check with latest stable version of firefox (version 4.0 instead of the beta) and see if that works.

---

### Post by a.sarkar on 2011-04-10
Tried firefox version 4.0 with google video plugin. Worked without a glitch.
So it was just firefox version 3.6.11 which was not compatible with the google video plugin.
Funny because it was working couple of weeks back.

---

### Post by supergirlkara on 2011-04-10
That's weird I wonder why google talk plugin stopped working? I use pidgin for my messaging services including google talk. It gets better with every update.

---

### Post by a.sarkar on 2011-04-10
Google talk plugin still works (with Firefox v4.0, Seamonkey, Chromium-browser). It just doesn't work with Firefox 3.6.16 - well at least not on my machine.

---

