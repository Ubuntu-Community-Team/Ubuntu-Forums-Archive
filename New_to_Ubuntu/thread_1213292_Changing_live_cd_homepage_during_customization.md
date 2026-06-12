---
title: "Changing live cd homepage during customization?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-07-14
Is it possible to do this, anyone the file I have to change to do this? I am in customization right now for the 8.04.2 hardy desktop, anyone know how to edit a file so i can save the changes to the live cd.

---

### Post by ericeclifford on 2009-07-15
1 day  bump :0

---

### Post by ericeclifford on 2009-07-15
I tried putting this into the prefs.js file, but didnt work.

user_pref("browser.startup.homepage", "www.google.com")

---

### Post by ericeclifford on 2009-07-15
I Guess I could try it by, opening up the firefox browser before I compress it into a iso image, and change the preferences homepage to [www.google.com](www.google.com) and see if it saves.

---

### Post by Cheesemill on 2009-07-15
Set up Ubuntu just how you want it then use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a custom Live CD of your installation.

---

### Post by ericeclifford on 2009-07-15
> **Cheesemill said:**
> Set up Ubuntu just how you want it then use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a custom Live CD of your installation.

I do not want to use that :( I am using a script for my customization and want to learn the config files and stuff.

---

### Post by ericeclifford on 2009-07-15
anymore suggestions? I looked for hours trying to find an solution for this particular problem.

---

### Post by ericeclifford on 2009-07-17
Kind of solved, I had to apt-get remove ubufox which had a .jar file that set my home page.

And I also had to remove firefox-branding.js because the first time you launch firefox on a live cd or a hard disk install it will go to a page under a pref line in that file.

And I confured browsersettings files thats in the firefox-3.0.10 folder, not the best fix but a fix, still trying to find out if I need firefoxbranding.js or ubufox for anything special on the live cd and a better fix.

---

