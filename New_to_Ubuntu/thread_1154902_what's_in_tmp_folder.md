---
title: "what's in tmp folder"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by mjncheers on 2009-05-10
hi,

Please help... an absolute newbie here...

I'm using a Ubuntu live CD to test things out (I haven't really started yet).

Sorry I don't know much about computer, but I noticed something in the tmp file that I want to ask about.

There are files in the tmp folder that are followed by something like encrypted passwords:
keyring-9fyIeh (for ex.)
orbit-ubuntu
pulse-SHGIkdjgoa3Ill
seahorse-hi4Dl7
ssh-npawJc3590 > has a file agent.4349
virtual-ubuntu.8gf367

Well...are these default files?
agent.4349 happens to coincide with a trojan name so that worries me

I haven't installed yet. I have checked with the MD5 before I burned the .iso. 

Any help is welcome. Thanks~

:)

---

### Post by mcduck on 2009-05-10
/tmp is used for any temporary stuff that the system, or programs, need. All contents are erased when you restart the system so you don't need to worry about anything nasty being inside /tmp. :) Just random data that programs need to put somewhere for a while..

---

### Post by mjncheers on 2009-05-10
big thanks!

---

### Post by studiodude on 2009-05-14
so can it be emptied in the same way as on a windows machine or do you need to restart - mine has accumilated almost a gigabyte since last night!!

---

### Post by mcduck on 2009-05-14
> **studiodude said:**
> so can it be emptied in the same way as on a windows machine or do you need to restart - mine has accumilated almost a gigabyte since last night!!

Things should disappear on their own as soon as they are not needed any more. I wouldn't recommend removing stuff from /tmp by hand unless you are absolutely sure which program uses the files you are about to remove and that the program in question is not running any more.

---

### Post by studiodude on 2009-05-14
Ok, thats the answer I was looking for and made the question worth asking rather than me barging in thinking all temp files are just for the bin.

Thanks for your help.

---

### Post by NHArticleTen on 2009-05-14
do NOT randomly delete or alter items in tmp

---

