---
title: "Moodle install"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by cacs on 2011-05-28
Hi. I want to install the moodle in my pc, but i'm not being able to.
LAMP is ok: 
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.


But how to run moodle on it?


TY, C.S.

---

### Post by trozamon on 2011-05-28
I would suggest a quick google search or a trip to Moodle's website, which will lead you to their tutorials. Please don't ask questions that can be easily answered by a little bit of effort on your part. Anyways, here's a link:

[http://docs.moodle.org/en/Administrator_documentation](http://docs.moodle.org/en/Administrator_documentation)

---

### Post by terrykiwi83 on 2011-05-28
Yep as trozamon said you really need to ask the people over at Moodle that question. There are plenty of how-to's on their website.

---

### Post by cacs on 2011-05-29
Thank you, but of course I tried a google search and moodle's tutorials first! :(
Because I couldn't do it I tried to go for help on system forum, don't seem so bad after all!

---

### Post by cacs on 2011-05-29
> **trozamon said:**
> I would suggest a quick google search or a trip to Moodle's website, which will lead you to their tutorials. Please don't ask questions that can be easily answered by a little bit of effort on your part. Anyways, here's a link:

[http://docs.moodle.org/en/Administrator_documentation](http://docs.moodle.org/en/Administrator_documentation)

From the site above and [tuxtweaks.com]("http://ubuntuforums.org/tuxtweaks.com") i was able after much work accomplish it! :)

---

### Post by binkles on 2011-05-29
You need to put all the moodle files into /etc/www
Put them in the root of www if you want or in a folder IE: /etc/www/moodle

Create a database in phpmyadmin

Navigate to the moodle files in your browser.

Follow the onscreen install instructions.

---

