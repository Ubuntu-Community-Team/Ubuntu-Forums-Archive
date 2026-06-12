---
title: "Enabling PHP/HTML Code Highlighting in TXT files in GEdit"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Been Told on 2010-06-07
Hi everyone :)
I've been running Ubuntu on my Netbook for a few months and now I've installed it on my desktop. I'm moving away from Windows - apart from gaming.
Anyway, I've never had any problems and so: No problems = no experience.

I'm using the Firefox Addon itsalltext. It lets you open the content of a textarea in a text editor of your choice. It's stored as a .txt file (in the temp folder I believe) and opened in a specified editor - in my case it's the awesome GEdit.
A lot of the time it's HTML or PHP that I'm editing (making forum styles mostly), so it would be useful to have txt files automatically display as PHP (or at least HTML) files.

I've not been able to find anything on Google or on this forum, so I'll be grateful for any tips.

OT:
I am totally amazed at how user-friendly Ubuntu is. It's incredible!

---

### Post by Joeb454 on 2010-06-07
I believe you have 2 options - you can rename the file to the correct extension (i.e. somefile.php or somefile.html).

Alternatively, you can change the highlighting syntax in gedit from **View > Highlight Mode** and change it to HTML/PHP from there :)

---

### Post by Been Told on 2010-06-07
Thanks Joeb,
renaming is not an option as file is created and passed to Gedit on the fly. If I rename it, it doesn't automatically get passed back to Firefox when I save it in Gedit, which is the whole point of the itsalltext addon.
As for the other option - I can't believe I didn't spot that lol!
It certainly helps.

I would still like to be able to make Gedit code-highlight text files as if they were PHP or HTML though. Is there a plugin perhaps that can do this? Or some other way? I didn't find anything in the options.

---

### Post by sanderd17 on 2010-06-07
sorry, not working

I said:

```

cd /usr/share/gtksourceview-2.0/language-specs
sudo cp php.lang txt.lang

```

---

### Post by Been Told on 2010-06-07
That's perfect! Thanx sanderd!!!

---

### Post by sanderd17 on 2010-06-07
does it work with you? weird, it didn't work with me. But I found this:
[http://ubuntuforums.org/showthread.php?t=736843]("http://ubuntuforums.org/showthread.php?t=736843")

---

### Post by Been Told on 2010-06-07
Spoken too soon... Didn't work for me.

As for the article you linked to, I'm afraid it went right over my nooby head.

---

