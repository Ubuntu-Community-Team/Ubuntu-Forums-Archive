---
title: "Cannot delete shares"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by P45 on 2008-07-20
Being a recent convert to Ubuntu I experimented to get my network running.  In the course of that I created a bunch of shared folders as windows shares on Ubuntu in the file browser.

Some time later I finally got Samba running properly and then went to delete the shares I had created in the file browser.  Those shares show as 'unknown' type and date modified also 'unknown', and they will not delete.  They show up across the network - they even work - but I don't want them.

When I move them to trash I get a dialog box (this one for the share I called ubuntu-peter): 
   "Cannot move file to trash, do you want to delete immediately?  
    The file "ubuntu-peter" cannot be moved to the trash."

So I pick Delete and get: 
   "Error while deleting. 
    There was an error deleting ubuntu-peter."
and under Show more details it offers
   "Operation not supported by backend"

The only available option then is to skip - leaving the share intact.

I thought I might use the Terminal and delete them as sudo but I cannot find the files.

I installed and ran SWAT thinking it might delete them but they don't show up on SWAT at all.

Can anyone suggest how I might delete these unwanted shares please?

Thanks, Peter

---

### Post by chickendude1313 on 2008-07-20
What does ls -l give you in the directory with the shares?

What happens if you try to rm share? (sudo if you don't own the share).

---

### Post by P45 on 2008-07-21
> **chickendude1313 said:**
> What does ls -l give you in the directory with the shares?

I cannot find that directory.  Can you tell me where to look please (remembering that they are not samba shares)?

> **chickendude1313 said:**
> What happens if you try to rm share? (sudo if you don't own the share).

I don't know how I would identify the share for this command.

Thanks for your questions - you give me hope.  Peter

---

### Post by chickendude1313 on 2008-07-21
In what directory did you make the share? (What directory were you in in the file browser when you made the shares)

Or even better
How did you go about making the share?

---

### Post by P45 on 2008-07-21
IIRC the shares were made in File Browser (Places / Home folder).  They were created by right click on a directory in my home folder and altering the properties.  I don't remember whether they were made using 'sharing' or permissions or a combination of both.

I was experimenting remember - I did not know where I was or how to get where I needed to be.

I even created a share of my home folder - it works too.  They were all made much the same way.

Peter

---

### Post by chickendude1313 on 2008-07-21
so you have some folders in your home directory which have sharing enabled?

but if you open up a terminal and do an ls, you don't see them?

What are the names of the folders which you have shared?

Try opening a terminal and doing:
find ~ -name "ubuntu-peter"
Basically, that searches through ~ (your home directory) for a file or directory named "ubuntu-peter". See if it finds it at all.

---

### Post by P45 on 2008-07-21
No joy: (the share name is confirmed to be all lower case)

peter@Ubuntu:~$ find ~ -name "ubuntu-peter"
find: /home/peter/.dbus: Permission denied
peter@Ubuntu:~$ sudo find ~ -name "ubuntu-peter"
sudo: unable to resolve host Ubuntu
[sudo] password for peter: 
find: /home/peter/.gvfs: Permission denied

I don't pretend to understand why it is unable to resolve host Ubuntu but I presume that is not critical to the issue at hand.

The data directories containing my files are here of course - I don't plan to delete them.

Thanks for your thoughts,  Peter

---

