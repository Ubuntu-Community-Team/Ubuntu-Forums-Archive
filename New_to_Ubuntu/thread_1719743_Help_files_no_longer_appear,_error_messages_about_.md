---
title: "Help files no longer appear, error messages about xml"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by O Gopal on 2011-04-02
About a week ago I installed Maverick. Now my help files no longer properly appear. 

More precisely: I can access the "Ubuntu Help Center" page and go one level below that -- for example, to "Connecting to the Internet" ("Ways of Connecting") -- but not deeper. 

At first the help messages came up in Firefox as what seems to be xml text -- English text with lots of tags -- with an error message: [INDENT][COLOR=Blue]This xml file does not appear to have any style information associated with it. The document tree is shown below.[/COLOR]
[/INDENT]I used Synaptic to uninstall and reinstall Yelp. The same for ubuntu-docs. Anything that seemed relevant.

After a while, I instead got a message like this:[INDENT]    [COLOR=Blue]XML Parsing Error: undefined entity
   Location: file://///usr/share/gnome/help/internet/C/internet.xml#connecting-wired
   Line Number 14, Column 1:<book lang="&language;" id="internet">
^[/COLOR]
[/INDENT]Consulting this thread -- [http://ubuntuforums.org/showthread.php?t=1682845&highlight=docbook+xml](http://ubuntuforums.org/showthread.php?t=1682845&highlight=docbook+xml) -- I figured that perhaps the help files were set to open with the wrong application.

Checking the file referred to in the error message, I saw it was set to open with Firefox. That seemed wrong, but setting it to any other available program listed -- for example, Document Viewer or Text Editor -- doesn't work. (Error message: "Unable to open document. File type Microsoft Virtual Topic Definition. File (application/xml) is not supported."

There's an option to set "Custom" as the application to use, but it seems one is expected to supply a command, and I wouldn't know what to set. 

And so I am at a dead end. 

I am totally green to Ubuntu. Migrating from Windows. Clean install of Maverick from Live CD. 

Can I think of anything I did to cause the problem to begin with?

I had installed Kmymoney and later thought some sort of KDE conflict might be the cause. So I uninstalled the program. (hadn't entered any data into it yet). But the problem remained.

Before the problem appeared, I had also (following a forum post) manually edited the "Locales" file, changing "en_ZA" to "en_US." (At installation, when the routine had asked me where I was, I had simplemindedly answered "South Africa," which was true -- but I'm an American and need American localization.) I don't know whether editing that file caused the trouble or not.

Now I am literally helpless -- at least when offline. So I would be most grateful for guidance from online.

Thank you.

---

### Post by O Gopal on 2011-04-04
Since I had only installed Ubuntu about a week ago, and since I had a full backup of my data, I simply reinstalled everything. That, of course, solved the problem. 

Lessons learned:

[LIST=1]
[*]You can easily and safely change locales here: System-->Administration-->Language Support. On the "Language" tab choose your language, on the "Text" tab choose the format you prefer for displaying numbers, dates, and currency.
[*]Hey, newbie, stay out of the system files! You shouldn't need to mess with them, and you're better off staying away from them till you're more experienced (and perhaps even then).
[*]When you look to a forum post for advice, take note of the date of the posting. Old advice may no longer be right.
[*]Kmymoney was innocent. Installing Kmymoney will **not **mess up your help system.
[*]Reinstalling can be a very good strategy.
[/LIST]

---

### Post by O Gopal on 2011-04-06
Now the issue has truly been solved. 

After a fresh install of Ubuntu, I installed e-Sword and MS Office under CrossOver Linux, and the problem reoccurred. 

Jack Phinney, tech rep from Codeweavers, responded with admirable swiftness:

------------------------------

As for your help menu system - I think you've found a new bug in Crossover.  I
endeavored to re-create your setup with an Ubuntu 10.10 32-bit machine and a
fresh install of Crossover.  With just Crossover, and Crossover + eSword, the
help system was fine.  After I installed MS Office 2007, I saw the same
problem.  When I deleted the MS Office 2007 bottle but left e-Sword, the help
system worked fine.

I think what you're seeing is caused by some devious behavior in the manner
that Crossover sets up MS Office file associations. I've created a bug report
for our developers to investigate.

Now, to try and fix this problem, go into Crossover's Manage Bottles menu.
Click on your Microsoft Office 2007 bottle, and then Control Panel, and open up
"Edit Associations".  Un-check "show common file types only", and then scroll
down to the bottom.  Locate the ".xml" extensions, and change them both to
"Ignore extension".  Then click "apply" and "ok".

If you now go to your help menu, does it work?

------------------------------

It did work. That does solve the problem. And shows the value of high-quality tech support.

---

### Post by frank cox on 2012-02-05
Personally I prefer e-sword, I have used it for many years. However :The Word" is just as good and will run all the modules from e-sword. It is a no-brainer to install under wine, just ignore the one error message at the start and that is that.



> **O Gopal said:**
> About a week ago I installed Maverick. Now my help files no longer properly appear. 

More precisely: I can access the "Ubuntu Help Center" page and go one level below that -- for example, to "Connecting to the Internet" ("Ways of Connecting") -- but not deeper. 

At first the help messages came up in Firefox as what seems to be xml text -- English text with lots of tags -- with an error message:[INDENT][COLOR=Blue]This xml file does not appear to have any style information associated with it. The document tree is shown below.[/COLOR]
[/INDENT]I used Synaptic to uninstall and reinstall Yelp. The same for ubuntu-docs. Anything that seemed relevant.

After a while, I instead got a message like this:[INDENT]    [COLOR=Blue]XML Parsing Error: undefined entity
   Location: file://///usr/share/gnome/help/internet/C/internet.xml#connecting-wired
   Line Number 14, Column 1:<book lang="&language;" id="internet">
^[/COLOR]
[/INDENT]Consulting this thread -- [http://ubuntuforums.org/showthread.php?t=1682845&highlight=docbook+xml](http://ubuntuforums.org/showthread.php?t=1682845&highlight=docbook+xml) -- I figured that perhaps the help files were set to open with the wrong application.

Checking the file referred to in the error message, I saw it was set to open with Firefox. That seemed wrong, but setting it to any other available program listed -- for example, Document Viewer or Text Editor -- doesn't work. (Error message: "Unable to open document. File type Microsoft Virtual Topic Definition. File (application/xml) is not supported."

There's an option to set "Custom" as the application to use, but it seems one is expected to supply a command, and I wouldn't know what to set. 

And so I am at a dead end. 

I am totally green to Ubuntu. Migrating from Windows. Clean install of Maverick from Live CD. 

Can I think of anything I did to cause the problem to begin with?

I had installed Kmymoney and later thought some sort of KDE conflict might be the cause. So I uninstalled the program. (hadn't entered any data into it yet). But the problem remained.

Before the problem appeared, I had also (following a forum post) manually edited the "Locales" file, changing "en_ZA" to "en_US." (At installation, when the routine had asked me where I was, I had simplemindedly answered "South Africa," which was true -- but I'm an American and need American localization.) I don't know whether editing that file caused the trouble or not.

Now I am literally helpless -- at least when offline. So I would be most grateful for guidance from online.

Thank you.

---

