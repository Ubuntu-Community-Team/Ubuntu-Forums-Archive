---
title: "OOoWriter files corrupt ALL of them?????"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Kellemora on 2009-03-05
Hi Gang

I'll ask here before heading over to OOo, since it might be Ubuntu related.

Applies to Hardy 8.04 64 bit ONLY, not the 32 bit Hardy machines!

EVERY file written in OOoWriter and saved "ON THE DATA FILE SERVER" is NOW showing, File is corrupt and cannot be opened, would you like OOo to repair this file?
Select yes and the file opens with nothing wrong with the file.

However, if we MOVE the file from the File Server to the Desktop FIRST and then open it, we get no file corruption error.

We get NO SUCH MESSAGE if we open the exact same file from a 32 bit Ubuntu machine, nor from OOoWriter on an XP machine.
It is ONLY occurring on the 64 bit Ubuntu machine.
This is why I'm asking HERE, it seems to be an Ubuntu related problem!

Any Ideas gang?????

TTUL
Gary

---

### Post by Xiong Chiamiov on 2009-03-07
Giving some information about your network setup, including details on "the data file server" would be helpful.

---

### Post by Kellemora on 2009-03-07
Hi XC

Data File Server is an HP Pavilian 753n running Ubuntu Hardy 32 bit, file system is EXT3 with only ONE shared folder named File_Server, then of course EVERYTHING else is in sub-folders under that folder.  Sharing provided by Samba!

As I said in my opening post, we can open ANY .odt file from any 32 bit Ubuntu computer without errors, and from our last remaining XP machines without errors.
It doesn't matter which file we select, large or small, old or new. 
They all work fine on 32 bit and ALL say they are corrupt when trying to open them on the 64 bit machine.  EVEN those files created on the 64 bit machine and saved to the Data File Servers folders.

I purposely created a duplicate file of the one that was corrupted on my desktop folder, opened and closed it like 25 times, printed it out twice, no problems.  Saved it to the Data File Server, opened it with the other machines, came back to this one and got the error.
Repeated the above WITHOUT opening it with any other machine, still got the same error.
Took the file that was showing the errors, copied it back to the desktop under a different file name, opened right up with no errors.  Copied it back to the Data File Server and the error was back again.

Since yesterday I have checked nearly every daily use file on the Data File Server, about 45 of them, they give no errors on any machine, but ALL of them give the corrupt error on this machine.

Which is a built-up using ASUS M2N68-AM Mobo 4 gig RAM, 64 bit Ubuntu, 1 gig LAN, dual core AMD64.

I checked both Open Office Org and Launchpad and the consensus is that Samba is the culprit causing the problem.  Which is why I didn't bother to bump this after it sat so long.

Samba and especially the Bugs in Nautilus have dealt us fits for over 6 months now!  But we have found work arounds for most of the bugs in Nautilus, not all of them in Samba though.

Thanks for taking a look!

TTUL
Gary

---

### Post by jimreynold2nd on 2009-03-07
Umm... I suspect Samba too. Try NFS?

---

### Post by Kellemora on 2009-03-07
Hi Jim

I have NFS installed also, but have no idea how to make it use it!

Stuff like that is still over my head I'm afraid!

I didn't understand a word of the Wiki about using it.

Thanks

TTUL
Gary

---

