---
title: "Cannot Mount UDF Volume..."
date: 2009-09-13
forum: New to Ubuntu
---

### Post by redfox1160 on 2009-09-13
Hello everyone
I burned a data DVD on my Windows Vista machine, and wanted to use it on my Linux one. When I put the DVD in, an error came up that said:

"Cannot Mount Volume.
Invalid mount option when attempting to mount the volume 'UDF Volume'"

I am not very good with linux, but I am okay. I am running 9.04. Thanks for any help.

---

### Post by redfox1160 on 2009-09-14
I don't know if we are allowed to bump threads, but I am only doing it once...

---

### Post by egalvan on 2009-09-14
actually, thread bumps are allowed once every 24 hours.

And some folks search for un-answered threads...

so bumping may be counter-productive.

---

### Post by The Cog on 2009-09-14
I read somewhere that Windows writes malformed UDF disks, and that such malformed disks can only be mounted by root. 

So try something like this:
sudo mkdir /media/win-udf-cd
sudo mount /dev/cdrom /media/win-udf-cd

---

