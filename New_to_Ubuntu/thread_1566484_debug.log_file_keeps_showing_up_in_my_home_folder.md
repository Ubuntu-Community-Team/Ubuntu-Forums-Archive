---
title: "debug.log file keeps showing up in my home folder"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by libihero on 2010-09-02
what program is making it, and how can i stop it?

---

### Post by wesleybailey on 2010-09-02
Please post some of the sample text inside the debug log so I can find out what program is creating it.

Latest Tutorial: [Convert uif to iso file]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by OskO on 2010-09-02
Same thing happens to me, Im afraid there is not much to say about it since always is a nasty empty text file :(

---

### Post by libihero on 2010-09-03
ya mine is also an empty document

---

### Post by libihero on 2010-09-15
bump...

---

### Post by wesleybailey on 2010-09-15
I'm not sure how we can track down the program that creates the empty file. 

Have you recently added any programs, that do not come with the base ubuntu.

Just a thought.

Run this, and see if the user or group is different from the rest
```
ls -la
```

```
-rw-------  1 username  username      71536 2010-09-15 08:47 .debug
```

---

### Post by mtvoid on 2010-09-29
It's been bugging me too. After a bit of detective work, I've narrowed it down to the presence of the Google Talk browser plugin, I'm guessing that all of you seeing this problem have it installed too.

Additionally, I've noted that the problem only seems to be affecting applications using the Webkit library to display web pages (I've seen it with Liferea and Midori, but not Chromium, which does not depend on libwebkit provided by the system, or Firefox, which does not use Webkit). 

One doesn't need to actually use the Google Talk plugin for debug.log to be created. A visit to any web page that requires a plugin to display some content, e.g. Flash or Java, will trigger the creation of the file, as long as the Google Talk plugin files (libnpgoogletalk.so and libnpgtpo3dautoplugin.so) are also installed.

Another reference to this bug on a linux based system:
[https://bbs.archlinux.org/viewtopic.php?pid=825846](https://bbs.archlinux.org/viewtopic.php?pid=825846)

---

