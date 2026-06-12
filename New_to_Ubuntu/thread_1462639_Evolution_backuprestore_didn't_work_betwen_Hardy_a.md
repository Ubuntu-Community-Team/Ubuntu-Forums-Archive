---
title: "Evolution backup/restore didn't work betwen Hardy and Karmic. WHY?"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-04-25
Hi Community:

I needed to upgrade from Hardy Herron (HH) LTS to Karmic Koala (KK) to take advantage of one softare package that works much better on KK.

So, I backed everthing up in preparation to migrate from HH to KK. This included backing up data used/created by the mail reader Evolution. And here is where my problem started...

With all the right pluggins installed (edit > plugins > backup and restore plugin), the Evolution Help pages (Help > Evolution FAQ) answers the question, "How can I completely backup evolution?"

The answer on that page is: "If you are using evolution > 2.22 then, Ensure you have "Backup and Restore" plugin enabled in Edit -> Plugins -> Backup and Restore. Then use File->Backup Settings and File->Restore Settings ."

Backing things up w/ File > backup settings produces the file "evolution-backup.tar.gz" Really nice. 

Then (as noted above), the FAQ says, "Then use File->Backup Settings and File->Restore Settings " to restore your data, presumably.

So I did the backup, installed KK, and then tried to restore my data using the recommended sequence described above.

Guess what? It did not work! :confused:

The restore sequence in KK wanted a FILE. not a tar.gz thing...

Well... to make a long story short... KK just did not work out for me for that and other reasons... so I reinstalled HH... and used the recommended sequence, "File->Restore Settings" to restore my data. 

Guess what? It worked in HH! :confused:

This really worried me: I plan to migrate to the new LTS from the old LTS within the next few months.... and I've got information here that suggests that the restore might not work when I do the migration...

Would anyone venture a guess why Evolution did not work when I tried to restore using Evolution in KK? 

Would anyone venture a guess whether Evolution can be restored between HH LTS and the new forthcoming LTS??

I feel that this may be important to many people in our Community who will upgrade between LTS versions soon.

Thanks!
Phil Smith
Duluth, GA

---

### Post by cariboo on 2010-04-26
Just a question, if you untarred the .gz file, could you restore then?

As regards to upgrading to Lucid, if you have a separate home directory, just backup the files as a precaution, but you shouldn't have to do anything else.

---

### Post by Old Jimma on 2010-04-26
Nope. Evolution in Karmic Koala wanted one file.

---

### Post by pme 72 on 2010-04-29
I struggled getting my 9.04 back up of Evolution to be recognized in a fresh install of 9.10. An Internet search turned up others with similar issues and several fixes. My notes for the event read "Got Evolution to recognize my backup file-changed the extracted file name to .evolution". I probably spent an hour extracting the file multiple times and renaming it before stumbling on a combination that worked. I sympathize with your frustration.

---

### Post by Old Jimma on 2010-05-01
Thanks, PME:

I hope others see your response when they look for info on restoring Evolution!

All the best,
Phil Smith
Duluth, GA

---

