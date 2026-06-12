---
title: "Fixing Rhythmbox Lyrics Plugin"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by mvalviar on 2009-05-23
Rhythmbox's lyrics plugin is not working when I run RB in the terminal I get this error when I try to fetch some lyrics.

```

File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Not Found

```

How do I fix this?

---

### Post by mvalviar on 2009-05-24
*********************** up ***************************

---

### Post by chrisod on 2009-05-24
I'd try uninstalling and reinstalling the plugin and also checking to make sure you have the most recent version. Also find the web page for the plugin and make sure it is compatible with whatever version of Rhythmbox that you are using.

---

### Post by mvalviar on 2009-05-26
The plugin is installed by default in Jaunty. I trien installing the whole package (rhythmbox) it didn't fix it. Anymore ideas?

---

