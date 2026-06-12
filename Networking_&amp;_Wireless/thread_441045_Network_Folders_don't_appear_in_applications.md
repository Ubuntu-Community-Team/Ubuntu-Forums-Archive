---
title: "Network Folders don't appear in applications"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by rjmusto on 2007-05-12
Have installed Feisty on a home network PC and is running great.

I have a networked drive where all my photo and music files are stored and I can access these under Places and I have added a link to these folders so they appear in the left hand plane of Places. So far so good.

However, these networked folders do not appear on the Open File list in most applications. For example, I can't open a photo file with Gimp as it doesn't list the network anywhere.
I have tried to 'Make a Link' to these network folders from the right click menu but it throws up an error: 'Unsupported Operation'

The only exception to this is the Open Office apps, these do list the network folders under the Open File menu.

How can I get a mapped network drive to work properly so that all apps see these folders?

Thanks.

---

### Post by spd106 on 2007-05-14
It's probably better to add the directories as bookmarks, these tend to show up more in the file chooser. Also bear in mind that not all apps support GTK file choosers.

---

### Post by rjmusto on 2007-05-17
Thanks for the reply.

I've tried the bookmark route too, but they don't show up either. 
There must surely be some way of getting these folders to show in the apps?

This is one area of Linux where I feel the system really lets you down - dare I say it feels a bit like it was working with Windows 3.11!

How difficult would it be to get a drag and drop system working that just adds a link, instead of copying the whole folder?

R

---

### Post by Detonate on 2007-05-17
> **rjmusto said:**
> 
There must surely be some way of getting these folders to show in the apps?

Mount them.

---

### Post by Seq on 2007-05-17
Not all apps, even GTK+ ones actually use the gnome vfs layer, which handles the smb (and ftp, etc) links. You would have to mount them, as Detonate indicated.

---

### Post by rjmusto on 2007-05-20
Good advice,  thanks.

I've followed the procedure on the Feisty documentation and have got the folder mounted ok.

It is a bit unreliable though. I can browse it ok and use it with most apps but if I try to access it with others, then the whole lot hang. Haven't sust out a pattern yet, but seems to be ok with only one application running. More than that and things go awry. I usually have to reboot to clear it.

Any suggestions?

---

### Post by measekite on 2007-09-15
I too have a similar problem.  Gimp cannot see the network.  Open Office does fine and so does every other application I have tried so far.

What applications have you used that could not access the network?

---

