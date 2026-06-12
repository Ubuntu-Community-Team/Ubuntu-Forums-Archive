---
title: "daily server backup solution"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by dumbalien on 2009-03-19
Hi,

Is there an easier way of backing up files from a file server than copying them to a USB hardrive everyday. We are using XP on the main computer with 5 computers networked to this one.

what would the benefits of moving over to Ubuntu server?

thanks.

---

### Post by sahabcse on 2009-03-19
Hi 

Try "sbackup"

---

### Post by OffAxis on 2009-03-19
On windows the easiest way would be to set up a Backup schedule. It's under Start-->All Programs-->Accessories-->System Tools-->Backup

> what would the benefits of moving over to Ubuntu server?

Better stability, for one. It really depends on what you want to do.

---

### Post by dumbalien on 2009-03-19
it will mainly be a straight forward file server storing spreadsheets and autocad drawings.

it will store all the files and requires backing up each day!

---

### Post by gn2 on 2009-03-19
To backup a Windows PC a good tool is [SyncToy]("http://www.microsoft.com/Downloads/details.aspx?familyid=C26EFA36-98E0-4EE9-A7C5-98D0592D8C52&displaylang=en"), I use it to back up my wife's business PC to a NAS and a USB drive.
You can never have too much backup......

---

### Post by Kellemora on 2009-03-19
Hi DA

Instead of using Backups, Mirror your drives instead!
That way only CHANGED files are recopied, not all the files.

In our case, a backup takes about 6 hours, a mirror takes about 2 to 5 minutes, depending on how much had changed.  If we pick up a new client and all their associated files, it could take 10 minutes one time is all.

Our Data Server is not really a server at all, it's a spare computer with 2 hard drives, one in EXT3 format and the other in NTFS format, plus we have an off-site hard drive that is NTFS also.

Using RSync, any files stored on the EXT3 HD are synced to the NTFS hard drive, 5 times a day.  10AM, Noon, 3PM, 5PM and finally at 7PM.  At 9PM the NTFS is mirrored (with the delete option turned off) to the off-site NTFS drive.  I think the reason for having delete turned off is obvious since many employees have access to the files.  You don't want a deleted file server to automatically delete your primary mirror too.

I do have a couple of little side jobs running via RSync also, that copies a folder in Wine on one computer to the desktop, then copies it to the file server.  I can't seem to get the folder to go from Wine on one computer directly to the File Server without errors.  But by copying it to the desktop first, no errors, then from the Desktop to the File Server, no errors.  It's been looked into many times, no permission problems exist that could be found.  Just an inability to create new files on the File Server from Wine I suppose.  But doing the double jump is no problem and can actually be beneficial, for me anyhow, as I can check things real quick without having to open the program itself.

Good Luck

TTUL
Gary

---

### Post by OffAxis on 2009-03-19
that rsync comment is a bit confusing...

There's different backup types;
[LIST]
[*]Full - Everything gets copied over and backed-up (takes the longest)
[*]Incremental - only files that are different than those in the destination location are copied over (and the archive bit on these files gets flipped)
[*]Differential - like incremental, but the archive bit on the file doesn't get flipped (so it would still be read as 'needs to be backed up')
[/LIST]

rsync is a file copying tool. It has dozens of options, and can be used for backups, but it still performs one of the fundamental backup types.

Any backup program worth it's salt will let you specify what backup type you want to perform.

If you're on a peer-to-peer network and there's no need to run server functions (like a DNS or web server) than there's nothing wrong with using the XP machine or one of the other workstations to perform the backup; a server isn't going to bring anything new to your setup.

---

