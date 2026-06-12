---
title: "Cannot open text files through share."
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Kayone on 2009-12-07
This one is kinda odd. 

I can open up and view a text file locally

I can map the drive and connect to the share
I can create a text file on the share
I can create a non-text file on the share
I can view the non-text file on the share

I can't view the text file. It says I don't have permissions. I am logged into the WIndows share as administrator and I am the originator of the file. I can literally create the file and .00001 seconds later, I can't open it.

Odd!
Any ideas?

---

### Post by Kayone on 2009-12-07
OK... maybe I screwed something up by trying to mount the share. Feel free to laugh at my sad attempts to figure out how to map a drive in linux.

I typed:
showmount
show mount (apparently linux doesn't use these lol)
mount drive://ip address for share
mount drive://ipaddress for share/share
mount drive:\\ip address for share\share
mount -t smbfs

None of this could be causing this to happen?!  Right?!

---

