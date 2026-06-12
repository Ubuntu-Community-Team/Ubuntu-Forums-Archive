---
title: "Deleted files cannot be found"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by 10.04newbie on 2010-07-29
The usual howler - Inadvertently deleted a directory of music files but when I came to look for them via the file browser/deleted files, I received the message "The folder contents could not be displayed"

Any suggestions please ?

---

### Post by nothingspecial on 2010-07-29
How did you delete them?

I am not aware of this file browser/deleted files thing

Do you mean the trash?

If you do, open the trash, right click on the directory and click restore.

---

### Post by bumanie on 2010-07-29
Use photorec which is part of the testdisk suite.> sudo apt-get install testdisk > sudo photorecRead the tutorial [here]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") - should be able to search for the music file type and retrieve them if they have not been over written. Despite the name, photorec can search 100+ file types, not just photos - I'm fairly sure it can [find mp3]("http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec").

---

### Post by 10.04newbie on 2010-07-29
I deleted the folder using the right-click 'move to deleted items folder'

The deleted items folder is the Trash folder but I am unable to access any of its contents.

---

### Post by ajgreeny on 2010-07-29
Are you sure your right click did not stray into the "delete" field if you have enabled it?  It is quite easy to do if you're in a hurry.

If that is a possibility then you may just be lucky with testdisk/photorec, but you may have to accept their loss.

Backup, backup, backup, as all should do, but too many don't.

---

### Post by 10.04newbie on 2010-07-29
> **bumanie said:**
> Use photorec which is part of the testdisk suite. Read the tutorial [here]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") - should be able to search for the music file type and retrieve them if they have not been over written. Despite the name, photorec can search 100+ file types, not just photos - I'm fairly sure it can [find mp3]("http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec").

After installing the package ok, the command sudo photorec did not work

---

### Post by 10.04newbie on 2010-07-29
> **ajgreeny said:**
> Are you sure your right click did not stray into the "delete" field if you have enabled it?  It is quite easy to do if you're in a hurry.

If that is a possibility then you may just be lucky with testdisk/photorec, but you may have to accept their loss.

Backup, backup, backup, as all should do, but too many don't.

I definitely selected 'Move to deleted items;

---

### Post by ajgreeny on 2010-07-29
Let's also double check that you were not using nautilus as root at the time, ie, having started it with ```
gksu nautilus
```or using the nautilus-gksu extension, perhaps having used a root privileges nautilus for some other purpose prior to deleting these files.

If so, your files may be in root's trash, not in your user's trash.

---

### Post by 10.04newbie on 2010-07-29
The only way I could find any reference to the deleted items folder was to use the termina lcommand gksudo nautilus. What is the actual path to the trash directory ?  I can't seem to find it.

---

### Post by mikewhatever on 2010-07-29
> **10.04newbie said:**
> The only way I could find any reference to the deleted items folder was to use the termina lcommand gksudo nautilus. What is the actual path to the trash directory ?  I can't seem to find it.

```
.local/share/Trash/files
```
Gksudo nautilus was completely unnecessary.

---

### Post by nothingspecial on 2010-07-29
Right click your panel.

Choose "add to panel" then choose "deleted items"

Click the icon, right click the directory you deleted and choose "restore"

---

### Post by 10.04newbie on 2010-07-29
> **mikewhatever said:**
> ```
.local/share/Trash/files
```Gksudo nautilus was completely unnecessary.

Consider my knuckes well and truly rapped ! Remember, I am a novice at all this and as for your code, entering that in the terminal, results in a 'No such file or directory' response.

---

### Post by 10.04newbie on 2010-07-29
> **nothingspecial said:**
> Right click your panel.

Choose "add to panel" then choose "deleted items"

Click the icon, right click the directory you deleted and choose "restore"

When I right-click the top anel, there is no such option to add

---

### Post by RiceMonster on 2010-07-29
> **10.04newbie said:**
> Consider my knuckes well and truly rapped ! Remember, I am a novice at all this and as for your code, entering that in the terminal, results in a 'No such file or directory' response.

That's where they are located under your home directory, not a terminal command. Open up your home directory, view hidden files and navigate to it.

---

### Post by 10.04newbie on 2010-07-29
Files now found and restored to the music directory  - Thanks to all who helped me. Just one other question, Other items in the trash folder are taking up a lot of space - how can these be permanently deleted ?

---

### Post by jtarin on 2010-07-29
> **10.04newbie said:**
> Files now found and restored to the music directory  - Thanks to all who helped me. Just one other question, Other items in the trash folder are taking up a lot of space - how can these be permanently deleted ?There should be a trash icon on your panel.If you left-click it opens in Nautilus and there will be a button on the right that says "Empty Trash".If you right-click on the icon it will display a menu with selections. Select "Empty Trash".

---

### Post by 10.04newbie on 2010-07-29
> **jtarin said:**
> There should be a trash icon on your panel.If you left-click it opens in Nautilus and there will be a button on the right that says "Empty Trash".If you right-click on the icon it will display a menu with selections. Select "Empty Trash".

In my version (Ubuntu 10.04 for netbook), no such icon exists. I have tried to create one, without success.

---

### Post by jtarin on 2010-07-29
Temporarily you can run these in a terminal:

```

rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null
```
This will remove trash in your home and root folder

Also, you can access the Trash typing in Nautilus:
```
trash:///
```

---

### Post by iponeverything on 2010-07-29
Do not run rm rf anything unless you know what your doing. One space where it does not belong in the command will destroy your data. 

rm -i is better in most cases as it prompts you before deleting the files, this way if you make make a typo you can catch it and it won't hose your data.

---

### Post by linux18 on 2010-07-29
> **iponeverything said:**
> Do not run rm rf anything unless you know what your doing. One space where it does not belong in the command will destroy your data. 

rm -i is better in most cases as it prompts you before deleting the files, this way if you make make a typo you can catch it and it won't hose your data.
Are you the same guy who says that in every thread I see?
sometimes rm -rf is helpful and if anyone read the code of something they would know what it means.

---

### Post by iponeverything on 2010-07-29
> **linux18 said:**
> Are you the same guy who says that in every thread I see?
sometimes rm -rf is helpful and if anyone read the code of something they would know what it means.

and are you same guy that says that in every thread I see?

Many people here seem to only have one tool in their toolbox, a sledgehammer and they break it out at every opportunity.

---

### Post by linux18 on 2010-07-30
> **iponeverything said:**
> and are you same guy that says that in every thread I see?

Many people here seem to only have one tool in their toolbox, a sledgehammer and they break it out at every opportunity.
How did you know about my love of sledgehammers? :) :) :)

---

### Post by mikewhatever on 2010-07-30
> **10.04newbie said:**
> Consider my knuckes well and truly rapped ! Remember, I am a novice at all this and as for your code, entering that in the terminal, results in a 'No such file or directory' response.

You've asked for the location and I gave it to you, no need to make a drama.:rolleyes:

---

### Post by 10.04newbie on 2010-07-31
> **ajgreeny said:**
> Let's also double check that you were not using nautilus as root at the time, ie, having started it with ```
gksu nautilus
```or using the nautilus-gksu extension, perhaps having used a root privileges nautilus for some other purpose prior to deleting these files.

If so, your files may be in root's trash, not in your user's trash.

I think you may be right. Would this account for the fact that I cannot now gain access to ' 'users and groups' ? (The error message I receive when clicking users icon is 'Could not execute 'Users and Groups'. Failed to execute child process "/root/local/share/trash". Permission denied' - and if so, what remedial action can I take ?

---

### Post by nothingspecial on 2010-07-31
Have you lost admin access to everything?

---

