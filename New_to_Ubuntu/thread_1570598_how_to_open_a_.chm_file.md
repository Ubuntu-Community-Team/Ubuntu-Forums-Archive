---
title: "how to open a .chm file?"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by listerdl on 2010-09-08
I ran into a number of .chm viewers for Linux, all available within the Ubuntu repositories.

As a Gnome user I did this: sudo aptitude install gnochm

But it still doesnt open the .chm file - any ideas?

thanks

---

### Post by JohnHeikkila on 2010-09-08
try installing "xchm", it's a cross-platform program so it could work.
Or then the .chm file isn't a "Microsoft Compiled HTML Help" file.
Maybe it's a "ChemDraw Chemical Structure file".

---

### Post by Paul820 on 2010-09-08
Just right click on the file, select open with other application and choose your app. If the app isn't in the list you can browse to it by adding the path. If you don't know the path, open a terminal and type
> whereis yourAppName
Obviously replacing 'yourAppName' with the application you want to use. It will (usually) be in /bin

---

### Post by sikander3786 on 2010-09-08
> **listerdl said:**
> I ran into a number of .chm viewers for Linux, all available within the Ubuntu repositories.

As a Gnome user I did this: sudo aptitude install gnochm

But it still doesnt open the .chm file - any ideas?

thanks
Myself using gnochm without any problems. It opens up and runs fine for me.

If not already done this, right click on any .chm file, go to properties and in the "Open With" select "gnochm" what happens?

Does running "gnochm" without the quotes from a terminal, give any errors?

---

### Post by cguy on 2010-09-08
Nothing opens a .chm correctly.

KCHM is the best of all, as far as I can remember.

---

### Post by Paul820 on 2010-09-08
> **cguy said:**
> Nothing opens a .chm correctly.

KCHM is the best of all, as far as I can remember.

I have never had any problems with xchm, works fine for me.

---

### Post by dilantha on 2010-11-20
> **JohnHeikkila said:**
> try installing "xchm", it's a cross-platform program so it could work.
Or then the .chm file isn't a "Microsoft Compiled HTML Help" file.
Maybe it's a "ChemDraw Chemical Structure file".

Thanks...It worked for me..:)

---

### Post by cmcanulty on 2010-11-20
chmsee has always worked well for me

---

### Post by orewacrazy on 2012-05-09
> **cguy said:**
> Nothing opens a .chm correctly.

KCHM is the best of all, as far as I can remember.

I always using chmsee and work well on me \\:D/

---

### Post by sadaruwan12 on 2012-05-10
Your problem is that your .chm files are not associated with any program to open it so you've to manually assign a program.

do the following right click on a .chm file -> then go to properties -> Go to Open With tab -> If gnoshm is not there press "Show other Applications" button from there select gnochm then press "Set As Default" button.

Now all your .chm files are associated with the gnochm program when you double click on one of them they'll open up in gnochm.

---

### Post by elporsche907 on 2012-08-16
Hi  Everybody, I do really hope all of you are doing so great, answering your question I opened a terminal window and installed xchm library in my ubuntu applying the following command:

[I][B]sudo apt-get install xchm
[/B][/I]
Afterwards I selected the interesting file, click right button on my mouse cursor and selected the option "xchm" and then the file was opened!!!!!

Try it!!!!!

Greetings my friends!!!!

---

### Post by wildmanne39 on 2012-08-16
Thanks for sharing. Thread Closed.

---

