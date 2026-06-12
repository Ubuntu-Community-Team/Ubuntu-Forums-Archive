---
title: "undo a delete?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by sceeeggg on 2011-04-05
I am new to ubuntu, I am new to these forums. I deleted a folder this morning that I did not intend to delete.
I would like to recover it. I right clicked the folder and clicked delete from the menu. It did not go the trash folder that is on the lower right hand corner of the desk top. I am hoping that there is a way to find it elsewhere on the computer.

---

### Post by r-senior on 2011-04-05
It won't be anywhere else, that delete option really does delete it. It is possible to get it back but results are not guaranteed:

[http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)

To be fair, Nautilus does make itself clear (see attached).

If you want to avoid the mistake again. In Nautilus (file manager), go to Edit->Preferences, then the Behaviour tab. There's an option at the bottom that allows you to remove that delete option. You will only be able to send to trash then, not delete in one action.

ps. Welcome to the forum. Hopefully your future posts will result in better news. I bet everyone on this forum has accidentally deleted something at some point.

---

### Post by sceeeggg on 2011-04-06
To be fair, Nautilus does make itself clear (see attached).[COLOR=Blue]
[/COLOR] 
Thank you for responding. The attached that you included, or anything like it, never appeared when I choose
delete. So now I will be much more careful. I guess delete really means gone for good!

---

### Post by HermanAB on 2011-04-06
Well, first look in the trash can.  If it is there, restore it. If it isn't there, then you are pretty much out of luck.

---

### Post by searchfgold6789 on 2011-04-06
If the folder was important, you might try using PhotoRec from a Live CD (so that you don't overwrite the space where the folder was).

---

### Post by Elfy on 2011-04-06
If you were root when you deleted the folder it would possibly not be in your trash but root's.

---

### Post by QLee on 2011-04-06
sceeeggg,

A default install of Ubuntu does not have the "delete" on the nautilus right click menu. So, you would have had to option it that way to be able to bypass the trash. Even so, there would have been the warning that r-senior mentioned when you did it. 

forestpiskie's suggestion is related to something that new users often do, find a way to  send something to root's trash and then not be able to find it in their user's trash. What folder did you delete? Was it one owned by root?

---

### Post by The Cog on 2011-04-06
QLee is right. The default install doesn't show the delete option in the right-click menu. 

I have a feeling that nautilus keeps a separate deleted items folder for each mounted filesystem. So if you (for instance) deleted something on a USB stick, it would create a hidden folder on there and hide the "deleted" items in the hidden folder. It might be worth enabling the showing of hidden files (Ctrl-H or View->Show hodden files) and look round for a likely looking hidden folder (hidden files/folders have a name that starts with a dot).

---

