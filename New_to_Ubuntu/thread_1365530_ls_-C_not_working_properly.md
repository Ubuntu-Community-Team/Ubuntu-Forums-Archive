---
title: "ls -C not working properly?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by switch10 on 2009-12-27
when I have a very short list of files in a directory listing in columns works, but when I have a very long list of files (when listing in columns would be useful), listing in columns doesn't work.  Am I missing something?  Is there an alternative to list many files in columns?


Thanks

Dave

---

### Post by markjensen on 2009-12-27
I am going to guess that the problem is you have one or more very long filenames in there.  I think that the ls -C command will base the column width on this, and you may only see one column, depending on your terminal's width.

Try stretching your terminal to the full width of your screen, and re-run the command.

---

### Post by switch10 on 2009-12-27
> **markjensen said:**
> I am going to guess that the problem is you have one or more very long filenames in there.  I think that the ls -C command will base the column width on this, and you may only see one column, depending on your terminal's width.

Try stretching your terminal to the full width of your screen, and re-run the command.

thanks yeah I thought that might be it.  the file names are pretty long.  my screen is stretched though...  Maybe ill make my font smaller.

---

