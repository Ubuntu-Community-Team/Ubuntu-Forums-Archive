---
title: "Copying the HOME folder while working"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-03-11
Hello!

This might be a stupid question. I planned to try a new boot setup this weekend and therefore am copying my home folder to an external HD as a backup. The copy process is quite slow (I'm copying the .-folders as well, leaving out only .wine as that lead to problems in the past) and stops from time to time.

I'm wondering whether that's because I'm using the PC while copying, probably changing lots of files in my home folder (I'm only browsing, but some process are running in the back of course). What will I have copied in the end? A snapshot of each while as it looked like the moment it was copied? Maybe a corrupted file because it was changed during copying?

Should I boot from a live CD and copy the home folder from there? Or just leave out all .-configuration-files as they are not that important to me?

Thank you very much,

Blutkoete

P.S.: I thought about using a backup tool for this but in the past this simple HOME backup was very convenient for me.

P.P.S.: Extra question: I always liked the smooth light-weight LXDE variants, but the creators of such systems seem to avoid 64bit; while I know that it's meant for old systems, I still love the speed it provides on new systems and was wondering whether someone knows a full 64-bit LXDE implementation. Lubuntu states that you can install a base 64-bit Ubuntu and add LXDE, but my bandwith is limited and I'd like to download a complete image at the university.

---

### Post by vanadium on 2011-03-11
Operating systems change very six months and (some) come for free. The good ones (typically the free ones) install in less than an hours. So, there is no point in backing up a system and configuration settings.

What is unique and irreplaceable is your personal data. That is what you should backup, and very regularly so (at least once a day).

Indeed, you should not be working on your data while you are backing up.

An rsync backup of your data is most convenient. The first time, the backup takes some time, because all data are copied to the backup medium. However, subsequent runs are lightning fast: only updated files are copied over.

---

### Post by Blutkoete on 2011-03-11
Thank you, I use RSYNC quite often to sync save file from games but - shame on me - never thought of using it for backup.

One question for the experts: If I use dolphin for copying a folder, and a file in that folder changes while copying, what will happen?

---

### Post by vanadium on 2011-03-11
If the file is copied before the change is saved, then it will be the old version. If the file is copied after the change is saver, it will be the new version.

---

