---
title: "how do I open a folder"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by hekastos on 2011-02-07
I have to admit this sounds as stupid as it is embarrassing, but what can I do, so I have to ask you guys. I tried to create a tar.gz file from a folder which worked, but somehow I screwed it up and now when I click on places/home folder or places/desktop always the archiv manager opens and tells me that he does not know the archive format, of course he doesn't because I just want to open the freaky folder. I have a folder laying on my desktop which I can open just fine, so my workaround is always to open this folder and navigate through the file system to my target, this is very annoying, so my question is how can I unlink my places open command from archive manager and what did I do wrong?

thanks a lot for any help and sorry for this childish question! ;)

---

### Post by migs73 on 2011-02-07
Right click on the folder and select 'open with other application'

From the list select 'file browser' and make sure the 'remember this application for 'folder' files' box is checked.

Click open and your done.

Regards

Mike

---

### Post by hekastos on 2011-02-08
thx a lot for your reply, but unfortunately this doesn't work because a right click in the menu under Places on i.e. "downloads" or "home folder" has the same result as a left click (at least for me) the normal folders on my desktop or in a subdirectory work, just not the folders under places in the ubuntu menu left from the clock or right from applications menu... I hope I was able to express myself clearly, sorry I'm no native speaker.

and again thx for any help!!!

---

### Post by wojox on 2011-02-08
Post this back:

```
cat .config/user-dirs.dirs
```

---

### Post by [Snc] on 2011-02-08
Try right click a folder on your desktop, select "open with" then "Other Application"
Then in the list look for "File browser" or click "use custom command" and enter "nautilus".
Check "Remember this application for 'folder' files"

That should do it.

---

### Post by hekastos on 2011-02-08
thanks a lot that really did it!!!
perhaps you can guess what happend or explain how is opening a folder in Places different from the desktop? just so I know for next time, anyway big THX ):P

---

### Post by migs73 on 2011-02-09
??:confused:??

Which reply sorted your problem?

[snc] and mine were the same and wojox's should have generated a list in terminal that he wanted you to post back.

Just in case someone is reading this with the same issues.

---

### Post by Primefalcon on 2011-02-09
my guess in sncs reply since that is how you change the default ap for a program, the cat command is a display to terminal, in tis case my guess is he was looking for trouble shooting info

---

### Post by hekastos on 2011-02-11
@migs yes sync and your advice were basically the same and helped, but I didn't realize on your comment that it has to be done with the working folder not the not working one (as I said because the not working folder can not be right clicked, basically all my confusion came from this fact that Places folders can not be right clicked...) 

thx again!

---

### Post by migs73 on 2011-02-11
I see the subtle difference between mine and snc's now, I just wanted to know so others reading the thread with the same problem know what it is that requires to be done.

Mike:)

---

