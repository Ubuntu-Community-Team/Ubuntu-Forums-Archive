---
title: "cant read/edit admin files/folders off external hd"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by milk11 on 2010-04-02
Im new to Ubuntu and Linux after my laptop running windows xp suffered a short (my hd was not damaged). 

My current machine has two internal hd's; one with windows xp and the other with ubuntu 9.10. 

When I plug my old laptop hd in as an external under windows, it will get recognized, but immediately freezes and gives me the error: cyclic redundancy check. 

I decided to give linux a whirl and low and behold, it reads the drive and even lets me view documents on old usernames, but not the admins. 

How can I view the admin files and pull my documents/pictures/music off of the drive? I am assuming that I don't have permission to view them because I required a username/pw to login to the account.

Thank you in advance.

---

### Post by mikewhatever on 2010-04-06
Not quite sure what you mean by the '*admins*'. Is that what you call documents pictures and music? Why not just copy your files to the Windows partition?

---

### Post by -humanaut- on 2010-04-06
hmm... Trying this hit "alt-f2" gksu nautilus then try and copy the files that way. I don't think you have root permissions on the mounted drive that should fix it if thats the problem oh yeah and right click on the files after copying them to your linux partition and make sure you give yourself permission to read & write.

---

### Post by milk11 on 2010-04-06
Hi Mikewhatever, there are different user names on the drive. one being administrator which was the only password protected user name. It is under the administrator login that all of my files are now unaccessible/hidden.

Thank you.

---

### Post by milk11 on 2010-04-06
Humanaut, I tried the root files, but unfortunately when I try to copy the admin folder to my desk top I receive the following error: Error stating file '/media/5C88A76F88A745FC/Documents and Settings/Administrator/.gimp-2.6': Input/output error.

When I try and change the permissions under right click, properties they changes will not save and revert back to the create and delete folders permission.

Thank you for your help.

---

### Post by audiomick on 2010-04-06
Hi.
I think that "gksu nautilus" is the right way to go.

One of the files that is causing your error
```
Settings/Administrator/.gimp-2.6
```
looks like a Gimp setup file. Whilst it might be nice to recover that, it is not absolutely neccessary. Try copying the files one at a time instead of the whole folder. If there is one thing in the folder that it doesn't like, in my experience, it will complain about the whole folder.

As far as the permission change goes, you also need to do that in the "root" instance of nautilus. In the "normal" file manager it will not be possible if the files do not belong to the user who is attempting the change. Is this how you are trying to do it?

---

### Post by milk11 on 2010-04-06
audiomick,
i attempted to go in through the root files but when i click on the administrator folder, there are no sub folders.

for permission change, under root it wont allow me to right click, properties into the permissions. is there another way to do this?

Thank you.

---

### Post by Calash on 2010-04-06
A cyclic redundancy check error in Windows is a sign of a failing drive, or possible some very corrupted sectors.

I am not sure if Ubuntu has the tools to check a NTFS drive, I do know it can do FAT and FAT32.

Honestly I would boot back into windows and run a chkdsk /f on the external drive and see if that can do anything to clear up the problems.  However if it is immediately freezing that may be a problem.  You can try holding the right shift key when you plug the drive in.  I believe that should bypass any autorun it tries to do and just mount the drive.

---

### Post by -humanaut- on 2010-04-06
"gksu" would be the easiest but there's other ways around it if your drives not dead. This is kind of a long shot but 'gksu nautilus' make your way to the files in question and see if you can literally just right-click copy then paste in a current working directory. First though make sure you're drive is usable and if this doesn't work there's always the terminal we can try.

---

### Post by J V on 2010-04-06
so far 4 people havn't read the thread and posted the same gksudo nautilus advice...

Sounds like your HD is damaged, download testdisk and see if you can salvage some files like that, otherwise it looks like the data is permanently gone.

---

### Post by -humanaut- on 2010-04-06
Did you figure out if that Harddrive was working?

---

### Post by milk11 on 2010-04-06
Thank you JV. I ran testdisk and it said the hd was ok. so i am using photorec to restore the files. I will let you know when it finished how it worked out.

thanks again

---

