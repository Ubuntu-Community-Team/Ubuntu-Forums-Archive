---
title: "Problems importing profiles to Firefox"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by uni-corn on 2010-04-19
So I am running 9.10 on my laptop and still have Windows 7 on my tower and I have been in the middle of migrating everything.

The last thing I need to do is make my Firefox on here look like the Firefox on my tower(bookmarks, extensions, etc.). Is there any way I can do this?

I copied the Mozilla Firefox folder from my tower and moved it to my laptop, but I can't seem to find where to put it.... It contains all of the profiles/extensions that I need, I just don't know the correct path here in this OS.

And FWIW, I won't be using FF once I finish, I just want to be able to import all of these things in to Chrome.


Thank you

-V

---

### Post by e4uforums on 2010-04-19
Bookmarks can be exported from Firefox by going to Bookmarks>Organize Bookmarks>Import and Backup.  You can use the same process to import them when you get to the new machine.

As for plugins and extensions, I would just install them on FireFox in Ubuntu.  There are some plugins that are OS specific, and the extensions (like flash) are definitely OS specific.

---

### Post by uni-corn on 2010-04-19
Oh my! Thank you so much, I was never aware that one could do this!

---

### Post by e4uforums on 2010-04-19
Glad it worked for you!

---

### Post by LowSky on 2010-04-19
For others who might read this, if you are moving bookmarks from to different verison of Firefox (lets say FF 3.0 to 3.5) it might not work properly, but you can save your bookmarks as a HTML file instead using nearly the same method

---

### Post by lovinglinux on 2010-04-19
> **e4uforums said:**
> Bookmarks can be exported from Firefox by going to Bookmarks>Organize Bookmarks>Import and Backup.  You can use the same process to import them when you get to the new machine.

As for plugins and extensions, I would just install them on FireFox in Ubuntu.  There are some plugins that are OS specific, and the extensions (like flash) are definitely OS specific.

+1

You could use [FEBE](https://addons.mozilla.org/en-US/firefox/search/?q=FEBE) extension to selective backup your FF profile without the extensions and restore it on the new system. Nevertheless, when migrating from Windows to Linux I also recommend exporting your bookmarks and starting your profile from scratch.

Firefox profiles are stored under ~/.mozilla/firefox

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

