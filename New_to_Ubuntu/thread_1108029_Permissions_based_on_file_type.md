---
title: "Permissions based on file type"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by pzs on 2009-03-27
Is there any way I can get Linux to generate new files with permissions based on the file type? Every time I start a new Perl or Python script I have to chmod u+x before I can run it. Of course, I don't want *all* new files to have execute privileges, but having it look for .pl or .py to decide would make sense.

Cheers.

---

### Post by HermanAB on 2009-03-27
Linux doesn't work like that.  The .ext part of a file name is a Microsoft DOS thing that doesn't really mean anything in Linux.  File types are detected by an appropriately named program called 'file'.  That is why you can name a jpeg picture as picture.gif or picture.txt and The Gimp will still open it without a complaint.

Some Linux desktop system, notable KDE does look at the .ext part of file names to try and figure things out, but that is not how it is supposed to be.

So, if you want a file to be executable, then you got to set it yourself - that is a securty thing, but you could use wild cards:
$ chmod +x *pl

and you could even make that a cron job by placing a script in /etc/cron.hourly:
#! /bin/bash
chmod +x /home/wherever/*pl

...of course, you got to make that script executable too!

Cheers,

Herman

---

### Post by Bachstelze on 2009-03-27
> **HermanAB said:**
> Some Linux desktop system, notable KDE does look at the .ext part of file names to try and figure things out, but that is not how it is supposed to be.

KDE uses MIME types to determine for example which application a file is opened with.

---

### Post by Taras.M.K on 2009-03-27
How do you create new *.pl files. Do you use "$ touch filename.pl" or some editor (environment). Maybe you can set it there?

---

### Post by perpetualcacophany on 2009-03-27
> **Taras.M.K said:**
> How do you create new *.pl files. Do you use "$ touch filename.pl" or some editor (environment). Maybe you can set it there?

```

$ touch filename.pl && chmod +x filename.pl

```

That would create it and make it executable. You really don't need the extension though as others have said before.

---

### Post by Taras.M.K on 2009-03-27
> **perpetualcacophany said:**
> ```

$ touch filename.pl && chmod +x filename.pl

```

That would create it and make it executable. You really don't need the extension though as others have said before.
Quite. Or even create some alias for it like "touchx".

---

