---
title: "How To Gain Access To Locked Files &amp; Folders?"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by rez182 on 2011-04-24
i recently used an app called photorec to recover files from a deleted partitioned pen drive. the files were restored randomly (couldent get what i wanted, back :'( ) and now i cant delete those files from the home folder. a lock icon appears over the folder icon. btw i am able to read the files but not write it...

how can i gain access to these files?

---

### Post by ~Plue on 2011-04-24
run the following to change the ownership of the files to your user
```
sudo chown -R $USER: /path/to/folder/
```and change the read only permissions to read+write;
```
chmod -R u+wr  /path/to/folder/
```
**edit: **do not run it directly on your home folder (which seem to be the recovery directory here!), as it may cause some problems as described in the next post.

---

### Post by yetiman64 on 2011-04-24
> **rez182 said:**
> i recently used an app called photorec to recover files from a deleted partitioned pen drive. the files were restored randomly (couldent get what i wanted, back :'( ) and now i cant delete those files from the home folder. a lock icon appears over the folder icon. btw i am able to read the files but not write it...

how can i gain access to these files?

The command photorec needs sudo before it if I recall correctly and though the files are saved to your home folder they will be owned by root. I would normally suggest a root browser but the files will remain in root's trash taking up disk space. So I will suggest a terminal method instead.

Firstly open a terminal, and type in "sudo rm" (without the quotes) and press the spacebar ONCE.

Now in your home folder highlight all the files you need to remove (hold down the CTRL key while clicking the files to make a multiple selection). When you have selected all you need, drag the multiple selection into the terminal. Then hit enter. You will have to enter your user password but note it won't show as you do so (a security feature of Ubuntu). Press enter again.

All the root owned files should then dissapear (deleted).

**Edit**: I should note the "sudo rm" command can be danderous if you select and delete the wrong file/s, TAKE CARE WITH IT. You don't get second chances to recover a file if you make a mistake. It is permanent. 

If you don't feel comfortable with using it, use ~Plue's method to change ownership of the files to yourself, then delete them as usual.

@ Plue, your second command may change the permissions on the file .ICEauthority from 600 to 644 if that command is run directly on the home folder which may not be a good thing, Please check again as hidden files and folders are in the home folder and may be affected adversly.

---

### Post by rez182 on 2011-04-24
@yetiman64, thanks for making it so easy, but it didnt work, it says:
> rm: cannot remove `/home/rez/recup_dir.1': Is a directory
rm: cannot remove `/home/rez/recup_dir.2': Is a directory
rm: cannot remove `/home/rez/recup_dir.3': Is a directory
rm: cannot remove `/home/rez/recup_dir.4': Is a directory
rm: cannot remove `/home/rez/recup_dir.5': Is a directory
@~Plue, can i use the click and drag for your solution?
EDIT: Drag n' Drop**

---

### Post by yetiman64 on 2011-04-24
> **rez182 said:**
> @yetiman64, thanks for making it so easy, but it didnt work, it says:
@~Plue, can i use the click and drag for your solution?
EDIT: Drag n' Drop**

Change the command to "sudo rm -r " and highlight and drag the folders in to the terminal. I assumed you were deleting files from your first post not directories. Use the same method though and be very careful.

---

### Post by ~Plue on 2011-04-24
> **rez182 said:**
> 
@~Plue, can i use the click and drag for your solution?
EDIT: Drag n' Drop**
 you could, but its not a good idea to use the second one it as i didn't take into account that the home folder could be the recovery directory. some files there need to retain their permissions. and since you've already deleted the files, it would be a lot simpler to use yetiman's method instead

---

### Post by dcsoldschool53 on 2011-04-24
[B]If you have the files in Trash already, try this command to empty the trash bin.
```
sudo rm -rf /home/yourusername/.local/share/Trash/*
```If you have them some where else, try.```
gksu nautilus /path/to/directory
```Put in your password, and nautilus will open, so that you can delete those files in the directory that you specified. Then close nautilus. WARNING! Be care of what you delete as the administrator in nautilus[/B]

---

### Post by rez182 on 2011-04-24
@~Plue, im sorry im a little confused now, i still didnt delete anything, so should i be worried using drag and drop method, even if i do it carefully making sure i dont delete anything else but those folders?

EDIT: what method should i use to permanently delete those folders from my home folder? (so many options)

---

### Post by yetiman64 on 2011-04-24
> **dcsoldschool53 said:**
> [B]If you have the files in Trash already, try this command to empty the trash bin.
```
sudo rm -rf &#8216;/home/username/.local/share/Trash
```If you have them some where else, try.```
gksu nautilus /path/to/directory
```delete those files in the directory that you specified. Then close nautilus. WARNING! Be care of what you delete as the administrator in nautilus[/B]


@ dcsoldschool53, **your first command will remove the trash directory itself not just the contents** and you don't need sudo to delete files or folders in a users home directory plus the  -f or force switch is totally unnecessary. Please reconsider it.

OP if you follow my first post but change the command to "sudo rm -r" (recursive switch for directories) those folders and their contents will be removed.

---

### Post by rez182 on 2011-04-24
thanks alot yetiman and plue, it worked :)

---

### Post by ~Plue on 2011-04-24
> **rez182 said:**
> @~Plue, im sorry im a little confused now, i still didnt delete anything, so should i be worried using drag and drop method, even if i do it  carefully making sure i dont delete anything else but those folders?

again, its a wrong assumption on my part. if you follow yetimans advice, everything should be fine.

---

### Post by yetiman64 on 2011-04-24
> **rez182 said:**
> thanks alot yetiman and plue, it worked :)

You're welcome,
Cheers from yetiman64. :)

---

### Post by dcsoldschool53 on 2011-04-24
> **yetiman64 said:**
> @ dcsoldschool53, **your first command will remove the trash directory itself not just the contents** and you don't need sudo to delete files or folders in a users home directory plus the  -f or force switch is totally unnecessary. Please reconsider it.

OP if you follow my first post but change the command to "sudo rm -r" (recursive switch for directories) those folders and their contents will be removed.

You are right, because the command is actually```
sudo rm -rf  ~/.local/share/Trash/*
```This will work.  I forgot to add the * after Trash/. SORRY this will not delete the trash folder but it will delete everything in it.

---

### Post by yetiman64 on 2011-04-24
> **dcsoldschool53 said:**
> You are right, because the command is actually```
sudo rm -rf  ~/.local/share/Trash/*
```This will work.  I forgot to add the * after Trash/. SORRY this will not delete the trash folder but it will delete everything in it.

You are removing files/folders in the users home directory so sudo is not needed also the force switch is unnecessary so  the command in this case should be,

```
rm -r ~/.local/share/Trash/*
```You only need to invoke sudo if the files/folders are owned by root.

Just tested this here and it works .

---

### Post by susanabra on 2012-10-06
@ yetiman 64, Worked for me with some folders (directories) that were beginning to drive me completely mad! Thank you. :-)

---

### Post by wildmanne39 on 2012-10-06
Thanks for sharing. Thread Closed.

---

