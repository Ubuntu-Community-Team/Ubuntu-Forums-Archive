---
title: "Replacement for OneNote ?"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by immoweichert on 2010-04-12
I've looked at a few of the old threads in the forum, but none really have been able to give me a satisfactory answer. Is there a true replacement of OneNote available to run in Linux/Ubuntu ? One that allows you to import your OneNote files as well (similar to how OpenOffice allows you to use your Windows Office files) ? Alternatively does OneNote run without any problems in WINE ? I personally do not use OneNote, but SWMBO is comletely hooked (and has her life completely organized with it).  She wants to have Ubuntu (like the rest of the household) but she does not want to give up her beloved OneNote.  :confused:

---

### Post by ajgreeny on 2010-04-12
have a look at basket, a kde application that seems to allow the same uses.

I had never heard of OneNote and don't run windows so don't really know how similar it is, but it's worth a look.

---

### Post by Odd-rationale on 2010-04-12
If you are looking for a replacement that has similar features and will open OneNote files, then the answer would have to be no.

OneNote reportedly works OK in Wine. You can check the WineHQ AppDB here:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2911](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2911)

For programs that have similar functionality to OneNote, try BasKet or Tomboy.

You might also want see if Evernote (not opensource) will suit you needs: [http://www.evernote.com/](http://www.evernote.com/)

Although there is no Linux client, the web interface and web clipper bookmarklet may be sufficient.

Although, it seems like she already has everything setup in OneNote, so she may not want to do everything over again. The problems of using a locked-down proprietary program... :?

---

### Post by Murrquan on 2010-04-12
If she's using OneNote 2007, she can export all her notes as PDF files. That way she can read them in Linux.

Obviously, her mileage may vary, but I *personally* find Tomboy about a million times more suited to my needs than OneNote. Find out what she's doing with it; is she just taking text notes or is she using all of its features? If the latter, then BasKet might work better for her, but then again it might not.

You could try positioning these apps not as replacements but as neat things she could use for note-taking while she's in Linux (you have dual-boot set up, right?). Tomboy in particular has a Windows client, so if it makes her feel better you could try syncing your notes between the two partitions, like by using a USB flash drive. Then she could just copy-and-paste from Tomboy into OneNote when she's in Windows, assuming you can't get it  to run well enough in Wine.

---

### Post by Mark Phelps on 2010-04-12
I'm a long term user of OneNote, and when I switched over to using Ubuntu daily, I went on the same search.

I found that BasKet provided a lot of the note-taking features of OneNote, but it was limited pretty much to that.

It's been a couple of years since I used BasKet, and at the time, there were no current .debs, so I had to download the source and build the executable -- a LOT more work than I had anticipated.

---

### Post by immoweichert on 2010-04-13
Thanks for all your replies. I've installed Karmic on her system now (but kept XP for the moment), so she'll be able to try out all your suggestions. She does make full use of OneNote incl. the tabs, tables, pictures , so she might just end up using OneNote in WINE.

---

### Post by Mark Phelps on 2010-04-13
While Wine certainly does some things well, results vary enormously with specific MS Office products and versions.

The page below is from the WineHQ site for OneNote:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2911]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2911")

The silver rating is a warning to not expect much to work. If you click on the test results on the right side, you will see more details about what works and what doesn't.

---

