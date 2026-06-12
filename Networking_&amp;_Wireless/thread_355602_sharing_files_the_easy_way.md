---
title: "sharing files the easy way"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by darrengoddard on 2007-02-07
hi everyone - please forgive the stupidity of my question - blame it on the noobness

i have desktop pc and a laptop both running ubuntu 6.10.  all i want to do is listen to the music and look at the photos and alter the documents stored on my desktop machine from my laptop using my wireless router.  i have set up samba and marked the files on both machines that i want to share but i cannot see them anywhere.  (btw places->network servers->windows network->mshome->desktop brings up a message "sorry couldn't display contents of windows network: desktop)

i have checked the lists and the forums and most of the discussion seems to be about wanting to see windows drives which (thank god) i don't want/need to do.

so before i get into some heavy duty samba-ing about, can someone tell me if there is a simple way to allow me to access the folders.

smiling (sheepishly)

darren

---

### Post by kvonb on 2007-02-07
If you don't want Windows access to your files, I would suggest using native NFS.

When you right click on the folder you want to share, from the drop down box select NFS instead of samba, that should do the trick :).

---

### Post by darrengoddard on 2007-02-07
well i appreciate your help.  have tried this but without success ... yet.

when i changed the setting to NFS i noticed boxes to be filled in about adding allowed hosts.  sorry to be really dense but assuming that i do have to add a host can you tell me where to look and what to put.

many thanks in advance

i never thought monkeying about with my computer - relatively solitary hobby - would lead me into such a warm and welcoming community.

darren :)

---

### Post by dmizer on 2007-02-07
the gui interface doesn't work well for nfs.

fortunately, the cli method is VERY simple.  follow the fourth link in my sig to get nfs to work.

---

