---
title: "making 1 hr videos  into 10 min clips"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by bilgrami on 2010-11-03
hi i am relatively new to ubuntu and would like  to make a i hr video  into 10 min clips could you tell me how it is done

---

### Post by migs73 on 2010-11-03
There is a application called PiTiVi installed as default in 10.04 and 10.10. this will be able to do it.

Applications  > Sound & Video > PiTiVi Video Editor

Welcome:)

---

### Post by bilgrami on 2010-11-03
thanks i have split it into parts but cannot understand how to save each part as a different file

---

### Post by migs73 on 2010-11-03
Sorry, I can't help you just now I am on my work XP machine. Have a google to see of there are any how to's for PiTiVi. I fyou find anything interesting, post the link back here, as I would like to see that myself. Ihave only stitched stuff together on it so far.
Maybe you need to crop out the 50 mins you don't want then save, then do the same, for the next 10min clip?

---

### Post by P4man on 2010-11-03
I dont think there is an easy way with pitivi. You;d have to split it one by one and save/export one by one. Thats tedious. Especially if this is a recurring job, its probably  easier to use this:
[http://manpages.ubuntu.com/manpages/hardy/man1/avisplit.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/avisplit.1.html)

You can install avisplit through the software center (search for "transcode utility programs").

There might a be graphical alternative or a gui for it, but should be pretty straightforward from a command line.

---

### Post by allfoxwy on 2010-11-03
I think you may try this package: "mkvtoolnix-gui", it`s a GUI for mkvmerge which is a tool to generate MKV files. 

I`m using a localized Ubuntu, so the following step`s English name is just my guess, excuse me.

1. Open a terminal, install mkvtoolnix-gui with the command: sudo aptitude install mkvtoolnix-gui.

2. Then in Application menu --> Sound & Video --> mkvmerge GUI.

3. Add your input file with that obvious Add button at the top of the UI.

4. Switch to [COLOR=#000000]Global tab.

5. Check "Enable split".

6. Choose "By timing".

7. Input the time length, "00:10:00" stands for 10 min.

8. Click Start button at the bottom of the UI.

9. Wait until it is finished.

10. End of the job.
[/COLOR]

---

### Post by khelben1979 on 2010-11-03
Check [this thread]("http://ubuntuforums.org/showpost.php?p=4236863&postcount=4").

---

