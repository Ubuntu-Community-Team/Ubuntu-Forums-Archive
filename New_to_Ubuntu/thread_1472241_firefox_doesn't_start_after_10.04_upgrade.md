---
title: "firefox doesn't start after 10.04 upgrade"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by dwhite on 2010-05-04
Just upgraded to 10.04 (from karma) last night, tried to start firefox, seems to begin loading then just stops.  have reinstalled with synaptic same thing happens.

any ideas?

---

### Post by ibuclaw on 2010-05-04
Open home directory, show hidden files/folders (by pressing "Ctrl+H") - and look for a directory named **.mozilla**

Rename it to ie: **.mozilla-old** and try again.

NOTE: this will start you with a clean new profile. All saved passwords / browsing history won't be carried over.

Regards

---

### Post by richard.scott-ettrick on 2010-05-04
> **ibuclaw said:**
> Open home directory, show hidden files/folders (by pressing "Ctrl+H") - and look for a directory named **.mozilla**

Rename it to ie: **.mozilla-old** and try again.

NOTE: this will start you with a clean new profile. All saved passwords / browsing history won't be carried over.

Regards
Brilliant! It Works. I had the same problem with firefox after upgrade.

---

### Post by dwhite on 2010-05-04
Fix appeared to work at first but Firefox is very unstable.  

Opens initially and navigates to the ubuntu start page on google, I can navigate to another website (like yahoo.com for example) fine and then upon navigating to a new page from there Firefox quites...

on a positive note... i have downloaded Midori and it works fine but i would still like a fix to the Firefox problem if there are any suggestions...

thanks,

doug white  

> **ibuclaw said:**
> Open home directory, show hidden files/folders (by pressing "Ctrl+H") - and look for a directory named **.mozilla**

Rename it to ie: **.mozilla-old** and try again.

NOTE: this will start you with a clean new profile. All saved passwords / browsing history won't be carried over.

Regards

---

### Post by cuberts on 2010-05-04
> **dwhite said:**
> Just upgraded to 10.04 (from karma) last night, tried to start firefox, seems to begin loading then just stops.  have reinstalled with synaptic same thing happens.

any ideas?Then try to install a new web browser, and then using that web browser you could reinstall the newest version of firefox.

---

### Post by sabinedoll on 2010-05-05
Hi,
I had the same problem, it is now SOLVED. I had various error messages from no-script to segmentation fault. First Firefox did not start at all, even after uninstalling and re-installing. Then I removed the old browser files in the mozilla folder and also removed the .ini file in this folder (hidden folder in the home folder). Then firefox started and immediately crashed. I then started firefox in a Terminal (Applications/Accessories/Terminal) with the command: firefox -safe-mode         This opens a window, which gives you the opportunity to remove add-ons etc. I then had to choose: Continue in safe-mode (because my browser was STILL crashing. The terminal then gave an error, stating thet it could not retrieve 'libmoon'. I then started Synaptic (package manager) and typed libmoon in the search-box. This belonged to a program (plugin for firefox) called moonlight, which I had installed years ago. Removing these packages solved all my problems.
P.S.: There nay be other plugins or addons, which are equally noxious, so it is best to remove evrything and give it a fresh start.

Hope this helps!

---

### Post by bloom_20 on 2010-05-07
Same thing happened to me, i renamed .mozilla to .mozilla-old and that got firefox running. BUT now when i go to Edit-Preferences that makes Firefox crash again. I did open firefox in safe mode and uninstalled the libmoon package that i had installed and all other packages as well and made a complete fresh install of firefox. But it still doesnt work, any ideas what to do?

Thanks!

---

