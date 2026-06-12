---
title: "USB thumbdrive empty, but shows 700MB space used"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by ReplicateThis on 2010-09-19
Hi.
I've attached two screenshots below - one showing that there are no files or anything at all on my thumbdrive, and another showing that this same "empty" drive has 700MB of space used.  

How does "nothing" take up space on the drive?  How can I delete "nothing" to get the space back?

Thanks!

---

### Post by Elfy on 2010-09-19
Try doing Ctrl+H in the filemanager and look in the trash

---

### Post by ReplicateThis on 2010-09-19
Thanks.  That did indeed work.

Is there any way I can set the thumbdrive (just the thumbdrive and not the regular hard drives) to delete stuff immediately instead of sending to trash?  Or set a maximum size of the trash so it'll only keep the last items I deleted up to a certain size?

I'm not trying to get Ubuntu to act exactly like Windoze, but in this regard Windoze's style of just keeping a very small trash bin (or none at all) makes more sense to me on a 1 GB thumb drive...

Thanks again!

---

### Post by JKyleOKC on 2010-09-19
> **ReplicateThis said:**
> Is there any way I can set the thumbdrive (just the thumbdrive and not the regular hard drives) to delete stuff immediately instead of sending to trash?If you press and hold either shift key while doing the delete, either from the menu or by using the DEL key, that will bypass the Trash folder and remove the selected file immediately. You'll get a message box asking you to confirm, since there won't be any ability to recover the file later. I don't know of any way to make this automatic, however.

---

### Post by ReplicateThis on 2010-09-19
Fair enough - and not the biggest of deals anyway.  Thanks for the help.  Marking thread as solved.

Thanks again, all!

---

### Post by Elfy on 2010-09-19
Not sure you can make that automatic.

I'd +1 JKyleOKC's shift+delete.

You can though add a delete command to the right click menu that will bypass the trash.

Found this - that is 2 years old, but **_might_** still work [http://ubuntuforums.org/showthread.php?t=698649](http://ubuntuforums.org/showthread.php?t=698649)

---

### Post by ReplicateThis on 2010-09-19
Thanks for pointing those out.

On an aside, seems strange that a script would be necessary to regulate trash space.  I would have thought that to be an easily configurable thing to do through the operating system, like by right clicking on the trash icon...  ;)

It's the little things like this that I believe sometimes turn off new users from using Linux...  But that conversation should be left to another thread...

I thank you again for your help!

---

### Post by QLee on 2010-09-20
[QUOTE=ReplicateThis]...
On an aside, seems strange that a script would be necessary to regulate trash space.  I would have thought that to be an easily configurable thing to do through the operating system, like by right clicking on the trash icon...  ;)
...[/QUOTE]


With different operating systems it shouldn't seem strange that some things are done differently. Much of the software was written by people with different opinions on useful functionality.

To me, it doesn't seem too strange for file deletion behaviour to be configured in System-->Preferences-->File Management. 

So, rather than "strange", I just think it "different". It might require a small amendment to the way you normally operate in a different OS.

---

### Post by ReplicateThis on 2010-09-20
> **QLee said:**
> To me, it doesn't seem too strange for file deletion behaviour to be configured in System-->Preferences-->File Management. 

This is exactly what I was looking for, and no one had suggested a way to adjust it like this before.

Unfortunately there is no such heading in my System --> Preferences.  
I was trying to take a screenshot to show this, but it seems I can't take a screenshot of a pull-down menu with the PrtScr button...  Anyway, my list goes from Emerald Theme Manager right to IBus Preferences - no File Management.  Personal File Sharing is the only heading in this menu that seems to have anything to do with files, and it isn't what I need.

Perhaps I worded it wrong before.  Both "strange" and "different" are not as appropriate as "non-intuitive".  I'm not looking for Linux to be Windoze by any means, but in XP I could operate like Neo in the Matrix and jump around bullets.  Here in Linux I'm, well, much more confused, and limited in my abilities.

Anyway, if anyone has a suggestion on how I can adjust the size of the trash file on my thumbdrive, it would be fantastic, but I have no such heading as System-->Preferences-->File Management.  And I do have a workaround so it's not really a huge deal in any case.

Thanks again for everyone's help!

---

### Post by Elfy on 2010-09-20
Hidden in the menu by default I think. It is exactly the same though as doing Edit Preferences in a nautilus instance.

There is no trash sizing option in there.

---

### Post by ReplicateThis on 2010-09-20
I know how to hide and unhide files and folders in Nautilus, but not in a menu.

I wasn't aware there could be hidden menu items.  How would I be able to reveal them?

Thanks!

---

### Post by Elfy on 2010-09-20
> **ReplicateThis said:**
> I wasn't aware there could be hidden menu items.  How would I be able to reveal them?

Thanks!

Right click the menu on the panel - Edit Menu

---

### Post by ReplicateThis on 2010-09-20
Awesome - found it!

To everyone - thank you once again for the help!  :)

---

### Post by jkmcg on 2012-08-27
> **Elfy said:**
> Try doing Ctrl+H in the filemanager and look in the trash

I am new and do not know where to find the "file manager" is this the computer manager in administration tools?

---

