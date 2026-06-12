---
title: "General internet error on networked open office org"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by ginestre on 2008-03-24
I have Feisty on several machines around the house, all networked via cable. The machines are all visible and browsable from each other.  I have user accounts on each, with the same username and password.  There is a default installation of open office org on each, in English, version 2.2.0.

Within OOo, I can open,  read and write files across the network from downstairs to upstairs with no problem: I do File > Open > browse to file place > select > enter user password in the dialog box >and it works.

From downstairs to upstairs, I can't- even though for me the setups are identical. Why?

From the problem machine, I do File > Open > browse to file place > select > enter user password in the (apparently identical) dialog box, which then comes back as if the password were wrong, three times, before coming up with an Open Office org error message 'general internet error'

As far as I can tell, the two systems are set up identically - but there is obviously some setting somewhere that needs tweaking. But where? Any ideas as to where can I look for the widget or wodget I need to change (so as to be able to work from wherever in the house the kids aren't wreaking havoc) would be very gratefully accepted, and tried.  

TIA

---

### Post by Eiríkr on 2008-03-24
How have you implemented file sharing?  Since you mention password dialogs, I'm assuming Samba?  

I'm a little confused about your machines, as you note that you *can* access from downstairs to upstairs, and then that you *can't* -- likely a typo somewhere.  Let's assume that access from upstairs to downstairs is okay, but downstairs to upstairs is problematic.  

D->U, can you access the same directory in which the problem OOo files reside via Nautilus, and add or subtract files?  If you can in Nautilus but OOo still has trouble, the issue might possibly be related to file locking for the specific OOo file you're trying to open.  If you can't modify the contents of the directory in Nautilus, there's something else going on.  Either way, it would be useful to post the contents of the smb.conf file for the machine you're having trouble accessing.  You can view the file by typing the following into a terminal on the problem machine:
```
less /etc/samba/smb.conf
```

Cheers,

Eiríkr

---

### Post by ginestre on 2008-03-25
> **Eiríkr said:**
> How have you implemented file sharing? .....
Eiríkr

Thanks for the reply.  I'm using SSH - there is no real reason for this choice other than that someone told me it was an OK solution., and it works well in Nautilus, in all directions and from/to any machine.  In Nautilus I can browse any where, copy cut rename etc anything. 

I looked at the smb conf file, bur it was just the empty default (presumably because I'm not using it. Should I be? I thought samba was for linux<> windowes but I don't use windows at all.)

I can access from downstairs to upstairs in Nautilus, but not in OOo. 
From upstairs to downstairs I can access everything in both Nautilus and OOo. All files were created originally by the same username, regardless of  where they are now found, and some were additionally copied over with Nautilus- which is a pain as it's leading to multiple diverging copies that I'm having a hard time keeping track of. I'd like just one repository somewhere on the system- this is the nub.  Both sets of files (the originals and the copies) present the same difficulties.

Trying to open a file with OOo across the nw.....
On both machines I get the same pasword dialog box when I try to open across the nw in OOo. It gives me my username, and asks for a pwd. Downstairs to upstairs it works, but not the other way round.  I assume this is an OOo dialog, but it may something else invoked by File->Open, I suppose. On the one machine it works, on the other it gives me three attempts and then fails with a General Internet Error message. 

TIA, again

---

### Post by Eiríkr on 2008-03-25
SFTP over SSH is indeed one of the easiest ways to go for Lin-Lin sharing.  I had no idea OOo could open files via SFTP though, that's an interesting wrinkle.  

To rule out SSH itself, can you still access the problem machine via a regular terminal ssh session?  Do you have any better success browsing via Nautilus to the containing directory over SFTP, and then double-clicking the OOo files, rather than navigating to the containing directory in the OOo file open dialog?  And have you ever been able to open files directly through OOo, or has this accessibility problem been pretty consistent?

Cheers,

Eiríkr

---

