---
title: "uninstalling/reinstalling Firefox"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-12
Goal: put firefox bookmarks into new user account (firefox browser)

Problem: JSON archive files not seen when trying to restore firefox database under Organize Bookmarks > import and backup > restore;
was at correct directory but system was in endless search for json type files.

Workaround attempt: moved mozilla folders [Extensions and Firefox| under >home>user>.mozilla to >home>newuser>.mozilla

Wrong!  Mozilla did not like this went starting Firefox app back up.
I downloaded newest version and ran archive manager but looking at version information on browser>HELP>About Mozilla Firefox the rev level is still 3.06 instead of 3.07; also HELP>Check for updates is at half intensity (not selectable).

I wanted to remove/reinstall Firefox application but got this:

cannot remove 'firefox 3.0 -branding'
one or more applicatons depend on firefox 3.0 -branding. To remove firefox and dependent applications use Synaptic Package Mgr.


I don't want to do this unless there is no other way to get Firefox straightened out.

---

### Post by fly-by-night on 2009-03-12
Use Foxmarks [https://addons.mozilla.org/en-US/firefox/addon/2410](https://addons.mozilla.org/en-US/firefox/addon/2410) 
or FEBE [https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

Note with FEBE you can control what is backed up and restored in FEBE Options.  During a backup Firefox will freeze until backup is completed.

Install backup again in a new profile by first installing FEBE and then use the restore option.

Also you need to configure the backup directory in Tools/FEBE/FEBE Options/Directory.  Something like home/Username/Desktop will do.

edit:  NOTE - (I don't know/remember the technical terminology) - The version of Firefox you manually choose to install runs alongside the "firefox base files". Therefore you have Firefox and Firefox 3.0.6/7 installed.  Do not try and remove the default Firefox as it's needed for your other versions.  Every new version you install refer (symbolic links or something) back to the default base installation.

---

### Post by LowSky on 2009-03-12
I use the back up (json) feature all the time between windows and Ubuntu, and it works just fine.

I did it just yesterday, on two systems, one running the Alpha of 9.04 and Ubutnu 8.10 on my netbook, and on my Windows PC at work

---

