---
title: "Unable to move firefox profile into encrypted private directory"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by KIAaze on 2010-08-30
Hi,

I started using the encrypted ~/Private directory made with "ecryptfs-setup-private".

However, I can't figure out how to move my firefox profile in there so that firefox keeps on working.

Every time, I get an error message like this:
```
Firefox cannot use the profile because it is in use.

To continue, close the running instance of Firefox or choose a different profile.
```
(while no firefox process is running and no .parentlock file exists)

I first tried simply creating a symlink from ~/.mozilla to ~/Private/.mozilla (after copying the .mozilla directory there first of course) -> failed
Then I tried creating a symlink from ~/.mozilla to ~/.mozilla_old -> failed again

Now I tried creating a new profile through the firefox profile manager and chose ~/Private/.mozilla/firefox as profile directory. -> same error message when starting the new profile again.
(while old profiles in ~/.mozilla still work)

However, when I create a new profile with /tmp/fofofo/ as profile directory, it works.

How can I put my firefox profile (the whole .mozilla dir would be even nicer) into ~/Private?

---

### Post by KIAaze on 2010-09-09
Problem solved.
Solution:
0)Backup firefox profile
1)Remove any ~/.mozilla and ~/Private/.mozilla symlinks or directories
2)Run ```
firefox -P
```
3)Create a new profile and create+choose a directory of the form ~/Private/.mozilla/firefox/$USER
4)Close firefox
5)Remove contents of newly created profile
6)Move contents of backed up profile into new profile directory
7)Start firefox. Add-ons should be enabled, but not working.
8)Disable any add-on, restart firefox, re-enable the add-on and restart firefox again. Everything should work now.

I found a bug with some extensions when symlinking the .mozilla dir to somewhere else. Will post more details later. Basically, firefox crashes after the second time after extensions like sync, stylish, greasemonkey or downloadhelper have been installed.

---

