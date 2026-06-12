---
title: "File permissions issue"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by HunterjWizard on 2009-12-28
All right I'm posting here because I am relatively new to Linux in general. I am running a small Ubuntu fileserver at work and for the first few weeks everything was going fine. I could access the shares from windows boxes, create and delete files, copy files I needed to share, the works. 
 
Then(And I don't know if this is related) there was a powerfailure and the server had to be reset. It's just an experiment at this point so it doesn't have a battery backup. Anyway, since then, or maybe not(it is difficult to pinpoint a start-date) I can no longer do anything besides look at the files in the shares. I can execute them, but I cannot copy/delete/rename anything.
 
When I look at the files from Ubuntu, everything has a little lock emblem next to it which apparently means no write. When I check the permissions is says nobody owns them so the permissions cannot be set.
 
This has unfortunately made the server basically useless. Any help will be greatly appreciated and thanks in advance.

---

### Post by phillw on 2009-12-28
Hi and welcome to forums.

Are the files that cannot be written to in any particular directory (folder) ?
You mentioned that they owned by no-one - who, or what is their group ?
What is the group for those with permissions to write to the files / directories ?

Regards,

Phill.

---

### Post by mapes12 on 2009-12-28
From what I gather you are looking at a windoze box(es) from a Ubu machine? That being the case you might want to try accessing the shares using su permissions. In Terminal ```
gksudo nautilus
``` then right click the folder/file you want to manage, select Properties then the Permissions tab and make changes from there.

WARNING: Do not delete anything when using nautilus with su permissions without pressing Shift+Delete at the same time. Otherwise your root trash will fill up and you will spend ages trying to figure out where all your disk space has disappeared to.

Mark

---

### Post by HunterjWizard on 2009-12-28
Hi Phill, 
 
The files are in /home/rick, (rick is my username)then there are a number of subfolders shared from there, it's inside the subfolders that the problem occurs. For examble: all the files in /home/rick/labfiles have the lock emblem. labfiles is shared across the network and I used to be able to copy files into it from my windows box(the old fileserver)
 
The owner for the locked files is listed as 'nobody' and the group is 'nogroup'. If it matters, all the files in this folder were copied there from a windows box.
 
Thanks.

---

### Post by HunterjWizard on 2009-12-28
> **mapes12 said:**
> From what I gather you are looking at a windoze box(es) from a Ubu machine? 
 
I access them from different 'windoze':P machines around the campus(this is a school), but I have a monitor/keyboard/mouse setup and am looking at everything on the gnome desktop at the physical machine. I'm a little... let's call it 'inept' when it comes to doing things the command line way.
 
Edit: I tried the nautilus command, it's still showing the files as belonging to nobody and no group and thus will not let me edit the permissions.

---

### Post by mapes12 on 2009-12-28
> Edit: I tried the nautilus command, it's still showing the files as belonging to nobody and no group and thus will not let me edit the permissions.Did you right click and then select the Permissions tab. You should be able to make the Permission changes in there.

---

### Post by HunterjWizard on 2009-12-28
> **mapes12 said:**
> Did you right click and then select the Permissions tab. You should be able to make the Permission changes in there.
 
Yes, that's where it's showing the status, the boxes for changing permissions are greyed out.
 
Edit: Ok my mistake, when I typed in the command it oppened a enw file browser window, when I navigated to the files from that window I am now able to edit the permissions, thanks.

---

### Post by HunterjWizard on 2009-12-28
Ok, sitting at the Ubuntu machine I can now rename files, delete, edit, move around, etc in the window I got from typing the nautilus command in (extremly helpful, I'll be saving that one).
 
However, the permissions are still all wonky. I can now change the owner and group, but it does not apply to the subfolders and when I modify read/write settings it changes them back.

---

### Post by phillw on 2009-12-28
> The owner for the locked files is listed as 'nobody' and the group is 'nogroup'. If it matters, all the files in this folder were copied there from a windows box.

Windows doesn't 'do' permissions - That's why no one had permissions. using nautilus should get you running, if they're all in one directory, you can use the command line also.

Phill.

---

### Post by HunterjWizard on 2009-12-28
There's about 4 directories where I'm having this problem, though each one has dozens of sub directories.
 
I still cannot write to the shares from my windows box, which is kind of the main issue right now.
 
Any ideas on why this all happened in the first place so I can keep from getting in this rut again?
 
Edit: After fiddling with it a little bit more everything seems to be back up and running, whew. Still would like to figure out what went wrong to begin with.

---

