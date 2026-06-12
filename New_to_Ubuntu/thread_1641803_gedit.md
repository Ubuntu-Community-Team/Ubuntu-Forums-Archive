---
title: "gedit"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by mistypotato on 2010-12-09
Up until I started using 9.04, I used gedit extensively.

Never had a moment's trouble with it.

Now, it seems to be getting worse and worse.





What I mean is, I'm getting errors that it can't understand the encoding of files I'm trying to open.

Is anyone else having this issue with gedit?

If not, I'm wondering if it could be a failing network card since the files in question were always transferred back and forth across my LAN....but I don't seem to be having trouble with any other files.

---

### Post by cariboo on 2010-12-09
Are they just plain text files? What happens when you try to view the files using cat?

---

### Post by lmarmisa on 2010-12-09
No problem with **gedit** here.

Maybe these commands could help you:

[LIST]
[*]**xxd** - creates a hex (and ASCII too) dump of a given file.
[*]**md5sum** - this tool checks the integrity of a file by means of the [MD5]("http://en.wikipedia.org/wiki/MD5") fingerprint. Run this command in the origin and the destination sides of your transferred files in order to verify if both copies of your files are identical.
[/LIST]
Best regards,

Luis

---

### Post by rburkartjo on 2010-12-10
no problem either on my end and use it daily

---

### Post by v1ad on 2010-12-10
never had a problem.

---

