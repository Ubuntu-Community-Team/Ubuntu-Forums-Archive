---
title: "permissions noob questions"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by dimitriv on 2009-06-20
hi

i have a volume called /media/communal/ which contains multiple folders with subfolders. i am listed as Owner for the files and folders any my access to these folders/files is fine.

I want other local accounts to access some of these folders/files but only to have read access (not edit/move or delete etc.). 

1) What's the best way to reset all permissions for all folders/files so that I'm the owner and nobody has any access (i've been trying a whole bunch of different settings without success so it would be good to reset and have a known base point)

2) I've created 'groupa' and made the accounts as members of 'groupa'. How should I assign permissions so that groupa have access to use all files and subfolders as below:

folder_a/              (don't want access)
folder_a/folder_a_1/   (don't want access)
folder_a/folder_a_2/   (want access and all sub folders)
folder_b/              (want access and all sub folders)
folder_c/              (don't want access)


Under Windows NTFS I know how I'd configure this and am probably expecting it to work in a similar way. 

Logged in as myself or running gksudo nautilus i've then modified individual folder permissions so that 'groupa' have 'access files'. I also tried seting File Access to Read Only, but moments after setting it changes back to '---', i also clicked 'Apply Permissions to Enclosed Files'. but accounts in groupa still don't have access

please advise

thanks

---

### Post by scrooge_74 on 2009-06-21
You only need to change the permissions for the other users to be read only.

---

