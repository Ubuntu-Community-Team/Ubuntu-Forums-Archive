---
title: "Accidently deleted file"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Crazedpsyc on 2010-06-20
After spending weeks working on a shell script, I made it delete itself with echo > myfile.sh instead of echo >> myfile.sh. then, since I wanted to see what happened, I reloaded the file in gedit and it was empty. help me get it back! maybe theres a way to see th :mad::confused:

---

### Post by Penguin Guy on 2010-06-20
GEdit often caches files with and adds a [FONT="Courier New"]~[/FONT] extension, press [COLOR="Green"]Ctrl + H[/COLOR] to see these files. Apart from that, there's not much you can do.

---

### Post by tacotime on 2010-06-20
> **Crazedpsyc said:**
> After spending weeks working on a shell script, I made it delete itself with echo > myfile.sh instead of echo >> myfile.sh. then, since I wanted to see what happened, I reloaded the file in gedit and it was empty. help me get it back! maybe theres a way to see th :mad::confused:

ubuntu geek has an article on deleted file recovery -[here]("http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html") I hope that helps...

.:EDIIT:. after reading the article it looks like crap... sorry dood, I don't think there's much you can do..

---

### Post by Crazedpsyc on 2010-06-20
thanks for the quick responses, i'm looking at the article, and there were none of those cache files that I could see in the folder myfile.sh is in. :(

EDIT: I tried scalpel, and it finished with:
> Image file pass 1/2.
Allocating work queues...
Work queues allocation complete. Building carve lists...
Carve lists built.  Workload:
&#65533; with header "\x46\x4f\x52\x45\x4d\x4f\x53\x54" and footer "" --> 0 files
Carving files from image.
Image file pass 2/2.
../cmd: 100.0% |*************************************|    1.0 bytes    00:00 ETAProcessing of image file complete. Cleaning up...
Done.
Scalpel is done, files carved = 0, elapsed = 0 seconds.


Are you sure there is no way to see a history of commands executed by a shell script?

---

### Post by shawnansasio on 2010-06-20
see if there is a .swp (hidden) version of your file in the same dir that your file wast in when edited

---

### Post by Crazedpsyc on 2010-06-20
nope

---

### Post by Crazedpsyc on 2010-06-21
alright, I found a slightly older version on my backup disk, so I'm fine

---

