---
title: "Printer not working"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by bradfordly on 2011-06-04
This is driving me crazy! When i try to connect to a windows 7 printer (HP 1020) via samba and verify it, it says print share inaccessible and I cannot install it correctly (cant connect to CIFS host it says). It worked on 10.10 and when i recently booted 10.10 from a live cd it worked. What is the difference from 10.10 to 11.04 that it doesn't work? Please Help!!!:confused:

---

### Post by garvinrick4 on 2011-06-04
Look at your printer location Like: smb//:WORKGROUP/XXXXX
What ever it is in the working install of 10.10 and down: or the live cd. Write down under printer preferences:
In URL type in "localhost:631" hit enter, Will go to Cups and you can install
printer from there same as with printer in ubuntu and you can put in correct
URI of printer. 11.04 comes up with a different one, slightly have to look closely.
Have not figured out why but a lot of users had the same problem in network samba workgroup printer.

---

