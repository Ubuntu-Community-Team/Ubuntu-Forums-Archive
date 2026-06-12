---
title: "[SOLVED] Download problems"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by DucksAndDolphins on 2008-12-27
So I got myself an external hard drive because I no longer have space on my Ubuntu partition. This problem has been solved by the external, for the most part. However, when I attempt to download pretty much anything, I receive an error message saying that I do not have any more space on the drive and that I should try saving in a different location (i.e. my external). The problem with this is that I cannot choose where to save the download before it closes.

Is there any way I can make the external the main place for saving downloads?

---

### Post by jamesrfla on 2008-12-27
Go to Edit>Preferences in Firefox. Then on the main tab chose where to save the downloads.

---

### Post by taurus on 2008-12-27
Do you have a write permission to that external harddrive?  Are you using firefox to download stuff?  Change the Sa_v_e files to in firefox -> Edit -> Preferences to your external harddrive then.

---

### Post by hailukah on 2008-12-27
Also, if your root partition is full you may begin to experience problems when programs have to write data to the /tmp folder.  It would probably be a good idea to open a terminal and type

sudo apt-get clean

This will free up some space (possibly a lot) by removing the compressed package downloads that apt-get, synaptic, etc. use when installing and updating programs.  Don't worry, it won't uninstall anything.

---

### Post by eagle416 on 2008-12-27
are you in firefox? Go to preferences (I think that's under EDIT), under Main, look for where it says "Save downloads To"

---

### Post by DucksAndDolphins on 2008-12-27
Kay so I did a clean on it, and that seems to have worked nicely; when I go to Preferences in Firefox, I changed it so that it saves to the external, but it still says that it will save to the desktop?

---

