---
title: "Firefox being weird"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by luvinit on 2009-05-17
Hi, as of this morning Firefox 3 is being strange. All bookmarks have disappeared and backups cannot be restored. RSS feed toolbar is gone and back and forward arrows, reload and stop buttons are greyed out. I have tried reinstalling and deleting localstore.rdf files. I am using Hardy Heron. Help appreciated.

---

### Post by Ben Crisford on 2009-05-17
> **luvinit said:**
> Hi, as of this morning Firefox 3 is being strange. All bookmarks have disappeared and backups cannot be restored. RSS feed toolbar is gone and back and forward arrows, reload and stop buttons are greyed out. I have tried reinstalling and deleting localstore.rdf files. I am using Hardy Heron. Help appreciated.

Have you changed anything in your system recently?

If not you might want to report this as a bug :).

---

### Post by luvinit on 2009-05-17
No nothing other than returning to Hardy after Jaunty not working properly, but that was two weeks ago. I also shut down firefox seemingly correctly last time I used it. Maybe there was an update to firefox recently, I can't remember. Another thing to add is that you cannot use the key command of a greyed out icon e.g. F5 to refresh the page.

---

### Post by fly-by-night on 2009-05-17
It might be either a broken link to your profile or a broken profile.

Try starting Firefox with: firefox -profilemanager.  If you get that far create a new profile.  Test it to see if it work.  Close FF then copy and paste your old profile into the new one.  Profile is in home folder under ".mozilla".

Run nautilus as root (I think you need to) then do the copy and paste above.

If you need more detailed help I'll be happy to assist (if that's the problem).

---

### Post by kerry_s on 2009-05-17
> **fly-by-night said:**
> It might be either a broken link to your profile or a broken profile.

Try starting Firefox with: firefox -profilemanager.  If you get that far create a new profile.  Test it to see if it work.  Close FF then copy and paste your old profile into the new one.  Profile is in home folder under ".mozilla".

Run nautilus as root (I think you need to) then do the copy and paste above.

If you need more detailed help I'll be happy to assist (if that's the problem).

no, you never need to run **root** anything in your home folder, thats how things get screwed up.

---

### Post by lovinglinux on 2009-05-17
Backup your profile just in case. Then delete the file *places.sqlite* from the profile folder. Start Firefox and try to import a bookmark backup. If it doesn't work, then try deleting your entire profile.

---

### Post by luvinit on 2009-05-17
OK that worked, I was able to import my bookmark backups and some of my add on settings, but copying everything from the old profile causes the same problem. The main thing is that I could preserve many years worth of bookmarks.Thank you all.

---

### Post by lovinglinux on 2009-05-17
> **luvinit said:**
> OK that worked, I was able to import my bookmark backups and some of my add on settings, but copying everything from the old profile causes the same problem. The main thing is that I could preserve many years worth of bookmarks.Thank you all.

Now that it is working, make sure you make backups of your entire profile with [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109). It allows you to schedule backups and keep any number of copies of it. If you encounter a problem like this again, just restore the latest FEBE backup and you will have all your stuff back (bookmarks, extensions, setting, cookies, passwords...).

---

