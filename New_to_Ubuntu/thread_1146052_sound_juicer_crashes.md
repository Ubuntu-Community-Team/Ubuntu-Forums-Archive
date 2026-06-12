---
title: "sound juicer crashes"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by al.adab on 2009-05-02
hello

does anyone know why sound juicer crashes (ubuntu 9.04) when I click "Extract" after inserting a music CD? It closes itself down.

---

### Post by hansdown on 2009-05-02
Hi al.adab.

There are a few bug reports, but I haven't found any helpful solutions.

Possibly it will be fixed with an update.

[http://www.google.ca/search?q=sound+juicer+crash+in+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=sound+juicer+crash+in+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Ericyzfr1 on 2009-05-02
Did you try to reinstall it? I use it a couple of days ago, it crashed on the first attempt, then worked fine. I did have to install it from the repos.

---

### Post by al.adab on 2009-05-02
I did reinstall it...and it magically worked it! Thanks!

---

### Post by PTo on 2009-05-04
I had the same problem and unfortunatly reinstalling didn't help. Then I found this [bug report ]("https://lists.ubuntu.com/archives/desktop-bugs/2007-February/078904.html") and I saw that the songs had no name indeed. When I named all the songs it worked!

---

### Post by reylafo on 2009-05-18
Solved this problem by doing the following:

cd ./.gconf/apps
mv sound-juicer sound-juicer.bak

Restart sound-juicer "aka. Audio CD Extractor"

This rebuilds the "conf" file, then sound-juicer worked OK.

---

### Post by konsty on 2010-04-09
> **PTo said:**
> I had the same problem and unfortunatly reinstalling didn't help. Then I found this [bug report ]("https://lists.ubuntu.com/archives/desktop-bugs/2007-February/078904.html") and I saw that the songs had no name indeed. When I named all the songs it worked!
Thanks! worked for me.

---

### Post by alfh on 2010-05-16
sound-juicer crashes when extracting a song with empty/null name

This bug has been around at least since 2007. Hope somebody who knows how to fix it reads this thread and fixes it. I would if I could...

Meanwhile, make shure to name your songs. It'll save you the frustrations of looking for another ripping program.

---

### Post by rlue on 2010-09-21
> **reylafo said:**
> Solved this problem by doing the following:

cd ./.gconf/apps
mv sound-juicer sound-juicer.bak

Restart sound-juicer "aka. Audio CD Extractor"

This rebuilds the "conf" file, then sound-juicer worked OK.

This did it for me

---

### Post by rudecam on 2011-12-23
i've tried the solution listed above but none worked for me. sound juicer still crashes on me.
any other idea?
other programs for ripping audio files?
i use ubuntu 10.04

---

