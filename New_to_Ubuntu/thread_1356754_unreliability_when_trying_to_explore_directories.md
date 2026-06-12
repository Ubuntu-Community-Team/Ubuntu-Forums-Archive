---
title: "unreliability when trying to explore directories"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by koba101 on 2009-12-16
ok...i wanted to post this problem 'cause i found it be persisting in the last few days, i have to log out and in to get stuff working

when i explore a folder I sometimes see the cursor loading and nothing being displayed in the directory

[IMG]http://i45.tinypic.com/5akxaq.png[/IMG]

it shows no files, even though there are at least 4

i logout and back in and i see them

---

### Post by philinux on 2009-12-16
How about pressing F5 to refresh the folder view.

---

### Post by koba101 on 2009-12-16
tried that..won't work..and one time it got even worse, it just showed me SOME of the files, for some reason it did not show me the PDF files

---

### Post by Chesamo on 2009-12-16
Do you have the proper permissions to view/open the files in that directory?

---

### Post by philinux on 2009-12-16
Open your home folder. ctrl h to show hidden. Navigate to .gconf/apps and rename the nautilus folder to nautilus.bak

Logout then in. Nautilus will then have it's default settings.

You can restore the folder if need be.

I just tried this with no problem.

---

### Post by koba101 on 2009-12-16
i do have the proper permisssion,

I'll try philinux's suggestion and keep monitoring the system see if something like this happens again

---

