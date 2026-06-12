---
title: "Google Chrome behaves abnormally after Upgrade."
date: 2010-10-18
forum: New to Ubuntu
---

### Post by babloo75 on 2010-10-18
I upgraded my system from Ubuntu 10.04 to 10.10 through Update manager. Previously I was using Google Chrome, and had removed it from the system before upgrade. Now after reinstalling it, a pop up window opens whenever I start Google chrome. It says:

"Your profile can not be used because it is from a newer version of Google Chrome.
Some features may be unavailable. Please specify a different profile directory or use a newer version of Chrome."

Is there any remedy for this problem? Please help.
Thanks in advance...

---

### Post by ibizatunes on 2010-10-18
if you go into nautilus and show hidden file 
 /home/<user>/.config/google-chrome
and rename that to google-chrome.old your should then install chrome and it should work out the box OK, had a similar issue myself

---

### Post by babloo75 on 2010-10-18
> **ibizatunes said:**
> if you go into nautilus and show hidden file 
 /home/<user>/.config/google-chrome
and rename that to google-chrome.old your should then install chrome and it should work out the box OK, had a similar issue myself

I am sorry to ask, but where can I find 'nautilus'?

---

### Post by ibizatunes on 2010-10-18
the file manager in gnome is call nautilus
so top tool bar > place > home (then you will be in nautilus)

---

### Post by babloo75 on 2010-10-18
> **ibizatunes said:**
> if you go into nautilus and show hidden file 
 /home/<user>/.config/google-chrome
and rename that to google-chrome.old your should then install chrome and it should work out the box OK, had a similar issue myself

I am not able to find ".config/google-chrome"

---

### Post by GrouchyGaijin on 2010-10-18
Go to your home folder and hit Ctrl + H on the keyboard.

---

### Post by babloo75 on 2010-10-18
Thanks a lot

---

### Post by cejack on 2010-10-24
Same exact problem.  Did the above renaming of the config folder and Google Chrome still bites the dust when I load a web page.  Sadly happens to both Chromium and Google Chrome...

---

### Post by tajiknomi on 2010-10-24
[SIZE=2]*use **gksudo nautilus** in Terminal in order to enter as a root.......*[/SIZE]

---

### Post by babloo75 on 2010-10-24
For me, it is behaving normally now.
Thanks

---

### Post by cariboo on 2010-10-24
> **tajiknomi said:**
> [SIZE=2]*use **gksudo nautilus** in Terminal in order to enter as a root.......*[/SIZE]

You don't need to be root to mv/cp/rename/delete files in your home directory. You also don't use gksu in a terminal. To use gksu press Alt-F2 and type the command in the box that pops up.

---

### Post by cejack on 2010-10-24
Still screwed.  Google Chrome just spontaneously closes when it tries to surf a web page.  Same thing for Chromium.  Opera and Firefox work just fine though.  Guess I won't be using google chromium or chrome for any web browsing for a long time.  This happened when upgrading from 10.04 to 10.10 Ubuntu.

---

### Post by cejack on 2010-10-24
SOLVED - libmoon package was causing a segmentation fault.  Whatever the heck that is....

Remove libmoon or update to the latest release from Novell for Moonlight 3 pre-release package at least eliminates the crashing / closing behaviors of both Chromium and Chrome.  

Download here:

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

[http://www.go-mono.com/moonlight/prerelease.aspx](http://www.go-mono.com/moonlight/prerelease.aspx)

---

