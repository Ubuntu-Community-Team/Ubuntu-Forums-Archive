---
title: "How can I uninstall Savage 2?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Kosimo on 2008-12-24
I've installed Savage 2 (native) for linux, and now I'm wondering how can I uninstall it.  Can you please give me a clue? ;)

Thank you!

---

### Post by halitech on 2008-12-24
how did you install it?

---

### Post by Kosimo on 2008-12-24
> **halitech said:**
> how did you install it?

By running the executable installer .bin then it appear an installer (GUI).

---

### Post by halitech on 2008-12-24
where did you get the .bin file? that site should have uninstall instructions

---

### Post by Kosimo on 2008-12-24
> **halitech said:**
> where did you get the .bin file? that site should have uninstall instructions

From the official savage2 site (which is a free game now)

doesn't really say anything about how to uninstall it... :(


[http://savage2.s2games.com/download.php](http://savage2.s2games.com/download.php)

---

### Post by ajgreeny on 2008-12-24
Have you looked in synaptic?  Programs often appear there even if not installed that way, and can be uninstalled using the normal synaptic options of *Remove* or *Remove completely*.

---

### Post by halitech on 2008-12-24
that has to be one of the poorest designed websites I've been on in awhile. Only thing I can find is you can email them at [email]support@s2games.com[/email] or use this page to send them a question [http://savage2.s2games.com/cs.php](http://savage2.s2games.com/cs.php)

---

### Post by Kosimo on 2008-12-24
> **halitech said:**
> that has to be one of the poorest designed websites I've been on in awhile. Only thing I can find is you can email them at [email]support@s2games.com[/email] or use this page to send them a question [http://savage2.s2games.com/cs.php](http://savage2.s2games.com/cs.php)

I know...  Thank you for the advice :) I'll contact them

---

### Post by Elvenrix on 2008-12-26
You can run the uninstaller in Savage 2 folder, note that you must sudo to do that.

---

### Post by Kosimo on 2008-12-26
> **Elvenrix said:**
> You can run the uninstaller in Savage 2 folder, note that you must sudo to do that.

I can't see the uninstaller.

---

### Post by Teabicky on 2008-12-26
Does this work?

> sudo apt-get remove Savage\ 2

---

### Post by Kosimo on 2008-12-26
> **Teabicky said:**
> Does this work?

It won't work as it haven't been installed by apt-get, so it doesn't even knows that Savage 2 is installed.  I think that what I can do is just remove the Savage2 folder in /usr/local/games/

---

### Post by nuytnie on 2008-12-26
If you just ran the installer .bin with the default options like I did, then you should see uninstall_Savage2.sh in your installdirectory (default /home/USERNAME/savage2

Just run that one and it should take care of your problem. Unless you can't find this script...

---

### Post by gaeanmage on 2009-01-03
yep.. that's right. from the Savage2 folder (not .savage2) run ./uninstall-Savage2.sh

---

### Post by krimedct on 2010-08-31
Running ./uninstall-Savage2.sh "worked" for me, it removed the entries from the menu (aplications/games) but I had to delete Savage2 folder manually.

---

### Post by openlord on 2011-03-23
I tried uninstalling Savage 2 from terminal but problem is a dialog box appears showing ' Fatal error deletion failed' with only an option to close it.Any other suggestions?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-04-18
> **openlord said:**
> I tried uninstalling Savage 2 from terminal but problem is a dialog box appears showing ' Fatal error deletion failed' with only an option to close it.Any other suggestions?
i got the same, but it deleted all the shortcut files inside the Games folder, but the savage files in the savage 2 folder is all still there, can i just delete that folder, that is located in my home derictory?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-04-18
anyoneeee?

---

### Post by dudejoe4 on 2011-06-29
I was getting the same error but I just added sudo and it uninstalled. 
sudo /usr/local/games/Savage2/uninstall-Savage2.sh
 
worked for me :D

---

