---
title: "Recycler virus"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Struggling1 on 2009-08-22
I recently used my memory stick on a windows PC and now have the "RECYCLER" virus stuck in my trash can.  I've tried deleting it, but it just stays put.
Is there some way of getting rid of this menace?  :confused:

I'm really not clued up on computer speak, so please keep replies as jargon-free as possible.  Thanks in advance.

---

### Post by earthpigg on 2009-08-22
you could always pop it into an ubuntu machine and use gparted to wipe it clean, but you would lose any information you have on it.

to install gparted:
> sudo apt-get install gparted

to run gparted:
system -> administration -> partition editor

---

### Post by MelDJ on 2009-08-22
did you  delete anything from it while using ubuntu?

---

### Post by mapes12 on 2009-08-22
You could have a go at deleting it using root permissions with Nautilus ```
gksu nautilus
```Be careful with this. Highlight the file to delete then press Shift+Delete. If you don't press the Shift key and just use the Delete key all you will do is move the file to Roots trash bin without knowing it.

---

### Post by ibuclaw on 2009-08-22
> **Struggling1 said:**
> I recently used my memory stick on a windows PC and now have the "RECYCLER" virus stuck in my trash can.  I've tried deleting it, but it just stays put.
Is there some way of getting rid of this menace?  :confused:

I'm really not clued up on computer speak, so please keep replies as jargon-free as possible.  Thanks in advance.
[LIST=1]
[*]Open up the file browser and go to your memory stick.
[*]Press **Ctrl+H** and you should see some folders with a period infront of them.
[*]Select the folder **.Trash** and press Delete to permanently remove the directory and all files/folders inside.
[/LIST]
'.Trash' is where all files you moved to the trash can are stored, so if you moved the "RECYCLER" virus to the trashcan on the USB stick, this action should permanently remove it.

Regards
Iain

---

### Post by Struggling1 on 2009-08-24
Thanks for the feedback, guys.
The horrid RECYCLER folder is in the trash can of the hard drive.    I tried the “gksu nautilus” command suggested, but it still wouldn't go away.

If I run the “sudo apt-get install gparted “ advised above, how will that affect the data on my hard drive?
Also, apart from looking unsightly, what is this virus' MO?  What is it doing the data on my computer?

---

### Post by mapes12 on 2009-08-24
> **Struggling1 said:**
> Thanks for the feedback, guys.
The horrid RECYCLER folder is in the trash can of the hard drive.    I tried the &#8220;gksu nautilus&#8221; command suggested, but it still wouldn't go away.

If I run the &#8220;sudo apt-get install gparted &#8220; advised above, how will that affect the data on my hard drive?
Also, apart from looking unsightly, what is this virus' MO?  What is it doing the data on my computer?GParted is a partitioning utility. Your Trash will be in your /home/*username* folder so depending on how you have your partitions setup you could loose all your data. I wouldn't use Gparted to solve your problem.

Have a look at this thread to see if there is anything that can help you:[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

On a Linux machine the virus is just a pest. It can't execute any commands with root permissions to mess things up.

---

### Post by nhasian on 2009-08-24
lucky that you run linux.  the recycler virus cannot execute in linux, and even if it could there is no registry for it to infect so it just stays dormant on the memory stick not harming your computer in any way.  with your memory stick mounted, just right click on its icon on the desktop and select format.  problem is solved.

---

### Post by Struggling1 on 2009-08-24
Yippee!  It worked.  I used the command ( gksudo nautilus ~/.local/share/Trash ) that was suggested, and now (to all appearances at least) I'm Recycler free.
Thanks guys! :guitar:

---

