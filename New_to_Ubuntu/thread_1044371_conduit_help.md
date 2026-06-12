---
title: "conduit help?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by An_Dynas on 2009-01-19
after reading some rave reviews I decided to try conduit to sync some files and folders.  Unfortunately, it locks up every time I try to connect to box.net to upload.  Currently pulling my hair out b/c this looks like a really good program/idea.

There seems to be no usuable documentation on the main site nor any available forum to seek help. Anyone use this program?  Have any good ideas?  know where some help could be found?

---

### Post by compiledkernel on 2009-01-19
I would imagine if Conduit is locking up, you would see something in /var/log/messages at the time it occurs. 

Additionally though, it might be a size or extension limitation. I seem to remember that Box.net has size limitations depending on the level of account you hold as well.

---

### Post by An_Dynas on 2009-01-19
it does have a size limitation, but the seizure occurs as soon as conduit begins communicating with box.net, before any uploading occurs.  Going to my box.net account I can see that nothing uploaded.

The program links with box.net, then box.net asks for the login information, accepts same and says proceed -- then the trouble starts.  Error appears to be software communication, or possibly user error, but in either event I don't know what I'm doing wrong.

---

### Post by An_Dynas on 2009-01-19
> **compiledkernel said:**
> I would imagine if Conduit is locking up, you would see something in /var/log/messages at the time it occurs. 


Thanks for the tip, have never been to this file before.  Other than typical startup lines and connection to an external drive, I don't see anything from today indicating a lockup.  What should I expect?  Also, what does occasional "--MARK--" line note?

---

### Post by compiledkernel on 2009-01-19
[http://bugzilla.gnome.org/show_bug.cgi?id=550216](http://bugzilla.gnome.org/show_bug.cgi?id=550216)

There appear to be a bug or two related to this. 

I would suggest running conduit from a terminal window, and then trying again and posting whatever output from that terminal window comes up.

---

