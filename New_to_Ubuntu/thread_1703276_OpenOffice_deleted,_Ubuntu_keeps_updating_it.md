---
title: "OpenOffice deleted, Ubuntu keeps updating it"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by zaivala on 2011-03-09
I deleted OpenOffice.org. It's too big, too slow, and not compatible enough with Office.  I've installed Gnome Office (AbiWord, Gnumeric) which takes care of 2 of those 3 problems.

But when I run updates, Ubuntu wants to "update" my OpenOffice.

What do I do to get Ubuntu to stop checking for OpenOffice?

I'm running Karmic on a 2001 Sony Vaio laptop. I've tried Lucid (slower) and Maverick (can't load, no Unity drivers). Karmic runs fine.

---

### Post by Perfect Storm on 2011-03-09
Have you checked synaptic Package Manager from leftovers of OpenOffice?

---

### Post by Paddy Landau on 2011-03-09
How did you delete it? Did you manually delete the program files, or did you uninstall it through the Software Manager (package manager)?

If you just deleted the files, the package manager won't know about it. You need to uninstall it, through one of Ubuntu Software Manager, Synaptic Package Manager or apt-get.

---

### Post by zaivala on 2011-03-09
I uninstalled it through the Ubuntu Software Center. Where I may have made the mistake is, I did that just after installing, and before running updates.

I noticed that, before running Updates, Gnome Office was "not available", but after it was and I installed it. However, I'm still getting the OpenOffice updates when the Update Manager runs.

AI, I will check Synaptic.

---

### Post by false truths on 2011-03-09
When you remove OpenOffice, you have to do it through the terminal to get rid of everything.

```
sudo apt-get remove --purge openoffice*.*
```

That's what I used to remove OpenOffice completely when I switched to LibreOffice.

[URL="http://i1-news.softpedia-static.com/images/extra/LINUX/large/libreofficeubuntu-large_001.jpg"]
[/URL]

---

### Post by owiknowi on 2011-03-09
in synaptic package manager, right click on installed software and choose 'mark for complete removal' usual does the trick too.

in my personal opinion it's best to remove (purge) unwanted software before updating.

---

### Post by zaivala on 2011-03-09
Thank you both. I'm booting the laptop to try your suggestion.

I'm trying Terminal first. Says it will remove 221 Mb of stuff. Yayy. Done.

Now running Update Manager. Success!

---

