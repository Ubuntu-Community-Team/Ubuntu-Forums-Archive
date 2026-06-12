---
title: "How to recover an overwritten file?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by pyster on 2010-01-04
I have accidently overwritten a .doc file, is there any easy way to quickly restore this file? I have looked around but found no suitable resolution, I only wish to restore the file nothing else. I dont have internet on that computer where the file was saved, but on another one with Windows. Answers for dummies, please!! =)

---

### Post by ajgreeny on 2010-01-04
If you did the overwriting in OOo, your best hope is that you have a backup copy saved.  By default, the option for this is not enabled in OOo Tools->Options->Load/Save->General, unfortunately, but you may have done so and will be able to find the backup in ~/.openoffice.org/3/user/backup.

Perhaps it's worth enabling that now just in case, for future similar situations.

---

### Post by Hospadar on 2010-01-04
If no backup file was saved by the application, there's pretty much no way to recover such a file short of electron microscopy.

In certain rare situations deleted files may be recovered since their data remains on the disk, but are not longer referenced by the disks file table.  In the case of overwritten files however, the data for the new file is often written in the same place as the old file, making it extremely difficult to recover the data.

---

### Post by pyster on 2010-01-04
thanks for your help, that option was not enabled but it is now in case of future misfortunes...

---

### Post by StefM5 on 2011-04-22
@ajgreeny,

Hello, I've made the above mentioned mistake. I've checked and see that my 'Always create backup copy' box in Tools>options> etc. is checked. However, I don;t understand where I can find the original of the overwritten OO-document.

Who can shed some light in my dark Linux world?

Thanx,
Stef

---

### Post by alphacrucis2 on 2011-04-22
> **StefM5 said:**
> @ajgreeny,

Hello, I've made the above mentioned mistake. I've checked and see that my 'Always create backup copy' box in Tools>options> etc. is checked. However, I don;t understand where I can find the original of the overwritten OO-document.

Who can shed some light in my dark Linux world?

Thanx,
Stef

Under Libre Office which is an OO Fork, the backups are kept under

.libreoffice/3/user/backup

In openoffice v3 I would imagine the folder is:

.openoffice/3/user/backup

Files and folders that start with a '.' are hidden by default. If you open up Places -Home Folder and then select View - Show Hidden Files you will see them.

---

### Post by p_a_c on 2012-09-27
@ajgreeny, @alphacrucis2, thanks!

I had a similar situation where OpenOffice's automatic document recovery overwrote a document with an older version. It turned out that OpenOffice did save a backup (of the document it overwrote) in .openoffice/3/user/backup, even though the 'Always create backup copy' box wasn't checked.

Anyway, posted this in case it's useful to someone else later.

Thanks again!

---

