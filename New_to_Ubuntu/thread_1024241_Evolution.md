---
title: "Evolution"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Gingerman on 2008-12-28
For some reason, Evolution keeps messing up.  I'm running Hardy Heron.

I have had to reinstall Evolution three times in the last month.

Someone sent me an email explaining the hidden file that the backup contacts and such are stored in, but all my emails went away when I had to reinstall Evolution.

I don't know diddly about the terminal.

But, can anyone tell me what to do in terminal, in words of one syllable, which can be entered by someone wearing boxing gloves, what I should do to retrieve my contacts?

---

### Post by howefield on 2008-12-28
Evolution has a backup facility which will create a file containing your settings, calendar, emails ect ect.

From the Evolution File menu select Backup Settings and follow the prompts. Just as easy to restore by selecting Restore Settings and point it to your saved file.

Does this help or have I missed your point ?

Also on a side note, might be worth considering creating a gmail account and pulling your current email account through that into Evolution via imap. This has the benefit of archiving your mail so you need never lose another.

---

### Post by 73ckn797 on 2008-12-28
> **Gingerman said:**
> For some reason, Evolution keeps messing up.  I'm running Hardy Heron.

I have had to reinstall Evolution three times in the last month.

Someone sent me an email explaining the hidden file that the backup contacts and such are stored in, but all my emails went away when I had to reinstall Evolution.

I don't know diddly about the terminal.

But, can anyone tell me what to do in terminal, in words of one syllable, which can be entered by someone wearing boxing gloves, what I should do to retrieve my contacts?

Look under /home/_*yourname*_/.evolution via Places/Computer/Home. You will have to first enable viewing hidden files under Places/Computer then Edit/Preferences/View. All info files will be there. "Yourname" is, well, your name, the name of your directory created when you installed Ubuntu. This is all dependent upon whether that directory still exists in the manner in which it was initially created and whether it still has the info you seem to have lost.

From that point follow the previous directions on backing up the info within Evolution.
> **howefield said:**
> Evolution has a backup facility which will create a file containing your settings, calendar, emails ect ect.

From the Evolution File menu select Backup Settings and follow the prompts. Just as easy to restore by selecting Restore Settings and point it to your saved file.

Does this help or have I missed your point ?

Also on a side note, might be worth considering creating a gmail account and pulling your current email account through that into Evolution via imap. This has the benefit of archiving your mail so you need never lose another.


Hope this helps. It does not require any terminal input.

---

### Post by elitenoobboy on 2009-01-08
I didn't backup using the evolution backup thing, but I do have the original .evolution folder that has all of my settings. Simply copying the .evolution folder into my home directory never works. Most of my email accounts are imap, but restoring the .evolution file never restores any of those accounts. How do I fix this?

---

