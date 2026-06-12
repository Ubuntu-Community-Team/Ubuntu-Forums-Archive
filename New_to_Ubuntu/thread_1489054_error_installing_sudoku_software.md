---
title: "error installing sudoku software"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by jud1929 on 2010-05-20
Hi,

I'm new to Linux and need help learning to install programs that are not in Synaptic.
I'm using Karmic.  I  have downloaded a Sudoku program from Weekend Code.
After clicking to unzip it, I tried to run it by clicking on the file with exe suffix.
The error message is
 Archive:  /home/jud1929/.cache/.fr-pOLEZD/fbskb/util/skbbatch.exe
[/home/jud1929/.cache/.fr-pOLEZD/fbskb/util/skbbatch.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/jud1929/.cache/.fr-pOLEZD/fbskb/util/skbbatch.exe or
          /home/jud1929/.cache/.fr-pOLEZD/fbskb/util/skbbatch.exe.zip, and cannot find /home/jud1929/.cache/.fr-pOLEZD/fbskb/util/skbbatch.exe.ZIP, period.

Could you give me a hand, please.

Thank you

Jud

---

### Post by roger_1960 on 2010-05-20
Hi

You have been trying to install windows software under linux.  I suggest you read all of the following article - its very helpful

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Welcome and good reading!

---

### Post by SlidingHorn on 2010-05-20
I believe Roger's correct.  However, Ubuntu has a Sudoku game installed by default.  From your main menu, go to:

Applications > Games > Logic > Sudoku

---

### Post by arochester on 2010-05-20
It says "Compiled programs are provided for Linux (Ubuntu) and Windows."

When decompressed the file has an "SRC" which has "linux" inside

---

### Post by jud1929 on 2010-05-20
> **arochester said:**
> It says "Compiled programs are provided for Linux (Ubuntu) and Windows."

When decompressed the file has an "SRC" which has "linux" inside



Thanks to all of you for your help. The article on installing software is great and I've bookmarked but is doesn't seem to apply here.

I see the file SRC   - now what do I do please?

Thanks again,

---

### Post by roger_1960 on 2010-05-21
Hi again

Had a look at the folders you have downloaded.  No .deb file  or .tar.gz files.  If possible at all, its complicated to install binary files manually!  I would try running the windows software under WINE (available in the synaptic repositories.  Before trying it, read [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

This often works well for software which is not fast moving graphics.

---

